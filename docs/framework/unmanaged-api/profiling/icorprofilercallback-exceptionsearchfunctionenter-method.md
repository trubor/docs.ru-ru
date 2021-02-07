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
ms.openlocfilehash: 6e77ab5dc8c15a1d0785fb83310183c0a4693225
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706198"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="2102f-103">Метод ICorProfilerCallback::ExceptionSearchFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="2102f-103">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>

<span data-ttu-id="2102f-104">Уведомляет профилировщик о том, что фаза поиска обработки исключений начала Поиск функции для поиска обработчика для текущего исключения.</span><span class="sxs-lookup"><span data-stu-id="2102f-104">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2102f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2102f-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2102f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2102f-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="2102f-107">\[in] идентификатор введенной функции.</span><span class="sxs-lookup"><span data-stu-id="2102f-107">\[in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="2102f-108">Требования</span><span class="sxs-lookup"><span data-stu-id="2102f-108">Requirements</span></span>  

 <span data-ttu-id="2102f-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2102f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2102f-110">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2102f-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2102f-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2102f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2102f-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2102f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2102f-113">См. также</span><span class="sxs-lookup"><span data-stu-id="2102f-113">See also</span></span>

- [<span data-ttu-id="2102f-114">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="2102f-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2102f-115">Метод ExceptionSearchFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="2102f-115">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
