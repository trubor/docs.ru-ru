---
description: Дополнительные сведения о интерфейсе ICorDebugStepper
title: Интерфейс ICorDebugStepper
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
ms.openlocfilehash: a16df9d25b4d87b0638448c1fdf8fec4759261d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803598"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="1128c-103">Интерфейс ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="1128c-103">ICorDebugStepper Interface</span></span>

<span data-ttu-id="1128c-104">Представляет предпринимаемый отладчиком шаг при выполнении кода, служащий идентификатором на промежутке между подачей команды и ее завершением, а также предоставляет возможность отмены шага.</span><span class="sxs-lookup"><span data-stu-id="1128c-104">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1128c-105">Методы</span><span class="sxs-lookup"><span data-stu-id="1128c-105">Methods</span></span>  
  
|<span data-ttu-id="1128c-106">Метод</span><span class="sxs-lookup"><span data-stu-id="1128c-106">Method</span></span>|<span data-ttu-id="1128c-107">Описание</span><span class="sxs-lookup"><span data-stu-id="1128c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1128c-108">Метод Deactivate</span><span class="sxs-lookup"><span data-stu-id="1128c-108">Deactivate Method</span></span>](icordebugstepper-deactivate-method.md)|<span data-ttu-id="1128c-109">Приводит `ICorDebugStepper` к отмене полученной команды последнего шага.</span><span class="sxs-lookup"><span data-stu-id="1128c-109">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="1128c-110">Метод IsActive</span><span class="sxs-lookup"><span data-stu-id="1128c-110">IsActive Method</span></span>](icordebugstepper-isactive-method.md)|<span data-ttu-id="1128c-111">Возвращает значение, указывающее, выполняется ли `ICorDebugStepper` в данный момент шаг.</span><span class="sxs-lookup"><span data-stu-id="1128c-111">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="1128c-112">Метод SetInterceptMask</span><span class="sxs-lookup"><span data-stu-id="1128c-112">SetInterceptMask Method</span></span>](icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="1128c-113">Задает значение CorDebugIntercept, указывающее типы кода, в который выполняется пошаговое выполнение.</span><span class="sxs-lookup"><span data-stu-id="1128c-113">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="1128c-114">Метод SetRangeIL</span><span class="sxs-lookup"><span data-stu-id="1128c-114">SetRangeIL Method</span></span>](icordebugstepper-setrangeil-method.md)|<span data-ttu-id="1128c-115">Задает значение, указывающее, должны ли вызовы метода [ICorDebugStepper:: степранже](icordebugstepper-steprange-method.md) передавать значения аргументов, относящихся к машинному коду или коду кода на языке MSIL, который проходит через шаг.</span><span class="sxs-lookup"><span data-stu-id="1128c-115">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="1128c-116">Метод SetUnmappedStopMask</span><span class="sxs-lookup"><span data-stu-id="1128c-116">SetUnmappedStopMask Method</span></span>](icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="1128c-117">Задает значение Кордебугунмаппедстоп, указывающее тип несопоставленного кода, в котором выполнение будет остановлено.</span><span class="sxs-lookup"><span data-stu-id="1128c-117">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="1128c-118">Метод Step</span><span class="sxs-lookup"><span data-stu-id="1128c-118">Step Method</span></span>](icordebugstepper-step-method.md)|<span data-ttu-id="1128c-119">Приводит `ICorDebugStepper` к пошаговому вызову содержащего его потока и, при необходимости, для продолжения единого пошагового выполнения функций, которые вызываются в потоке.</span><span class="sxs-lookup"><span data-stu-id="1128c-119">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="1128c-120">Метод StepOut</span><span class="sxs-lookup"><span data-stu-id="1128c-120">StepOut Method</span></span>](icordebugstepper-stepout-method.md)|<span data-ttu-id="1128c-121">Приводит `ICorDebugStepper` к пошаговому вызову содержащего его потока и выполнению, когда текущий кадр возвращает управление вызывающему кадру.</span><span class="sxs-lookup"><span data-stu-id="1128c-121">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="1128c-122">Метод StepRange</span><span class="sxs-lookup"><span data-stu-id="1128c-122">StepRange Method</span></span>](icordebugstepper-steprange-method.md)|<span data-ttu-id="1128c-123">Приводит `ICorDebugStepper` к пошаговому вызову содержащего его потока и возврату при достижении кода, находящегося за последним из указанных диапазонов.</span><span class="sxs-lookup"><span data-stu-id="1128c-123">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1128c-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="1128c-124">Remarks</span></span>  

 <span data-ttu-id="1128c-125">`ICorDebugStepper`Интерфейс выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="1128c-125">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
- <span data-ttu-id="1128c-126">Он выступает в качестве идентификатора между выдаваемыми командой Step и завершением этой команды.</span><span class="sxs-lookup"><span data-stu-id="1128c-126">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
- <span data-ttu-id="1128c-127">Он предоставляет центральный интерфейс для инкапсуляции всех шагов, которые можно выполнить.</span><span class="sxs-lookup"><span data-stu-id="1128c-127">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
- <span data-ttu-id="1128c-128">Он позволяет преждевременно отменить операцию пошагового выполнения.</span><span class="sxs-lookup"><span data-stu-id="1128c-128">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="1128c-129">Для каждого потока может существовать несколько шагов.</span><span class="sxs-lookup"><span data-stu-id="1128c-129">There can be more than one stepper per thread.</span></span> <span data-ttu-id="1128c-130">Например, при пошаговом выполнении функции может быть достигнута точка останова, и пользователю может потребоваться начать новую операцию пошагового выполнения внутри этой функции.</span><span class="sxs-lookup"><span data-stu-id="1128c-130">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="1128c-131">Для определения способа решения этой проблемы отладчику необходимо присвоить значение.</span><span class="sxs-lookup"><span data-stu-id="1128c-131">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="1128c-132">Отладчик может захотеть отменить исходную операцию пошагового выполнения или вложить две операции.</span><span class="sxs-lookup"><span data-stu-id="1128c-132">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="1128c-133">`ICorDebugStepper`Интерфейс поддерживает оба варианта.</span><span class="sxs-lookup"><span data-stu-id="1128c-133">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="1128c-134">Средство организации пошагового выполнения может переноситься между потоками, если среда CLR выполняет перекрестный потоковый вызов.</span><span class="sxs-lookup"><span data-stu-id="1128c-134">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1128c-135">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="1128c-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1128c-136">Требования</span><span class="sxs-lookup"><span data-stu-id="1128c-136">Requirements</span></span>  

 <span data-ttu-id="1128c-137">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1128c-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1128c-138">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1128c-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1128c-139">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1128c-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1128c-140">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1128c-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1128c-141">См. также</span><span class="sxs-lookup"><span data-stu-id="1128c-141">See also</span></span>

- [<span data-ttu-id="1128c-142">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="1128c-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
