---
description: 'Дополнительные сведения: перечисление COR_PRF_GC_ROOT_FLAGS'
title: Перечисление COR_PRF_GC_ROOT_FLAGS
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
ms.openlocfilehash: 6d566ed5ac1d0b4e15a855fbbb8a0fca3a5a429e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648822"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a><span data-ttu-id="8d1f8-103">Перечисление COR_PRF_GC_ROOT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8d1f8-103">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>

<span data-ttu-id="8d1f8-104">Указывает свойство корня сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="8d1f8-104">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d1f8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8d1f8-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="8d1f8-106">Члены</span><span class="sxs-lookup"><span data-stu-id="8d1f8-106">Members</span></span>  
  
|<span data-ttu-id="8d1f8-107">Член</span><span class="sxs-lookup"><span data-stu-id="8d1f8-107">Member</span></span>|<span data-ttu-id="8d1f8-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8d1f8-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="8d1f8-109">Корень предотвращает перемещение объекта в сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="8d1f8-109">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="8d1f8-110">Корень не препятствует сбору мусора.</span><span class="sxs-lookup"><span data-stu-id="8d1f8-110">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="8d1f8-111">Корень ссылается на поле объекта, а не на сам объект.</span><span class="sxs-lookup"><span data-stu-id="8d1f8-111">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="8d1f8-112">Корень предотвращает сборку мусора, если значение счетчика ссылок объекта является определенным значением.</span><span class="sxs-lookup"><span data-stu-id="8d1f8-112">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d1f8-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="8d1f8-113">Remarks</span></span>  

 <span data-ttu-id="8d1f8-114">`COR_PRF_GC_ROOT_FLAGS` Битовая маска, которая предоставляет дополнительные сведения о специальных корневых элементах.</span><span class="sxs-lookup"><span data-stu-id="8d1f8-114">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="8d1f8-115">Однако не все корни являются специальными.</span><span class="sxs-lookup"><span data-stu-id="8d1f8-115">However, not all roots are special.</span></span> <span data-ttu-id="8d1f8-116">Например, некоторые корни не являются слабыми ссылками, внутренними указателями, закрепленными или подсчитаны ссылки.</span><span class="sxs-lookup"><span data-stu-id="8d1f8-116">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="8d1f8-117">Для таких корней нет флагов для передачи.</span><span class="sxs-lookup"><span data-stu-id="8d1f8-117">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="8d1f8-118">Таким образом, методы, использующие это перечисление, например метод [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) , отправляют 0 для битовой маски флагов, что означает, что все флаги отключены.</span><span class="sxs-lookup"><span data-stu-id="8d1f8-118">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d1f8-119">Требования</span><span class="sxs-lookup"><span data-stu-id="8d1f8-119">Requirements</span></span>  

 <span data-ttu-id="8d1f8-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d1f8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d1f8-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8d1f8-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d1f8-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d1f8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d1f8-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d1f8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d1f8-124">См. также</span><span class="sxs-lookup"><span data-stu-id="8d1f8-124">See also</span></span>

- [<span data-ttu-id="8d1f8-125">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="8d1f8-125">Profiling Enumerations</span></span>](profiling-enumerations.md)
