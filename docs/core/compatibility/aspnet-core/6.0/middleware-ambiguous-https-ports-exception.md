---
title: 'Критическое изменение. ПО промежуточного слоя: ПО промежуточного слоя перенаправления HTTPS создает исключение для неоднозначных портов HTTPS'
description: Сведения о критическом изменении в ASP.NET Core 6.0 — ПО промежуточного слоя. ПО промежуточного слоя перенаправления HTTPS создает исключение для неоднозначных портов HTTPS
author: scottaddie
ms.author: scaddie
ms.date: 02/04/2021
ms.openlocfilehash: 1f49e0df7eaa2eecd83643c9596e745109a340b7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488259"
---
# <a name="middleware-https-redirection-middleware-throws-exception-on-ambiguous-https-ports"></a><span data-ttu-id="b7d6d-103">ПО промежуточного слоя: ПО промежуточного слоя перенаправления HTTPS создает исключение для неоднозначных портов HTTPS</span><span class="sxs-lookup"><span data-stu-id="b7d6d-103">Middleware: HTTPS Redirection Middleware throws exception on ambiguous HTTPS ports</span></span>

<span data-ttu-id="b7d6d-104">В ASP.NET Core 6.0 [ПО промежуточного слоя перенаправления HTTPS](xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A) вызывает исключение типа <xref:System.InvalidOperationException> при обнаружении нескольких портов HTTPS в конфигурации сервера.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-104">In ASP.NET Core 6.0, the [HTTPS Redirection Middleware](xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A) throws an exception of type <xref:System.InvalidOperationException> when it finds multiple HTTPS ports in the server configuration.</span></span> <span data-ttu-id="b7d6d-105">Сообщение исключения содержит текст "Не удается определить HTTPS порт от IServerAddressesFeature, найдено несколько значений.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-105">The exception's message contains the text "Cannot determine the https port from IServerAddressesFeature, multiple values were found.</span></span> <span data-ttu-id="b7d6d-106">Задайте требуемый порт явно в HttpsRedirectionOptions.HttpsPort."</span><span class="sxs-lookup"><span data-stu-id="b7d6d-106">Set the desired port explicitly on HttpsRedirectionOptions.HttpsPort."</span></span>

<span data-ttu-id="b7d6d-107">Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#29222](https://github.com/dotnet/aspnetcore/issues/29222).</span><span class="sxs-lookup"><span data-stu-id="b7d6d-107">For discussion, see GitHub issue [dotnet/aspnetcore#29222](https://github.com/dotnet/aspnetcore/issues/29222).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b7d6d-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="b7d6d-108">Version introduced</span></span>

<span data-ttu-id="b7d6d-109">6,0</span><span class="sxs-lookup"><span data-stu-id="b7d6d-109">6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="b7d6d-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="b7d6d-110">Old behavior</span></span>

<span data-ttu-id="b7d6d-111">Если ПО промежуточного слоя перенаправления HTTPS не настроено явно с помощью порта, во время первого запроса выполняется поиск <xref:Microsoft.AspNetCore.Hosting.Server.Features.IServerAddressesFeature>, чтобы определить HTTPS-порт, на который должно выполняться перенаправление.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-111">When the HTTPS Redirection Middleware isn't explicitly configured with a port, it searches <xref:Microsoft.AspNetCore.Hosting.Server.Features.IServerAddressesFeature> during the first request to determine the HTTPS port to which it should redirect.</span></span>

<span data-ttu-id="b7d6d-112">Если нет HTTPS-портов или нескольких отдельных портов, то неясно, какой порт следует использовать.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-112">If there are no HTTPS ports or multiple distinct ports, it's unclear which port should be used.</span></span> <span data-ttu-id="b7d6d-113">ПО промежуточного слоя регистрирует предупреждение и отключается.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-113">The middleware logs a warning and disables itself.</span></span> <span data-ttu-id="b7d6d-114">HTTP-запросы обрабатываются обычным образом.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-114">HTTP requests are processed normally.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="b7d6d-115">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="b7d6d-115">New behavior</span></span>

