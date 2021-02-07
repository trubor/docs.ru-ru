---
description: 'Дополнительные сведения о: интерфейс ICorPublishEnum'
title: Интерфейс ICorPublishEnum
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: c0d50f67bd61eecbade0b226f2f569ac26712faf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721610"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="2e8a2-103">Интерфейс ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="2e8a2-103">ICorPublishEnum Interface</span></span>

<span data-ttu-id="2e8a2-104">Служит абстрактным базовым интерфейсом для перечислителей, используемых в публикации сведений о процессах и доменах приложений.</span><span class="sxs-lookup"><span data-stu-id="2e8a2-104">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e8a2-105">Методы</span><span class="sxs-lookup"><span data-stu-id="2e8a2-105">Methods</span></span>  
  
|<span data-ttu-id="2e8a2-106">Метод</span><span class="sxs-lookup"><span data-stu-id="2e8a2-106">Method</span></span>|<span data-ttu-id="2e8a2-107">Описание</span><span class="sxs-lookup"><span data-stu-id="2e8a2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e8a2-108">Метод Clone</span><span class="sxs-lookup"><span data-stu-id="2e8a2-108">Clone Method</span></span>](icorpublishenum-clone-method.md)|<span data-ttu-id="2e8a2-109">Создает копию данного объекта `ICorPublishEnum`.</span><span class="sxs-lookup"><span data-stu-id="2e8a2-109">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="2e8a2-110">Метод GetCount</span><span class="sxs-lookup"><span data-stu-id="2e8a2-110">GetCount Method</span></span>](icorpublishenum-getcount-method.md)|<span data-ttu-id="2e8a2-111">Возвращает число элементов в перечислении.</span><span class="sxs-lookup"><span data-stu-id="2e8a2-111">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="2e8a2-112">Метод Reset</span><span class="sxs-lookup"><span data-stu-id="2e8a2-112">Reset Method</span></span>](icorpublishenum-reset-method.md)|<span data-ttu-id="2e8a2-113">Перемещает курсор в начало перечисления.</span><span class="sxs-lookup"><span data-stu-id="2e8a2-113">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="2e8a2-114">Метод Skip</span><span class="sxs-lookup"><span data-stu-id="2e8a2-114">Skip Method</span></span>](icorpublishenum-skip-method.md)|<span data-ttu-id="2e8a2-115">Перемещает курсор вперед в перечислении на указанное число элементов.</span><span class="sxs-lookup"><span data-stu-id="2e8a2-115">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e8a2-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="2e8a2-116">Remarks</span></span>  

 <span data-ttu-id="2e8a2-117">Следующие перечислители являются производными от `ICorPublishEnum` :</span><span class="sxs-lookup"><span data-stu-id="2e8a2-117">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="2e8a2-118">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="2e8a2-118">ICorPublishAppDomainEnum</span></span>](icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="2e8a2-119">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="2e8a2-119">ICorPublishProcessEnum</span></span>](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="2e8a2-120">Требования</span><span class="sxs-lookup"><span data-stu-id="2e8a2-120">Requirements</span></span>  

 <span data-ttu-id="2e8a2-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e8a2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e8a2-122">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="2e8a2-122">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2e8a2-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e8a2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e8a2-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e8a2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e8a2-125">См. также</span><span class="sxs-lookup"><span data-stu-id="2e8a2-125">See also</span></span>

- [<span data-ttu-id="2e8a2-126">Кокласс CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="2e8a2-126">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
- [<span data-ttu-id="2e8a2-127">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="2e8a2-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
