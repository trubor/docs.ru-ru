---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионсеарчфунктионентер'
title: Метод ICorProfilerCallback::ExceptionSearchFunctionEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
ms.openlocfilehash: d9989ef8b1ae50202ba6900b95504a7d50e10dfc
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759486"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="1cdbe-103">Метод ICorProfilerCallback::ExceptionSearchFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="1cdbe-103">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>

<span data-ttu-id="1cdbe-104">Уведомляет профилировщик о том, что фаза поиска обработки исключений начала Поиск функции для поиска обработчика для текущего исключения.</span><span class="sxs-lookup"><span data-stu-id="1cdbe-104">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cdbe-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1cdbe-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cdbe-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1cdbe-106">Parameters</span></span>

<span data-ttu-id="1cdbe-107">`functionId` окне Идентификатор введенной функции.</span><span class="sxs-lookup"><span data-stu-id="1cdbe-107">`functionId` [in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="1cdbe-108">Требования</span><span class="sxs-lookup"><span data-stu-id="1cdbe-108">Requirements</span></span>  

 <span data-ttu-id="1cdbe-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cdbe-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cdbe-110">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1cdbe-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1cdbe-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cdbe-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cdbe-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cdbe-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cdbe-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1cdbe-113">See also</span></span>

- [<span data-ttu-id="1cdbe-114">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="1cdbe-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1cdbe-115">Метод ExceptionSearchFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="1cdbe-115">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