<span data-ttu-id="b7d6d-116">Если ПО промежуточного слоя перенаправления HTTPS не настроено явно с помощью порта, во время первого запроса выполняется поиск `IServerAddressesFeature`, чтобы определить HTTPS-порт, на который должно выполняться перенаправление.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-116">When the HTTPS Redirection Middleware isn't explicitly configured with a port, it searches `IServerAddressesFeature` during the first request to determine the HTTPS port to which it should redirect.</span></span>

<span data-ttu-id="b7d6d-117">Если HTTPS-порты отсутствуют, то ПО промежуточного слоя по-прежнему регистрирует предупреждение и отключается.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-117">If there are no HTTPS ports, the middleware still logs a warning and disables itself.</span></span> <span data-ttu-id="b7d6d-118">HTTP-запросы обрабатываются обычным образом.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-118">HTTP requests are processed normally.</span></span> <span data-ttu-id="b7d6d-119">Это поведение поддерживает следующее:</span><span class="sxs-lookup"><span data-stu-id="b7d6d-119">This behavior supports:</span></span>

* <span data-ttu-id="b7d6d-120">Сценарии разработки без протокола HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-120">Development scenarios without HTTPS.</span></span>
* <span data-ttu-id="b7d6d-121">Сценарии размещения, в которых работа протокола TLS завершается до достижения сервера.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-121">Hosted scenarios in which TLS is terminated before reaching the server.</span></span>

<span data-ttu-id="b7d6d-122">При наличии нескольких разных портов неясно, какой порт следует использовать.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-122">If there are multiple distinct ports, it's unclear which port should be used.</span></span> <span data-ttu-id="b7d6d-123">ПО промежуточного слоя создает исключение и обработка HTTP-запроса завершается сбоем.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-123">The middleware throws an exception and fails the HTTP request.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b7d6d-124">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="b7d6d-124">Reason for change</span></span>

<span data-ttu-id="b7d6d-125">Это изменение предотвращает возможность обслуживания потенциально конфиденциальных данных через незашифрованные HTTP-соединения, если известно, что протокол HTTPS доступен.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-125">This change prevents potentially sensitive data from being served over unencrypted HTTP connections when HTTPS is known to be available.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b7d6d-126">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="b7d6d-126">Recommended action</span></span>

<span data-ttu-id="b7d6d-127">Чтобы включить перенаправление HTTPS, если на сервере имеется несколько HTTPS-портов, в конфигурации необходимо указать один порт.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-127">To enable HTTPS redirection when the server has multiple distinct HTTPS ports, you must specify one port in the configuration.</span></span> <span data-ttu-id="b7d6d-128">Дополнительные сведения см. в разделе [Конфигурация портов](/aspnet/core/security/enforcing-ssl?view=aspnetcore-5.0&preserve-view=true#port-configuration).</span><span class="sxs-lookup"><span data-stu-id="b7d6d-128">For more information, see [Port configuration](/aspnet/core/security/enforcing-ssl?view=aspnetcore-5.0&preserve-view=true#port-configuration).</span></span>

<span data-ttu-id="b7d6d-129">Если ПО промежуточного слоя перенаправления HTTPS в приложении не требуется, удалите `UseHttpsRedirection` из *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="b7d6d-129">If you don't need the HTTPS Redirection Middleware in your app, remove `UseHttpsRedirection` from *Startup.cs*.</span></span>

<span data-ttu-id="b7d6d-130">Если необходимо динамически выбрать правильный HTTPS-порт, оставьте отзыв в статье на сайте GitHub [dotnet/aspnetcore#21291](https://github.com/dotnet/aspnetcore/issues/21291).</span><span class="sxs-lookup"><span data-stu-id="b7d6d-130">If you need to select the correct HTTPS port dynamically, provide feedback in GitHub issue [dotnet/aspnetcore#21291](https://github.com/dotnet/aspnetcore/issues/21291).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b7d6d-131">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="b7d6d-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection`

-->
