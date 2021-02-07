---
description: 'Дополнительные сведения о: интерфейс ICorPublish'
title: Интерфейс ICorPublish
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 0cec1d3407246989c6b916ca0760e6f556566ce6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721831"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="88958-103">Интерфейс ICorPublish</span><span class="sxs-lookup"><span data-stu-id="88958-103">ICorPublish Interface</span></span>

<span data-ttu-id="88958-104">Служит общим интерфейсом для публикации сведений о процессах и сведениях о доменах приложений в этих процессах.</span><span class="sxs-lookup"><span data-stu-id="88958-104">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88958-105">Методы</span><span class="sxs-lookup"><span data-stu-id="88958-105">Methods</span></span>  
  
|<span data-ttu-id="88958-106">Метод</span><span class="sxs-lookup"><span data-stu-id="88958-106">Method</span></span>|<span data-ttu-id="88958-107">Описание</span><span class="sxs-lookup"><span data-stu-id="88958-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88958-108">Метод EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="88958-108">EnumProcesses Method</span></span>](icorpublish-enumprocesses-method.md)|<span data-ttu-id="88958-109">Возвращает экземпляр [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) , содержащий управляемые процессы, запущенные на этом компьютере.</span><span class="sxs-lookup"><span data-stu-id="88958-109">Gets an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="88958-110">Метод GetProcess</span><span class="sxs-lookup"><span data-stu-id="88958-110">GetProcess Method</span></span>](icorpublish-getprocess-method.md)|<span data-ttu-id="88958-111">Возвращает экземпляр [ICorPublishProcess](icorpublishprocess-interface.md) , представляющий процесс с указанным идентификатором.</span><span class="sxs-lookup"><span data-stu-id="88958-111">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88958-112">Требования</span><span class="sxs-lookup"><span data-stu-id="88958-112">Requirements</span></span>  

 <span data-ttu-id="88958-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88958-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88958-114">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="88958-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="88958-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88958-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88958-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88958-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88958-117">См. также</span><span class="sxs-lookup"><span data-stu-id="88958-117">See also</span></span>

- [<span data-ttu-id="88958-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="88958-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="88958-119">Кокласс CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="88958-119">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
