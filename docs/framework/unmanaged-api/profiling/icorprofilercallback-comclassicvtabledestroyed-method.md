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
ms.openlocfilehash: e8ed6be2519a9f8959ac4f59313f73f13d6c569b
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760565"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="9cae9-103">Метод ICorProfilerCallback::COMClassicVTableDestroyed</span><span class="sxs-lookup"><span data-stu-id="9cae9-103">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>

<span data-ttu-id="9cae9-104">Уведомляет профилировщик о том, что виртуальная таблица COM-взаимодействия удалена.</span><span class="sxs-lookup"><span data-stu-id="9cae9-104">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9cae9-105">Этот обратный вызов, скорее всего, никогда не происходит, так как уничтожение vtable происходит очень близко к завершению работы.</span><span class="sxs-lookup"><span data-stu-id="9cae9-105">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cae9-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9cae9-106">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cae9-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="9cae9-107">Parameters</span></span>

<span data-ttu-id="9cae9-108">`wrappedClassId` окне Идентификатор класса, для которого была создана эта таблица vtable.</span><span class="sxs-lookup"><span data-stu-id="9cae9-108">`wrappedClassId` [in] The ID of the class for which this vtable was created.</span></span>

<span data-ttu-id="9cae9-109">`implementedIID` окне Идентификатор интерфейса, реализуемого классом.</span><span class="sxs-lookup"><span data-stu-id="9cae9-109">`implementedIID` [in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="9cae9-110">Это значение может быть равно NULL, если интерфейс является только внутренним.</span><span class="sxs-lookup"><span data-stu-id="9cae9-110">This value may be NULL if the interface is internal only.</span></span>

<span data-ttu-id="9cae9-111">`pVTable` окне Указатель на начало таблицы vtable.</span><span class="sxs-lookup"><span data-stu-id="9cae9-111">`pVTable` [in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="9cae9-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="9cae9-112">Remarks</span></span>  

 <span data-ttu-id="9cae9-113">Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="9cae9-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="9cae9-114">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="9cae9-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="9cae9-115">Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="9cae9-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cae9-116">Требования</span><span class="sxs-lookup"><span data-stu-id="9cae9-116">Requirements</span></span>  

 <span data-ttu-id="9cae9-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cae9-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cae9-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9cae9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9cae9-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cae9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cae9-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cae9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cae9-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9cae9-121">See also</span></span>

- [<span data-ttu-id="9cae9-122">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="9cae9-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9cae9-123">Метод COMClassicVTableCreated</span><span class="sxs-lookup"><span data-stu-id="9cae9-123">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
