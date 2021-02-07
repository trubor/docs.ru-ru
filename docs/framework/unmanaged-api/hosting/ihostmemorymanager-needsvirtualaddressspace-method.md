---
description: 'Дополнительные сведения о методе: IHostMemoryManager:: NeedsVirtualAddressSpace'
title: Метод IHostMemoryManager::NeedsVirtualAddressSpace
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
ms.openlocfilehash: 95d4128decffc82fdcb198155b48a31420f71220
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707791"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="4e4d7-103">Метод IHostMemoryManager::NeedsVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="4e4d7-103">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>

<span data-ttu-id="4e4d7-104">Уведомляет узел о том, что среда CLR будет пытаться использовать указанную память.</span><span class="sxs-lookup"><span data-stu-id="4e4d7-104">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e4d7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4e4d7-105">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e4d7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4e4d7-106">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="4e4d7-107">окне Начальный адрес памяти.</span><span class="sxs-lookup"><span data-stu-id="4e4d7-107">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="4e4d7-108">окне Размер памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="4e4d7-108">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e4d7-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="4e4d7-109">Remarks</span></span>  

 <span data-ttu-id="4e4d7-110">`NeedsVirtualAddressSpace`Метод является методом обратного вызова и должен быть реализован модулем записи размещающего приложения.</span><span class="sxs-lookup"><span data-stu-id="4e4d7-110">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="4e4d7-111">Он вызывается средой CLR.</span><span class="sxs-lookup"><span data-stu-id="4e4d7-111">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="4e4d7-112">Если узел не хочет, чтобы среда CLR использовала указанную память, она может вернуть E_OUTOFMEMORY HRESULT.</span><span class="sxs-lookup"><span data-stu-id="4e4d7-112">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e4d7-113">Требования</span><span class="sxs-lookup"><span data-stu-id="4e4d7-113">Requirements</span></span>  

 <span data-ttu-id="4e4d7-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e4d7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e4d7-115">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4e4d7-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e4d7-116">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4e4d7-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e4d7-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e4d7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e4d7-118">См. также</span><span class="sxs-lookup"><span data-stu-id="4e4d7-118">See also</span></span>

- [<span data-ttu-id="4e4d7-119">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="4e4d7-119">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
