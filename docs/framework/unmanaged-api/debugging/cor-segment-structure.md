---
description: 'Дополнительные сведения: структура COR_SEGMENT'
title: Структура COR_SEGMENT
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
ms.openlocfilehash: 9bbc452b2c2036d019175ac1be8b9917ffa07b6a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712198"
---
# <a name="cor_segment-structure"></a><span data-ttu-id="0b1ba-103">Структура COR_SEGMENT</span><span class="sxs-lookup"><span data-stu-id="0b1ba-103">COR_SEGMENT Structure</span></span>

<span data-ttu-id="0b1ba-104">Содержит сведения об области памяти в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="0b1ba-104">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b1ba-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0b1ba-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;
    CORDB_ADDRESS end;
    CorDebugGenerationTypes gen;
    ULONG heap;
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="0b1ba-106">Члены</span><span class="sxs-lookup"><span data-stu-id="0b1ba-106">Members</span></span>  
  
|<span data-ttu-id="0b1ba-107">Член</span><span class="sxs-lookup"><span data-stu-id="0b1ba-107">Member</span></span>|<span data-ttu-id="0b1ba-108">Описание</span><span class="sxs-lookup"><span data-stu-id="0b1ba-108">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="0b1ba-109">Начальный адрес области памяти.</span><span class="sxs-lookup"><span data-stu-id="0b1ba-109">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="0b1ba-110">Конечный адрес области памяти.</span><span class="sxs-lookup"><span data-stu-id="0b1ba-110">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="0b1ba-111">Элемент перечисления [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md), который указывает на создание области памяти.</span><span class="sxs-lookup"><span data-stu-id="0b1ba-111">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="0b1ba-112">Номер кучи, в которой находится область памяти.</span><span class="sxs-lookup"><span data-stu-id="0b1ba-112">The heap number in which the memory region resides.</span></span> <span data-ttu-id="0b1ba-113">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="0b1ba-113">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b1ba-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="0b1ba-114">Remarks</span></span>  

 <span data-ttu-id="0b1ba-115">Структура `COR_SEGMENTS` представляет область памяти в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="0b1ba-115">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="0b1ba-116">Объекты `COR_SEGMENTS` являются членами объекта коллекции [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md), которая заполняется путем вызова метода [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md).</span><span class="sxs-lookup"><span data-stu-id="0b1ba-116">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="0b1ba-117">В поле `heap` указан номер обработчика, который соответствует определенной куче.</span><span class="sxs-lookup"><span data-stu-id="0b1ba-117">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="0b1ba-118">Для сборщиков мусора на рабочей станции это значение всегда равно нулю, ведь на рабочих станциях только одна куча сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="0b1ba-118">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="0b1ba-119">Для сборщиков мусора на сервере это значение соответствует обработчику, к которому привязана куча.</span><span class="sxs-lookup"><span data-stu-id="0b1ba-119">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="0b1ba-120">Куч сборки мусора может быть больше или меньше фактического числа обработчиков в связи с особенностями реализации сборщика мусора.</span><span class="sxs-lookup"><span data-stu-id="0b1ba-120">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b1ba-121">Требования</span><span class="sxs-lookup"><span data-stu-id="0b1ba-121">Requirements</span></span>  

 <span data-ttu-id="0b1ba-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b1ba-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b1ba-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b1ba-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b1ba-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b1ba-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b1ba-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b1ba-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b1ba-126">См. также</span><span class="sxs-lookup"><span data-stu-id="0b1ba-126">See also</span></span>

- [<span data-ttu-id="0b1ba-127">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="0b1ba-127">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0b1ba-128">Отладка</span><span class="sxs-lookup"><span data-stu-id="0b1ba-128">Debugging</span></span>](index.md)
