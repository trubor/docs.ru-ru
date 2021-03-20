---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Initialize'
title: Метод ICorProfilerCallback::Initialize
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
ms.openlocfilehash: c7138a1a39a1d32c751c205a86c00e6070a236b3
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760422"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="55d9a-103">Метод ICorProfilerCallback::Initialize</span><span class="sxs-lookup"><span data-stu-id="55d9a-103">ICorProfilerCallback::Initialize Method</span></span>

<span data-ttu-id="55d9a-104">Вызывается для инициализации профилировщика кода при запуске нового приложения среды CLR.</span><span class="sxs-lookup"><span data-stu-id="55d9a-104">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55d9a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="55d9a-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55d9a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="55d9a-106">Parameters</span></span>

<span data-ttu-id="55d9a-107">`pICorProfilerInfoUnk` окне Указатель на интерфейс [IUnknown](/cpp/atl/iunknown) , который профилировщик должен запрашивать для указателя интерфейса [ICorProfilerInfo](icorprofilerinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="55d9a-107">`pICorProfilerInfoUnk` [in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="55d9a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="55d9a-108">Remarks</span></span>  

 <span data-ttu-id="55d9a-109">`Initialize`Вызов является единственной возможностью включать (или отключать) обратные вызовы, которые являются неизменяемыми.</span><span class="sxs-lookup"><span data-stu-id="55d9a-109">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="55d9a-110">После включения обратного вызова в `Initialize` вызове он не может быть отключен позже с помощью команды [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="55d9a-110">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="55d9a-111">Значение COR_PRF_MONITOR_IMMUTABLE перечисления [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) указывает, какие события являются неизменяемыми.</span><span class="sxs-lookup"><span data-stu-id="55d9a-111">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55d9a-112">Требования</span><span class="sxs-lookup"><span data-stu-id="55d9a-112">Requirements</span></span>  

 <span data-ttu-id="55d9a-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55d9a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55d9a-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55d9a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="55d9a-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55d9a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55d9a-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55d9a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d9a-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="55d9a-117">See also</span></span>

- [<span data-ttu-id="55d9a-118">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="55d9a-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="55d9a-119">Метод Shutdown</span><span class="sxs-lookup"><span data-stu-id="55d9a-119">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
