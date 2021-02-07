---
description: 'Дополнительные сведения о методе ICorDebugStepper:: Степранже'
title: Метод ICorDebugStepper::StepRange
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
ms.openlocfilehash: 868925ef301cca15b7887505e879f5fff02002e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717586"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="ebd43-103">Метод ICorDebugStepper::StepRange</span><span class="sxs-lookup"><span data-stu-id="ebd43-103">ICorDebugStepper::StepRange Method</span></span>

<span data-ttu-id="ebd43-104">Приводит к тому, что данный ICorDebugStepper пошаговым путем через содержащий его поток и возвращает, когда он достигает кода, находящегося за последним из указанных диапазонов.</span><span class="sxs-lookup"><span data-stu-id="ebd43-104">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebd43-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ebd43-105">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebd43-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ebd43-106">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="ebd43-107">окне Задайте для значение, чтобы `true` выполнить шаг с заходом в функцию, которая вызывается в потоке.</span><span class="sxs-lookup"><span data-stu-id="ebd43-107">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="ebd43-108">Задайте для значение `false` , чтобы выполнить шаг с обходом функции.</span><span class="sxs-lookup"><span data-stu-id="ebd43-108">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="ebd43-109">окне Массив структур COR_DEBUG_STEP_RANGE, каждый из которых задает диапазон.</span><span class="sxs-lookup"><span data-stu-id="ebd43-109">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="ebd43-110">[in] Размер массива `ranges`.</span><span class="sxs-lookup"><span data-stu-id="ebd43-110">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebd43-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="ebd43-111">Remarks</span></span>  

 <span data-ttu-id="ebd43-112">`StepRange`Метод работает так же, как метод [ICorDebugStepper:: Step](icordebugstepper-step-method.md) , за исключением того, что он не завершается до достижения кода за пределами заданного диапазона.</span><span class="sxs-lookup"><span data-stu-id="ebd43-112">The `StepRange` method works like the [ICorDebugStepper::Step](icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="ebd43-113">Это может быть более эффективным, чем шаг с заходом по одной инструкции за раз.</span><span class="sxs-lookup"><span data-stu-id="ebd43-113">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="ebd43-114">Диапазоны задаются в виде списка пар смещений от начала кадра средства Организации.</span><span class="sxs-lookup"><span data-stu-id="ebd43-114">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="ebd43-115">Диапазоны задаются относительно кода промежуточного языка MSIL метода.</span><span class="sxs-lookup"><span data-stu-id="ebd43-115">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="ebd43-116">Вызовите [ICorDebugStepper:: SetRangeIL](icordebugstepper-setrangeil-method.md) с, `false` чтобы сделать диапазоны относительно машинного кода метода.</span><span class="sxs-lookup"><span data-stu-id="ebd43-116">Call [ICorDebugStepper::SetRangeIL](icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebd43-117">Требования</span><span class="sxs-lookup"><span data-stu-id="ebd43-117">Requirements</span></span>  

 <span data-ttu-id="ebd43-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebd43-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebd43-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebd43-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebd43-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebd43-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebd43-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebd43-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
