---
description: 'Дополнительные сведения о методе: ICorDebugEval:: Abort'
title: Метод ICorDebugEval::Abort
ms.date: 03/30/2017
api_name:
- ICorDebugEval.Abort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type:
- apiref
ms.openlocfilehash: d61cb0d696a8a134d992bc8dbbfdb61103ef469f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694322"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="2895d-103">Метод ICorDebugEval::Abort</span><span class="sxs-lookup"><span data-stu-id="2895d-103">ICorDebugEval::Abort Method</span></span>

<span data-ttu-id="2895d-104">Прерывает вычисление, которое данный объект ICorDebugEval сейчас выполняет.</span><span class="sxs-lookup"><span data-stu-id="2895d-104">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2895d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2895d-105">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2895d-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="2895d-106">Remarks</span></span>  

 <span data-ttu-id="2895d-107">Если оценка является вложенной и не является самой последней, `Abort` метод может завершиться ошибкой.</span><span class="sxs-lookup"><span data-stu-id="2895d-107">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2895d-108">Требования</span><span class="sxs-lookup"><span data-stu-id="2895d-108">Requirements</span></span>  

 <span data-ttu-id="2895d-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2895d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2895d-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2895d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2895d-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2895d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2895d-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2895d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
