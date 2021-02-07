---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионсеарчфилтерентер'
title: Метод ICorProfilerCallback::ExceptionSearchFilterEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
ms.openlocfilehash: ca0eb80f57d7c00d0abfab1bb602650c951a30e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745384"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="c7552-103">Метод ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="c7552-103">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>

<span data-ttu-id="c7552-104">Уведомляет профилировщик о том, что фаза поиска обработки исключений начала выполнять пользовательский фильтр исключений.</span><span class="sxs-lookup"><span data-stu-id="c7552-104">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7552-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c7552-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7552-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c7552-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="c7552-107">\[in] идентификатор функции, которая содержит фильтр.</span><span class="sxs-lookup"><span data-stu-id="c7552-107">\[in] The ID of the function that contains the filter.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7552-108">Требования</span><span class="sxs-lookup"><span data-stu-id="c7552-108">Requirements</span></span>  

 <span data-ttu-id="c7552-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7552-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7552-110">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c7552-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c7552-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7552-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7552-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7552-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7552-113">См. также</span><span class="sxs-lookup"><span data-stu-id="c7552-113">See also</span></span>

- [<span data-ttu-id="c7552-114">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c7552-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c7552-115">Метод ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="c7552-115">ExceptionSearchFilterLeave Method</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)
