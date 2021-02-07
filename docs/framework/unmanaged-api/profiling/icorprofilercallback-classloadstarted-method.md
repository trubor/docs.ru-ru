---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Класслоадстартед'
title: Метод ICorProfilerCallback::ClassLoadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 2474f8041b0858cbcb81d3f4042f1748cb99df3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706478"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="7c964-103">Метод ICorProfilerCallback::ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="7c964-103">ICorProfilerCallback::ClassLoadStarted Method</span></span>

<span data-ttu-id="7c964-104">Уведомляет профилировщик о том, что класс загружается.</span><span class="sxs-lookup"><span data-stu-id="7c964-104">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c964-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7c964-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c964-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7c964-106">Parameters</span></span>

- `classId`

  <span data-ttu-id="7c964-107">\[в] определяет класс, который загружается.</span><span class="sxs-lookup"><span data-stu-id="7c964-107">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c964-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="7c964-108">Remarks</span></span>  

 <span data-ttu-id="7c964-109">Значение недопустимо `classId` для информационного запроса, пока не будет вызван метод [ICorProfilerCallback:: класслоадфинишед](icorprofilercallback-classloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7c964-109">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c964-110">Требования</span><span class="sxs-lookup"><span data-stu-id="7c964-110">Requirements</span></span>  

 <span data-ttu-id="7c964-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c964-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c964-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7c964-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7c964-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c964-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c964-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c964-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c964-115">См. также</span><span class="sxs-lookup"><span data-stu-id="7c964-115">See also</span></span>

- [<span data-ttu-id="7c964-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7c964-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
