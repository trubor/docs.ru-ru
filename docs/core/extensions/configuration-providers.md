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
# <a name="configuration-providers-in-net"></a><span data-ttu-id="8ada7-103">Поставщики конфигурации в .NET</span><span class="sxs-lookup"><span data-stu-id="8ada7-103">Configuration providers in .NET</span></span>

<span data-ttu-id="8ada7-104">Конфигурацию в .NET можно выполнять с помощью с поставщиков конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8ada7-104">Configuration in .NET is possible with configuration providers.</span></span> <span data-ttu-id="8ada7-105">Существует несколько типов поставщиков в зависимости от различных источников конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8ada7-105">There are several types of providers that rely on various configuration sources.</span></span> <span data-ttu-id="8ada7-106">В этой статье подробно описаны различные поставщики конфигурации и соответствующие им источники.</span><span class="sxs-lookup"><span data-stu-id="8ada7-106">This article details all of the different configuration providers and their corresponding sources.</span></span>

- [<span data-ttu-id="8ada7-107">Поставщик конфигурации файла</span><span class="sxs-lookup"><span data-stu-id="8ada7-107">File configuration provider</span></span>](#file-configuration-provider)
- [<span data-ttu-id="8ada7-108">Поставщик конфигурации переменных среды</span><span class="sxs-lookup"><span data-stu-id="8ada7-108">Environment variable configuration provider</span></span>](#environment-variable-configuration-provider)
- [<span data-ttu-id="8ada7-109">Поставщик конфигурации командной строки</span><span class="sxs-lookup"><span data-stu-id="8ada7-109">Command-line configuration provider</span></span>](#command-line-configuration-provider)
- [<span data-ttu-id="8ada7-110">Поставщик конфигурации ключа для каждого файла</span><span class="sxs-lookup"><span data-stu-id="8ada7-110">Key-per-file configuration provider</span></span>](#key-per-file-configuration-provider)
- [<span data-ttu-id="8ada7-111">Поставщик конфигурации памяти</span><span class="sxs-lookup"><span data-stu-id="8ada7-111">Memory configuration provider</span></span>](#memory-configuration-provider)

## <a name="file-configuration-provider"></a><span data-ttu-id="8ada7-112">Поставщик конфигурации файла</span><span class="sxs-lookup"><span data-stu-id="8ada7-112">File configuration provider</span></span>

<span data-ttu-id="8ada7-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> является базовым классом для загрузки конфигурации из файловой системы.</span><span class="sxs-lookup"><span data-stu-id="8ada7-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> is the base class for loading configuration from the file system.</span></span> <span data-ttu-id="8ada7-114">Следующие поставщики конфигурации являются производными от `FileConfigurationProvider`:</span><span class="sxs-lookup"><span data-stu-id="8ada7-114">The following configuration providers derive from `FileConfigurationProvider`:</span></span>

- [<span data-ttu-id="8ada7-115">Поставщик конфигурации JSON</span><span class="sxs-lookup"><span data-stu-id="8ada7-115">JSON configuration provider</span></span>](#json-configuration-provider)
- [<span data-ttu-id="8ada7-116">Поставщик конфигурации XML</span><span class="sxs-lookup"><span data-stu-id="8ada7-116">XML configuration provider</span></span>](#xml-configuration-provider)
- [<span data-ttu-id="8ada7-117">Поставщик конфигурации INI</span><span class="sxs-lookup"><span data-stu-id="8ada7-117">INI configuration provider</span></span>](#ini-configuration-provider)

### <a name="json-configuration-provider"></a><span data-ttu-id="8ada7-118">Поставщик конфигурации JSON</span><span class="sxs-lookup"><span data-stu-id="8ada7-118">JSON configuration provider</span></span>

<span data-ttu-id="8ada7-119">Класс <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> загружает конфигурацию из JSON-файла.</span><span class="sxs-lookup"><span data-stu-id="8ada7-119">The <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> class loads configuration from a JSON file.</span></span> <span data-ttu-id="8ada7-120">Установите пакет NuGet [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json).</span><span class="sxs-lookup"><span data-stu-id="8ada7-120">Install the [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) NuGet package.</span></span>

<span data-ttu-id="8ada7-121">Перегрузки могут указывать:</span><span class="sxs-lookup"><span data-stu-id="8ada7-121">Overloads can specify:</span></span>

- <span data-ttu-id="8ada7-122">является ли файл обязательным или нет;</span><span class="sxs-lookup"><span data-stu-id="8ada7-122">Whether the file is optional</span></span>
- <span data-ttu-id="8ada7-123">будет ли перезагружена конфигурация, если файл изменится.</span><span class="sxs-lookup"><span data-stu-id="8ada7-123">Whether the configuration is reloaded if the file changes</span></span>

<span data-ttu-id="8ada7-124">Рассмотрим следующий код.</span><span class="sxs-lookup"><span data-stu-id="8ada7-124">Consider the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="1-39,43-44" highlight="23-29":::

<span data-ttu-id="8ada7-125">Предыдущий код:</span><span class="sxs-lookup"><span data-stu-id="8ada7-125">The preceding code:</span></span>

- <span data-ttu-id="8ada7-126">Удаляет всех существующих поставщиков конфигурации, добавленных по умолчанию в метод <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="8ada7-126">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="8ada7-127">Настраивает поставщика конфигурации JSON для загрузки файлов *appsettings.json* и *appsettings*.`Environment`.*json* со следующими параметрами:</span><span class="sxs-lookup"><span data-stu-id="8ada7-127">Configures the JSON configuration provider to load the *appsettings.json* and  *appsettings*.`Environment`.*json* files with the following options:</span></span>
  - <span data-ttu-id="8ada7-128">`optional: true`. Файл является необязательным.</span><span class="sxs-lookup"><span data-stu-id="8ada7-128">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="8ada7-129">`reloadOnChange: true`: При сохранении изменений файл перезагружается.</span><span class="sxs-lookup"><span data-stu-id="8ada7-129">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>

<span data-ttu-id="8ada7-130">Параметры JSON переопределяются параметрами в [поставщике конфигурации переменных среды](#environment-variable-configuration-provider) и [поставщике конфигурации командной строки](#command-line-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="8ada7-130">The JSON settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="8ada7-131">Ниже приведен пример файла *appsettings.json* с различными параметрами конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8ada7-131">An example *appsettings.json* file with various configuration settings follows:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json":::

<span data-ttu-id="8ada7-132">Из экземпляра <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> после добавления поставщиков конфигурации можно вызвать <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> для получения объекта <xref:Microsoft.Extensions.Configuration.IConfigurationRoot>.</span><span class="sxs-lookup"><span data-stu-id="8ada7-132">From the <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance, after configuration providers have been added you can call <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> to get the <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> object.</span></span> <span data-ttu-id="8ada7-133">Корневой элемент конфигурации представляет корень иерархии конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8ada7-133">The configuration root represents the root of a configuration hierarchy.</span></span> <span data-ttu-id="8ada7-134">Разделы из конфигурации можно привязать к экземплярам объектов .NET, а затем предоставлять в виде <xref:Microsoft.Extensions.Options.IOptions%601> через внедрение зависимостей.</span><span class="sxs-lookup"><span data-stu-id="8ada7-134">Sections from the configuration can be bound to instances of .NET objects, and later provided as <xref:Microsoft.Extensions.Options.IOptions%601> through dependency injection.</span></span>

<span data-ttu-id="8ada7-135">Рассмотрим класс `TransientFaultHandlingOptions`, определенный следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8ada7-135">Consider the `TransientFaultHandlingOptions` class defined as follows:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs":::

<span data-ttu-id="8ada7-136">Следующий код создает корень конфигурации, привязывает раздел к типу класса `TransientFaultHandlingOptions` и выводит привязанные значения в окно консоли:</span><span class="sxs-lookup"><span data-stu-id="8ada7-136">The following code builds the configuration root, binds a section to the `TransientFaultHandlingOptions` class type, and prints the bound values to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

<span data-ttu-id="8ada7-137">Приложение запишет следующий пример выходных данных:</span><span class="sxs-lookup"><span data-stu-id="8ada7-137">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="40-42":::

### <a name="xml-configuration-provider"></a><span data-ttu-id="8ada7-138">Поставщик конфигурации XML</span><span class="sxs-lookup"><span data-stu-id="8ada7-138">XML configuration provider</span></span>

<span data-ttu-id="8ada7-139">Класс <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> загружает конфигурацию из XML-файла во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="8ada7-139">The <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> class loads configuration from an XML file at runtime.</span></span> <span data-ttu-id="8ada7-140">Установите пакет NuGet [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml).</span><span class="sxs-lookup"><span data-stu-id="8ada7-140">Install the [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) NuGet package.</span></span>

<span data-ttu-id="8ada7-141">В следующем примере кода демонстрируется конфигурация XML-файлов с помощью поставщика конфигурации XML.</span><span class="sxs-lookup"><span data-stu-id="8ada7-141">The following code demonstrates configuration of XML files using the XML configuration provider.</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="1-34,52,58-59" highlight="23-34":::

<span data-ttu-id="8ada7-142">Предыдущий код:</span><span class="sxs-lookup"><span data-stu-id="8ada7-142">The preceding code:</span></span>

- <span data-ttu-id="8ada7-143">Удаляет всех существующих поставщиков конфигурации, добавленных по умолчанию в метод <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="8ada7-143">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="8ada7-144">Настраивает поставщика конфигурации XML для загрузки файлов *appsettings.xml* и *repeating-example.xml* со следующими параметрами:</span><span class="sxs-lookup"><span data-stu-id="8ada7-144">Configures the XML configuration provider to load the *appsettings.xml* and *repeating-example.xml* files with the following options:</span></span>
  - <span data-ttu-id="8ada7-145">`optional: true`. Файл является необязательным.</span><span class="sxs-lookup"><span data-stu-id="8ada7-145">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="8ada7-146">`reloadOnChange: true`: При сохранении изменений файл перезагружается.</span><span class="sxs-lookup"><span data-stu-id="8ada7-146">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>
- <span data-ttu-id="8ada7-147">Настраивает поставщика конфигурации переменных среды.</span><span class="sxs-lookup"><span data-stu-id="8ada7-147">Configures the environment variables configuration provider.</span></span>
- <span data-ttu-id="8ada7-148">Настраивает поставщик конфигурации командной строки, если переданный элемент `args` содержит аргументы.</span><span class="sxs-lookup"><span data-stu-id="8ada7-148">Configures the command-line configuration provider if the given `args` contains arguments.</span></span>

<span data-ttu-id="8ada7-149">Параметры XML переопределяются параметрами в [поставщике конфигурации переменных среды](#environment-variable-configuration-provider) и [поставщике конфигурации командной строки](#command-line-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="8ada7-149">The XML settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="8ada7-150">Ниже приведен пример файла *appsettings.xml* с различными параметрами конфигурации:</span><span class="sxs-lookup"><span data-stu-id="8ada7-150">An example *appsettings.xml* file with various configuration settings follows:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/appsettings.xml":::

<span data-ttu-id="8ada7-151">Повторяющиеся элементы, использующие то же имя элемента, работают, если атрибут `name` используется для различения элементов.</span><span class="sxs-lookup"><span data-stu-id="8ada7-151">Repeating elements that use the same element name work if the `name` attribute is used to distinguish the elements:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/repeating-example.xml":::

<span data-ttu-id="8ada7-152">Следующий код считывает предыдущий файл конфигурации и отображает ключи и значения:</span><span class="sxs-lookup"><span data-stu-id="8ada7-152">The following code reads the previous configuration file and displays the keys and values:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="36-51":::

<span data-ttu-id="8ada7-153">Приложение запишет следующий пример выходных данных:</span><span class="sxs-lookup"><span data-stu-id="8ada7-153">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="53-57":::

<span data-ttu-id="8ada7-154">Атрибуты можно использовать для предоставления значений.</span><span class="sxs-lookup"><span data-stu-id="8ada7-154">Attributes can be used to supply values:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <key attribute="value" />
  <section>
    <key attribute="value" />
  </section>
</configuration>
```

<span data-ttu-id="8ada7-155">Предыдущий файл конфигурации загружает следующие ключи с помощью `value`.</span><span class="sxs-lookup"><span data-stu-id="8ada7-155">The previous configuration file loads the following keys with `value`:</span></span>

- `key:attribute`
- `section:key:attribute`

### <a name="ini-configuration-provider"></a><span data-ttu-id="8ada7-156">Поставщик конфигурации INI</span><span class="sxs-lookup"><span data-stu-id="8ada7-156">INI configuration provider</span></span>

<span data-ttu-id="8ada7-157">Класс <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> загружает конфигурацию из INI-файла во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="8ada7-157">The <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> class loads configuration from an INI file at runtime.</span></span> <span data-ttu-id="8ada7-158">Установите пакет NuGet [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini).</span><span class="sxs-lookup"><span data-stu-id="8ada7-158">Install the [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  NuGet package.</span></span>

<span data-ttu-id="8ada7-159">Следующий код очищает всех поставщиков конфигурации и добавляет `IniConfigurationProvider` с двумя INI-файлами в качестве источника:</span><span class="sxs-lookup"><span data-stu-id="8ada7-159">The following code clears all the configuration providers and adds the `IniConfigurationProvider` with two INI files as the source:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="1-37,44-45" highlight="24-30":::

<span data-ttu-id="8ada7-160">Ниже приведен пример файла *appsettings.ini* с различными параметрами конфигурации:</span><span class="sxs-lookup"><span data-stu-id="8ada7-160">An example *appsettings.ini* file with various configuration settings follows:</span></span>

:::code language="ini" source="snippets/configuration/console-ini/appsettings.ini":::

<span data-ttu-id="8ada7-161">Следующий код отображает приведенные выше параметры конфигурации, записывая их в окно консоли:</span><span class="sxs-lookup"><span data-stu-id="8ada7-161">The following code displays the preceding configuration settings by writing them to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="32-36":::

<span data-ttu-id="8ada7-162">Приложение запишет следующий пример выходных данных:</span><span class="sxs-lookup"><span data-stu-id="8ada7-162">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="38-43":::

## <a name="environment-variable-configuration-provider"></a><span data-ttu-id="8ada7-163">Поставщик конфигурации переменных среды</span><span class="sxs-lookup"><span data-stu-id="8ada7-163">Environment variable configuration provider</span></span>

<span data-ttu-id="8ada7-164">При использовании конфигурации по умолчанию <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> загружает конфигурацию из пар "ключ-значение" в переменных среды после чтения файлов *appsettings.json*, *appsettings.* `Environment` *.json* и диспетчера секретов.</span><span class="sxs-lookup"><span data-stu-id="8ada7-164">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> loads configuration from environment variable key-value pairs after reading *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span> <span data-ttu-id="8ada7-165">Поэтому значения ключей, считанные из среды, переопределяют значения, считанные из *appsettings.json*, *appsettings.* `Environment` *.json* и диспетчера секретов.</span><span class="sxs-lookup"><span data-stu-id="8ada7-165">Therefore, key values read from the environment override values read from *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span>

<span data-ttu-id="8ada7-166">Разделитель `:` не работает с иерархическими ключами переменных среды на всех платформах.</span><span class="sxs-lookup"><span data-stu-id="8ada7-166">The `:` separator doesn't work with environment variable hierarchical keys on all platforms.</span></span> <span data-ttu-id="8ada7-167">Двойной знак подчеркивания (`__`) автоматически заменяется на `:` и поддерживается на всех платформах.</span><span class="sxs-lookup"><span data-stu-id="8ada7-167">The double underscore (`__`) is automatically replaced by a `:` and is supported by all platforms.</span></span> <span data-ttu-id="8ada7-168">Например, разделитель `:` не поддерживается [Bash](https://linuxhint.com/bash-environment-variables), а `__` — поддерживается.</span><span class="sxs-lookup"><span data-stu-id="8ada7-168">For example, the `:` separator is not supported by [Bash](https://linuxhint.com/bash-environment-variables), but `__` is.</span></span>

<span data-ttu-id="8ada7-169">Следующие команды `set`:</span><span class="sxs-lookup"><span data-stu-id="8ada7-169">The following `set` commands:</span></span>

- <span data-ttu-id="8ada7-170">Задают ключи и значения среды в предыдущем примере в Windows.</span><span class="sxs-lookup"><span data-stu-id="8ada7-170">Set the environment keys and values of the preceding example on Windows.</span></span>
- <span data-ttu-id="8ada7-171">Проверяют параметры, изменив их значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8ada7-171">Test the settings by changing them from their default values.</span></span> <span data-ttu-id="8ada7-172">Команда `dotnet run` должна выполняться в каталоге проекта.</span><span class="sxs-lookup"><span data-stu-id="8ada7-172">The `dotnet run` command must be run in the project directory.</span></span>

```dotnetcli
set SecretKey="Secret key from environment"
set TransientFaultHandlingOptions__Enabled="true"
set TransientFaultHandlingOptions__AutoRetryDelay="00:00:13"

dotnet run
```

<span data-ttu-id="8ada7-173">Предыдущие параметры среды:</span><span class="sxs-lookup"><span data-stu-id="8ada7-173">The preceding environment settings:</span></span>

- <span data-ttu-id="8ada7-174">Задаются только в процессах, запускаемых из командного окна, в котором они были установлены.</span><span class="sxs-lookup"><span data-stu-id="8ada7-174">Are only set in processes launched from the command window they were set in.</span></span>
- <span data-ttu-id="8ada7-175">Не будут считываться веб-приложениями, запущенными в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8ada7-175">Won't be read by web apps launched with Visual Studio.</span></span>

<span data-ttu-id="8ada7-176">Следующие команды [setx](/windows-server/administration/windows-commands/setx) можно использовать для задания ключей и значений среды в Windows.</span><span class="sxs-lookup"><span data-stu-id="8ada7-176">The following [setx](/windows-server/administration/windows-commands/setx) commands can be used to set the environment keys and values on Windows.</span></span> <span data-ttu-id="8ada7-177">В отличие от `set`, параметры `setx` сохраняются.</span><span class="sxs-lookup"><span data-stu-id="8ada7-177">Unlike `set`, `setx` settings are persisted.</span></span> <span data-ttu-id="8ada7-178">`/M` задает переменную в системной среде.</span><span class="sxs-lookup"><span data-stu-id="8ada7-178">`/M` sets the variable in the system environment.</span></span> <span data-ttu-id="8ada7-179">Если параметр `/M` не используется, задается переменная среды пользователя.</span><span class="sxs-lookup"><span data-stu-id="8ada7-179">If the `/M` switch isn't used, a user environment variable is set.</span></span>

```dotnetcli
setx SecretKey "Secret key from setx environment" /M
setx TransientFaultHandlingOptions__Enabled "true" /M
setx TransientFaultHandlingOptions__AutoRetryDelay "00:00:05" /M

dotnet run
```

<span data-ttu-id="8ada7-180">Чтобы проверить, что предыдущие команды переопределяют *appsettings.json* и *appsettings.* `Environment` *.json*, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="8ada7-180">To test that the preceding commands override *appsettings.json* and *appsettings.*`Environment`*.json*:</span></span>

- <span data-ttu-id="8ada7-181">В Visual Studio: Выйдите из среды Visual Studio и перезапустите ее.</span><span class="sxs-lookup"><span data-stu-id="8ada7-181">With Visual Studio: Exit and restart Visual Studio.</span></span>
- <span data-ttu-id="8ada7-182">В CLI: Откройте новое командное окно и введите `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="8ada7-182">With the CLI: Start a new command window and enter `dotnet run`.</span></span>

<span data-ttu-id="8ada7-183">Вызовите <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> со строкой, чтобы указать префикс для переменных среды:</span><span class="sxs-lookup"><span data-stu-id="8ada7-183">Call <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> with a string to specify a prefix for environment variables:</span></span>

:::code language="csharp" source="snippets/configuration/console-env/Program.cs" highlight="21-22":::

<span data-ttu-id="8ada7-184">В приведенном выше коде:</span><span class="sxs-lookup"><span data-stu-id="8ada7-184">In the preceding code:</span></span>

- <span data-ttu-id="8ada7-185">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` добавляется после поставщиков конфигурации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8ada7-185">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` is added after the default configuration providers.</span></span> <span data-ttu-id="8ada7-186">Пример упорядочивания поставщиков конфигурации см. в разделе [Поставщик конфигурации XML](#xml-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="8ada7-186">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>
- <span data-ttu-id="8ada7-187">Переменные среды, установленные с префиксом `CustomPrefix_`, переопределяют поставщиков конфигурации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8ada7-187">Environment variables set with the `CustomPrefix_` prefix override the default configuration providers.</span></span> <span data-ttu-id="8ada7-188">Сюда входят переменные среды без префикса.</span><span class="sxs-lookup"><span data-stu-id="8ada7-188">This includes environment variables without the prefix.</span></span>

<span data-ttu-id="8ada7-189">Префикс отделяется при создании пары конфигурации "ключ-значение".</span><span class="sxs-lookup"><span data-stu-id="8ada7-189">The prefix is stripped off when the configuration key-value pairs are read.</span></span>

<span data-ttu-id="8ada7-190">Следующие команды проверяют пользовательский префикс:</span><span class="sxs-lookup"><span data-stu-id="8ada7-190">The following commands test the custom prefix:</span></span>

```dotnetcli
set CustomPrefix__SecretKey="Secret key with CustomPrefix_ environment"
set CustomPrefix__TransientFaultHandlingOptions__Enabled=true
set CustomPrefix__TransientFaultHandlingOptions__AutoRetryDelay=00:00:21

dotnet run
```

<span data-ttu-id="8ada7-191">Конфигурация по умолчанию загружает переменные среды и аргументы командной строки с префиксом `DOTNET_`.</span><span class="sxs-lookup"><span data-stu-id="8ada7-191">The default configuration loads environment variables and command-line arguments prefixed with `DOTNET_`.</span></span> <span data-ttu-id="8ada7-192">Префикс `DOTNET_` используется .NET для конфигурации [узла](generic-host.md#host-configuration) и [приложения](generic-host.md#app-configuration), но не для конфигурации пользователя.</span><span class="sxs-lookup"><span data-stu-id="8ada7-192">The `DOTNET_` prefix is used by .NET for [host](generic-host.md#host-configuration) and [app configuration](generic-host.md#app-configuration), but not for user configuration.</span></span>

<span data-ttu-id="8ada7-193">Дополнительные сведения о конфигурации узла и приложения см. в разделе [Универсальный узел .NET](generic-host.md).</span><span class="sxs-lookup"><span data-stu-id="8ada7-193">For more information on host and app configuration, see [.NET Generic Host](generic-host.md).</span></span>

<span data-ttu-id="8ada7-194">В [Службе приложений Azure](https://azure.microsoft.com/services/app-service) выберите **Новый параметр приложения** на странице **Параметры > Конфигурация**.</span><span class="sxs-lookup"><span data-stu-id="8ada7-194">On [Azure App Service](https://azure.microsoft.com/services/app-service), select **New application setting** on the **Settings > Configuration** page.</span></span> <span data-ttu-id="8ada7-195">Параметры приложения Службы приложений Azure:</span><span class="sxs-lookup"><span data-stu-id="8ada7-195">Azure App Service application settings are:</span></span>

- <span data-ttu-id="8ada7-196">Шифруются, когда они неактивны, и передаются по зашифрованному каналу.</span><span class="sxs-lookup"><span data-stu-id="8ada7-196">Encrypted at rest and transmitted over an encrypted channel.</span></span>
- <span data-ttu-id="8ada7-197">Предоставляются как переменные среды.</span><span class="sxs-lookup"><span data-stu-id="8ada7-197">Exposed as environment variables.</span></span>

### <a name="connection-string-prefixes"></a><span data-ttu-id="8ada7-198">Префиксы строк подключения</span><span class="sxs-lookup"><span data-stu-id="8ada7-198">Connection string prefixes</span></span>

<span data-ttu-id="8ada7-199">API конфигурации имеет особые правила обработки для четырех переменных среды строки подключения.</span><span class="sxs-lookup"><span data-stu-id="8ada7-199">The Configuration API has special processing rules for four connection string environment variables.</span></span> <span data-ttu-id="8ada7-200">Эти строки подключения участвуют в настройке строк подключения Azure для среды приложения.</span><span class="sxs-lookup"><span data-stu-id="8ada7-200">These connection strings are involved in configuring Azure connection strings for the app environment.</span></span> <span data-ttu-id="8ada7-201">Переменные среды с префиксами, указанными в таблице, загружаются в приложение с конфигурацией по умолчанию или если префикс не предоставлен для `AddEnvironmentVariables`.</span><span class="sxs-lookup"><span data-stu-id="8ada7-201">Environment variables with the prefixes shown in the table are loaded into the app with the default configuration or when no prefix is supplied to `AddEnvironmentVariables`.</span></span>

| <span data-ttu-id="8ada7-202">Префикс строки подключения</span><span class="sxs-lookup"><span data-stu-id="8ada7-202">Connection string prefix</span></span> | <span data-ttu-id="8ada7-203">Поставщик</span><span class="sxs-lookup"><span data-stu-id="8ada7-203">Provider</span></span>                                                                |
|--------------------------|-------------------------------------------------------------------------|
| `CUSTOMCONNSTR_`         | <span data-ttu-id="8ada7-204">Поставщик пользователя</span><span class="sxs-lookup"><span data-stu-id="8ada7-204">Custom provider</span></span>                                                         |
| `MYSQLCONNSTR_`          | [<span data-ttu-id="8ada7-205">MySQL</span><span class="sxs-lookup"><span data-stu-id="8ada7-205">MySQL</span></span>](https://www.mysql.com)                                          |
| `SQLAZURECONNSTR_`       | [<span data-ttu-id="8ada7-206">База данных SQL Azure</span><span class="sxs-lookup"><span data-stu-id="8ada7-206">Azure SQL Database</span></span>](https://azure.microsoft.com/services/sql-database) |
| `SQLCONNSTR_`            | [<span data-ttu-id="8ada7-207">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8ada7-207">SQL Server</span></span>](https://www.microsoft.com/sql-server)                      |

<span data-ttu-id="8ada7-208">Когда переменная среды обнаруживается и загружается в конфигурацию с одним из четырех префиксов, приведенных в таблице, происходит следующее.</span><span class="sxs-lookup"><span data-stu-id="8ada7-208">When an environment variable is discovered and loaded into configuration with any of the four prefixes shown in the table:</span></span>

- <span data-ttu-id="8ada7-209">Ключ конфигурации создается путем удаления префикса переменных среды и добавления ключа раздела конфигурации (`ConnectionStrings`).</span><span class="sxs-lookup"><span data-stu-id="8ada7-209">The configuration key is created by removing the environment variable prefix and adding a configuration key section (`ConnectionStrings`).</span></span>
- <span data-ttu-id="8ada7-210">Создается новая пара "ключ — значение" конфигурации, которая представляет поставщика подключения базы данных (за исключением `CUSTOMCONNSTR_`, который не имеет указанного поставщика).</span><span class="sxs-lookup"><span data-stu-id="8ada7-210">A new configuration key-value pair is created that represents the database connection provider (except for `CUSTOMCONNSTR_`, which has no stated provider).</span></span>

| <span data-ttu-id="8ada7-211">Ключ переменной среды</span><span class="sxs-lookup"><span data-stu-id="8ada7-211">Environment variable key</span></span> | <span data-ttu-id="8ada7-212">Преобразованный ключ конфигурации</span><span class="sxs-lookup"><span data-stu-id="8ada7-212">Converted configuration key</span></span> | <span data-ttu-id="8ada7-213">Запись конфигурации поставщика</span><span class="sxs-lookup"><span data-stu-id="8ada7-213">Provider configuration entry</span></span>                                                    |
|--------------------------|-----------------------------|---------------------------------------------------------------------------------|
| `CUSTOMCONNSTR_{KEY}`    | `ConnectionStrings:{KEY}`   | <span data-ttu-id="8ada7-214">Запись конфигурации не создана.</span><span class="sxs-lookup"><span data-stu-id="8ada7-214">Configuration entry not created.</span></span>                                                |
| `MYSQLCONNSTR_{KEY}`     | `ConnectionStrings:{KEY}`   | <span data-ttu-id="8ada7-215">Ключ: `ConnectionStrings:{KEY}_ProviderName`:</span><span class="sxs-lookup"><span data-stu-id="8ada7-215">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="8ada7-216">Значение: `MySql.Data.MySqlClient`</span><span class="sxs-lookup"><span data-stu-id="8ada7-216">Value: `MySql.Data.MySqlClient`</span></span> |
| `SQLAZURECONNSTR_{KEY}`  | `ConnectionStrings:{KEY}`   | <span data-ttu-id="8ada7-217">Ключ: `ConnectionStrings:{KEY}_ProviderName`:</span><span class="sxs-lookup"><span data-stu-id="8ada7-217">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="8ada7-218">Значение: `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="8ada7-218">Value: `System.Data.SqlClient`</span></span>  |
| `SQLCONNSTR_{KEY}`       | `ConnectionStrings:{KEY}`   | <span data-ttu-id="8ada7-219">Ключ: `ConnectionStrings:{KEY}_ProviderName`:</span><span class="sxs-lookup"><span data-stu-id="8ada7-219">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="8ada7-220">Значение: `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="8ada7-220">Value: `System.Data.SqlClient`</span></span>  |

### <a name="environment-variables-set-in-launchsettingsjson"></a><span data-ttu-id="8ada7-221">Переменные среды, заданные в launchSettings.json</span><span class="sxs-lookup"><span data-stu-id="8ada7-221">Environment variables set in launchSettings.json</span></span>

<span data-ttu-id="8ada7-222">Переменные среды, заданные в *launchSettings.json*, переопределяют переменные, заданные в системной среде.</span><span class="sxs-lookup"><span data-stu-id="8ada7-222">Environment variables set in *launchSettings.json* override those set in the system environment.</span></span>

## <a name="command-line-configuration-provider"></a><span data-ttu-id="8ada7-223">Поставщик конфигурации командной строки</span><span class="sxs-lookup"><span data-stu-id="8ada7-223">Command-line configuration provider</span></span>

<span data-ttu-id="8ada7-224">При использовании конфигурации по умолчанию <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> загружает конфигурацию из пар "ключ-значение" аргументов командной строки после следующих источников конфигурации:</span><span class="sxs-lookup"><span data-stu-id="8ada7-224">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> loads configuration from command-line argument key-value pairs after the following configuration sources:</span></span>

- <span data-ttu-id="8ada7-225">Файлы *appsettings.json* и *appsettings*.`Environment`.*json*.</span><span class="sxs-lookup"><span data-stu-id="8ada7-225">*appsettings.json* and *appsettings*.`Environment`.*json* files.</span></span>
- <span data-ttu-id="8ada7-226">Секреты приложения (диспетчер секретов) в среде `Development`.</span><span class="sxs-lookup"><span data-stu-id="8ada7-226">App secrets (Secret Manager) in the `Development` environment.</span></span>
- <span data-ttu-id="8ada7-227">Переменные среды.</span><span class="sxs-lookup"><span data-stu-id="8ada7-227">Environment variables.</span></span>

<span data-ttu-id="8ada7-228">По умолчанию значения конфигурации, заданные для значений конфигурации переопределения в командной строке, задаются для всех остальных поставщиков конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8ada7-228">By default, configuration values set on the command line override configuration values set with all the other configuration providers.</span></span>

### <a name="command-line-arguments"></a><span data-ttu-id="8ada7-229">аргументов командной строки;</span><span class="sxs-lookup"><span data-stu-id="8ada7-229">Command-line arguments</span></span>

<span data-ttu-id="8ada7-230">Следующая команда задает ключи и значения с помощью `=`:</span><span class="sxs-lookup"><span data-stu-id="8ada7-230">The following command sets keys and values using `=`:</span></span>

```dotnetcli
dotnet run SecretKey="Secret key from command line"
```

<span data-ttu-id="8ada7-231">Следующая команда задает ключи и значения с помощью `/`:</span><span class="sxs-lookup"><span data-stu-id="8ada7-231">The following command sets keys and values using `/`:</span></span>

```dotnetcli
dotnet run /SecretKey "Secret key set from forward slash"
```

<span data-ttu-id="8ada7-232">Следующая команда задает ключи и значения с помощью `--`:</span><span class="sxs-lookup"><span data-stu-id="8ada7-232">The following command sets keys and values using `--`:</span></span>

```dotnetcli
dotnet run --SecretKey "Secret key set from double hyphen"
```

<span data-ttu-id="8ada7-233">Значение ключа:</span><span class="sxs-lookup"><span data-stu-id="8ada7-233">The key value:</span></span>

- <span data-ttu-id="8ada7-234">Должно соответствовать `=`, или ключ должен иметь префикс `--` или `/`, когда значение следует за пробелом.</span><span class="sxs-lookup"><span data-stu-id="8ada7-234">Must follow `=`, or the key must have a prefix of `--` or `/` when the value follows a space.</span></span>
- <span data-ttu-id="8ada7-235">Является обязательным, если используется параметр `=`.</span><span class="sxs-lookup"><span data-stu-id="8ada7-235">Isn't required if `=` is used.</span></span> <span data-ttu-id="8ada7-236">Например, `SomeKey=`.</span><span class="sxs-lookup"><span data-stu-id="8ada7-236">For example, `SomeKey=`.</span></span>

<span data-ttu-id="8ada7-237">В рамках одной и той же команды не смешивайте пары "ключ-значение" аргумента командной строки, которые используют `=` с парами "ключ-значение" с пробелом.</span><span class="sxs-lookup"><span data-stu-id="8ada7-237">Within the same command, don't mix command-line argument key-value pairs that use `=` with key-value pairs that use a space.</span></span>

## <a name="key-per-file-configuration-provider"></a><span data-ttu-id="8ada7-238">Поставщик конфигурации ключа для каждого файла</span><span class="sxs-lookup"><span data-stu-id="8ada7-238">Key-per-file configuration provider</span></span>

<span data-ttu-id="8ada7-239"><xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> использует файлы каталога как пары "ключ — значение" конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8ada7-239">The <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> uses a directory's files as configuration key-value pairs.</span></span> <span data-ttu-id="8ada7-240">Ключ является именем файла.</span><span class="sxs-lookup"><span data-stu-id="8ada7-240">The key is the file name.</span></span> <span data-ttu-id="8ada7-241">Значением является содержимое файла.</span><span class="sxs-lookup"><span data-stu-id="8ada7-241">The value is the file's contents.</span></span> <span data-ttu-id="8ada7-242">Поставщик конфигурации ключа для каждого файла используется в сценариях размещения Docker.</span><span class="sxs-lookup"><span data-stu-id="8ada7-242">The Key-per-file configuration provider is used in Docker hosting scenarios.</span></span>

<span data-ttu-id="8ada7-243">Чтобы активировать конфигурацию ключа для каждого файла, вызовите метод расширения <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> в экземпляре <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>.</span><span class="sxs-lookup"><span data-stu-id="8ada7-243">To activate key-per-file configuration, call the <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> extension method on an instance of <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>.</span></span> <span data-ttu-id="8ada7-244">Значение параметра `directoryPath` должно быть абсолютным путем к файлам.</span><span class="sxs-lookup"><span data-stu-id="8ada7-244">The `directoryPath` to the files must be an absolute path.</span></span>

<span data-ttu-id="8ada7-245">Перегрузки позволяют указать следующее.</span><span class="sxs-lookup"><span data-stu-id="8ada7-245">Overloads permit specifying:</span></span>

- <span data-ttu-id="8ada7-246">`Action<KeyPerFileConfigurationSource>` — делегат, который настраивает источник.</span><span class="sxs-lookup"><span data-stu-id="8ada7-246">An `Action<KeyPerFileConfigurationSource>` delegate that configures the source.</span></span>
- <span data-ttu-id="8ada7-247">Обязательно ли указывать каталог и путь к каталогу.</span><span class="sxs-lookup"><span data-stu-id="8ada7-247">Whether the directory is optional and the path to the directory.</span></span>

<span data-ttu-id="8ada7-248">Двойное подчеркивание (`__`) используется в качестве разделителя ключа конфигурации в именах файлов.</span><span class="sxs-lookup"><span data-stu-id="8ada7-248">The double-underscore (`__`) is used as a configuration key delimiter in file names.</span></span> <span data-ttu-id="8ada7-249">Например, в имени файла `Logging__LogLevel__System` создается ключ конфигурации `Logging:LogLevel:System`.</span><span class="sxs-lookup"><span data-stu-id="8ada7-249">For example, the file name `Logging__LogLevel__System` produces the configuration key `Logging:LogLevel:System`.</span></span>

<span data-ttu-id="8ada7-250">Чтобы указать конфигурацию приложения, при сборке веб-узла вызовите `ConfigureAppConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="8ada7-250">Call `ConfigureAppConfiguration` when building the host to specify the app's configuration:</span></span>

```csharp
.ConfigureAppConfiguration((_, configuration) =>
{
    var path = Path.Combine(
        Directory.GetCurrentDirectory(), "path/to/files");

    configuration.AddKeyPerFile(directoryPath: path, optional: true);
})
```

## <a name="memory-configuration-provider"></a><span data-ttu-id="8ada7-251">Поставщик конфигурации памяти</span><span class="sxs-lookup"><span data-stu-id="8ada7-251">Memory configuration provider</span></span>

<span data-ttu-id="8ada7-252"><xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> использует коллекцию памяти в качестве пар "ключ — значение" конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8ada7-252">The <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> uses an in-memory collection as configuration key-value pairs.</span></span>

<span data-ttu-id="8ada7-253">Следующий код добавляет коллекцию памяти в систему конфигурации:</span><span class="sxs-lookup"><span data-stu-id="8ada7-253">The following code adds a memory collection to the configuration system:</span></span>

:::code language="csharp" source="snippets/configuration/console-memory/Program.cs" highlight="22-29":::

<span data-ttu-id="8ada7-254">В приведенном выше коде <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> добавляет поставщика памяти после поставщиков конфигурации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8ada7-254">In the preceding code, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> adds the memory provider after the default configuration providers.</span></span> <span data-ttu-id="8ada7-255">Пример упорядочивания поставщиков конфигурации см. в разделе [Поставщик конфигурации XML](#xml-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="8ada7-255">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ada7-256">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8ada7-256">See also</span></span>

- [<span data-ttu-id="8ada7-257">Конфигурация в .NET</span><span class="sxs-lookup"><span data-stu-id="8ada7-257">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="8ada7-258">Универсальный узел .NET</span><span class="sxs-lookup"><span data-stu-id="8ada7-258">.NET Generic Host</span></span>](generic-host.md)
- [<span data-ttu-id="8ada7-259">Реализация пользовательского поставщика конфигурации</span><span class="sxs-lookup"><span data-stu-id="8ada7-259">Implement a custom configuration provider</span></span>](custom-configuration-provider.md)
