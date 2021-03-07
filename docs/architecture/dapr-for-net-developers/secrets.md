---
title: Стандартный блок секретов ДАПР
description: Описание стандартного блока секретов, его функций, преимуществ и способов применения
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: 94942b396af947b2a3e49b918b2b082c15f4bb08
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401852"
---
# <a name="the-dapr-secrets-building-block"></a><span data-ttu-id="0fec9-103">Стандартный блок секретов ДАПР</span><span class="sxs-lookup"><span data-stu-id="0fec9-103">The Dapr secrets building block</span></span>

<span data-ttu-id="0fec9-104">Для корпоративных приложений требуются секреты.</span><span class="sxs-lookup"><span data-stu-id="0fec9-104">Enterprise applications require secrets.</span></span> <span data-ttu-id="0fec9-105">Ниже приведены распространенные примеры.</span><span class="sxs-lookup"><span data-stu-id="0fec9-105">Common examples include:</span></span>

- <span data-ttu-id="0fec9-106">Строка подключения к базе данных, которая содержит имя пользователя и пароль.</span><span class="sxs-lookup"><span data-stu-id="0fec9-106">A database connection string that contains a username and password.</span></span>
- <span data-ttu-id="0fec9-107">Ключ API для вызова внешнего веб-API.</span><span class="sxs-lookup"><span data-stu-id="0fec9-107">An API key for calling an external web API.</span></span>
- <span data-ttu-id="0fec9-108">Сертификат клиента для проверки подлинности во внешней системе.</span><span class="sxs-lookup"><span data-stu-id="0fec9-108">A client certificate for authenticating to an external system.</span></span>

<span data-ttu-id="0fec9-109">Секреты должны тщательно управляться, чтобы они никогда не раскрываются вне приложения.</span><span class="sxs-lookup"><span data-stu-id="0fec9-109">Secrets must be carefully managed so that they're never disclosed outside of the application.</span></span>

<span data-ttu-id="0fec9-110">Не давно, мы популярны хранить секреты приложений в файле конфигурации внутри базы кода приложения.</span><span class="sxs-lookup"><span data-stu-id="0fec9-110">Not long ago, it was popular to store application secrets in a configuration file inside the application codebase.</span></span> <span data-ttu-id="0fec9-111">Разработчики .NET будут любовью файл *web.config* .</span><span class="sxs-lookup"><span data-stu-id="0fec9-111">.NET developers will fondly recall the *web.config* file.</span></span> <span data-ttu-id="0fec9-112">В то время как простота реализации, интеграция секретов в вместе с кодом была далеко из безопасности.</span><span class="sxs-lookup"><span data-stu-id="0fec9-112">While simple to implement, integrating secrets to along with code was far from secure.</span></span> <span data-ttu-id="0fec9-113">Распространенным вамом был включение файла при отправке в общедоступный репозиторий GIT с предоставлением секретов в мире.</span><span class="sxs-lookup"><span data-stu-id="0fec9-113">A common misstep was to include the file when pushing to a public GIT repository, exposing the secrets to the world.</span></span>

