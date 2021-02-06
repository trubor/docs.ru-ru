---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: AssemblyUnloadFinished'
title: Метод ICorProfilerCallback::AssemblyUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 30d6bd805a1466d6a65728b22f677ba00e09ffb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648029"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="f34bc-103">Метод ICorProfilerCallback::AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="f34bc-103">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>

<span data-ttu-id="f34bc-104">Уведомляет профилировщик о том, что сборка была выгружена.</span><span class="sxs-lookup"><span data-stu-id="f34bc-104">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f34bc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f34bc-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f34bc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f34bc-106">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="f34bc-107">\[в] определяет сборку, которая выгружается.</span><span class="sxs-lookup"><span data-stu-id="f34bc-107">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="f34bc-108">\[in] значение HRESULT, указывающее, успешно ли выгружена сборка.</span><span class="sxs-lookup"><span data-stu-id="f34bc-108">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="f34bc-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="f34bc-109">Remarks</span></span>  

 <span data-ttu-id="f34bc-110">Значение недопустимо `assemblyId` для информационного запроса после возврата метода [ICorProfilerCallback:: ассемблюнлоадстартед](icorprofilercallback-assemblyunloadstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f34bc-110">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="f34bc-111">Некоторые части выгрузки сборки могут продолжаться после `AssemblyUnloadFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="f34bc-111">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="f34bc-112">Ошибка HRESULT в `hrStatus` указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="f34bc-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="f34bc-113">Однако значение HRESULT в случае успеха в `hrStatus` указывает только на то, что первая часть выгрузки сборки завершилась успешно.</span><span class="sxs-lookup"><span data-stu-id="f34bc-113">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f34bc-114">Требования</span><span class="sxs-lookup"><span data-stu-id="f34bc-114">Requirements</span></span>  

 <span data-ttu-id="f34bc-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f34bc-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f34bc-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f34bc-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f34bc-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f34bc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f34bc-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f34bc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f34bc-119">См. также</span><span class="sxs-lookup"><span data-stu-id="f34bc-119">See also</span></span>

- [<span data-ttu-id="f34bc-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f34bc-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
