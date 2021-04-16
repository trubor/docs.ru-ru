---
title: Конфигурация приложения
description: Узнайте, как настроить приложения Blazor без использования ConfigurationManager.
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 360d9077bc981a2e9875bb1f86b49c0029424d6e
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509797"
---
# <a name="app-configuration"></a><span data-ttu-id="6476b-103">Конфигурация приложения</span><span class="sxs-lookup"><span data-stu-id="6476b-103">App configuration</span></span>

<span data-ttu-id="6476b-104">Основной способ загрузки конфигурации приложения в Web Forms — с записями в файле *web.config* &mdash; либо на сервере, либо в связанном файле конфигурации, на который ссылается *web.config*. Статический объект `ConfigurationManager` можно использовать для взаимодействия с параметрами приложения, строками подключения репозитория данных и другими поставщиками расширенной конфигурации, добавленными в приложение.</span><span class="sxs-lookup"><span data-stu-id="6476b-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="6476b-105">Обычно для просмотра взаимодействия с конфигурацией приложения отображается следующий код:</span><span class="sxs-lookup"><span data-stu-id="6476b-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="6476b-106">При использовании ASP.NET Core и Blazor на стороне сервера файл *web.config* может присутствовать, если приложение размещено на сервере Windows IIS.</span><span class="sxs-lookup"><span data-stu-id="6476b-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="6476b-107">Однако взаимодействия `ConfigurationManager` с этой конфигурацией не требуется, и вы можете получить более структурированную конфигурацию приложения из других источников.</span><span class="sxs-lookup"><span data-stu-id="6476b-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="6476b-108">Давайте посмотрим, как собирается конфигурация и как можно получить доступ к сведениям о конфигурации из файла *web.config*.</span><span class="sxs-lookup"><span data-stu-id="6476b-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="6476b-109">Источники конфигураций</span><span class="sxs-lookup"><span data-stu-id="6476b-109">Configuration sources</span></span>

<span data-ttu-id="6476b-110">ASP.NET Core признает наличие множества источников конфигурации, которые вы можете использовать для приложения.</span><span class="sxs-lookup"><span data-stu-id="6476b-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="6476b-111">Платформа пытается предложить наиболее подходящие из этих функций по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6476b-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="6476b-112">Конфигурация считывается и объединяется из этих различных источников с помощью ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6476b-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="6476b-113">Более поздние загруженные значения для одного и того же ключа конфигурации имеют приоритет над более ранними значениями.</span><span class="sxs-lookup"><span data-stu-id="6476b-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="6476b-114">ASP.NET Core была разработана для обеспечения работы в облаке и упрощения настройки приложений для их пользователей и разработчиков.</span><span class="sxs-lookup"><span data-stu-id="6476b-114">ASP.NET Core was designed to be cloud-aware and to make the configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="6476b-115">ASP.NET Core работает с учетом среды и знает, работает ли она в среде `Production` или `Development`.</span><span class="sxs-lookup"><span data-stu-id="6476b-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="6476b-116">Индикатор среды задается в системной переменной среды `ASPNETCORE_ENVIRONMENT`.</span><span class="sxs-lookup"><span data-stu-id="6476b-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="6476b-117">Если значение не задано, приложение по умолчанию работает в среде `Production`.</span><span class="sxs-lookup"><span data-stu-id="6476b-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="6476b-118">Приложение может активировать и добавить конфигурацию из нескольких источников, в зависимости от имени среды.</span><span class="sxs-lookup"><span data-stu-id="6476b-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="6476b-119">По умолчанию конфигурация загружается из следующих ресурсов в указанном порядке:</span><span class="sxs-lookup"><span data-stu-id="6476b-119">By default, the configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="6476b-120">файла *appsettings.jsв*, если он есть;</span><span class="sxs-lookup"><span data-stu-id="6476b-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="6476b-121">файла *appsettings.{ENVIRONMENT_NAME}.json*, если он есть;</span><span class="sxs-lookup"><span data-stu-id="6476b-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="6476b-122">файла секретов пользователя на диске, если он есть;</span><span class="sxs-lookup"><span data-stu-id="6476b-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="6476b-123">Переменные среды</span><span class="sxs-lookup"><span data-stu-id="6476b-123">Environment variables</span></span>
1. <span data-ttu-id="6476b-124">аргументов командной строки;</span><span class="sxs-lookup"><span data-stu-id="6476b-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="6476b-125">Формат файла appsettings.jsк и доступ к нему</span><span class="sxs-lookup"><span data-stu-id="6476b-125">appsettings.json format and access</span></span>

<span data-ttu-id="6476b-126">Файл *appsettings.jsв* может быть иерархическим со значениями, структурированными как в следующем JSON:</span><span class="sxs-lookup"><span data-stu-id="6476b-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

