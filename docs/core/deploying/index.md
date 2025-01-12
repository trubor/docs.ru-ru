---
title: Публикация приложений
description: Узнайте способы публикации приложений .NET. .NET позволяет публиковать приложения для конкретной платформы и кроссплатформенные приложения. Приложение можно опубликовать как автономное или как зависимое от среды. Каждый режим влияет на то, как пользователь запускает приложение.
ms.date: 02/05/2021
ms.openlocfilehash: ca0fa4ff5e17a3fa4c636604ae81b63ffbbc99f6
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874294"
---
# <a name="net-application-publishing-overview"></a>Общие сведения о публикации приложений .NET

Приложения .NET можно публиковать в двух разных режимах. Режим влияет на то, как пользователь запускает приложение.

При публикации *автономного* приложения в состав включается среда выполнения и библиотеки .NET, а также приложение и его зависимости. Пользователи приложения могут запустить его на компьютере, на котором не установлена среда выполнения .NET.

При публикации приложения в качестве *зависимого от среды* создается приложение, которое включает только само приложение и его зависимости. Пользователям приложения необходимо отдельно установить среду выполнения .NET.

Оба режима публикации по умолчанию создают исполняемый файл, зависящий от платформы. Приложения, зависящие от среды, могут создаваться без исполняемого файла, и эти приложения являются кросс-платформенными.

При создании исполняемого файла можно указать целевую платформу с идентификатором среды выполнения (RID). Дополнительные сведения об идентификаторах среды выполнения см. в [этом каталоге для .NET](../rid-catalog.md).

В следующей таблице приведены команды, используемые для публикации автономных и зависящих от среды для каждой версии пакета SDK:

