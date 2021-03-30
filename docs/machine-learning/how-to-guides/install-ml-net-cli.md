---
title: Установка средства ML.NET CLI
description: Узнайте, как установить, обновить, удалить средство ML.NET CLI, или вернутся к его предыдущей версии.
ms.date: 06/08/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: a2fdaa06c1602a2c3986b2f034cd1840e39d16a3
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876777"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>Установка средства ML.NET CLI

Узнайте, как установить ML.NET CLI (интерфейс командной строки) в Windows, Mac или Linux.

ML.NET CLI создает качественные модели ML.NET и исходный код с помощью автоматизированного машинного обучения (AutoML) и набора данных для обучения.

> [!NOTE]
> Этот раздел относится к ML.NET CLI и ML.NET AutoML, находящимся в данный момент в предварительной версии; материалы могут быть изменены.

## <a name="pre-requisites"></a>Предварительные требования

- [Пакет SDK для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1)

- (Необязательно) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)

Вы можете запускать проекты, написанные на C#, из Visual Studio по нажатию кнопки `F5` или с помощью `dotnet run` (.NET Core CLI).

Примечание. Если после установки пакета SDK для .NET Core команда `dotnet tool` не работает, выйдите из Windows и снова войдите в систему.

## <a name="install"></a>Установка

Средство ML.NET CLI устанавливается так же, как и любое другое глобальное средство .NET. Для этого используйте команду `dotnet tool install` .NET Core CLI.

В примере ниже показано, как установить ML.NET CLI в расположении веб-канала NuGet по умолчанию.

```dotnetcli
dotnet tool install -g mlnet
```

Если не удается установить средство (то есть оно недоступно в режиме по умолчанию веб-канала NuGet), отображаются сообщения об ошибках. Убедитесь, что установлены флажки для нужных веб-каналов.

Если установка выполнена успешно, отображается сообщение с командой, используемой для вызова средства, и установленной версией, аналогичное приведенному ниже:

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Можно проверить успешность установки, введя следующую команду:

```console
mlnet
```

Вы увидите справку для команд, доступных для средства mlnet, например для команды classification.

## <a name="install-a-specific-release-version"></a>Установка конкретного выпуска

Если вам необходимо установить предварительную или конкретную версию средства, можно указать [платформу](../../standard/frameworks.md), используя следующий формат:

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

Вы также можете проверить, был ли пакет установлен правильно, введя следующую команду:

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>Удаление пакета интерфейса командной строки

Введите следующую команду, чтобы удалить пакет с локального компьютера:

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>Обновление пакета интерфейса командной строки

Введите следующую команду, чтобы обновить пакет на локальном компьютере:

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>Настройка предложений CLI (автозавершение по нажатию TAB)

Так как средство ML.NET CLI основано на `System.CommandLine`, оно имеет встроенную поддержку нажатия клавиши TAB.

Пример того, как работает автоматическое завершение по нажатию клавиши TAB, см в следующей анимации:

![изображение](./media/cli-tab-completion.gif)

Автозавершение клавишей TAB (варианты параметров) работает в *Windows PowerShell* и *bash для macOS и Linux*, но не будет работать в *командной строке Windows*.

Чтобы включить его в текущей предварительной версии, конечный пользователь должен выполнить в каждой оболочке ряд однократных действий, описанных ниже. После этого варианты завершения будут работать для всех приложений, написанных с помощью `System.CommandLine`, например ML.NET CLI.

На компьютере, где вы хотите включить завершение, необходимо сделать две вещи.

1. Установите глобальное средство `dotnet-suggest`, запустив следующую команду:

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. Добавьте соответствующую оболочку совместимости к профилю оболочки. Может потребоваться создать файл профиля оболочки. Скрипт оболочки совместимости перенаправит запрос завершения из оболочки в средство `dotnet-suggest`, которое делегирует его в соответствующее `System.CommandLine`-приложение.

    - Для bash следует добавить содержимое [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/main/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) в `~/.bash_profile`.

    - Для PowerShell следует добавить содержимое [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/main/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) в свой профиль PowerShell. Ожидаемый путь к профилю PowerShell можно получить, выполнив следующую команду в консоли:

    ```console
    echo $profile
    ```

(В других оболочках [найдите](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) или откройте [соответствующее обращение](https://github.com/dotnet/System.CommandLine/issues).)

## <a name="installation-directory"></a>Каталог установки

ML.NET CLI можно установить в каталоге по умолчанию или в выбранном вами расположении. Каталоги по умолчанию:

| Операционная система          | Path                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Эти расположения добавляются в путь пользователя при первом запуске пакета SDK, поэтому установленные в них глобальные средства можно вызывать напрямую.

Обратите внимание, что глобальные средства входят в область конкретного пользователя, а не глобальную область компьютера. Таким образом, нельзя установить глобальное средство, которое будет доступно для всех пользователей компьютера. Средство доступно только для тех профилей пользователей, в которых оно установлено.

Глобальные средства также можно установить в конкретном каталоге. При установке в конкретном каталоге необходимо убедиться, что команда доступна, включив этот каталог в путь, вызвав команду с указанным каталогом или вызвав средство из указанного каталога.
В этом случае .NET Core CLI не добавляет это расположение автоматически в переменную среды PATH.

## <a name="see-also"></a>См. также

- [Обзор ML.NET CLI](../automate-training-with-cli.md)
- [Учебник. Проанализируйте тональность с помощью ML.NET CLI](../tutorials/sentiment-analysis-cli.md)
- [Справочное руководство по команде auto-train в ML.NET CLI](../reference/ml-net-cli-reference.md)
- [Данные телеметрии в интерфейсе командной строки ML.NET](../resources/ml-net-cli-telemetry.md)
