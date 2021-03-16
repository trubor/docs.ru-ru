---
title: 'Критическое изменение в Blazor: свойство WebEventDescriptor.EventArgsType заменено'
description: 'Сведения о критическом изменении в ASP.NET Core 6.0: свойство WebEventDescriptor.EventArgsType заменено свойством EventName.'
author: scottaddie
ms.author: scaddie
ms.date: 02/24/2021
no-loc:
- Blazor
ms.openlocfilehash: 6df086ed234c0071ede83e9fe9d1710f011a2039
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102260018"
---
# <a name="blazor-no-loc-textwebeventdescriptoreventargstype-property-replaced"></a><span data-ttu-id="85eb7-103">Blazor: свойство :::no-loc text="WebEventDescriptor.EventArgsType"::: заменено</span><span class="sxs-lookup"><span data-stu-id="85eb7-103">Blazor: :::no-loc text="WebEventDescriptor.EventArgsType"::: property replaced</span></span>

<span data-ttu-id="85eb7-104">Класс <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor> является частью внутреннего протокола Blazor для обмена событиями между JavaScript и .NET.</span><span class="sxs-lookup"><span data-stu-id="85eb7-104">The <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor> class is part of Blazor's internal protocol for communicating events from JavaScript into .NET.</span></span> <span data-ttu-id="85eb7-105">Этот класс обычно используется не кодом приложения, а разработчиками платформы.</span><span class="sxs-lookup"><span data-stu-id="85eb7-105">This class isn't typically used by app code, but rather by platform authors.</span></span>

<span data-ttu-id="85eb7-106">Начиная с ASP.NET Core 6.0, свойство <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A> в `WebEventDescriptor` заменяется новым свойством `EventName`.</span><span class="sxs-lookup"><span data-stu-id="85eb7-106">Starting in ASP.NET Core 6.0, the <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A> property on `WebEventDescriptor` is being replaced by a new `EventName` property.</span></span> <span data-ttu-id="85eb7-107">Это изменение не должно повлиять на код приложения, так как относится к низкоуровневой реализации платформы.</span><span class="sxs-lookup"><span data-stu-id="85eb7-107">This change is unlikely to affect any app code, as it's a low-level platform implementation detail.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="85eb7-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="85eb7-108">Version introduced</span></span>

<span data-ttu-id="85eb7-109">6,0</span><span class="sxs-lookup"><span data-stu-id="85eb7-109">6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="85eb7-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="85eb7-110">Old behavior</span></span>

<span data-ttu-id="85eb7-111">В ASP.NET Core 5.0 и более ранних версий свойство `EventArgsType` описывает нестандартное имя категории, используемое только в Blazor, для групп типов событий DOM.</span><span class="sxs-lookup"><span data-stu-id="85eb7-111">In ASP.NET Core 5.0 and earlier, the property `EventArgsType` describes a nonstandard, Blazor-specific category name for groups of DOM event types.</span></span> <span data-ttu-id="85eb7-112">Например, события `click` и `mousedown` сопоставлены со значением `EventArgsType`=`mouse`.</span><span class="sxs-lookup"><span data-stu-id="85eb7-112">For example, the `click` and `mousedown` events were both mapped to an `EventArgsType` value of `mouse`.</span></span> <span data-ttu-id="85eb7-113">Аналогично, события `cut`, `copy` и `paste` сопоставлены со значением `EventArgsType`=`clipboard`.</span><span class="sxs-lookup"><span data-stu-id="85eb7-113">Similarly, `cut`, `copy`, and `paste` events are mapped to an `EventArgsType` value of `clipboard`.</span></span> <span data-ttu-id="85eb7-114">Эти имена категорий используются для определения типа .NET, используемого при десериализации входных данных аргументов события.</span><span class="sxs-lookup"><span data-stu-id="85eb7-114">These category names are used to determine the .NET type to use for deserializing the incoming event arguments data.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="85eb7-115">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="85eb7-115">New behavior</span></span>

<span data-ttu-id="85eb7-116">Начиная с ASP.NET Core 6.0, новое свойство `EventName` содержит только имя исходного события.</span><span class="sxs-lookup"><span data-stu-id="85eb7-116">Starting in ASP.NET Core 6.0, the new property `EventName` only specifies the original event's name.</span></span> <span data-ttu-id="85eb7-117">Примеры: `click`, `mousedown`, `cut`, `copy` или `paste`.</span><span class="sxs-lookup"><span data-stu-id="85eb7-117">For example, `click`, `mousedown`, `cut`, `copy`, or `paste`.</span></span> <span data-ttu-id="85eb7-118">Больше нет необходимости предоставлять имя категории для Blazor.</span><span class="sxs-lookup"><span data-stu-id="85eb7-118">There's no longer a need to supply a Blazor-specific category name.</span></span> <span data-ttu-id="85eb7-119">По этой причине старое свойство `EventArgsType` удаляется.</span><span class="sxs-lookup"><span data-stu-id="85eb7-119">For that reason, the old property `EventArgsType` is removed.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="85eb7-120">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="85eb7-120">Reason for change</span></span>

<span data-ttu-id="85eb7-121">В запросе на вытягивание [dotnet/aspnetcore#29993](https://github.com/dotnet/aspnetcore/pull/29993) была добавлена поддержка классов пользовательских аргументов событий.</span><span class="sxs-lookup"><span data-stu-id="85eb7-121">In pull request [dotnet/aspnetcore#29993](https://github.com/dotnet/aspnetcore/pull/29993), support for custom event arguments classes was introduced.</span></span> <span data-ttu-id="85eb7-122">В рамках этой поддержки платформа больше не предполагает, что все события относятся к предопределенному набору категорий.</span><span class="sxs-lookup"><span data-stu-id="85eb7-122">As part of this support, the framework no longer relies on all events fitting into a predefined set of categories.</span></span> <span data-ttu-id="85eb7-123">Теперь платформе достаточно знать имя исходного события.</span><span class="sxs-lookup"><span data-stu-id="85eb7-123">The framework now only needs to know the original event name.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="85eb7-124">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="85eb7-124">Recommended action</span></span>

<span data-ttu-id="85eb7-125">Это не должно повлиять на код приложений, и вам ничего не придется изменять.</span><span class="sxs-lookup"><span data-stu-id="85eb7-125">App code should be unaffected and doesn't need to change.</span></span>

<span data-ttu-id="85eb7-126">Если вы создаете пользовательскую платформу отрисовки Blazor, может потребоваться обновить механизм диспетчеризации событий в `Renderer`.</span><span class="sxs-lookup"><span data-stu-id="85eb7-126">If building a custom Blazor rendering platform, you may need to update the mechanism for dispatching events into the `Renderer`.</span></span> <span data-ttu-id="85eb7-127">Замените все жестко закодированные правила для категорий событий на более простую логику, которая предоставляет исходное имя необработанного события.</span><span class="sxs-lookup"><span data-stu-id="85eb7-127">Replace any hardcoded rules about event categories with simpler logic that supplies the original, raw event name.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="85eb7-128">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="85eb7-128">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`P:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType`

-->
