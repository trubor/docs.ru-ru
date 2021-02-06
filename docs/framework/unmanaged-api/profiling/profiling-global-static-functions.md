---
description: 'Дополнительные сведения: профилирование глобальных статических функций'
title: Глобальные статические функции профилирования
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 86e4b6bda73b0783f5f95e4e7dbc24f1ccccb130
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646378"
---
# <a name="profiling-global-static-functions"></a><span data-ttu-id="a0ea4-103">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="a0ea4-103">Profiling Global Static Functions</span></span>

<span data-ttu-id="a0ea4-104">В этом разделе описываются неуправляемые функции API, используемые API профилирования.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-104">This section describes the unmanaged API functions that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0ea4-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="a0ea4-105">In This Section</span></span>  
  
## <a name="net-framework-version-1-profiling-functions"></a><span data-ttu-id="a0ea4-106">Платформа .NET Framework функции профилирования версии 1</span><span class="sxs-lookup"><span data-stu-id="a0ea4-106">.NET Framework version 1 Profiling Functions</span></span>  

 [<span data-ttu-id="a0ea4-107">Функция FunctionEnter</span><span class="sxs-lookup"><span data-stu-id="a0ea4-107">FunctionEnter Function</span></span>](functionenter-function.md)  
 <span data-ttu-id="a0ea4-108">Уведомляет профилировщик о передаче управления в функцию.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-108">Notifies the profiler that control is being passed to a function.</span></span> <span data-ttu-id="a0ea4-109">Не рекомендуется использовать в платформа .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-109">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="a0ea4-110">Функция FunctionLeave</span><span class="sxs-lookup"><span data-stu-id="a0ea4-110">FunctionLeave Function</span></span>](functionleave-function.md)  
 <span data-ttu-id="a0ea4-111">Уведомляет профилировщик о том, что функция собирается вернуть вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-111">Notifies the profiler that a function is about to return to the caller.</span></span> <span data-ttu-id="a0ea4-112">Не рекомендуется использовать в платформа .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-112">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="a0ea4-113">Функция FunctionTailcall</span><span class="sxs-lookup"><span data-stu-id="a0ea4-113">FunctionTailcall Function</span></span>](functiontailcall-function.md)  
 <span data-ttu-id="a0ea4-114">Уведомляет профилировщик о том, что выполняемая в данный момент функция собирается выполнить вызов другой функции с префиксом tail.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-114">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span> <span data-ttu-id="a0ea4-115">Не рекомендуется использовать в платформа .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-115">Deprecated in the .NET Framework 2.0.</span></span>  
  
