---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Класслоадфинишед'
title: Метод ICorProfilerCallback::ClassLoadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: 52fd26c1efaf9b85caeb5af7184ae70e1d29b9ff
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760225"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="cd1b9-103">Метод ICorProfilerCallback::ClassLoadFinished</span><span class="sxs-lookup"><span data-stu-id="cd1b9-103">ICorProfilerCallback::ClassLoadFinished Method</span></span>

<span data-ttu-id="cd1b9-104">Уведомляет профилировщик о том, что загрузка класса завершена.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-104">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd1b9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cd1b9-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd1b9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cd1b9-106">Parameters</span></span>

<span data-ttu-id="cd1b9-107">`classId` окне Идентифицирует загруженный класс.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-107">`classId` [in] Identifies the class that was loaded.</span></span>

<span data-ttu-id="cd1b9-108">`hrStatus` окне Значение HRESULT, указывающее, успешно ли загружен класс.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-108">`hrStatus` [in] An HRESULT that indicates whether the class loaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="cd1b9-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="cd1b9-109">Remarks</span></span>  

 <span data-ttu-id="cd1b9-110">Значение недопустимо `classId` для информационного запроса до `ClassLoadFinished` вызова метода.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-110">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="cd1b9-111">Некоторые части загрузки класса могут продолжаться после `ClassLoadFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-111">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="cd1b9-112">Ошибка HRESULT в `hrStatus` указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="cd1b9-113">Однако значение HRESULT в случае успеха в `hrStatus` указывает только на то, что первая часть загрузки класса завершилась успешно.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-113">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd1b9-114">Требования</span><span class="sxs-lookup"><span data-stu-id="cd1b9-114">Requirements</span></span>  

 <span data-ttu-id="cd1b9-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd1b9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd1b9-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd1b9-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd1b9-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd1b9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd1b9-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd1b9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd1b9-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="cd1b9-119">See also</span></span>

- [<span data-ttu-id="cd1b9-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="cd1b9-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="cd1b9-121">Метод ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="cd1b9-121">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
