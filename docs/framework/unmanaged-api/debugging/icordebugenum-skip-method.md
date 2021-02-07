---
description: 'Дополнительные сведения о методе: ICorDebugEnum:: Skip'
title: Метод ICorDebugEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type:
- apiref
ms.openlocfilehash: f72e400b3c2c911f609aca19f1b7d6a3a4e785cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694361"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="ee031-103">Метод ICorDebugEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="ee031-103">ICorDebugEnum::Skip Method</span></span>

<span data-ttu-id="ee031-104">Перемещает курсор вперед в перечислении на указанное число элементов.</span><span class="sxs-lookup"><span data-stu-id="ee031-104">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee031-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ee031-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee031-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ee031-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="ee031-107">окне Число элементов, по которым перемещается курсор.</span><span class="sxs-lookup"><span data-stu-id="ee031-107">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee031-108">Требования</span><span class="sxs-lookup"><span data-stu-id="ee031-108">Requirements</span></span>  

 <span data-ttu-id="ee031-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee031-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee031-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee031-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee031-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee031-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee031-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee031-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee031-113">См. также</span><span class="sxs-lookup"><span data-stu-id="ee031-113">See also</span></span>

- [<span data-ttu-id="ee031-114">Интерфейс ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="ee031-114">ICorDebugEnum Interface</span></span>](icordebugenum-interface1.md)
