---
title: События времени выполнения
description: Проверьте события диагностики, созданные средой выполнения .NET (CoreCLR), которые могут использоваться с ETW, LTTng или Евентпипе.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- runtime events (CoreCLR)
- ETW, EventPipe runtime events (CoreCLR)
ms.openlocfilehash: 33fa7275ce40934ce043b4d0dba5749c37515755
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594050"
---
# <a name="net-runtime-events"></a><span data-ttu-id="7951b-103">События среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="7951b-103">.NET runtime events</span></span>

<span data-ttu-id="7951b-104">Среда выполнения .NET (CoreCLR) выдает различные события, которые могут использоваться для диагностики проблем с приложением .NET, которые можно использовать с помощью различных механизмов, таких как `ETW` , `LTTng` и `EventPipe` .</span><span class="sxs-lookup"><span data-stu-id="7951b-104">The .NET runtime (CoreCLR) emits various events that can be used to diagnose issues with your .NET application that can be consumed via various mechanisms such as `ETW`, `LTTng`, and `EventPipe`.</span></span>

<span data-ttu-id="7951b-105">Этот документ служит ссылкой на события, запускаемые средой выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7951b-105">This document serves as a reference on the events that are fired by .NET Core runtime.</span></span>

<span data-ttu-id="7951b-106">Сведения о событиях времени выполнения в .NET Framework см. в разделе [события ETW среды CLR](../../framework/performance/clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="7951b-106">For runtime events in .NET Framework, see [CLR ETW Events](../../framework/performance/clr-etw-events.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7951b-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="7951b-107">In this section</span></span>

<span data-ttu-id="7951b-108">[События состязания](runtime-contention-events.md)</span><span class="sxs-lookup"><span data-stu-id="7951b-108">[Contention Events](runtime-contention-events.md)</span></span>\
<span data-ttu-id="7951b-109">Эти события собираются сведения о конфликтах блокировки монитора.</span><span class="sxs-lookup"><span data-stu-id="7951b-109">These events collect information about monitor lock contentions.</span></span>

<span data-ttu-id="7951b-110">[События сборки мусора](runtime-garbage-collection-events.md)</span><span class="sxs-lookup"><span data-stu-id="7951b-110">[Garbage Collection Events](runtime-garbage-collection-events.md)</span></span>\
<span data-ttu-id="7951b-111">Эти события собирают сведения, относящиеся к сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="7951b-111">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="7951b-112">Они помогают в диагностике и отладке, включая определение того, сколько раз выполнялась сборка мусора, сколько памяти было освобождено во время сборки мусора и т. д.</span><span class="sxs-lookup"><span data-stu-id="7951b-112">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc.</span></span>

<span data-ttu-id="7951b-113">[События исключений](runtime-exception-events.md)</span><span class="sxs-lookup"><span data-stu-id="7951b-113">[Exception Events](runtime-exception-events.md)</span></span>\
<span data-ttu-id="7951b-114">Эти события времени выполнения захватывают сведения о возникших исключениях.</span><span class="sxs-lookup"><span data-stu-id="7951b-114">These runtime events capture information about exceptions that are thrown.</span></span>

<span data-ttu-id="7951b-115">[События взаимодействия](runtime-interop-events.md)</span><span class="sxs-lookup"><span data-stu-id="7951b-115">[Interop Events](runtime-interop-events.md)</span></span>\
<span data-ttu-id="7951b-116">Эти события времени выполнения захватывают сведения о создании заглушек на стандартном промежуточном языке (CIL).</span><span class="sxs-lookup"><span data-stu-id="7951b-116">These runtime events capture information about Common Intermediate Language (CIL) stub generation.</span></span>

<span data-ttu-id="7951b-117">[События загрузчика и связывателя](runtime-loader-binder-events.md)</span><span class="sxs-lookup"><span data-stu-id="7951b-117">[Loader and Binder Events](runtime-loader-binder-events.md)</span></span>\
<span data-ttu-id="7951b-118">Эти события собираются сведения, связанные с загрузкой и выгрузкой сборок и модулей.</span><span class="sxs-lookup"><span data-stu-id="7951b-118">These events collect information relating to loading and unloading assemblies and modules.</span></span>

<span data-ttu-id="7951b-119">[События методов](runtime-method-events.md)</span><span class="sxs-lookup"><span data-stu-id="7951b-119">[Method Events](runtime-method-events.md)</span></span>\
<span data-ttu-id="7951b-120">Эти события собирают сведения, связанные с методами.</span><span class="sxs-lookup"><span data-stu-id="7951b-120">These events collect information that is specific to methods.</span></span> <span data-ttu-id="7951b-121">Полезные данные этих событий необходимы для разрешения символов.</span><span class="sxs-lookup"><span data-stu-id="7951b-121">The payload of these events is required for symbol resolution.</span></span> <span data-ttu-id="7951b-122">Кроме того, эти события содержат полезные сведения, например сколько раз вызывался метод.</span><span class="sxs-lookup"><span data-stu-id="7951b-122">In addition, these events provide helpful information such as the number of times a method was called.</span></span>

<span data-ttu-id="7951b-123">[События потока](runtime-thread-events.md)</span><span class="sxs-lookup"><span data-stu-id="7951b-123">[Thread Events](runtime-thread-events.md)</span></span>\
<span data-ttu-id="7951b-124">Эти события собирают сведения о рабочих потоках и потоках ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="7951b-124">These events collect information about worker and I/O threads.</span></span>

<span data-ttu-id="7951b-125">[События типа](runtime-type-events.md)</span><span class="sxs-lookup"><span data-stu-id="7951b-125">[Type Events](runtime-type-events.md)</span></span>\
<span data-ttu-id="7951b-126">Эти события собираются сведения о системе типов.</span><span class="sxs-lookup"><span data-stu-id="7951b-126">These events collect information about the type system.</span></span>
