---
description: 'Дополнительные сведения о методе: ICorProfilerCallback2:: RootReferences2'
title: Метод ICorProfilerCallback2::RootReferences2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
ms.openlocfilehash: a599014cc9fb47b103a136b9e5569d38031c9377
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799087"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="36d7e-103">Метод ICorProfilerCallback2::RootReferences2</span><span class="sxs-lookup"><span data-stu-id="36d7e-103">ICorProfilerCallback2::RootReferences2 Method</span></span>

<span data-ttu-id="36d7e-104">Уведомляет профилировщик о корневых ссылках после сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="36d7e-104">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="36d7e-105">Этот метод является расширением метода [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="36d7e-105">This method is an extension of the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36d7e-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="36d7e-106">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36d7e-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="36d7e-107">Parameters</span></span>  

 `cRootRefs`  
 <span data-ttu-id="36d7e-108">окне Число элементов в `rootRefIds` `rootKinds` `rootFlags` массивах,, и `rootIds` .</span><span class="sxs-lookup"><span data-stu-id="36d7e-108">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="36d7e-109">окне Массив идентификаторов объектов, каждый из которых ссылается на статический объект или объект в стеке.</span><span class="sxs-lookup"><span data-stu-id="36d7e-109">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="36d7e-110">Элементы `rootKinds` массива предоставляют сведения для классификации соответствующих элементов в `rootRefIds` массиве.</span><span class="sxs-lookup"><span data-stu-id="36d7e-110">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="36d7e-111">окне Массив значений [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) , указывающих тип корня сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="36d7e-111">[in] An array of [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="36d7e-112">окне Массив значений [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) , описывающих свойства корня сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="36d7e-112">[in] An array of [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="36d7e-113">окне Массив значений UINT_PTR, указывающих на целое число, которое содержит дополнительные сведения об корне сборки мусора в зависимости от значения `rootKinds` параметра.</span><span class="sxs-lookup"><span data-stu-id="36d7e-113">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="36d7e-114">Если корневым типом является стек, то для функции, содержащей переменную, используется корневой идентификатор.</span><span class="sxs-lookup"><span data-stu-id="36d7e-114">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="36d7e-115">Если этот корневой идентификатор равен 0, функция является неименованной функцией, которая является внутренней для среды CLR.</span><span class="sxs-lookup"><span data-stu-id="36d7e-115">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="36d7e-116">Если корневой тип является обработчиком, корневой идентификатор — для обработчика сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="36d7e-116">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="36d7e-117">Для других корневых типов идентификатор является непрозрачным значением и должен игнорироваться.</span><span class="sxs-lookup"><span data-stu-id="36d7e-117">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36d7e-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="36d7e-118">Remarks</span></span>  

 <span data-ttu-id="36d7e-119">`rootRefIds` `rootKinds` `rootFlags` Массивы,, и `rootIds` являются параллельными массивами.</span><span class="sxs-lookup"><span data-stu-id="36d7e-119">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="36d7e-120">То есть,,, `rootRefIds[i]` `rootKinds[i]` `rootFlags[i]` и `rootIds[i]` имеют тот же корень.</span><span class="sxs-lookup"><span data-stu-id="36d7e-120">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="36d7e-121">Оба `RootReferences` `RootReferences2` метода и вызываются для уведомления профилировщика.</span><span class="sxs-lookup"><span data-stu-id="36d7e-121">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="36d7e-122">Профилировщики, как правило, реализуют один метод или другой, но не оба, так как передаваемые сведения `RootReferences2` являются надмножеством переданного `RootReferences` .</span><span class="sxs-lookup"><span data-stu-id="36d7e-122">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="36d7e-123">Записи в могут `rootRefIds` быть равны нулю, что означает, что соответствующая корневая ссылка имеет значение NULL и не ссылается на объект в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="36d7e-123">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="36d7e-124">Идентификаторы объектов, возвращаемые, `RootReferences2` недопустимы во время обратного вызова, так как сборка мусора может находиться в процессе перемещения объектов из старых адресов в новые адреса.</span><span class="sxs-lookup"><span data-stu-id="36d7e-124">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="36d7e-125">В связи с этим профилировщикам не следует пытаться проверять объекты во время вызова `RootReferences2`.</span><span class="sxs-lookup"><span data-stu-id="36d7e-125">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="36d7e-126">При вызове [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) все объекты были перемещены в новые расположения и могут быть безопасно проверены.</span><span class="sxs-lookup"><span data-stu-id="36d7e-126">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36d7e-127">Требования</span><span class="sxs-lookup"><span data-stu-id="36d7e-127">Requirements</span></span>  

 <span data-ttu-id="36d7e-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36d7e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36d7e-129">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36d7e-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36d7e-130">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36d7e-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36d7e-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d7e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d7e-132">См. также</span><span class="sxs-lookup"><span data-stu-id="36d7e-132">See also</span></span>

- [<span data-ttu-id="36d7e-133">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="36d7e-133">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="36d7e-134">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="36d7e-134">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
