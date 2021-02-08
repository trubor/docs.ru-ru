---
description: Дополнительные сведения о перечислении CorGCReferenceType
title: Перечисление CorGCReferenceType
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
ms.openlocfilehash: a1f534f9fe4b9ba4ede0bef94f35cf1688fe1817
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801518"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="8682c-103">Перечисление CorGCReferenceType</span><span class="sxs-lookup"><span data-stu-id="8682c-103">CorGCReferenceType Enumeration</span></span>

<span data-ttu-id="8682c-104">Идентифицирует источник объекта, в котором должна быть выполнена сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="8682c-104">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8682c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8682c-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a><span data-ttu-id="8682c-106">Члены</span><span class="sxs-lookup"><span data-stu-id="8682c-106">Members</span></span>  
  
|<span data-ttu-id="8682c-107">Имя участника</span><span class="sxs-lookup"><span data-stu-id="8682c-107">Member name</span></span>|<span data-ttu-id="8682c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8682c-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="8682c-109">Дескриптор строгой ссылки из таблицы дескрипторов объектов.</span><span class="sxs-lookup"><span data-stu-id="8682c-109">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="8682c-110">Указатель на закрепленную строгую ссылку из таблицы обработчика объектов.</span><span class="sxs-lookup"><span data-stu-id="8682c-110">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="8682c-111">Указатель на слабую ссылку из таблицы обработчика объектов.</span><span class="sxs-lookup"><span data-stu-id="8682c-111">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="8682c-112">Указатель на слабый объект, подсчитанный по ссылке, из таблицы обработчика объектов.</span><span class="sxs-lookup"><span data-stu-id="8682c-112">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="8682c-113">Указатель на объект, подсчитанный по ссылке, из таблицы обработчика объектов.</span><span class="sxs-lookup"><span data-stu-id="8682c-113">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="8682c-114">Маркер зависимого объекта из таблицы обработчика объектов.</span><span class="sxs-lookup"><span data-stu-id="8682c-114">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="8682c-115">Асинхронный закрепленный объект из таблицы дескрипторов объектов.</span><span class="sxs-lookup"><span data-stu-id="8682c-115">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="8682c-116">Строгая ссылка, хранящая приблизительный размер общего закрытия всех объектов и корневых объектов во время сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="8682c-116">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="8682c-117">Ссылка из управляемого стека.</span><span class="sxs-lookup"><span data-stu-id="8682c-117">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="8682c-118">Ссылка из очереди метода завершения.</span><span class="sxs-lookup"><span data-stu-id="8682c-118">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="8682c-119">корхандлестронгонли</span><span class="sxs-lookup"><span data-stu-id="8682c-119">CorHandleStrongOnly</span></span>|<span data-ttu-id="8682c-120">Возвращать только строгие ссылки из таблицы Handle.</span><span class="sxs-lookup"><span data-stu-id="8682c-120">Return only strong references from the handle table.</span></span> <span data-ttu-id="8682c-121">Это значение используется только методом [метод ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8682c-121">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="8682c-122">Возвращать только слабые ссылки из таблицы Handle.</span><span class="sxs-lookup"><span data-stu-id="8682c-122">Return only weak references from the handle table.</span></span> <span data-ttu-id="8682c-123">Это значение используется только методом [метод ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8682c-123">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="8682c-124">Возвращает все ссылки из таблицы Handle.</span><span class="sxs-lookup"><span data-stu-id="8682c-124">Return all references from the handle table.</span></span> <span data-ttu-id="8682c-125">Это значение используется только методом [метод ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8682c-125">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8682c-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="8682c-126">Remarks</span></span>  

 <span data-ttu-id="8682c-127">`CorGCReferenceType`Перечисление используется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8682c-127">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
- <span data-ttu-id="8682c-128">В качестве значения `type` поля структуры [COR_GC_REFERENCE](cor-gc-reference-structure.md) указывает источник ссылки или маркера.</span><span class="sxs-lookup"><span data-stu-id="8682c-128">As the value of the `type` field of the [COR_GC_REFERENCE](cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
- <span data-ttu-id="8682c-129">В качестве `types` аргумента метода [метод ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) указывает типы дескрипторов, включаемых в перечисление.</span><span class="sxs-lookup"><span data-stu-id="8682c-129">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8682c-130">Требования</span><span class="sxs-lookup"><span data-stu-id="8682c-130">Requirements</span></span>  

 <span data-ttu-id="8682c-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8682c-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8682c-132">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8682c-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8682c-133">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8682c-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8682c-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8682c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8682c-135">См. также</span><span class="sxs-lookup"><span data-stu-id="8682c-135">See also</span></span>

- [<span data-ttu-id="8682c-136">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="8682c-136">Debugging Enumerations</span></span>](debugging-enumerations.md)
