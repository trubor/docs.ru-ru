---
description: 'Дополнительные сведения о: интерфейс Икорпрофилерфунктионконтрол'
title: Интерфейс ICorProfilerFunctionControl
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
ms.openlocfilehash: 7b4ac58d2b8754108b4e10493596776987a93a49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753319"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="e4dfb-103">Интерфейс ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="e4dfb-103">ICorProfilerFunctionControl Interface</span></span>

<span data-ttu-id="e4dfb-104">Предоставляет методы, позволяющие профилировщику кода взаимодействовать со средой выполнения CLR и контролировать порядок генерирования кода JIT-компилятором при повторной компиляции указанного метода.</span><span class="sxs-lookup"><span data-stu-id="e4dfb-104">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4dfb-105">Методы</span><span class="sxs-lookup"><span data-stu-id="e4dfb-105">Methods</span></span>  
  
|<span data-ttu-id="e4dfb-106">Метод</span><span class="sxs-lookup"><span data-stu-id="e4dfb-106">Method</span></span>|<span data-ttu-id="e4dfb-107">Описание</span><span class="sxs-lookup"><span data-stu-id="e4dfb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4dfb-108">Метод SetCodegenFlags</span><span class="sxs-lookup"><span data-stu-id="e4dfb-108">SetCodegenFlags Method</span></span>](icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="e4dfb-109">Задает один или несколько флагов из перечисления [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) для управления созданием кода для перекомпилированной функции JIT.</span><span class="sxs-lookup"><span data-stu-id="e4dfb-109">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="e4dfb-110">Метод SetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="e4dfb-110">SetILFunctionBody Method</span></span>](icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="e4dfb-111">Заменяет тело метода на языке CIL.</span><span class="sxs-lookup"><span data-stu-id="e4dfb-111">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="e4dfb-112">Метод SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="e4dfb-112">SetILInstrumentedCodeMap Method</span></span>](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="e4dfb-113">Устанавливает карту кода для указанной функции с помощью указанных записей карты языка CIL.</span><span class="sxs-lookup"><span data-stu-id="e4dfb-113">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4dfb-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="e4dfb-114">Remarks</span></span>  

 <span data-ttu-id="e4dfb-115">Интерфейс `ICorProfilerFunctionControl` предоставляет методы для генерации управляющего кода для одной перекомпилированной функции.</span><span class="sxs-lookup"><span data-stu-id="e4dfb-115">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="e4dfb-116">Профилировщик получает экземпляр этого интерфейса через обратный вызов [ICorProfilerCallback4:: жетрежитпараметерс](icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e4dfb-116">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="e4dfb-117">Каждый экземпляр `ICorProfilerFunctionControl` управляет всеми экземплярами одной функции.</span><span class="sxs-lookup"><span data-stu-id="e4dfb-117">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4dfb-118">Требования</span><span class="sxs-lookup"><span data-stu-id="e4dfb-118">Requirements</span></span>  

 <span data-ttu-id="e4dfb-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4dfb-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4dfb-120">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e4dfb-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4dfb-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4dfb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4dfb-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4dfb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4dfb-123">См. также</span><span class="sxs-lookup"><span data-stu-id="e4dfb-123">See also</span></span>

- [<span data-ttu-id="e4dfb-124">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="e4dfb-124">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="e4dfb-125">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="e4dfb-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e4dfb-126">Метод EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="e4dfb-126">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)
