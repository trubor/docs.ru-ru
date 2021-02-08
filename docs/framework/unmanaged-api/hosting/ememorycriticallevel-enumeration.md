---
description: Дополнительные сведения о перечислении EMemoryCriticalLevel
title: Перечисление EMemoryCriticalLevel
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
ms.openlocfilehash: 88965a29164de1ec7b01c2fcc8f51415127e69fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785436"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="41a02-103">Перечисление EMemoryCriticalLevel</span><span class="sxs-lookup"><span data-stu-id="41a02-103">EMemoryCriticalLevel Enumeration</span></span>

<span data-ttu-id="41a02-104">Содержит значения, которые указывают на влияние сбоя при запросе определенного выделения памяти, но не могут быть удовлетворены.</span><span class="sxs-lookup"><span data-stu-id="41a02-104">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41a02-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="41a02-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="41a02-106">Члены</span><span class="sxs-lookup"><span data-stu-id="41a02-106">Members</span></span>  
  
|<span data-ttu-id="41a02-107">Член</span><span class="sxs-lookup"><span data-stu-id="41a02-107">Member</span></span>|<span data-ttu-id="41a02-108">Описание</span><span class="sxs-lookup"><span data-stu-id="41a02-108">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="41a02-109">Указывает, что выделение является критически важным для исполнения управляемого кода в домене, который запросил выделение.</span><span class="sxs-lookup"><span data-stu-id="41a02-109">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="41a02-110">Если память не может быть выделена, среда CLR не может гарантировать, что домен будет использоваться.</span><span class="sxs-lookup"><span data-stu-id="41a02-110">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="41a02-111">Основное приложение принимает решение, какое действие следует предпринять, если выделение не может быть удовлетворено.</span><span class="sxs-lookup"><span data-stu-id="41a02-111">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="41a02-112">Он может дать среде CLR команду на автоматическое прерывание `AppDomain` или разрешить ее выполнение путем вызова методов в [ICLRPolicyManager](iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="41a02-112">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="41a02-113">Указывает, что выделение является критически важным для выполнения управляемого кода в процессе.</span><span class="sxs-lookup"><span data-stu-id="41a02-113">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="41a02-114">Это значение используется при запуске и при запуске методов завершения.</span><span class="sxs-lookup"><span data-stu-id="41a02-114">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="41a02-115">Если память не может быть выделена, среда CLR не может работать в процессе.</span><span class="sxs-lookup"><span data-stu-id="41a02-115">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="41a02-116">Если выделение завершается неудачей, среда CLR фактически отключается.</span><span class="sxs-lookup"><span data-stu-id="41a02-116">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="41a02-117">Все последующие вызовы в среде CLR завершаются сбоем с HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="41a02-117">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="41a02-118">Указывает, что выделение является критически важным для выполнения задачи, которая запросила выделение.</span><span class="sxs-lookup"><span data-stu-id="41a02-118">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="41a02-119">Если память не может быть выделена, среда CLR не может гарантировать, что задача может быть выполнена.</span><span class="sxs-lookup"><span data-stu-id="41a02-119">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="41a02-120">В случае сбоя среда CLR создает исключение <xref:System.Threading.ThreadAbortException> в системном потоке физической операции.</span><span class="sxs-lookup"><span data-stu-id="41a02-120">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41a02-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="41a02-121">Remarks</span></span>  

 <span data-ttu-id="41a02-122">Методы выделения памяти, определенные в интерфейсах [IHostMemoryManager](ihostmemorymanager-interface.md) и [IHostMAlloc](ihostmalloc-interface.md) , принимают параметр этого типа.</span><span class="sxs-lookup"><span data-stu-id="41a02-122">The memory allocation methods defined in the [IHostMemoryManager](ihostmemorymanager-interface.md) and [IHostMAlloc](ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="41a02-123">В зависимости от серьезности сбоя узел может решить, следует ли немедленно выполнить запрос на выделение или подождать, пока он не будет удовлетворен.</span><span class="sxs-lookup"><span data-stu-id="41a02-123">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41a02-124">Требования</span><span class="sxs-lookup"><span data-stu-id="41a02-124">Requirements</span></span>  

 <span data-ttu-id="41a02-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41a02-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41a02-126">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41a02-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41a02-127">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41a02-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41a02-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41a02-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a02-129">См. также</span><span class="sxs-lookup"><span data-stu-id="41a02-129">See also</span></span>

- [<span data-ttu-id="41a02-130">Интерфейс ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="41a02-130">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="41a02-131">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="41a02-131">Hosting Enumerations</span></span>](hosting-enumerations.md)
