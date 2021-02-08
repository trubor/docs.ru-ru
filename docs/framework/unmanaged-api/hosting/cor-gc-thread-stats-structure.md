---
description: 'Дополнительные сведения: структура COR_GC_THREAD_STATS'
title: Структура COR_GC_THREAD_STATS
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 179eb335e9f8c118ee98d4b777c347f3758ee0c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799789"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="592d3-103">Структура COR_GC_THREAD_STATS</span><span class="sxs-lookup"><span data-stu-id="592d3-103">COR_GC_THREAD_STATS Structure</span></span>

<span data-ttu-id="592d3-104">Содержит статистику по каждому потоку, относящуюся к сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="592d3-104">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="592d3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="592d3-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="592d3-106">Члены</span><span class="sxs-lookup"><span data-stu-id="592d3-106">Members</span></span>  
  
|<span data-ttu-id="592d3-107">Член</span><span class="sxs-lookup"><span data-stu-id="592d3-107">Member</span></span>|<span data-ttu-id="592d3-108">Описание</span><span class="sxs-lookup"><span data-stu-id="592d3-108">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="592d3-109">Число байтов памяти, выделенных в потоке, связанном с текущим `COR_GC_THREAD_STATS` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="592d3-109">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="592d3-110">Это число сбрасывается в ноль каждый раз, когда происходит сборка мусора нулевого поколения.</span><span class="sxs-lookup"><span data-stu-id="592d3-110">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="592d3-111">Число байтов, преобразованных в более высокое поколение при последней сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="592d3-111">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="592d3-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="592d3-112">Remarks</span></span>  

 <span data-ttu-id="592d3-113">[ICLRTask:: жетмемстатс](iclrtask-getmemstats-method.md) принимает выходной параметр типа `COR_GC_THREAD_STATS` .</span><span class="sxs-lookup"><span data-stu-id="592d3-113">[ICLRTask::GetMemStats](iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="592d3-114">Требования</span><span class="sxs-lookup"><span data-stu-id="592d3-114">Requirements</span></span>  

 <span data-ttu-id="592d3-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="592d3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="592d3-116">**Заголовок:** Гчост. idl</span><span class="sxs-lookup"><span data-stu-id="592d3-116">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="592d3-117">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="592d3-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="592d3-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="592d3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="592d3-119">См. также</span><span class="sxs-lookup"><span data-stu-id="592d3-119">See also</span></span>

- [<span data-ttu-id="592d3-120">Структуры размещения</span><span class="sxs-lookup"><span data-stu-id="592d3-120">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="592d3-121">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="592d3-121">IHostTask Interface</span></span>](ihosttask-interface.md)
