---
ms.openlocfilehash: b75f9ce8e878c935dcc5fd9dc292369720b895e9
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105152728"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="da71c-101">HTTP. Изменения SameSite в браузере влияют на проверку подлинности</span><span class="sxs-lookup"><span data-stu-id="da71c-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="da71c-102">Для некоторых браузеров, таких как Chrome и Firefox, были внесены критические изменения в реализации `SameSite` для файлов cookie.</span><span class="sxs-lookup"><span data-stu-id="da71c-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="da71c-103">Эти изменения негативно влияют на сценарии удаленной проверки подлинности, такие как OpenID Connect и WS-Federation, от которых нужно явно отказаться, отправив `SameSite=None`.</span><span class="sxs-lookup"><span data-stu-id="da71c-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="da71c-104">Однако `SameSite=None` нарушает работу других браузеров в iOS 12 и некоторых более старых версий.</span><span class="sxs-lookup"><span data-stu-id="da71c-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="da71c-105">Приложению требуется определить эти версии и опустить `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="da71c-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="da71c-106">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="da71c-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="da71c-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="da71c-107">Version introduced</span></span>

<span data-ttu-id="da71c-108">3.1 (предварительная версия 1)</span><span class="sxs-lookup"><span data-stu-id="da71c-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="da71c-109">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="da71c-109">Old behavior</span></span>

<span data-ttu-id="da71c-110">`SameSite` является расширением проекта стандарта за 2016 год для файлов cookie в HTTP.</span><span class="sxs-lookup"><span data-stu-id="da71c-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="da71c-111">Этот атрибут предназначен для устранения подделки межсайтовых запросов (CSRF).</span><span class="sxs-lookup"><span data-stu-id="da71c-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="da71c-112">Изначально этот атрибут был спроектирован в виде функции, с которой серверы должны были явно соглашаться, добавляя новые параметры.</span><span class="sxs-lookup"><span data-stu-id="da71c-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="da71c-113">В ASP.NET Core 2.0 была добавлена начальная поддержка для `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="da71c-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="da71c-114">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="da71c-114">New behavior</span></span>

