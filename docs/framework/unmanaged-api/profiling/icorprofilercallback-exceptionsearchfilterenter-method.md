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
ms.openlocfilehash: 29a9eed75e5d8a954dfb23dedf3d2080e0d139d2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760224"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="248da-103">Метод ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="248da-103">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>

<span data-ttu-id="248da-104">Уведомляет профилировщик о том, что фаза поиска обработки исключений начала выполнять пользовательский фильтр исключений.</span><span class="sxs-lookup"><span data-stu-id="248da-104">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="248da-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="248da-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="248da-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="248da-106">Parameters</span></span>

<span data-ttu-id="248da-107">`functionId` окне Идентификатор функции, которая содержит фильтр.</span><span class="sxs-lookup"><span data-stu-id="248da-107">`functionId` [in] The ID of the function that contains the filter.</span></span>

## <a name="requirements"></a><span data-ttu-id="248da-108">Требования</span><span class="sxs-lookup"><span data-stu-id="248da-108">Requirements</span></span>  

 <span data-ttu-id="248da-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="248da-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="248da-110">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="248da-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="248da-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="248da-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="248da-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="248da-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="248da-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="248da-113">See also</span></span>

- [<span data-ttu-id="248da-114">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="248da-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="248da-115">Метод ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="248da-115">ExceptionSearchFilterLeave Method</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)
