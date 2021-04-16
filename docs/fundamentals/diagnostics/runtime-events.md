---
title: События среды выполнения
description: Проверьте события диагностики, созданные средой выполнения .NET (CoreCLR), которые могут использоваться с ETW, LTTng или EventPipe.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- runtime events (CoreCLR)
- ETW, EventPipe runtime events (CoreCLR)
ms.openlocfilehash: 33fa7275ce40934ce043b4d0dba5749c37515755
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594050"
---
# <a name="net-runtime-events"></a><span data-ttu-id="084bb-103">События среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="084bb-103">.NET runtime events</span></span>

<span data-ttu-id="084bb-104">Среда выполнения .NET (CoreCLR) выдает различные события, которые можно использовать для диагностики проблем с приложением .NET, посредством различных механизмов, таких как `ETW`, `LTTng` и `EventPipe`.</span><span class="sxs-lookup"><span data-stu-id="084bb-104">The .NET runtime (CoreCLR) emits various events that can be used to diagnose issues with your .NET application that can be consumed via various mechanisms such as `ETW`, `LTTng`, and `EventPipe`.</span></span>

<span data-ttu-id="084bb-105">Этот документ служит ссылкой на события, запускаемые средой выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="084bb-105">This document serves as a reference on the events that are fired by .NET Core runtime.</span></span>

<span data-ttu-id="084bb-106">Сведения о событиях среды выполнения в платформе .NET Framework см. в разделе [События трассировки событий Windows среды CLR](../../framework/performance/clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="084bb-106">For runtime events in .NET Framework, see [CLR ETW Events](../../framework/performance/clr-etw-events.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="084bb-107">Содержание раздела</span><span class="sxs-lookup"><span data-stu-id="084bb-107">In this section</span></span>

<span data-ttu-id="084bb-108">[События конфликтов](runtime-contention-events.md)</span><span class="sxs-lookup"><span data-stu-id="084bb-108">[Contention Events](runtime-contention-events.md)</span></span>\
<span data-ttu-id="084bb-109">Эти события собирают сведения о конфликтах блокировки монитора.</span><span class="sxs-lookup"><span data-stu-id="084bb-109">These events collect information about monitor lock contentions.</span></span>

<span data-ttu-id="084bb-110">[События сборки мусора](runtime-garbage-collection-events.md)</span><span class="sxs-lookup"><span data-stu-id="084bb-110">[Garbage Collection Events](runtime-garbage-collection-events.md)</span></span>\
<span data-ttu-id="084bb-111">Эти события собирают сведения, относящиеся к сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="084bb-111">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="084bb-112">Они помогают при диагностике и отладке, в том числе позволяют определить, сколько раз осуществлялась сборка мусора, какой объем памяти был освобожден в ходе сборки мусора и т. д.</span><span class="sxs-lookup"><span data-stu-id="084bb-112">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc.</span></span>

<span data-ttu-id="084bb-113">[События исключений](runtime-exception-events.md)</span><span class="sxs-lookup"><span data-stu-id="084bb-113">[Exception Events](runtime-exception-events.md)</span></span>\
<span data-ttu-id="084bb-114">Эти события среды выполнения собирают сведения о возникших исключениях.</span><span class="sxs-lookup"><span data-stu-id="084bb-114">These runtime events capture information about exceptions that are thrown.</span></span>

<span data-ttu-id="084bb-115">[События взаимодействия](runtime-interop-events.md)</span><span class="sxs-lookup"><span data-stu-id="084bb-115">[Interop Events](runtime-interop-events.md)</span></span>\
<span data-ttu-id="084bb-116">Эти события среды выполнения собирают сведения о создании заглушки CIL.</span><span class="sxs-lookup"><span data-stu-id="084bb-116">These runtime events capture information about Common Intermediate Language (CIL) stub generation.</span></span>

<span data-ttu-id="084bb-117">[События загрузчика и модуля привязки](runtime-loader-binder-events.md)</span><span class="sxs-lookup"><span data-stu-id="084bb-117">[Loader and Binder Events](runtime-loader-binder-events.md)</span></span>\
<span data-ttu-id="084bb-118">Эти события собирают информацию, относящуюся к загрузке и выгрузке сборок и модулей.</span><span class="sxs-lookup"><span data-stu-id="084bb-118">These events collect information relating to loading and unloading assemblies and modules.</span></span>

<span data-ttu-id="084bb-119">[События методов](runtime-method-events.md)</span><span class="sxs-lookup"><span data-stu-id="084bb-119">[Method Events](runtime-method-events.md)</span></span>\
<span data-ttu-id="084bb-120">Эти события собирают сведения, связанные с методами.</span><span class="sxs-lookup"><span data-stu-id="084bb-120">These events collect information that is specific to methods.</span></span> <span data-ttu-id="084bb-121">Полезные данные этих событий необходимы для разрешения символов.</span><span class="sxs-lookup"><span data-stu-id="084bb-121">The payload of these events is required for symbol resolution.</span></span> <span data-ttu-id="084bb-122">Кроме того, эти события содержат полезные сведения, например сколько раз вызывался метод.</span><span class="sxs-lookup"><span data-stu-id="084bb-122">In addition, these events provide helpful information such as the number of times a method was called.</span></span>

<span data-ttu-id="084bb-123">[События потоков](runtime-thread-events.md)</span><span class="sxs-lookup"><span data-stu-id="084bb-123">[Thread Events](runtime-thread-events.md)</span></span>\
<span data-ttu-id="084bb-124">Эти события собирают сведения о рабочих потоках и потоках ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="084bb-124">These events collect information about worker and I/O threads.</span></span>

<span data-ttu-id="084bb-125">[События типов](runtime-type-events.md)</span><span class="sxs-lookup"><span data-stu-id="084bb-125">[Type Events](runtime-type-events.md)</span></span>\
<span data-ttu-id="084bb-126">Эти события собирают сведения о системе типов.</span><span class="sxs-lookup"><span data-stu-id="084bb-126">These events collect information about the type system.</span></span>
