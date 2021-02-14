---
title: Критическое изменение. Kestrel. Атрибуты сообщения журнала изменились
description: Сведения о критическом изменении в ASP.NET Core 6.0 — Kestrel. Атрибуты сообщения журнала изменились
author: scottaddie
ms.author: scaddie
ms.date: 02/01/2021
ms.openlocfilehash: 30b03c22a6c85623fec7db14b58b169f887395a0
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/04/2021
ms.locfileid: "99551542"
---
# <a name="kestrel-log-message-attributes-changed"></a><span data-ttu-id="c374e-103">Kestrel. Атрибуты сообщения журнала изменились</span><span class="sxs-lookup"><span data-stu-id="c374e-103">Kestrel: Log message attributes changed</span></span>

<span data-ttu-id="c374e-104">У сообщений журнала Kestrel есть связанные идентификаторы и имена.</span><span class="sxs-lookup"><span data-stu-id="c374e-104">Kestrel log messages have associated IDs and names.</span></span> <span data-ttu-id="c374e-105">Эти атрибуты однозначно идентифицируют различные виды сообщений журнала.</span><span class="sxs-lookup"><span data-stu-id="c374e-105">These attributes uniquely identify different kinds of log messages.</span></span> <span data-ttu-id="c374e-106">Некоторые из этих идентификаторов и имен были ошибочно продублированы.</span><span class="sxs-lookup"><span data-stu-id="c374e-106">Some of those IDs and names were incorrectly duplicated.</span></span> <span data-ttu-id="c374e-107">В ASP.NET Core 6.0 проблема с дублированием исправлена.</span><span class="sxs-lookup"><span data-stu-id="c374e-107">This duplication problem is fixed in ASP.NET Core 6.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c374e-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="c374e-108">Version introduced</span></span>

<span data-ttu-id="c374e-109">6,0</span><span class="sxs-lookup"><span data-stu-id="c374e-109">6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="c374e-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="c374e-110">Old behavior</span></span>

<span data-ttu-id="c374e-111">В следующей таблице показано состояние затронутых сообщений журнала до выхода версии ASP.NET Core 6.0.</span><span class="sxs-lookup"><span data-stu-id="c374e-111">The following table shows the state of the affected log messages before ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="c374e-112">Описание сообщения</span><span class="sxs-lookup"><span data-stu-id="c374e-112">Message description</span></span>                   | <span data-ttu-id="c374e-113">Имя</span><span class="sxs-lookup"><span data-stu-id="c374e-113">Name</span></span>                    | <span data-ttu-id="c374e-114">ID</span><span class="sxs-lookup"><span data-stu-id="c374e-114">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="c374e-115">Сообщения журнала о закрытии подключений HTTP/2</span><span class="sxs-lookup"><span data-stu-id="c374e-115">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="c374e-116">36</span><span class="sxs-lookup"><span data-stu-id="c374e-116">36</span></span> |
| <span data-ttu-id="c374e-117">Сообщения журнала об отправке кадров HTTP/2</span><span class="sxs-lookup"><span data-stu-id="c374e-117">HTTP/2 frame sending log messages</span></span>     | `Http2FrameReceived`    | <span data-ttu-id="c374e-118">37</span><span class="sxs-lookup"><span data-stu-id="c374e-118">37</span></span> |

## <a name="new-behavior"></a><span data-ttu-id="c374e-119">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="c374e-119">New behavior</span></span>

<span data-ttu-id="c374e-120">В следующей таблице показано состояние затронутых сообщений журнала в версии ASP.NET Core 6.0.</span><span class="sxs-lookup"><span data-stu-id="c374e-120">The following table shows the state of the affected log messages in ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="c374e-121">Описание сообщения</span><span class="sxs-lookup"><span data-stu-id="c374e-121">Message description</span></span>                   | <span data-ttu-id="c374e-122">Имя</span><span class="sxs-lookup"><span data-stu-id="c374e-122">Name</span></span>                    | <span data-ttu-id="c374e-123">ID</span><span class="sxs-lookup"><span data-stu-id="c374e-123">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="c374e-124">Сообщения журнала о закрытии подключений HTTP/2</span><span class="sxs-lookup"><span data-stu-id="c374e-124">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="c374e-125">48</span><span class="sxs-lookup"><span data-stu-id="c374e-125">48</span></span> |
| <span data-ttu-id="c374e-126">Сообщения журнала об отправке кадров HTTP/2</span><span class="sxs-lookup"><span data-stu-id="c374e-126">HTTP/2 frame sending log messages</span></span>     | `Http2FrameSending`     | <span data-ttu-id="c374e-127">49</span><span class="sxs-lookup"><span data-stu-id="c374e-127">49</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="c374e-128">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="c374e-128">Reason for change</span></span>

<span data-ttu-id="c374e-129">Чтобы можно было идентифицировать разные типы сообщений, идентификаторы и имена журналов должны быть уникальными.</span><span class="sxs-lookup"><span data-stu-id="c374e-129">Log IDs and names should be unique so different message types can be identified.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c374e-130">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="c374e-130">Recommended action</span></span>

<span data-ttu-id="c374e-131">Если у вас есть код или конфигурация, которые ссылаются на старые идентификаторы и имена, обновите эти ссылки, чтобы в них указывались новые идентификаторы и имена.</span><span class="sxs-lookup"><span data-stu-id="c374e-131">If you have code or configuration that references the old IDs and names, update those references to use the new IDs and names.</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
