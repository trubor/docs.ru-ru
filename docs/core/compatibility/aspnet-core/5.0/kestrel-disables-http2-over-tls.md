---
title: Критическое изменение. Kestrel. HTTP/2 по TLS отключен в несовместимых версиях Windows
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Kestrel. HTTP/2 по TLS отключен в несовместимых версиях Windows
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b8bbe113b3357508b6af29fa9a4d1431f6a6acea
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498117"
---
# <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a><span data-ttu-id="690ed-103">Kestrel. HTTP/2 по TLS отключен в несовместимых версиях Windows</span><span class="sxs-lookup"><span data-stu-id="690ed-103">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>

<span data-ttu-id="690ed-104">Чтобы включить HTTP/2 по TLS в Windows, необходимо выполнить два условия:</span><span class="sxs-lookup"><span data-stu-id="690ed-104">To enable HTTP/2 over Transport Layer Security (TLS) on Windows, two requirements need to be met:</span></span>

- <span data-ttu-id="690ed-105">поддержка согласования протокола уровня приложений доступна, начиная с Windows 8.1 и Windows Server 2012 R2;</span><span class="sxs-lookup"><span data-stu-id="690ed-105">Application-Layer Protocol Negotiation (ALPN) support, which is available starting with Windows 8.1 and Windows Server 2012 R2.</span></span>
- <span data-ttu-id="690ed-106">набор шифров, совместимых с HTTP/2, доступен, начиная с Windows 10 и Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="690ed-106">A set of ciphers compatible with HTTP/2, which is available starting with Windows 10 and Windows Server 2016.</span></span>

<span data-ttu-id="690ed-107">Таким образом, поведение Kestrel при настройке HTTP/2 по протоколу TLS изменилось следующим образом:</span><span class="sxs-lookup"><span data-stu-id="690ed-107">As such, Kestrel's behavior when HTTP/2 over TLS is configured has changed to:</span></span>

- <span data-ttu-id="690ed-108">Переход на использование более ранней версии `Http1` и регистрация сообщения в журнале на уровне `Information`, если [ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) имеет значение `Http1AndHttp2`.</span><span class="sxs-lookup"><span data-stu-id="690ed-108">Downgrade to `Http1` and log a message at the `Information` level when [ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) is set to `Http1AndHttp2`.</span></span> <span data-ttu-id="690ed-109">Значение `Http1AndHttp2` является значением по умолчанию для свойства `ListenOptions.HttpProtocols`.</span><span class="sxs-lookup"><span data-stu-id="690ed-109">`Http1AndHttp2` is the default value for `ListenOptions.HttpProtocols`.</span></span>
- <span data-ttu-id="690ed-110">Выводится `NotSupportedException`, если `ListenOptions.HttpProtocols` имеет значение `Http2`.</span><span class="sxs-lookup"><span data-stu-id="690ed-110">Throw a `NotSupportedException` when `ListenOptions.HttpProtocols` is set to `Http2`.</span></span>

