---
description: 'Дополнительные сведения о: интерфейс ICLRControl'
title: Интерфейс ICLRControl
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: e108506d06b746d631f4c15c37d467399de30aba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637668"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="f12dd-103">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="f12dd-103">ICLRControl Interface</span></span>

<span data-ttu-id="f12dd-104">Предоставляет методы, позволяющие узлу получать ссылки и настраивать аспекты среды CLR.</span><span class="sxs-lookup"><span data-stu-id="f12dd-104">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f12dd-105">Методы</span><span class="sxs-lookup"><span data-stu-id="f12dd-105">Methods</span></span>  
  
|<span data-ttu-id="f12dd-106">Метод</span><span class="sxs-lookup"><span data-stu-id="f12dd-106">Method</span></span>|<span data-ttu-id="f12dd-107">Описание</span><span class="sxs-lookup"><span data-stu-id="f12dd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f12dd-108">Метод GetCLRManager</span><span class="sxs-lookup"><span data-stu-id="f12dd-108">GetCLRManager Method</span></span>](iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="f12dd-109">Возвращает указатель интерфейса на экземпляр любого из типов диспетчера, который узел может использовать для настройки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="f12dd-109">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="f12dd-110">Метод SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="f12dd-110">SetAppDomainManagerType Method</span></span>](iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="f12dd-111">Задает тип, производный от <xref:System.AppDomainManager> типа для диспетчеров доменов приложений.</span><span class="sxs-lookup"><span data-stu-id="f12dd-111">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f12dd-112">Требования</span><span class="sxs-lookup"><span data-stu-id="f12dd-112">Requirements</span></span>  

 <span data-ttu-id="f12dd-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f12dd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f12dd-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f12dd-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f12dd-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f12dd-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f12dd-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f12dd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12dd-117">См. также</span><span class="sxs-lookup"><span data-stu-id="f12dd-117">See also</span></span>

- [<span data-ttu-id="f12dd-118">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="f12dd-118">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="f12dd-119">Интерфейс ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="f12dd-119">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="f12dd-120">Интерфейс ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="f12dd-120">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="f12dd-121">Интерфейс ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="f12dd-121">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="f12dd-122">Интерфейс ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="f12dd-122">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="f12dd-123">Интерфейс ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="f12dd-123">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="f12dd-124">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="f12dd-124">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="f12dd-125">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="f12dd-125">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="f12dd-126">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="f12dd-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
