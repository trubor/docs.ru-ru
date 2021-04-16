---
title: События конфликтов блокировки монитора в среде выполнения
description: См. события ETW, собирающие сведения, относящиеся к конфликтам блокировки монитора.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- monitor lock contention events (CoreCLR)
- ETW, EventPipe, LTTng contention events (CoreCLR)
ms.openlocfilehash: 38e5f493d4b223b4839dbd6f814cf656722189b2
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594053"
---
# <a name="net-runtime-contention-events"></a><span data-ttu-id="895e3-103">События конфликтов среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="895e3-103">.NET runtime contention events</span></span>

<span data-ttu-id="895e3-104">Эти события среды выполнения записывают сведения о конфликтах блокировки монитора с `Monitor.Enter` или ключевым словом C# lock.</span><span class="sxs-lookup"><span data-stu-id="895e3-104">These runtime events capture information about monitor lock contentions such as with `Monitor.Enter` or the C# lock keyword.</span></span> <span data-ttu-id="895e3-105">Дополнительные сведения об использовании этих событий в целях диагностики см. в статье [Ведение журнала и трассировка в приложениях .NET](../../core/diagnostics/logging-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="895e3-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="contentionstart_v1-event"></a><span data-ttu-id="895e3-106">Событие ContentionStart_V1</span><span class="sxs-lookup"><span data-stu-id="895e3-106">ContentionStart_V1 event</span></span>

<span data-ttu-id="895e3-107">Это событие выдается в начале конфликта блокировки монитора.</span><span class="sxs-lookup"><span data-stu-id="895e3-107">This event is emitted at the start of a monitor lock contention.</span></span>

|<span data-ttu-id="895e3-108">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="895e3-108">Keyword for raising the event</span></span>|<span data-ttu-id="895e3-109">Level</span><span class="sxs-lookup"><span data-stu-id="895e3-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="895e3-110">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="895e3-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="895e3-111">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="895e3-111">Informational (4)</span></span>|

 <span data-ttu-id="895e3-112">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="895e3-112">The following table shows event information.</span></span>

|<span data-ttu-id="895e3-113">Событие</span><span class="sxs-lookup"><span data-stu-id="895e3-113">Event</span></span>|<span data-ttu-id="895e3-114">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="895e3-114">Event ID</span></span>|<span data-ttu-id="895e3-115">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="895e3-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="895e3-116">81</span><span class="sxs-lookup"><span data-stu-id="895e3-116">81</span></span>|<span data-ttu-id="895e3-117">Конфликт блокировки монитора начинается.</span><span class="sxs-lookup"><span data-stu-id="895e3-117">A monitor lock contention starts.</span></span>|

|<span data-ttu-id="895e3-118">Имя поля</span><span class="sxs-lookup"><span data-stu-id="895e3-118">Field name</span></span>|<span data-ttu-id="895e3-119">Тип данных</span><span class="sxs-lookup"><span data-stu-id="895e3-119">Data type</span></span>|<span data-ttu-id="895e3-120">Описание</span><span class="sxs-lookup"><span data-stu-id="895e3-120">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="895e3-121">`0` — управляемый; `1` — собственный.</span><span class="sxs-lookup"><span data-stu-id="895e3-121">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="895e3-122">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="895e3-122">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="contentionstop_v1-event"></a><span data-ttu-id="895e3-123">Событие ContentionStop_V1</span><span class="sxs-lookup"><span data-stu-id="895e3-123">ContentionStop_V1 event</span></span>

<span data-ttu-id="895e3-124">Это событие выдается в конце конфликта блокировки монитора.</span><span class="sxs-lookup"><span data-stu-id="895e3-124">This event is emitted at the end of a monitor lock contention.</span></span>

|<span data-ttu-id="895e3-125">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="895e3-125">Keyword for raising the event</span></span>|<span data-ttu-id="895e3-126">Level</span><span class="sxs-lookup"><span data-stu-id="895e3-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="895e3-127">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="895e3-127">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="895e3-128">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="895e3-128">Informational (4)</span></span>|

 <span data-ttu-id="895e3-129">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="895e3-129">The following table shows event information.</span></span>

|<span data-ttu-id="895e3-130">Событие</span><span class="sxs-lookup"><span data-stu-id="895e3-130">Event</span></span>|<span data-ttu-id="895e3-131">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="895e3-131">Event ID</span></span>|<span data-ttu-id="895e3-132">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="895e3-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStop_V1`|<span data-ttu-id="895e3-133">91</span><span class="sxs-lookup"><span data-stu-id="895e3-133">91</span></span>|<span data-ttu-id="895e3-134">Конфликт блокировки монитора завершается.</span><span class="sxs-lookup"><span data-stu-id="895e3-134">A monitor lock contention ends.</span></span>|

|<span data-ttu-id="895e3-135">Имя поля</span><span class="sxs-lookup"><span data-stu-id="895e3-135">Field name</span></span>|<span data-ttu-id="895e3-136">Тип данных</span><span class="sxs-lookup"><span data-stu-id="895e3-136">Data type</span></span>|<span data-ttu-id="895e3-137">Описание</span><span class="sxs-lookup"><span data-stu-id="895e3-137">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="895e3-138">`0` — управляемый; `1` — собственный.</span><span class="sxs-lookup"><span data-stu-id="895e3-138">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="895e3-139">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="895e3-139">Unique ID for the instance of CoreCLR.</span></span>|
|`DurationNs`|`win:Double`|<span data-ttu-id="895e3-140">Длительность конфликта в наносекундах.</span><span class="sxs-lookup"><span data-stu-id="895e3-140">Duration of the contention in nanoseconds.</span></span>|
