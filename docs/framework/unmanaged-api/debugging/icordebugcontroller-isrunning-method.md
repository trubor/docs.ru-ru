---
description: 'См. Дополнительные сведения о методе ICorDebugController:: onвыполняющемуся.'
title: Метод ICorDebugController::IsRunning
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
ms.openlocfilehash: 6a0628cc39765d9cb295877d912d92dbb27937da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764584"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="07dd6-103">Метод ICorDebugController::IsRunning</span><span class="sxs-lookup"><span data-stu-id="07dd6-103">ICorDebugController::IsRunning Method</span></span>

<span data-ttu-id="07dd6-104">Возвращает значение, указывающее, выполняются ли в настоящий момент потоки в процессе.</span><span class="sxs-lookup"><span data-stu-id="07dd6-104">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07dd6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="07dd6-105">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07dd6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="07dd6-106">Parameters</span></span>  

 `pbRunning`  
 <span data-ttu-id="07dd6-107">заполняет Указатель на значение, равное, `true` Если потоки в процессе выполняются свободно; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="07dd6-107">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07dd6-108">Требования</span><span class="sxs-lookup"><span data-stu-id="07dd6-108">Requirements</span></span>  

 <span data-ttu-id="07dd6-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07dd6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07dd6-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07dd6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07dd6-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07dd6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07dd6-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07dd6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07dd6-113">См. также</span><span class="sxs-lookup"><span data-stu-id="07dd6-113">See also</span></span>