<span data-ttu-id="6476b-127">При отображении с помощью вышеуказанного JSON система конфигурации преобразует дочерние значения в плоские структуры и ссылается на полные иерархические пути.</span><span class="sxs-lookup"><span data-stu-id="6476b-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="6476b-128">Символ двоеточия (`:`) разделяет каждое свойство в иерархии.</span><span class="sxs-lookup"><span data-stu-id="6476b-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="6476b-129">Например, ключ конфигурации `section1:key0` обращается к значению `key0` объектного литерала `section1`.</span><span class="sxs-lookup"><span data-stu-id="6476b-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="6476b-130">Секреты пользователя.</span><span class="sxs-lookup"><span data-stu-id="6476b-130">User secrets</span></span>

<span data-ttu-id="6476b-131">Секреты пользователя:</span><span class="sxs-lookup"><span data-stu-id="6476b-131">User secrets are:</span></span>

* <span data-ttu-id="6476b-132">Являются значениями конфигурации, хранящимися в JSON-файле на рабочей станции разработчика, за пределами папки разработки приложения.</span><span class="sxs-lookup"><span data-stu-id="6476b-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="6476b-133">Загружаются только при выполнении в среде `Development`.</span><span class="sxs-lookup"><span data-stu-id="6476b-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="6476b-134">Связаны с конкретным приложением.</span><span class="sxs-lookup"><span data-stu-id="6476b-134">Associated with a specific app.</span></span>
* <span data-ttu-id="6476b-135">Управляется с помощью команды `user-secrets` интерфейса командной строки .NET.</span><span class="sxs-lookup"><span data-stu-id="6476b-135">Managed with the .NET CLI's `user-secrets` command.</span></span>

<span data-ttu-id="6476b-136">Настройте приложение для хранения секретов, выполнив команду `user-secrets`:</span><span class="sxs-lookup"><span data-stu-id="6476b-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="6476b-137">Предыдущая команда добавляет элемент `UserSecretsId` в файл проекта.</span><span class="sxs-lookup"><span data-stu-id="6476b-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="6476b-138">Элемент содержит идентификатор GUID, который используется для связывания секретов с приложением.</span><span class="sxs-lookup"><span data-stu-id="6476b-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="6476b-139">Затем можно определить секрет с помощью команды `set`.</span><span class="sxs-lookup"><span data-stu-id="6476b-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="6476b-140">Пример:</span><span class="sxs-lookup"><span data-stu-id="6476b-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="6476b-141">Предыдущая команда делает ключ конфигурации `Parent:ApiKey` доступным на рабочей станции разработчика со значением `12345`.</span><span class="sxs-lookup"><span data-stu-id="6476b-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="6476b-142">Дополнительные сведения о создании, хранении и управлении секретами пользователей см. в документе [Безопасное хранения разрабатываемых секретов приложений в ASP.NET Core](/aspnet/core/security/app-secrets).</span><span class="sxs-lookup"><span data-stu-id="6476b-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="6476b-143">Переменные среды</span><span class="sxs-lookup"><span data-stu-id="6476b-143">Environment variables</span></span>

<span data-ttu-id="6476b-144">Следующий набор значений, загружаемых в конфигурацию приложения, — это переменные среды системы.</span><span class="sxs-lookup"><span data-stu-id="6476b-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="6476b-145">Все параметры переменных среды системы теперь доступны через API настройки.</span><span class="sxs-lookup"><span data-stu-id="6476b-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="6476b-146">При чтении внутри приложения иерархические значения преобразуются в плоские структуры и разделяются символами двоеточия.</span><span class="sxs-lookup"><span data-stu-id="6476b-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="6476b-147">Однако некоторые операционные системы не разрешают имена переменных среды с двоеточием.</span><span class="sxs-lookup"><span data-stu-id="6476b-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="6476b-148">ASP.NET Core устраняет это ограничение, преобразуя значения с двойным подчеркиванием (`__`) в двоеточия при обращении к ним.</span><span class="sxs-lookup"><span data-stu-id="6476b-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="6476b-149">Значение `Parent:ApiKey` из раздела о секретах пользователя выше можно переопределить с помощью переменной среды `Parent__ApiKey`.</span><span class="sxs-lookup"><span data-stu-id="6476b-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="6476b-150">аргументов командной строки;</span><span class="sxs-lookup"><span data-stu-id="6476b-150">Command-line arguments</span></span>

<span data-ttu-id="6476b-151">Кроме того, конфигурацию можно указать в виде аргументов командной строки при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="6476b-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="6476b-152">Используйте двойное тире (`--`) или прямую косую черту (`/`), чтобы указать имя устанавливаемого значения конфигурации и значение, которое необходимо настроить.</span><span class="sxs-lookup"><span data-stu-id="6476b-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="6476b-153">Синтаксис напоминает следующие команды:</span><span class="sxs-lookup"><span data-stu-id="6476b-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="6476b-154">Возвращение web.config</span><span class="sxs-lookup"><span data-stu-id="6476b-154">The return of web.config</span></span>

