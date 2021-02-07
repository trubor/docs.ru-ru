---
description: 'Дополнительные сведения о методе ICorDebugStepper:: Сетунмаппедстопмаск'
title: Метод ICorDebugStepper::SetUnmappedStopMask
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
ms.openlocfilehash: 60b8fd4b74e1eeb76868fc6cdac308ff805e44db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717721"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="4a4c2-103">Метод ICorDebugStepper::SetUnmappedStopMask</span><span class="sxs-lookup"><span data-stu-id="4a4c2-103">ICorDebugStepper::SetUnmappedStopMask Method</span></span>

<span data-ttu-id="4a4c2-104">Задает значение, указывающее тип несопоставленного кода, в котором выполнение будет остановлено.</span><span class="sxs-lookup"><span data-stu-id="4a4c2-104">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a4c2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a4c2-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a4c2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4a4c2-106">Parameters</span></span>  

 `mask`  
 <span data-ttu-id="4a4c2-107">окне Значение перечисления Кордебугунмаппедстоп, указывающее тип несопоставленного кода, в котором отладчик остановит выполнение.</span><span class="sxs-lookup"><span data-stu-id="4a4c2-107">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="4a4c2-108">Значение по умолчанию — STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="4a4c2-108">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="4a4c2-109">Значение STOP_UNMANAGED допустимо только при отладке взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="4a4c2-109">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a4c2-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="4a4c2-110">Remarks</span></span>  

 <span data-ttu-id="4a4c2-111">Когда отладчик находит JIT-компиляцию, которая не имеет соответствующего сопоставления с MSIL, он прекращает выполнение, если установлен флаг, указывающий этот тип несопоставленного кода. в противном случае выполнение по шагам прозрачно продолжится.</span><span class="sxs-lookup"><span data-stu-id="4a4c2-111">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="4a4c2-112">Если отладчик не использует средство многошагового режима для входа в метод, он не обязательно будет выполнять шаг с обходом несопоставленного кода.</span><span class="sxs-lookup"><span data-stu-id="4a4c2-112">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a4c2-113">Требования</span><span class="sxs-lookup"><span data-stu-id="4a4c2-113">Requirements</span></span>  

 <span data-ttu-id="4a4c2-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a4c2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a4c2-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a4c2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a4c2-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a4c2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a4c2-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a4c2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
