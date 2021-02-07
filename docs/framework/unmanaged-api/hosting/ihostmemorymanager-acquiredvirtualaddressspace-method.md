---
description: 'Дополнительные сведения о методе: IHostMemoryManager:: Аккуиредвиртуаладдрессспаце'
title: Метод IHostMemoryManager::AcquiredVirtualAddressSpace
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
ms.openlocfilehash: 70424c5bf907cfc3fb2e8951464335323f9331f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707921"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="42798-103">Метод IHostMemoryManager::AcquiredVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="42798-103">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>

<span data-ttu-id="42798-104">Уведомляет узел о том, что среда CLR получила указанную память из операционной системы.</span><span class="sxs-lookup"><span data-stu-id="42798-104">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42798-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="42798-105">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42798-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="42798-106">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="42798-107">окне Начальный адрес памяти.</span><span class="sxs-lookup"><span data-stu-id="42798-107">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="42798-108">окне Размер памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="42798-108">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42798-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="42798-109">Remarks</span></span>  

 <span data-ttu-id="42798-110">`AcquiredVirtualAddressSpace`Метод является методом обратного вызова и должен быть реализован модулем записи размещающего приложения.</span><span class="sxs-lookup"><span data-stu-id="42798-110">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="42798-111">Он вызывается средой CLR.</span><span class="sxs-lookup"><span data-stu-id="42798-111">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42798-112">Требования</span><span class="sxs-lookup"><span data-stu-id="42798-112">Requirements</span></span>  

 <span data-ttu-id="42798-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42798-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42798-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="42798-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42798-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42798-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42798-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42798-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42798-117">См. также</span><span class="sxs-lookup"><span data-stu-id="42798-117">See also</span></span>

- [<span data-ttu-id="42798-118">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="42798-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
