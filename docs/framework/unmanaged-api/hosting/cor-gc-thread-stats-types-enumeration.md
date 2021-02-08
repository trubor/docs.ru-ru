---
description: 'Дополнительные сведения: перечисление COR_GC_THREAD_STATS_TYPES'
title: Перечисление COR_GC_THREAD_STATS_TYPES
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS_TYPES
helpviewer_keywords:
- COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type:
- apiref
ms.openlocfilehash: 04bc4e11c527b83cf5f1384b1092cc0d084008a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799776"
---
# <a name="cor_gc_thread_stats_types-enumeration"></a><span data-ttu-id="6f5d7-103">Перечисление COR_GC_THREAD_STATS_TYPES</span><span class="sxs-lookup"><span data-stu-id="6f5d7-103">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>

<span data-ttu-id="6f5d7-104">Указывает статистику сборки мусора для потока.</span><span class="sxs-lookup"><span data-stu-id="6f5d7-104">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f5d7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6f5d7-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="6f5d7-106">Члены</span><span class="sxs-lookup"><span data-stu-id="6f5d7-106">Members</span></span>  
  
|<span data-ttu-id="6f5d7-107">Член</span><span class="sxs-lookup"><span data-stu-id="6f5d7-107">Member</span></span>|<span data-ttu-id="6f5d7-108">Описание</span><span class="sxs-lookup"><span data-stu-id="6f5d7-108">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="6f5d7-109">Поток содержит байты, которые были повышены в последней сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="6f5d7-109">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f5d7-110">Требования</span><span class="sxs-lookup"><span data-stu-id="6f5d7-110">Requirements</span></span>  

 <span data-ttu-id="6f5d7-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f5d7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f5d7-112">**Заголовок:** Гчост. idl, Гчост. h</span><span class="sxs-lookup"><span data-stu-id="6f5d7-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="6f5d7-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f5d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f5d7-114">См. также</span><span class="sxs-lookup"><span data-stu-id="6f5d7-114">See also</span></span>

- [<span data-ttu-id="6f5d7-115">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="6f5d7-115">Hosting Enumerations</span></span>](hosting-enumerations.md)
