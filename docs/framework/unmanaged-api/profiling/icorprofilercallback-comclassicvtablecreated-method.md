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
ms.openlocfilehash: 04ba37b9c1307539c9fdf299f4667e7026d571be
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760578"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="03d3a-103">Метод ICorProfilerCallback::COMClassicVTableCreated</span><span class="sxs-lookup"><span data-stu-id="03d3a-103">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>

<span data-ttu-id="03d3a-104">Уведомляет профилировщик о том, что для указанного IID и класса был создан объект vtable COM-взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="03d3a-104">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03d3a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="03d3a-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03d3a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="03d3a-106">Parameters</span></span>

<span data-ttu-id="03d3a-107">`wrappedClasId` окне Идентификатор класса, для которого была создана таблица vtable.</span><span class="sxs-lookup"><span data-stu-id="03d3a-107">`wrappedClasId` [in] The ID of the class for which the vtable has been created.</span></span>

<span data-ttu-id="03d3a-108">`implementedIID` окне Идентификатор интерфейса, реализуемого классом.</span><span class="sxs-lookup"><span data-stu-id="03d3a-108">`implementedIID` [in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="03d3a-109">Это значение может быть равно NULL, если интерфейс является только внутренним.</span><span class="sxs-lookup"><span data-stu-id="03d3a-109">This value may be NULL if the interface is internal only.</span></span>

<span data-ttu-id="03d3a-110">`pVTable` окне Указатель на начало таблицы vtable.</span><span class="sxs-lookup"><span data-stu-id="03d3a-110">`pVTable` [in] A pointer to the start of the vtable.</span></span>

<span data-ttu-id="03d3a-111">`cSlots` окне Число слотов в таблице vtable.</span><span class="sxs-lookup"><span data-stu-id="03d3a-111">`cSlots` [in] The number of slots that are in the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="03d3a-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="03d3a-112">Remarks</span></span>  

 <span data-ttu-id="03d3a-113">Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="03d3a-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="03d3a-114">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="03d3a-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="03d3a-115">Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="03d3a-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03d3a-116">Требования</span><span class="sxs-lookup"><span data-stu-id="03d3a-116">Requirements</span></span>  

 <span data-ttu-id="03d3a-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03d3a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03d3a-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="03d3a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="03d3a-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03d3a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03d3a-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03d3a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03d3a-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="03d3a-121">See also</span></span>

- [<span data-ttu-id="03d3a-122">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="03d3a-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="03d3a-123">Метод COMClassicVTableDestroyed</span><span class="sxs-lookup"><span data-stu-id="03d3a-123">COMClassicVTableDestroyed Method</span></span>](icorprofilercallback-comclassicvtabledestroyed-method.md)
