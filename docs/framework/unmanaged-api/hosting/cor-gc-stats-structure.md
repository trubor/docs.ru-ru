---
description: 'Дополнительные сведения: структура COR_GC_STATS'
title: Структура COR_GC_STATS
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
ms.openlocfilehash: 9b1002f462fb9b447e521cd1b3e5c78297eefc04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799812"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="78e04-103">Структура COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="78e04-103">COR_GC_STATS Structure</span></span>

<span data-ttu-id="78e04-104">Содержит статистические данные о механизме сборки мусора среды CLR.</span><span class="sxs-lookup"><span data-stu-id="78e04-104">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78e04-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="78e04-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="78e04-106">Члены</span><span class="sxs-lookup"><span data-stu-id="78e04-106">Members</span></span>  
  
|<span data-ttu-id="78e04-107">Член</span><span class="sxs-lookup"><span data-stu-id="78e04-107">Member</span></span>|<span data-ttu-id="78e04-108">Описание</span><span class="sxs-lookup"><span data-stu-id="78e04-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="78e04-109">Указывает, какие значения полей должны вычисляться и возвращаться.</span><span class="sxs-lookup"><span data-stu-id="78e04-109">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="78e04-110">Указывает количество сборок мусора, принудительно выполненных внешним запросом.</span><span class="sxs-lookup"><span data-stu-id="78e04-110">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="78e04-111">Указывает количество сборок мусора, выполненных для каждого поколения.</span><span class="sxs-lookup"><span data-stu-id="78e04-111">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="78e04-112">Общее число килобайтов, зафиксированных во всех кучах.</span><span class="sxs-lookup"><span data-stu-id="78e04-112">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="78e04-113">Общее количество килобайтов, зарезервированных во всех кучах.</span><span class="sxs-lookup"><span data-stu-id="78e04-113">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="78e04-114">Размер кучи нулевого поколения (в килобайтах).</span><span class="sxs-lookup"><span data-stu-id="78e04-114">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="78e04-115">Размер кучи поколения (в килобайтах).</span><span class="sxs-lookup"><span data-stu-id="78e04-115">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="78e04-116">Размер кучи второго поколения (в килобайтах).</span><span class="sxs-lookup"><span data-stu-id="78e04-116">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="78e04-117">Размер кучи больших объектов (в килобайтах).</span><span class="sxs-lookup"><span data-stu-id="78e04-117">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="78e04-118">Размер (в килобайтах) объектов, перешедших из поколения 0 в поколение.</span><span class="sxs-lookup"><span data-stu-id="78e04-118">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="78e04-119">Размер (в килобайтах) объектов, перешедших из поколения 1 в поколение 2.</span><span class="sxs-lookup"><span data-stu-id="78e04-119">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78e04-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="78e04-120">Remarks</span></span>  

 <span data-ttu-id="78e04-121">Метод [иклргкманажер:: stats](iclrgcmanager-getstats-method.md) требует, чтобы `Flags` поле `COR_GC_STATS` структуры было установлено в одно или несколько значений перечисления [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) , чтобы указать, какую статистику следует задать.</span><span class="sxs-lookup"><span data-stu-id="78e04-121">The [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="78e04-122">Следующая таблица сопоставляет статистические данные, предоставленные этой структурой, с двумя значениями перечисления [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) `COR_GC_COUNTS` и `COR_GC_MEMORYUSAGE` .</span><span class="sxs-lookup"><span data-stu-id="78e04-122">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="78e04-123">Задается COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="78e04-123">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="78e04-124">Задается COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="78e04-124">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="78e04-125">Пример использования таков:</span><span class="sxs-lookup"><span data-stu-id="78e04-125">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="78e04-126">Требования</span><span class="sxs-lookup"><span data-stu-id="78e04-126">Requirements</span></span>  

 <span data-ttu-id="78e04-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78e04-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78e04-128">**Заголовок:** Гчост. idl</span><span class="sxs-lookup"><span data-stu-id="78e04-128">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="78e04-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78e04-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78e04-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78e04-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e04-131">См. также</span><span class="sxs-lookup"><span data-stu-id="78e04-131">See also</span></span>

- [<span data-ttu-id="78e04-132">Структуры размещения</span><span class="sxs-lookup"><span data-stu-id="78e04-132">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="78e04-133">Автоматическое управление памятью</span><span class="sxs-lookup"><span data-stu-id="78e04-133">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="78e04-134">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="78e04-134">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
