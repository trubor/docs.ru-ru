---
description: 'Дополнительные сведения о методе: Игчостконтрол:: RequestVirtualMemLimit'
title: Метод IGCHostControl::RequestVirtualMemLimit
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
ms.openlocfilehash: b0ee22671b63be0ed0d23ebb103a6a5a7ca9f2b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709429"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="7d19f-103">Метод IGCHostControl::RequestVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="7d19f-103">IGCHostControl::RequestVirtualMemLimit Method</span></span>

<span data-ttu-id="7d19f-104">Запрашивает у узла изменение ограничений виртуальной памяти.</span><span class="sxs-lookup"><span data-stu-id="7d19f-104">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d19f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7d19f-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d19f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d19f-106">Parameters</span></span>  

 `sztMaxVirtualMemMB`  
 <span data-ttu-id="7d19f-107">окне Запрошенный размер выделенной памяти.</span><span class="sxs-lookup"><span data-stu-id="7d19f-107">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="7d19f-108">[вход, выход] Указатель на фактический размер выделенной памяти.</span><span class="sxs-lookup"><span data-stu-id="7d19f-108">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d19f-109">Требования</span><span class="sxs-lookup"><span data-stu-id="7d19f-109">Requirements</span></span>  

 <span data-ttu-id="7d19f-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d19f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d19f-111">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7d19f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d19f-112">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d19f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d19f-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d19f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d19f-114">См. также</span><span class="sxs-lookup"><span data-stu-id="7d19f-114">See also</span></span>

- [<span data-ttu-id="7d19f-115">Интерфейс IGCHostControl</span><span class="sxs-lookup"><span data-stu-id="7d19f-115">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)
