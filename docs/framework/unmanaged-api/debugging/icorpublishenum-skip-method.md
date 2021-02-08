---
description: 'Дополнительные сведения о методе: ICorPublishEnum:: Skip'
title: Метод ICorPublishEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
ms.openlocfilehash: f0124681c8051a5c05c1caf3edd06c697da486e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794607"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="73928-103">Метод ICorPublishEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="73928-103">ICorPublishEnum::Skip Method</span></span>

<span data-ttu-id="73928-104">Перемещает курсор вперед в перечислении на указанное число элементов.</span><span class="sxs-lookup"><span data-stu-id="73928-104">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73928-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="73928-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73928-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="73928-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="73928-107">окне Число элементов, по которым перемещается курсор.</span><span class="sxs-lookup"><span data-stu-id="73928-107">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73928-108">Требования</span><span class="sxs-lookup"><span data-stu-id="73928-108">Requirements</span></span>  

 <span data-ttu-id="73928-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73928-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73928-110">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="73928-110">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="73928-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73928-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73928-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73928-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73928-113">См. также</span><span class="sxs-lookup"><span data-stu-id="73928-113">See also</span></span>

- [<span data-ttu-id="73928-114">Интерфейс ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="73928-114">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
