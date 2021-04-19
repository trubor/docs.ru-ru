---
title: Критическое изменение. Kestrel. Атрибуты сообщения журнала изменились
description: Сведения о критическом изменении в ASP.NET Core 6.0 — Kestrel. Атрибуты сообщения журнала изменились
ms.author: scaddie
ms.date: 02/01/2021
ms.openlocfilehash: daeb9ae418f343a00e9563ef3e2b5090a7f016a9
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255172"
---
# <a name="kestrel-log-message-attributes-changed"></a><span data-ttu-id="d5c55-103">Kestrel. Атрибуты сообщения журнала изменились</span><span class="sxs-lookup"><span data-stu-id="d5c55-103">Kestrel: Log message attributes changed</span></span>

<span data-ttu-id="d5c55-104">У сообщений журнала Kestrel есть связанные идентификаторы и имена.</span><span class="sxs-lookup"><span data-stu-id="d5c55-104">Kestrel log messages have associated IDs and names.</span></span> <span data-ttu-id="d5c55-105">Эти атрибуты однозначно идентифицируют различные виды сообщений журнала.</span><span class="sxs-lookup"><span data-stu-id="d5c55-105">These attributes uniquely identify different kinds of log messages.</span></span> <span data-ttu-id="d5c55-106">Некоторые из этих идентификаторов и имен были ошибочно продублированы.</span><span class="sxs-lookup"><span data-stu-id="d5c55-106">Some of those IDs and names were incorrectly duplicated.</span></span> <span data-ttu-id="d5c55-107">В ASP.NET Core 6.0 проблема с дублированием исправлена.</span><span class="sxs-lookup"><span data-stu-id="d5c55-107">This duplication problem is fixed in ASP.NET Core 6.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d5c55-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="d5c55-108">Version introduced</span></span>

<span data-ttu-id="d5c55-109">ASP.NET Core 6.0</span><span class="sxs-lookup"><span data-stu-id="d5c55-109">ASP.NET Core 6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="d5c55-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="d5c55-110">Old behavior</span></span>

<span data-ttu-id="d5c55-111">В следующей таблице показано состояние затронутых сообщений журнала до выхода версии ASP.NET Core 6.0.</span><span class="sxs-lookup"><span data-stu-id="d5c55-111">The following table shows the state of the affected log messages before ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="d5c55-112">Описание сообщения</span><span class="sxs-lookup"><span data-stu-id="d5c55-112">Message description</span></span>                   | <span data-ttu-id="d5c55-113">Имя</span><span class="sxs-lookup"><span data-stu-id="d5c55-113">Name</span></span>                    | <span data-ttu-id="d5c55-114">ID</span><span class="sxs-lookup"><span data-stu-id="d5c55-114">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="d5c55-115">Сообщения журнала о закрытии подключений HTTP/2</span><span class="sxs-lookup"><span data-stu-id="d5c55-115">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="d5c55-116">36</span><span class="sxs-lookup"><span data-stu-id="d5c55-116">36</span></span> |
| <span data-ttu-id="d5c55-117">Сообщения журнала об отправке кадров HTTP/2</span><span class="sxs-lookup"><span data-stu-id="d5c55-117">HTTP/2 frame sending log messages</span></span>     | `Http2FrameReceived`    | <span data-ttu-id="d5c55-118">37</span><span class="sxs-lookup"><span data-stu-id="d5c55-118">37</span></span> |

## <a name="new-behavior"></a><span data-ttu-id="d5c55-119">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="d5c55-119">New behavior</span></span>

<span data-ttu-id="d5c55-120">В следующей таблице показано состояние затронутых сообщений журнала в версии ASP.NET Core 6.0.</span><span class="sxs-lookup"><span data-stu-id="d5c55-120">The following table shows the state of the affected log messages in ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="d5c55-121">Описание сообщения</span><span class="sxs-lookup"><span data-stu-id="d5c55-121">Message description</span></span>                   | <span data-ttu-id="d5c55-122">Имя</span><span class="sxs-lookup"><span data-stu-id="d5c55-122">Name</span></span>                    | <span data-ttu-id="d5c55-123">ID</span><span class="sxs-lookup"><span data-stu-id="d5c55-123">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="d5c55-124">Сообщения журнала о закрытии подключений HTTP/2</span><span class="sxs-lookup"><span data-stu-id="d5c55-124">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="d5c55-125">48</span><span class="sxs-lookup"><span data-stu-id="d5c55-125">48</span></span> |
| <span data-ttu-id="d5c55-126">Сообщения журнала об отправке кадров HTTP/2</span><span class="sxs-lookup"><span data-stu-id="d5c55-126">HTTP/2 frame sending log messages</span></span>     | `Http2FrameSending`     | <span data-ttu-id="d5c55-127">49</span><span class="sxs-lookup"><span data-stu-id="d5c55-127">49</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="d5c55-128">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="d5c55-128">Reason for change</span></span>

<span data-ttu-id="d5c55-129">Чтобы можно было идентифицировать разные типы сообщений, идентификаторы и имена журналов должны быть уникальными.</span><span class="sxs-lookup"><span data-stu-id="d5c55-129">Log IDs and names should be unique so different message types can be identified.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d5c55-130">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="d5c55-130">Recommended action</span></span>

<span data-ttu-id="d5c55-131">Если у вас есть код или конфигурация, которые ссылаются на старые идентификаторы и имена, обновите эти ссылки, чтобы в них указывались новые идентификаторы и имена.</span><span class="sxs-lookup"><span data-stu-id="d5c55-131">If you have code or configuration that references the old IDs and names, update those references to use the new IDs and names.</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
