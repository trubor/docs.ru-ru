---
description: 'Дополнительные сведения о: интерфейс ICLRMemoryNotificationCallback'
title: Интерфейс ICLRMemoryNotificationCallback
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
ms.openlocfilehash: 46e53cdf0b7f797b8945237d47fc3b521b08ddb7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689243"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="d7afd-103">Интерфейс ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="d7afd-103">ICLRMemoryNotificationCallback Interface</span></span>

<span data-ttu-id="d7afd-104">Позволяет узлу сообщать об условиях нехватки памяти с помощью подхода, аналогичного функции Win32 `CreateMemoryResourceNotification` .</span><span class="sxs-lookup"><span data-stu-id="d7afd-104">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7afd-105">Методы</span><span class="sxs-lookup"><span data-stu-id="d7afd-105">Methods</span></span>  
  
|<span data-ttu-id="d7afd-106">Метод</span><span class="sxs-lookup"><span data-stu-id="d7afd-106">Method</span></span>|<span data-ttu-id="d7afd-107">Описание</span><span class="sxs-lookup"><span data-stu-id="d7afd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7afd-108">Метод OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="d7afd-108">OnMemoryNotification Method</span></span>](iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="d7afd-109">Уведомляет среду CLR о загрузке памяти на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d7afd-109">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7afd-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="d7afd-110">Remarks</span></span>  

 <span data-ttu-id="d7afd-111">Узел использует `ICLRMemoryNotificationCallback` интерфейс для запроса освобождения ресурсов памяти CLR.</span><span class="sxs-lookup"><span data-stu-id="d7afd-111">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7afd-112">Требования</span><span class="sxs-lookup"><span data-stu-id="d7afd-112">Requirements</span></span>  

 <span data-ttu-id="d7afd-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7afd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7afd-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d7afd-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7afd-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d7afd-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7afd-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7afd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7afd-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d7afd-117">See also</span></span>

- [<span data-ttu-id="d7afd-118">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="d7afd-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="d7afd-119">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="d7afd-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
