---
description: 'Дополнительные сведения о методе ICorDebugStepper:: Steping.'
title: Метод ICorDebugStepper::StepOut
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: ef404c928ab711aef8032655a02cbd917416e806
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717619"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="c68e2-103">Метод ICorDebugStepper::StepOut</span><span class="sxs-lookup"><span data-stu-id="c68e2-103">ICorDebugStepper::StepOut Method</span></span>

<span data-ttu-id="c68e2-104">Приводит к тому, что данный ICorDebugStepper пошаговым путем через содержащий его поток и завершается, когда текущий кадр возвращает управление вызывающему кадру.</span><span class="sxs-lookup"><span data-stu-id="c68e2-104">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c68e2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c68e2-105">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c68e2-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="c68e2-106">Remarks</span></span>  

 <span data-ttu-id="c68e2-107">`StepOut`Операция будет завершена после возврата в обычном режиме из текущего кадра в вызывающий кадр.</span><span class="sxs-lookup"><span data-stu-id="c68e2-107">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="c68e2-108">Если `StepOut` вызывается в неуправляемом коде, этот шаг завершается, когда текущий кадр возвращается в управляемый код, вызвавший его.</span><span class="sxs-lookup"><span data-stu-id="c68e2-108">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="c68e2-109">В платформа .NET Framework версии 2,0 не используйте `StepOut` с установленным флагом STOP_UNMANAGED, так как он завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="c68e2-109">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="c68e2-110">(Используйте [ICorDebugStepper:: сетунмаппедстопмаск](icordebugstepper-setunmappedstopmask-method.md) для установки флагов для пошагового выполнения.) Отладчики взаимодействия должны выполнять шаг с заходом в собственный код.</span><span class="sxs-lookup"><span data-stu-id="c68e2-110">(Use [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c68e2-111">Требования</span><span class="sxs-lookup"><span data-stu-id="c68e2-111">Requirements</span></span>  

 <span data-ttu-id="c68e2-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c68e2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c68e2-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c68e2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c68e2-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c68e2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c68e2-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c68e2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
