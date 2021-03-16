---
title: Непрерывная интеграция (CI) с использованием пакета SDK для .NET и его средств
description: Узнайте, как использовать пакет SDK для .NET и его средства на сервере сборки с непрерывной интеграцией.
ms.date: 05/18/2017
ms.openlocfilehash: fd1548f5c2d0a5191dd54c315c90a8ce3f8a5305
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103189999"
---
# <a name="using-the-net-sdk-and-tools-in-continuous-integration-ci"></a>Использование пакета SDK и средств .NET при непрерывной интеграции (CI)

В этой статье описывается использование пакета SDK для .NET и входящих в него средств на сервере сборки. Набор инструментов .NET поддерживает два режима: интерактивный (разработчик вводит команды в командной строке) и автоматический (сервер непрерывной интеграции выполняет скрипт сборки). Команды, параметры, входные и выходные данные совпадают. В этом случае нужно только указать способ получения средств и систему сборки приложения. В этом документе рассматриваются сценарии ввода в эксплуатацию средства обеспечения непрерывной интеграции, а также рекомендации по разработке и структуре скриптов сборки.

## <a name="installation-options-for-ci-build-servers"></a>Варианты установки для серверов сборки CI

### <a name="using-the-native-installers"></a>Использование собственных установщиков

В macOS, Linux и Windows доступны собственные установщики. Установщики требуют доступа администратора (sudo) к серверу сборки. Преимущество использования собственного установщика заключается в том, что он устанавливает собственные зависимости, необходимые для выполнения средства. Кроме того, собственные установщики обеспечивают системную установку пакета SDK.

Пользователи macOS должны использовать установщики PKG. В случае с Linux можно выбрать диспетчер пакетов на основе каналов, например apt-get для Ubuntu или yum для CentOS. Кроме того, можно использовать сами пакеты (DEB или RPM). Для платформ Windows можно использовать установщик MSI.

