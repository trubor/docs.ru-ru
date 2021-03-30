---
title: Установка .NET в Windows
description: Сведения о версиях Windows, в которых возможна установка .NET.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 9b0c5c2ea26546a142029b730dfd38923231bae4
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873748"
---
# <a name="install-net-on-windows"></a>Установка .NET в Windows

> [!div class="op_single_selector"]
>
> - [Установка в Windows](windows.md)
> - [Установка в macOS](macos.md)
> - [Установка на Linux](linux.md)

В этой статье вы узнаете, как установить .NET в Windows. .NET состоит из среды выполнения и пакета SDK. Среда выполнения используется для запуска приложения .NET и может не включаться в состав приложения. Пакет SDK используется для создания приложений и библиотек .NET. Среда выполнения .NET всегда устанавливается вместе с пакетом SDK.

.NET 5.0 является последней версией.

> [!div class="button"]
> [Скачать .NET](https://dotnet.microsoft.com/download/dotnet)

## <a name="supported-releases"></a>Поддерживаемые выпуски

В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Windows, в которых они поддерживаются. Эти версии поддерживаются до окончания поддержки версии [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core), либо до окончания жизненного цикла версии [Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

Даты окончания жизненного цикла версий Windows 10 зависят от выпуска. В следующей таблице рассматриваются только выпуски **Домашняя**, **Профессиональная**, **Pro для образовательных учреждений** и **Pro для рабочих станций**. Дополнительные сведения см. в [справочных материалах по жизненному циклу поддержки Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

> [!TIP]
> Символ `+` представляет минимальную версию.

| Операционная система            | .NET Core 2.1 | .NET Core 3.1 | .NET 5 |
|-----------------------------|---------------|---------------|--------|
| Windows 10 или Windows Server версии 20H2    | ✔️           | ✔️            | ✔️    |
| Windows 10 или Windows Server версии 2004    | ✔️           | ✔️            | ✔️    |
| Windows 10 или Windows Server версии 1909    | ✔️           | ✔️            | ✔️    |
| Windows 10 или Windows Server версии 1903    | ✔️           | ✔️            | ✔️    |
| Windows 10, версия 1809    | ✔️           | ✔️            | ✔️    |
|  Windows 10, версия 1803    | ✔️           | ✔️            | ✔️    |
|  Windows 10, версия 1709    | ✔️           | ✔️            | ✔️    |
| Windows 10 (версия 1607)    | ✔️           | ✔️            | ✔️    |
| Windows 8.1                 | ✔️           | ✔️            | ✔️    |
| Windows 7 с пакетом обновления 1 (SP1), [ESU][esu]    | ✔️           | ✔️            | ✔️    |
| Windows Server 2019<br>Windows Server 2016<br>Windows Server 2012 R2<br>      | ✔️           | ✔️            | ✔️    |
| Windows Server Core 2012 R2 | ✔️           | ✔️            | ✔️    |
| Nano Server, версия 1809 и выше  | ✔️           | ✔️            | ✔️    |
| Nano Server, версия 1803   | ✔️           | ✔️            | ❌    |

## <a name="unsupported-releases"></a>Неподдерживаемые выпуски

Следующие версии .NET больше не поддерживаются (❌).

- 3.0
- 2.2
- 2.0

## <a name="runtime-information"></a>Сведения о среде выполнения

Среда выполнения используется для запуска приложений, созданных с помощью .NET. При публикации приложения автор может включить среду выполнения в его состав. В противном случае устанавливать среду выполнения будет пользователь.

В Windows можно установить три различные версии среды выполнения:

- *Среда выполнения ASP.NET Core*\
  Используется для запуска приложений ASP.NET Core. Включает среду выполнения .NET.

- *Среда выполнения для классических приложений*\
  Используется для запуска классических приложений .NET WPF и Windows Forms для Windows. Включает среду выполнения .NET.

- *Среда выполнения .NET*\
  Простейшая среда выполнения, в состав которой не входят какие-либо другие среды выполнения. Чтобы обеспечить максимальный уровень совместимости с приложениями .NET, настоятельно рекомендуется устанавливать *среду выполнения ASP.NET Core* и *среду выполнения для классических приложений*.

> [!div class="button"]
> [Загрузка среды выполнения .NET](https://dotnet.microsoft.com/download/dotnet)

## <a name="sdk-information"></a>Сведения о пакете SDK

Пакет SDK используется для создания и публикации приложений и библиотек .NET. При установке пакета SDK также устанавливаются все три [среды выполнения](#runtime-information): ASP.NET Core, компьютер и .NET.

## <a name="dependencies"></a>Зависимости

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[.NET 5.0](#tab/net50)

.NET 5.0 поддерживает следующие версии Windows:

> [!NOTE]
> Символ `+` представляет минимальную версию.

| Операционная система                  | Version       | Архитектуры   |
|---------------------|---------------|-----------------|
| Клиент Windows 10   | Версия 1607+ | x64, x86, ARM64 |
| Клиент Windows      | 7 с пакетом обновления 1 и более поздних версий (SP1+), 8.1   | x64, x86        |
| Windows Server      | 2012 R2+      | x64, x86        |
| Windows Server Core | 2012 R2+      | x64, x86        |
| Nano Server         | Версия 1809+ | X64             |

Дополнительные сведения об операционных системах, дистрибутивах и политике жизненного цикла, поддерживаемых .NET 5.0, см. в статье [Поддерживаемые .NET 5.0 версии ОС](https://github.com/dotnet/core/blob/main/release-notes/5.0/5.0-supported-os.md).

# <a name="net-core-31"></a>[.NET Core 3.1](#tab/netcore31)

.NET Core 3.1 поддерживает следующие версии Windows:

> [!NOTE]
> Символ `+` представляет минимальную версию.

| Операционная система                            | Version                        | Архитектуры   |
| ----------------------------- | ------------------------------ | --------------- |
| Клиент Windows                | 7 с пакетом обновления 1 и более поздних версий (SP1+), 8.1                    | x64, x86        |
| Клиент Windows 10             | Версия 1607+                  | x64, x86        |
| Windows Server                | 2012 R2+                       | x64, x86        |
| Nano Server                   | Версия 1803+                  | x64, ARM32      |

Дополнительные сведения об операционных системах, дистрибутивах и политике жизненного цикла, поддерживаемых .NET Core 3.1, см. в статье [Поддерживаемые .NET Core 3.1 версии ОС](https://github.com/dotnet/core/blob/main/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*Сейчас .NET Core 3.0 ❌ не поддерживается. Дополнительные сведения см. в статье о [политике поддержки .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

.NET Core 3.0 поддерживает следующие версии Windows:

> [!NOTE]
> Символ `+` представляет минимальную версию.

| Операционная система                            | Version                        | Архитектуры   |
| ----------------------------- | ------------------------------ | --------------- |
| Клиент Windows                | 7 с пакетом обновления 1 и более поздних версий (SP1+), 8.1                    | x64, x86        |
| Клиент Windows 10             | Версия 1607+                  | x64, x86        |
| Windows Server                | 2012 R2+                       | x64, x86        |
| Nano Server                   | Версия 1803+                  | x64, ARM32      |

Дополнительные сведения об операционных системах, дистрибутивах и политике жизненного цикла, поддерживаемых .NET Core 3.0, см. в статье [Поддерживаемые .NET Core 3.0 версии ОС](https://github.com/dotnet/core/blob/main/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*Сейчас .NET Core 2.2 ❌ не поддерживается. Дополнительные сведения см. в статье о [политике поддержки .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

.NET Core 2.2 поддерживает следующие версии Windows:

> [!NOTE]
> Символ `+` представляет минимальную версию.

| Операционная система                            | Version                        | Архитектуры   |
| ----------------------------- | ------------------------------ | --------------- |
| Клиент Windows                | 7 с пакетом обновления 1 и более поздних версий (SP1+), 8.1                    | x64, x86        |
| Клиент Windows 10             | Версия 1607+                  | x64, x86        |
| Windows Server                | 2008 R2 с пакетом обновления 1 или более поздней версии (SP1+)                   | x64, x86        |
| Nano Server                   | Версия 1803+                   | x64, ARM32      |

Дополнительные сведения об операционных системах, дистрибутивах и политике жизненного цикла, поддерживаемых .NET Core 2.2, см. в статье [Поддерживаемые .NET Core 2.2 версии ОС](https://github.com/dotnet/core/blob/main/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 поддерживает следующие версии Windows:

> [!NOTE]
> Символ `+` представляет минимальную версию.

| Операционная система                            | Version                        | Архитектуры   |
| ----------------------------- | ------------------------------ | --------------- |
| Клиент Windows                | 7 с пакетом обновления 1 и более поздних версий (SP1+), 8.1                    | x64, x86        |
| Клиент Windows 10             | Версия 1607+                  | x64, x86        |
| Windows Server                | 2008 R2 с пакетом обновления 1 или более поздней версии (SP1+)                   | x64, x86        |
| Nano Server                   | Версия 1803+                  | x64,            |

Дополнительные сведения об операционных системах, дистрибутивах и политике жизненного цикла, поддерживаемых .NET Core 2.1, см. в статье [Поддерживаемые .NET Core 2.1 версии ОС](https://github.com/dotnet/core/blob/main/release-notes/2.1/2.1-supported-os.md).

### <a name="offline-install-for-windows-7"></a>Автономная установка для Windows 7

При выполнении автономной установки платформы .NET Core 2.1 в Windows 7 необходимо сначала убедиться, что на целевом компьютере установлена актуальная версия [Центра корневой сертификации Microsoft 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm).

Средство _certmgr.exe_ позволяет автоматизировать установку сертификата и его получение из Visual Studio или Windows SDK. Следующая команда используется для установки сертификата перед запуском установщика платформы .NET Core 2.1:

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

Обязательно ознакомьтесь с зависимостями ниже, необходимыми для [Windows 7](#additional-deps).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2

При установке пакета SDK для .NET или среды выполнения .NET в следующих версиях Windows требуются дополнительные зависимости:

| Операционная система         | Предварительные требования                                                                    |
|--------------------------|----------------------------------------------------------------------------------|
| Windows 7 с пакетом обновления 1 (SP1), [ESU][esu] | – Распространяемый компонент Microsoft Visual C++ 2015–2019, [64-разрядный][vcc64] / [32-разрядный][vcc32] <br> – Обновление KB3063858, [64-разрядное][kb64] / [32-разрядное][kb32] <br> - [Центр корневой сертификации Microsoft 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) (только удаленный установщик .NET Core 2.1) |
| Windows Vista с пакетом обновления 2 (SP2)       | Распространяемый компонент Microsoft Visual C++ 2015–2019, [64-разрядный][vcc64] / [32-разрядный][vcc32] |
| Windows 8.1              | Распространяемый компонент Microsoft Visual C++ 2015–2019, [64-разрядный][vcc64] / [32-разрядный][vcc32] |
| Windows Server 2008 R2   | Распространяемый компонент Microsoft Visual C++ 2015–2019, [64-разрядный][vcc64] / [32-разрядный][vcc32] |
| Windows Server 2012 R2   | Распространяемый компонент Microsoft Visual C++ 2015–2019, [64-разрядный][vcc64] / [32-разрядный][vcc32] |

Приведенные выше требования также применяются, если возникает ошибка, связанная с любой из следующих библиотек DLL:

- *api-ms-win-crt-runtime-l1-1-0.dll*
- *api-ms-win-cor-timezone-l1-1-0.dll*
- *hostfxr.dll*

## <a name="install-with-powershell-automation"></a>Установка с помощью функции автоматизации PowerShell

[Сценарии dotnet-install](../tools/dotnet-install-script.md) используются для автоматизации непрерывной интеграции и ее осуществления без прав администратора. Вы можете скачать сценарий со [страницы справочника по сценариям dotnet-install](../tools/dotnet-install-script.md).

Этот сценарий по умолчанию устанавливает последнюю версию [с долгосрочной поддержкой (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core), которой сейчас является .NET Core 3.1. Вы можете выбрать конкретный выпуск, указав параметр `Channel`. Включите параметр `Runtime` для установки среды выполнения. В противном случае сценарий устанавливает пакет SDK.

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

Установите пакет SDK, опустив параметр `-Runtime`. В этом примере для параметра `-Channel` задано значение `Current`, которое определяет установку последней поддерживаемой версии.

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a>Установка с помощью Visual Studio

Если вы используете Visual Studio для разработки приложений .NET, в следующей таблице указана минимальная требуемая версия Visual Studio на основе целевой версии пакета SDK для .NET.

| Версия пакета SDK для .NET      | Версия Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 5,0                   | Visual Studio 2019 версии 16.8 или более поздней. |
| 3.1                   | Visual Studio 2019 версии 16.4 или более поздней. |
| 3.0                   | Visual Studio 2019 версии 16.3 или более поздней. |
| 2.2                   | Visual Studio 2017 версии 15.9 или более поздней. |
| 2.1                   | Visual Studio 2017 версии 15.7 или более поздней. |

Если среда Visual Studio уже установлена, вы можете проверить ее версию, выполнив указанные ниже действия.

01. Запустите Visual Studio.
01. Выберите **Справка** > **О Microsoft Visual Studio**.
01. Считайте номер версии из диалогового окна **О программе**.

Visual Studio может установить последнюю версию пакета SDK для .NET и среды выполнения .NET.

> [!div class="button"]
> [Скачайте Visual Studio.](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

### <a name="select-a-workload"></a>Выбор рабочей нагрузки

При установке или изменении Visual Studio выберите одну или несколько из следующих рабочих нагрузок в зависимости от типа создаваемого приложения:

- рабочая нагрузка **Кроссплатформенная разработка .NET Core** в разделе **Другие наборы инструментов**;
- рабочая нагрузка **ASP.NET и разработка веб-приложений** в разделе **Веб-разработка и облако**;
- рабочая нагрузка **Разработка для Azure** в разделе **Веб-разработка и облако**;
- рабочая нагрузка **Разработка классических приложений .NET** в разделе **Классические и мобильные**.

[![Windows Visual Studio 2019 с рабочей нагрузкой .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>Установка вместе с Visual Studio Code

Visual Studio Code — это эффективный и облегченный редактор исходного кода, который работает на компьютере. Visual Studio Code доступен для Windows, macOS и Linux.

Хотя Visual Studio Code не поставляется с автоматическим установщиком .NET Core, таким как Visual Studio, добавление поддержки .NET Core не вызывает затруднений.

01. [Скачайте и установите Visual Studio Code](https://code.visualstudio.com/Download).
01. [Скачайте и установите пакет SDK для .NET Core](https://dotnet.microsoft.com/download/dotnet).
01. [Установите расширение C# из Marketplace для Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

## <a name="windows-installer"></a>Установщик Windows

[Страница загрузки](https://dotnet.microsoft.com/download/dotnet) для .NET содержит исполняемые файлы установщика Windows.

При использовании установщиков Windows для установки .NET вы можете указать путь установки, задав параметры `DOTNETHOME_X64` и `DOTNETHOME_X86`.

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

Для установки .NET в автоматическом режиме, например, в рабочей среде, или для поддержки непрерывной интеграции, используйте следующие параметры:

- `/install`\
Устанавливает .NET.

- `/quiet`\
Предотвращает отображение любого пользовательского интерфейса и запросов.

- `norestart`\
Предотвращает все попытки перезапуска.

```console
dotnet-sdk-3.1.301-win-x64.exe /install /quiet /norestart
```

Дополнительные сведения смотрите в статье [Параметры командной строки стандартного установщика](/windows/win32/msi/standard-installer-command-line-options).

> [!TIP]
> В случае успешной установки установщик возвращает код 0; если требуется перезагрузка, установщик возвращает код 3010. Любое другое значение обычно является кодом ошибки.

## <a name="download-and-manually-install"></a>Скачивание и установка вручную

В качестве альтернативы установщикам Windows для .NET можно скачать и вручную установить пакет SDK или среду выполнения. Установка вручную как правило выполняется в рамках тестирования непрерывной интеграции. В большинстве случаев разработчикам и пользователям рекомендуется использовать [установщик](https://dotnet.microsoft.com/download/dotnet).

Как пакет SDK для .NET, так и среду выполнения .NET можно установить вручную после скачивания. При установке пакета SDK для .NET не нужно устанавливать соответствующую среду выполнения. Сначала скачайте двоичный выпуск пакета SDK или среды выполнения с одного из следующих сайтов:

- [Скачиваемые файлы для .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)
- [Скачиваемые файлы для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1)
- [Скачиваемые файлы для .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet/2.1)
- [Все скачиваемые файлы для .NET Core](https://dotnet.microsoft.com/download/dotnet)

Создайте каталог, в который будет выполнено извлечение .NET, например `%USERPROFILE%\dotnet`. Затем извлеките скачанный ZIP-файл в этот каталог.

По умолчанию команды и приложения .NET CLI не будут использовать платформу .NET, установленную таким образом. Вам нужно выбрать ее явно. Для этого измените переменные среды, с которыми запускается приложение:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

Такой подход позволяет установить несколько версий в отдельные расположения, а затем явно выбрать расположение установки, которое должно использовать приложение, запустив приложение с переменными среды, указывающими на это расположение.

Если параметр `DOTNET_MULTILEVEL_LOOKUP` имеет значение `0`, .NET игнорирует любые установленные глобально версии .NET. Если нужно, чтобы платформа .NET учитывала глобальное расположение установки по умолчанию при выборе лучшей платформы для запуска приложения, удалите этот параметр среды. По умолчанию обычно используется каталог `C:\Program Files\dotnet`, в который выполняется установка .NET при использовании установщика.

## <a name="docker"></a>Docker

Контейнеры обеспечивают простой способ изоляции приложения от остальной части основной системы. Контейнеры на одном компьютере совместно использую только ядро, а также используют ресурсы, которые передаются в приложение.

.NET можно выполнять в контейнере Docker. Официальные образы Docker для .NET публикуются в реестре контейнеров Microsoft (MCR), и доступ к ним можно получить в [репозитории Microsoft .NET Docker Hub](https://hub.docker.com/_/microsoft-dotnet). Каждый репозиторий содержит рабочие образы для разных сочетаний .NET (пакета SDK или среды выполнения) и операционной системы.

Корпорация Майкрософт предоставляет образы, которые предназначены для конкретных сценариев. Например [репозиторий ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-aspnet) содержит образы, которые предназначены для запуска приложений ASP.NET Core в рабочей среде.

Дополнительные сведения об использовании .NET в контейнере Docker см. в статьях [Введение в .NET и Docker](../docker/introduction.md) и [Примеры](https://github.com/dotnet/dotnet-docker/blob/main/samples/README.md).

## <a name="next-steps"></a>Дальнейшие действия

- [Проверка того, установлена ли платформа .NET](how-to-detect-installed-versions.md?pivots=os-windows).
- [Учебник. Hello World](../tutorials/with-visual-studio.md).
- [Учебник. Создание приложения с помощью Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Учебник. Контейнеризация приложения .NET Core](../docker/build-container.md).

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
[vcc64]: https://aka.ms/vs/16/release/vc_redist.x64.exe
[vcc32]: https://aka.ms/vs/16/release/vc_redist.x86.exe
[kb64]: https://www.microsoft.com/download/details.aspx?id=47442
[kb32]: https://www.microsoft.com/download/details.aspx?id=47409
