---
description: 'Дополнительные сведения о методе: ICorProfilerCallback9::D Инамикмесодунлоадед'
title: 'ICorProfilerCallback9: метод:D Инамикмесодунлоадед'
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: bc7f95b5101658c93eeb9fcef51e9c0f1bd2f2bd
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760201"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="9866e-103">ICorProfilerCallback9: метод:D Инамикмесодунлоадед</span><span class="sxs-lookup"><span data-stu-id="9866e-103">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>

<span data-ttu-id="9866e-104">[Поддерживается в платформа .NET Framework 4.7.2 и более поздних версиях]</span><span class="sxs-lookup"><span data-stu-id="9866e-104">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="9866e-105">Уведомляет профилировщик каждый раз, когда динамический метод уничтожается сборщиком мусора и затем выгружается.</span><span class="sxs-lookup"><span data-stu-id="9866e-105">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9866e-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9866e-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9866e-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="9866e-107">Parameters</span></span>  

<span data-ttu-id="9866e-108">`functionId` окне Идентификатор функции в памяти, которая была собрана и выгружена сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="9866e-108">`functionId` [in] The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="9866e-109">Требования</span><span class="sxs-lookup"><span data-stu-id="9866e-109">Requirements</span></span>  

 <span data-ttu-id="9866e-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9866e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9866e-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9866e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9866e-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9866e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9866e-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9866e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9866e-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9866e-114">See also</span></span>

- [<span data-ttu-id="9866e-115">ICorProfilerCallback8. Динамикмесоджиткомпилатионстартед, метод</span><span class="sxs-lookup"><span data-stu-id="9866e-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="9866e-116">ICorProfilerCallback8. Динамикмесоджиткомпилатионфинишед, метод</span><span class="sxs-lookup"><span data-stu-id="9866e-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="9866e-117">Интерфейс ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="9866e-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="9866e-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="9866e-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
