---
description: 'Дополнительные сведения о методе: ICorConfiguration:: Сетгксреадконтрол'
title: Метод ICorConfiguration::SetGCThreadControl
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
ms.openlocfilehash: 8b9388bdefb9da2ce51b62ab68eeee54645e43ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636647"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="14e54-103">Метод ICorConfiguration::SetGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="14e54-103">ICorConfiguration::SetGCThreadControl Method</span></span>

<span data-ttu-id="14e54-104">Задает интерфейс обратного вызова для потоков планирования для задач, не относящихся к среде выполнения, которые в противном случае были бы заблокированы для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="14e54-104">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14e54-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="14e54-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14e54-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="14e54-106">Parameters</span></span>  

 `pGCThreadControl`  
 <span data-ttu-id="14e54-107">окне Указатель на объект [IGCThreadControl](igcthreadcontrol-interface.md) , который уведомляет основное приложение о приостановке потоков для задач, не относящихся к среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="14e54-107">[in] A pointer to an [IGCThreadControl](igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14e54-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="14e54-108">Remarks</span></span>  

 <span data-ttu-id="14e54-109">Узел может выбрать один из обратных вызовов [IGCThreadControl:: среадисблоккингфорсуспенсион](igcthreadcontrol-threadisblockingforsuspension-method.md) , следует ли перепланировать поток.</span><span class="sxs-lookup"><span data-stu-id="14e54-109">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14e54-110">Требования</span><span class="sxs-lookup"><span data-stu-id="14e54-110">Requirements</span></span>  

 <span data-ttu-id="14e54-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14e54-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14e54-112">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="14e54-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14e54-113">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="14e54-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14e54-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14e54-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e54-115">См. также</span><span class="sxs-lookup"><span data-stu-id="14e54-115">See also</span></span>

- [<span data-ttu-id="14e54-116">Интерфейс ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="14e54-116">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
