---
title: Средство диагностики dotnet-sos — .NET CLI
description: Узнайте, как установить и использовать средство CLI dotnet-sos для управления расширением отладчика SOS, которое используется с собственными отладчиками в Windows и Linux.
ms.date: 11/17/2020
ms.topic: reference
ms.openlocfilehash: 83458ac0933034886dee51e0258acaeef9a8ed89
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740596"
---
# <a name="sos-installer-dotnet-sos"></a>Установщик SOS (dotnet-sos)

**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий

## <a name="install"></a>Установка

Есть два способа загрузки и установки `dotnet-sos`:

- **Средство dotnet global:**

  Чтобы установить последнюю версию [пакета NuGet](https://www.nuget.org/packages/dotnet-sos) `dotnet-sos`, используйте команду [dotnet tool install](../tools/dotnet-tool-install.md).

  ```dotnetcli
  dotnet tool install --global dotnet-sos
  ```

- **Прямое скачивание:**

  скачайте исполняемый файл средства, соответствующий вашей платформе:

  | OS  | Платформа |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [arm](https://aka.ms/dotnet-sos/win-arm) \| [arm-x64](https://aka.ms/dotnet-sos/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-sos/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-sos/linux-x64) \| [arm](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64) |

## <a name="synopsis"></a>Краткий обзор

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a>Описание

Глобальное средство `dotnet-sos` устанавливает [расширение отладчика SOS](sos-debugging-extension.md). Это расширение позволяет проверять управляемое состояние .NET Core из отладчиков машинного кода, таких как lldb и windbg.

> [!NOTE]
> Установка SOS с помощью средства `dotnet-sos` требуется только в Linux или macOS.  Это также может потребоваться в Windows, если вы используете старые средства отладки. Последние версии [Отладчика Windows](/windows-hardware/drivers/debugger/debugger-download-tools) (версии WinDbg или CDB >= 10.0.18317.1001) автоматически загружают SOS из коллекции расширений Майкрософт.  

## <a name="options"></a>Параметры

- **`--version`**

  Отображение сведений о версии.

- **`-h|--help`**

  Отображение справки в командной строке.

## <a name="dotnet-sos-install"></a>dotnet-sos install

Установка [расширения SOS](sos-debugging-extension.md) локально для отладки процессов .NET Core. В macOS и Linux файл *LLDBINIT* будет обновлен таким образом, чтобы расширение загружалось автоматически при запуске lldb. При установке SOS в Windows с более старыми средствами отладки (ниже версии 10.0.18317.1001) необходимо вручную загрузить расширение в WinDbg или CDB, запустив `.load %USERPROFILE%\.dotnet\sos\sos.dll` в отладчике.

### <a name="synopsis"></a>Краткий обзор

```console
dotnet-sos install [--architecture <arch>]
```

### <a name="options"></a>Параметры

- **`--architecture <arch>`**

  Задает архитектуру процессора для устанавливаемых двоичных файлов SOS. По умолчанию средство `dotnet-sos` устанавливает архитектуру хост-компьютера. Используйте этот параметр, если необходимо установить SOS для архитектуры, отличной от архитектуры узла dotnet. Например, если вы запускаете двоичные файлы Arm32 на узле Arm64, необходимо установить SOS командой `dotnet-sos install --architecture Arm`.

  Доступны следующие архитектуры:

  - `Arm`
  - `Arm64`
  - `X86`
  - `X64`

## <a name="dotnet-sos-uninstall"></a>dotnet-sos uninstall

Удаление [расширения SOS](sos-debugging-extension.md), а в Linux и macOS также удаление из конфигурации lldb.

### <a name="synopsis"></a>Краткий обзор

```console
dotnet-sos uninstall
```
