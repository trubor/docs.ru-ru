---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионсеарчкатчерфаунд'
title: Метод ICorProfilerCallback::ExceptionSearchCatcherFound
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: 080e9be61e4f10cbfb60696a5089aca0c3f2843f
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759993"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="213d5-103">Метод ICorProfilerCallback::ExceptionSearchCatcherFound</span><span class="sxs-lookup"><span data-stu-id="213d5-103">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>

<span data-ttu-id="213d5-104">Уведомляет профилировщик о том, что на фазе поиска исключений обнаружен обработчик для созданного исключения.</span><span class="sxs-lookup"><span data-stu-id="213d5-104">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="213d5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="213d5-105">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="213d5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="213d5-106">Parameters</span></span>

<span data-ttu-id="213d5-107">`functionId` окне Идентификатор функции, которая содержит обработчик исключений.</span><span class="sxs-lookup"><span data-stu-id="213d5-107">`functionId` [in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="213d5-108">Требования</span><span class="sxs-lookup"><span data-stu-id="213d5-108">Requirements</span></span>  

 <span data-ttu-id="213d5-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="213d5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="213d5-110">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="213d5-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="213d5-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="213d5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="213d5-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="213d5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="213d5-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="213d5-113">See also</span></span>

- [<span data-ttu-id="213d5-114">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="213d5-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
