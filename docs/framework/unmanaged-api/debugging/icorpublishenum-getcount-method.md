---
description: 'Дополнительные сведения о методе: ICorPublishEnum:: NOCOUNT'
title: Метод ICorPublishEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
ms.openlocfilehash: 99e831ae366604e2ae7494bf80fb2e7f25532582
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721623"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="428da-103">Метод ICorPublishEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="428da-103">ICorPublishEnum::GetCount Method</span></span>

<span data-ttu-id="428da-104">Возвращает число элементов в перечислении.</span><span class="sxs-lookup"><span data-stu-id="428da-104">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="428da-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="428da-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="428da-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="428da-106">Parameters</span></span>  

 `pcelt`  
 <span data-ttu-id="428da-107">заполняет Указатель на число элементов в перечислении.</span><span class="sxs-lookup"><span data-stu-id="428da-107">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="428da-108">Требования</span><span class="sxs-lookup"><span data-stu-id="428da-108">Requirements</span></span>  

 <span data-ttu-id="428da-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="428da-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="428da-110">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="428da-110">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="428da-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="428da-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="428da-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="428da-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="428da-113">См. также</span><span class="sxs-lookup"><span data-stu-id="428da-113">See also</span></span>

- [<span data-ttu-id="428da-114">Интерфейс ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="428da-114">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