## <a name="net-framework-version-2-profiling-functions"></a><span data-ttu-id="a0ea4-116">Функции профилирования платформа .NET Framework версии 2</span><span class="sxs-lookup"><span data-stu-id="a0ea4-116">.NET Framework version 2 Profiling Functions</span></span>  

 [<span data-ttu-id="a0ea4-117">Функция FunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="a0ea4-117">FunctionIDMapper Function</span></span>](functionidmapper-function.md)  
 <span data-ttu-id="a0ea4-118">Уведомляет профилировщик о том, что заданный идентификатор функции может быть повторно сопоставлен с альтернативным ИДЕНТИФИКАТОРом для использования в обратных вызовах [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)и [FunctionTailcall2](functiontailcall2-function.md) для этой функции.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-118">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="a0ea4-119">Также позволяет профилировщику указать, требуется ли получать обратные вызовы для этой функции.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-119">Also enables the profiler to indicate whether it wants to receive callbacks for that function</span></span>  
  
 [<span data-ttu-id="a0ea4-120">Функция FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="a0ea4-120">FunctionEnter2 Function</span></span>](functionenter2-function.md)  
 <span data-ttu-id="a0ea4-121">Уведомляет профилировщик о передаче управления в функцию и предоставляет сведения о кадре стека и аргументах функции.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-121">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="a0ea4-122">Не рекомендуется использовать в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-122">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a0ea4-123">Функция FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="a0ea4-123">FunctionLeave2 Function</span></span>](functionleave2-function.md)  
 <span data-ttu-id="a0ea4-124">Уведомляет профилировщик о том, что функция собирается вернуться к вызывающему объекту, и предоставляет сведения о кадре стека и возвращаемом значении функции.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-124">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span> <span data-ttu-id="a0ea4-125">Не рекомендуется использовать в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-125">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a0ea4-126">Функция FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="a0ea4-126">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)  
 <span data-ttu-id="a0ea4-127">Уведомляет профилировщик о том, что выполняемая в данный момент функция собирается выполнить вызов другой функции с префиксом tail и предоставляет сведения о кадре стека.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-127">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span> <span data-ttu-id="a0ea4-128">Не рекомендуется использовать в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-128">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a0ea4-129">Функция StackSnapshotCallback</span><span class="sxs-lookup"><span data-stu-id="a0ea4-129">StackSnapshotCallback Function</span></span>](stacksnapshotcallback-function.md)  
 <span data-ttu-id="a0ea4-130">Предоставляет профилировщику сведения о каждом управляемом кадре и каждом запуске неуправляемых кадров в стеке во время прохода стека, который инициируется методом [ICorProfilerInfo2::D остаккснапшот](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a0ea4-130">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="net-framework-version-4-profiling-functions"></a><span data-ttu-id="a0ea4-131">Функции профилирования платформа .NET Framework версии 4</span><span class="sxs-lookup"><span data-stu-id="a0ea4-131">.NET Framework version 4 Profiling Functions</span></span>  

 [<span data-ttu-id="a0ea4-132">Функция FunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="a0ea4-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)  
 <span data-ttu-id="a0ea4-133">Уведомляет профилировщик о том, что заданный идентификатор функции может быть повторно сопоставлен с альтернативным ИДЕНТИФИКАТОРом для использования в ответных вызовах [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), [FunctionTailcall3](functiontailcall3-function.md)или[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)и [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) для этой функции.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-133">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="a0ea4-134">Также позволяет профилировщику указывать, хотят ли они получать обратные вызовы для этой функции.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-134">Also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
 <span data-ttu-id="a0ea4-135">`FunctionIDMapper2` расширяет функцию [FunctionIDMapper](functionidmapper-function.md) с помощью `clientData` параметра, который профилировщики могут использовать для устранения неоднозначности между средами выполнения.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-135">`FunctionIDMapper2` extends the [FunctionIDMapper](functionidmapper-function.md) function with a `clientData` parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
 [<span data-ttu-id="a0ea4-136">Функция FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="a0ea4-136">FunctionEnter3 Function</span></span>](functionenter3-function.md)  
 <span data-ttu-id="a0ea4-137">Уведомляет профилировщик о передаче управления в функцию.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-137">Notifies the profiler that control is being passed to a function.</span></span>  
  
 [<span data-ttu-id="a0ea4-138">Функция FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a0ea4-138">FunctionEnter3WithInfo Function</span></span>](functionenter3withinfo-function.md)  
 <span data-ttu-id="a0ea4-139">Уведомляет профилировщик о передаче управления в функцию и предоставляет маркер, который можно передать в [ICorProfilerInfo3:: GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) для получения кадра стека и аргументов функции.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-139">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
 [<span data-ttu-id="a0ea4-140">Функция FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="a0ea4-140">FunctionLeave3 Function</span></span>](functionleave3-function.md)  
 <span data-ttu-id="a0ea4-141">Уведомляет профилировщик о том, что управление возвращается из функции.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-141">Notifies the profiler that control is being returned from a function.</span></span>  
  
 [<span data-ttu-id="a0ea4-142">Функция FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a0ea4-142">FunctionLeave3WithInfo Function</span></span>](functionleave3withinfo-function.md)  
 <span data-ttu-id="a0ea4-143">Уведомляет профилировщик о том, что управление возвращается из функции, и предоставляет маркер, который можно передать в [ICorProfilerInfo3:: GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) для получения кадра стека и возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-143">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
 [<span data-ttu-id="a0ea4-144">Функция FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="a0ea4-144">FunctionTailcall3 Function</span></span>](functiontailcall3-function.md)  
 <span data-ttu-id="a0ea4-145">Уведомляет профилировщик о том, что выполняемая в данный момент функция собирается выполнить вызов другой функции с префиксом tail.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-145">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
 [<span data-ttu-id="a0ea4-146">Функция FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a0ea4-146">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)  
 <span data-ttu-id="a0ea4-147">Уведомляет профилировщик о том, что выполняемая в данный момент функция собирается выполнить вызов другой функции с префиксом tail, и предоставляет маркер, который можно передать в [ICorProfilerInfo3:: GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) для получения кадра стека.</span><span class="sxs-lookup"><span data-stu-id="a0ea4-147">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a0ea4-148">См. также</span><span class="sxs-lookup"><span data-stu-id="a0ea4-148">Related Sections</span></span>  

 [<span data-ttu-id="a0ea4-149">Общие сведения о профилировании</span><span class="sxs-lookup"><span data-stu-id="a0ea4-149">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="a0ea4-150">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="a0ea4-150">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="a0ea4-151">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="a0ea4-151">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="a0ea4-152">Структуры профилирования</span><span class="sxs-lookup"><span data-stu-id="a0ea4-152">Profiling Structures</span></span>](profiling-structures.md)
