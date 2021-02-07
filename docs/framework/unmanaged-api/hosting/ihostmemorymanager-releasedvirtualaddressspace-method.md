---
description: 'Дополнительные сведения о методе: IHostMemoryManager:: Релеаседвиртуаладдрессспаце'
title: Метод IHostMemoryManager::ReleasedVirtualAddressSpace
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
ms.openlocfilehash: e67e80018b5002bdf2a50530af9ab057696fff4c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707778"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="0c3ee-103">Метод IHostMemoryManager::ReleasedVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="0c3ee-103">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>

<span data-ttu-id="0c3ee-104">Уведомляет узел о том, что среда CLR завершила работу с заданной памятью.</span><span class="sxs-lookup"><span data-stu-id="0c3ee-104">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c3ee-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0c3ee-105">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c3ee-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0c3ee-106">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="0c3ee-107">окне Указатель на начальный адрес памяти для освобождения.</span><span class="sxs-lookup"><span data-stu-id="0c3ee-107">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c3ee-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="0c3ee-108">Remarks</span></span>  

 <span data-ttu-id="0c3ee-109">`ReleasedVirtualAddressSpace`Метод является методом обратного вызова и должен быть реализован модулем записи размещающего приложения.</span><span class="sxs-lookup"><span data-stu-id="0c3ee-109">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="0c3ee-110">Он вызывается средой CLR.</span><span class="sxs-lookup"><span data-stu-id="0c3ee-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c3ee-111">Требования</span><span class="sxs-lookup"><span data-stu-id="0c3ee-111">Requirements</span></span>  

 <span data-ttu-id="0c3ee-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c3ee-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c3ee-113">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0c3ee-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c3ee-114">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c3ee-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c3ee-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c3ee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c3ee-116">См. также</span><span class="sxs-lookup"><span data-stu-id="0c3ee-116">See also</span></span>

- [<span data-ttu-id="0c3ee-117">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="0c3ee-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
