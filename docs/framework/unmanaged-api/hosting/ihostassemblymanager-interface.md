---
description: 'Дополнительные сведения о: интерфейс IHostAssemblyManager'
title: Интерфейс IHostAssemblyManager
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
ms.openlocfilehash: 649771f79e65039adfa8c0ade9f167b1679bb917
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709000"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="afded-103">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="afded-103">IHostAssemblyManager Interface</span></span>

<span data-ttu-id="afded-104">Предоставляет методы, позволяющие узлу указывать наборы сборок, которые должны быть загружены средой CLR или узлом.</span><span class="sxs-lookup"><span data-stu-id="afded-104">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="afded-105">Методы</span><span class="sxs-lookup"><span data-stu-id="afded-105">Methods</span></span>  
  
|<span data-ttu-id="afded-106">Метод</span><span class="sxs-lookup"><span data-stu-id="afded-106">Method</span></span>|<span data-ttu-id="afded-107">Описание</span><span class="sxs-lookup"><span data-stu-id="afded-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="afded-108">Метод GetAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="afded-108">GetAssemblyStore Method</span></span>](ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="afded-109">Возвращает указатель интерфейса на объект [IHostAssemblyStore](ihostassemblystore-interface.md) , представляющий список сборок, загруженных узлом.</span><span class="sxs-lookup"><span data-stu-id="afded-109">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="afded-110">Метод GetNonHostStoreAssemblies</span><span class="sxs-lookup"><span data-stu-id="afded-110">GetNonHostStoreAssemblies Method</span></span>](ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="afded-111">Возвращает указатель интерфейса на объект [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , представляющий список сборок, которые узел загружает в среду CLR.</span><span class="sxs-lookup"><span data-stu-id="afded-111">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afded-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="afded-112">Remarks</span></span>  

 <span data-ttu-id="afded-113">Узел не является обязательным для реализации `IHostAssemblyManager` или `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="afded-113">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="afded-114">Если узел выполняет реализацию `IHostAssemblyManager` , он также должен реализовать `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="afded-114">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="afded-115">Среда выполнения запрашивает `IHostAssemblyManager` , вызывая [IHostControl:: жесостманажер](ihostcontrol-gethostmanager-method.md) при инициализации с `IID` IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="afded-115">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afded-116">Требования</span><span class="sxs-lookup"><span data-stu-id="afded-116">Requirements</span></span>  

 <span data-ttu-id="afded-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afded-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afded-118">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="afded-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="afded-119">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="afded-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afded-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afded-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afded-121">См. также</span><span class="sxs-lookup"><span data-stu-id="afded-121">See also</span></span>

- [<span data-ttu-id="afded-122">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="afded-122">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="afded-123">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="afded-123">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="afded-124">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="afded-124">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="afded-125">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="afded-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
