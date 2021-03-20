---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: FunctionUnloadStarted'
title: Метод ICorProfilerCallback::FunctionUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: ce3cf406b8d2f91613bce878db8a4f9e0838c052
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760435"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="be34a-103">Метод ICorProfilerCallback::FunctionUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="be34a-103">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>

<span data-ttu-id="be34a-104">Уведомляет профилировщик о запуске среды выполнения для выгрузки функции.</span><span class="sxs-lookup"><span data-stu-id="be34a-104">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be34a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="be34a-105">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="be34a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="be34a-106">Parameters</span></span>

<span data-ttu-id="be34a-107">`functionId` окне Идентификатор выгрузки функции.</span><span class="sxs-lookup"><span data-stu-id="be34a-107">`functionId` [in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="be34a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="be34a-108">Remarks</span></span>  

 <span data-ttu-id="be34a-109">Значение `functionId` параметра больше не является допустимым после возврата этим методом вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="be34a-109">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be34a-110">Требования</span><span class="sxs-lookup"><span data-stu-id="be34a-110">Requirements</span></span>  

 <span data-ttu-id="be34a-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be34a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be34a-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be34a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be34a-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be34a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be34a-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be34a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be34a-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="be34a-115">See also</span></span>

- [<span data-ttu-id="be34a-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="be34a-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
