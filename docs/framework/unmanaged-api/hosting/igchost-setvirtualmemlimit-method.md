---
description: 'Дополнительные сведения о методе: IGCHost:: Setvirtualmemlimit-'
title: Метод IGCHost::SetVirtualMemLimit
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
ms.openlocfilehash: 62cd9e2d84e51f0544e464bdbf49c50af8086546
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709442"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="097e2-103">Метод IGCHost::SetVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="097e2-103">IGCHost::SetVirtualMemLimit Method</span></span>

<span data-ttu-id="097e2-104">Задает максимальный размер виртуальной памяти среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="097e2-104">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="097e2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="097e2-105">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="097e2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="097e2-106">Parameters</span></span>  

 `sztMaxVirtualMemMB`  
 <span data-ttu-id="097e2-107">окне Максимальный размер виртуальной памяти среды выполнения в мегабайтах.</span><span class="sxs-lookup"><span data-stu-id="097e2-107">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="097e2-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="097e2-108">Remarks</span></span>  

 <span data-ttu-id="097e2-109">Максимальный размер виртуальной памяти среды выполнения можно изменить динамически.</span><span class="sxs-lookup"><span data-stu-id="097e2-109">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="097e2-110">Требования</span><span class="sxs-lookup"><span data-stu-id="097e2-110">Requirements</span></span>  

 <span data-ttu-id="097e2-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="097e2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="097e2-112">**Заголовок:** Гчост. idl, Гчост. h</span><span class="sxs-lookup"><span data-stu-id="097e2-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="097e2-113">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="097e2-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="097e2-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="097e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097e2-115">См. также</span><span class="sxs-lookup"><span data-stu-id="097e2-115">See also</span></span>

- [<span data-ttu-id="097e2-116">Интерфейс IGCHost</span><span class="sxs-lookup"><span data-stu-id="097e2-116">IGCHost Interface</span></span>](igchost-interface.md)
