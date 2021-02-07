---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ClassUnloadStarted'
title: Метод ICorProfilerCallback::ClassUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 3dae88d9cbe9ed2a2e234d02420a65c6a9ca003d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706376"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="03858-103">Метод ICorProfilerCallback::ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="03858-103">ICorProfilerCallback::ClassUnloadStarted Method</span></span>

<span data-ttu-id="03858-104">Уведомляет профилировщик о выгрузке класса.</span><span class="sxs-lookup"><span data-stu-id="03858-104">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03858-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="03858-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03858-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="03858-106">Parameters</span></span>

- `classId`

  <span data-ttu-id="03858-107">\[в] определяет класс, который выгружается.</span><span class="sxs-lookup"><span data-stu-id="03858-107">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="03858-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="03858-108">Remarks</span></span>  

 <span data-ttu-id="03858-109">Значение недопустимо `classId` для информационного запроса после `ClassUnloadStarted` возврата метода — это последний шанс профилировщика получить сведения об этом классе.</span><span class="sxs-lookup"><span data-stu-id="03858-109">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03858-110">Требования</span><span class="sxs-lookup"><span data-stu-id="03858-110">Requirements</span></span>  

 <span data-ttu-id="03858-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03858-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03858-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="03858-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="03858-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03858-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03858-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03858-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03858-115">См. также</span><span class="sxs-lookup"><span data-stu-id="03858-115">See also</span></span>

- [<span data-ttu-id="03858-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="03858-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="03858-117">Метод ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="03858-117">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
