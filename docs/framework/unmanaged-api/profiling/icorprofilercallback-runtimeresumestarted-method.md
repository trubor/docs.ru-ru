---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: RuntimeResumeStarted'
title: Метод ICorProfilerCallback::RuntimeResumeStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeResumeStarted method [.NET Framework profiling]
- RuntimeResumeStarted method [.NET Framework profiling]
ms.assetid: 5854bfb2-c568-4f19-904a-7c9d41e7b995
topic_type:
- apiref
ms.openlocfilehash: 74e87906b4c429d795aa3074b25f4ac7a9edfa37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788843"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="ec9e3-103">Метод ICorProfilerCallback::RuntimeResumeStarted</span><span class="sxs-lookup"><span data-stu-id="ec9e3-103">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>

<span data-ttu-id="ec9e3-104">Уведомляет профилировщик о том, что среда выполнения возобновляет все потоки времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="ec9e3-104">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec9e3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ec9e3-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="ec9e3-106">Требования</span><span class="sxs-lookup"><span data-stu-id="ec9e3-106">Requirements</span></span>  

 <span data-ttu-id="ec9e3-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec9e3-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec9e3-108">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec9e3-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec9e3-109">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec9e3-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec9e3-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec9e3-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec9e3-111">См. также</span><span class="sxs-lookup"><span data-stu-id="ec9e3-111">See also</span></span>

- [<span data-ttu-id="ec9e3-112">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ec9e3-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ec9e3-113">Метод RuntimeResumeFinished</span><span class="sxs-lookup"><span data-stu-id="ec9e3-113">RuntimeResumeFinished Method</span></span>](icorprofilercallback-runtimeresumefinished-method.md)
