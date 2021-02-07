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
ms.openlocfilehash: 243660d3159e3c8c1d052c08e9c7499e7065d301
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753332"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="c0156-103">ICorProfilerCallback9: метод:D Инамикмесодунлоадед</span><span class="sxs-lookup"><span data-stu-id="c0156-103">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>

<span data-ttu-id="c0156-104">[Поддерживается в платформа .NET Framework 4.7.2 и более поздних версиях]</span><span class="sxs-lookup"><span data-stu-id="c0156-104">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="c0156-105">Уведомляет профилировщик каждый раз, когда динамический метод уничтожается сборщиком мусора и затем выгружается.</span><span class="sxs-lookup"><span data-stu-id="c0156-105">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0156-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c0156-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0156-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="c0156-107">Parameters</span></span>  

<span data-ttu-id="c0156-108">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="c0156-108">[in] `functionId`</span></span>  
<span data-ttu-id="c0156-109">Идентификатор функции в памяти, которая была собрана и выгружена сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="c0156-109">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="c0156-110">Требования</span><span class="sxs-lookup"><span data-stu-id="c0156-110">Requirements</span></span>  

 <span data-ttu-id="c0156-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0156-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0156-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c0156-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0156-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0156-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0156-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c0156-114">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0156-115">См. также</span><span class="sxs-lookup"><span data-stu-id="c0156-115">See also</span></span>

- [<span data-ttu-id="c0156-116">ICorProfilerCallback8. Динамикмесоджиткомпилатионстартед, метод</span><span class="sxs-lookup"><span data-stu-id="c0156-116">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="c0156-117">ICorProfilerCallback8. Динамикмесоджиткомпилатионфинишед, метод</span><span class="sxs-lookup"><span data-stu-id="c0156-117">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="c0156-118">Интерфейс ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="c0156-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="c0156-119">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="c0156-119">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
