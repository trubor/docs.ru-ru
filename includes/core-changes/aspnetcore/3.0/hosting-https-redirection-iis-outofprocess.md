---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032750"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a><span data-ttu-id="a1a9a-101">Размещение. Для приложений IIS вне процесса включено перенаправление HTTPS</span><span class="sxs-lookup"><span data-stu-id="a1a9a-101">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>

<span data-ttu-id="a1a9a-102">В [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) версии 13.0.19218.0 для размещения с помощью IIS вне процесса можно реализовать существующую функцию перенаправления HTTPS для приложений ASP.NET Core 3.0 и 2.2.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-102">Version 13.0.19218.0 of the [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) for hosting via IIS out-of-process enables an existing HTTPS redirection feature for ASP.NET Core 3.0 and 2.2 apps.</span></span>

<span data-ttu-id="a1a9a-103">Обсуждение этого вопроса см. на странице [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span><span class="sxs-lookup"><span data-stu-id="a1a9a-103">For discussion, see [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a1a9a-104">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="a1a9a-104">Version introduced</span></span>

<span data-ttu-id="a1a9a-105">3.0</span><span class="sxs-lookup"><span data-stu-id="a1a9a-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a1a9a-106">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="a1a9a-106">Old behavior</span></span>

<span data-ttu-id="a1a9a-107">В шаблоне проекта ASP.NET Core 2.1 впервые представлена поддержка методов HTTPS промежуточного слоя, таких как <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> и <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-107">The ASP.NET Core 2.1 project template first introduced support for HTTPS middleware methods like <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> and <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span></span> <span data-ttu-id="a1a9a-108">Для включения перенаправления HTTPS требовалось добавить конфигурацию, поскольку приложения, находящиеся в разработке, не используют порт по умолчанию 443.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-108">Enabling HTTPS redirection required the addition of configuration, since apps in development don't use the default port of 443.</span></span> <span data-ttu-id="a1a9a-109">[Протокол HSTS](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) активен только в том случае, если запрос уже использует протокол HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) is active only if the request is already using HTTPS.</span></span> <span data-ttu-id="a1a9a-110">По умолчанию localhost пропускается.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-110">Localhost is skipped by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a1a9a-111">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="a1a9a-111">New behavior</span></span>

<span data-ttu-id="a1a9a-112">В ASP.NET Core 3.0 [усовершенствован](https://github.com/dotnet/AspNetCore/pull/4685) сценарий IIS HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-112">In ASP.NET Core 3.0, the IIS HTTPS scenario was [enhanced](https://github.com/dotnet/AspNetCore/pull/4685).</span></span> <span data-ttu-id="a1a9a-113">Благодаря этому усовершенствованию приложение может обнаруживать порты HTTPS сервера и сделать так, что `UseHttpsRedirection` будет работать по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-113">With the enhancement, an app could discover the server's HTTPS ports and make `UseHttpsRedirection` work by default.</span></span> <span data-ttu-id="a1a9a-114">Внутрипроцессный компонент выполнял обнаружение порта с помощью функции `IServerAddresses`, которая влияет только на приложения ASP.NET Core 3.0, поскольку внутрипроцессная библиотека имеет версию платформы.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-114">The in-process component accomplished port discovery with the `IServerAddresses` feature, which only affects ASP.NET Core 3.0 apps because the in-process library is versioned with the framework.</span></span> <span data-ttu-id="a1a9a-115">Внепроцессный компонент был изменен — теперь он автоматически добавляет переменную среды `ASPNETCORE_HTTPS_PORT`.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-115">The out-of-process component changed to automatically add the `ASPNETCORE_HTTPS_PORT` environment variable.</span></span> <span data-ttu-id="a1a9a-116">Это изменение повлияло на приложения ASP.NET Core 2.2 и 3.0, поскольку внепроцессный компонент используется совместно глобально.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-116">This change affected both ASP.NET Core 2.2 and 3.0 apps because the out-of-process component is shared globally.</span></span> <span data-ttu-id="a1a9a-117">Данное изменение не затрагивает приложения ASP.NET Core 2.1, так как они по умолчанию используют более раннюю версию ANCM.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-117">ASP.NET Core 2.1 apps aren't affected because they use a prior version of ANCM by default.</span></span>

<span data-ttu-id="a1a9a-118">Предыдущее поведение было изменено в ASP.NET Core 3.0.1 и 3.1.0 Preview 3 с целью отмены изменений в работе ASP.NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-118">The preceding behavior was modified in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 to reverse the behavior changes in ASP.NET Core 2.x.</span></span> <span data-ttu-id="a1a9a-119">Эти изменения влияют только на приложения, находящиеся вне процесса IIS.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-119">These changes only affect IIS out-of-process apps.</span></span>

<span data-ttu-id="a1a9a-120">Как описано выше, установка ASP.NET Core 3.0.0 имела побочный результат — активацию `UseHttpsRedirection` промежуточного слоя в приложениях ASP.NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-120">As detailed above, installing ASP.NET Core 3.0.0 had the side effect of also activating the `UseHttpsRedirection` middleware in ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="a1a9a-121">В ANCM в ASP.NET Core 3.0.1 и 3.1.0 Preview 3 было внесено соответствующее изменение, поэтому их установка больше не влияет на работу приложений ASP.NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-121">A change was made to ANCM in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 such that installing them no longer has this effect on ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="a1a9a-122">Переменная среды `ASPNETCORE_HTTPS_PORT`, которая заполнялась ANCM в ASP.NET Core 3.0.0, была изменена на `ASPNETCORE_ANCM_HTTPS_PORT` в ASP.NET Core 3.0.1 и 3.1.0 Preview 3.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-122">The `ASPNETCORE_HTTPS_PORT` environment variable that ANCM populated in ASP.NET Core 3.0.0 was changed to `ASPNETCORE_ANCM_HTTPS_PORT` in ASP.NET Core 3.0.1 and 3.1.0 Preview 3.</span></span> <span data-ttu-id="a1a9a-123">В этих выпусках также был обновлен компонент `UseHttpsRedirection` для понимания новых и старых переменных.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-123">`UseHttpsRedirection` was also updated in these releases to understand both the new and old variables.</span></span> <span data-ttu-id="a1a9a-124">Обновление для ASP.NET Core 2.x не предусмотрено.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-124">ASP.NET Core 2.x won't be updated.</span></span> <span data-ttu-id="a1a9a-125">В результате возвращается предыдущему поведению (отключено по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="a1a9a-125">As a result, it reverts to the previous behavior of being disabled by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a1a9a-126">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="a1a9a-126">Reason for change</span></span>

<span data-ttu-id="a1a9a-127">Улучшена функциональность ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-127">Improved ASP.NET Core 3.0 functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a1a9a-128">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="a1a9a-128">Recommended action</span></span>

<span data-ttu-id="a1a9a-129">Если все клиенты должны использовать протокол HTTPS, никаких действий не требуется.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-129">No action is required if you want all clients to use HTTPS.</span></span> <span data-ttu-id="a1a9a-130">Чтобы разрешить некоторым клиентам использовать протокол HTTP, выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-130">To allow some clients to use HTTP, take one of the following steps:</span></span>

* <span data-ttu-id="a1a9a-131">Удалите вызовы `UseHttpsRedirection` и `UseHsts` из метода `Startup.Configure` проекта и разверните приложение повторно.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-131">Remove the calls to `UseHttpsRedirection` and `UseHsts` from your project's `Startup.Configure` method, and redeploy the app.</span></span>
* <span data-ttu-id="a1a9a-132">В файле *web.config* задайте для переменной среды `ASPNETCORE_HTTPS_PORT` пустую строку.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-132">In your *web.config* file, set the `ASPNETCORE_HTTPS_PORT` environment variable to an empty string.</span></span> <span data-ttu-id="a1a9a-133">Это изменение можно выполнить непосредственно на сервере без повторного развертывания приложения.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-133">This change can occur directly on the server without redeploying the app.</span></span> <span data-ttu-id="a1a9a-134">Пример:</span><span class="sxs-lookup"><span data-stu-id="a1a9a-134">For example:</span></span>

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

<span data-ttu-id="a1a9a-135">`UseHttpsRedirection` по-прежнему можно:</span><span class="sxs-lookup"><span data-stu-id="a1a9a-135">`UseHttpsRedirection` can still be:</span></span>

* <span data-ttu-id="a1a9a-136">Активировать вручную в ASP.NET Core 2.x, задав для переменной среды `ASPNETCORE_HTTPS_PORT` соответствующий номер порта (в большинстве рабочих сценариев это порт 443).</span><span class="sxs-lookup"><span data-stu-id="a1a9a-136">Activated manually in ASP.NET Core 2.x by setting the `ASPNETCORE_HTTPS_PORT` environment variable to the appropriate port number (443 in most production scenarios).</span></span>
* <span data-ttu-id="a1a9a-137">Отключить в ASP.NET Core 3.x, задав `ASPNETCORE_ANCM_HTTPS_PORT` с пустым строковым значением.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-137">Deactivated in ASP.NET Core 3.x by defining `ASPNETCORE_ANCM_HTTPS_PORT` with an empty string value.</span></span> <span data-ttu-id="a1a9a-138">Это значение задается таким же образом, как и в предыдущем примере `ASPNETCORE_HTTPS_PORT`.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-138">This value is set in the same fashion as the preceding `ASPNETCORE_HTTPS_PORT` example.</span></span>

<span data-ttu-id="a1a9a-139">На компьютеры, на которых выполняются приложения ASP.NET Core 3.0.0, следует установить среду выполнения ASP.NET Core 3.0.1, прежде чем устанавливать ASP.NET Core 3.1.0 Preview 3 ANCM.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-139">Machines running ASP.NET Core 3.0.0 apps should install the ASP.NET Core 3.0.1 runtime before installing the ASP.NET Core 3.1.0 Preview 3 ANCM.</span></span> <span data-ttu-id="a1a9a-140">Это гарантирует, что `UseHttpsRedirection` будет работать правильно для приложений ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-140">Doing so ensures that `UseHttpsRedirection` continues to operate as expected for the ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="a1a9a-141">Ввиду того, что компонент ANCM является глобальным, в службе приложений Azure он развертывает по отдельному расписанию, отличному от расписания для среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-141">In Azure App Service, ANCM deploys on a separate schedule from the runtime because of its global nature.</span></span> <span data-ttu-id="a1a9a-142">ANCM был развернут в Azure с этими изменениями после развертывания ASP.NET Core 3.0.1 и 3.1.0.</span><span class="sxs-lookup"><span data-stu-id="a1a9a-142">ANCM was deployed to Azure with these changes after ASP.NET Core 3.0.1 and 3.1.0 were deployed.</span></span>

#### <a name="category"></a><span data-ttu-id="a1a9a-143">Категория</span><span class="sxs-lookup"><span data-stu-id="a1a9a-143">Category</span></span>

<span data-ttu-id="a1a9a-144">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a1a9a-144">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a1a9a-145">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a1a9a-145">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