Последние надежные двоичные файлы можно найти на [странице скачиваемых файлов .NET](https://dotnet.microsoft.com/download). Чтобы использовать последние (возможно, ненадежные) предварительные выпуски средств, воспользуйтесь ссылками в [репозитории GitHub dotnet/core-sdk](https://github.com/dotnet/core-sdk#installers-and-binaries). Для дистрибутивов Linux также доступны архивы `tar.gz` (`tarballs`). Используйте вложенные в них скрипты, чтобы установить .NET Core.

### <a name="using-the-installer-script"></a>Использование скрипта установки

Скрипт установки позволяет выполнять установку на сервере сборки без прав администратора. Кроме того, с его помощью очень легко обеспечить автоматизацию. Скрипт самостоятельно скачивает средство и распаковывает его в стандартную или указанную папку. Вы также можете указать версию средства, которую следует установить, а также нужно ли установить пакет SDK целиком или только общую среду выполнения.

Работу скрипта установки можно автоматизировать в начале процесса сборки. Это позволяет получить и установить требуемую версию пакета SDK. *Требуемая версия* — это версия пакета SDK, необходимая в проектах для сборки. Этот скрипт позволяет установить пакет SDK в локальном каталоге на сервере, запустить средства из папки установки, а затем выполнить очистку после завершения сборки (очистку также может выполнить сервер непрерывной интеграции). Это обеспечивает инкапсуляцию и изоляцию процесса сборки. Ссылку на скрипт установки можно найти в статье о [dotnet-install](dotnet-install-script.md).

> [!NOTE]
> **Azure DevOps Services**
>
> При использовании скрипта установки собственные зависимости не устанавливаются автоматически. Их необходимо установить вручную, если их нет в операционной системе. Дополнительные сведения см. в статье [Зависимости и требования для .NET](../install/windows.md#dependencies).

## <a name="ci-setup-examples"></a>Примеры установки решений CI

В этом разделе приведены сведения о ручной настройке с помощью скрипта PowerShell или bash, а также описано несколько решений SaaS для непрерывной интеграции, таких как [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/) и [Azure Pipelines](/azure/devops/pipelines/index).

### <a name="manual-setup"></a>Ручная настройка

Каждая служба SaaS имеет собственные методы создания и настройки процесса сборки. Если вы используете другое решения SaaS, нежели упомянутые выше, или хотите внести дополнительные изменения, конфигурацию необходимо выполнить вручную.

Как правило, в процессе ручной настройки необходимо получить версию средства (или последнюю сборку) и выполнить скрипт сборки. Вы можете использовать скрипт PowerShell или bash, чтобы настроить команды .NET, а также файл проекта, который определяет процесс сборки. Подробные сведения об этих параметрах см. в разделе [Оркестрация сборки](#orchestrating-the-build).

После создания сценария, выполняющего ручную настройку сервера сборки CI, проверьте его на локальном компьютере разработки. Если проблем со скриптом не возникло, разверните его на сервере сборки CI. Ниже приведен относительно простой сценарий PowerShell, позволяющий получить пакет SDK для .NET и установить его на сервере сборки Windows:

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it
#   does, it's removed. This is not strictly required, but it's a
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://dot.net/v1/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

Сведения о реализации процесса сборки следует указать в конце скрипта. Скрипт получает средства, а затем выполняет процесс сборки. Ниже приведен скрипт bash, который выполняет те же действия, что и описанный выше сценарий PowerShell, он выполняется на компьютерах UNIX.

```bash
#!/bin/bash
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://dot.net/v1/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a>Travis CI

Средство [Travis CI](https://travis-ci.org/) можно настроить, чтобы установить пакет SDK для .NET с помощью языка `csharp` и ключа `dotnet`. Дополнительные сведения см. в официальной документации Travis CI по [созданию проектов C#, F# или Visual Basic](https://docs.travis-ci.com/user/languages/csharp/). Обратите внимание, что при доступе к сведениям сообщества Travis CI идентификатор языка `language: csharp` работает для всех языков .NET, в том числе F# и Mono.

Travis CI выполняет в *матрице сборки* как задания macOS, так и задания Linux. Вы можете указать сочетание среды выполнения, окружения, а также исключений и включений, чтобы охватить свои сочетания сборки приложения. Дополнительные сведения см. в статье о [настройке сборки](https://docs.travis-ci.com/user/customizing-the-build) в документации по Travis CI. Средства на основе MSBuild включают среды выполнения LTS (1.0.x) и текущие среды выполнения (1.1.x). Установив этот пакет SDK, вы получите все необходимые компоненты сборки.

### <a name="appveyor"></a>AppVeyor

Средство [AppVeyor](https://www.appveyor.com/) устанавливает рабочий образ сборки `Visual Studio 2017` с пакетом SDK для .NET Core 1.0.1. Доступны и другие образы сборки с разными версиями пакета SDK для .NET. Дополнительные сведения см. в [примере appveyor.yml](https://github.com/dotnet/docs/blob/main/appveyor.yml) и статье [о рабочих образах сборки](https://www.appveyor.com/docs/build-environment/#build-worker-images) в документации по AppVeyor.

Двоичные файлы пакета SDK для .NET загружаются в подкаталог и распаковываются в нем с помощью скрипта установки. Затем они добавляются в переменную среды `PATH`. Добавьте матрицу сборки, чтобы выполнить тесты интеграции с разными версиями пакета SDK для .NET:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a>Azure DevOps Services

Настройте Azure DevOps Services, чтобы создавать проекты .NET, используя один из следующих подходов:

1. Выполнение скрипта из раздела [Ручная настройка](#manual-setup) с использованием собственных команд.
1. Создание сборки, состоящей из нескольких встроенных задач сборки Azure DevOps Services, которые используют средства .NET.

Оба решения допустимые. С помощью скрипта ручной настройки можно управлять версиями средства, полученными в процессе сборки. Сборка выполняется с помощью скрипта, который необходимо создать. В этой статье описывается только создание вручную. Дополнительные сведения о создании сборки с помощью задач сборки Azure DevOps Services см. в документации по [Azure Pipelines](/azure/devops/pipelines/index).

Чтобы использовать скрипт ручной настройки в Azure DevOps Services, создайте определение сборки и укажите скрипт, выполняющий этап сборки. Это можно сделать с помощью пользовательского интерфейса Azure DevOps Services:

1. Сначала создайте определение сборки. Когда появится окно определения типа создаваемой сборки, выберите параметр **Пусто**.

   ![Выбор пустого определения сборки](./media/using-ci-with-cli/select-empty-build-definition.png)

1. После настройки репозитория сборки откроется окно "Определения сборок". Выберите **Добавить шаг сборки**:

   ![Добавление шага сборки](./media/using-ci-with-cli/add-build-step.png)

1. После этого откроется **каталог задач**. В нем содержатся задачи, используемые в сборке. Так как у вас есть скрипт, нажмите кнопку **Добавить** рядом с параметром **PowerShell: Запуск скрипта PowerShell**.

   ![Добавление этапа сценария PowerShell](./media/using-ci-with-cli/add-powershell-script.png)

1. Настройте сервер сборки. Добавьте скрипт из репозитория, для которого выполняется сборка:

   ![Указание выполняемого сценария PowerShell](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a>Оркестрация сборки

Большая часть статьи посвящена тому, как получить средства .NET и настроить различные службы CI. Оркестрация или *фактическое создание* кода с помощью .NET Core до этого момента не упоминались. Способ структурирования процесса сборки зависит от многих факторов, которые нельзя здесь описать в общем виде. Дополнительные сведения об оркестрации сборок на основе каждой упомянутой в этой статье технологии, а также ресурсы и примеры см. в документации по [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/) и [Azure Pipelines](/azure/devops/pipelines/index).

Два принципиальных подхода структурирования процесса сборки кода .NET с использованием средств .NET заключаются в использовании MSBuild напрямую или с помощью программ командной строки .NET. Выберите подход, который проще и удобнее для вас. MSBuild предоставляет возможность представить процесс сборки в виде задач и целевых объектов, но сложность этого подхода заключается в необходимости изучения синтаксиса файла проекта MSBuild. Подход с использованием программ командной строки .NET, возможно, проще, но в этом случае следует написать логику оркестрации на языке написания скриптов, например `bash` или PowerShell.

## <a name="see-also"></a>См. также раздел

- [Скачиваемые файлы .NET для Linux](https://dotnet.microsoft.com/download?initial-os=linux)
