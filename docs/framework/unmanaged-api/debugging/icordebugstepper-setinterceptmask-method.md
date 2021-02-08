---
description: 'Дополнительные сведения о методе ICorDebugStepper:: Сетинтерцептмаск'
title: Метод ICorDebugStepper::SetInterceptMask
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: 33a42b154d063a29022034fd8061599a5e0e5503
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803551"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="c915b-103">Метод ICorDebugStepper::SetInterceptMask</span><span class="sxs-lookup"><span data-stu-id="c915b-103">ICorDebugStepper::SetInterceptMask Method</span></span>

<span data-ttu-id="c915b-104">Задает значение, указывающее типы кода, в который выполняется пошаговое выполнение.</span><span class="sxs-lookup"><span data-stu-id="c915b-104">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c915b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c915b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c915b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c915b-106">Parameters</span></span>  

 `mask`  
 <span data-ttu-id="c915b-107">окне Сочетание значений перечисления CorDebugIntercept, определяющих типы кода.</span><span class="sxs-lookup"><span data-stu-id="c915b-107">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c915b-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="c915b-108">Remarks</span></span>  

 <span data-ttu-id="c915b-109">Если задан бит для перехватчика, средство пошагового выполнения будет выполнено при обнаружении заданного типа перехвата кода.</span><span class="sxs-lookup"><span data-stu-id="c915b-109">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="c915b-110">Если бит сброшен, перехват кода будет пропущен.</span><span class="sxs-lookup"><span data-stu-id="c915b-110">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="c915b-111">`SetInterceptMask`Метод может иметь непредвиденные взаимодействия с [ICorDebugStepper:: сетунмаппедстопмаск](icordebugstepper-setunmappedstopmask-method.md) (от точки зрения пользователя).</span><span class="sxs-lookup"><span data-stu-id="c915b-111">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="c915b-112">Например, если единственная видимая (т. е. не внутренняя) часть кода инициализации класса не имеет сведений о сопоставлении и STOP_NO_MAPPING_INFO не задана (см. метод [ICorDebugStepper:: сетунмаппедстопмаск](icordebugstepper-setunmappedstopmask-method.md) и перечисление кордебугунмаппедстоп), средство организации пошаговое руководство будет пройдет инициализацию класса.</span><span class="sxs-lookup"><span data-stu-id="c915b-112">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="c915b-113">По умолчанию будет использоваться только значение INTERCEPT_NONE `CorDebugIntercept` перечисления.</span><span class="sxs-lookup"><span data-stu-id="c915b-113">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c915b-114">Требования</span><span class="sxs-lookup"><span data-stu-id="c915b-114">Requirements</span></span>  

 <span data-ttu-id="c915b-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c915b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c915b-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c915b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c915b-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c915b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c915b-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c915b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
