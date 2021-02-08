---
description: 'Дополнительные сведения о методе: ICorProfilerCallback8::D Инамикмесоджиткомпилатионфинишед'
title: 'ICorProfilerCallback8: метод:D Инамикмесоджиткомпилатионфинишед'
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: d076307b9e57c27753297cad8eebc1b9aa9433f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781718"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="77e5d-103">ICorProfilerCallback8: метод:D Инамикмесоджиткомпилатионфинишед</span><span class="sxs-lookup"><span data-stu-id="77e5d-103">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>

<span data-ttu-id="77e5d-104">[Поддерживается в платформа .NET Framework 4,7 и более поздних версиях]</span><span class="sxs-lookup"><span data-stu-id="77e5d-104">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="77e5d-105">Уведомляет профилировщик о завершении JIT-компиляции динамического метода.</span><span class="sxs-lookup"><span data-stu-id="77e5d-105">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77e5d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77e5d-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77e5d-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="77e5d-107">Parameters</span></span>  

<span data-ttu-id="77e5d-108">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="77e5d-108">[in] `functionId`</span></span>  
<span data-ttu-id="77e5d-109">Идентификатор функции в памяти, для которой запускается JIT-компиляция.</span><span class="sxs-lookup"><span data-stu-id="77e5d-109">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="77e5d-110">[входные] `hrStatus` Значение, указывающее, была ли JIT-компиляция успешной.</span><span class="sxs-lookup"><span data-stu-id="77e5d-110">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="77e5d-111">[входные] `fIsSafeToBlock` 
 `true` чтобы указать, что блокировка может привести к тому, что среда выполнения будет ожидать возврата вызывающим потоком из этого обратного вызова. `false`чтобы указать, что блокировка не повлияет на работу среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="77e5d-111">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="77e5d-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="77e5d-112">Remarks</span></span>  

<span data-ttu-id="77e5d-113">Этот обратный вызов активируется каждый раз, когда JIT-компиляция динамического метода завершается.</span><span class="sxs-lookup"><span data-stu-id="77e5d-113">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="77e5d-114">Сюда входят различные суррогаты IL и методы LCG.</span><span class="sxs-lookup"><span data-stu-id="77e5d-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="77e5d-115">Его цель — предоставить средствам записи профилировщика достаточно информации для распознавания скомпилированного метода для пользователей.</span><span class="sxs-lookup"><span data-stu-id="77e5d-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="77e5d-116">`functionId` нельзя использовать значения для разрешения их маркеров метаданных, так как динамические методы не имеют метаданных.</span><span class="sxs-lookup"><span data-stu-id="77e5d-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="77e5d-117">Требования</span><span class="sxs-lookup"><span data-stu-id="77e5d-117">Requirements</span></span>  

 <span data-ttu-id="77e5d-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77e5d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77e5d-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="77e5d-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="77e5d-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77e5d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77e5d-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="77e5d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e5d-122">См. также</span><span class="sxs-lookup"><span data-stu-id="77e5d-122">See also</span></span>

- [<span data-ttu-id="77e5d-123">Метод DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="77e5d-123">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="77e5d-124">Интерфейс ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="77e5d-124">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
