---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Комклассиквтаблекреатед'
title: Метод ICorProfilerCallback::COMClassicVTableCreated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type:
- apiref
ms.openlocfilehash: 134ca44cbcd7a275e3ad61a3dd4decaa92668b5b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657714"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="e1a9d-103">Метод ICorProfilerCallback::COMClassicVTableCreated</span><span class="sxs-lookup"><span data-stu-id="e1a9d-103">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>

<span data-ttu-id="e1a9d-104">Уведомляет профилировщик о том, что для указанного IID и класса был создан объект vtable COM-взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="e1a9d-104">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1a9d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e1a9d-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1a9d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e1a9d-106">Parameters</span></span>

- `wrappedClasId`

  <span data-ttu-id="e1a9d-107">\[in] идентификатор класса, для которого была создана таблица vtable.</span><span class="sxs-lookup"><span data-stu-id="e1a9d-107">\[in] The ID of the class for which the vtable has been created.</span></span>

- `implementedIID`

  <span data-ttu-id="e1a9d-108">\[in] идентификатор интерфейса, реализуемого классом.</span><span class="sxs-lookup"><span data-stu-id="e1a9d-108">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="e1a9d-109">Это значение может быть равно NULL, если интерфейс является только внутренним.</span><span class="sxs-lookup"><span data-stu-id="e1a9d-109">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="e1a9d-110">\[in] указатель на начало таблицы vtable.</span><span class="sxs-lookup"><span data-stu-id="e1a9d-110">\[in] A pointer to the start of the vtable.</span></span>

- `cSlots`

  <span data-ttu-id="e1a9d-111">\[in] число слотов в таблице vtable.</span><span class="sxs-lookup"><span data-stu-id="e1a9d-111">\[in] The number of slots that are in the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1a9d-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="e1a9d-112">Remarks</span></span>  

 <span data-ttu-id="e1a9d-113">Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="e1a9d-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="e1a9d-114">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="e1a9d-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="e1a9d-115">Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="e1a9d-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1a9d-116">Требования</span><span class="sxs-lookup"><span data-stu-id="e1a9d-116">Requirements</span></span>  

 <span data-ttu-id="e1a9d-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1a9d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1a9d-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1a9d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1a9d-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1a9d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1a9d-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1a9d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a9d-121">См. также</span><span class="sxs-lookup"><span data-stu-id="e1a9d-121">See also</span></span>

- [<span data-ttu-id="e1a9d-122">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e1a9d-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e1a9d-123">Метод COMClassicVTableDestroyed</span><span class="sxs-lookup"><span data-stu-id="e1a9d-123">COMClassicVTableDestroyed Method</span></span>](icorprofilercallback-comclassicvtabledestroyed-method.md)
