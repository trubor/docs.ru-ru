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
ms.openlocfilehash: 91de255b2214ad0c6ce6911d9533df593142a191
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760682"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="12140-103">Метод ICorProfilerCallback::ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="12140-103">ICorProfilerCallback::ClassUnloadStarted Method</span></span>

<span data-ttu-id="12140-104">Уведомляет профилировщик о выгрузке класса.</span><span class="sxs-lookup"><span data-stu-id="12140-104">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12140-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="12140-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12140-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="12140-106">Parameters</span></span>

<span data-ttu-id="12140-107">`classId` окне Определяет выгружается класс.</span><span class="sxs-lookup"><span data-stu-id="12140-107">`classId` [in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="12140-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="12140-108">Remarks</span></span>  

 <span data-ttu-id="12140-109">Значение недопустимо `classId` для информационного запроса после `ClassUnloadStarted` возврата метода — это последний шанс профилировщика получить сведения об этом классе.</span><span class="sxs-lookup"><span data-stu-id="12140-109">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12140-110">Требования</span><span class="sxs-lookup"><span data-stu-id="12140-110">Requirements</span></span>  

 <span data-ttu-id="12140-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12140-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12140-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12140-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12140-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12140-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12140-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12140-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12140-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="12140-115">See also</span></span>

- [<span data-ttu-id="12140-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="12140-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="12140-117">Метод ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="12140-117">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
