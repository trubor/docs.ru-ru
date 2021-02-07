---
description: 'Дополнительные сведения о методе: ICorDebugEval:: onactive'
title: Метод ICorDebugEval::IsActive
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
ms.openlocfilehash: 2314814f8979f460063017ebdf46beb512417395
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694062"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="8e153-103">Метод ICorDebugEval::IsActive</span><span class="sxs-lookup"><span data-stu-id="8e153-103">ICorDebugEval::IsActive Method</span></span>

<span data-ttu-id="8e153-104">Возвращает значение, указывающее, выполняется ли в данный момент объект ICorDebugEval.</span><span class="sxs-lookup"><span data-stu-id="8e153-104">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e153-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8e153-105">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e153-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8e153-106">Parameters</span></span>  

 `pbActive`  
 <span data-ttu-id="8e153-107">заполняет Указатель на значение, указывающее, активна ли эта оценка.</span><span class="sxs-lookup"><span data-stu-id="8e153-107">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e153-108">Требования</span><span class="sxs-lookup"><span data-stu-id="8e153-108">Requirements</span></span>  

 <span data-ttu-id="8e153-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e153-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e153-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e153-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e153-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e153-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e153-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e153-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