<span data-ttu-id="6476b-155">Если вы развернули приложение в Windows на IIS, файл *web.config* по-прежнему настраивает IIS для управления приложением.</span><span class="sxs-lookup"><span data-stu-id="6476b-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="6476b-156">По умолчанию службы IIS добавляют ссылку на модуль ASP.NET Core (ANCM).</span><span class="sxs-lookup"><span data-stu-id="6476b-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="6476b-157">ANCM — это собственный модуль IIS, в котором размещается приложение вместо веб-сервера Kestrel.</span><span class="sxs-lookup"><span data-stu-id="6476b-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="6476b-158">Этот раздел *web.config* напоминает следующую XML-разметку:</span><span class="sxs-lookup"><span data-stu-id="6476b-158">This *web.config* section resembles the following XML markup:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

<span data-ttu-id="6476b-159">Конфигурация конкретного приложения может быть определена путем вложения элемента `environmentVariables` в элемент `aspNetCore`.</span><span class="sxs-lookup"><span data-stu-id="6476b-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="6476b-160">Значения, определенные в этом разделе, представлены в приложении ASP.NET Core как переменные среды.</span><span class="sxs-lookup"><span data-stu-id="6476b-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="6476b-161">Переменные среды загружаются соответствующим образом во время выполнения этого сегмента запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="6476b-161">The environment variables load appropriately during that segment of app startup.</span></span>

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="6476b-162">Чтение конфигурации в приложении</span><span class="sxs-lookup"><span data-stu-id="6476b-162">Read configuration in the app</span></span>

<span data-ttu-id="6476b-163">В ASP.NET Core предоставляет конфигурацию приложения с помощью интерфейса <xref:Microsoft.Extensions.Configuration.IConfiguration>.</span><span class="sxs-lookup"><span data-stu-id="6476b-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="6476b-164">Этот интерфейс конфигурации должны запрашивать компоненты Blazor, страницы Blazor и любые другие управляемые ASP.NET Core классы, которым требуется доступ к конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6476b-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="6476b-165">Платформа ASP.NET Core автоматически заполнит этот интерфейс разрешенной конфигурацией, настроенной ранее.</span><span class="sxs-lookup"><span data-stu-id="6476b-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="6476b-166">На странице Blazor или в разметке Razor компонента можно внедрить объект `IConfiguration` с директивой `@inject`, расположенной в верхней части файла *.razor*, следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6476b-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="6476b-167">Приведенная выше инструкция делает объект `IConfiguration` доступным в качестве переменной `Configuration` для всего остального шаблона Razor.</span><span class="sxs-lookup"><span data-stu-id="6476b-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="6476b-168">Отдельные параметры конфигурации можно прочитать, указав иерархию параметров конфигурации, которую нужно использовать в качестве параметра индексатора:</span><span class="sxs-lookup"><span data-stu-id="6476b-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="6476b-169">Вы можете извлечь все разделы конфигурации с помощью метода <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> для извлечения коллекции ключей в определенном месте с синтаксисом, аналогичным `GetSection("section1")`, чтобы получить конфигурацию для section1 из предыдущего примера.</span><span class="sxs-lookup"><span data-stu-id="6476b-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="6476b-170">Строго типизированная конфигурация</span><span class="sxs-lookup"><span data-stu-id="6476b-170">Strongly typed configuration</span></span>

<span data-ttu-id="6476b-171">С помощью Web Forms можно было создать строго типизированный тип конфигурации, наследуемый от типа <xref:System.Configuration.ConfigurationSection> и связанных с ним типов.</span><span class="sxs-lookup"><span data-stu-id="6476b-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="6476b-172">`ConfigurationSection` позволяет настроить некоторые бизнес-правила и обработку для этих значений конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6476b-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="6476b-173">В ASP.NET Core можно указать иерархию классов, которая будет принимать значения конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6476b-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="6476b-174">Это классы:</span><span class="sxs-lookup"><span data-stu-id="6476b-174">These classes:</span></span>

* <span data-ttu-id="6476b-175">Наследовать от родительского класса не нужно.</span><span class="sxs-lookup"><span data-stu-id="6476b-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="6476b-176">Должны быть включены свойства `public`, соответствующие свойствам и ссылкам на типы для структуры конфигурации, которую вы хотите зафиксировать.</span><span class="sxs-lookup"><span data-stu-id="6476b-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="6476b-177">Для предыдущего образца *appsettings.js* можно было определить следующие классы для записи значений:</span><span class="sxs-lookup"><span data-stu-id="6476b-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

<span data-ttu-id="6476b-178">Эту иерархию классов можно заполнить, добавив следующую строку в метод `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="6476b-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="6476b-179">В оставшейся части приложения можно добавить входной параметр в классы или директиву `@inject` в шаблоны Razor типа `IOptions<MyConfig>` для получения строго типизированных параметров конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6476b-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="6476b-180">Свойство `IOptions<MyConfig>.Value` даст значение `MyConfig`, заполненное из параметров конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6476b-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="6476b-181">Дополнительные сведения о функции параметров можно найти в документе [Шаблон параметров в ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces).</span><span class="sxs-lookup"><span data-stu-id="6476b-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6476b-182">[Назад](middleware.md)
>[Вперед](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="6476b-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
