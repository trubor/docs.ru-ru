---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ClassUnloadFinished'
title: Метод ICorProfilerCallback::ClassUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: ae1ef56a1eb3b9b45c2165ecceb0af826cc7a2ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657740"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="80e5c-103">Метод ICorProfilerCallback::ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="80e5c-103">ICorProfilerCallback::ClassUnloadFinished Method</span></span>

<span data-ttu-id="80e5c-104">Уведомляет профилировщик о завершении выгрузки класса.</span><span class="sxs-lookup"><span data-stu-id="80e5c-104">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e5c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="80e5c-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80e5c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="80e5c-106">Parameters</span></span>

- `classId`

  <span data-ttu-id="80e5c-107">\[в] определяет класс, который был выгружен.</span><span class="sxs-lookup"><span data-stu-id="80e5c-107">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="80e5c-108">\[in] значение HRESULT, указывающее, успешно ли выгружен класс.</span><span class="sxs-lookup"><span data-stu-id="80e5c-108">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="80e5c-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="80e5c-109">Remarks</span></span>  

 <span data-ttu-id="80e5c-110">Некоторые части выгрузки класса могут продолжаться после `ClassUnloadFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="80e5c-110">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="80e5c-111">Ошибка HRESULT в `hrStatus` указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="80e5c-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="80e5c-112">Однако значение HRESULT в случае успеха в `hrStatus` указывает только на то, что первая часть выгрузки класса успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="80e5c-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80e5c-113">Требования</span><span class="sxs-lookup"><span data-stu-id="80e5c-113">Requirements</span></span>  

 <span data-ttu-id="80e5c-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80e5c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e5c-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="80e5c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80e5c-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80e5c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80e5c-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80e5c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e5c-118">См. также</span><span class="sxs-lookup"><span data-stu-id="80e5c-118">See also</span></span>

- [<span data-ttu-id="80e5c-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="80e5c-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="80e5c-120">Метод ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="80e5c-120">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
