---
title: Критическое изменение. Локализация. Из ПО промежуточного слоя локализации запроса удален устаревший конструктор
description: Сведения о критическом изменении в ASP.NET Core 5.0 — локализация. Из ПО промежуточного слоя локализации запроса удален устаревший конструктор
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 53dd0f25078dae140d34d6d21d66983f78b8bdb0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759958"
---
# <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a><span data-ttu-id="6d49c-103">Локализация. Из ПО промежуточного слоя локализации запроса удален устаревший конструктор</span><span class="sxs-lookup"><span data-stu-id="6d49c-103">Localization: Obsolete constructor removed in request localization middleware</span></span>

<span data-ttu-id="6d49c-104">Конструктор <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware>, в котором отсутствует параметр <xref:Microsoft.Extensions.Logging.ILoggerFactory>, был помечен [в этой фиксации](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0) как устаревший.</span><span class="sxs-lookup"><span data-stu-id="6d49c-104">The <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructor that lacks an <xref:Microsoft.Extensions.Logging.ILoggerFactory> parameter was marked as obsolete [in this commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span></span> <span data-ttu-id="6d49c-105">В ASP.NET Core 5.0 устаревший конструктор был удален.</span><span class="sxs-lookup"><span data-stu-id="6d49c-105">In ASP.NET Core 5.0, the obsolete constructor was removed.</span></span> <span data-ttu-id="6d49c-106">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span><span class="sxs-lookup"><span data-stu-id="6d49c-106">For discussion, see [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="6d49c-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="6d49c-107">Version introduced</span></span>

<span data-ttu-id="6d49c-108">5.0, предварительная версия 8</span><span class="sxs-lookup"><span data-stu-id="6d49c-108">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="6d49c-109">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="6d49c-109">Old behavior</span></span>

<span data-ttu-id="6d49c-110">Присутствует устаревший конструктор `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)`.</span><span class="sxs-lookup"><span data-stu-id="6d49c-110">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor exists.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="6d49c-111">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="6d49c-111">New behavior</span></span>

<span data-ttu-id="6d49c-112">Устаревший конструктор `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` удален.</span><span class="sxs-lookup"><span data-stu-id="6d49c-112">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor doesn't exist.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="6d49c-113">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="6d49c-113">Reason for change</span></span>

<span data-ttu-id="6d49c-114">Это изменение гарантирует, что ПО промежуточного слоя локализации запроса будет всегда иметь доступ к средству ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="6d49c-114">This change ensures that the request localization middleware always has access to a logger.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="6d49c-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="6d49c-115">Recommended action</span></span>

<span data-ttu-id="6d49c-116">При создании экземпляра `RequestLocalizationMiddleware` вручную передайте экземпляр `ILoggerFactory` в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="6d49c-116">When manually constructing an instance of `RequestLocalizationMiddleware`, pass an `ILoggerFactory` instance in the constructor.</span></span> <span data-ttu-id="6d49c-117">Если допустимый экземпляр `ILoggerFactory` недоступен в этом контексте, попробуйте передать конструктор ПО промежуточного слоя экземпляру <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory>.</span><span class="sxs-lookup"><span data-stu-id="6d49c-117">If a valid `ILoggerFactory` instance isn't available in that context, consider passing the middleware constructor a <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="6d49c-118">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="6d49c-118">Affected APIs</span></span>

[<span data-ttu-id="6d49c-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span><span class="sxs-lookup"><span data-stu-id="6d49c-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span></span>](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

### Category

ASP.NET Core

### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
