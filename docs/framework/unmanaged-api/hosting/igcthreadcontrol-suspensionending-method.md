---
description: 'Дополнительные сведения о методе: IGCThreadControl:: SuspensionEnding'
title: Метод IGCThreadControl::SuspensionEnding
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
ms.openlocfilehash: 5ff889f45ea3664312060f373907e65c367276f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709273"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="99bec-103">Метод IGCThreadControl::SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="99bec-103">IGCThreadControl::SuspensionEnding Method</span></span>

<span data-ttu-id="99bec-104">Уведомляет узел о том, что среда выполнения возобновляет потоки после сборки мусора или другой приостановки.</span><span class="sxs-lookup"><span data-stu-id="99bec-104">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99bec-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="99bec-105">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99bec-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="99bec-106">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="99bec-107">окне Поколение, на котором была выполнена сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="99bec-107">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99bec-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="99bec-108">Remarks</span></span>  

 <span data-ttu-id="99bec-109">Не Перепланируйте потоки во время `SuspensionEnding` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="99bec-109">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99bec-110">Требования</span><span class="sxs-lookup"><span data-stu-id="99bec-110">Requirements</span></span>  

 <span data-ttu-id="99bec-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99bec-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99bec-112">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="99bec-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99bec-113">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99bec-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99bec-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99bec-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99bec-115">См. также</span><span class="sxs-lookup"><span data-stu-id="99bec-115">See also</span></span>

- [<span data-ttu-id="99bec-116">Интерфейс IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="99bec-116">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
