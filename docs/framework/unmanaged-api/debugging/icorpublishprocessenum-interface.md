---
description: 'Дополнительные сведения о: интерфейс ICorPublishProcessEnum'
title: Интерфейс ICorPublishProcessEnum
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 87d80d066995dbeca67f461e01652dd3deb3bf1b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790494"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="8e223-103">Интерфейс ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="8e223-103">ICorPublishProcessEnum Interface</span></span>

<span data-ttu-id="8e223-104">Подкласс интерфейса [ICorPublishEnum](icorpublishenum-interface.md) , предоставляющий методы для прохода по коллекции объектов [ICorPublishProcess](icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8e223-104">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e223-105">Методы</span><span class="sxs-lookup"><span data-stu-id="8e223-105">Methods</span></span>  
  
|<span data-ttu-id="8e223-106">Метод</span><span class="sxs-lookup"><span data-stu-id="8e223-106">Method</span></span>|<span data-ttu-id="8e223-107">Описание</span><span class="sxs-lookup"><span data-stu-id="8e223-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e223-108">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="8e223-108">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="8e223-109">Возвращает указанное количество `ICorPublishProcess` экземпляров из коллекции, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="8e223-109">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e223-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="8e223-110">Remarks</span></span>  

 <span data-ttu-id="8e223-111">`ICorPublishProcessEnum`Интерфейс реализует методы абстрактного интерфейса [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8e223-111">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="8e223-112">`ICorPublishProcessEnum`Экземпляр создается методом [ICorPublish:: EnumProcesses](icorpublish-enumprocesses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8e223-112">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="8e223-113">Обход коллекции `ICorPublishProcess` объектов основан на условиях фильтрации, заданных на момент `ICorPublishProcessEnum` создания экземпляра.</span><span class="sxs-lookup"><span data-stu-id="8e223-113">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e223-114">Требования</span><span class="sxs-lookup"><span data-stu-id="8e223-114">Requirements</span></span>  

 <span data-ttu-id="8e223-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e223-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e223-116">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="8e223-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="8e223-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e223-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e223-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e223-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e223-119">См. также</span><span class="sxs-lookup"><span data-stu-id="8e223-119">See also</span></span>

- [<span data-ttu-id="8e223-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="8e223-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8e223-121">Кокласс CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="8e223-121">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
