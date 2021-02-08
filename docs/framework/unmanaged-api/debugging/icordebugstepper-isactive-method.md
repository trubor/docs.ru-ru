---
description: 'Дополнительные сведения о методе ICorDebugStepper:: "onactive"'
title: Метод ICorDebugStepper::IsActive
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: 7ef937ac3c1e6f3ad9ad83b5fa84382cac3ac9c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803572"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="86a14-103">Метод ICorDebugStepper::IsActive</span><span class="sxs-lookup"><span data-stu-id="86a14-103">ICorDebugStepper::IsActive Method</span></span>

<span data-ttu-id="86a14-104">Возвращает значение, указывающее, выполняется ли в данный момент шаг.</span><span class="sxs-lookup"><span data-stu-id="86a14-104">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86a14-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="86a14-105">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86a14-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="86a14-106">Parameters</span></span>  

 `pbActive`  
 <span data-ttu-id="86a14-107">заполняет Возвращает `true` , если средство Организации в данный момент исполняет шаг; в противном случае возвращает `false` .</span><span class="sxs-lookup"><span data-stu-id="86a14-107">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86a14-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="86a14-108">Remarks</span></span>  

 <span data-ttu-id="86a14-109">Любое действие шага остается активным до тех пор, пока отладчик не получит вызов [ICorDebugManagedCallback:: StepComplete](icordebugmanagedcallback-stepcomplete-method.md) , который автоматически деактивирует средство Организации.</span><span class="sxs-lookup"><span data-stu-id="86a14-109">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="86a14-110">Пошаговое руководство также может быть деактивировано преждевременно путем вызова [ICorDebugStepper::D еактивате](icordebugstepper-deactivate-method.md) до достижения условия обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="86a14-110">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86a14-111">Требования</span><span class="sxs-lookup"><span data-stu-id="86a14-111">Requirements</span></span>  

 <span data-ttu-id="86a14-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86a14-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86a14-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86a14-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86a14-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86a14-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86a14-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86a14-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
