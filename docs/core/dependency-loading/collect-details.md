---
title: Сбор подробных сведений о загрузке сборок — .NET Core
description: Узнайте, как выполнить сбор сведений о загрузке сборок в .NET Core.
author: elinor-fung
ms.author: elfung
ms.date: 11/17/2020
ms.openlocfilehash: 505fc827021fe4d34675b2ef5a7fc5746ada1af6
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872942"
---
# <a name="collect-detailed-assembly-loading-information"></a>Сбор подробных сведений о загрузке сборок

Начиная с .NET 5.0, среда выполнения может создавать события с помощью `EventPipe` с подробными сведениями о [загрузке управляемой сборки](loading-managed.md), которые упрощают диагностику проблем с загрузкой сборок. Такие [события](../../fundamentals/diagnostics/runtime-loader-binder-events.md) выдаются поставщиком `Microsoft-Windows-DotNETRuntime` с ключевым словом `AssemblyLoader` (`0x4`).

## <a name="prerequisites"></a>Предварительные требования

- [Пакет SDK для .NET 5.0](https://dotnet.microsoft.com/download) или более поздней версии.
- Средство [dotnet-trace](../diagnostics/dotnet-trace.md).

## <a name="collect-a-trace-with-assembly-loading-events"></a>Сбор трассировки с помощью событий загрузки сборок

Чтобы включить события загрузки сборок в среде выполнения и собирать для них трассировки, используйте `dotnet-trace` с помощью следующей команды:

```console
dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id <pid>
```

При этом будет собрана трассировка указанного `<pid>`, которая активирует события `AssemblyLoader` в поставщике `Microsoft-Windows-DotNETRuntime`. Результатом будет файл `.nettrace`.

## <a name="view-a-trace"></a>Просмотр трассировки

Собранный файл трассировки можно просмотреть в Windows с помощью представления "События" в [PerfView](https://github.com/microsoft/perfview). Все события загрузки сборок будут иметь префикс `Microsoft-Windows-DotNETRuntime/AssemblyLoader`.

## <a name="example-on-windows"></a>Пример (в Windows)

Здесь используется [пример точек расширения загрузки сборок](https://docs.microsoft.com/samples/dotnet/samples/assembly-loading-extension-points/). Приложение пытается загрузить сборку `MyLibrary`, на которую не ссылается приложение и которая поэтому требует обработки в точке расширения загрузки сборок для успешной загрузки.

### <a name="collect-the-trace"></a>Сбор трассировки

01. Перейдите к каталогу со скачанным примером. Выполните сборку приложения с помощью команды:

    ```console
    dotnet build
    ```

01. Запустите приложение с аргументами для приостановки и ожидания нажатия клавиши. При возобновлении приложение попытается загрузить сборку `AssemblyLoadContext` по умолчанию, без обработки для успешной загрузки. Перейдите к выходному каталогу и выполните команду:

    ```console
    AssemblyLoading.exe /d default
    ```

01. Найдите идентификатор процесса приложения.

    ```console
    dotnet-trace ps
    ```

    В выходных данных будут указаны доступные процессы. Пример:

    ```console
    35832 AssemblyLoading C:\src\AssemblyLoading\bin\Debug\net5.0\AssemblyLoading.exe
    ```

01. Подключите `dotnet-trace` к выполняющемуся приложению.

    ```console
    dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id 35832
    ```

01. В окне, где выполняется приложение, нажмите любую клавишу, чтобы продолжить выполнение программы. Трассировка будет автоматически прекращена после завершения работы приложения.

### <a name="view-the-trace"></a>Просмотр трассировки

Откройте собранную трассировку в [PerfView](https://github.com/microsoft/perfview) и откройте представление "События". Отфильтруйте список событий для отображения событий `Microsoft-Windows-DotNETRuntime/AssemblyLoader`.

:::image type="content" source="media/collect-details/assembly-loader-filter.png" alt-text="Изображение фильтра загрузчика сборок PerfView":::

Будут показаны все загрузки сборок, которые были выполнены в приложении после начала трассировки. Чтобы просмотреть операцию загрузки для нужной сборки в этом примере (`MyLibrary`), мы можем задать дополнительные фильтры.

### <a name="assembly-loads"></a>Загрузки сборок

Отфильтруйте представление для отображения событий [`Start`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstart-event) и [`Stop`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstop-event) в разделе `Microsoft-Windows-DotNETRuntime/AssemblyLoader` с помощью списка событий слева. Добавьте к представлению столбцы `AssemblyName`, `ActivityID` и `Success`. Выполните фильтрацию по событиям, содержащим `MyLibrary`.

:::image type="content" source="media/collect-details/start-stop.png" alt-text="Изображение событий запуска и завершения в PerfView":::

| Имя события             | AssemblyName                                      | Идентификатор действия | Успех |
| ---------------------- | ------------------------------------------------- | ---------- | ------- |
| `AssemblyLoader/Start` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | //1/2/     |         |
| `AssemblyLoader/Stop`  | `MyLibrary, Culture=neutral, PublicKeyToken=null` | //1/2/     | False   |

Вы должны увидеть одну пару `Start`/`Stop` с `Success=False` для события `Stop`, что указывает на сбой операции загрузки. Обратите внимание, что два события имеют одинаковый идентификатор действия. Идентификатор действия можно использовать для фильтрации всех остальных событий загрузчика сборок с отображением только тех из них, которые относятся к этой операции загрузки.

### <a name="breakdown-of-attempt-to-load"></a>Детализация попытки загрузки

Чтобы просмотреть детализацию для операции загрузки, отфильтруйте представления по [событиям `ResolutionAttempted`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#resolutionattempted-event) в разделе `Microsoft-Windows-DotNETRuntime/AssemblyLoader` с помощью списка событий слева. Добавьте к представлению столбцы `AssemblyName`, `Stage` и `Result`. Выполните фильтрацию по событиям с идентификатором действия из пары `Start`/`Stop`.

:::image type="content" source="media/collect-details/resolution-attempted.png" alt-text="Изображение событий ResolutionAttempted в PerfView":::

| Имя события                           | AssemblyName                                      | Этап                               | Результат             |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AppDomainAssemblyResolveEvent`     | `AssemblyNotFound` |

Приведенные выше события указывают, что загрузчик сборок попытался разрешить сборку путем поиска в текущем контексте загрузки, запуска логики проверки по умолчанию для сборок управляемого приложения, вызова обработчиков для события <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> и вызова обработчиков для <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>. При выполнении каждого из этих шагов сборка не была найдена.

### <a name="extension-points"></a>Точки расширения

Чтобы узнать, какие точки расширения были вызваны, выполните фильтрацию представления по [`AssemblyLoadContextResolvingHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadcontextresolvinghandlerinvoked-event) и [`AppDomainAssemblyResolveHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#appdomainassemblyresolvehandlerinvoked-event) в разделе `Microsoft-Windows-DotNETRuntime/AssemblyLoader` с помощью списка событий слева. Добавьте к представлению столбцы `AssemblyName` и `HandlerName`. Выполните фильтрацию по событиям с идентификатором действия из пары `Start`/`Stop`.

:::image type="content" source="media/collect-details/extension-point.png" alt-text="Изображение событий точки расширения в PerfView":::

| Имя события                                                  | AssemblyName                                      | HandlerName                      |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` |
| `AssemblyLoader/AppDomainAssemblyResolveHandlerInvoked`     | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAppDomainAssemblyResolve`     |

Приведенные выше события указывают на то, что обработчик с именем `OnAssemblyLoadContextResolving` был вызван для события <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType>, а обработчик с именем `OnAppDomainAssemblyResolve` — для события <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.

### <a name="collect-another-trace"></a>Сбор дополнительной трассировки

Запустите приложение с аргументами, чтобы обработчик события <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> загружал сборку `MyLibrary`.

```console
AssemblyLoading /d default alc-resolving
```

Соберите и откройте еще один файл `.nettrace`, выполнив [приведенные выше шаги](#collect-the-trace).

Снова выполните фильтрацию по событиям `Start` и `Stop` для `MyLibrary`. Вы должны увидеть пару `Start`/`Stop` с `Start`/`Stop` между ними. Внутренняя операция загрузки представляет загрузку, активируемую обработчиком для <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> при вызове <xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType>. Вы должны увидеть `Success=True` для события `Stop`, что указывает на успешную операцию загрузки. В поле `ResultAssemblyPath` отображается путь к итоговой сборке.

:::image type="content" source="media/collect-details/start-stop-success.png" alt-text="Изображение успешных событий запуска и завершения в PerfView":::

| Имя события             | AssemblyName                                                       | Идентификатор действия | Успех | ResultAssemblyPath                                      |
| ---------------------- | ------------------------------------------------------------------ |------------|---------| ------------------------------------------------------- |
| `AssemblyLoader/Start` |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | //1/2/     |         |                                                         |
| `AssemblyLoader/Start` | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | //1/2/1/   |         |                                                         |
| `AssemblyLoader/Stop`  | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | //1/2/1/   | True    | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |
| `AssemblyLoader/Stop`  |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | //1/2/     | True    | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |

Затем можно просмотреть события `ResolutionAttempted` с идентификатором действия из внешней нагрузки, чтобы определить шаг, на котором сборка была успешно разрешена. На этот раз события покажут, что этап `AssemblyLoadContextResolvingEvent` был выполнен успешно. В поле `ResultAssemblyPath` отображается путь к итоговой сборке.

:::image type="content" source="media/collect-details/resolution-attempted-success.png" alt-text="Изображение успешных событий ResolutionAttempted в PerfView":::

| Имя события                           | AssemblyName                                      | Этап                               | Результат             | ResultAssemblyPath |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `Success`          | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |

При просмотре событий `AssemblyLoadContextResolvingHandlerInvoked` станет понятно, что был вызван обработчик с именем `OnAssemblyLoadContextResolving`. В поле `ResultAssemblyPath` отображается путь к сборке, возвращенной обработчиком.

:::image type="content" source="media/collect-details/extension-point-success.png" alt-text="Изображение успешных событий точки расширения в PerfView":::

| Имя события                                                  | AssemblyName                                      | HandlerName                      | ResultAssemblyPath |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- | ------------------ |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |

Обратите внимание, что событие `ResolutionAttempted` с этапом `AppDomainAssemblyResolveEvent` или какие-либо события `AppDomainAssemblyResolveHandlerInvoked` больше не существуют, так как сборка была успешно загружена до достижения шага алгоритма загрузки, вызывающего событие <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.

## <a name="see-also"></a>См. также раздел

- [События загрузчика сборок](../../fundamentals/diagnostics/runtime-loader-binder-events.md)
- [dotnet-trace](../diagnostics/dotnet-trace.md)
- [PerfView](https://github.com/microsoft/perfview)
