---
title: Команда dotnet nuget verify
description: Команда otnet nuget verify проверяет подписанный пакет.
author: kartheekp-ms
ms.date: 10/08/2020
ms.openlocfilehash: 1c300e5a09b4049a9895b9b3f6c742f701dc2200
ms.sourcegitcommit: 985c603cb21a085f8a8105f34ff5b87a44b76ab4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107564848"
---
# <a name="dotnet-nuget-verify"></a>dotnet nuget verify

**Эта статья относится к следующему:** ✔️ пакет SDK для .NET 5.0.100-rc.2.x и более поздних версий

## <a name="name"></a>Имя

`dotnet nuget verify` — проверяет подписанный пакет NuGet.

## <a name="synopsis"></a>Краткий обзор

```dotnetcli
dotnet nuget verify [<package-path(s)>]
    [--all]
    [--certificate-fingerprint <FINGERPRINT>]
    [-v|--verbosity <LEVEL>]

dotnet nuget verify -h|--help
```

## <a name="description"></a>Описание

Команда `dotnet nuget verify` проверяет подписанный пакет NuGet.

## <a name="arguments"></a>Аргументы

- **`package-path(s)`**

  Указывает путь к файлу проверяемого пакета. Для проверки нескольких пакетов можно передать несколько аргументов с расположением.

## <a name="options"></a>Параметры

- **`--all`**

  Указывает, что для пакетов нужно выполнить все возможные проверки. По умолчанию проверяются только `signatures`.

> [!NOTE]
> В настоящее время эта команда поддерживает только проверку `signature`.

- **`--certificate-fingerprint <FINGERPRINT>`**

  Убедитесь, что сертификат подписавшего лица совпадает с одним из указанных отпечатков `SHA256`. Этот параметр можно указать несколько раз, чтобы предоставить несколько отпечатков.

* **`-v|--verbosity <LEVEL>`**

  Задает [уровень детализации MSBuild](/visualstudio/msbuild/obtaining-build-logs-with-msbuild#verbosity-settings). Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`. Значение по умолчанию — `minimal`.

    В следующей таблице показано, что отображается для каждого уровня детализации.

                                      | `q[uiet]` | `m[inimal]` | `n[ormal]` | `d[etailed]` | `diag[nostic]`
    ----------------------------------| --------- | ----------- | ---------- | -----------| --------------
    `Certificate chain Information`   | ❌       | ❌          | ❌         | ✔️         | ✔️
    `Path to package being verified`  | ❌       | ❌          | ✔️         | ✔️         | ✔️
    `Hashing algorithm used for signature`        | ❌       | ❌          | ✔️         | ✔️         | ✔️
    `Author/Repository Certificate -> SHA1 hash`| ❌       | ❌          | ✔️         | ✔️         | ✔️
    `Author/Repository Certificate -> Issued By`| ❌       | ❌          | ✔️         | ✔️         | ✔️
    `Timestamp Certificate -> Issued By`| ❌       | ❌          | ✔️         | ✔️         | ✔️
    `Timestamp Certificate -> SHA-256 hash`| ❌       | ❌          | ✔️         | ✔️         | ✔️
    `Timestamp Certificate -> Validity period`| ❌       | ❌          | ✔️         | ✔️         | ✔️
    `Timestamp Certificate -> SHA1 hash`| ❌       | ❌          | ✔️         | ✔️         | ✔️
    `Timestamp Certificate -> Subject name`| ❌       | ❌          | ✔️         | ✔️         | ✔️
    `Author/Repository Certificate -> Subject name`| ❌       | ✔️          | ✔️         | ✔️         | ✔️
    `Author/Repository Certificate -> SHA-256 hash`| ❌       | ✔️          | ✔️         | ✔️         | ✔️
    `Author/Repository Certificate -> Validity period`| ❌       | ✔️          | ✔️         | ✔️         | ✔️
    `Author/Repository Certificate -> Service index URL (If applicable)`| ❌       | ✔️          | ✔️         | ✔️         | ✔️
    `Package name being verified`                    | ❌       | ✔️          | ✔️         | ✔️         | ✔️
    `Type of signature (author or repository)`| ❌       | ✔️          | ✔️         | ✔️         | ✔️

    ❌ указывает сведения, которые **не отображаются**. ✔️ указывает сведения, которые будут отображаться.

* **`-h|--help`**

  Выводит краткую справку по команде.

## <a name="examples"></a>Примеры

- Проверка *foo.nupkg*.

  ```dotnetcli
  dotnet nuget verify foo.nupkg
  ```

- Проверка нескольких пакетов NuGet: *foo.nupkg* и *всех файлов .nupkg в указанном каталоге*.

  ```dotnetcli
  dotnet nuget verify foo.nupkg c:\mydir\*.nupkg
  ```

- Проверка того, что сигнатура *foo.nupkg* соответствует указанному отпечатку сертификата.

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039
  ```

- Проверка того, что сигнатура *foo.nupkg* соответствует одному из указанных отпечатков сертификата.

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039 --certificate-fingerprint EC10992GG5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E027
  ```
