---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Комклассиквтабледестройед'
title: Метод ICorProfilerCallback::COMClassicVTableDestroyed
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
ms.openlocfilehash: 91ed5bb65d3a64f1f85a09a710b507974f51c79b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706387"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="a449c-103">Метод ICorProfilerCallback::COMClassicVTableDestroyed</span><span class="sxs-lookup"><span data-stu-id="a449c-103">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>

<span data-ttu-id="a449c-104">Уведомляет профилировщик о том, что виртуальная таблица COM-взаимодействия удалена.</span><span class="sxs-lookup"><span data-stu-id="a449c-104">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a449c-105">Этот обратный вызов, скорее всего, никогда не происходит, так как уничтожение vtable происходит очень близко к завершению работы.</span><span class="sxs-lookup"><span data-stu-id="a449c-105">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a449c-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a449c-106">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a449c-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="a449c-107">Parameters</span></span>

- `wrappedClassId`

  <span data-ttu-id="a449c-108">\[in] идентификатор класса, для которого была создана эта таблица vtable.</span><span class="sxs-lookup"><span data-stu-id="a449c-108">\[in] The ID of the class for which this vtable was created.</span></span>

- `implementedIID`

  <span data-ttu-id="a449c-109">\[in] идентификатор интерфейса, реализуемого классом.</span><span class="sxs-lookup"><span data-stu-id="a449c-109">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="a449c-110">Это значение может быть равно NULL, если интерфейс является только внутренним.</span><span class="sxs-lookup"><span data-stu-id="a449c-110">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="a449c-111">\[in] указатель на начало таблицы vtable.</span><span class="sxs-lookup"><span data-stu-id="a449c-111">\[in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="a449c-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="a449c-112">Remarks</span></span>  

 <span data-ttu-id="a449c-113">Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="a449c-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="a449c-114">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="a449c-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="a449c-115">Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="a449c-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a449c-116">Требования</span><span class="sxs-lookup"><span data-stu-id="a449c-116">Requirements</span></span>  

 <span data-ttu-id="a449c-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a449c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a449c-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a449c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a449c-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a449c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a449c-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a449c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a449c-121">См. также</span><span class="sxs-lookup"><span data-stu-id="a449c-121">See also</span></span>

- [<span data-ttu-id="a449c-122">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a449c-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a449c-123">Метод COMClassicVTableCreated</span><span class="sxs-lookup"><span data-stu-id="a449c-123">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
