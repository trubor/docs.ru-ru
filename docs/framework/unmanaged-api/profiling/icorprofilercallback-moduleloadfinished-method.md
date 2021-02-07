---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ModuleLoadFinished'
title: Метод ICorProfilerCallback::ModuleLoadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
ms.openlocfilehash: 960eb9edd036055069ef3f9ab3a93602ce4ef9bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745350"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="d469a-103">Метод ICorProfilerCallback::ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="d469a-103">ICorProfilerCallback::ModuleLoadFinished Method</span></span>

<span data-ttu-id="d469a-104">Уведомляет профилировщик о завершении загрузки модуля.</span><span class="sxs-lookup"><span data-stu-id="d469a-104">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d469a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d469a-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d469a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d469a-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="d469a-107">окне Идентификатор модуля, загрузка которого завершена.</span><span class="sxs-lookup"><span data-stu-id="d469a-107">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="d469a-108">окне Значение HRESULT, указывающее, успешно ли загружен модуль.</span><span class="sxs-lookup"><span data-stu-id="d469a-108">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d469a-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="d469a-109">Remarks</span></span>  

 <span data-ttu-id="d469a-110">Значение недопустимо `moduleId` для информационного запроса до `ModuleLoadFinished` вызова метода.</span><span class="sxs-lookup"><span data-stu-id="d469a-110">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="d469a-111">Некоторые части загрузки модуля могут продолжаться после `ModuleLoadFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="d469a-111">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="d469a-112">Ошибка HRESULT в `hrStatus` указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="d469a-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="d469a-113">Однако значение HRESULT в случае успеха в `hrStatus` указывает только на то, что первая часть загрузки модуля завершилась успешно.</span><span class="sxs-lookup"><span data-stu-id="d469a-113">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d469a-114">Требования</span><span class="sxs-lookup"><span data-stu-id="d469a-114">Requirements</span></span>  

 <span data-ttu-id="d469a-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d469a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d469a-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d469a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d469a-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d469a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d469a-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d469a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d469a-119">См. также</span><span class="sxs-lookup"><span data-stu-id="d469a-119">See also</span></span>

- [<span data-ttu-id="d469a-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d469a-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d469a-121">Метод ModuleLoadStarted</span><span class="sxs-lookup"><span data-stu-id="d469a-121">ModuleLoadStarted Method</span></span>](icorprofilercallback-moduleloadstarted-method.md)
