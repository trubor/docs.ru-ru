---
description: 'Дополнительные сведения о методе: IGCThreadControl:: SuspensionStarting'
title: Метод IGCThreadControl::SuspensionStarting
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
ms.openlocfilehash: b9d068e6995a73e9a9a31d5d5debf008f9748630
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709299"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="bd884-103">Метод IGCThreadControl::SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="bd884-103">IGCThreadControl::SuspensionStarting Method</span></span>

<span data-ttu-id="bd884-104">Уведомляет узел о том, что среда выполнения начинает приостановку потока для сборки мусора или другой приостановки.</span><span class="sxs-lookup"><span data-stu-id="bd884-104">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd884-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bd884-105">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd884-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="bd884-106">Remarks</span></span>  

 <span data-ttu-id="bd884-107">Не Перепланируйте потоки во время `SuspensionStarting` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="bd884-107">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd884-108">Требования</span><span class="sxs-lookup"><span data-stu-id="bd884-108">Requirements</span></span>  

 <span data-ttu-id="bd884-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd884-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd884-110">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bd884-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd884-111">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd884-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd884-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd884-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd884-113">См. также</span><span class="sxs-lookup"><span data-stu-id="bd884-113">See also</span></span>

- [<span data-ttu-id="bd884-114">Интерфейс IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="bd884-114">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
