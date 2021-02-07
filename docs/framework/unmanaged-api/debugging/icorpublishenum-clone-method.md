---
description: 'Дополнительные сведения о методе: ICorPublishEnum:: Clone'
title: Метод ICorPublishEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
ms.openlocfilehash: 6001f27451afdb564da6275a31256ac348bc693a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721649"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="f8ac4-103">Метод ICorPublishEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="f8ac4-103">ICorPublishEnum::Clone Method</span></span>

<span data-ttu-id="f8ac4-104">Создает копию этого объекта [ICorPublishEnum](icorpublishenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f8ac4-104">Creates a copy of this [ICorPublishEnum](icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8ac4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f8ac4-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8ac4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f8ac4-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="f8ac4-107">заполняет Указатель на адрес `ICorPublishEnum` объекта, который является копией этого `ICorPublishEnum` объекта.</span><span class="sxs-lookup"><span data-stu-id="f8ac4-107">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8ac4-108">Требования</span><span class="sxs-lookup"><span data-stu-id="f8ac4-108">Requirements</span></span>  

 <span data-ttu-id="f8ac4-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8ac4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8ac4-110">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="f8ac4-110">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f8ac4-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8ac4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8ac4-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8ac4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8ac4-113">См. также</span><span class="sxs-lookup"><span data-stu-id="f8ac4-113">See also</span></span>

- [<span data-ttu-id="f8ac4-114">Интерфейс ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="f8ac4-114">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
