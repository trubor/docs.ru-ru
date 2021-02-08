---
description: 'Дополнительные сведения о методе: ICorProfilerCallback4:: Жетрежитпараметерс'
title: Метод ICorProfilerCallback4::GetReJITParameters
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: f8dbf2c6ae80e41b8427fdaf0ef617a83138bb14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788765"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="ae7f2-103">Метод ICorProfilerCallback4::GetReJITParameters</span><span class="sxs-lookup"><span data-stu-id="ae7f2-103">ICorProfilerCallback4::GetReJITParameters Method</span></span>

<span data-ttu-id="ae7f2-104">Позволяет профилировщику кода устанавливать альтернативные флаги создания кода для нового текста перекомпилированного метода.</span><span class="sxs-lookup"><span data-stu-id="ae7f2-104">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae7f2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ae7f2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae7f2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ae7f2-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="ae7f2-107">окне Модуль, содержащий метод, для которого среда CLR требует параметры JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="ae7f2-107">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="ae7f2-108">окне `MethodDef` Метод, для которого среда CLR требует параметры JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="ae7f2-108">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="ae7f2-109">окне Указатель на интерфейс [икорпрофилерфунктионконтрол](icorprofilerfunctioncontrol-interface.md) , который профилировщик может использовать для предоставления сведений о JIT-компиляции для метода, для которого выполняется повторная компиляция.</span><span class="sxs-lookup"><span data-stu-id="ae7f2-109">[in] A pointer to an [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae7f2-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="ae7f2-110">Remarks</span></span>  

 <span data-ttu-id="ae7f2-111">Среда CLR выдает `GetReJITParameters` обратный вызов, чтобы профилировщик мог указать параметры для перекомпиляции данного метода.</span><span class="sxs-lookup"><span data-stu-id="ae7f2-111">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="ae7f2-112">`GetReJITParameters`Обратный вызов выдается только один раз для каждой функции; параметры, предоставляемые профилировщиком, применяются ко всем экземплярам этой функции.</span><span class="sxs-lookup"><span data-stu-id="ae7f2-112">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae7f2-113">Требования</span><span class="sxs-lookup"><span data-stu-id="ae7f2-113">Requirements</span></span>  

 <span data-ttu-id="ae7f2-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae7f2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae7f2-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ae7f2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae7f2-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae7f2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae7f2-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae7f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae7f2-118">См. также</span><span class="sxs-lookup"><span data-stu-id="ae7f2-118">See also</span></span>

- [<span data-ttu-id="ae7f2-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ae7f2-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ae7f2-120">Интерфейс ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="ae7f2-120">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="ae7f2-121">Метод JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="ae7f2-121">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="ae7f2-122">Метод ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="ae7f2-122">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
