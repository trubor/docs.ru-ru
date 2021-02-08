---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионсеарчфилтерлеаве'
title: Метод ICorProfilerCallback::ExceptionSearchFilterLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave method [.NET Framework profiling]
- ExceptionSearchFilterLeave method [.NET Framework profiling]
ms.assetid: c28a2a82-dd11-4385-843f-b509fb61753b
topic_type:
- apiref
ms.openlocfilehash: d2195e8e055b25f71efbfbcc71e933daa07a4e3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799126"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="59d21-103">Метод ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="59d21-103">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>

<span data-ttu-id="59d21-104">Уведомляет профилировщик о завершении выполнения фильтра пользователем.</span><span class="sxs-lookup"><span data-stu-id="59d21-104">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d21-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="59d21-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="59d21-106">Требования</span><span class="sxs-lookup"><span data-stu-id="59d21-106">Requirements</span></span>  

 <span data-ttu-id="59d21-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59d21-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59d21-108">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="59d21-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="59d21-109">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59d21-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59d21-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59d21-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59d21-111">См. также</span><span class="sxs-lookup"><span data-stu-id="59d21-111">See also</span></span>

- [<span data-ttu-id="59d21-112">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="59d21-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="59d21-113">Метод ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="59d21-113">ExceptionSearchFilterEnter Method</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)
