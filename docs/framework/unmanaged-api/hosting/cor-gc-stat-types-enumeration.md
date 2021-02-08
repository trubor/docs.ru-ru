---
description: 'Дополнительные сведения: перечисление COR_GC_STAT_TYPES'
title: Перечисление COR_GC_STAT_TYPES
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: c4ea3175c777d49a5d6cffdf506f42e479784971
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799813"
---
# <a name="cor_gc_stat_types-enumeration"></a><span data-ttu-id="2246d-103">Перечисление COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="2246d-103">COR_GC_STAT_TYPES Enumeration</span></span>

<span data-ttu-id="2246d-104">Указывает статистику, записываемую для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="2246d-104">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2246d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2246d-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="2246d-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="2246d-106">Remarks</span></span>  

 <span data-ttu-id="2246d-107">Это перечисление указывает, какая статистика в структуре [COR_GC_STATS](cor-gc-stats-structure.md) должна быть задана методом [Иклргкманажер:: stats](iclrgcmanager-getstats-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2246d-107">This enumeration specifies which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="2246d-108">Элементы</span><span class="sxs-lookup"><span data-stu-id="2246d-108">Members</span></span>  
  
|<span data-ttu-id="2246d-109">Член</span><span class="sxs-lookup"><span data-stu-id="2246d-109">Member</span></span>|<span data-ttu-id="2246d-110">Описание</span><span class="sxs-lookup"><span data-stu-id="2246d-110">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="2246d-111">Записывает количество сборок мусора, выполненных для каждого поколения.</span><span class="sxs-lookup"><span data-stu-id="2246d-111">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="2246d-112">Записывает статистику использования памяти и размера сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="2246d-112">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2246d-113">Требования</span><span class="sxs-lookup"><span data-stu-id="2246d-113">Requirements</span></span>  

 <span data-ttu-id="2246d-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2246d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2246d-115">**Заголовок:** Гчост. idl, Гчост. h</span><span class="sxs-lookup"><span data-stu-id="2246d-115">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="2246d-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2246d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2246d-117">См. также</span><span class="sxs-lookup"><span data-stu-id="2246d-117">See also</span></span>

- [<span data-ttu-id="2246d-118">Структура COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="2246d-118">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="2246d-119">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="2246d-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
