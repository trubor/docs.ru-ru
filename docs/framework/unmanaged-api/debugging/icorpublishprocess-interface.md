---
description: 'Дополнительные сведения о: интерфейс ICorPublishProcess'
title: Интерфейс ICorPublishProcess
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
ms.openlocfilehash: 8dbc619d33c2c9b625dde852948dff00b5be926e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800881"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="75f91-103">Интерфейс ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="75f91-103">ICorPublishProcess Interface</span></span>

<span data-ttu-id="75f91-104">Предоставляет методы, которые обращаются к сведениям, отображаемым в процессе.</span><span class="sxs-lookup"><span data-stu-id="75f91-104">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75f91-105">Методы</span><span class="sxs-lookup"><span data-stu-id="75f91-105">Methods</span></span>  
  
|<span data-ttu-id="75f91-106">Метод</span><span class="sxs-lookup"><span data-stu-id="75f91-106">Method</span></span>|<span data-ttu-id="75f91-107">Описание</span><span class="sxs-lookup"><span data-stu-id="75f91-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75f91-108">Метод EnumAppDomains</span><span class="sxs-lookup"><span data-stu-id="75f91-108">EnumAppDomains Method</span></span>](icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="75f91-109">Возвращает экземпляр [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) , содержащий домены приложений в процессе, на который ссылается this `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="75f91-109">Gets an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="75f91-110">Метод GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="75f91-110">GetDisplayName Method</span></span>](icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="75f91-111">Возвращает полный путь к исполняемому файлу для процесса, на который ссылается this `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="75f91-111">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="75f91-112">Метод GetProcessID</span><span class="sxs-lookup"><span data-stu-id="75f91-112">GetProcessID Method</span></span>](icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="75f91-113">Возвращает идентификатор операционной системы для процесса, на который ссылается this `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="75f91-113">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="75f91-114">Метод IsManaged</span><span class="sxs-lookup"><span data-stu-id="75f91-114">IsManaged Method</span></span>](icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="75f91-115">Возвращает значение, указывающее, называется ли процесс, на который ссылается данный объект, `ICorPublishProcess` выполнением управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="75f91-115">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75f91-116">Требования</span><span class="sxs-lookup"><span data-stu-id="75f91-116">Requirements</span></span>  

 <span data-ttu-id="75f91-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75f91-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75f91-118">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="75f91-118">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="75f91-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75f91-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75f91-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75f91-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f91-121">См. также</span><span class="sxs-lookup"><span data-stu-id="75f91-121">See also</span></span>

- [<span data-ttu-id="75f91-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="75f91-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="75f91-123">Кокласс CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="75f91-123">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
