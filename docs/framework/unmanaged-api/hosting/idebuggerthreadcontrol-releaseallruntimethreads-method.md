---
description: 'Дополнительные сведения о методе: Идебугжерсреадконтрол:: Релеасеаллрунтимесреадс'
title: Метод IDebuggerThreadControl::ReleaseAllRuntimeThreads
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
ms.openlocfilehash: bf551ccc2ae5bde3333dc8e3957099590a494dd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709793"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="c0b05-103">Метод IDebuggerThreadControl::ReleaseAllRuntimeThreads</span><span class="sxs-lookup"><span data-stu-id="c0b05-103">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>

<span data-ttu-id="c0b05-104">Уведомляет узел о том, что службы отладки собирается освободить все заблокированные потоки.</span><span class="sxs-lookup"><span data-stu-id="c0b05-104">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0b05-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c0b05-105">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="c0b05-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="c0b05-106">Remarks</span></span>  

 <span data-ttu-id="c0b05-107">`ReleaseAllRuntimeThreads`Метод никогда не будет вызываться в потоке среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="c0b05-107">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="c0b05-108">Если в узле заблокирован поток среды выполнения, он должен освободить его сейчас.</span><span class="sxs-lookup"><span data-stu-id="c0b05-108">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0b05-109">Требования</span><span class="sxs-lookup"><span data-stu-id="c0b05-109">Requirements</span></span>  

 <span data-ttu-id="c0b05-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0b05-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0b05-111">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c0b05-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c0b05-112">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0b05-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0b05-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0b05-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b05-114">См. также</span><span class="sxs-lookup"><span data-stu-id="c0b05-114">See also</span></span>

- [<span data-ttu-id="c0b05-115">Интерфейс IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="c0b05-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
