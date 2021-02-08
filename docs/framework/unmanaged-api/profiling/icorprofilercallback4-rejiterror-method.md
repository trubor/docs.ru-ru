---
description: 'Дополнительные сведения о методе: ICorProfilerCallback4:: Режитеррор'
title: Метод ICorProfilerCallback4::ReJITError
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
ms.openlocfilehash: f5173d90e65a1e9f1049ba7eadc1ce9cf7630096
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788700"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="24627-103">Метод ICorProfilerCallback4::ReJITError</span><span class="sxs-lookup"><span data-stu-id="24627-103">ICorProfilerCallback4::ReJITError Method</span></span>

<span data-ttu-id="24627-104">Уведомляет профилировщик о том, что компилятор JIT обнаружил ошибку в процессе перекомпиляции.</span><span class="sxs-lookup"><span data-stu-id="24627-104">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24627-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="24627-105">Syntax</span></span>  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24627-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="24627-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="24627-107">окне Объект, `ModuleID` в котором была выполнена повторная попытка повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="24627-107">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="24627-108">окне `MethodDef` Метод метода, для которого была выполнена попытка повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="24627-108">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="24627-109">окне Экземпляр функции, который перекомпилируется или помечен для повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="24627-109">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="24627-110">Это значение может быть `NULL` , если ошибка возникла для каждого метода, а не для каждого экземпляра (например, если профилировщик указал недопустимый токен метаданных для повторной компиляции метода).</span><span class="sxs-lookup"><span data-stu-id="24627-110">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="24627-111">окне Значение HRESULT, указывающее природу сбоя.</span><span class="sxs-lookup"><span data-stu-id="24627-111">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="24627-112">Список значений см. в разделе Status HRESULTs.</span><span class="sxs-lookup"><span data-stu-id="24627-112">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24627-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="24627-113">Return Value</span></span>  

 <span data-ttu-id="24627-114">Значения, возвращаемые из этого обратного вызова, игнорируются.</span><span class="sxs-lookup"><span data-stu-id="24627-114">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="24627-115">Значения HRESULT для состояния</span><span class="sxs-lookup"><span data-stu-id="24627-115">Status HRESULTS</span></span>  
  
|<span data-ttu-id="24627-116">Массив значений HRESULT для состояния</span><span class="sxs-lookup"><span data-stu-id="24627-116">Status array HRESULT</span></span>|<span data-ttu-id="24627-117">Описание</span><span class="sxs-lookup"><span data-stu-id="24627-117">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="24627-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="24627-118">E_INVALIDARG</span></span>|<span data-ttu-id="24627-119">`moduleID`Токен или `methodDef` имеет значение `NULL` .</span><span class="sxs-lookup"><span data-stu-id="24627-119">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="24627-120">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="24627-120">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="24627-121">Модуль еще не полностью загружен или находится в процессе выгрузки.</span><span class="sxs-lookup"><span data-stu-id="24627-121">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="24627-122">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="24627-122">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="24627-123">Указанный модуль был динамически создан (например, by `Reflection.Emit` ) и поэтому не поддерживается этим методом.</span><span class="sxs-lookup"><span data-stu-id="24627-123">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="24627-124">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="24627-124">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="24627-125">Экземпляр метода создается в собираемой сборке и поэтому не может быть перекомпилирован.</span><span class="sxs-lookup"><span data-stu-id="24627-125">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="24627-126">Обратите внимание, что типы и функции, определенные в контексте, не являющемся контекстом отражения (например, `List<MyCollectibleStruct>` ), можно создать в собираемой сборке.</span><span class="sxs-lookup"><span data-stu-id="24627-126">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="24627-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="24627-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="24627-128">В среде CLR возникла нехватка памяти при попытке пометить указанный метод для повторной компиляции JIT.</span><span class="sxs-lookup"><span data-stu-id="24627-128">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="24627-129">Другое</span><span class="sxs-lookup"><span data-stu-id="24627-129">Other</span></span>|<span data-ttu-id="24627-130">Операционная система возвратила сбой за пределами среды CLR.</span><span class="sxs-lookup"><span data-stu-id="24627-130">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="24627-131">Например, если системный вызов для изменения защиты доступа к странице памяти завершается ошибкой, отображается сообщение об ошибке операционной системы.</span><span class="sxs-lookup"><span data-stu-id="24627-131">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="24627-132">Требования</span><span class="sxs-lookup"><span data-stu-id="24627-132">Requirements</span></span>  

 <span data-ttu-id="24627-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24627-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24627-134">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24627-134">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24627-135">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24627-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24627-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24627-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24627-137">См. также</span><span class="sxs-lookup"><span data-stu-id="24627-137">See also</span></span>

- [<span data-ttu-id="24627-138">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="24627-138">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="24627-139">Интерфейс ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="24627-139">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
