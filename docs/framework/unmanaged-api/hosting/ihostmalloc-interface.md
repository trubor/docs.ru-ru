---
description: 'Дополнительные сведения о: интерфейс IHostMalloc'
title: Интерфейс IHostMalloc
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
ms.openlocfilehash: cd04a0f71fd429ea10b9edcce02806f4afa57148
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708181"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="92af1-103">Интерфейс IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="92af1-103">IHostMalloc Interface</span></span>

<span data-ttu-id="92af1-104">Предоставляет методы, позволяющие среде CLR запрашивать детализированные выделения из кучи через узел.</span><span class="sxs-lookup"><span data-stu-id="92af1-104">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92af1-105">Методы</span><span class="sxs-lookup"><span data-stu-id="92af1-105">Methods</span></span>  
  
|<span data-ttu-id="92af1-106">Метод</span><span class="sxs-lookup"><span data-stu-id="92af1-106">Method</span></span>|<span data-ttu-id="92af1-107">Описание</span><span class="sxs-lookup"><span data-stu-id="92af1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92af1-108">Метод Alloc</span><span class="sxs-lookup"><span data-stu-id="92af1-108">Alloc Method</span></span>](ihostmalloc-alloc-method.md)|<span data-ttu-id="92af1-109">Запрашивает у узла выделение запрошенного объема памяти из кучи.</span><span class="sxs-lookup"><span data-stu-id="92af1-109">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="92af1-110">Метод DebugAlloc</span><span class="sxs-lookup"><span data-stu-id="92af1-110">DebugAlloc Method</span></span>](ihostmalloc-debugalloc-method.md)|<span data-ttu-id="92af1-111">Запрашивает, что узел выделяет запрошенный объем памяти из кучи, и дополнительно следит за местом выделения памяти.</span><span class="sxs-lookup"><span data-stu-id="92af1-111">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="92af1-112">Метод Free</span><span class="sxs-lookup"><span data-stu-id="92af1-112">Free Method</span></span>](ihostmalloc-free-method.md)|<span data-ttu-id="92af1-113">Освобождает память, выделенную с помощью `Alloc` метода.</span><span class="sxs-lookup"><span data-stu-id="92af1-113">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92af1-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="92af1-114">Remarks</span></span>  

 <span data-ttu-id="92af1-115">Среда CLR получает указатель интерфейса на `IHostMalloc` экземпляр, вызывая метод [IHostMemoryManager:: CreateMalloc](ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="92af1-115">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92af1-116">Требования</span><span class="sxs-lookup"><span data-stu-id="92af1-116">Requirements</span></span>  

 <span data-ttu-id="92af1-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92af1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92af1-118">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="92af1-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92af1-119">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92af1-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92af1-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92af1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92af1-121">См. также</span><span class="sxs-lookup"><span data-stu-id="92af1-121">See also</span></span>

- [<span data-ttu-id="92af1-122">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="92af1-122">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="92af1-123">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="92af1-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
