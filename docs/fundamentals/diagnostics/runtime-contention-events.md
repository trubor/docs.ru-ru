---
title: Отслеживание событий времени выполнения конфликтов блокировки
description: См. события ETW, собирающие сведения, относящиеся к конфликтам блокировки монитора.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- monitor lock contention events (CoreCLR)
- ETW, EventPipe, LTTng contention events (CoreCLR)
ms.openlocfilehash: 38e5f493d4b223b4839dbd6f814cf656722189b2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594053"
---
# <a name="net-runtime-contention-events"></a><span data-ttu-id="563c2-103">События состязания времени выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="563c2-103">.NET runtime contention events</span></span>

<span data-ttu-id="563c2-104">Эти события времени выполнения захватывают сведения о конфликтах блокировки монитора, таких как WITH `Monitor.Enter` или ключевое слово C# lock.</span><span class="sxs-lookup"><span data-stu-id="563c2-104">These runtime events capture information about monitor lock contentions such as with `Monitor.Enter` or the C# lock keyword.</span></span> <span data-ttu-id="563c2-105">Дополнительные сведения об использовании этих событий в целях диагностики см. в разделе [ведение журнала и трассировка приложений .NET](../../core/diagnostics/logging-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="563c2-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="contentionstart_v1-event"></a><span data-ttu-id="563c2-106">ContentionStart_V1 событие</span><span class="sxs-lookup"><span data-stu-id="563c2-106">ContentionStart_V1 event</span></span>

<span data-ttu-id="563c2-107">Это событие создается в начале конфликта блокировки монитора.</span><span class="sxs-lookup"><span data-stu-id="563c2-107">This event is emitted at the start of a monitor lock contention.</span></span>

|<span data-ttu-id="563c2-108">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="563c2-108">Keyword for raising the event</span></span>|<span data-ttu-id="563c2-109">Level</span><span class="sxs-lookup"><span data-stu-id="563c2-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="563c2-110">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="563c2-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="563c2-111">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="563c2-111">Informational (4)</span></span>|

 <span data-ttu-id="563c2-112">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="563c2-112">The following table shows event information.</span></span>

|<span data-ttu-id="563c2-113">Событие</span><span class="sxs-lookup"><span data-stu-id="563c2-113">Event</span></span>|<span data-ttu-id="563c2-114">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="563c2-114">Event ID</span></span>|<span data-ttu-id="563c2-115">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="563c2-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="563c2-116">81</span><span class="sxs-lookup"><span data-stu-id="563c2-116">81</span></span>|<span data-ttu-id="563c2-117">Начинается состязание за блокировки монитора.</span><span class="sxs-lookup"><span data-stu-id="563c2-117">A monitor lock contention starts.</span></span>|

|<span data-ttu-id="563c2-118">Имя поля</span><span class="sxs-lookup"><span data-stu-id="563c2-118">Field name</span></span>|<span data-ttu-id="563c2-119">Тип данных</span><span class="sxs-lookup"><span data-stu-id="563c2-119">Data type</span></span>|<span data-ttu-id="563c2-120">Описание</span><span class="sxs-lookup"><span data-stu-id="563c2-120">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="563c2-121">`0` для управляемого; `1` для машинного кода.</span><span class="sxs-lookup"><span data-stu-id="563c2-121">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="563c2-122">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="563c2-122">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="contentionstop_v1-event"></a><span data-ttu-id="563c2-123">ContentionStop_V1 событие</span><span class="sxs-lookup"><span data-stu-id="563c2-123">ContentionStop_V1 event</span></span>

<span data-ttu-id="563c2-124">Это событие создается в конце конфликта блокировки монитора.</span><span class="sxs-lookup"><span data-stu-id="563c2-124">This event is emitted at the end of a monitor lock contention.</span></span>

|<span data-ttu-id="563c2-125">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="563c2-125">Keyword for raising the event</span></span>|<span data-ttu-id="563c2-126">Level</span><span class="sxs-lookup"><span data-stu-id="563c2-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="563c2-127">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="563c2-127">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="563c2-128">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="563c2-128">Informational (4)</span></span>|

 <span data-ttu-id="563c2-129">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="563c2-129">The following table shows event information.</span></span>

|<span data-ttu-id="563c2-130">Событие</span><span class="sxs-lookup"><span data-stu-id="563c2-130">Event</span></span>|<span data-ttu-id="563c2-131">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="563c2-131">Event ID</span></span>|<span data-ttu-id="563c2-132">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="563c2-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStop_V1`|<span data-ttu-id="563c2-133">91</span><span class="sxs-lookup"><span data-stu-id="563c2-133">91</span></span>|<span data-ttu-id="563c2-134">Завершено состязание за блокировку монитора.</span><span class="sxs-lookup"><span data-stu-id="563c2-134">A monitor lock contention ends.</span></span>|

|<span data-ttu-id="563c2-135">Имя поля</span><span class="sxs-lookup"><span data-stu-id="563c2-135">Field name</span></span>|<span data-ttu-id="563c2-136">Тип данных</span><span class="sxs-lookup"><span data-stu-id="563c2-136">Data type</span></span>|<span data-ttu-id="563c2-137">Описание</span><span class="sxs-lookup"><span data-stu-id="563c2-137">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="563c2-138">`0` для управляемого; `1` для машинного кода.</span><span class="sxs-lookup"><span data-stu-id="563c2-138">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="563c2-139">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="563c2-139">Unique ID for the instance of CoreCLR.</span></span>|
|`DurationNs`|`win:Double`|<span data-ttu-id="563c2-140">Длительность состязания в наносекундах.</span><span class="sxs-lookup"><span data-stu-id="563c2-140">Duration of the contention in nanoseconds.</span></span>|
