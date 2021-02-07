---
description: 'Дополнительные сведения о: интерфейс ICorPublishAppDomainEnum'
title: Интерфейс ICorPublishAppDomainEnum
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
ms.openlocfilehash: 4e84af576103a792308fd44f903f2ae4daa5d736
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721792"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="0c997-103">Интерфейс ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="0c997-103">ICorPublishAppDomainEnum Interface</span></span>

<span data-ttu-id="0c997-104">Подкласс интерфейса [ICorPublishEnum](icorpublishenum-interface.md) , предоставляющий методы для прохода по коллекции объектов [ICorPublishAppDomain](icorpublishappdomain-interface.md) , которые в данный момент существуют в процессе.</span><span class="sxs-lookup"><span data-stu-id="0c997-104">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c997-105">Методы</span><span class="sxs-lookup"><span data-stu-id="0c997-105">Methods</span></span>  
  
|<span data-ttu-id="0c997-106">Метод</span><span class="sxs-lookup"><span data-stu-id="0c997-106">Method</span></span>|<span data-ttu-id="0c997-107">Описание</span><span class="sxs-lookup"><span data-stu-id="0c997-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c997-108">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="0c997-108">Next Method</span></span>](icorpublishappdomainenum-next-method.md)|<span data-ttu-id="0c997-109">Возвращает указанное количество `ICorPublishAppDomain` экземпляров из коллекции, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="0c997-109">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c997-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="0c997-110">Remarks</span></span>  

 <span data-ttu-id="0c997-111">`ICorPublishAppDomainEnum`Интерфейс реализует методы абстрактного интерфейса [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0c997-111">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c997-112">Требования</span><span class="sxs-lookup"><span data-stu-id="0c997-112">Requirements</span></span>  

 <span data-ttu-id="0c997-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c997-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c997-114">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="0c997-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0c997-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c997-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c997-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c997-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c997-117">См. также</span><span class="sxs-lookup"><span data-stu-id="0c997-117">See also</span></span>

- [<span data-ttu-id="0c997-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="0c997-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0c997-119">Кокласс CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="0c997-119">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
