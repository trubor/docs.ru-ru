---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ModuleUnloadFinished'
title: Метод ICorProfilerCallback::ModuleUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
ms.openlocfilehash: 32182beb879813a4e60f69494bd93799c0f66e1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745261"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="52a0c-103">Метод ICorProfilerCallback::ModuleUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="52a0c-103">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>

<span data-ttu-id="52a0c-104">Уведомляет профилировщик о завершении выгрузки модуля.</span><span class="sxs-lookup"><span data-stu-id="52a0c-104">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52a0c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="52a0c-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52a0c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="52a0c-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="52a0c-107">окне Идентификатор выгруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="52a0c-107">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="52a0c-108">окне Значение HRESULT, указывающее, успешно ли выгружен модуль.</span><span class="sxs-lookup"><span data-stu-id="52a0c-108">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52a0c-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="52a0c-109">Remarks</span></span>  

 <span data-ttu-id="52a0c-110">Значение недопустимо `moduleId` для информационного запроса после возврата метода [ICorProfilerCallback:: ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="52a0c-110">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="52a0c-111">Некоторые части выгрузки класса могут продолжаться после `ModuleUnloadFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="52a0c-111">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="52a0c-112">Ошибка HRESULT в `hrStatus` указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="52a0c-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="52a0c-113">Однако значение HRESULT в случае успеха в `hrStatus` указывает только на то, что первая часть выгрузки модуля успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="52a0c-113">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52a0c-114">Требования</span><span class="sxs-lookup"><span data-stu-id="52a0c-114">Requirements</span></span>  

 <span data-ttu-id="52a0c-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52a0c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52a0c-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="52a0c-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52a0c-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52a0c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52a0c-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52a0c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a0c-119">См. также</span><span class="sxs-lookup"><span data-stu-id="52a0c-119">See also</span></span>

- [<span data-ttu-id="52a0c-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="52a0c-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
