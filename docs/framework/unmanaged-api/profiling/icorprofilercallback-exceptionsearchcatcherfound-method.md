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
ms.openlocfilehash: b222e629cbfce2fde27c2d266b3a343466a1419c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706322"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="8c973-103">Метод ICorProfilerCallback::ExceptionSearchCatcherFound</span><span class="sxs-lookup"><span data-stu-id="8c973-103">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>

<span data-ttu-id="8c973-104">Уведомляет профилировщик о том, что на фазе поиска исключений обнаружен обработчик для созданного исключения.</span><span class="sxs-lookup"><span data-stu-id="8c973-104">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c973-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8c973-105">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c973-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8c973-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="8c973-107">\[in] идентификатор функции, которая содержит обработчик исключений.</span><span class="sxs-lookup"><span data-stu-id="8c973-107">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="8c973-108">Требования</span><span class="sxs-lookup"><span data-stu-id="8c973-108">Requirements</span></span>  

 <span data-ttu-id="8c973-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c973-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c973-110">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8c973-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8c973-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c973-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c973-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c973-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c973-113">См. также</span><span class="sxs-lookup"><span data-stu-id="8c973-113">See also</span></span>

- [<span data-ttu-id="8c973-114">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8c973-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
