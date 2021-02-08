---
description: 'Дополнительные сведения о методе: Идебугжерсреадконтрол:: Среадисблоккингфордебугжер'
title: Метод IDebuggerThreadControl::ThreadIsBlockingForDebugger
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
ms.openlocfilehash: 0fa96b2e36ea6653e1698dd32fa1e73d223afb94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789519"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="2af91-103">Метод IDebuggerThreadControl::ThreadIsBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="2af91-103">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>

<span data-ttu-id="2af91-104">Уведомляет узел о том, что поток, отправляющий этот обратный вызов, будет заблокирован в службах отладки.</span><span class="sxs-lookup"><span data-stu-id="2af91-104">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af91-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2af91-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="2af91-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="2af91-106">Remarks</span></span>  

 <span data-ttu-id="2af91-107">`ThreadIsBlockingForDebugger`Метод всегда будет вызываться в потоке среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="2af91-107">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="2af91-108">`ThreadIsBlockingForDebugger`Метод дает узлу возможность выполнить еще одно действие, пока блокируется поток.</span><span class="sxs-lookup"><span data-stu-id="2af91-108">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2af91-109">Требования</span><span class="sxs-lookup"><span data-stu-id="2af91-109">Requirements</span></span>  

 <span data-ttu-id="2af91-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2af91-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2af91-111">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2af91-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2af91-112">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2af91-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2af91-113">**Версии .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2af91-113">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af91-114">См. также</span><span class="sxs-lookup"><span data-stu-id="2af91-114">See also</span></span>

- [<span data-ttu-id="2af91-115">Интерфейс IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="2af91-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
