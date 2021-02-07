---
description: 'Дополнительные сведения о методе: ICorDebugEval2:: RudeAbort'
title: Метод ICorDebugEval2::RudeAbort
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
ms.openlocfilehash: 2835fd635da007b5ee3f0e642b77f3954945f168
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693516"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="6c332-103">Метод ICorDebugEval2::RudeAbort</span><span class="sxs-lookup"><span data-stu-id="6c332-103">ICorDebugEval2::RudeAbort Method</span></span>

<span data-ttu-id="6c332-104">Прерывает вычисление, выполняемое `ICorDebugEval2` в данный момент.</span><span class="sxs-lookup"><span data-stu-id="6c332-104">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c332-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6c332-105">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6c332-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="6c332-106">Remarks</span></span>  

 <span data-ttu-id="6c332-107">`RudeAbort` не освобождает никакие блокировки, которые содержит средство оценки, поэтому сеанс отладки остается в ненадежном состоянии.</span><span class="sxs-lookup"><span data-stu-id="6c332-107">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="6c332-108">Вызывайте этот метод с особой осторожностью.</span><span class="sxs-lookup"><span data-stu-id="6c332-108">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c332-109">Требования</span><span class="sxs-lookup"><span data-stu-id="6c332-109">Requirements</span></span>  

 <span data-ttu-id="6c332-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c332-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c332-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c332-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c332-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c332-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c332-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c332-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