<span data-ttu-id="da71c-115">Компания Google предложила новый проект стандарта, не имеющий обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="da71c-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="da71c-116">Этот стандарт изменяет режим по умолчанию на `Lax` и добавляет новую запись `None` для явного отказа. `Lax` подходит для файлов cookie большинства приложений, однако нарушает работу межсайтовых сценариев, таких как вход с использованием WS-Federation и OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="da71c-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="da71c-117">Основную часть процедур входа OAuth это не затрагивает из-за различий в последовательностях обработки запросов.</span><span class="sxs-lookup"><span data-stu-id="da71c-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="da71c-118">Новый параметр `None` вызывает проблемы совместимости для клиентов, в которых реализован предыдущий проект стандарта (например, iOS 12).</span><span class="sxs-lookup"><span data-stu-id="da71c-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="da71c-119">Эти изменения будут включены в Chrome 80.</span><span class="sxs-lookup"><span data-stu-id="da71c-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="da71c-120">Сведения о сроках выпуска продукта Chrome см. в [новостях по SameSite](https://www.chromium.org/updates/same-site).</span><span class="sxs-lookup"><span data-stu-id="da71c-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="da71c-121">Продукт ASP.NET Core 3.1 был обновлен, чтобы реализовать новое поведение `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="da71c-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="da71c-122">Это обновление переопределяет поведение `SameSiteMode.None` для выдачи `SameSite=None` и добавляет новое значение `SameSiteMode.Unspecified`, чтобы опустить атрибут `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="da71c-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="da71c-123">Все API файлов cookie теперь по умолчанию используют `Unspecified`, хотя некоторые компоненты, использующие файлы cookie, задают более конкретные значения для соответствующих сценариев, таких как корреляция OpenID Connect и файлы cookie nonce.</span><span class="sxs-lookup"><span data-stu-id="da71c-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="da71c-124">Сведения о последних переменах в этой области см. в разделе [HTTP. Некоторые значения по умолчанию параметра SameSite для файлов cookie изменены на None](../../../../docs/core/compatibility/3.0.md#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="da71c-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](../../../../docs/core/compatibility/3.0.md#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="da71c-125">В ASP.NET Core 3.0 большинство значений по умолчанию изменились с <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> на <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (однако по-прежнему используется более ранний стандарт).</span><span class="sxs-lookup"><span data-stu-id="da71c-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="da71c-126">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="da71c-126">Reason for change</span></span>

<span data-ttu-id="da71c-127">Изменения в браузере и спецификации, описанные выше.</span><span class="sxs-lookup"><span data-stu-id="da71c-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="da71c-128">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="da71c-128">Recommended action</span></span>

<span data-ttu-id="da71c-129">Приложения, взаимодействующие с удаленными сайтами, например через стороннюю процедуру входа, должны:</span><span class="sxs-lookup"><span data-stu-id="da71c-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="da71c-130">тестировать эти сценарии в нескольких браузерах;</span><span class="sxs-lookup"><span data-stu-id="da71c-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="da71c-131">применить исправление определения браузеров в рамках политики файлов cookie, описанное в разделе [Поддержка более старых браузеров](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="da71c-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="da71c-132">Инструкции по тестированию и определению браузеров см. в следующем разделе:</span><span class="sxs-lookup"><span data-stu-id="da71c-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="da71c-133">Определение того, затрагивают ли вас эти изменения</span><span class="sxs-lookup"><span data-stu-id="da71c-133">Determine if you're affected</span></span>

<span data-ttu-id="da71c-134">Протестируйте свое веб-приложение с использованием версии клиента, которая может явно согласиться на новое поведение.</span><span class="sxs-lookup"><span data-stu-id="da71c-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="da71c-135">В Chrome, Firefox и Microsoft Edge Chromium предусмотрены флаги функции явного согласия, которые можно использовать для тестирования.</span><span class="sxs-lookup"><span data-stu-id="da71c-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="da71c-136">Убедитесь, что ваше приложение совместимо с более старыми версиями клиента после установки исправлений, что особенно актуально для Safari.</span><span class="sxs-lookup"><span data-stu-id="da71c-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="da71c-137">Дополнительные сведения см. в разделе [Поддержка более старых браузеров](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="da71c-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="da71c-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="da71c-138">Chrome</span></span>

<span data-ttu-id="da71c-139">Chrome 78 и более поздних версий дает неверные результаты тестирования.</span><span class="sxs-lookup"><span data-stu-id="da71c-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="da71c-140">Эти версии используют временные меры исправления и позволяют использовать файлы cookie, имеющие возраст менее двух минут.</span><span class="sxs-lookup"><span data-stu-id="da71c-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="da71c-141">При включении соответствующих флагов тестирования Chrome 76 и 77 дают более точные результаты.</span><span class="sxs-lookup"><span data-stu-id="da71c-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="da71c-142">Чтобы проверить новое поведение, включите `chrome://flags/#same-site-by-default-cookies`.</span><span class="sxs-lookup"><span data-stu-id="da71c-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="da71c-143">Для Chrome 75 и более ранних версий новый параметр `None` вызывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="da71c-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="da71c-144">Дополнительные сведения см. в разделе [Поддержка более старых браузеров](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="da71c-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="da71c-145">Google не предоставляет более старые версии Chrome.</span><span class="sxs-lookup"><span data-stu-id="da71c-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="da71c-146">Однако можно скачать более старые версии Chromium, которых достаточно для тестирования.</span><span class="sxs-lookup"><span data-stu-id="da71c-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="da71c-147">Следуйте указаниям на странице [скачивания Chromium](https://www.chromium.org/getting-involved/download-chromium).</span><span class="sxs-lookup"><span data-stu-id="da71c-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="da71c-148">Chromium 76 Win64</span><span class="sxs-lookup"><span data-stu-id="da71c-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="da71c-149">Chromium 74 Win64</span><span class="sxs-lookup"><span data-stu-id="da71c-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="da71c-150">Safari</span><span class="sxs-lookup"><span data-stu-id="da71c-150">Safari</span></span>

<span data-ttu-id="da71c-151">В Safari 12 строго реализован предыдущий проект стандарта, поэтому этот браузер завершается со сбоем, если встречает новое значение `None` в файлах cookie.</span><span class="sxs-lookup"><span data-stu-id="da71c-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="da71c-152">Такой сценарий следует исключить с помощью кода определения браузеров, приведенного в разделе [Поддержка более старых браузеров](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="da71c-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="da71c-153">Обязательно проведите тестирование Safari 12 и 13, а также процедур входа на основе WebKit и механизмов ОС с использованием Библиотеки проверки подлинности Майкрософт (MSAL), Библиотеки проверки подлинности Active Directory (ADAL) или любой другой библиотеки.</span><span class="sxs-lookup"><span data-stu-id="da71c-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="da71c-154">Эта проблема зависит от базовой версии ОС.</span><span class="sxs-lookup"><span data-stu-id="da71c-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="da71c-155">Известно, что в OSX Mojave 10.14 и iOS 12 имеются проблемы совместимости с этим новым поведением.</span><span class="sxs-lookup"><span data-stu-id="da71c-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="da71c-156">Обновление до OSX Catalina 10.15 или iOS 13 позволяет устранить их.</span><span class="sxs-lookup"><span data-stu-id="da71c-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="da71c-157">Сейчас в Safari нет флага явного согласия для тестирования поведения, описанного в новой спецификации.</span><span class="sxs-lookup"><span data-stu-id="da71c-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="da71c-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="da71c-158">Firefox</span></span>

<span data-ttu-id="da71c-159">Поддержку нового стандарта для Firefox можно проверить в версии 68 и более поздних, указав явное согласие на странице `about:config` с помощью флага компонента `network.cookie.sameSite.laxByDefault`.</span><span class="sxs-lookup"><span data-stu-id="da71c-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="da71c-160">Сведения о проблемах совместимости для более ранних версий Firefox отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="da71c-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="da71c-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="da71c-161">Microsoft Edge</span></span>

<span data-ttu-id="da71c-162">Хотя Microsoft Edge поддерживает старый стандарт `SameSite`, начиная с версии 44, в нем нет никаких проблем совместимости с новым стандартом.</span><span class="sxs-lookup"><span data-stu-id="da71c-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="da71c-163">Microsoft Edge Chromium</span><span class="sxs-lookup"><span data-stu-id="da71c-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="da71c-164">Используется флаг компонента `edge://flags/#same-site-by-default-cookies`.</span><span class="sxs-lookup"><span data-stu-id="da71c-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="da71c-165">При тестировании в Microsoft Chromium 78 никакие проблемы совместимости не наблюдались.</span><span class="sxs-lookup"><span data-stu-id="da71c-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="da71c-166">Electron</span><span class="sxs-lookup"><span data-stu-id="da71c-166">Electron</span></span>

<span data-ttu-id="da71c-167">Версии Electron включают в себя более старые версии Chromium.</span><span class="sxs-lookup"><span data-stu-id="da71c-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="da71c-168">Например, в Microsoft Teams используется версия Electron — Chromium 66, в которой реализовано старое поведение.</span><span class="sxs-lookup"><span data-stu-id="da71c-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="da71c-169">Выполните собственное тестирование совместимости для версии Electron, используемой вашим продуктом.</span><span class="sxs-lookup"><span data-stu-id="da71c-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="da71c-170">Дополнительные сведения см. в разделе [Поддержка более старых браузеров](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="da71c-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="da71c-171">Поддержка более старых браузеров</span><span class="sxs-lookup"><span data-stu-id="da71c-171">Support older browsers</span></span>

<span data-ttu-id="da71c-172">Стандарт `SameSite` за 2016 год предписывает обрабатывать неизвестные значения как значения `SameSite=Strict`.</span><span class="sxs-lookup"><span data-stu-id="da71c-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="da71c-173">Следовательно, все старые браузеры, поддерживающие оригинальный стандарт, могут прекращать работу, встретив свойство `SameSite` со значением `None`.</span><span class="sxs-lookup"><span data-stu-id="da71c-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="da71c-174">Если требуется поддерживать эти старые браузеры, веб-приложения должны реализовать определение браузеров.</span><span class="sxs-lookup"><span data-stu-id="da71c-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="da71c-175">ASP.NET Core не реализует определение браузеров, так как значения заголовков запросов `User-Agent` крайне непостоянны и меняются каждую неделю.</span><span class="sxs-lookup"><span data-stu-id="da71c-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="da71c-176">Вместо этого точка расширения в политике файлов cookie позволяет добавить логику, связанную с `User-Agent`.</span><span class="sxs-lookup"><span data-stu-id="da71c-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="da71c-177">Добавьте в файл *Startup.cs* следующий код:</span><span class="sxs-lookup"><span data-stu-id="da71c-177">In *Startup.cs*, add the following code:</span></span>

```csharp
private void CheckSameSite(HttpContext httpContext, CookieOptions options)
{
    if (options.SameSite == SameSiteMode.None)
    {
        var userAgent = httpContext.Request.Headers["User-Agent"].ToString();
        // TODO: Use your User Agent library of choice here.
        if (/* UserAgent doesn't support new behavior */)
        {
            options.SameSite = SameSiteMode.Unspecified;
        }
    }
}

public void ConfigureServices(IServiceCollection services)
{
    services.Configure<CookiePolicyOptions>(options =>
    {
        options.MinimumSameSitePolicy = SameSiteMode.Unspecified;
        options.OnAppendCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
        options.OnDeleteCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
    });
}

public void Configure(IApplicationBuilder app)
{
    // Before UseAuthentication or anything else that writes cookies.
    app.UseCookiePolicy();

    app.UseAuthentication();
    // code omitted for brevity
}
```

##### <a name="opt-out-switches"></a><span data-ttu-id="da71c-178">Параметры явного отказа</span><span class="sxs-lookup"><span data-stu-id="da71c-178">Opt-out switches</span></span>

<span data-ttu-id="da71c-179">Параметр совместимости `Microsoft.AspNetCore.SuppressSameSiteNone` позволяет временно явно отказаться от нового поведения файлов cookie ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="da71c-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="da71c-180">Добавьте следующий код JSON в файл *runtimeconfig.template.json* в своем проекте:</span><span class="sxs-lookup"><span data-stu-id="da71c-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="da71c-181">Другие версии</span><span class="sxs-lookup"><span data-stu-id="da71c-181">Other Versions</span></span>

<span data-ttu-id="da71c-182">Подготавливаются к выпуску соответствующие исправления `SameSite` для следующих продуктов:</span><span class="sxs-lookup"><span data-stu-id="da71c-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="da71c-183">ASP.NET Core 2.1, 2.2 и 3.0</span><span class="sxs-lookup"><span data-stu-id="da71c-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="da71c-184">`Microsoft.Owin` 4.1</span><span class="sxs-lookup"><span data-stu-id="da71c-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="da71c-185">`System.Web` (для .NET Framework 4.7.2 и более поздних версий)</span><span class="sxs-lookup"><span data-stu-id="da71c-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="da71c-186">Категория</span><span class="sxs-lookup"><span data-stu-id="da71c-186">Category</span></span>

<span data-ttu-id="da71c-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="da71c-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da71c-188">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="da71c-188">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieBuilder.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieOptions.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`
- `Overload:Microsoft.AspNetCore.Http.CookieBuilder.SameSite`
- `Overload:Microsoft.AspNetCore.Http.CookieOptions.SameSite`
- `T:Microsoft.AspNetCore.Http.SameSiteMode`
- `T:Microsoft.Net.Http.Headers.SameSiteMode`
- `Overload:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite`

-->
