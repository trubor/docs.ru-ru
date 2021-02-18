---
title: 'Критическое изменение. Blazor: изменено имя параметра в методе RequestImageFileAsync'
description: Сведения о критическом изменении в ASP.NET Core 6.0 — Blazor. изменено имя параметра в методе RequestImageFileAsync
author: scottaddie
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: bfaaa6bfe94c32fbc1a5b5b70db863d105d389b5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488264"
---
# <a name="blazor-parameter-name-changed-in-requestimagefileasync-method"></a><span data-ttu-id="90353-103">Blazor: изменено имя параметра в методе RequestImageFileAsync</span><span class="sxs-lookup"><span data-stu-id="90353-103">Blazor: Parameter name changed in RequestImageFileAsync method</span></span>

<span data-ttu-id="90353-104">Параметр `maxWith` метода `RequestImageFileAsync` был переименован из `maxWith` в `maxWidth`.</span><span class="sxs-lookup"><span data-stu-id="90353-104">The `RequestImageFileAsync` method's `maxWith` parameter was renamed from `maxWith` to `maxWidth`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="90353-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="90353-105">Version introduced</span></span>

<span data-ttu-id="90353-106">6.0, предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="90353-106">6.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="90353-107">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="90353-107">Old behavior</span></span>

<span data-ttu-id="90353-108">Имя параметра пишется как `maxWith`.</span><span class="sxs-lookup"><span data-stu-id="90353-108">The parameter name is spelled `maxWith`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="90353-109">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="90353-109">New behavior</span></span>

<span data-ttu-id="90353-110">Имя параметра пишется как `maxWidth`.</span><span class="sxs-lookup"><span data-stu-id="90353-110">The parameter name is spelled `maxWidth`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="90353-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="90353-111">Reason for change</span></span>

<span data-ttu-id="90353-112">Исходное имя параметра было типографической ошибкой.</span><span class="sxs-lookup"><span data-stu-id="90353-112">The original parameter name was a typographical error.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="90353-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="90353-113">Recommended action</span></span>

<span data-ttu-id="90353-114">Если вы используете именованные параметры в API `RequestImageFile`, измените имя параметра `maxWith` на `maxWidth`.</span><span class="sxs-lookup"><span data-stu-id="90353-114">If you're using named parameters in the `RequestImageFile` API, update the `maxWith` parameter name to `maxWidth`.</span></span> <span data-ttu-id="90353-115">В противном случае изменение не требуется.</span><span class="sxs-lookup"><span data-stu-id="90353-115">Otherwise, no change is necessary.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="90353-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="90353-116">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync`

-->
