---
title: Поставщики конфигурации в .NET
description: Узнайте, как использовать API поставщика конфигурации для настройки приложений .NET.
author: IEvangelist
ms.author: dapine
ms.date: 03/08/2021
ms.openlocfilehash: 5f248c93de1773a8bbe8209f002806fb196bb260
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605013"
---
# <a name="configuration-providers-in-net"></a>Поставщики конфигурации в .NET

Конфигурацию в .NET можно выполнять с помощью с поставщиков конфигурации. Существует несколько типов поставщиков в зависимости от различных источников конфигурации. В этой статье подробно описаны различные поставщики конфигурации и соответствующие им источники.

- [Поставщик конфигурации файла](#file-configuration-provider)
- [Поставщик конфигурации переменных среды](#environment-variable-configuration-provider)
- [Поставщик конфигурации командной строки](#command-line-configuration-provider)
- [Поставщик конфигурации ключа для каждого файла](#key-per-file-configuration-provider)
- [Поставщик конфигурации памяти](#memory-configuration-provider)

## <a name="file-configuration-provider"></a>Поставщик конфигурации файла

<xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> является базовым классом для загрузки конфигурации из файловой системы. Следующие поставщики конфигурации являются производными от `FileConfigurationProvider`:

- [Поставщик конфигурации JSON](#json-configuration-provider)
- [Поставщик конфигурации XML](#xml-configuration-provider)
- [Поставщик конфигурации INI](#ini-configuration-provider)

### <a name="json-configuration-provider"></a>Поставщик конфигурации JSON

Класс <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> загружает конфигурацию из JSON-файла. Установите пакет NuGet [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json).

Перегрузки могут указывать:

- является ли файл обязательным или нет;
- будет ли перезагружена конфигурация, если файл изменится.

Рассмотрим следующий код.

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="1-39,43-44" highlight="23-29":::

Предыдущий код:

- Удаляет всех существующих поставщиков конфигурации, добавленных по умолчанию в метод <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])>.
- Настраивает поставщика конфигурации JSON для загрузки файлов *appsettings.json* и *appsettings*.`Environment`.*json* со следующими параметрами:
  - `optional: true`. Файл является необязательным.
  - `reloadOnChange: true`: При сохранении изменений файл перезагружается.

Параметры JSON переопределяются параметрами в [поставщике конфигурации переменных среды](#environment-variable-configuration-provider) и [поставщике конфигурации командной строки](#command-line-configuration-provider).

Ниже приведен пример файла *appsettings.json* с различными параметрами конфигурации.

:::code language="json" source="snippets/configuration/console-json/appsettings.json":::

Из экземпляра <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> после добавления поставщиков конфигурации можно вызвать <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> для получения объекта <xref:Microsoft.Extensions.Configuration.IConfigurationRoot>. Корневой элемент конфигурации представляет корень иерархии конфигурации. Разделы из конфигурации можно привязать к экземплярам объектов .NET, а затем предоставлять в виде <xref:Microsoft.Extensions.Options.IOptions%601> через внедрение зависимостей.

Рассмотрим класс `TransientFaultHandlingOptions`, определенный следующим образом:

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs":::

Следующий код создает корень конфигурации, привязывает раздел к типу класса `TransientFaultHandlingOptions` и выводит привязанные значения в окно консоли:

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

Приложение запишет следующий пример выходных данных:

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="40-42":::

### <a name="xml-configuration-provider"></a>Поставщик конфигурации XML

Класс <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> загружает конфигурацию из XML-файла во время выполнения. Установите пакет NuGet [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml).

В следующем примере кода демонстрируется конфигурация XML-файлов с помощью поставщика конфигурации XML.

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="1-34,52,58-59" highlight="23-34":::

Предыдущий код:

- Удаляет всех существующих поставщиков конфигурации, добавленных по умолчанию в метод <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])>.
- Настраивает поставщика конфигурации XML для загрузки файлов *appsettings.xml* и *repeating-example.xml* со следующими параметрами:
  - `optional: true`. Файл является необязательным.
  - `reloadOnChange: true`: При сохранении изменений файл перезагружается.
- Настраивает поставщика конфигурации переменных среды.
- Настраивает поставщик конфигурации командной строки, если переданный элемент `args` содержит аргументы.

Параметры XML переопределяются параметрами в [поставщике конфигурации переменных среды](#environment-variable-configuration-provider) и [поставщике конфигурации командной строки](#command-line-configuration-provider).

Ниже приведен пример файла *appsettings.xml* с различными параметрами конфигурации:

:::code language="xml" source="snippets/configuration/console-xml/appsettings.xml":::

Повторяющиеся элементы, использующие то же имя элемента, работают, если атрибут `name` используется для различения элементов.

:::code language="xml" source="snippets/configuration/console-xml/repeating-example.xml":::

Следующий код считывает предыдущий файл конфигурации и отображает ключи и значения:

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="36-51":::

Приложение запишет следующий пример выходных данных:

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="53-57":::

Атрибуты можно использовать для предоставления значений.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <key attribute="value" />
  <section>
    <key attribute="value" />
  </section>
</configuration>
```

Предыдущий файл конфигурации загружает следующие ключи с помощью `value`.

- `key:attribute`
- `section:key:attribute`

### <a name="ini-configuration-provider"></a>Поставщик конфигурации INI

Класс <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> загружает конфигурацию из INI-файла во время выполнения. Установите пакет NuGet [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini).

Следующий код очищает всех поставщиков конфигурации и добавляет `IniConfigurationProvider` с двумя INI-файлами в качестве источника:

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="1-37,44-45" highlight="24-30":::

Ниже приведен пример файла *appsettings.ini* с различными параметрами конфигурации:

:::code language="ini" source="snippets/configuration/console-ini/appsettings.ini":::

Следующий код отображает приведенные выше параметры конфигурации, записывая их в окно консоли:

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="32-36":::

Приложение запишет следующий пример выходных данных:

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="38-43":::

## <a name="environment-variable-configuration-provider"></a>Поставщик конфигурации переменных среды

При использовании конфигурации по умолчанию <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> загружает конфигурацию из пар "ключ-значение" в переменных среды после чтения файлов *appsettings.json*, *appsettings.* `Environment` *.json* и диспетчера секретов. Поэтому значения ключей, считанные из среды, переопределяют значения, считанные из *appsettings.json*, *appsettings.* `Environment` *.json* и диспетчера секретов.

Разделитель `:` не работает с иерархическими ключами переменных среды на всех платформах. Двойной знак подчеркивания (`__`) автоматически заменяется на `:` и поддерживается на всех платформах. Например, разделитель `:` не поддерживается [Bash](https://linuxhint.com/bash-environment-variables), а `__` — поддерживается.

Следующие команды `set`:

- Задают ключи и значения среды в предыдущем примере в Windows.
- Проверяют параметры, изменив их значения по умолчанию. Команда `dotnet run` должна выполняться в каталоге проекта.

```dotnetcli
set SecretKey="Secret key from environment"
set TransientFaultHandlingOptions__Enabled="true"
set TransientFaultHandlingOptions__AutoRetryDelay="00:00:13"

dotnet run
```

Предыдущие параметры среды:

- Задаются только в процессах, запускаемых из командного окна, в котором они были установлены.
- Не будут считываться веб-приложениями, запущенными в Visual Studio.

Следующие команды [setx](/windows-server/administration/windows-commands/setx) можно использовать для задания ключей и значений среды в Windows. В отличие от `set`, параметры `setx` сохраняются. `/M` задает переменную в системной среде. Если параметр `/M` не используется, задается переменная среды пользователя.

```dotnetcli
setx SecretKey "Secret key from setx environment" /M
setx TransientFaultHandlingOptions__Enabled "true" /M
setx TransientFaultHandlingOptions__AutoRetryDelay "00:00:05" /M

dotnet run
```

Чтобы проверить, что предыдущие команды переопределяют *appsettings.json* и *appsettings.* `Environment` *.json*, выполните следующие действия:

- В Visual Studio: Выйдите из среды Visual Studio и перезапустите ее.
- В CLI: Откройте новое командное окно и введите `dotnet run`.

Вызовите <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> со строкой, чтобы указать префикс для переменных среды:

:::code language="csharp" source="snippets/configuration/console-env/Program.cs" highlight="21-22":::

В приведенном выше коде:

- `config.AddEnvironmentVariables(prefix: "CustomPrefix_")` добавляется после поставщиков конфигурации по умолчанию. Пример упорядочивания поставщиков конфигурации см. в разделе [Поставщик конфигурации XML](#xml-configuration-provider).
- Переменные среды, установленные с префиксом `CustomPrefix_`, переопределяют поставщиков конфигурации по умолчанию. Сюда входят переменные среды без префикса.

Префикс отделяется при создании пары конфигурации "ключ-значение".

Следующие команды проверяют пользовательский префикс:

```dotnetcli
set CustomPrefix__SecretKey="Secret key with CustomPrefix_ environment"
set CustomPrefix__TransientFaultHandlingOptions__Enabled=true
set CustomPrefix__TransientFaultHandlingOptions__AutoRetryDelay=00:00:21

dotnet run
```

Конфигурация по умолчанию загружает переменные среды и аргументы командной строки с префиксом `DOTNET_`. Префикс `DOTNET_` используется .NET для конфигурации [узла](generic-host.md#host-configuration) и [приложения](generic-host.md#app-configuration), но не для конфигурации пользователя.

Дополнительные сведения о конфигурации узла и приложения см. в разделе [Универсальный узел .NET](generic-host.md).

В [Службе приложений Azure](https://azure.microsoft.com/services/app-service) выберите **Новый параметр приложения** на странице **Параметры > Конфигурация**. Параметры приложения Службы приложений Azure:

- Шифруются, когда они неактивны, и передаются по зашифрованному каналу.
- Предоставляются как переменные среды.

### <a name="connection-string-prefixes"></a>Префиксы строк подключения

API конфигурации имеет особые правила обработки для четырех переменных среды строки подключения. Эти строки подключения участвуют в настройке строк подключения Azure для среды приложения. Переменные среды с префиксами, указанными в таблице, загружаются в приложение с конфигурацией по умолчанию или если префикс не предоставлен для `AddEnvironmentVariables`.

| Префикс строки подключения | Поставщик                                                                |
|--------------------------|-------------------------------------------------------------------------|
| `CUSTOMCONNSTR_`         | Поставщик пользователя                                                         |
| `MYSQLCONNSTR_`          | [MySQL](https://www.mysql.com)                                          |
| `SQLAZURECONNSTR_`       | [База данных SQL Azure](https://azure.microsoft.com/services/sql-database) |
| `SQLCONNSTR_`            | [SQL Server](https://www.microsoft.com/sql-server)                      |

Когда переменная среды обнаруживается и загружается в конфигурацию с одним из четырех префиксов, приведенных в таблице, происходит следующее.

- Ключ конфигурации создается путем удаления префикса переменных среды и добавления ключа раздела конфигурации (`ConnectionStrings`).
- Создается новая пара "ключ — значение" конфигурации, которая представляет поставщика подключения базы данных (за исключением `CUSTOMCONNSTR_`, который не имеет указанного поставщика).

| Ключ переменной среды | Преобразованный ключ конфигурации | Запись конфигурации поставщика                                                    |
|--------------------------|-----------------------------|---------------------------------------------------------------------------------|
| `CUSTOMCONNSTR_{KEY}`    | `ConnectionStrings:{KEY}`   | Запись конфигурации не создана.                                                |
| `MYSQLCONNSTR_{KEY}`     | `ConnectionStrings:{KEY}`   | Ключ: `ConnectionStrings:{KEY}_ProviderName`:<br>Значение: `MySql.Data.MySqlClient` |
| `SQLAZURECONNSTR_{KEY}`  | `ConnectionStrings:{KEY}`   | Ключ: `ConnectionStrings:{KEY}_ProviderName`:<br>Значение: `System.Data.SqlClient`  |
| `SQLCONNSTR_{KEY}`       | `ConnectionStrings:{KEY}`   | Ключ: `ConnectionStrings:{KEY}_ProviderName`:<br>Значение: `System.Data.SqlClient`  |

### <a name="environment-variables-set-in-launchsettingsjson"></a>Переменные среды, заданные в launchSettings.json

Переменные среды, заданные в *launchSettings.json*, переопределяют переменные, заданные в системной среде.

## <a name="command-line-configuration-provider"></a>Поставщик конфигурации командной строки

При использовании конфигурации по умолчанию <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> загружает конфигурацию из пар "ключ-значение" аргументов командной строки после следующих источников конфигурации:

- Файлы *appsettings.json* и *appsettings*.`Environment`.*json*.
- Секреты приложения (диспетчер секретов) в среде `Development`.
- Переменные среды.

По умолчанию значения конфигурации, заданные для значений конфигурации переопределения в командной строке, задаются для всех остальных поставщиков конфигурации.

### <a name="command-line-arguments"></a>аргументов командной строки;

Следующая команда задает ключи и значения с помощью `=`:

```dotnetcli
dotnet run SecretKey="Secret key from command line"
```

Следующая команда задает ключи и значения с помощью `/`:

```dotnetcli
dotnet run /SecretKey "Secret key set from forward slash"
```

Следующая команда задает ключи и значения с помощью `--`:

```dotnetcli
dotnet run --SecretKey "Secret key set from double hyphen"
```

Значение ключа:

- Должно соответствовать `=`, или ключ должен иметь префикс `--` или `/`, когда значение следует за пробелом.
- Является обязательным, если используется параметр `=`. Например, `SomeKey=`.

В рамках одной и той же команды не смешивайте пары "ключ-значение" аргумента командной строки, которые используют `=` с парами "ключ-значение" с пробелом.

## <a name="key-per-file-configuration-provider"></a>Поставщик конфигурации ключа для каждого файла

<xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> использует файлы каталога как пары "ключ — значение" конфигурации. Ключ является именем файла. Значением является содержимое файла. Поставщик конфигурации ключа для каждого файла используется в сценариях размещения Docker.

Чтобы активировать конфигурацию ключа для каждого файла, вызовите метод расширения <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> в экземпляре <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>. Значение параметра `directoryPath` должно быть абсолютным путем к файлам.

Перегрузки позволяют указать следующее.

- `Action<KeyPerFileConfigurationSource>` — делегат, который настраивает источник.
- Обязательно ли указывать каталог и путь к каталогу.

Двойное подчеркивание (`__`) используется в качестве разделителя ключа конфигурации в именах файлов. Например, в имени файла `Logging__LogLevel__System` создается ключ конфигурации `Logging:LogLevel:System`.

Чтобы указать конфигурацию приложения, при сборке веб-узла вызовите `ConfigureAppConfiguration`.

```csharp
.ConfigureAppConfiguration((_, configuration) =>
{
    var path = Path.Combine(
        Directory.GetCurrentDirectory(), "path/to/files");

    configuration.AddKeyPerFile(directoryPath: path, optional: true);
})
```

## <a name="memory-configuration-provider"></a>Поставщик конфигурации памяти

<xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> использует коллекцию памяти в качестве пар "ключ — значение" конфигурации.

Следующий код добавляет коллекцию памяти в систему конфигурации:

:::code language="csharp" source="snippets/configuration/console-memory/Program.cs" highlight="22-29":::

В приведенном выше коде <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> добавляет поставщика памяти после поставщиков конфигурации по умолчанию. Пример упорядочивания поставщиков конфигурации см. в разделе [Поставщик конфигурации XML](#xml-configuration-provider).

## <a name="see-also"></a>См. также раздел

- [Конфигурация в .NET](configuration.md)
- [Универсальный узел .NET](generic-host.md)
- [Реализация пользовательского поставщика конфигурации](custom-configuration-provider.md)
