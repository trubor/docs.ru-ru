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
ms.openlocfilehash: 91c0b6a600a1c7c12905a7a9817e6e7e9601c3c0
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759473"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="21f8d-103">Метод ICorProfilerCallback::AssemblyUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="21f8d-103">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>

<span data-ttu-id="21f8d-104">Уведомляет профилировщик о выгрузке сборки.</span><span class="sxs-lookup"><span data-stu-id="21f8d-104">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21f8d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="21f8d-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21f8d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="21f8d-106">Parameters</span></span>

<span data-ttu-id="21f8d-107">`assemblyId` окне Определяет выгрузку сборки.</span><span class="sxs-lookup"><span data-stu-id="21f8d-107">`assemblyId` [in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="21f8d-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="21f8d-108">Remarks</span></span>  

 <span data-ttu-id="21f8d-109">Значение недопустимо `assemblyId` для информационного запроса после `AssemblyUnloadStarted` возврата метода — это последний шанс профилировщика получить сведения об этой сборке.</span><span class="sxs-lookup"><span data-stu-id="21f8d-109">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21f8d-110">Требования</span><span class="sxs-lookup"><span data-stu-id="21f8d-110">Requirements</span></span>  

 <span data-ttu-id="21f8d-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21f8d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21f8d-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21f8d-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21f8d-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21f8d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21f8d-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21f8d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f8d-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="21f8d-115">See also</span></span>

- [<span data-ttu-id="21f8d-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="21f8d-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="21f8d-117">Метод AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="21f8d-117">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
