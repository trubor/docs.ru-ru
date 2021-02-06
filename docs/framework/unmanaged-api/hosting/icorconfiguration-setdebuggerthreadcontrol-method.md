---
description: 'Дополнительные сведения о методе: ICorConfiguration:: Setdebuggerthreadcontrol-'
title: Метод ICorConfiguration::SetDebuggerThreadControl
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
ms.openlocfilehash: 9bf024f3feb6df44a94f8a5f1a626bb6e0c91d31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636667"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="94500-103">Метод ICorConfiguration::SetDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="94500-103">ICorConfiguration::SetDebuggerThreadControl Method</span></span>

<span data-ttu-id="94500-104">Задает интерфейс обратного вызова, который службы отладки будут вызывать, так как потоки среды CLR блокируются и разблокируются для отладки.</span><span class="sxs-lookup"><span data-stu-id="94500-104">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94500-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="94500-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94500-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="94500-106">Parameters</span></span>  

 `pDebuggerThreadControl`  
 <span data-ttu-id="94500-107">окне Указатель на объект [идебугжерсреадконтрол](idebuggerthreadcontrol-interface.md) , который уведомляет узел о блокировании и разблокировке потоков службами отладки.</span><span class="sxs-lookup"><span data-stu-id="94500-107">[in] A pointer to an [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94500-108">Требования</span><span class="sxs-lookup"><span data-stu-id="94500-108">Requirements</span></span>  

 <span data-ttu-id="94500-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94500-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94500-110">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="94500-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94500-111">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="94500-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94500-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94500-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94500-113">См. также</span><span class="sxs-lookup"><span data-stu-id="94500-113">See also</span></span>

- [<span data-ttu-id="94500-114">Интерфейс ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="94500-114">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
