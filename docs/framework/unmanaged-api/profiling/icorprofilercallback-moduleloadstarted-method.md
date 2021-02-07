---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Модулелоадстартед'
title: Метод ICorProfilerCallback::ModuleLoadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
ms.openlocfilehash: e8d15bece7baf82f69162663da00d331c7904837
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745272"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="cbabe-103">Метод ICorProfilerCallback::ModuleLoadStarted</span><span class="sxs-lookup"><span data-stu-id="cbabe-103">ICorProfilerCallback::ModuleLoadStarted Method</span></span>

<span data-ttu-id="cbabe-104">Уведомляет профилировщик о загрузке модуля.</span><span class="sxs-lookup"><span data-stu-id="cbabe-104">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbabe-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cbabe-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbabe-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cbabe-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="cbabe-107">окне Идентификатор загружаемого модуля.</span><span class="sxs-lookup"><span data-stu-id="cbabe-107">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbabe-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="cbabe-108">Remarks</span></span>  

 <span data-ttu-id="cbabe-109">Значение недопустимо `moduleId` для информационного запроса, пока не будет вызван метод [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cbabe-109">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbabe-110">Требования</span><span class="sxs-lookup"><span data-stu-id="cbabe-110">Requirements</span></span>  

 <span data-ttu-id="cbabe-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbabe-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbabe-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cbabe-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cbabe-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbabe-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbabe-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbabe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbabe-115">См. также</span><span class="sxs-lookup"><span data-stu-id="cbabe-115">See also</span></span>

- [<span data-ttu-id="cbabe-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="cbabe-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
