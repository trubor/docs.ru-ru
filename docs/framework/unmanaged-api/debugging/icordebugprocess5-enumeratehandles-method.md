---
description: 'Дополнительные сведения о методе: метод ICorDebugProcess5:: EnumerateHandles'
title: Метод ICorDebugProcess5::EnumerateHandles
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
ms.openlocfilehash: 62ca1390ceec634e6651dc013345688fe5892bcd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649914"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="82874-103">Метод ICorDebugProcess5::EnumerateHandles</span><span class="sxs-lookup"><span data-stu-id="82874-103">ICorDebugProcess5::EnumerateHandles Method</span></span>

<span data-ttu-id="82874-104">Возвращает перечислитель для дескрипторов объектов в процессе.</span><span class="sxs-lookup"><span data-stu-id="82874-104">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82874-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="82874-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82874-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="82874-106">Parameters</span></span>  

 `types`  
 <span data-ttu-id="82874-107">окне Побитовое сочетание значений [CorGCReferenceType](corgcreferencetype-enumeration.md) , определяющих тип дескрипторов, включаемых в коллекцию.</span><span class="sxs-lookup"><span data-stu-id="82874-107">[in] A bitwise combination of [CorGCReferenceType](corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="82874-108">заполняет Указатель на адрес [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) , который является перечислителем для объектов, которые должны быть собраны в мусор.</span><span class="sxs-lookup"><span data-stu-id="82874-108">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82874-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="82874-109">Remarks</span></span>  

 <span data-ttu-id="82874-110">`EnumerateHandles` — Это вспомогательная функция, которая поддерживает проверку таблицы Handle.</span><span class="sxs-lookup"><span data-stu-id="82874-110">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="82874-111">Он похож на метод [метод ICorDebugProcess5:: енумератегкреференцес](icordebugprocess5-enumerategcreferences-method.md) , за исключением того, что вместо заполнения коллекции [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) всеми объектами, которые должны быть собраны сборщиком мусора, он включает только объекты, имеющие дескрипторы из таблицы дескрипторов.</span><span class="sxs-lookup"><span data-stu-id="82874-111">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="82874-112">`types`Параметр задает типы обработчиков для включения в коллекцию.</span><span class="sxs-lookup"><span data-stu-id="82874-112">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="82874-113">`types` может быть любым из следующих трех членов перечисления [CorGCReferenceType](corgcreferencetype-enumeration.md) :</span><span class="sxs-lookup"><span data-stu-id="82874-113">`types` can be any of the following three members of the [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="82874-114">`CorHandleStrongOnly` (обрабатывает только строгие ссылки).</span><span class="sxs-lookup"><span data-stu-id="82874-114">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="82874-115">`CorHandleWeakOnly` (дескрипторы только для слабых ссылок).</span><span class="sxs-lookup"><span data-stu-id="82874-115">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="82874-116">`CorHandleAll` (все дескрипторы).</span><span class="sxs-lookup"><span data-stu-id="82874-116">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82874-117">Требования</span><span class="sxs-lookup"><span data-stu-id="82874-117">Requirements</span></span>  

 <span data-ttu-id="82874-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82874-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82874-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82874-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82874-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82874-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82874-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82874-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82874-122">См. также</span><span class="sxs-lookup"><span data-stu-id="82874-122">See also</span></span>

- [<span data-ttu-id="82874-123">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="82874-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="82874-124">Отладка</span><span class="sxs-lookup"><span data-stu-id="82874-124">Debugging</span></span>](index.md)
