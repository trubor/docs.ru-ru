---
description: 'Дополнительные сведения о методе: IGCThreadControl:: Среадисблоккингфорсуспенсион'
title: Метод IGCThreadControl::ThreadIsBlockingForSuspension
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: 13023a75ab1c438abebbeb16fd9fe7c4b95c37ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709208"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="2bdaf-103">Метод IGCThreadControl::ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="2bdaf-103">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>

<span data-ttu-id="2bdaf-104">Уведомляет узел о том, что поток, выполняющий вызов, будет заблокирован, возможно, для сборки мусора или другой приостановки.</span><span class="sxs-lookup"><span data-stu-id="2bdaf-104">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bdaf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2bdaf-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="2bdaf-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="2bdaf-106">Remarks</span></span>  

 <span data-ttu-id="2bdaf-107">Основное приложение может выбрать в `ThreadIsBlockingForSuspension` обратном вызове, следует ли перепланировать поток.</span><span class="sxs-lookup"><span data-stu-id="2bdaf-107">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bdaf-108">Требования</span><span class="sxs-lookup"><span data-stu-id="2bdaf-108">Requirements</span></span>  

 <span data-ttu-id="2bdaf-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bdaf-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bdaf-110">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2bdaf-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2bdaf-111">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2bdaf-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bdaf-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bdaf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bdaf-113">См. также</span><span class="sxs-lookup"><span data-stu-id="2bdaf-113">See also</span></span>

- [<span data-ttu-id="2bdaf-114">Интерфейс IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="2bdaf-114">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
