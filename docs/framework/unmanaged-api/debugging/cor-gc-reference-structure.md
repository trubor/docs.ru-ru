---
description: 'Дополнительные сведения: структура COR_GC_REFERENCE'
title: Структура COR_GC_REFERENCE
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
ms.openlocfilehash: 38518bb1eb870081621bf32af9e63cdaa208dbd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801817"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="69725-103">Структура COR_GC_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="69725-103">COR_GC_REFERENCE Structure</span></span>

<span data-ttu-id="69725-104">Содержит сведения об объекте, в котором должна быть выполнена сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="69725-104">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69725-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="69725-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="69725-106">Члены</span><span class="sxs-lookup"><span data-stu-id="69725-106">Members</span></span>  
  
|<span data-ttu-id="69725-107">Член</span><span class="sxs-lookup"><span data-stu-id="69725-107">Member</span></span>|<span data-ttu-id="69725-108">Описание</span><span class="sxs-lookup"><span data-stu-id="69725-108">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="69725-109">Указатель на домен приложения, которому принадлежит маркер или объект.</span><span class="sxs-lookup"><span data-stu-id="69725-109">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="69725-110">Его значение может быть `null` .</span><span class="sxs-lookup"><span data-stu-id="69725-110">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="69725-111">Интерфейс ICorDebugValue или ICorDebugReferenceValue, соответствующий объекту, который должен быть собран сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="69725-111">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="69725-112">Значение перечисления [CorGCReferenceType](corgcreferencetype-enumeration.md) , указывающее, откуда поступил корень.</span><span class="sxs-lookup"><span data-stu-id="69725-112">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="69725-113">Дополнительные сведения см. в разделе «Примечания».</span><span class="sxs-lookup"><span data-stu-id="69725-113">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="69725-114">Дополнительные данные об объекте, который должен быть собран сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="69725-114">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="69725-115">Эти сведения зависят от источника объекта, как указано в `type` поле.</span><span class="sxs-lookup"><span data-stu-id="69725-115">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="69725-116">Дополнительные сведения см. в разделе «Примечания».</span><span class="sxs-lookup"><span data-stu-id="69725-116">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69725-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="69725-117">Remarks</span></span>  

 <span data-ttu-id="69725-118">`type`Поле является значением перечисления [CorGCReferenceType](corgcreferencetype-enumeration.md) , которое указывает, откуда поступила ссылка.</span><span class="sxs-lookup"><span data-stu-id="69725-118">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="69725-119">Конкретное `COR_GC_REFERENCE` значение может отражать любой из следующих видов управляемых объектов:</span><span class="sxs-lookup"><span data-stu-id="69725-119">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="69725-120">Объекты из всех управляемых стеков ( `CorGCReferenceType.CorReferenceStack` ).</span><span class="sxs-lookup"><span data-stu-id="69725-120">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="69725-121">Сюда входят динамические ссылки в управляемом коде, а также объекты, созданные средой CLR.</span><span class="sxs-lookup"><span data-stu-id="69725-121">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="69725-122">Объекты из таблицы Handle ( `CorGCReferenceType.CorHandle*` ).</span><span class="sxs-lookup"><span data-stu-id="69725-122">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="69725-123">Это включает в себя строгие ссылки ( `HNDTYPE_STRONG` и `HNDTYPE_REFCOUNT` ) и статические переменные в модуле.</span><span class="sxs-lookup"><span data-stu-id="69725-123">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="69725-124">Объекты из очереди метода завершения ( `CorGCReferenceType.CorReferenceFinalizer` ).</span><span class="sxs-lookup"><span data-stu-id="69725-124">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="69725-125">Очередь метода завершения помещает объекты в корни до запуска метода завершения.</span><span class="sxs-lookup"><span data-stu-id="69725-125">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="69725-126">`extraData`Поле содержит дополнительные данные в зависимости от источника (или типа) ссылки.</span><span class="sxs-lookup"><span data-stu-id="69725-126">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="69725-127">Доступны следующие значения:</span><span class="sxs-lookup"><span data-stu-id="69725-127">Possible values are:</span></span>  
  
- <span data-ttu-id="69725-128">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="69725-128">`DependentSource`.</span></span> <span data-ttu-id="69725-129">Если `type` имеет значение `CorGCREferenceType.CorHandleStrongDependent` , то это поле является объектом, в котором в случае со сроком существования объект, который должен быть собран в мусор, находится в корне `COR_GC_REFERENCE.Location` .</span><span class="sxs-lookup"><span data-stu-id="69725-129">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="69725-130">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="69725-130">`RefCount`.</span></span> <span data-ttu-id="69725-131">Если значение `type` равно `CorGCREferenceType.CorHandleStrongRefCount` , это поле представляет собой счетчик ссылок для маркера.</span><span class="sxs-lookup"><span data-stu-id="69725-131">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="69725-132">`Size`.</span><span class="sxs-lookup"><span data-stu-id="69725-132">`Size`.</span></span> <span data-ttu-id="69725-133">Если значение `type` равно `CorGCREferenceType.CorHandleStrongSizedByref` , это поле является последним размером дерева объектов, для которого сборщик мусора вычисляет корни объекта.</span><span class="sxs-lookup"><span data-stu-id="69725-133">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="69725-134">Обратите внимание, что это вычисление не обязательно в актуальном состоянии.</span><span class="sxs-lookup"><span data-stu-id="69725-134">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69725-135">Требования</span><span class="sxs-lookup"><span data-stu-id="69725-135">Requirements</span></span>  

 <span data-ttu-id="69725-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69725-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69725-137">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69725-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69725-138">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69725-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69725-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69725-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69725-140">См. также</span><span class="sxs-lookup"><span data-stu-id="69725-140">See also</span></span>

- [<span data-ttu-id="69725-141">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="69725-141">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="69725-142">Отладка</span><span class="sxs-lookup"><span data-stu-id="69725-142">Debugging</span></span>](index.md)