<span data-ttu-id="0fec9-114">Широко принятой методологией для создания современных распределенных приложений является [Twelve-Factorное приложение](https://12factor.net/).</span><span class="sxs-lookup"><span data-stu-id="0fec9-114">A widely accepted methodology for constructing modern distributed applications is [The Twelve-Factor App](https://12factor.net/).</span></span> <span data-ttu-id="0fec9-115">Он описывает набор принципов и рекомендации.</span><span class="sxs-lookup"><span data-stu-id="0fec9-115">It describes a set of principles and best practices.</span></span> <span data-ttu-id="0fec9-116">Третий фактор предписывает, что *Конфигурация и секреты должны быть внешними вне базы кода.*</span><span class="sxs-lookup"><span data-stu-id="0fec9-116">Its third factor prescribes that *configuration and secrets be externalized outside of the code base.*</span></span>

<span data-ttu-id="0fec9-117">Чтобы решить эту проблему, платформа .NET Core включает функцию [диспетчера секретов](/aspnet/core/security/app-secrets#secret-manager) , которая хранит конфиденциальные данные в физической папке за пределами дерева проекта.</span><span class="sxs-lookup"><span data-stu-id="0fec9-117">To address this concern, the .NET Core platform includes a [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) feature that stores sensitive data in a physical folder outside of the project tree.</span></span> <span data-ttu-id="0fec9-118">Хотя секреты находятся за пределами системы управления версиями, эта функция не шифрует данные.</span><span class="sxs-lookup"><span data-stu-id="0fec9-118">While secrets are outside of source control, this feature doesn't encrypt data.</span></span> <span data-ttu-id="0fec9-119">Он предназначен только для **целей разработки** .</span><span class="sxs-lookup"><span data-stu-id="0fec9-119">It's designed for **development purposes** only.</span></span>

<span data-ttu-id="0fec9-120">Более современная и безопасной практикой является изоляция секретов в средстве управления секретами, например **Hashicorp Vault** или **Azure Key Vault**.</span><span class="sxs-lookup"><span data-stu-id="0fec9-120">A more modern and secure practice is to isolate secrets in a secrets management tool like **Hashicorp Vault** or **Azure Key Vault**.</span></span>  <span data-ttu-id="0fec9-121">Эти средства позволяют хранить секреты извне, изменять учетные данные в разных средах и ссылаться на них из кода приложения.</span><span class="sxs-lookup"><span data-stu-id="0fec9-121">These tools enable you to store secrets externally, vary credentials across environments, and reference them from application code.</span></span> <span data-ttu-id="0fec9-122">Однако каждый инструмент имеет свои сложности и обученную кривую.</span><span class="sxs-lookup"><span data-stu-id="0fec9-122">However, each tool has its complexities and learning curve.</span></span>

<span data-ttu-id="0fec9-123">ДАПР предлагает стандартный блок, упрощающий управление секретами.</span><span class="sxs-lookup"><span data-stu-id="0fec9-123">Dapr offers a building block that simplifies managing secrets.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="0fec9-124">Решение</span><span class="sxs-lookup"><span data-stu-id="0fec9-124">What it solves</span></span>

<span data-ttu-id="0fec9-125">[Стандартный блок ДАПР секреты](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/) абстрагирует сложность работы с секретными и секретными средствами управления.</span><span class="sxs-lookup"><span data-stu-id="0fec9-125">The Dapr [secrets building block](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/) abstracts away the complexity of working with secrets and secret management tools.</span></span>

- <span data-ttu-id="0fec9-126">Он скрывает базовые коммуникации через единый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="0fec9-126">It hides the underlying plumbing through a unified interface.</span></span>
- <span data-ttu-id="0fec9-127">Он поддерживает различные *подключаемые* компоненты хранилища секретов, которые могут различаться в зависимости от разработки и рабочей среды.</span><span class="sxs-lookup"><span data-stu-id="0fec9-127">It supports various *pluggable* secret store components, which can vary between development and production.</span></span>
- <span data-ttu-id="0fec9-128">Приложениям не требуются прямые зависимости от библиотек хранилища секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-128">Applications don't require direct dependencies on secret store libraries.</span></span>
- <span data-ttu-id="0fec9-129">Разработчикам не требуются подробные сведения о каждом хранилище секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-129">Developers don't require detailed knowledge of each secret store.</span></span>

<span data-ttu-id="0fec9-130">ДАПР обрабатывает все перечисленные выше проблемы.</span><span class="sxs-lookup"><span data-stu-id="0fec9-130">Dapr handles all of the above concerns.</span></span>

<span data-ttu-id="0fec9-131">Доступ к секретам обеспечивается с помощью проверки подлинности и авторизации.</span><span class="sxs-lookup"><span data-stu-id="0fec9-131">Access to the secrets is secured through authentication and authorization.</span></span> <span data-ttu-id="0fec9-132">Доступ к секретам может получить только приложение с достаточными правами.</span><span class="sxs-lookup"><span data-stu-id="0fec9-132">Only an application with sufficient rights can access secrets.</span></span> <span data-ttu-id="0fec9-133">Приложения, работающие в Kubernetes, могут также использовать встроенный механизм управления секретами.</span><span class="sxs-lookup"><span data-stu-id="0fec9-133">Applications running in Kubernetes can also use its built-in secrets management mechanism.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="0fec9-134">Принцип работы</span><span class="sxs-lookup"><span data-stu-id="0fec9-134">How it works</span></span>

<span data-ttu-id="0fec9-135">Приложения используют стандартный блок секреты двумя способами:</span><span class="sxs-lookup"><span data-stu-id="0fec9-135">Applications use the secrets building block in two ways:</span></span>

- <span data-ttu-id="0fec9-136">Получение секрета непосредственно из блока приложения.</span><span class="sxs-lookup"><span data-stu-id="0fec9-136">Retrieve a secret directly from the application block.</span></span>
- <span data-ttu-id="0fec9-137">Косвенная ссылка на секрет из конфигурации компонента ДАПР.</span><span class="sxs-lookup"><span data-stu-id="0fec9-137">Reference a secret indirectly from a Dapr component configuration.</span></span>

<span data-ttu-id="0fec9-138">Извлечение секретов напрямую рассматривается в первую очередь.</span><span class="sxs-lookup"><span data-stu-id="0fec9-138">Retrieving secrets directly is covered first.</span></span> <span data-ttu-id="0fec9-139">Ссылка на секрет из файла конфигурации компонента ДАПР описана в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="0fec9-139">Referencing a secret from a Dapr component configuration file is addressed in a later section.</span></span>

<span data-ttu-id="0fec9-140">Приложение взаимодействует с ДАПР расширения при использовании стандартного блока секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-140">The application interacts with a Dapr sidecar when using the secrets building block.</span></span> <span data-ttu-id="0fec9-141">Расширения предоставляет API секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-141">The sidecar exposes the secrets API.</span></span> <span data-ttu-id="0fec9-142">API можно вызывать с помощью HTTP или gRPC.</span><span class="sxs-lookup"><span data-stu-id="0fec9-142">The API can be called with either HTTP or gRPC.</span></span> <span data-ttu-id="0fec9-143">Используйте следующий URL-адрес для вызова API HTTP:</span><span class="sxs-lookup"><span data-stu-id="0fec9-143">Use the following URL to call the HTTP API:</span></span>

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/<name>?<metadata>
```

<span data-ttu-id="0fec9-144">URL-адрес содержит следующие сегменты:</span><span class="sxs-lookup"><span data-stu-id="0fec9-144">The URL contains the following segments:</span></span>

- <span data-ttu-id="0fec9-145">`<dapr-port>` Указывает номер порта, на котором прослушивается расширения ДАПР.</span><span class="sxs-lookup"><span data-stu-id="0fec9-145">`<dapr-port>` specifies the port number upon which the Dapr sidecar is listening.</span></span>
- <span data-ttu-id="0fec9-146">`<store-name>` Указывает имя хранилища секретов ДАПР.</span><span class="sxs-lookup"><span data-stu-id="0fec9-146">`<store-name>` specifies the name of the Dapr secret store.</span></span>
- <span data-ttu-id="0fec9-147">`<name>` Указывает имя секрета для извлечения.</span><span class="sxs-lookup"><span data-stu-id="0fec9-147">`<name>` specifies  the name of the secret to retrieve.</span></span>
- <span data-ttu-id="0fec9-148">`<metadata>` предоставляет дополнительные сведения о секрете.</span><span class="sxs-lookup"><span data-stu-id="0fec9-148">`<metadata>` provides additional information for the secret.</span></span> <span data-ttu-id="0fec9-149">Этот сегмент является необязательным, и свойства метаданных различаются для хранилища секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-149">This segment is optional and metadata properties differ per secret store.</span></span> <span data-ttu-id="0fec9-150">Дополнительные сведения о свойствах метаданных см. в [справочнике по API секретов]([Secrets API reference | Dapr Docs](https://docs.dapr.io/reference/api/secrets_api/)).</span><span class="sxs-lookup"><span data-stu-id="0fec9-150">For more information on metadata properties, see the [secrets API reference]([Secrets API reference | Dapr Docs](https://docs.dapr.io/reference/api/secrets_api/)).</span></span>

 > [!NOTE]
 > <span data-ttu-id="0fec9-151">Приведенный выше URL-адрес представляет собственный вызов API ДАПР, доступный для любой платформы разработки, поддерживающей HTTP или gRPC.</span><span class="sxs-lookup"><span data-stu-id="0fec9-151">The above URL represents the native Dapr API call available to any development platform that supports HTTP or gRPC.</span></span> <span data-ttu-id="0fec9-152">Популярные платформы, такие как .NET, Java и Go, имеют собственные пользовательские API.</span><span class="sxs-lookup"><span data-stu-id="0fec9-152">Popular platforms like .NET, Java, and Go have their own custom APIs.</span></span>

<span data-ttu-id="0fec9-153">Ответ JSON содержит ключ и значение секрета.</span><span class="sxs-lookup"><span data-stu-id="0fec9-153">The JSON response contains the key and value of the secret.</span></span>

<span data-ttu-id="0fec9-154">На рис. 10-1 показано, как ДАПР обрабатывает запрос для API секретов:</span><span class="sxs-lookup"><span data-stu-id="0fec9-154">Figure 10-1 shows how Dapr handles a request for the secrets API:</span></span>

![Схема получения секрета с помощью API секретов ДАПР.](media/secrets/secrets-flow.png)

<span data-ttu-id="0fec9-156">**Рис. 10-1**.</span><span class="sxs-lookup"><span data-stu-id="0fec9-156">**Figure 10-1**.</span></span> <span data-ttu-id="0fec9-157">Получение секрета с помощью API секретов ДАПР.</span><span class="sxs-lookup"><span data-stu-id="0fec9-157">Retrieving a secret with the Dapr secrets API.</span></span>

1. <span data-ttu-id="0fec9-158">Служба вызывает ДАПР секреты API, а также имя хранилища секретов и секрет для получения.</span><span class="sxs-lookup"><span data-stu-id="0fec9-158">The service calls the Dapr secrets API, along with the name of the secret store, and secret to retrieve.</span></span>
1. <span data-ttu-id="0fec9-159">ДАПР расширения извлекает указанный секрет из хранилища секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-159">The Dapr sidecar retrieves the specified secret from the secret store.</span></span>
1. <span data-ttu-id="0fec9-160">ДАПР расширения возвращает секретную информацию обратно в службу.</span><span class="sxs-lookup"><span data-stu-id="0fec9-160">The Dapr sidecar returns the secret information back to the service.</span></span>

<span data-ttu-id="0fec9-161">В некоторых хранилищах секретов поддерживается хранение нескольких пар "ключ-значение" в одном секрете.</span><span class="sxs-lookup"><span data-stu-id="0fec9-161">Some secret stores support storing multiple key/value pairs in a single secret.</span></span> <span data-ttu-id="0fec9-162">В этих сценариях ответ будет содержать несколько пар "ключ-значение" в одном ответе JSON, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="0fec9-162">For those scenarios, the response would contain multiple key/value pairs in a single JSON response as in the following example:</span></span>

```http
GET http://localhost:3500/v1.0/secrets/secret-store/interestRates?metadata.version_id=3
```

```json
{
  "tier1-percentage": "2.5",
  "tier2-percentage": "3.8",
  "tier3-percentage": "5.1"
}
```

<span data-ttu-id="0fec9-163">API ДАПР Secrets также предоставляет операцию для получения всех секретов, к которым приложение имеет доступ.</span><span class="sxs-lookup"><span data-stu-id="0fec9-163">The Dapr secrets API also offers an operation to retrieve all the secrets the application has access to:</span></span>

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/bulk
```

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="0fec9-164">Использование пакета SDK для ДАПР .NET</span><span class="sxs-lookup"><span data-stu-id="0fec9-164">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="0fec9-165">Для разработчиков .NET пакет SDK для ДАПР .NET упрощает управление секретами ДАПР.</span><span class="sxs-lookup"><span data-stu-id="0fec9-165">For .NET developers, the Dapr .NET SDK streamlines Dapr secret management.</span></span> <span data-ttu-id="0fec9-166">Рассмотрим `DaprClient.GetSecretAsync` метод.</span><span class="sxs-lookup"><span data-stu-id="0fec9-166">Consider the `DaprClient.GetSecretAsync` method.</span></span> <span data-ttu-id="0fec9-167">Он позволяет получить секрет непосредственно из любого хранилища секретов ДАПР с минимальными усилиями.</span><span class="sxs-lookup"><span data-stu-id="0fec9-167">It enables you to retrieve a secret directly from any Dapr secret store with minimal effort.</span></span> <span data-ttu-id="0fec9-168">Ниже приведен пример выборки секрета строки подключения для базы данных SQL Server:</span><span class="sxs-lookup"><span data-stu-id="0fec9-168">Here's an example of fetching a connection string secret for a SQL Server database:</span></span>

```csharp
var metadata = new Dictionary<string, string> { ["version_id"] = "3" };
Dictionary<string, string> secrets = await daprClient.GetSecretAsync("secret-store", "eshopsecrets", metadata);
string connectionString = secrets["customerdb"];
```

<span data-ttu-id="0fec9-169">`GetSecretAsync`Ниже приведены аргументы для метода.</span><span class="sxs-lookup"><span data-stu-id="0fec9-169">Arguments for the `GetSecretAsync` method include:</span></span>

- <span data-ttu-id="0fec9-170">Имя компонента хранилища секретов ДАПР ("Secret-Store")</span><span class="sxs-lookup"><span data-stu-id="0fec9-170">The name of the Dapr secret store component ('secret-store')</span></span>
- <span data-ttu-id="0fec9-171">Секрет для извлечения ("ешопсекретс")</span><span class="sxs-lookup"><span data-stu-id="0fec9-171">The secret to retrieve ('eshopsecrets')</span></span>
- <span data-ttu-id="0fec9-172">Необязательные пары "ключ-значение" метаданных ("version_id = 3")</span><span class="sxs-lookup"><span data-stu-id="0fec9-172">Optional metadata key/value pairs ('version_id=3')</span></span>

<span data-ttu-id="0fec9-173">Метод реагирует на объект Dictionary в качестве секрета, который может содержать несколько пар "ключ-значение".</span><span class="sxs-lookup"><span data-stu-id="0fec9-173">The method responds with a dictionary object as a secret can contain multiple key/value pairs.</span></span> <span data-ttu-id="0fec9-174">В приведенном выше примере `customerdb` для возвращения строки подключения в коллекции упоминается секрет с именем.</span><span class="sxs-lookup"><span data-stu-id="0fec9-174">In the example above, the secret named `customerdb` is referenced from the collection to return a connection string.</span></span>

<span data-ttu-id="0fec9-175">В пакете SDK для ДАПР .NET также реализован поставщик конфигурации .NET.</span><span class="sxs-lookup"><span data-stu-id="0fec9-175">The Dapr .NET SDK also features a .NET configuration provider.</span></span> <span data-ttu-id="0fec9-176">Загружает указанные секреты в базовый [API конфигурации .NET Core](../../core/extensions/configuration.md).</span><span class="sxs-lookup"><span data-stu-id="0fec9-176">It loads specified secrets into the underlying [.NET Core configuration API](../../core/extensions/configuration.md).</span></span> <span data-ttu-id="0fec9-177">Затем работающее приложение может ссылаться на секреты из `IConfiguration` словаря, зарегистрированного в ASP.NET Core внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="0fec9-177">The running application can then reference secrets from the `IConfiguration` dictionary that is registered in ASP.NET Core dependency injection.</span></span>

<span data-ttu-id="0fec9-178">Поставщик конфигурации секретов доступен из пакета NuGet [Dapr.Extensions.Configфигурации](https://www.nuget.org/packages/Dapr.Extensions.Configuration) .</span><span class="sxs-lookup"><span data-stu-id="0fec9-178">The secrets configuration provider is available from the [Dapr.Extensions.Configuration](https://www.nuget.org/packages/Dapr.Extensions.Configuration) NuGet package.</span></span> <span data-ttu-id="0fec9-179">Поставщик можно зарегистрировать в `Program.cs` веб-API ASP.NET приложении:</span><span class="sxs-lookup"><span data-stu-id="0fec9-179">The provider can be registered in the `Program.cs` of an ASP.NET Web API application:</span></span>  

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureAppConfiguration(config =>
        {
            var daprClient = new DaprClientBuilder().Build();
            var secretDescriptors = new List<DaprSecretDescriptor>
            {
                new DaprSecretDescriptor("eshopsecrets")
            };
            config.AddDaprSecretStore("secret-store", secretDescriptors, daprClient);
        })
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

<span data-ttu-id="0fec9-180">Приведенный выше пример загружает `eshopsecrets` коллекцию секретов в систему конфигурации .NET при запуске.</span><span class="sxs-lookup"><span data-stu-id="0fec9-180">The above example loads the `eshopsecrets` secrets collection into the .NET configuration system at startup.</span></span> <span data-ttu-id="0fec9-181">Для регистрации поставщика требуется экземпляр `DaprClient` для вызова API секретов на ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="0fec9-181">Registering the provider requires an instance of `DaprClient` to invoke the secrets API on the Dapr sidecar.</span></span> <span data-ttu-id="0fec9-182">Другие аргументы включают имя хранилища секретов и `DaprSecretDescriptor` объект с именем секрета.</span><span class="sxs-lookup"><span data-stu-id="0fec9-182">The other arguments include the name of the secret store and a `DaprSecretDescriptor` object with the name of the secret.</span></span>

<span data-ttu-id="0fec9-183">После загрузки вы можете получить секреты непосредственно из кода приложения:</span><span class="sxs-lookup"><span data-stu-id="0fec9-183">Once loaded, you can retrieve secrets directly from application code:</span></span>

```csharp
public void GetCustomer(IConfiguration config)
{
    var connectionString = config["eshopsecrets"]["customerdb"];
}
```

## <a name="secret-store-components"></a><span data-ttu-id="0fec9-184">Компоненты хранилища секретов</span><span class="sxs-lookup"><span data-stu-id="0fec9-184">Secret store components</span></span>

<span data-ttu-id="0fec9-185">Стандартный блок секреты поддерживает несколько компонентов хранилища секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-185">The secrets building block supports several secret store components.</span></span> <span data-ttu-id="0fec9-186">На момент написания статьи доступны следующие хранилища секретов:</span><span class="sxs-lookup"><span data-stu-id="0fec9-186">At the time of writing, the following secret stores are available:</span></span>

- <span data-ttu-id="0fec9-187">Переменные среды</span><span class="sxs-lookup"><span data-stu-id="0fec9-187">Environment Variables</span></span>
- <span data-ttu-id="0fec9-188">Локальный файл</span><span class="sxs-lookup"><span data-stu-id="0fec9-188">Local file</span></span>
- <span data-ttu-id="0fec9-189">Секреты Kubernetes</span><span class="sxs-lookup"><span data-stu-id="0fec9-189">Kubernetes secrets</span></span>
- <span data-ttu-id="0fec9-190">Диспетчер секретов AWS</span><span class="sxs-lookup"><span data-stu-id="0fec9-190">AWS Secrets Manager</span></span>
- <span data-ttu-id="0fec9-191">Хранилище ключей Azure;</span><span class="sxs-lookup"><span data-stu-id="0fec9-191">Azure Key Vault</span></span>
- <span data-ttu-id="0fec9-192">Диспетчер секретов обеспечить</span><span class="sxs-lookup"><span data-stu-id="0fec9-192">GCP Secret Manager</span></span>
- <span data-ttu-id="0fec9-193">Хранилище HashiCorp</span><span class="sxs-lookup"><span data-stu-id="0fec9-193">HashiCorp Vault</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0fec9-194">Переменные среды и компоненты локальных файлов предназначены только для рабочих нагрузок разработки.</span><span class="sxs-lookup"><span data-stu-id="0fec9-194">The environment variables and local file components are designed for development workloads only.</span></span>

<span data-ttu-id="0fec9-195">В следующих разделах показано, как настроить хранилище секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-195">The following sections show how to configure a secret store.</span></span>

### <a name="configuration"></a><span data-ttu-id="0fec9-196">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="0fec9-196">Configuration</span></span>

<span data-ttu-id="0fec9-197">Вы настраиваете хранилище секретов с помощью файла конфигурации компонента ДАПР.</span><span class="sxs-lookup"><span data-stu-id="0fec9-197">You configure a secret store using a Dapr component configuration file.</span></span> <span data-ttu-id="0fec9-198">Ниже показана типичная структура файла.</span><span class="sxs-lookup"><span data-stu-id="0fec9-198">The typical structure of the file is shown below:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: [component name]
  namespace: [namespace]
spec:
  type: secretstores.[secret store type]
  version: [secret store version]
  metadata:
  - name: [property name]
    value: [property value]
```

<span data-ttu-id="0fec9-199">Для всех файлов конфигурации компонентов ДАПР требуется указать `name` вместе с необязательным `namespace` значением.</span><span class="sxs-lookup"><span data-stu-id="0fec9-199">All Dapr component configuration files require a `name` along with an optional `namespace` value.</span></span> <span data-ttu-id="0fec9-200">Кроме того, `type` поле в `spec` разделе указывает тип компонента хранилища секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-200">Additionally, the `type` field in the `spec` section specifies the type of secret store component.</span></span> <span data-ttu-id="0fec9-201">Свойства в `metadata` разделе различаются для каждого хранилища секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-201">The properties in the `metadata` section differ per secret store.</span></span>

### <a name="indirectly-consume-dapr-secrets"></a><span data-ttu-id="0fec9-202">Косвенно использовать секреты ДАПР</span><span class="sxs-lookup"><span data-stu-id="0fec9-202">Indirectly consume Dapr secrets</span></span>

<span data-ttu-id="0fec9-203">Как упоминалось ранее в этой главе, приложения могут также использовать секреты, ссылаясь на них в файлах конфигурации компонентов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-203">As mentioned earlier in this chapter, applications can also consume secrets by referencing them in component configuration files.</span></span> <span data-ttu-id="0fec9-204">Рассмотрим [компонент управления состоянием](state-management.md) , который использует кэш Redis для хранения состояния:</span><span class="sxs-lookup"><span data-stu-id="0fec9-204">Consider a [state management component](state-management.md) that uses Redis cache for storing state:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: e$h0p0nD@pr
```

<span data-ttu-id="0fec9-205">Приведенный выше файл конфигурации содержит пароль в формате **открытого текста** для подключения к серверу Redis.</span><span class="sxs-lookup"><span data-stu-id="0fec9-205">The above configuration file contains a **clear-text** password for connecting to the Redis server.</span></span> <span data-ttu-id="0fec9-206">**Жестко** зафиксированные пароли всегда являются неправильными идеями.</span><span class="sxs-lookup"><span data-stu-id="0fec9-206">**Hardcoded** passwords are always a bad idea.</span></span> <span data-ttu-id="0fec9-207">При принудительной отправке этого файла конфигурации в общедоступный репозиторий будет предоставляться пароль.</span><span class="sxs-lookup"><span data-stu-id="0fec9-207">Pushing this configuration file to a public repository would expose the password.</span></span> <span data-ttu-id="0fec9-208">Сохранение пароля в секретном хранилище значительно улучшит этот сценарий.</span><span class="sxs-lookup"><span data-stu-id="0fec9-208">Storing the password in a secret store would dramatically improve this scenario.</span></span>

<span data-ttu-id="0fec9-209">В следующих примерах это демонстрируется с помощью нескольких разных хранилищ секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-209">The following examples demonstrate this using several different secret stores.</span></span>

### <a name="local-file"></a><span data-ttu-id="0fec9-210">Локальный файл</span><span class="sxs-lookup"><span data-stu-id="0fec9-210">Local file</span></span>

<span data-ttu-id="0fec9-211">Компонент локального файла предназначен для сценариев разработки.</span><span class="sxs-lookup"><span data-stu-id="0fec9-211">The local file component is designed for development scenarios.</span></span> <span data-ttu-id="0fec9-212">Он сохраняет секреты в локальной файловой системе внутри JSON-файла.</span><span class="sxs-lookup"><span data-stu-id="0fec9-212">It stores secrets on the local filesystem inside a JSON file.</span></span> <span data-ttu-id="0fec9-213">Ниже приведен пример с именем `eshop-secrets.json` .</span><span class="sxs-lookup"><span data-stu-id="0fec9-213">Here's an example named `eshop-secrets.json`.</span></span> <span data-ttu-id="0fec9-214">Он содержит один секретный пароль для Redis:</span><span class="sxs-lookup"><span data-stu-id="0fec9-214">It contains a single secret - a password for Redis:</span></span>

```json
{
  "eShopRedisPassword": "e$h0p0nD@pr"
}
```

<span data-ttu-id="0fec9-215">Этот файл помещается в `components` папку, указанную при запуске приложения ДАПР.</span><span class="sxs-lookup"><span data-stu-id="0fec9-215">You place this file in a `components` folder that you specify when running the Dapr application.</span></span>

<span data-ttu-id="0fec9-216">Следующий файл конфигурации хранилища секретов использует JSON-файл в качестве хранилища секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-216">The following secret store configuration file consumes the JSON file as a secret store.</span></span> <span data-ttu-id="0fec9-217">Он также помещается в `components` папку:</span><span class="sxs-lookup"><span data-stu-id="0fec9-217">It's also placed in the `components` folder:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-local-secret-store
  namespace: eshop
spec:
  type: secretstores.local.file
  version: v1
  metadata:
  - name: secretsFile
    value: ./components/eshop-secrets.json
  - name: nestedSeparator
    value: ":"
```

<span data-ttu-id="0fec9-218">Тип компонента — `secretstore.local.file` .</span><span class="sxs-lookup"><span data-stu-id="0fec9-218">The component type is `secretstore.local.file`.</span></span> <span data-ttu-id="0fec9-219">`secretsFile`Элемент Metadata указывает путь к секретному файлу.</span><span class="sxs-lookup"><span data-stu-id="0fec9-219">The `secretsFile` metadata element specifies the path to the secrets file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0fec9-220">Путь к секретному файлу может быть абсолютным или относительным.</span><span class="sxs-lookup"><span data-stu-id="0fec9-220">The path to a secrets file can be a absolute or relative path.</span></span> <span data-ttu-id="0fec9-221">Относительный путь основан на папке, в которой запускается приложение.</span><span class="sxs-lookup"><span data-stu-id="0fec9-221">The relative path is based on the folder in which the application starts.</span></span> <span data-ttu-id="0fec9-222">В этом примере `components` Папка является вложенной папкой каталога, содержащего приложение .NET.</span><span class="sxs-lookup"><span data-stu-id="0fec9-222">In the example, the `components` folder is a sub-folder of the directory that contains the .NET application.</span></span>

<span data-ttu-id="0fec9-223">В папке приложения запустите приложение ДАПР, указав `components` путь в качестве аргумента командной строки:</span><span class="sxs-lookup"><span data-stu-id="0fec9-223">From the application folder, start the Dapr application specifying the `components` path as a command-line argument:</span></span>

```console
dapr run --app-id basket-api --components-path ./components dotnet run
```

> [!NOTE]
> <span data-ttu-id="0fec9-224">Приведенный выше пример применяется к запуску ДАПР в собственном режиме.</span><span class="sxs-lookup"><span data-stu-id="0fec9-224">This above example applies to running Dapr in self-hosted mode.</span></span> <span data-ttu-id="0fec9-225">Для размещения Kubernetes рекомендуется использовать подключения томов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-225">For Kubernetes hosting, consider using volume mounts.</span></span>

<span data-ttu-id="0fec9-226">`nestedSeparator`В файле конфигурации ДАПР указывает символ для *СПРЯМЛЕНИЯ* иерархии JSON.</span><span class="sxs-lookup"><span data-stu-id="0fec9-226">The `nestedSeparator` in a Dapr configuration file specifies a character to *flatten* a JSON hierarchy.</span></span> <span data-ttu-id="0fec9-227">Рассмотрим следующий фрагмент кода:</span><span class="sxs-lookup"><span data-stu-id="0fec9-227">Consider the following snippet:</span></span>

```json
{
    "redisPassword": "some password",
    "connectionStrings": {
        "customerdb": "some connection string",
        "productdb": "some connection string"
    }
}
```

<span data-ttu-id="0fec9-228">Используя двоеточие в качестве разделителя, можно получить `customerdb` строку соединения с помощью ключа `connectionStrings:customerdb` .</span><span class="sxs-lookup"><span data-stu-id="0fec9-228">Using a colon as a separator, you can retrieve the `customerdb` connection-string using the key `connectionStrings:customerdb`.</span></span>

> [!NOTE]
> <span data-ttu-id="0fec9-229">Двоеточие `:` является значением разделителя по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0fec9-229">The colon `:` is the default separator value.</span></span>

<span data-ttu-id="0fec9-230">В следующем примере файл конфигурации управления состоянием ссылается на локальный компонент хранилища секретов, чтобы получить пароль для подключения к серверу Redis:</span><span class="sxs-lookup"><span data-stu-id="0fec9-230">In the next example, a state management configuration file references the local secret store component to obtain the password for connecting to the Redis server:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    secretKeyRef:
      name: eShopRedisPassword
      key: eShopRedisPassword
auth:
  secretStore: eshop-local-secret-store
```

<span data-ttu-id="0fec9-231">`secretKeyRef`Элемент ссылается на секрет, содержащий пароль.</span><span class="sxs-lookup"><span data-stu-id="0fec9-231">The `secretKeyRef` element references the secret containing the password.</span></span> <span data-ttu-id="0fec9-232">Он заменяет более раннее значение *clear-Text* .</span><span class="sxs-lookup"><span data-stu-id="0fec9-232">It replaces the earlier *clear-text* value.</span></span> <span data-ttu-id="0fec9-233">Имя секрета и имя ключа, которые `eShopRedisPassword` ссылаются на секрет.</span><span class="sxs-lookup"><span data-stu-id="0fec9-233">The secret name and the key name, `eShopRedisPassword`, reference the secret.</span></span> <span data-ttu-id="0fec9-234">Имя компонента управления секретами `eshop-local-secret-store` находится в `auth` элементе Metadata.</span><span class="sxs-lookup"><span data-stu-id="0fec9-234">The name of the secret management component `eshop-local-secret-store` is found in the `auth` metadata element.</span></span>

<span data-ttu-id="0fec9-235">Может возникнуть вопрос, почему `eShopRedisPassword` он идентичен как для имени, так и для ключа в ссылке на секрет.</span><span class="sxs-lookup"><span data-stu-id="0fec9-235">You might wonder why `eShopRedisPassword` is identical for both the name and key in the secret reference.</span></span> <span data-ttu-id="0fec9-236">В хранилище секретов локального файла секреты не идентифицируются с отдельным именем.</span><span class="sxs-lookup"><span data-stu-id="0fec9-236">In the local file secret store, secrets aren't identified with a separate name.</span></span> <span data-ttu-id="0fec9-237">Сценарий будет отличаться в следующем примере с использованием секретов Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="0fec9-237">The scenario will be different in the next example using Kubernetes secrets.</span></span>

### <a name="kubernetes-secret"></a><span data-ttu-id="0fec9-238">Секрет Kubernetes</span><span class="sxs-lookup"><span data-stu-id="0fec9-238">Kubernetes secret</span></span>

<span data-ttu-id="0fec9-239">Во втором примере основное внимание уделяется ДАПР приложению, работающему в Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="0fec9-239">This second example focuses on a Dapr application running in Kubernetes.</span></span> <span data-ttu-id="0fec9-240">Он использует стандартный механизм секреты, Kubernetes предложения.</span><span class="sxs-lookup"><span data-stu-id="0fec9-240">It uses the standard secrets mechanism that Kubernetes offers.</span></span> <span data-ttu-id="0fec9-241">Используйте интерфейс командной строки Kubernetes ( `kubectl` ), чтобы создать секрет с именем `eshop-redis-secret` , который содержит пароль:</span><span class="sxs-lookup"><span data-stu-id="0fec9-241">Use the Kubernetes CLI (`kubectl`) to create a secret named `eshop-redis-secret` that contains the password:</span></span>

```console
kubectl create secret generic eshopsecrets --from-literal=redisPassword=e$h0p0nD@pr -n eshop
```

<span data-ttu-id="0fec9-242">После создания можно сослаться на секрет в файле конфигурации компонента для управления состоянием:</span><span class="sxs-lookup"><span data-stu-id="0fec9-242">Once created, you can reference the secret in the component configuration file for state management:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: eshopsecrets
      key: redisPassword
auth:
  secretStore: kubernetes
```

<span data-ttu-id="0fec9-243">`secretKeyRef`Элемент указывает имя секрета Kubernetes и ключ секрета, `eshopsecrets` и `redisPassword` соответственно.</span><span class="sxs-lookup"><span data-stu-id="0fec9-243">The `secretKeyRef` element specifies the name of the Kubernetes secret and the secret's key, `eshopsecrets`, and `redisPassword` respectively.</span></span> <span data-ttu-id="0fec9-244">`auth`Раздел Metadata указывает ДАПР использовать компонент управления секретами Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="0fec9-244">The `auth` metadata section instructs Dapr to use the Kubernetes secrets management component.</span></span>

> [!NOTE]
> <span data-ttu-id="0fec9-245">Проверка подлинности является значением по умолчанию при использовании секретов Kubernetes и может быть опущено.</span><span class="sxs-lookup"><span data-stu-id="0fec9-245">Auth is the default value when using Kubernetes secrets and can be omitted.</span></span>

<span data-ttu-id="0fec9-246">В рабочем параметре секреты обычно создаются как часть автоматизированного конвейера CI/CD.</span><span class="sxs-lookup"><span data-stu-id="0fec9-246">In a production setting, secrets are typically created as part of an automated CI/CD pipeline.</span></span> <span data-ttu-id="0fec9-247">Это гарантирует, что только пользователи с достаточными разрешениями смогут получить доступ к секретам и изменить их.</span><span class="sxs-lookup"><span data-stu-id="0fec9-247">Doing so ensures only people with sufficient permissions can access and change the secrets.</span></span> <span data-ttu-id="0fec9-248">Разработчики создают файлы конфигурации, не зная фактического значения секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-248">Developers create configuration files without knowing the actual value of the secrets.</span></span>

### <a name="azure-key-vault"></a><span data-ttu-id="0fec9-249">Хранилище ключей Azure;</span><span class="sxs-lookup"><span data-stu-id="0fec9-249">Azure Key Vault</span></span>

<span data-ttu-id="0fec9-250">Следующий пример предназначен для работы в реальном рабочем сценарии.</span><span class="sxs-lookup"><span data-stu-id="0fec9-250">The next example is geared toward a real-world production scenario.</span></span> <span data-ttu-id="0fec9-251">В нем используется **Azure Key Vault** в качестве хранилища секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-251">It uses **Azure Key Vault** as the secret store.</span></span> <span data-ttu-id="0fec9-252">Azure Key Vault — это управляемая служба Azure, которая позволяет безопасно хранить секреты в облаке.</span><span class="sxs-lookup"><span data-stu-id="0fec9-252">Azure Key Vault is a managed Azure service that enables secrets to be stored securely in the cloud.</span></span>

<span data-ttu-id="0fec9-253">Для работы этого примера необходимо выполнить следующие условия.</span><span class="sxs-lookup"><span data-stu-id="0fec9-253">For this example to work, the following prerequisites must be satisfied:</span></span>

- <span data-ttu-id="0fec9-254">Вы защитили административный доступ к подписке Azure.</span><span class="sxs-lookup"><span data-stu-id="0fec9-254">You've secured administrative access to an Azure subscription.</span></span>
- <span data-ttu-id="0fec9-255">Вы подготовили Azure Key Vault с именем `eshopkv` , содержащее секрет с именем `redisPassword` , который содержит пароль для подключения к серверу Redis.</span><span class="sxs-lookup"><span data-stu-id="0fec9-255">You've provisioned an Azure Key Vault named `eshopkv` that holds a secret named `redisPassword` that contains the password for connecting to the Redis server.</span></span>
- <span data-ttu-id="0fec9-256">Вы создали [субъект-службу](/azure/active-directory/develop/howto-create-service-principal-portal) в Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0fec9-256">You've created [service principal](/azure/active-directory/develop/howto-create-service-principal-portal) in Azure Active Directory.</span></span>
- <span data-ttu-id="0fec9-257">Вы установили сертификат X509 для этого субъекта-службы (содержащий открытый и закрытый ключи) в локальной файловой системе.</span><span class="sxs-lookup"><span data-stu-id="0fec9-257">You've installed an X509 certificate for this service principal (containing both the public and private key) on the local filesystem.</span></span>

> [!NOTE]
> <span data-ttu-id="0fec9-258">Субъект-служба — это удостоверение, которое может использоваться приложением для проверки подлинности службы Azure.</span><span class="sxs-lookup"><span data-stu-id="0fec9-258">A service principal is an identity that can be used by an application to authenticate an Azure service.</span></span> <span data-ttu-id="0fec9-259">Субъект-служба использует сертификат X509.</span><span class="sxs-lookup"><span data-stu-id="0fec9-259">The service principal uses a X509 certificate.</span></span> <span data-ttu-id="0fec9-260">Приложение использует этот сертификат в качестве учетных данных для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="0fec9-260">The application uses this certificate as a credential to authenticate itself.</span></span>

<span data-ttu-id="0fec9-261">В [документации по хранилищу секретов дапр Azure Key Vault](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault/) содержатся пошаговые инструкции по созданию и настройке среды Key Vault.</span><span class="sxs-lookup"><span data-stu-id="0fec9-261">The [Dapr Azure Key Vault secret store documentation](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault/) provides step-by-step instructions to create and configure a Key Vault environment.</span></span>

#### <a name="use-key-vault-when-running-in-self-hosted-mode"></a><span data-ttu-id="0fec9-262">Использование Key Vault при работе в автономном режиме</span><span class="sxs-lookup"><span data-stu-id="0fec9-262">Use Key Vault when running in self-hosted mode</span></span>

<span data-ttu-id="0fec9-263">Для использования Azure Key Vault в режиме автономного размещения ДАПР требуется следующий файл конфигурации:</span><span class="sxs-lookup"><span data-stu-id="0fec9-263">Consuming Azure Key Vault in Dapr self-hosted mode requires the following configuration file:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-azurekv-secret-store
  namespace: eshop
spec:
  type: secretstores.azure.keyvault
  version: v1
  metadata:
  - name: vaultName
    value: eshopkv
  - name: spnTenantId
    value: "619926af-a7c3-4e95-93ed-4ecc4e3e652b"
  - name: spnClientId
    value: "6cf48032-6c38-43be-9d6f-2a43ce736b09"
  - name: spnCertificateFile
    value : "azurekv-spn-cert.pfx"
```

<span data-ttu-id="0fec9-264">Тип хранилища секретов — `secretstores.azure.keyvault` .</span><span class="sxs-lookup"><span data-stu-id="0fec9-264">The secret store type is `secretstores.azure.keyvault`.</span></span> <span data-ttu-id="0fec9-265">`metadata`Элемент, для которого необходимо настроить доступ к Key Vault, требует следующих свойств:</span><span class="sxs-lookup"><span data-stu-id="0fec9-265">The `metadata` element to configure access to Key Vault requires the following properties:</span></span>

- <span data-ttu-id="0fec9-266">`vaultName`Содержит имя Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="0fec9-266">The `vaultName` contains the name of the Azure Key Vault.</span></span>
- <span data-ttu-id="0fec9-267">`spnTenantId`Содержит *идентификатор клиента* субъекта-службы, используемого для проверки подлинности в Key Vault.</span><span class="sxs-lookup"><span data-stu-id="0fec9-267">The `spnTenantId` contains the *tenant ID* of the service principal used to authenticate against the Key Vault.</span></span>
- <span data-ttu-id="0fec9-268">`spnClientId`Содержит *идентификатор приложения* субъекта-службы, используемого для проверки подлинности в Key Vault.</span><span class="sxs-lookup"><span data-stu-id="0fec9-268">The `spnClientId` contains the *app ID* of the service principal used to authenticate against the Key Vault.</span></span>
- <span data-ttu-id="0fec9-269">`spnCertificateFile`Содержит путь к файлу сертификата субъекта-службы для проверки подлинности в Key Vault.</span><span class="sxs-lookup"><span data-stu-id="0fec9-269">The `spnCertificateFile` contains the path to the certificate file for the service principal to authenticate against the Key Vault.</span></span>

> [!TIP]
> <span data-ttu-id="0fec9-270">Сведения о субъекте-службе можно скопировать из портал Azure или Azure CLI.</span><span class="sxs-lookup"><span data-stu-id="0fec9-270">You can copy the service principal information from the Azure portal or Azure CLI .</span></span>

<span data-ttu-id="0fec9-271">Теперь приложение может получить пароль Redis из Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="0fec9-271">Now the application can retrieve the Redis password from the Azure Key Vault.</span></span>

#### <a name="use-key-vault-when-running-on-kubernetes"></a><span data-ttu-id="0fec9-272">Использование Key Vault при выполнении в Kubernetes</span><span class="sxs-lookup"><span data-stu-id="0fec9-272">Use Key Vault when running on Kubernetes</span></span>

<span data-ttu-id="0fec9-273">Для использования Azure Key Vault с ДАПР и Kubernetes также требуется субъект-служба для проверки подлинности Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="0fec9-273">Consuming Azure Key Vault with Dapr and Kubernetes also requires a service principal to authenticate against the Azure Key Vault.</span></span>

<span data-ttu-id="0fec9-274">Сначала создайте *секрет Kubernetes* , который содержит файл сертификата, с помощью средства CLI kubectl:</span><span class="sxs-lookup"><span data-stu-id="0fec9-274">First, create a *Kubernetes secret* that contains a certificate file using the kubectl CLI tool:</span></span>

```console
kubectl create secret generic [k8s_spn_secret_name] --from-file=[pfx_certificate_file_local_path] -n eshop
```

<span data-ttu-id="0fec9-275">Команда требует два аргумента командной строки:</span><span class="sxs-lookup"><span data-stu-id="0fec9-275">The command requires two command-line arguments:</span></span>

- <span data-ttu-id="0fec9-276">`[k8s_spn_secret_name]` — Это имя секрета в хранилище секретов Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="0fec9-276">`[k8s_spn_secret_name]` is the secret name in Kubernetes secret store.</span></span>
- <span data-ttu-id="0fec9-277">`[pfx_certificate_file_local_path]` путь к файлу сертификата X509.</span><span class="sxs-lookup"><span data-stu-id="0fec9-277">`[pfx_certificate_file_local_path]` is the path of X509 certificate file.</span></span>

<span data-ttu-id="0fec9-278">После создания можно сослаться на секрет Kubernetes в файле конфигурации компонента хранилища секретов:</span><span class="sxs-lookup"><span data-stu-id="0fec9-278">Once created, you can reference the Kubernetes secret in the secret store component configuration file:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-azurekv-secret-store
  namespace: eshop
spec:
  type: secretstores.azure.keyvault
  version: v1
  metadata:
  - name: vaultName
    value: [your_keyvault_name]
  - name: spnTenantId
    value: "619926af-a7c3-4e95-93ed-4ecc4e3e652b"
  - name: spnClientId
    value: "6cf48032-6c38-43be-9d6f-2a43ce736b09"
  - name: spnCertificate
    secretKeyRef:
      name: [k8s_spn_secret_name]
      key: [pfx_certificate_file_local_name]
auth:
    secretStore: kubernetes
```

<span data-ttu-id="0fec9-279">На этом этапе приложение, работающее в Kubernetes, может получить пароль Redis из Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="0fec9-279">At this point, an application running in Kubernetes can retrieve the Redis password from the Azure Key Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0fec9-280">Очень важно, чтобы файл сертификата X509 для субъекта-службы оставался в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="0fec9-280">It's critical to keep the X509 certificate file for the service principal in a safe place.</span></span> <span data-ttu-id="0fec9-281">Его лучше разместить в хорошо известной папке за пределами репозитория исходного кода.</span><span class="sxs-lookup"><span data-stu-id="0fec9-281">It's best to place it in a well-known folder outside the source-code repository.</span></span> <span data-ttu-id="0fec9-282">Затем файл конфигурации может ссылаться на файл сертификата из этой хорошо известной папки.</span><span class="sxs-lookup"><span data-stu-id="0fec9-282">The configuration file can then reference the certificate file from this well-known folder.</span></span> <span data-ttu-id="0fec9-283">На локальном компьютере разработки вы несете ответственность за копирование сертификата в папку.</span><span class="sxs-lookup"><span data-stu-id="0fec9-283">On a local development machine, you're responsible for copying the certificate to the folder.</span></span> <span data-ttu-id="0fec9-284">Для автоматизированных развертываний конвейер скопирует сертификат на компьютер, на котором развернуто приложение.</span><span class="sxs-lookup"><span data-stu-id="0fec9-284">For automated deployments, the pipeline will copy the certificate to the machine where the application is deployed.</span></span> <span data-ttu-id="0fec9-285">Рекомендуется использовать другой субъект-службу для каждой среды.</span><span class="sxs-lookup"><span data-stu-id="0fec9-285">It's a best practice to use a different service principal per environment.</span></span> <span data-ttu-id="0fec9-286">Таким образом, субъект-служба из среды разработки не сможет получить доступ к секретам в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="0fec9-286">Doing so prevents the service principal from a DEVELOPMENT environment to access secrets in a PRODUCTION environment.</span></span>

<span data-ttu-id="0fec9-287">При работе в службе Azure Kubernetes Service (AKS) предпочтительнее использовать [управляемое удостоверение Azure](/azure/active-directory/managed-identities-azure-resources/overview) для проверки подлинности в Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="0fec9-287">When running in  Azure Kubernetes Service (AKS), it's preferable to use an [Azure Managed Identity](/azure/active-directory/managed-identities-azure-resources/overview) for authenticating against Azure Key Vault.</span></span> <span data-ttu-id="0fec9-288">Управляемые удостоверения выходят за рамки этой книги, но описаны в документации [Azure Key Vault с управляемыми удостоверениями](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault-managed-identity/) .</span><span class="sxs-lookup"><span data-stu-id="0fec9-288">Managed identities are outside of the scope of this book, but explained in the [Azure Key Vault with managed identities](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault-managed-identity/) documentation.</span></span>

### <a name="scope-secrets"></a><span data-ttu-id="0fec9-289">Секреты области</span><span class="sxs-lookup"><span data-stu-id="0fec9-289">Scope secrets</span></span>

<span data-ttu-id="0fec9-290">Области секрета позволяют контролировать, к каким секретам имеет доступ приложение.</span><span class="sxs-lookup"><span data-stu-id="0fec9-290">Secret scopes allow you to control which secrets your application can access.</span></span> <span data-ttu-id="0fec9-291">Вы настраиваете области в файле конфигурации ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="0fec9-291">You configure scopes in a Dapr sidecar configuration file.</span></span> <span data-ttu-id="0fec9-292">В [документации по конфигурации ДАПР](https://docs.dapr.io/operations/configuration/configuration-overview/) содержатся инструкции по области секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-292">The [Dapr configuration documentation](https://docs.dapr.io/operations/configuration/configuration-overview/) provides instructions for scoping secrets.</span></span>

<span data-ttu-id="0fec9-293">Ниже приведен пример файла конфигурации ДАПР расширения, который содержит области секрета:</span><span class="sxs-lookup"><span data-stu-id="0fec9-293">Here's an example of a Dapr sidecar configuration file that contains secret scopes:</span></span>

```yml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: dapr-config
  namespace: eshop
spec:
  tracing:
    samplingRate: "1"
  secrets:
    scopes:
      - storeName: eshop-azurekv-secret-store
        defaultAccess: allow
        deniedSecrets: ["redisPassword", "apiKey"]
```

<span data-ttu-id="0fec9-294">Вы указываете области для каждого хранилища секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-294">You specify scopes per secret store.</span></span> <span data-ttu-id="0fec9-295">В приведенном выше примере хранилище секретов имеет имя `eshop-azurekv-secret-store` .</span><span class="sxs-lookup"><span data-stu-id="0fec9-295">In the above example, the secret store is named `eshop-azurekv-secret-store`.</span></span> <span data-ttu-id="0fec9-296">Вы настраиваете доступ к секретам, используя следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="0fec9-296">You configure access to secrets using the following properties:</span></span>

| <span data-ttu-id="0fec9-297">Свойство.</span><span class="sxs-lookup"><span data-stu-id="0fec9-297">Property</span></span>         | <span data-ttu-id="0fec9-298">Значение</span><span class="sxs-lookup"><span data-stu-id="0fec9-298">Value</span></span>               | <span data-ttu-id="0fec9-299">Описание</span><span class="sxs-lookup"><span data-stu-id="0fec9-299">Description</span></span>                                                                                                                       |
|------------------|---------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| `defaultAccess`  | <span data-ttu-id="0fec9-300">`allow` или `deny`</span><span class="sxs-lookup"><span data-stu-id="0fec9-300">`allow` or `deny`</span></span>   | <span data-ttu-id="0fec9-301">Разрешает или запрещает доступ ко *всем* секретам в указанном хранилище секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-301">Allows or denies access to *all* secrets in the specified secret store.</span></span> <span data-ttu-id="0fec9-302">Это свойство является необязательным и имеет значение по умолчанию `allow` .</span><span class="sxs-lookup"><span data-stu-id="0fec9-302">This property is optional with a default value of `allow`.</span></span> |
| `allowedSecrets` | <span data-ttu-id="0fec9-303">Список секретных ключей</span><span class="sxs-lookup"><span data-stu-id="0fec9-303">List of secret keys</span></span> | <span data-ttu-id="0fec9-304">Секреты, указанные в массиве, будут доступны.</span><span class="sxs-lookup"><span data-stu-id="0fec9-304">Secrets specified in the array will be accessible.</span></span> <span data-ttu-id="0fec9-305">Это необязательное свойство.</span><span class="sxs-lookup"><span data-stu-id="0fec9-305">This property is optional.</span></span>                                                     |
| `deniedSecrets`  | <span data-ttu-id="0fec9-306">Список секретных ключей</span><span class="sxs-lookup"><span data-stu-id="0fec9-306">List of secret keys</span></span> | <span data-ttu-id="0fec9-307">Секретные данные, указанные в массиве, будут недоступны.</span><span class="sxs-lookup"><span data-stu-id="0fec9-307">Secrets specified in the array will NOT be accessible.</span></span> <span data-ttu-id="0fec9-308">Это необязательное свойство.</span><span class="sxs-lookup"><span data-stu-id="0fec9-308">This property is optional.</span></span>                                                 |

<span data-ttu-id="0fec9-309">`allowedSecrets`Свойства и `deniedSecrets` имеют приоритет над `defaultAccess` свойством.</span><span class="sxs-lookup"><span data-stu-id="0fec9-309">The `allowedSecrets` and `deniedSecrets` properties take precedence over the `defaultAccess` property.</span></span> <span data-ttu-id="0fec9-310">Представьте `defaultAccess: allowed` , как указать и `allowedSecrets` список.</span><span class="sxs-lookup"><span data-stu-id="0fec9-310">Imagine specifying `defaultAccess: allowed` and an `allowedSecrets` list.</span></span> <span data-ttu-id="0fec9-311">В этом случае приложение будет доступно только для секретов в `allowedSecrets` списке.</span><span class="sxs-lookup"><span data-stu-id="0fec9-311">In this case, only the secrets in the `allowedSecrets` list would be accessible by the application.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="0fec9-312">Эталонное приложение: Ешопондапр</span><span class="sxs-lookup"><span data-stu-id="0fec9-312">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="0fec9-313">В эталонном приложении Ешопондапр используется стандартный блок секреты для двух секретов:</span><span class="sxs-lookup"><span data-stu-id="0fec9-313">The eShopOnDapr reference application uses the secrets building block for two secrets:</span></span>

- <span data-ttu-id="0fec9-314">Пароль для подключения к кэшу Redis.</span><span class="sxs-lookup"><span data-stu-id="0fec9-314">The password for connecting to the Redis cache.</span></span>
- <span data-ttu-id="0fec9-315">Ключ API для использования API Twilio Sendgrid.</span><span class="sxs-lookup"><span data-stu-id="0fec9-315">The API-key for using the Twilio Sendgrid API.</span></span> <span data-ttu-id="0fec9-316">Приложение использует Твиллио для отправки сообщений электронной почты с помощью выходной привязки ДАПР (как описано в [главе стандартные блоки привязки](bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="0fec9-316">The application uses Twillio to send emails using a Dapr output binding (as described in the [bindings building block chapter](bindings.md)).</span></span>

<span data-ttu-id="0fec9-317">При запуске приложения с помощью Docker Compose используется хранилище секретов **локального файла** .</span><span class="sxs-lookup"><span data-stu-id="0fec9-317">When running the application using Docker Compose, the **local file** secret store is used.</span></span> <span data-ttu-id="0fec9-318">Файл конфигурации компонента находится `eshop-secretstore.yaml` в `dapr/components` папке репозитория ешопондапр:</span><span class="sxs-lookup"><span data-stu-id="0fec9-318">The component configuration file `eshop-secretstore.yaml` is found in the `dapr/components` folder of the eShopOnDapr repository:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-secretstore
  namespace: eshop
spec:
  type: secretstores.local.file
  version: v1
  metadata:
  - name: secretsFile
    value: ./components/eshop-secretstore.json
```

<span data-ttu-id="0fec9-319">Файл конфигурации ссылается на локальный файл хранилища `eshop-secretstore.json` , расположенный в той же папке:</span><span class="sxs-lookup"><span data-stu-id="0fec9-319">The configuration file references the local store file `eshop-secretstore.json` located in the same folder:</span></span>

```json
{
    "redisPassword": "**********",
    "sendgridAPIKey": "**********"
}
```

<span data-ttu-id="0fec9-320">`components`Папка указывается в командной строке и монтируется в качестве локальной папки в контейнере ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="0fec9-320">The `components` folder is specified in the command-line and mounted as a local folder inside the Dapr sidecar container.</span></span> <span data-ttu-id="0fec9-321">Ниже приведен фрагмент `docker-compose.override.yml` файла в корне репозитория, указывающий подключение тома.</span><span class="sxs-lookup"><span data-stu-id="0fec9-321">Here's a snippet from the `docker-compose.override.yml` file in the repository root that specifies the volume mount:</span></span>

```yaml
  ordering-backgroundtasks-dapr:
    command: ["./daprd",
      "-app-id", "ordering-backgroundtasks",
      "-app-port", "80",
      "-dapr-grpc-port", "50004",
      "-components-path", "/components",
      "-config", "/configuration/eshop-config.yaml"
      ]
    volumes:
      - "./dapr/components/:/components"
      - "./dapr/configuration/:/configuration"
```

> [!NOTE]
> <span data-ttu-id="0fec9-322">Файл переопределения Docker Compose содержит значения конфигурации, зависящие от среды.</span><span class="sxs-lookup"><span data-stu-id="0fec9-322">The Docker Compose override file contains environmental specific configuration values.</span></span>

<span data-ttu-id="0fec9-323">Параметр `/components` подключения тома и `--components-path` командной строки передается в `daprd` команду Startup.</span><span class="sxs-lookup"><span data-stu-id="0fec9-323">The `/components` volume mount and `--components-path` command-line argument are passed into the `daprd` startup command.</span></span>

<span data-ttu-id="0fec9-324">После настройки другие файлы конфигурации компонентов также могут ссылаться на секреты.</span><span class="sxs-lookup"><span data-stu-id="0fec9-324">Once configured, other component configuration files can also reference the secrets.</span></span> <span data-ttu-id="0fec9-325">Ниже приведен пример конфигурации компонента публикации или подписки, которая использует секреты:</span><span class="sxs-lookup"><span data-stu-id="0fec9-325">Here's an example of the Publish/Subscribe component configuration consuming secrets:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub
  namespace: eshop
spec:
  type: pubsub.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: redisPassword
auth:
  secretStore: eshop-secretstore
```

<span data-ttu-id="0fec9-326">В предыдущем примере для ссылки на секреты используется локальное хранилище Redis.</span><span class="sxs-lookup"><span data-stu-id="0fec9-326">In the preceding example, the local Redis store is used to reference secrets.</span></span>

## <a name="summary"></a><span data-ttu-id="0fec9-327">Итоги</span><span class="sxs-lookup"><span data-stu-id="0fec9-327">Summary</span></span>

<span data-ttu-id="0fec9-328">Стандартный блок ДАПР Secrets предоставляет возможности хранения и извлечения конфиденциальных параметров конфигурации, таких как пароли и строки подключения.</span><span class="sxs-lookup"><span data-stu-id="0fec9-328">The Dapr secrets building block provides capabilities for storing and retrieving sensitive configuration settings like passwords and connection-strings.</span></span> <span data-ttu-id="0fec9-329">Он сохраняет секретные данные в частном порядке и предотвращает их случайное раскрываемое.</span><span class="sxs-lookup"><span data-stu-id="0fec9-329">It keeps secrets private and prevents them from being accidentally disclosed.</span></span>

<span data-ttu-id="0fec9-330">Стандартный блок поддерживает несколько разных хранилищ секретов и скрывает их сложность с помощью API секретов ДАПР.</span><span class="sxs-lookup"><span data-stu-id="0fec9-330">The building block supports several different secret stores and hides their complexity with the Dapr secrets API.</span></span>

<span data-ttu-id="0fec9-331">Пакет SDK для ДАПР .NET предоставляет `DaprClient` объект для получения секретов.</span><span class="sxs-lookup"><span data-stu-id="0fec9-331">The Dapr .NET SDK provides a `DaprClient` object to retrieve secrets.</span></span> <span data-ttu-id="0fec9-332">Он также включает поставщик конфигурации .NET, который добавляет секреты в систему конфигурации .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fec9-332">It also includes a .NET configuration provider that adds secrets to the .NET Core configuration system.</span></span> <span data-ttu-id="0fec9-333">После загрузки вы можете использовать эти секреты в коде .NET.</span><span class="sxs-lookup"><span data-stu-id="0fec9-333">Once loaded, you can consume these secrets in your .NET code.</span></span>

<span data-ttu-id="0fec9-334">Вы можете использовать области секрета для управления доступом к конкретным секретам.</span><span class="sxs-lookup"><span data-stu-id="0fec9-334">You can use secret scopes to control access to specific secrets.</span></span>

## <a name="references"></a><span data-ttu-id="0fec9-335">Ссылки</span><span class="sxs-lookup"><span data-stu-id="0fec9-335">References</span></span>

- [<span data-ttu-id="0fec9-336">За пределами приложения Twelve-Factor</span><span class="sxs-lookup"><span data-stu-id="0fec9-336">Beyond the Twelve-Factor Application</span></span>](https://tanzu.vmware.com/content/blog/beyond-the-twelve-factor-app)

>[!div class="step-by-step"]
><span data-ttu-id="0fec9-337">[Назад](observability.md)
>[Вперед](summary.md)</span><span class="sxs-lookup"><span data-stu-id="0fec9-337">[Previous](observability.md)
[Next](summary.md)</span></span>
