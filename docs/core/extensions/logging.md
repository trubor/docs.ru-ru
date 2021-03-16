---
title: Ведение журнала в .NET
author: IEvangelist
description: Узнайте, как использовать платформу ведения журналов, предоставляемую пакетом NuGet Microsoft.Extensions.Logging.
ms.author: dapine
ms.date: 02/19/2021
ms.openlocfilehash: 834331b9e103138012bbe91586d0d5a7c08654ce
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102402168"
---
# <a name="logging-in-net"></a><span data-ttu-id="de34a-103">Ведение журнала в .NET</span><span class="sxs-lookup"><span data-stu-id="de34a-103">Logging in .NET</span></span>

<span data-ttu-id="de34a-104">.NET поддерживает API ведения журнала, который работает с разными встроенными и сторонними поставщиками.</span><span class="sxs-lookup"><span data-stu-id="de34a-104">.NET supports a logging API that works with a variety of built-in and third-party logging providers.</span></span> <span data-ttu-id="de34a-105">В этой статье описано, как использовать в коде API ведения журналов, работающего со встроенными поставщиками.</span><span class="sxs-lookup"><span data-stu-id="de34a-105">This article shows how to use the logging API with built-in providers.</span></span> <span data-ttu-id="de34a-106">Большинство примеров кода, приведенных в этой статье, применимы к любому приложению .NET, которое использует [универсальный узел](generic-host.md).</span><span class="sxs-lookup"><span data-stu-id="de34a-106">Most of the code examples shown in this article apply to any .NET app that uses the [Generic Host](generic-host.md).</span></span> <span data-ttu-id="de34a-107">Если вы используете приложения, которые не используют универсальный узел, см. статью [Консольное приложение без размещения](#non-host-console-app).</span><span class="sxs-lookup"><span data-stu-id="de34a-107">For apps that don't use the Generic Host, see [Non-host console app](#non-host-console-app).</span></span>

## <a name="create-logs"></a><span data-ttu-id="de34a-108">Создание журналов</span><span class="sxs-lookup"><span data-stu-id="de34a-108">Create logs</span></span>

<span data-ttu-id="de34a-109">Чтобы создавать журналы, используйте объект <xref:Microsoft.Extensions.Logging.ILogger%601> из [внедрения зависимостей](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="de34a-109">To create logs, use an <xref:Microsoft.Extensions.Logging.ILogger%601> object from [dependency injection (DI)](dependency-injection.md).</span></span>

<span data-ttu-id="de34a-110">В следующем примере происходит следующее:</span><span class="sxs-lookup"><span data-stu-id="de34a-110">The following example:</span></span>

- <span data-ttu-id="de34a-111">Создает средство ведения журнала `ILogger<Worker>`, которое использует *категорию* журналов с полным именем типа `Worker`.</span><span class="sxs-lookup"><span data-stu-id="de34a-111">Creates a logger, `ILogger<Worker>`, which uses a log *category* of the fully qualified name of the type `Worker`.</span></span> <span data-ttu-id="de34a-112">Категория ведения журналов представляет строку, которая связана с каждым журналом.</span><span class="sxs-lookup"><span data-stu-id="de34a-112">The log category is a string that is associated with each log.</span></span>
- <span data-ttu-id="de34a-113">Вызывает метод <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> для ведения журналов на уровне `Information`.</span><span class="sxs-lookup"><span data-stu-id="de34a-113">Calls <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> to log at the `Information` level.</span></span> <span data-ttu-id="de34a-114">*Уровень* ведения журналов определяет степень серьезности или важности записанного в журнал события.</span><span class="sxs-lookup"><span data-stu-id="de34a-114">The Log *level* indicates the severity of the logged event.</span></span>

:::code language="csharp" source="snippets/configuration/worker-service/Worker.cs" range="9-24" highlight="12":::

<span data-ttu-id="de34a-115">[Уровни](#log-level) и [категории](#log-category) рассматриваются подробнее далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="de34a-115">[Levels](#log-level) and [categories](#log-category) are explained in more detail later in this article.</span></span>

## <a name="configure-logging"></a><span data-ttu-id="de34a-116">Настройка журнала</span><span class="sxs-lookup"><span data-stu-id="de34a-116">Configure logging</span></span>

<span data-ttu-id="de34a-117">Конфигурацию ведения журналов обычно предоставляет раздел `Logging` в файлах *appsettings*.`{Environment}` *.json*.</span><span class="sxs-lookup"><span data-stu-id="de34a-117">Logging configuration is commonly provided by the `Logging` section of *appsettings*.`{Environment}`*.json* files.</span></span> <span data-ttu-id="de34a-118">Шаблоны рабочей службы .NET создают следующий файл *appsettings.Development.json*:</span><span class="sxs-lookup"><span data-stu-id="de34a-118">The following *appsettings.Development.json* file is generated by the .NET Worker service templates:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.Development.json":::

<span data-ttu-id="de34a-119">В приведенном выше документе JSON:</span><span class="sxs-lookup"><span data-stu-id="de34a-119">In the preceding JSON:</span></span>

- <span data-ttu-id="de34a-120">Указаны категории `"Default"`, `"Microsoft"`и `"Microsoft.Hosting.Lifetime"`.</span><span class="sxs-lookup"><span data-stu-id="de34a-120">The `"Default"`, `"Microsoft"`, and `"Microsoft.Hosting.Lifetime"` categories are specified.</span></span>
- <span data-ttu-id="de34a-121">Категория `"Microsoft"` применяется ко всем категориям, начинающимся с `"Microsoft"`.</span><span class="sxs-lookup"><span data-stu-id="de34a-121">The `"Microsoft"` category applies to all categories that start with `"Microsoft"`.</span></span>
- <span data-ttu-id="de34a-122">Категория `"Microsoft"` задает ведение журналов на уровне `Warning` и более высоком.</span><span class="sxs-lookup"><span data-stu-id="de34a-122">The `"Microsoft"` category logs at log level `Warning` and higher.</span></span>
- <span data-ttu-id="de34a-123">Категория `"Microsoft.Hosting.Lifetime"` является более детальной по сравнению с `"Microsoft"`, поэтому при выборе категории `"Microsoft.Hosting.Lifetime"` ведение журналов осуществляется на уровне "Информация" и более высоком.</span><span class="sxs-lookup"><span data-stu-id="de34a-123">The `"Microsoft.Hosting.Lifetime"` category is more specific than the `"Microsoft"` category, so the `"Microsoft.Hosting.Lifetime"` category logs at log level "Information" and higher.</span></span>
- <span data-ttu-id="de34a-124">Поскольку конкретный поставщик журналов не указан, `LogLevel` применяется ко всем включенным поставщикам, за исключением [Windows EventLog](logging-providers.md#windows-eventlog).</span><span class="sxs-lookup"><span data-stu-id="de34a-124">A specific log provider is not specified, so `LogLevel` applies to all the enabled logging providers except for the [Windows EventLog](logging-providers.md#windows-eventlog).</span></span>

<span data-ttu-id="de34a-125">Свойство `Logging` может иметь свойство <xref:Microsoft.Extensions.Logging.LogLevel> и свойства поставщика журналов.</span><span class="sxs-lookup"><span data-stu-id="de34a-125">The `Logging` property can have <xref:Microsoft.Extensions.Logging.LogLevel> and log provider properties.</span></span> <span data-ttu-id="de34a-126">Свойство `LogLevel` указывает минимальный [уровень](#log-level) журнала для выбранных категорий.</span><span class="sxs-lookup"><span data-stu-id="de34a-126">The `LogLevel` specifies the minimum [level](#log-level) to log for selected categories.</span></span> <span data-ttu-id="de34a-127">В приведенном выше коде JSON заданы уровни ведения журнала `Information` и `Warning`.</span><span class="sxs-lookup"><span data-stu-id="de34a-127">In the preceding JSON, `Information` and `Warning` log levels are specified.</span></span> <span data-ttu-id="de34a-128">`LogLevel` определяет степень серьезности журнала и задается в диапазоне от 0 до 6:</span><span class="sxs-lookup"><span data-stu-id="de34a-128">`LogLevel` indicates the severity of the log and ranges from 0 to 6:</span></span>

<span data-ttu-id="de34a-129">`Trace` = 0, `Debug` = 1, `Information` = 2, `Warning` = 3, `Error` = 4, `Critical` = 5 и `None` = 6.</span><span class="sxs-lookup"><span data-stu-id="de34a-129">`Trace` = 0, `Debug` = 1, `Information` = 2, `Warning` = 3, `Error` = 4, `Critical` = 5, and `None` = 6.</span></span>

<span data-ttu-id="de34a-130">Если задан `LogLevel`, журналы будут вестись для сообщений с указанным и более высокими уровнями.</span><span class="sxs-lookup"><span data-stu-id="de34a-130">When a `LogLevel` is specified, logging is enabled for messages at the specified level and higher.</span></span> <span data-ttu-id="de34a-131">В приведенном выше коде JSON задается ведение журналов для категории `Default` для сообщений с уровнем `Information` и более высоким.</span><span class="sxs-lookup"><span data-stu-id="de34a-131">In the preceding JSON, the `Default` category is logged for `Information` and higher.</span></span> <span data-ttu-id="de34a-132">Например, в журнал записываются сообщения с уровнями `Information`, `Warning`, `Error` и `Critical`.</span><span class="sxs-lookup"><span data-stu-id="de34a-132">For example, `Information`, `Warning`, `Error`, and `Critical` messages are logged.</span></span> <span data-ttu-id="de34a-133">Если `LogLevel` не задан, по умолчанию устанавливается уровень ведения журналов `Information`.</span><span class="sxs-lookup"><span data-stu-id="de34a-133">If no `LogLevel` is specified, logging defaults to the `Information` level.</span></span> <span data-ttu-id="de34a-134">Дополнительные сведения см. в статье [Уровни ведения журналов](#log-level).</span><span class="sxs-lookup"><span data-stu-id="de34a-134">For more information, see [Log levels](#log-level).</span></span>

<span data-ttu-id="de34a-135">Свойство поставщика может задавать свойство `LogLevel`.</span><span class="sxs-lookup"><span data-stu-id="de34a-135">A provider property can specify a `LogLevel` property.</span></span> <span data-ttu-id="de34a-136">Свойство `LogLevel` поставщика определяет уровень ведения журналов для этого поставщика и переопределяет любые другие не относящиеся к поставщику параметры ведения журналов.</span><span class="sxs-lookup"><span data-stu-id="de34a-136">`LogLevel` under a provider specifies levels to log for that provider, and overrides the non-provider log settings.</span></span> <span data-ttu-id="de34a-137">Рассмотрите следующий файл *appsettings.json*:</span><span class="sxs-lookup"><span data-stu-id="de34a-137">Consider the following *appsettings.json* file:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.Staging.json":::

<span data-ttu-id="de34a-138">Параметры в `Logging.{ProviderName}.LogLevel` переопределяют параметры в `Logging.LogLevel`.</span><span class="sxs-lookup"><span data-stu-id="de34a-138">Settings in `Logging.{ProviderName}.LogLevel` override settings in `Logging.LogLevel`.</span></span> <span data-ttu-id="de34a-139">В приведенном выше коде JSON для поставщика `Debug` задается уровень ведения журнала по умолчанию `Information`:</span><span class="sxs-lookup"><span data-stu-id="de34a-139">In the preceding JSON, the `Debug` provider's default log level is set to `Information`:</span></span>

`Logging:Debug:LogLevel:Default:Information`

<span data-ttu-id="de34a-140">Приведенный выше параметр задает уровень ведения журнала `Information` для всех категорий `Logging:Debug:`, за исключением `Microsoft.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="de34a-140">The preceding setting specifies the `Information` log level for every `Logging:Debug:` category except `Microsoft.Hosting`.</span></span> <span data-ttu-id="de34a-141">Если задана конкретная категория, она переопределяет категорию по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="de34a-141">When a specific category is listed, the specific category overrides the default category.</span></span> <span data-ttu-id="de34a-142">В приведенном выше коде JSON категории `Logging:Debug:LogLevel` `"Microsoft.Hosting"` и `"Default"` переопределяют параметры в `Logging:LogLevel`.</span><span class="sxs-lookup"><span data-stu-id="de34a-142">In the preceding JSON, the `Logging:Debug:LogLevel` categories `"Microsoft.Hosting"` and `"Default"` override the settings in `Logging:LogLevel`</span></span>

<span data-ttu-id="de34a-143">Минимальный уровень ведения журнала можно указать для:</span><span class="sxs-lookup"><span data-stu-id="de34a-143">The minimum log level can be specified for any of:</span></span>

- <span data-ttu-id="de34a-144">конкретных поставщиков.  Например: `Logging:EventSource:LogLevel:Default:Information`</span><span class="sxs-lookup"><span data-stu-id="de34a-144">Specific providers:  For example, `Logging:EventSource:LogLevel:Default:Information`</span></span>
- <span data-ttu-id="de34a-145">конкретных категорий. Например: `Logging:LogLevel:Microsoft:Warning`</span><span class="sxs-lookup"><span data-stu-id="de34a-145">Specific categories: For example, `Logging:LogLevel:Microsoft:Warning`</span></span>
- <span data-ttu-id="de34a-146">всех поставщиков и всех категорий: `Logging:LogLevel:Default:Warning`</span><span class="sxs-lookup"><span data-stu-id="de34a-146">All providers and all categories: `Logging:LogLevel:Default:Warning`</span></span>

<span data-ttu-id="de34a-147">***Любые*** журналы с уровнем ниже минимального:</span><span class="sxs-lookup"><span data-stu-id="de34a-147">Any logs below the minimum level are ***not***:</span></span>

- <span data-ttu-id="de34a-148">не передаются поставщику;</span><span class="sxs-lookup"><span data-stu-id="de34a-148">Passed to the provider.</span></span>
- <span data-ttu-id="de34a-149">не записываются в журнал и не отображаются.</span><span class="sxs-lookup"><span data-stu-id="de34a-149">Logged or displayed.</span></span>

<span data-ttu-id="de34a-150">Чтобы отключить все журналы, укажите [LogLevel.None](xref:Microsoft.Extensions.Logging.LogLevel).</span><span class="sxs-lookup"><span data-stu-id="de34a-150">To suppress all logs, specify [LogLevel.None](xref:Microsoft.Extensions.Logging.LogLevel).</span></span> <span data-ttu-id="de34a-151">`LogLevel.None` имеет значение 6, то есть выше `LogLevel.Critical` (5).</span><span class="sxs-lookup"><span data-stu-id="de34a-151">`LogLevel.None` has a value of 6, which is higher than `LogLevel.Critical` (5).</span></span>

<span data-ttu-id="de34a-152">Если поставщик поддерживает [области журналов](#log-scopes), `IncludeScopes` определяет, включены ли они.</span><span class="sxs-lookup"><span data-stu-id="de34a-152">If a provider supports [log scopes](#log-scopes), `IncludeScopes` indicates whether they're enabled.</span></span> <span data-ttu-id="de34a-153">Дополнительные сведения см. в статье [Области журналов](#log-scopes).</span><span class="sxs-lookup"><span data-stu-id="de34a-153">For more information, see [log scopes](#log-scopes)</span></span>

<span data-ttu-id="de34a-154">Следующий файл *appsettings.json* содержит параметры для всех встроенных поставщиков:</span><span class="sxs-lookup"><span data-stu-id="de34a-154">The following *appsettings.json* file contains settings for all of the built-in providers:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.Production.json":::

<span data-ttu-id="de34a-155">В предыдущем примере:</span><span class="sxs-lookup"><span data-stu-id="de34a-155">In the preceding sample:</span></span>

- <span data-ttu-id="de34a-156">Категории и уровни не являются предлагаемыми значениями.</span><span class="sxs-lookup"><span data-stu-id="de34a-156">The categories and levels are not suggested values.</span></span> <span data-ttu-id="de34a-157">Этот пример представлен с целью продемонстрировать все поставщики по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="de34a-157">The sample is provided to show all the default providers.</span></span>
- <span data-ttu-id="de34a-158">Параметры в `Logging.{ProviderName}.LogLevel` переопределяют параметры в `Logging.LogLevel`.</span><span class="sxs-lookup"><span data-stu-id="de34a-158">Settings in `Logging.{ProviderName}.LogLevel` override settings in `Logging.LogLevel`.</span></span> <span data-ttu-id="de34a-159">Например, уровень в `Debug.LogLevel.Default` переопределяет уровень в `LogLevel.Default`.</span><span class="sxs-lookup"><span data-stu-id="de34a-159">For example, the level in `Debug.LogLevel.Default` overrides the level in `LogLevel.Default`.</span></span>
- <span data-ttu-id="de34a-160">Для каждого поставщика используется *псевдоним*.</span><span class="sxs-lookup"><span data-stu-id="de34a-160">Each provider's *alias* is used.</span></span> <span data-ttu-id="de34a-161">Каждый поставщик определяет *псевдоним*, используемый в конфигурации вместо полного имени типа.</span><span class="sxs-lookup"><span data-stu-id="de34a-161">Each provider defines an *alias* that can be used in configuration in place of the fully qualified type name.</span></span> <span data-ttu-id="de34a-162">Ниже перечислены псевдонимы встроенных поставщиков.</span><span class="sxs-lookup"><span data-stu-id="de34a-162">The built-in providers' aliases are:</span></span>
  - <span data-ttu-id="de34a-163">Консоль</span><span class="sxs-lookup"><span data-stu-id="de34a-163">Console</span></span>
  - <span data-ttu-id="de34a-164">Отладка</span><span class="sxs-lookup"><span data-stu-id="de34a-164">Debug</span></span>
  - <span data-ttu-id="de34a-165">EventSource</span><span class="sxs-lookup"><span data-stu-id="de34a-165">EventSource</span></span>
  - <span data-ttu-id="de34a-166">EventLog</span><span class="sxs-lookup"><span data-stu-id="de34a-166">EventLog</span></span>
  - <span data-ttu-id="de34a-167">AzureAppServicesFile</span><span class="sxs-lookup"><span data-stu-id="de34a-167">AzureAppServicesFile</span></span>
  - <span data-ttu-id="de34a-168">AzureAppServicesBlob</span><span class="sxs-lookup"><span data-stu-id="de34a-168">AzureAppServicesBlob</span></span>
  - <span data-ttu-id="de34a-169">ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="de34a-169">ApplicationInsights</span></span>

### <a name="set-log-level-by-command-line-environment-variables-and-other-configuration"></a><span data-ttu-id="de34a-170">Настройка уровня ведения журнала с помощью командной строки, переменных среды и других способов конфигурации</span><span class="sxs-lookup"><span data-stu-id="de34a-170">Set log level by command line, environment variables, and other configuration</span></span>

<span data-ttu-id="de34a-171">Уровень ведения журнала может задаваться любыми [поставщиками конфигурации](configuration-providers.md).</span><span class="sxs-lookup"><span data-stu-id="de34a-171">Log level can be set by any of the [configuration providers](configuration-providers.md).</span></span> <span data-ttu-id="de34a-172">Например, вы можете создать хранимую переменную среды с именем `Logging:LogLevel:Microsoft` и значением `Information`.</span><span class="sxs-lookup"><span data-stu-id="de34a-172">For example, you can create a persisted environment variable named `Logging:LogLevel:Microsoft` with a value of `Information`.</span></span>

## <a name="command-line"></a>[<span data-ttu-id="de34a-173">Командная строка</span><span class="sxs-lookup"><span data-stu-id="de34a-173">Command Line</span></span>](#tab/command-line)

<span data-ttu-id="de34a-174">Создайте хранимую переменную среды и присвойте ей значение уровня ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="de34a-174">Create and assign persisted environment variable, given the log level value.</span></span>

```CMD
:: Assigns the env var to the value
setx "Logging__LogLevel__Microsoft" "Information" /M
```

<span data-ttu-id="de34a-175">В *новом* экземпляре **командной строки** считайте эту переменную среды.</span><span class="sxs-lookup"><span data-stu-id="de34a-175">In a *new* instance of the **Command Prompt**, read the environment variable.</span></span>

```CMD
:: Prints the env var value
echo %Logging__LogLevel__Microsoft%
```

## <a name="powershell"></a>[<span data-ttu-id="de34a-176">PowerShell</span><span class="sxs-lookup"><span data-stu-id="de34a-176">PowerShell</span></span>](#tab/powershell)

<span data-ttu-id="de34a-177">Создайте хранимую переменную среды и присвойте ей значение уровня ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="de34a-177">Create and assign persisted environment variable, given the log level value.</span></span>

```powershell
# Assigns the env var to the value
[System.Environment]::SetEnvironmentVariable(
    "Logging__LogLevel__Microsoft", "Information", "Machine")
```

<span data-ttu-id="de34a-178">В *новом* экземпляре **PowerShell** считайте эту переменную среды.</span><span class="sxs-lookup"><span data-stu-id="de34a-178">In a *new* instance of the **PowerShell**, read the environment variable.</span></span>

```powershell
# Prints the env var value
[System.Environment]::GetEnvironmentVariable(
    "Logging__LogLevel__Microsoft", "Machine")
```

## <a name="bash"></a>[<span data-ttu-id="de34a-179">Bash</span><span class="sxs-lookup"><span data-stu-id="de34a-179">Bash</span></span>](#tab/bash)

<span data-ttu-id="de34a-180">Создайте хранимую переменную среды и присвойте ей значение уровня ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="de34a-180">Create and assign persisted environment variable, given the log level value.</span></span>

```Bash
# Assigns the env var to the value, persists it across sessions
echo export Logging__LogLevel__Microsoft="Information" >> ~/.bashrc && source ~/.bashrc
```

<span data-ttu-id="de34a-181">Считывание переменной среды.</span><span class="sxs-lookup"><span data-stu-id="de34a-181">To read the environment variable.</span></span>

```Bash
# Prints the env var value
echo $Logging__LogLevel__Microsoft

# Or use printenv:
# printenv Logging__LogLevel__Microsoft
```

> [!NOTE]
> <span data-ttu-id="de34a-182">При настройке переменных среды, имена которых содержат точки (`.`), просмотрите вопрос об экспорте переменной с точкой (.) на **форуме Stack Exchange** и [утвержденный ответ](https://unix.stackexchange.com/a/93533).</span><span class="sxs-lookup"><span data-stu-id="de34a-182">When configuring environment variables with names that contain `.` (periods), consider the "Exporting a variable with a dot (.) in it" question on **Stack Exchange** and its corresponding [accepted answer](https://unix.stackexchange.com/a/93533).</span></span>

---

<span data-ttu-id="de34a-183">Указанный выше параметр среды сохраняется в среде.</span><span class="sxs-lookup"><span data-stu-id="de34a-183">The preceding environment setting is persisted in the environment.</span></span> <span data-ttu-id="de34a-184">Чтобы проверить параметры при работе с приложением, созданным на базе шаблонов рабочей службы .NET, выполните команду `dotnet run` в каталоге проекта после назначения переменной среды.</span><span class="sxs-lookup"><span data-stu-id="de34a-184">To test the settings when using an app created with the .NET Worker service templates, use the `dotnet run` command in the project directory after the environment variable is assigned.</span></span>

```dotnetcli
dotnet run
```

> [!TIP]
> <span data-ttu-id="de34a-185">После настройки переменной среды перезапустите интегрированную среду разработки, чтобы гарантировать доступность добавленных переменных среды.</span><span class="sxs-lookup"><span data-stu-id="de34a-185">After setting an environment variable, restart your integrated development environment (IDE) to ensure that newly added environment variables are available.</span></span>

<span data-ttu-id="de34a-186">В [Службе приложений Azure](https://azure.microsoft.com/services/app-service/) выберите **Новый параметр приложения** на странице **Параметры > Конфигурация**.</span><span class="sxs-lookup"><span data-stu-id="de34a-186">On [Azure App Service](https://azure.microsoft.com/services/app-service/), select **New application setting** on the **Settings > Configuration** page.</span></span> <span data-ttu-id="de34a-187">Параметры приложения Службы приложений Azure:</span><span class="sxs-lookup"><span data-stu-id="de34a-187">Azure App Service application settings are:</span></span>

- <span data-ttu-id="de34a-188">Шифруются, когда они неактивны, и передаются по зашифрованному каналу.</span><span class="sxs-lookup"><span data-stu-id="de34a-188">Encrypted at rest and transmitted over an encrypted channel.</span></span>
- <span data-ttu-id="de34a-189">Предоставляются как переменные среды.</span><span class="sxs-lookup"><span data-stu-id="de34a-189">Exposed as environment variables.</span></span>

<span data-ttu-id="de34a-190">Дополнительные сведения о настройке значений конфигурации .NET с помощью переменных среды см. в разделе [Поставщик конфигурации переменных среды](configuration-providers.md#environment-variable-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="de34a-190">For more information on setting .NET configuration values using environment variables, see [environment variables](configuration-providers.md#environment-variable-configuration-provider).</span></span>

## <a name="how-filtering-rules-are-applied"></a><span data-ttu-id="de34a-191">Применение правил фильтрации</span><span class="sxs-lookup"><span data-stu-id="de34a-191">How filtering rules are applied</span></span>

<span data-ttu-id="de34a-192">При создании объекта <xref:Microsoft.Extensions.Logging.ILogger%601> объект <xref:Microsoft.Extensions.Logging.ILoggerFactory> выбирает одно правило для каждого поставщика, которое будет применено к этому средству ведения журналов.</span><span class="sxs-lookup"><span data-stu-id="de34a-192">When an <xref:Microsoft.Extensions.Logging.ILogger%601> object is created, the <xref:Microsoft.Extensions.Logging.ILoggerFactory> object selects a single rule per provider to apply to that logger.</span></span> <span data-ttu-id="de34a-193">Все сообщения, записываемые с помощью экземпляра `ILogger`, фильтруются на основе выбранных правил.</span><span class="sxs-lookup"><span data-stu-id="de34a-193">All messages written by an `ILogger` instance are filtered based on the selected rules.</span></span> <span data-ttu-id="de34a-194">Самое подробное правило для каждой пары поставщика и категории выбирается из списка доступных правил.</span><span class="sxs-lookup"><span data-stu-id="de34a-194">The most specific rule for each provider and category pair is selected from the available rules.</span></span>

<span data-ttu-id="de34a-195">При создании `ILogger` для данной категории для каждого поставщика используется приведенный далее алгоритм:</span><span class="sxs-lookup"><span data-stu-id="de34a-195">The following algorithm is used for each provider when an `ILogger` is created for a given category:</span></span>

- <span data-ttu-id="de34a-196">Выберите все правила, которые соответствуют поставщику или его псевдониму.</span><span class="sxs-lookup"><span data-stu-id="de34a-196">Select all rules that match the provider or its alias.</span></span> <span data-ttu-id="de34a-197">Если ничего не найдено, выберите все правила с пустым поставщиком.</span><span class="sxs-lookup"><span data-stu-id="de34a-197">If no match is found, select all rules with an empty provider.</span></span>
- <span data-ttu-id="de34a-198">В результатах предыдущего шага выберите правила с самым длинным соответствующим префиксом категории.</span><span class="sxs-lookup"><span data-stu-id="de34a-198">From the result of the preceding step, select rules with longest matching category prefix.</span></span> <span data-ttu-id="de34a-199">Если ничего не найдено, выберите все правила, которые не указывают категорию.</span><span class="sxs-lookup"><span data-stu-id="de34a-199">If no match is found, select all rules that don't specify a category.</span></span>
- <span data-ttu-id="de34a-200">Если выбрано несколько правил, примите **последнее**.</span><span class="sxs-lookup"><span data-stu-id="de34a-200">If multiple rules are selected, take the **last** one.</span></span>
- <span data-ttu-id="de34a-201">Если правила не выбраны, укажите минимальный уровень ведения журнала с помощью <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.SetMinimumLevel(Microsoft.Extensions.Logging.ILoggingBuilder,Microsoft.Extensions.Logging.LogLevel)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de34a-201">If no rules are selected, use <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.SetMinimumLevel(Microsoft.Extensions.Logging.ILoggingBuilder,Microsoft.Extensions.Logging.LogLevel)?displayProperty=nameWithType> to specify the minimum logging level.</span></span>

## <a name="log-category"></a><span data-ttu-id="de34a-202">Категория журнала</span><span class="sxs-lookup"><span data-stu-id="de34a-202">Log category</span></span>

<span data-ttu-id="de34a-203">При создании объекта `ILogger` указывается *категория*.</span><span class="sxs-lookup"><span data-stu-id="de34a-203">When an `ILogger` object is created, a *category* is specified.</span></span> <span data-ttu-id="de34a-204">Эта категория входит в состав каждого сообщения журнала, создаваемого этим экземпляром `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="de34a-204">That category is included with each log message created by that instance of `ILogger`.</span></span> <span data-ttu-id="de34a-205">Строка категории является необязательной, однако по соглашению следует использовать имя класса.</span><span class="sxs-lookup"><span data-stu-id="de34a-205">The category string is arbitrary, but the convention is to use the class name.</span></span> <span data-ttu-id="de34a-206">Например, если служба в приложении определяется следующим объектом, категория может иметь значение `"Example.DefaultService"`.</span><span class="sxs-lookup"><span data-stu-id="de34a-206">For example, in an application with a service define like the following object, the category might be `"Example.DefaultService"`:</span></span>

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger<DefaultService> _logger;

        public DefaultService(ILogger<DefaultService> logger) =>
            _logger = logger;

        // ...
    }
}
```

<span data-ttu-id="de34a-207">Чтобы явно указать категорию, вызовите <xref:Microsoft.Extensions.Logging.LoggerFactory.CreateLogger%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="de34a-207">To explicitly specify the category, call <xref:Microsoft.Extensions.Logging.LoggerFactory.CreateLogger%2A?displayProperty=nameWithType>:</span></span>

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger _logger;

        public DefaultService(ILoggerFactory loggerFactory) =>
            _logger = loggerFactory.CreateLogger("CustomCategory");

        // ...
    }
}
```

<span data-ttu-id="de34a-208">Вызов `CreateLogger` с фиксированным именем может быть полезным при использовании в нескольких классах или типах, чтобы события можно было упорядочить по категориям.</span><span class="sxs-lookup"><span data-stu-id="de34a-208">Calling `CreateLogger` with a fixed name can be useful when used in multiple classes/types so the events can be organized by category.</span></span>

<span data-ttu-id="de34a-209">Использование `ILogger<T>` эквивалентно вызову `CreateLogger` с полным именем типа `T`.</span><span class="sxs-lookup"><span data-stu-id="de34a-209">`ILogger<T>` is equivalent to calling `CreateLogger` with the fully qualified type name of `T`.</span></span>

## <a name="log-level"></a><span data-ttu-id="de34a-210">Уровень ведения журнала</span><span class="sxs-lookup"><span data-stu-id="de34a-210">Log level</span></span>

<span data-ttu-id="de34a-211">В следующей таблице перечислены значения <xref:Microsoft.Extensions.Logging.LogLevel>, используемый для удобства метод расширения `Log{LogLevel}`, а также приводятся сведения о предполагаемом применении:</span><span class="sxs-lookup"><span data-stu-id="de34a-211">The following table lists the <xref:Microsoft.Extensions.Logging.LogLevel> values, the convenience `Log{LogLevel}` extension method, and the suggested usage:</span></span>

| <span data-ttu-id="de34a-212">LogLevel</span><span class="sxs-lookup"><span data-stu-id="de34a-212">LogLevel</span></span> | <span data-ttu-id="de34a-213">Значение</span><span class="sxs-lookup"><span data-stu-id="de34a-213">Value</span></span> | <span data-ttu-id="de34a-214">Метод</span><span class="sxs-lookup"><span data-stu-id="de34a-214">Method</span></span> | <span data-ttu-id="de34a-215">Описание</span><span class="sxs-lookup"><span data-stu-id="de34a-215">Description</span></span> |
|--|--|--|--|
| [<span data-ttu-id="de34a-216">Трассировка</span><span class="sxs-lookup"><span data-stu-id="de34a-216">Trace</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="de34a-217">0</span><span class="sxs-lookup"><span data-stu-id="de34a-217">0</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogTrace%2A> | <span data-ttu-id="de34a-218">Содержит наиболее подробные сообщения.</span><span class="sxs-lookup"><span data-stu-id="de34a-218">Contain the most detailed messages.</span></span> <span data-ttu-id="de34a-219">Эти сообщения могут содержать конфиденциальные данные приложения.</span><span class="sxs-lookup"><span data-stu-id="de34a-219">These messages may contain sensitive app data.</span></span> <span data-ttu-id="de34a-220">Эти сообщения по умолчанию отключены, и их ***никогда*** не следует включать в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="de34a-220">These messages are disabled by default and should ***not*** be enabled in production.</span></span> |
| [<span data-ttu-id="de34a-221">Отладка</span><span class="sxs-lookup"><span data-stu-id="de34a-221">Debug</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="de34a-222">1</span><span class="sxs-lookup"><span data-stu-id="de34a-222">1</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> | <span data-ttu-id="de34a-223">Используется для отладки и разработки.</span><span class="sxs-lookup"><span data-stu-id="de34a-223">For debugging and development.</span></span> <span data-ttu-id="de34a-224">В рабочей среде следует использовать с осторожностью из-за большого объема.</span><span class="sxs-lookup"><span data-stu-id="de34a-224">Use with caution in production due to the high volume.</span></span> |
| [<span data-ttu-id="de34a-225">Информация</span><span class="sxs-lookup"><span data-stu-id="de34a-225">Information</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="de34a-226">2</span><span class="sxs-lookup"><span data-stu-id="de34a-226">2</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> | <span data-ttu-id="de34a-227">Отслеживание общего потока работы приложения.</span><span class="sxs-lookup"><span data-stu-id="de34a-227">Tracks the general flow of the app.</span></span> <span data-ttu-id="de34a-228">Может использоваться в долгосрочных целях.</span><span class="sxs-lookup"><span data-stu-id="de34a-228">May have long-term value.</span></span> |
| [<span data-ttu-id="de34a-229">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="de34a-229">Warning</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="de34a-230">3</span><span class="sxs-lookup"><span data-stu-id="de34a-230">3</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogWarning%2A> | <span data-ttu-id="de34a-231">Для нестандартных или непредвиденных событий.</span><span class="sxs-lookup"><span data-stu-id="de34a-231">For abnormal or unexpected events.</span></span> <span data-ttu-id="de34a-232">Обычно содержит ошибки или условия, которые не приводят к сбою приложения.</span><span class="sxs-lookup"><span data-stu-id="de34a-232">Typically includes errors or conditions that don't cause the app to fail.</span></span> |
| [<span data-ttu-id="de34a-233">Ошибка</span><span class="sxs-lookup"><span data-stu-id="de34a-233">Error</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="de34a-234">4</span><span class="sxs-lookup"><span data-stu-id="de34a-234">4</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogError%2A> | <span data-ttu-id="de34a-235">Для ошибок и исключений, которые не могут быть обработаны.</span><span class="sxs-lookup"><span data-stu-id="de34a-235">For errors and exceptions that cannot be handled.</span></span> <span data-ttu-id="de34a-236">Эти сообщения указывают на сбой текущих операции или запроса, а не на ошибку уровня приложения.</span><span class="sxs-lookup"><span data-stu-id="de34a-236">These messages indicate a failure in the current operation or request, not an app-wide failure.</span></span> |
| [<span data-ttu-id="de34a-237">Критическая</span><span class="sxs-lookup"><span data-stu-id="de34a-237">Critical</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="de34a-238">5</span><span class="sxs-lookup"><span data-stu-id="de34a-238">5</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogCritical%2A> | <span data-ttu-id="de34a-239">Для сбоев, которые требуют немедленного внимания.</span><span class="sxs-lookup"><span data-stu-id="de34a-239">For failures that require immediate attention.</span></span> <span data-ttu-id="de34a-240">Примеры: потеря данных, нехватка места на диске.</span><span class="sxs-lookup"><span data-stu-id="de34a-240">Examples: data loss scenarios, out of disk space.</span></span> |
| [<span data-ttu-id="de34a-241">None</span><span class="sxs-lookup"><span data-stu-id="de34a-241">None</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="de34a-242">6</span><span class="sxs-lookup"><span data-stu-id="de34a-242">6</span></span> |  | <span data-ttu-id="de34a-243">Указывает, что сообщения не должны записываться.</span><span class="sxs-lookup"><span data-stu-id="de34a-243">Specifies that no messages should be written.</span></span> |

<span data-ttu-id="de34a-244">В приведенной выше таблице значения `LogLevel` приведены в порядке от самого низкого к самому высокому уровню серьезности.</span><span class="sxs-lookup"><span data-stu-id="de34a-244">In the previous table, the `LogLevel` is listed from lowest to highest severity.</span></span>

<span data-ttu-id="de34a-245">Первый параметр метода [Log](xref:Microsoft.Extensions.Logging.LoggerExtensions), <xref:Microsoft.Extensions.Logging.LogLevel>, указывает на степень серьезности журнала.</span><span class="sxs-lookup"><span data-stu-id="de34a-245">The [Log](xref:Microsoft.Extensions.Logging.LoggerExtensions) method's first parameter, <xref:Microsoft.Extensions.Logging.LogLevel>, indicates the severity of the log.</span></span> <span data-ttu-id="de34a-246">Вместо вызова `Log(LogLevel, ...)` большинство разработчиков вызывают методы расширения [Log{LogLevel}](xref:Microsoft.Extensions.Logging.LoggerExtensions).</span><span class="sxs-lookup"><span data-stu-id="de34a-246">Rather than calling `Log(LogLevel, ...)`, most developers call the [Log{LogLevel}](xref:Microsoft.Extensions.Logging.LoggerExtensions) extension methods.</span></span> <span data-ttu-id="de34a-247">Методы расширения `Log{LogLevel}` [вызывают метод Log и задают значение LogLevel](https://github.com/dotnet/extensions/blob/release/3.1/src/Logging/Logging.Abstractions/src/LoggerExtensions.cs).</span><span class="sxs-lookup"><span data-stu-id="de34a-247">The `Log{LogLevel}` extension methods [call the Log method and specify the LogLevel](https://github.com/dotnet/extensions/blob/release/3.1/src/Logging/Logging.Abstractions/src/LoggerExtensions.cs).</span></span> <span data-ttu-id="de34a-248">Например, следующие два вызова ведения журнала функционально эквивалентны и позволяют получить одинаковые журналы:</span><span class="sxs-lookup"><span data-stu-id="de34a-248">For example, the following two logging calls are functionally equivalent and produce the same log:</span></span>

```csharp
public void LogDetails()
{
    var logMessage = "Details for log.";

    _logger.Log(LogLevel.Information, AppLogEvents.Details, logMessage);
    _logger.LogInformation(AppLogEvents.Details, logMessage);
}
```

<span data-ttu-id="de34a-249">`AppLogEvents.Details` содержит идентификатор события и неявным образом представляется постоянным значением <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="de34a-249">`AppLogEvents.Details` is the event ID, and is implicitly represented by a constant <xref:System.Int32> value.</span></span> <span data-ttu-id="de34a-250">`AppLogEvents` обозначает класс, который предоставляет разные именованные константы для идентификаторов и отображается в разделе [Идентификатор события журнала](#log-event-id).</span><span class="sxs-lookup"><span data-stu-id="de34a-250">`AppLogEvents` is a class that exposes various named identifier constants and is displayed in the [Log event ID](#log-event-id) section.</span></span>

<span data-ttu-id="de34a-251">Следующий код создает журналы `Information`и `Warning`:</span><span class="sxs-lookup"><span data-stu-id="de34a-251">The following code creates `Information` and `Warning` logs:</span></span>

```csharp
public async Task<T> GetAsync<T>(string id)
{
    _logger.LogInformation(AppLogEvents.Read, "Reading value for {Id}", id);

    var result = await _repository.GetAsync(id);
    if (result is null)
    {
        _logger.LogWarning(AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
    }

    return result;
}
```

<span data-ttu-id="de34a-252">В коде выше первый параметр, `AppLogEvents.Read`, — это `Log{LogLevel}`[идентификатор события журнала](#log-event-id).</span><span class="sxs-lookup"><span data-stu-id="de34a-252">In the preceding code, the first `Log{LogLevel}` parameter,`AppLogEvents.Read`, is the [Log event ID](#log-event-id).</span></span> <span data-ttu-id="de34a-253">Второй параметр — это шаблон сообщения с заполнителями для значений аргументов, предоставляемых оставшимися параметрами метода.</span><span class="sxs-lookup"><span data-stu-id="de34a-253">The second parameter is a message template with placeholders for argument values provided by the remaining method parameters.</span></span> <span data-ttu-id="de34a-254">Параметры метода рассматриваются более подробно в разделе, посвященном [шаблону сообщений](#log-message-template) далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="de34a-254">The method parameters are explained in the [message template](#log-message-template) section later in this article.</span></span>

<span data-ttu-id="de34a-255">Настройте подходящий уровень ведения журнала и вызовите правильные методы `Log{LogLevel}`, чтобы управлять объемом данных журнала, записываемых на определенный носитель.</span><span class="sxs-lookup"><span data-stu-id="de34a-255">Configure the appropriate log level and call the correct `Log{LogLevel}` methods to control how much log output is written to a particular storage medium.</span></span> <span data-ttu-id="de34a-256">Пример:</span><span class="sxs-lookup"><span data-stu-id="de34a-256">For example:</span></span>

- <span data-ttu-id="de34a-257">В рабочей среде:</span><span class="sxs-lookup"><span data-stu-id="de34a-257">In production:</span></span>
  - <span data-ttu-id="de34a-258">При ведении журнала на уровнях `Trace` или `Information` создается большой объем подробных сообщений журнала.</span><span class="sxs-lookup"><span data-stu-id="de34a-258">Logging at the `Trace` or `Information` levels produces a high-volume of detailed log messages.</span></span> <span data-ttu-id="de34a-259">Чтобы контролировать затраты и не превысить лимиты объема хранилища данных, записывайте сообщения на уровнях `Trace` и `Information` в хранилище данных с низкими затратами и большим объемом.</span><span class="sxs-lookup"><span data-stu-id="de34a-259">To control costs and not exceed data storage limits, log `Trace` and `Information` level messages to a high-volume, low-cost data store.</span></span> <span data-ttu-id="de34a-260">Рассмотрите возможность ограничения уровней `Trace` и `Information` конкретными категориями.</span><span class="sxs-lookup"><span data-stu-id="de34a-260">Consider limiting `Trace` and `Information` to specific categories.</span></span>
  - <span data-ttu-id="de34a-261">При ведении журналов на уровнях с `Warning` по `Critical` создается немного сообщений.</span><span class="sxs-lookup"><span data-stu-id="de34a-261">Logging at `Warning` through `Critical` levels should produce few log messages.</span></span>
    - <span data-ttu-id="de34a-262">При этом стоимость и ограничения хранения, как правило, не важны.</span><span class="sxs-lookup"><span data-stu-id="de34a-262">Costs and storage limits usually aren't a concern.</span></span>
    - <span data-ttu-id="de34a-263">Меньший объем журналов позволяет выбирать среди большего количества вариантов хранения данных.</span><span class="sxs-lookup"><span data-stu-id="de34a-263">Few logs allow more flexibility in data store choices.</span></span>
- <span data-ttu-id="de34a-264">В среде разработки:</span><span class="sxs-lookup"><span data-stu-id="de34a-264">In development:</span></span>
  - <span data-ttu-id="de34a-265">Задайте значение `Warning`.</span><span class="sxs-lookup"><span data-stu-id="de34a-265">Set to `Warning`.</span></span>
  - <span data-ttu-id="de34a-266">Добавляйте сообщения уровней `Trace` или `Information` при устранении неполадок.</span><span class="sxs-lookup"><span data-stu-id="de34a-266">Add `Trace` or `Information` messages when troubleshooting.</span></span> <span data-ttu-id="de34a-267">Чтобы ограничить объем выходных данных, задавайте уровни `Trace` или `Information` только для исследуемых категорий.</span><span class="sxs-lookup"><span data-stu-id="de34a-267">To limit output, set `Trace` or `Information` only for the categories under investigation.</span></span>

<span data-ttu-id="de34a-268">Приведенный ниже код JSON задает уровень `Logging:Console:LogLevel:Microsoft:Information`:</span><span class="sxs-lookup"><span data-stu-id="de34a-268">The following JSON sets `Logging:Console:LogLevel:Microsoft:Information`:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.MSFT.json":::

## <a name="log-event-id"></a><span data-ttu-id="de34a-269">Идентификатор события журнала</span><span class="sxs-lookup"><span data-stu-id="de34a-269">Log event ID</span></span>

<span data-ttu-id="de34a-270">Каждый журнал может содержать *идентификатор события*, где <xref:Microsoft.Extensions.Logging.EventId> представляет структуру с идентификатором (`Id`) и необязательными свойствами `Name` только для чтения.</span><span class="sxs-lookup"><span data-stu-id="de34a-270">Each log can specify an *event identifer*, the <xref:Microsoft.Extensions.Logging.EventId> is a structure with an `Id` and optional `Name` readonly properties.</span></span> <span data-ttu-id="de34a-271">В этом примере исходного кода для определения идентификаторов событий используется класс `AppLogEvents`.</span><span class="sxs-lookup"><span data-stu-id="de34a-271">The sample source code uses the `AppLogEvents` class to define event IDs:</span></span>

```csharp
internal static class AppLogEvents
{
    internal const int Create = 1000;
    internal const int Read = 1001;
    internal const int Update = 1002;
    internal const int Delete = 1003;

    internal const int Details = 3000;
    internal const int Error = 3001;

    internal const int ReadNotFound = 4000;
    internal const int UpdateNotFound = 4001;

    // ...
}
```

<span data-ttu-id="de34a-272">Идентификатор события связывает набор событий.</span><span class="sxs-lookup"><span data-stu-id="de34a-272">An event ID associates a set of events.</span></span> <span data-ttu-id="de34a-273">Например, все журналы, связанные с чтением значений из репозитория, могут иметь идентификатор `1001`.</span><span class="sxs-lookup"><span data-stu-id="de34a-273">For example, all logs related to reading values from a repository might be `1001`.</span></span>

<span data-ttu-id="de34a-274">Поставщик ведения журналов может записывать идентификатор события в поле идентификатора, в сообщении журнала, или вообще не сохранять его.</span><span class="sxs-lookup"><span data-stu-id="de34a-274">The logging provider may log the event ID in an ID field, in the logging message, or not at all.</span></span> <span data-ttu-id="de34a-275">Поставщик Debug не отображает идентификаторы событий.</span><span class="sxs-lookup"><span data-stu-id="de34a-275">The Debug provider doesn't show event IDs.</span></span> <span data-ttu-id="de34a-276">Поставщик Console отображает идентификаторы событий в квадратных скобках после категории:</span><span class="sxs-lookup"><span data-stu-id="de34a-276">The console provider shows event IDs in brackets after the category:</span></span>

```console
info: Example.DefaultService.GetAsync[1001]
      Reading value for a1b2c3
warn: Example.DefaultService.GetAsync[4000]
      GetAsync(a1b2c3) not found
```

<span data-ttu-id="de34a-277">Некоторые поставщики ведения журнала хранят идентификатор события в поле, что позволяет выполнять фильтрацию по идентификатору.</span><span class="sxs-lookup"><span data-stu-id="de34a-277">Some logging providers store the event ID in a field, which allows for filtering on the ID.</span></span>

## <a name="log-message-template"></a><span data-ttu-id="de34a-278">Шаблон сообщения журнала</span><span class="sxs-lookup"><span data-stu-id="de34a-278">Log message template</span></span>

<span data-ttu-id="de34a-279">Каждый API ведения журнала использует шаблон сообщения.</span><span class="sxs-lookup"><span data-stu-id="de34a-279">Each log API uses a message template.</span></span> <span data-ttu-id="de34a-280">Шаблон сообщения может содержать заполнители, для которых предоставляются аргументы.</span><span class="sxs-lookup"><span data-stu-id="de34a-280">The message template can contain placeholders for which arguments are provided.</span></span> <span data-ttu-id="de34a-281">Используйте для заполнителей имена, а не числа.</span><span class="sxs-lookup"><span data-stu-id="de34a-281">Use names for the placeholders, not numbers.</span></span> <span data-ttu-id="de34a-282">Параметры, используемые для предоставления значений, определяются порядком заполнителей, а не их именами.</span><span class="sxs-lookup"><span data-stu-id="de34a-282">The order of placeholders, not their names, determines which parameters are used to provide their values.</span></span> <span data-ttu-id="de34a-283">В приведенном ниже коде имена параметров идут не по порядку в шаблоне сообщения:</span><span class="sxs-lookup"><span data-stu-id="de34a-283">In the following code, the parameter names are out of sequence in the message template:</span></span>

```csharp
string p1 = "param1";
string p2 = "param2";
_logger.LogInformation("Parameter values: {p2}, {p1}", p1, p2);
```

<span data-ttu-id="de34a-284">Приведенный выше код создает сообщение журнала со значениями параметров в определенном порядке:</span><span class="sxs-lookup"><span data-stu-id="de34a-284">The preceding code creates a log message with the parameter values in sequence:</span></span>

```text
Parameter values: param1, param2
```

<span data-ttu-id="de34a-285">Такой подход позволяет поставщикам ведения журнала реализовывать [семантическое или структурированное ведение журналов](https://github.com/NLog/NLog/wiki/How-to-use-structured-logging).</span><span class="sxs-lookup"><span data-stu-id="de34a-285">This approach allows logging providers to implement [semantic or structured logging](https://github.com/NLog/NLog/wiki/How-to-use-structured-logging).</span></span> <span data-ttu-id="de34a-286">Сами аргументы передаются в систему ведения журналов, а не только в отформатированный шаблон сообщения.</span><span class="sxs-lookup"><span data-stu-id="de34a-286">The arguments themselves are passed to the logging system, not just the formatted message template.</span></span> <span data-ttu-id="de34a-287">Это позволяет поставщикам ведения журнала хранить значения параметров как поля.</span><span class="sxs-lookup"><span data-stu-id="de34a-287">This enables logging providers to store the parameter values as fields.</span></span> <span data-ttu-id="de34a-288">Давайте рассмотрим следующий метод средства ведения журнала:</span><span class="sxs-lookup"><span data-stu-id="de34a-288">Consider the following logger method:</span></span>

```csharp
_logger.LogInformation("Getting item {Id} at {RunTime}", id, DateTime.Now);
```

<span data-ttu-id="de34a-289">Например, при ведении журнала в хранилище таблиц Azure:</span><span class="sxs-lookup"><span data-stu-id="de34a-289">For example, when logging to Azure Table Storage:</span></span>

- <span data-ttu-id="de34a-290">каждая сущность таблицы Azure может иметь свойства `ID` и `RunTime`;</span><span class="sxs-lookup"><span data-stu-id="de34a-290">Each Azure Table entity can have `ID` and `RunTime` properties.</span></span>
- <span data-ttu-id="de34a-291">использование таблиц со свойствами позволяет упростить выполнение запросов к данным журнала.</span><span class="sxs-lookup"><span data-stu-id="de34a-291">Tables with properties simplify queries on logged data.</span></span> <span data-ttu-id="de34a-292">Например, с помощью запроса можно находить все журналы в пределах определенного диапазона `RunTime`, не анализируя время ожидания текстового сообщения.</span><span class="sxs-lookup"><span data-stu-id="de34a-292">For example, a query can find all logs within a particular `RunTime` range without having to parse the time out of the text message.</span></span>

## <a name="log-exceptions"></a><span data-ttu-id="de34a-293">Запись исключений в журнал</span><span class="sxs-lookup"><span data-stu-id="de34a-293">Log exceptions</span></span>

<span data-ttu-id="de34a-294">Методы средства ведения журнала имеют перегрузки, которые принимают параметр исключения:</span><span class="sxs-lookup"><span data-stu-id="de34a-294">The logger methods have overloads that take an exception parameter:</span></span>

```csharp
public void Test(string id)
{
    try
    {
        if (id == "none")
        {
            throw new Exception("Default Id detected.");
        }
    }
    catch (Exception ex)
    {
        _logger.LogWarning(
            AppLogEvents.Error, ex,
            "Failed to process iteration: {Id}", id)
    }
}
```

<span data-ttu-id="de34a-295">Принципы записи исключений в журнал зависят от конкретного поставщика.</span><span class="sxs-lookup"><span data-stu-id="de34a-295">Exception logging is provider-specific.</span></span>

### <a name="default-log-level"></a><span data-ttu-id="de34a-296">Уровень ведения журнала по умолчанию</span><span class="sxs-lookup"><span data-stu-id="de34a-296">Default log level</span></span>

<span data-ttu-id="de34a-297">Если не задан уровень ведения журнала по умолчанию, то по умолчанию используется уровень `Information`.</span><span class="sxs-lookup"><span data-stu-id="de34a-297">If the default log level is not set, the default log level value is `Information`.</span></span>

<span data-ttu-id="de34a-298">Давайте рассмотрим следующее приложение службы рабочей роли:</span><span class="sxs-lookup"><span data-stu-id="de34a-298">For example, consider the following worker service app:</span></span>

- <span data-ttu-id="de34a-299">Создано на основе шаблонов рабочей роли .NET.</span><span class="sxs-lookup"><span data-stu-id="de34a-299">Created with the .NET Worker templates.</span></span>
- <span data-ttu-id="de34a-300">файлы *appsettings.json* и *appsettings.Development.json* были удалены или переименованы.</span><span class="sxs-lookup"><span data-stu-id="de34a-300">*appsettings.json* and *appsettings.Development.json* deleted or renamed.</span></span>

<span data-ttu-id="de34a-301">В рамках приведенной выше конфигурации при переходе на страницу сведений о конфиденциальности или домашнюю страницу создается множество сообщений с уровнем `Trace`, `Debug` и `Information`, в имени категории которых используется `Microsoft`.</span><span class="sxs-lookup"><span data-stu-id="de34a-301">With the preceding setup, navigating to the privacy or home page produces many `Trace`, `Debug`, and `Information`  messages with `Microsoft` in the category name.</span></span>

<span data-ttu-id="de34a-302">В следующем коде задается уровень ведения журнала по умолчанию в том случае, если этот уровень не определен в конфигурации:</span><span class="sxs-lookup"><span data-stu-id="de34a-302">The following code sets the default log level when the default log level is not set in configuration:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging => logging.SetMinimumLevel(LogLevel.Warning));
}
```

### <a name="filter-function"></a><span data-ttu-id="de34a-303">Функция фильтрации</span><span class="sxs-lookup"><span data-stu-id="de34a-303">Filter function</span></span>

<span data-ttu-id="de34a-304">Функция фильтрации вызывается для всех поставщиков и категорий, которым в конфигурации и (или) коде не назначены правила:</span><span class="sxs-lookup"><span data-stu-id="de34a-304">A filter function is invoked for all providers and categories that don't have rules assigned to them by configuration or code:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddFilter((provider, category, logLevel) =>
                {
                    return provider.Contains("ConsoleLoggerProvider")
                        && (category.Contains("Example") || category.Contains("Microsoft"))
                        && logLevel >= LogLevel.Information;
                }));
}
```

<span data-ttu-id="de34a-305">Приведенный выше код отображает журналы консоли, если категория содержит `Example` или `Microsoft` и задан уровень ведения журнала `Information` или выше.</span><span class="sxs-lookup"><span data-stu-id="de34a-305">The preceding code displays console logs when the category contains `Example` or `Microsoft` and the log level is `Information` or higher.</span></span>

## <a name="log-scopes"></a><span data-ttu-id="de34a-306">Области журналов</span><span class="sxs-lookup"><span data-stu-id="de34a-306">Log scopes</span></span>

 <span data-ttu-id="de34a-307">*Область* может группировать набор логических операций.</span><span class="sxs-lookup"><span data-stu-id="de34a-307">A *scope* can group a set of logical operations.</span></span> <span data-ttu-id="de34a-308">Эту возможность можно использовать для присоединения одних и тех же данных к каждому журналу, созданному как часть набора.</span><span class="sxs-lookup"><span data-stu-id="de34a-308">This grouping can be used to attach the same data to each log that's created as part of a set.</span></span> <span data-ttu-id="de34a-309">Например, каждый журнал, созданный в ходе обработки транзакции, может включать идентификатор транзакции.</span><span class="sxs-lookup"><span data-stu-id="de34a-309">For example, every log created as part of processing a transaction can include the transaction ID.</span></span>

<span data-ttu-id="de34a-310">Область:</span><span class="sxs-lookup"><span data-stu-id="de34a-310">A scope:</span></span>

- <span data-ttu-id="de34a-311">имеет тип <xref:System.IDisposable>, который возвращается методом <xref:Microsoft.Extensions.Logging.ILogger.BeginScope%2A>;</span><span class="sxs-lookup"><span data-stu-id="de34a-311">Is an <xref:System.IDisposable> type that's returned by the <xref:Microsoft.Extensions.Logging.ILogger.BeginScope%2A> method.</span></span>
- <span data-ttu-id="de34a-312">действует вплоть до удаления.</span><span class="sxs-lookup"><span data-stu-id="de34a-312">Lasts until it's disposed.</span></span>

<span data-ttu-id="de34a-313">Области поддерживаются следующими поставщиками:</span><span class="sxs-lookup"><span data-stu-id="de34a-313">The following providers support scopes:</span></span>

- `Console`
- [<span data-ttu-id="de34a-314">AzureAppServicesFile и AzureAppServicesBlob</span><span class="sxs-lookup"><span data-stu-id="de34a-314">AzureAppServicesFile and AzureAppServicesBlob</span></span>](xref:Microsoft.Extensions.Logging.AzureAppServices.BatchingLoggerOptions.IncludeScopes)

<span data-ttu-id="de34a-315">Используйте область, заключив вызовы средства ведения журналов в блок `using`:</span><span class="sxs-lookup"><span data-stu-id="de34a-315">Use a scope by wrapping logger calls in a `using` block:</span></span>

```csharp
public async Task<T> GetAsync<T>(string id)
{
    T result;

    using (_logger.BeginScope("using block message"))
    {
        _logger.LogInformation(
            AppLogEvents.Read, "Reading value for {Id}", id);

        var result = await _repository.GetAsync(id);
        if (result is null)
        {
            _logger.LogWarning(
                AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
        }
    }

    return result;
}
```

<span data-ttu-id="de34a-316">Следующий код JSON предоставляет области для поставщика Console:</span><span class="sxs-lookup"><span data-stu-id="de34a-316">The following JSON enables scopes for the console provider:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.IncludeScopes.json" highlight="9":::

<span data-ttu-id="de34a-317">Следующий код предоставляет области для поставщика Console:</span><span class="sxs-lookup"><span data-stu-id="de34a-317">The following code enables scopes for the console provider:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging((_, logging) =>
                logging.ClearProviders()
                    .AddConsole(options => options.IncludeScopes = true));
}
```

## <a name="non-host-console-app"></a><span data-ttu-id="de34a-318">Консольные приложения без размещения</span><span class="sxs-lookup"><span data-stu-id="de34a-318">Non-host console app</span></span>

<span data-ttu-id="de34a-319">Код ведения журнала для приложений без [универсального узла](generic-host.md) отличается тем, как [добавляются поставщики](logging-providers.md#built-in-logging-providers) и [создаются средства ведения журнала](#create-logs).</span><span class="sxs-lookup"><span data-stu-id="de34a-319">Logging code for apps without a [Generic Host](generic-host.md) differs in the way [providers are added](logging-providers.md#built-in-logging-providers) and [loggers are created](#create-logs).</span></span> <span data-ttu-id="de34a-320">В консольном приложении, не использующем узел, вызовите метод расширения `Add{provider name}` поставщика при создании `LoggerFactory`:</span><span class="sxs-lookup"><span data-stu-id="de34a-320">In a non-host console app, call the provider's `Add{provider name}` extension method while creating a `LoggerFactory`:</span></span>

```csharp
class Program
{
    static void Main(string[] args)
    {
        using var loggerFactory = LoggerFactory.Create(builder =>
        {
            builder
                .AddFilter("Microsoft", LogLevel.Warning)
                .AddFilter("System", LogLevel.Warning)
                .AddFilter("LoggingConsoleApp.Program", LogLevel.Debug)
                .AddConsole();
        });

        ILogger logger = loggerFactory.CreateLogger<Program>();
        logger.LogInformation("Example log message");
    }
}
```

<span data-ttu-id="de34a-321">Объект `loggerFactory` используется для создания экземпляра <xref:Microsoft.Extensions.Logging.ILogger>.</span><span class="sxs-lookup"><span data-stu-id="de34a-321">The `loggerFactory` object is used to create an <xref:Microsoft.Extensions.Logging.ILogger> instance.</span></span>

## <a name="create-logs-in-main"></a><span data-ttu-id="de34a-322">Создание журналов в классе Main</span><span class="sxs-lookup"><span data-stu-id="de34a-322">Create logs in Main</span></span>

<span data-ttu-id="de34a-323">Следующий код создает журналы в `Main`, получая экземпляр `ILogger` путем внедрения зависимостей после создания узла:</span><span class="sxs-lookup"><span data-stu-id="de34a-323">The following code logs in `Main` by getting an `ILogger` instance from DI after building the host:</span></span>

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;

class Program
{
    static Task Main(string[] args)
    {
        IHost host = Host.CreateDefaultBuilder(args).Build();

        var logger = host.Services.GetRequiredService<ILogger<Program>>();
        logger.LogInformation("Host created.");

        return host.RunAsync();
    }
}
```

### <a name="no-asynchronous-logger-methods"></a><span data-ttu-id="de34a-324">Асинхронные методы ведения журналов не выполняются</span><span class="sxs-lookup"><span data-stu-id="de34a-324">No asynchronous logger methods</span></span>

<span data-ttu-id="de34a-325">Скорость ведения журналов не должна влиять на производительность выполнения асинхронного кода.</span><span class="sxs-lookup"><span data-stu-id="de34a-325">Logging should be so fast that it isn't worth the performance cost of asynchronous code.</span></span> <span data-ttu-id="de34a-326">Если хранилище данных, предназначенное для регистрации сообщений журнала, работает медленно, сначала записывайте эти сообщения в быстродействующее хранилище,</span><span class="sxs-lookup"><span data-stu-id="de34a-326">If a logging data store is slow, don't write to it directly.</span></span> <span data-ttu-id="de34a-327">а затем перемещайте их в медленное хранилище.</span><span class="sxs-lookup"><span data-stu-id="de34a-327">Consider writing the log messages to a fast store initially, then moving them to the slow store later.</span></span> <span data-ttu-id="de34a-328">Например, если вы записываете журналы в SQL Server, вам не нужно делать это непосредственно в методе `Log`, так как методы `Log` являются синхронными.</span><span class="sxs-lookup"><span data-stu-id="de34a-328">For example, when logging to SQL Server, don't do so directly in a `Log` method, since the `Log` methods are synchronous.</span></span> <span data-ttu-id="de34a-329">Вместо этого синхронно добавьте сообщения журнала в очередь в памяти, и фоновый рабочий поток извлечет сообщения из очереди для выполнения асинхронных операций передачи данных в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="de34a-329">Instead, synchronously add log messages to an in-memory queue and have a background worker pull the messages out of the queue to do the asynchronous work of pushing data to SQL Server.</span></span>

## <a name="change-log-levels-in-a-running-app"></a><span data-ttu-id="de34a-330">Изменение уровней ведения журнала в работающем приложении</span><span class="sxs-lookup"><span data-stu-id="de34a-330">Change log levels in a running app</span></span>

<span data-ttu-id="de34a-331">API ведения журнала не включает сценарий для изменения уровней журнала во время работы приложения.</span><span class="sxs-lookup"><span data-stu-id="de34a-331">The Logging API doesn't include a scenario to change log levels while an app is running.</span></span> <span data-ttu-id="de34a-332">Однако некоторые поставщики конфигурации могут перезагружать конфигурацию, что немедленно влияет на конфигурацию ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="de34a-332">However, some configuration providers are capable of reloading configuration, which takes immediate effect on logging configuration.</span></span> <span data-ttu-id="de34a-333">Например, [поставщик конфигурации файлов](configuration-providers.md#file-configuration-provider) по умолчанию перезагружает конфигурацию ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="de34a-333">For example, the [File Configuration Provider](configuration-providers.md#file-configuration-provider) reloads logging configuration by default.</span></span> <span data-ttu-id="de34a-334">Если конфигурация изменяется в коде во время выполнения приложения, приложение может вызвать [IConfigurationRoot.Reload](xref:Microsoft.Extensions.Configuration.IConfigurationRoot.Reload%2A), чтобы обновить конфигурацию ведения журнала приложения.</span><span class="sxs-lookup"><span data-stu-id="de34a-334">If configuration is changed in code while an app is running, the app can call [IConfigurationRoot.Reload](xref:Microsoft.Extensions.Configuration.IConfigurationRoot.Reload%2A) to update the app's logging configuration.</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="de34a-335">Пакеты NuGet</span><span class="sxs-lookup"><span data-stu-id="de34a-335">NuGet packages</span></span>

<span data-ttu-id="de34a-336">Интерфейсы <xref:Microsoft.Extensions.Logging.ILogger%601> и <xref:Microsoft.Extensions.Logging.ILoggerFactory>, а также их реализации включены в пакет SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="de34a-336">The <xref:Microsoft.Extensions.Logging.ILogger%601> and <xref:Microsoft.Extensions.Logging.ILoggerFactory> interfaces and implementations are included in the .NET Core SDK.</span></span> <span data-ttu-id="de34a-337">Кроме того, они доступны в следующих пакетах NuGet:</span><span class="sxs-lookup"><span data-stu-id="de34a-337">They are also available in the following NuGet packages:</span></span>

- <span data-ttu-id="de34a-338">Эти интерфейсы находятся в пространстве имен [Microsoft.Extensions.Logging.Abstractions](https://www.nuget.org/packages/Microsoft.Extensions.Logging.Abstractions).</span><span class="sxs-lookup"><span data-stu-id="de34a-338">The interfaces are in [Microsoft.Extensions.Logging.Abstractions](https://www.nuget.org/packages/Microsoft.Extensions.Logging.Abstractions).</span></span>
- <span data-ttu-id="de34a-339">Их реализации по умолчанию находятся в пакете [Microsoft.Extensions.Logging](https://www.nuget.org/packages/microsoft.extensions.logging).</span><span class="sxs-lookup"><span data-stu-id="de34a-339">The default implementations are in [Microsoft.Extensions.Logging](https://www.nuget.org/packages/microsoft.extensions.logging).</span></span>

## <a name="apply-log-filter-rules-in-code"></a><span data-ttu-id="de34a-340">Применение правил фильтрации журналов в коде</span><span class="sxs-lookup"><span data-stu-id="de34a-340">Apply log filter rules in code</span></span>

<span data-ttu-id="de34a-341">Для настройки правил фильтрации журналов рекомендуется использовать [конфигурацию](configuration.md).</span><span class="sxs-lookup"><span data-stu-id="de34a-341">The preferred approach for setting log filter rules is by using [Configuration](configuration.md).</span></span>

<span data-ttu-id="de34a-342">В следующем примере показано, как зарегистрировать в коде правила фильтрации:</span><span class="sxs-lookup"><span data-stu-id="de34a-342">The following example shows how to register filter rules in code:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
               logging.AddFilter("System", LogLevel.Debug)
                  .AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)
                  .AddFilter<ConsoleLoggerProvider>("Microsoft", LogLevel.Trace));
}
```

<span data-ttu-id="de34a-343">`logging.AddFilter("System", LogLevel.Debug)` задает категорию `System` и уровень ведения журнала `Debug`.</span><span class="sxs-lookup"><span data-stu-id="de34a-343">`logging.AddFilter("System", LogLevel.Debug)` specifies the `System` category and log level `Debug`.</span></span> <span data-ttu-id="de34a-344">Поскольку конкретный поставщик не задан, фильтр применяется ко всем поставщикам.</span><span class="sxs-lookup"><span data-stu-id="de34a-344">The filter is applied to all providers because a specific provider was not configured.</span></span>

<span data-ttu-id="de34a-345">`AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)` задает:</span><span class="sxs-lookup"><span data-stu-id="de34a-345">`AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)` specifies:</span></span>

- <span data-ttu-id="de34a-346">поставщик ведения журнала `Debug`;</span><span class="sxs-lookup"><span data-stu-id="de34a-346">The `Debug` logging provider.</span></span>
- <span data-ttu-id="de34a-347">уровень ведения журнала `Information` и выше;</span><span class="sxs-lookup"><span data-stu-id="de34a-347">Log level `Information` and higher.</span></span>
- <span data-ttu-id="de34a-348">все категории, начинающиеся с `"Microsoft"`.</span><span class="sxs-lookup"><span data-stu-id="de34a-348">All categories starting with `"Microsoft"`.</span></span>

## <a name="see-also"></a><span data-ttu-id="de34a-349">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="de34a-349">See also</span></span>

- [<span data-ttu-id="de34a-350">Поставщики ведения журнала в NET</span><span class="sxs-lookup"><span data-stu-id="de34a-350">Logging providers in .NET</span></span>](logging-providers.md)
- [<span data-ttu-id="de34a-351">Реализация пользовательского поставщика ведения журнала в .NET</span><span class="sxs-lookup"><span data-stu-id="de34a-351">Implement a custom logging provider in .NET</span></span>](custom-logging-provider.md)
- [<span data-ttu-id="de34a-352">Форматирование журнала консоли</span><span class="sxs-lookup"><span data-stu-id="de34a-352">Console log formatting</span></span>](console-log-formatter.md)
- [<span data-ttu-id="de34a-353">Ведение журнала с высокой производительностью в .NET</span><span class="sxs-lookup"><span data-stu-id="de34a-353">High-performance logging in .NET</span></span>](high-performance-logging.md)
- <span data-ttu-id="de34a-354">Ошибки, связанные с ведением журнала, следует создавать в репозитории [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues).</span><span class="sxs-lookup"><span data-stu-id="de34a-354">Logging bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
