---
description: 'Дополнительные сведения о методе: IGCHost:: GetThreadStats'
title: Метод IGCHost::GetThreadStats
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
ms.openlocfilehash: 2d923560e915a0c88035caad70ad91149d793cb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709663"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="dfa0a-103">Метод IGCHost::GetThreadStats</span><span class="sxs-lookup"><span data-stu-id="dfa0a-103">IGCHost::GetThreadStats Method</span></span>

<span data-ttu-id="dfa0a-104">Возвращает статистику по потокам для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="dfa0a-104">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa0a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dfa0a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfa0a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dfa0a-106">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="dfa0a-107">окне Указатель на волокный файл cookie, указывающий поток, для которого необходимо получить статистику.</span><span class="sxs-lookup"><span data-stu-id="dfa0a-107">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="dfa0a-108">[вход, выход] Указатель на структуру [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) , содержащую статистику сборки мусора для указанного потока.</span><span class="sxs-lookup"><span data-stu-id="dfa0a-108">[in, out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa0a-109">Требования</span><span class="sxs-lookup"><span data-stu-id="dfa0a-109">Requirements</span></span>  

 <span data-ttu-id="dfa0a-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfa0a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfa0a-111">**Заголовок:** Гчост. idl, Гчост. h</span><span class="sxs-lookup"><span data-stu-id="dfa0a-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="dfa0a-112">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dfa0a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfa0a-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfa0a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa0a-114">См. также</span><span class="sxs-lookup"><span data-stu-id="dfa0a-114">See also</span></span>

- [<span data-ttu-id="dfa0a-115">Интерфейс IGCHost</span><span class="sxs-lookup"><span data-stu-id="dfa0a-115">IGCHost Interface</span></span>](igchost-interface.md)
