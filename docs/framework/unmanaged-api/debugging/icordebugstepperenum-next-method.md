---
description: 'Дополнительные сведения о методе: Икордебугстепперенум:: Next'
title: Метод ICorDebugStepperEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
ms.openlocfilehash: e0c17fbc570d5ea8a4a56c89a5a2c855ed045bd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717476"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="dbed8-103">Метод ICorDebugStepperEnum::Next</span><span class="sxs-lookup"><span data-stu-id="dbed8-103">ICorDebugStepperEnum::Next Method</span></span>

<span data-ttu-id="dbed8-104">Возвращает указанное число экземпляров ICorDebugStepper из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="dbed8-104">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbed8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dbed8-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbed8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dbed8-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="dbed8-107">окне Число `ICorDebugStepper` извлекаемых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="dbed8-107">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="dbed8-108">заполняет Массив указателей, каждый из которых указывает на `ICorDebugStepper` объект.</span><span class="sxs-lookup"><span data-stu-id="dbed8-108">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="dbed8-109">заполняет Указатель на число `ICorDebugStepper` фактически возвращенных экземпляров.</span><span class="sxs-lookup"><span data-stu-id="dbed8-109">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="dbed8-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="dbed8-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbed8-111">Требования</span><span class="sxs-lookup"><span data-stu-id="dbed8-111">Requirements</span></span>  

 <span data-ttu-id="dbed8-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbed8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbed8-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbed8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbed8-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbed8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbed8-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbed8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
