---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ассемблюнлоадстартед'
title: Метод ICorProfilerCallback::AssemblyUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
ms.openlocfilehash: e9c72d481df7242f305b5efa6f747866984b31f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657842"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="37d2e-103">Метод ICorProfilerCallback::AssemblyUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="37d2e-103">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>

<span data-ttu-id="37d2e-104">Уведомляет профилировщик о выгрузке сборки.</span><span class="sxs-lookup"><span data-stu-id="37d2e-104">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37d2e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="37d2e-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37d2e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="37d2e-106">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="37d2e-107">\[в] определяет сборку, которая выгружается.</span><span class="sxs-lookup"><span data-stu-id="37d2e-107">\[in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="37d2e-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="37d2e-108">Remarks</span></span>  

 <span data-ttu-id="37d2e-109">Значение недопустимо `assemblyId` для информационного запроса после `AssemblyUnloadStarted` возврата метода — это последний шанс профилировщика получить сведения об этой сборке.</span><span class="sxs-lookup"><span data-stu-id="37d2e-109">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37d2e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="37d2e-110">Requirements</span></span>  

 <span data-ttu-id="37d2e-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37d2e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37d2e-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="37d2e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="37d2e-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37d2e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37d2e-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37d2e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37d2e-115">См. также</span><span class="sxs-lookup"><span data-stu-id="37d2e-115">See also</span></span>

- [<span data-ttu-id="37d2e-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="37d2e-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="37d2e-117">Метод AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="37d2e-117">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
