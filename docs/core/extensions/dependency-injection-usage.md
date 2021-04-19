---
title: Использование внедрения зависимостей в .NET
description: Узнайте, как использовать внедрение зависимостей в приложениях .NET.
author: IEvangelist
ms.author: dapine
ms.date: 04/12/2021
ms.topic: tutorial
no-loc:
- Transient
- Scoped
- Singleton
- Example
ms.openlocfilehash: 03828496dfa3487ad70fac8cf32ff81844eca6fd
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494276"
---
# <a name="tutorial-use-dependency-injection-in-net"></a>Руководство. Использование внедрения зависимостей в .NET

В этом руководстве показано, как использовать [внедрение зависимостей в .NET](dependency-injection.md). Наряду с *расширениями Майкрософт* внедрение зависимостей является объектом первого класса, в котором службы добавляются и настраиваются в <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>. Интерфейс <xref:Microsoft.Extensions.Hosting.IHost> предоставляет собой экземпляр <xref:System.IServiceProvider>, который выступает в качестве контейнера всех зарегистрированных служб.

В этом руководстве описано следующее:

> [!div class="checklist"]
>
> - Создание консольного приложения .NET, использующего внедрение зависимостей
> - Создание и настройка [универсального узла](generic-host.md)
> - Написание нескольких интерфейсов и соответствующих реализаций
> - Использование времени существования службы и области для внедрения зависимостей

## <a name="prerequisites"></a>Предварительные требования

- [Пакет SDK для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии.
- Знакомство с созданием новых приложений .NET и установкой пакетов NuGet.

## <a name="create-a-new-console-application"></a>Создание нового консольного приложения

С помощью команды [dotnet new](../tools/dotnet-new.md) или мастера создания проектов в среде разработки создайте новое консольное приложение .NET с именем **ConsoleDI.Example** . Добавьте в проект пакет NuGet [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting).

## <a name="add-interfaces"></a>Добавление интерфейсов

Добавьте следующие интерфейсы в корень проекта:

*IOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

Интерфейс `IOperation` определяет одно свойство `OperationId`.

*ITransientOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::

*IScopedOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::

*ISingletonOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::

Все подынтерфейсы `IOperation` названы в соответствии с предполагаемым временем существования службы. Например, "Transient" или "Singleton".

## <a name="add-default-implementation"></a>Добавление реализации по умолчанию

Добавьте следующую реализацию по умолчанию для различных операций:

*DefaultOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

`DefaultOperation` реализует все интерфейсы именованной метки и инициализирует свойство `OperationId` последними четырьмя символами нового глобального уникального идентификатора (GUID).

## <a name="add-service-that-requires-di"></a>Добавление службы, требующей внедрения зависимостей

Добавьте следующий объект средства ведения журнала операций, который выступает в качестве службы для консольного приложения:

*OperationLogger.cs*

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

`OperationLogger` определяет конструктор, которому требуется каждый из вышеупомянутых интерфейсов метки, то есть `ITransientOperation`, `IScopedOperation` и `ISingletonOperation`. Объект предоставляет единственный метод, позволяющий потребителю записывать в журнал операции с заданным параметром `scope`. При вызове метод `LogOperations` записывает уникальный идентификатор каждой операции в строку и сообщение области.

## <a name="register-services-for-di"></a>Регистрация служб для внедрения зависимостей

Обновите файл *Program.cs*, используя следующий код:

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

Каждый метод расширения `services.Add{SERVICE_NAME}` добавляет (а потенциально и настраивает) службы. Рекомендуем придерживаться такого подхода в приложениях. Поместите методы расширения в пространство имен <xref:Microsoft.Extensions.DependencyInjection?displayProperty=fullName>, чтобы инкапсулировать группы зарегистрированных служб. Включение части `Microsoft.Extensions.DependencyInjection` пространства имен для методов расширения внедрения зависимостей также:

- позволяет отображать их в [IntelliSense](/visualstudio/ide/using-intellisense) без добавления дополнительных блоков `using`;
- позволяет избежать чрезмерного количества инструкций `using` в классе `Program` или `Startup`, из которого обычно вызываются эти методы расширения.

Приложение:

- создает экземпляр <xref:Microsoft.Extensions.Hosting.IHostBuilder> с [настройками привязки по умолчанию](generic-host.md#default-builder-settings);
- настраивает службы и добавляет их с соответствующим временем существования службы;
- вызывает метод <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> и назначает экземпляр <xref:Microsoft.Extensions.Hosting.IHost>;
- вызывает `ExemplifyScoping`, передавая <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType>.

## <a name="conclusion"></a>Заключение

Приложение отобразит выходные данные, аналогичные следующему примеру:

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
```

Из выходных данных приложения можно понять следующее.

- Операции Transient всегда различаются, при каждом извлечении службы создается новый экземпляр.
- Операции Scoped изменяются только с новой областью, но являются одним и тем же экземпляром в пределах области.
- Операции Singleton всегда одинаковы, новый экземпляр создается только один раз.

## <a name="see-also"></a>См. также раздел

* [Рекомендации по внедрению зависимостей](dependency-injection-guidelines.md)
* [Использование внедрения зависимостей в ASP.NET Core](/aspnet/core/fundamentals/dependency-injection)
