---
description: 'Дополнительные сведения о: Интерфейс IHostMemoryManager'
title: Интерфейс IHostMemoryManager
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
ms.openlocfilehash: c9b6f83b5c70a53388e886e1047798f660b826e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707892"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="2e85e-103">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="2e85e-103">IHostMemoryManager Interface</span></span>

<span data-ttu-id="2e85e-104">Предоставляет методы, позволяющие среде CLR выполнять запросы к виртуальной памяти через основное приложение вместо использования стандартных функций виртуальной памяти Win32.</span><span class="sxs-lookup"><span data-stu-id="2e85e-104">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e85e-105">Методы</span><span class="sxs-lookup"><span data-stu-id="2e85e-105">Methods</span></span>  
  
|<span data-ttu-id="2e85e-106">Метод</span><span class="sxs-lookup"><span data-stu-id="2e85e-106">Method</span></span>|<span data-ttu-id="2e85e-107">Описание</span><span class="sxs-lookup"><span data-stu-id="2e85e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e85e-108">Метод AcquiredVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="2e85e-108">AcquiredVirtualAddressSpace Method</span></span>](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="2e85e-109">Уведомляет узел о том, что среда CLR получила указанную память из операционной системы.</span><span class="sxs-lookup"><span data-stu-id="2e85e-109">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="2e85e-110">Метод CreateMAlloc</span><span class="sxs-lookup"><span data-stu-id="2e85e-110">CreateMAlloc Method</span></span>](ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="2e85e-111">Возвращает указатель интерфейса на экземпляр [IHostMAlloc](ihostmalloc-interface.md) , который используется для запроса выделения памяти из кучи, созданного узлом.</span><span class="sxs-lookup"><span data-stu-id="2e85e-111">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="2e85e-112">Метод GetMemoryLoad</span><span class="sxs-lookup"><span data-stu-id="2e85e-112">GetMemoryLoad Method</span></span>](ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="2e85e-113">Возвращает объем используемой в данный момент физической памяти, сообщаемой узлом.</span><span class="sxs-lookup"><span data-stu-id="2e85e-113">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="2e85e-114">Метод NeedsVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="2e85e-114">NeedsVirtualAddressSpace Method</span></span>](ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="2e85e-115">Уведомляет узел о том, что среда CLR будет пытаться использовать указанную память.</span><span class="sxs-lookup"><span data-stu-id="2e85e-115">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="2e85e-116">Метод RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="2e85e-116">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="2e85e-117">Регистрирует указатель на функцию обратного вызова, которая вызывается хостом для уведомления среды CLR о текущей загрузке памяти на компьютере.</span><span class="sxs-lookup"><span data-stu-id="2e85e-117">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="2e85e-118">Метод ReleasedVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="2e85e-118">ReleasedVirtualAddressSpace Method</span></span>](ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="2e85e-119">Уведомляет узел о том, что среда CLR завершила работу с заданной памятью.</span><span class="sxs-lookup"><span data-stu-id="2e85e-119">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="2e85e-120">Метод VirtualAlloc</span><span class="sxs-lookup"><span data-stu-id="2e85e-120">VirtualAlloc Method</span></span>](ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="2e85e-121">Служит логической оболочкой для соответствующей функции Win32, которая резервирует или фиксирует область страниц в виртуальном адресном пространстве вызывающего процесса.</span><span class="sxs-lookup"><span data-stu-id="2e85e-121">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="2e85e-122">Метод VirtualFree</span><span class="sxs-lookup"><span data-stu-id="2e85e-122">VirtualFree Method</span></span>](ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="2e85e-123">Служит логической оболочкой для соответствующей функции Win32, которая выдает, выдает или освобождает и отменяет выделение области страниц в виртуальном адресном пространстве вызывающего процесса.</span><span class="sxs-lookup"><span data-stu-id="2e85e-123">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="2e85e-124">Метод VirtualProtect</span><span class="sxs-lookup"><span data-stu-id="2e85e-124">VirtualProtect Method</span></span>](ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="2e85e-125">Служит логической оболочкой для соответствующей функции Win32, которая изменяет защиту в области зафиксированных страниц в виртуальном адресном пространстве вызывающего процесса.</span><span class="sxs-lookup"><span data-stu-id="2e85e-125">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="2e85e-126">Метод VirtualQuery</span><span class="sxs-lookup"><span data-stu-id="2e85e-126">VirtualQuery Method</span></span>](ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="2e85e-127">Служит логической оболочкой для соответствующей функции Win32, которая получает сведения о диапазоне страниц в виртуальном адресном пространстве вызывающего процесса.</span><span class="sxs-lookup"><span data-stu-id="2e85e-127">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e85e-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="2e85e-128">Remarks</span></span>  

 <span data-ttu-id="2e85e-129">`IHostMemoryManager` также предоставляет методы для среды CLR для получения указателя, с помощью которого можно выполнять запросы к памяти в куче и получать уровень нехватки памяти в процессе, сообщаемый узлом.</span><span class="sxs-lookup"><span data-stu-id="2e85e-129">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e85e-130">Требования</span><span class="sxs-lookup"><span data-stu-id="2e85e-130">Requirements</span></span>  

 <span data-ttu-id="2e85e-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e85e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e85e-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e85e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e85e-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e85e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e85e-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e85e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e85e-135">См. также</span><span class="sxs-lookup"><span data-stu-id="2e85e-135">See also</span></span>

- [<span data-ttu-id="2e85e-136">Интерфейс IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="2e85e-136">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="2e85e-137">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="2e85e-137">Hosting Interfaces</span></span>](hosting-interfaces.md)