| Type                                                                                     | SDK 2.1 | SDK 3.1 | SDK 5.0 | Команда |
| ---------------------------------------------------------------------------------------  | ------- | ------- | ------- | ------- |
| [зависящий от среды исполняемый файл](#publish-framework-dependent) для текущей платформы. |         | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [зависящий от среды исполняемый файл](#publish-framework-dependent) для определенной платформы.  |         | ✔️      | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [зависящий от среды кросс-платформенный двоичный файл](#publish-framework-dependent).               | ✔️      | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [автономный исполняемый файл](#publish-self-contained).                                    | ✔️      | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

Дополнительные сведения см. в статье о [команде dotnet publish для .NET](../tools/dotnet-publish.md).

## <a name="produce-an-executable"></a>Создание исполняемого файла

Исполняемые файлы не являются кроссплатформенными. Они относятся к операционной системе и архитектуре ЦП. При публикации приложения и создании исполняемого файла можно опубликовать приложение как [автономное](#publish-self-contained) или [зависящее от среды](#publish-framework-dependent). При публикации автономного приложения в пакет включается среда выполнения .NET, поэтому пользователям не нужно беспокоиться об установке .NET перед запуском приложения. Приложения, опубликованные как зависимые от среды, не предусматривают среду выполнения и библиотеки .NET. В пакет входят только приложение и сторонние зависимости.

Следующие команды создают исполняемый файл:

| Type                                                                                     | SDK 2.1 | SDK 3.1 | SDK 5.0 | Команда |
| ---------------------------------------------------------------------------------------- | ------- | ------- | ------- | ------- |
| [зависящий от среды исполняемый файл](#publish-framework-dependent) для текущей платформы. |         | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [зависящий от среды исполняемый файл](#publish-framework-dependent) для определенной платформы.  |         | ✔️      | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [автономный исполняемый файл](#publish-self-contained).                                    | ✔️      | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>Создание кроссплатформенного двоичного файла

Кросс-платформенные двоичные файлы создаются при публикации приложения, [зависящего от среды](#publish-framework-dependent), в виде файла *DLL*. Файл *DLL* называется по имени вашего проекта. Например, если ваше приложение называется **word_reader**, создается файл с именем *word_reader.dll*. Приложения, опубликованные таким образом, выполняются с помощью команды `dotnet <filename.dll>` на любой платформе.

Кроссплатформенные двоичные файлы могут работать в любой операционной системе, если целевая среда выполнения .NET уже установлена. Если же она не установлена, приложение может использовать для работы более новую среду выполнения, если настроено соответствующим образом. Дополнительные сведения см. в разделе [Накат зависящих от среды приложений](../versions/selection.md#framework-dependent-apps-roll-forward).

Следующая команда создает кроссплатформенный двоичный файл:

| Type                                                                                 | SDK 2.1 | SDK 3.x | SDK 5.0 | Команда |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- | ------- |
| [зависящий от среды кросс-платформенный двоичный файл](#publish-framework-dependent).           | ✔️      | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-framework-dependent"></a>Публикация зависящих от среды приложений

Приложения, опубликованные как зависящие от среды, являются кроссплатформенными и не включают среду выполнения .NET. Пользователю нужно будет установить среду выполнения .NET.

При публикации приложения, зависящего от среды, создается [кросс-платформенный двоичный файл](#produce-a-cross-platform-binary) с расширением *DLL* и [исполняемый файл, зависящий от платформы](#produce-an-executable), предназначенный для текущей платформы. Файл *DLL* является кроссплатформенным, а исполняемый файл — нет. Например, при публикации приложения с именем **word_reader** для Windows создается исполняемый файл *word_reader.exe* и файл *word_reader.dll*. Для Linux или macOS создается исполняемый файл *word_reader*, а также *word_reader.dll*. Дополнительные сведения об идентификаторах среды выполнения см. в [этом каталоге для .NET](../rid-catalog.md).

> [!IMPORTANT]
> Пакет SDK для .NET 2.1 не создает исполняемые файлы, зависящие от платформы, при публикации приложения, зависящего от среды.

Кроссплатформенный двоичный файл приложения можно запустить с помощью команды `dotnet <filename.dll>` и выполнять на любой платформе. Если приложение использует пакет NuGet с реализациями, зависящими от платформы, все зависимости платформ копируются в папку публикации вместе с приложением.

Вы можете создать исполняемый файл для конкретной платформы, передав параметры `-r <RID> --self-contained false` в команде [`dotnet publish`](../tools/dotnet-publish.md). Если параметр `-r` опущен, для текущей платформы создается исполняемый файл. Все пакеты NuGet, имеющие зависящие от платформы зависимости для целевой платформы, копируются в папку публикации. Если вам не нужен связанный с платформой исполняемый файл, можно указать `<UseAppHost>False</UseAppHost>` в файле проекта. Дополнительные сведения см. в статье [Справочник по MSBuild для проектов пакета SDK для .NET](../project-sdk/msbuild-props.md#useapphost).

### <a name="advantages"></a>Преимущества

- **Небольшое развертывание**\
Распределяются только приложение и его зависимости. Среду выполнения и библиотеки .NET устанавливает пользователь, и все приложения совместно используют среду выполнения.

- **Кроссплатформенные приложения**\
Ваше приложение и библиотеки на основе .NET работают в других операционных системах. Для приложения не нужно определять целевую платформу. Дополнительные сведения о формате файлов .NET см. в разделе [Формат файла сборки .NET](../../standard/assembly/file-format.md).

- **Использует последнюю исправленную версию среды выполнения**\
Приложение использует самую новую среду выполнения (в рамках целевого основного и дополнительного семейства .NET), установленную в целевой системе. Это означает, что приложение будет автоматически использовать последнюю исправленную версию среды выполнения .NET. Поведение по умолчанию можно переопределить. Дополнительные сведения см. в разделе [Накат зависящих от среды приложений](../versions/selection.md#framework-dependent-apps-roll-forward).

### <a name="disadvantages"></a>Недостатки

- **Требует предварительной установки среды выполнения**\
Приложение может выполняться, только если в системе, в которой оно размещено, уже установлена целевая версия .NET. Вы можете настроить поведение наката для приложения, чтобы либо требовать определенную версию .NET, либо разрешить более новую версию. Дополнительные сведения см. в разделе [Накат зависящих от среды приложений](../versions/selection.md#framework-dependent-apps-roll-forward).

- **.NET может измениться**\
Среду выполнения и библиотеки .NET можно обновлять на компьютере, где выполняется приложение. В редких случаях это может изменить поведение приложения, если используются библиотеки .NET, что характерно для большинства приложений. Вы можете настроить, как приложение будет использовать более новые версии .NET. Дополнительные сведения см. в разделе [Накат зависящих от среды приложений](../versions/selection.md#framework-dependent-apps-roll-forward).

Приведенные ниже недостатки применимы только к пакету SDK для .NET Core 2.1.

- **Используйте команду `dotnet`, чтобы запустить приложение**\
Для запуска приложения пользователи должны выполнить команду `dotnet <filename.dll>`. Пакет SDK для .NET Core 2.1 не создает исполняемые файлы, зависящие от платформы, при публикации приложения, зависящего от среды.

### <a name="examples"></a>Примеры

Публикация кросс-платформенного приложения, зависящего от среды. Исполняемый файл, предназначенный для текущей платформы, создается вместе с *DLL*-файлом.

```dotnet
dotnet publish
```

Публикация кросс-платформенного приложения, зависящего от среды. Вместе с *DLL*-файлом создается 64-разрядный исполняемый файл Linux. Эта команда не работает с пакетом SDK для .NET Core 2.1.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>Публикация автономных приложений

При публикации автономного приложения создается исполняемый файл, зависящий от платформы. Выходная папка публикации содержит все компоненты приложения, в том числе библиотеки .NET и целевую среду выполнения. Приложение изолировано от других приложений .NET и не использует локально установленную общую среду выполнения. Пользователю приложения не требуется скачивать и устанавливать .NET.

Исполняемый двоичный файл создается для указанной целевой платформы. Например, если у вас есть приложение с именем **word_reader** и вы публикуете автономный исполняемый файл для Windows, создается файл *word_reader.exe*. При публикации для Linux или macOS создается файл *word_reader*. Целевая платформа и архитектура указываются с помощью параметра `-r <RID>` для команды [`dotnet publish`](../tools/dotnet-publish.md). Дополнительные сведения об идентификаторах среды выполнения см. в [этом каталоге для .NET](../rid-catalog.md).

Если приложение имеет зависимости для определенной платформы, например пакет NuGet, содержащий зависимости для определенной платформы, они копируются в папку публикации вместе с приложением.

### <a name="advantages"></a>Преимущества

- **Управление версией .NET**\
Вы управляете тем, какая версия .NET развертывается вместе с приложением.

- **Нацеливание на конкретные платформы**\
Поскольку необходимо опубликовать приложение для каждой платформы, вы знаете, где будет выполняться приложение. Если в .NET появляется новая платформа, пользователи не смогут запустить приложение на ней до выпуска версии, предназначенной для этой платформы. Вы можете протестировать приложение на наличие проблем совместимости перед тем, как пользователи запустят приложение на новой платформе.

### <a name="disadvantages"></a>Недостатки

- **Более крупные развертывания**\
Так как приложение включает среду выполнения .NET и все зависимости приложения, размер скачиваемого файла и требуемого пространства на жестком диске будет больше, чем для версии, [зависящей от среды](#publish-framework-dependent).

  > [!TIP]
  > Вы можете уменьшить размер развертывания в системах Linux примерно на 28 МБ с помощью [*инвариантного режима глобализации*](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md) .NET. С его помощью приложение будет обрабатывать все языки и региональные параметры как [инвариантные языки и региональные параметры](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).

  > [!TIP]
  > Существует [предварительная версия функция усечения](trim-self-contained.md) позволяющая еще больше уменьшить размер развертывания.

- **Усложненное обновление версии .NET**\
Среду выполнения .NET (распространяемую с вашим приложением) можно обновить только путем выпуска новой версии приложения. Но при необходимости.NET обновит критически важные обновления системы безопасности для библиотеки платформы на компьютере, на котором выполняется приложение. Ответственность за полную проверку этого сценария обновления системы безопасности лежит на вас.

### <a name="examples"></a>Примеры

Публикация автономного приложения. Создается 64-разрядный исполняемый файл macOS.

```dotnet
dotnet publish -r osx-x64
```

Публикация автономного приложения. Создается 64-разрядный исполняемый файл Windows.

```dotnet
dotnet publish -r win-x64
```

## <a name="publish-with-readytorun-images"></a>Публикация с использованием образов ReadyToRun

Публикация с использованием образов ReadyToRun помогает оптимизировать время запуска приложения, хотя размер приложения при этом будет увеличен. Дополнительные сведения о публикации с использованием ReadyToRun см. [здесь](ready-to-run.md).

### <a name="advantages"></a>Преимущества

- **Оптимизированное времени запуска**\
Приложение будет тратить меньше времени на выполнение JIT.

### <a name="disadvantages"></a>Недостатки

- **Больший размер**\
Приложение будет занимать больше места на диске.

### <a name="examples"></a>Примеры

Опубликуйте автономное приложение с помощью ReadyToRun. Создается 64-разрядный исполняемый файл macOS.

```dotnet
dotnet publish -c Release -r osx-x64 -p:PublishReadyToRun=true
```

Опубликуйте автономное приложение с помощью ReadyToRun. Создается 64-разрядный исполняемый файл Windows.

```dotnet
dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
```

## <a name="see-also"></a>См. также

- [Развертывание приложений .NET с помощью .NET CLI](deploy-with-cli.md)
- [Развертывание приложений .NET с помощью Visual Studio](deploy-with-vs.md)
- [Каталог идентификаторов сред выполнения .NET](../rid-catalog.md)
- [Выбор версии .NET для использования](../versions/selection.md)
