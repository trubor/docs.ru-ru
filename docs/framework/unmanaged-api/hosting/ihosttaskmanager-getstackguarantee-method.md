---
description: 'Дополнительные сведения о методе: IHostTaskManager:: Жетстаккгуаранти'
title: Метод IHostTaskManager::GetStackGuarantee
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetStackGuarantee
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type:
- apiref
ms.openlocfilehash: 6c8bd9839ea0c1fdb72fbbd296061d1a2b6edfe1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753800"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="0a913-103">Метод IHostTaskManager::GetStackGuarantee</span><span class="sxs-lookup"><span data-stu-id="0a913-103">IHostTaskManager::GetStackGuarantee Method</span></span>

<span data-ttu-id="0a913-104">Возвращает объем стекового пространства, который гарантированно будет доступен после завершения операции с стеком, но до закрытия процесса.</span><span class="sxs-lookup"><span data-stu-id="0a913-104">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a913-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0a913-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a913-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0a913-106">Parameters</span></span>  

 `pGuarantee`  
 <span data-ttu-id="0a913-107">заполняет Указатель на количество доступных байтов.</span><span class="sxs-lookup"><span data-stu-id="0a913-107">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a913-108">Требования</span><span class="sxs-lookup"><span data-stu-id="0a913-108">Requirements</span></span>  

 <span data-ttu-id="0a913-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a913-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a913-110">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0a913-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a913-111">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a913-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a913-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a913-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a913-113">См. также</span><span class="sxs-lookup"><span data-stu-id="0a913-113">See also</span></span>

- [<span data-ttu-id="0a913-114">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="0a913-114">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
