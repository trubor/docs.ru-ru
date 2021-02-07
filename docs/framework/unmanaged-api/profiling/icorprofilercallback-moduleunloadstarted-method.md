---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ModuleUnloadStarted'
title: Метод ICorProfilerCallback::ModuleUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
ms.openlocfilehash: 3d10654e23481fe6f8956129a0aef7ed4206bba9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745233"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="edae7-103">Метод ICorProfilerCallback::ModuleUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="edae7-103">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>

<span data-ttu-id="edae7-104">Уведомляет профилировщик о выгрузке модуля.</span><span class="sxs-lookup"><span data-stu-id="edae7-104">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edae7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="edae7-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="edae7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="edae7-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="edae7-107">окне Идентификатор выгружается модуля.</span><span class="sxs-lookup"><span data-stu-id="edae7-107">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edae7-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="edae7-108">Remarks</span></span>  

 <span data-ttu-id="edae7-109">Значение недопустимо `moduleId` для информационного запроса после `ModuleUnloadStarted` возврата метода — это последний шанс профилировщика получить сведения об этом модуле.</span><span class="sxs-lookup"><span data-stu-id="edae7-109">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edae7-110">Требования</span><span class="sxs-lookup"><span data-stu-id="edae7-110">Requirements</span></span>  

 <span data-ttu-id="edae7-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edae7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edae7-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="edae7-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="edae7-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edae7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edae7-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edae7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edae7-115">См. также</span><span class="sxs-lookup"><span data-stu-id="edae7-115">See also</span></span>

- [<span data-ttu-id="edae7-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="edae7-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="edae7-117">Метод ModuleUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="edae7-117">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
