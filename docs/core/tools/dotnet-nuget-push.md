---
title: Команда dotnet nuget push
description: Команда dotnet nuget push отправляет пакет на сервер и публикует его.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 92e2593633343bda6990ca51d593455ff13f0df7
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478182"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Эта статья относится к следующему:** ✔️ пакет SDK для .NET Core 2.x и более поздних версий

## <a name="name"></a>name

`dotnet nuget push` — отправляет пакет на сервер и публикует его.

## <a name="synopsis"></a>Краткий обзор

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a>Описание

Команда `dotnet nuget push` отправляет пакет на сервер и публикует его. Команда push использует сервер и учетные данные, указанные в системном файле конфигурации NuGet или цепочке файлов конфигурации. См. дополнительные сведения о файлах конфигурации в статье о [настройке поведения NuGet](/nuget/consume-packages/configuring-nuget-behavior). Конфигурацию NuGet по умолчанию можно получить, загрузив файл *%AppData%\NuGet\NuGet.config* (Windows) или *$HOME/.local/share* (Linux и macOS). Затем нужно загрузить все файлы *nuget.config* или *.nuget\nuget.config*, начиная с корневого каталога диска и заканчивая текущим каталогом.

Команда отправляет существующий пакет. При этом пакет не создается. Для создания пакета используйте [`dotnet pack`](dotnet-pack.md).

## <a name="arguments"></a>Аргументы

- **`ROOT`**

  Указывает путь к файлу пакета для отправки.

## <a name="options"></a>Параметры

- **`-d|--disable-buffering`**

  Отключает буферизацию при передаче данных на сервер HTTP(S), чтобы снизить использование памяти.

- **`--force-english-output`**

  Принудительно запускает приложение с использованием инвариантного английского языка и региональных параметров.

- **`-h|--help`**

  Выводит краткую справку по команде.

- **`--interactive`**

  Позволяет блокировать команду до выполнения действия пользователем, например аутентификации. Параметр доступен, начиная с пакета SDK для .NET Core 2.2.

- **`-k|--api-key <API_KEY>`**

  Ключ API для сервера.

- **`-n|--no-symbols`**

  Не передает символы (даже если они присутствуют).

- **`--no-service-endpoint`**

  Не добавляет "api/v2/package" в исходный URL-адрес. Параметр доступен, начиная с пакета SDK для .NET Core 2.1.

- **`-s|--source <SOURCE>`**

  Определяет URL-адрес сервера. NuGet определяет источник в формате UNC или локальную папку и просто копирует файл вместо отправки через HTTP.
  > [!IMPORTANT]
  > Начиная с NuGet 3.4.2, этот параметр является обязательным, если в файле конфигурации NuGet не указано значение `DefaultPushSource`. Дополнительные сведения см. в статье [Configuring NuGet behavior](/nuget/consume-packages/configuring-nuget-behavior) (Настройка поведения NuGet).

- **`--skip-duplicate`**

  При принудительной отправке нескольких пакетов на сервер HTTP(S) обрабатывает любой ответ с кодом состояния 409 Conflict (конфликт) в виде предупреждения, чтобы можно было продолжить принудительную отправку. Доступно, начиная с пакета SDK для .NET Core 3.1.

- **`-sk|--symbol-api-key <API_KEY>`**

  Ключ API для сервера символов.

- **`-ss|--symbol-source <SOURCE>`**

  Указывает URL-адрес сервера символов.

- **`-t|--timeout <TIMEOUT>`**

  Указывает время ожидания для передачи на сервер в секундах. Значение по умолчанию — 300 секунд (5 минут). При указании 0 (ноль секунд) применяется значение по умолчанию.

## <a name="examples"></a>Примеры

- Отправляет *foo.nupkg* в источник push-уведомлений по умолчанию, указанный в файле конфигурации NuGet, используя ключ API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- Отправляет *foo.nupkg* на официальный сервер NuGet, предоставляя ключ API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * Отправляет *foo.nupkg* в пользовательский источник push-уведомлений `https://customsource`, предоставляя ключ API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- Отправляет *foo.nupkg* в источник push-уведомлений по умолчанию, указанный в файле конфигурации NuGet:

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- Отправляет *foo.symbols.nupkg* в источник символов по умолчанию:

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- Отправляет *foo.nupkg* в источник push-уведомлений по умолчанию, указанный в файле конфигурации NuGet, с временем ожидания 360 с:

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- Отправляет все файлы *NUPKG* из текущего каталога в источник push-уведомлений по умолчанию, указанный в файле конфигурации NuGet:

  ```dotnetcli
  dotnet nuget push "*.nupkg"
  ```

  > [!NOTE]
  > Если эта команда не работает, возможно, это связано с ошибкой, которая существовала в более старых версиях пакета SDK (пакет SDK для .NET Core 2.1 и более ранних версий).
  > Чтобы устранить эту проблему, обновите версию пакета SDK или выполните следующую команду: `dotnet nuget push "**/*.nupkg"`
  
  > [!NOTE]
  > Закрывающие кавычки необходимы для оболочек, таких как bash, выполняющих файл глобализации. Дополнительные сведения см. на странице [NuGet/Home#4393](https://github.com/NuGet/Home/issues/4393#issuecomment-667618120).

- Отправляет все файлы *NUPKG* в источник push-уведомлений по умолчанию, указанный в файле конфигурации NuGet, даже если сервер HTTP (S) возвращает в ответе конфликт 409:

  ```dotnetcli
  dotnet nuget push "*.nupkg" --skip-duplicate
  ```

- Отправляет все файлы *NUPKG* из текущего каталога в каталог локального веб-канала:

  ```dotnetcli
  dotnet nuget push "*.nupkg" -s c:\mydir
  ```

  Эта команда не сохраняет пакеты в иерархическую структуру папок, что рекомендуется для оптимизации производительности. Дополнительные сведения см. в разделе [Локальные веб-каналы](/nuget/hosting-packages/local-feeds).  