<span data-ttu-id="690ed-111">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068).</span><span class="sxs-lookup"><span data-stu-id="690ed-111">For discussion, see issue [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="690ed-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="690ed-112">Version introduced</span></span>

<span data-ttu-id="690ed-113">ASP.NET Core 5.0 (предварительная версия 7)</span><span class="sxs-lookup"><span data-stu-id="690ed-113">ASP.NET Core 5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="690ed-114">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="690ed-114">Old behavior</span></span>

<span data-ttu-id="690ed-115">В следующей таблице показано поведение при настройке HTTP/2 по TLS.</span><span class="sxs-lookup"><span data-stu-id="690ed-115">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="690ed-116">Протоколы</span><span class="sxs-lookup"><span data-stu-id="690ed-116">Protocols</span></span> | <span data-ttu-id="690ed-117">Windows 7,</span><span class="sxs-lookup"><span data-stu-id="690ed-117">Windows 7,</span></span><br /><span data-ttu-id="690ed-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="690ed-118">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="690ed-119">или более ранней версии</span><span class="sxs-lookup"><span data-stu-id="690ed-119">or earlier</span></span> | <span data-ttu-id="690ed-120">Windows 8,</span><span class="sxs-lookup"><span data-stu-id="690ed-120">Windows 8,</span></span><br /><span data-ttu-id="690ed-121">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="690ed-121">Windows Server 2012</span></span> | <span data-ttu-id="690ed-122">Windows 8.1,</span><span class="sxs-lookup"><span data-stu-id="690ed-122">Windows 8.1,</span></span><br /><span data-ttu-id="690ed-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="690ed-123">Windows Server 2012 R2</span></span> | <span data-ttu-id="690ed-124">Windows 10,</span><span class="sxs-lookup"><span data-stu-id="690ed-124">Windows 10,</span></span><br /><span data-ttu-id="690ed-125">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="690ed-125">Windows Server 2016,</span></span><br /><span data-ttu-id="690ed-126">или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="690ed-126">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="690ed-127">Выводится `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="690ed-127">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="690ed-128">Ошибка при подтверждении соединения по TLS</span><span class="sxs-lookup"><span data-stu-id="690ed-128">Error during TLS handshake</span></span>     | <span data-ttu-id="690ed-129">Ошибка при подтверждении соединения по TLS &ast;</span><span class="sxs-lookup"><span data-stu-id="690ed-129">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="690ed-130">Без ошибок</span><span class="sxs-lookup"><span data-stu-id="690ed-130">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="690ed-131">Переход на использование более ранней версии `Http1`</span><span class="sxs-lookup"><span data-stu-id="690ed-131">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="690ed-132">Переход на использование более ранней версии `Http1`</span><span class="sxs-lookup"><span data-stu-id="690ed-132">Downgrade to `Http1`</span></span>     | <span data-ttu-id="690ed-133">Ошибка при подтверждении соединения по TLS &ast;</span><span class="sxs-lookup"><span data-stu-id="690ed-133">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="690ed-134">Без ошибок</span><span class="sxs-lookup"><span data-stu-id="690ed-134">No error</span></span> |

<span data-ttu-id="690ed-135">&ast; Настройте совместимые комплекты шифров, чтобы включить эти сценарии.</span><span class="sxs-lookup"><span data-stu-id="690ed-135">&ast; Configure compatible cipher suites to enable these scenarios.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="690ed-136">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="690ed-136">New behavior</span></span>

<span data-ttu-id="690ed-137">В следующей таблице показано поведение при настройке HTTP/2 по TLS.</span><span class="sxs-lookup"><span data-stu-id="690ed-137">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="690ed-138">Протоколы</span><span class="sxs-lookup"><span data-stu-id="690ed-138">Protocols</span></span> | <span data-ttu-id="690ed-139">Windows 7,</span><span class="sxs-lookup"><span data-stu-id="690ed-139">Windows 7,</span></span><br /><span data-ttu-id="690ed-140">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="690ed-140">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="690ed-141">или более ранней версии</span><span class="sxs-lookup"><span data-stu-id="690ed-141">or earlier</span></span> | <span data-ttu-id="690ed-142">Windows 8,</span><span class="sxs-lookup"><span data-stu-id="690ed-142">Windows 8,</span></span><br /><span data-ttu-id="690ed-143">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="690ed-143">Windows Server 2012</span></span> | <span data-ttu-id="690ed-144">Windows 8.1,</span><span class="sxs-lookup"><span data-stu-id="690ed-144">Windows 8.1,</span></span><br /><span data-ttu-id="690ed-145">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="690ed-145">Windows Server 2012 R2</span></span> | <span data-ttu-id="690ed-146">Windows 10,</span><span class="sxs-lookup"><span data-stu-id="690ed-146">Windows 10,</span></span><br /><span data-ttu-id="690ed-147">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="690ed-147">Windows Server 2016,</span></span><br /><span data-ttu-id="690ed-148">или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="690ed-148">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="690ed-149">Выводится `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="690ed-149">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="690ed-150">Выводится `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="690ed-150">Throw `NotSupportedException`</span></span>     | <span data-ttu-id="690ed-151">Выводится `NotSupportedException` &ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="690ed-151">Throw `NotSupportedException` &ast;&ast;</span></span>     | <span data-ttu-id="690ed-152">Без ошибок</span><span class="sxs-lookup"><span data-stu-id="690ed-152">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="690ed-153">Переход на использование более ранней версии `Http1`</span><span class="sxs-lookup"><span data-stu-id="690ed-153">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="690ed-154">Переход на использование более ранней версии `Http1`</span><span class="sxs-lookup"><span data-stu-id="690ed-154">Downgrade to `Http1`</span></span>     | <span data-ttu-id="690ed-155">Переход на использование более ранней версии `Http1` &ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="690ed-155">Downgrade to `Http1` &ast;&ast;</span></span>     | <span data-ttu-id="690ed-156">Без ошибок</span><span class="sxs-lookup"><span data-stu-id="690ed-156">No error</span></span> |

<span data-ttu-id="690ed-157">&ast;&ast; Настройте совместимые комплекты шифров и задайте для параметра контекста приложения `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` значение `true`, чтобы включить эти сценарии.</span><span class="sxs-lookup"><span data-stu-id="690ed-157">&ast;&ast; Configure compatible cipher suites and set the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` to `true` to enable these scenarios.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="690ed-158">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="690ed-158">Reason for change</span></span>

<span data-ttu-id="690ed-159">Это изменение гарантирует, что ошибки совместимости для HTTP/2 по TLS в более старых версиях Windows отображаются как можно раньше и точнее.</span><span class="sxs-lookup"><span data-stu-id="690ed-159">This change ensures compatibility errors for HTTP/2 over TLS on older Windows versions are surfaced as early and as clearly as possible.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="690ed-160">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="690ed-160">Recommended action</span></span>

<span data-ttu-id="690ed-161">Необходимо обеспечить отключение HTTP/2 по TLS в несовместимых версиях Windows.</span><span class="sxs-lookup"><span data-stu-id="690ed-161">Ensure HTTP/2 over TLS is disabled on incompatible Windows versions.</span></span> <span data-ttu-id="690ed-162">Windows 8.1 и Windows Server 2012 R2 несовместимы, так как по умолчанию в них отсутствуют необходимые шифры.</span><span class="sxs-lookup"><span data-stu-id="690ed-162">Windows 8.1 and Windows Server 2012 R2 are incompatible since they lack the necessary ciphers by default.</span></span> <span data-ttu-id="690ed-163">Однако можно обновить параметры конфигурации компьютера для использования шифров, совместимых с HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="690ed-163">However, it's possible to update the Computer Configuration settings to use HTTP/2 compatible ciphers.</span></span> <span data-ttu-id="690ed-164">Дополнительные сведения см. в разделе [Комплекты шифров TLS в Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span><span class="sxs-lookup"><span data-stu-id="690ed-164">For more information, see [TLS cipher suites in Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span></span> <span data-ttu-id="690ed-165">После настройки необходимо включить HTTP/2 по TLS в Kestrel путем настройки параметра контекста приложения `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2`.</span><span class="sxs-lookup"><span data-stu-id="690ed-165">Once configured, HTTP/2 over TLS on Kestrel must be enabled by setting the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2`.</span></span> <span data-ttu-id="690ed-166">Пример:</span><span class="sxs-lookup"><span data-stu-id="690ed-166">For example:</span></span>

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

<span data-ttu-id="690ed-167">Основная поддержка не изменилась.</span><span class="sxs-lookup"><span data-stu-id="690ed-167">No underlying support has changed.</span></span> <span data-ttu-id="690ed-168">Например, HTTP/2 по TLS никогда не поддерживался в Windows 8 и Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="690ed-168">For example, HTTP/2 over TLS has never worked on Windows 8 or Windows Server 2012.</span></span> <span data-ttu-id="690ed-169">В результате этого изменения меняется представление ошибок в этих неподдерживаемых сценариях.</span><span class="sxs-lookup"><span data-stu-id="690ed-169">This change modifies how errors in these unsupported scenarios are presented.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="690ed-170">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="690ed-170">Affected APIs</span></span>

<span data-ttu-id="690ed-171">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="690ed-171">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
