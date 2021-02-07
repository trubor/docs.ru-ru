---
description: 'Дополнительные сведения о методе ICorDebugStepper:: Step'
title: Метод ICorDebugStepper::Step
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
ms.openlocfilehash: cb45575f7818784addf67eacda35442764e706af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717632"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="92bda-103">Метод ICorDebugStepper::Step</span><span class="sxs-lookup"><span data-stu-id="92bda-103">ICorDebugStepper::Step Method</span></span>

<span data-ttu-id="92bda-104">Приводит к тому, что данный ICorDebugStepper пошаговым путем через содержащий его поток, и, при необходимости, для продолжения пошагового выполнения функций, которые вызываются в потоке.</span><span class="sxs-lookup"><span data-stu-id="92bda-104">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92bda-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="92bda-105">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92bda-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="92bda-106">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="92bda-107">окне Задайте для значение, чтобы `true` выполнить шаг с заходом в функцию, которая вызывается в потоке.</span><span class="sxs-lookup"><span data-stu-id="92bda-107">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="92bda-108">Задайте для значение `false` , чтобы выполнить шаг с обходом функции.</span><span class="sxs-lookup"><span data-stu-id="92bda-108">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92bda-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="92bda-109">Remarks</span></span>  

 <span data-ttu-id="92bda-110">Шаг завершается, когда среда CLR выполняет следующую управляемую инструкцию в кадре этого средства.</span><span class="sxs-lookup"><span data-stu-id="92bda-110">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="92bda-111">Если `Step` метод вызывается в пошаговом процессе, который не находится в управляемом коде, шаг будет выполнен, когда поток выполняет следующую инструкцию управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="92bda-111">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92bda-112">Требования</span><span class="sxs-lookup"><span data-stu-id="92bda-112">Requirements</span></span>  

 <span data-ttu-id="92bda-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92bda-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92bda-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92bda-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92bda-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92bda-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92bda-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92bda-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
