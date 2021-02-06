---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: GetFunctionInfo2'
title: Метод ICorProfilerInfo2::GetFunctionInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
ms.openlocfilehash: f0534a2e8cc8a9ce24f2c2b3deaade6215e15b5a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657077"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="bd36b-103">Метод ICorProfilerInfo2::GetFunctionInfo2</span><span class="sxs-lookup"><span data-stu-id="bd36b-103">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>

<span data-ttu-id="bd36b-104">Получает родительский класс, токен метаданных и `ClassID` для каждого аргумента типа функции при их наличии.</span><span class="sxs-lookup"><span data-stu-id="bd36b-104">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd36b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bd36b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd36b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bd36b-106">Parameters</span></span>  

 `funcId`  
 <span data-ttu-id="bd36b-107">[входной] Идентификатор функции, для которой нужно получить родительский класс и другую информацию.</span><span class="sxs-lookup"><span data-stu-id="bd36b-107">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="bd36b-108">[входной] Значение `COR_PRF_FRAME_INFO`, указывающее на информацию о кадре стека.</span><span class="sxs-lookup"><span data-stu-id="bd36b-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="bd36b-109">[выходной] Указатель на родительский класс функции.</span><span class="sxs-lookup"><span data-stu-id="bd36b-109">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="bd36b-110">[выходной] Указатель на модуль, в котором определен родительский класс функции.</span><span class="sxs-lookup"><span data-stu-id="bd36b-110">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="bd36b-111">[выходной] Указатель на токен метаданных функции.</span><span class="sxs-lookup"><span data-stu-id="bd36b-111">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="bd36b-112">[in] Размер массива `typeArgs`.</span><span class="sxs-lookup"><span data-stu-id="bd36b-112">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="bd36b-113">[выходной] Указатель на общее количество значений `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="bd36b-113">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="bd36b-114">[выходной] Массив значений `ClassID`, каждое из которых является идентификатором аргумента типа функции.</span><span class="sxs-lookup"><span data-stu-id="bd36b-114">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="bd36b-115">При возврате из метода в параметре `typeArgs` содержатся все или некоторые значения `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="bd36b-115">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd36b-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="bd36b-116">Remarks</span></span>  

 <span data-ttu-id="bd36b-117">Чтобы получить интерфейс [метаданных](../metadata/index.md) для заданного модуля, код профилировщика может вызвать метод [ICorProfilerInfo:: жетмодулеметадата](icorprofilerinfo-getmodulemetadata-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bd36b-117">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="bd36b-118">Токен метаданных, возвращенный в расположение, на которое ссылается `pToken`, можно впоследствии использовать для доступа к метаданным функции.</span><span class="sxs-lookup"><span data-stu-id="bd36b-118">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="bd36b-119">Идентификатор класса и аргументы типа, возвращенные с помощью параметров `pClassId` и `typeArgs`, зависят от значения, переданного в параметре `frameInfo`, как показано в таблице ниже.</span><span class="sxs-lookup"><span data-stu-id="bd36b-119">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="bd36b-120">Значение параметра `frameInfo`</span><span class="sxs-lookup"><span data-stu-id="bd36b-120">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="bd36b-121">Результат</span><span class="sxs-lookup"><span data-stu-id="bd36b-121">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="bd36b-122">Значение `COR_PRF_FRAME_INFO`, полученное в результате обратного вызова `FunctionEnter2`</span><span class="sxs-lookup"><span data-stu-id="bd36b-122">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="bd36b-123">Значение `ClassID`, возвращенное в расположении, на которое ссылается параметр `pClassId`, и все аргументы типа, возвращенные в массиве `typeArgs`, будут точными.</span><span class="sxs-lookup"><span data-stu-id="bd36b-123">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="bd36b-124">Объект `COR_PRF_FRAME_INFO`, полученный из источника, отличного от обратного вызова `FunctionEnter2`</span><span class="sxs-lookup"><span data-stu-id="bd36b-124">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="bd36b-125">Точное значение `ClassID` и аргументы типа определить нельзя.</span><span class="sxs-lookup"><span data-stu-id="bd36b-125">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="bd36b-126">То есть, `ClassID` может иметь значение NULL, а некоторые аргументы типа могут быть возвращены в виде объекта <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="bd36b-126">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="bd36b-127">Нуль</span><span class="sxs-lookup"><span data-stu-id="bd36b-127">Zero</span></span>|<span data-ttu-id="bd36b-128">Точное значение `ClassID` и аргументы типа определить нельзя.</span><span class="sxs-lookup"><span data-stu-id="bd36b-128">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="bd36b-129">То есть, `ClassID` может иметь значение NULL, а некоторые аргументы типа могут быть возвращены в виде объекта <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="bd36b-129">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="bd36b-130">После возврата метода `GetFunctionInfo2` необходимо убедиться, что буфер `typeArgs` был достаточно велик, чтобы вместить в себя все значения `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="bd36b-130">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="bd36b-131">Для этого сравните значение, на которое указывает параметр `pcTypeArgs`, со значением параметра `cTypeArgs`.</span><span class="sxs-lookup"><span data-stu-id="bd36b-131">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="bd36b-132">Если параметр `pcTypeArgs` указывает на значение, превышающее значение `cTypeArgs`, деленное на размер значения `ClassID`, нужно выделить буфер `pcTypeArgs` большего размера, обновить параметр `cTypeArgs`, задав новый, больший размер и вызвать метод `GetFunctionInfo2` снова.</span><span class="sxs-lookup"><span data-stu-id="bd36b-132">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="bd36b-133">Кроме того, сначала можно вызвать метод `GetFunctionInfo2` с буфером `pcTypeArgs` нулевой длины для получения правильного размера буфера.</span><span class="sxs-lookup"><span data-stu-id="bd36b-133">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="bd36b-134">Затем можно задать размер буфера равным значению, возвращенному в параметре `pcTypeArgs`, деленному на размер значения `ClassID`, и вызвать метод `GetFunctionInfo2` снова.</span><span class="sxs-lookup"><span data-stu-id="bd36b-134">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd36b-135">Требования</span><span class="sxs-lookup"><span data-stu-id="bd36b-135">Requirements</span></span>  

 <span data-ttu-id="bd36b-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd36b-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd36b-137">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bd36b-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd36b-138">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd36b-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd36b-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd36b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd36b-140">См. также</span><span class="sxs-lookup"><span data-stu-id="bd36b-140">See also</span></span>

- [<span data-ttu-id="bd36b-141">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="bd36b-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="bd36b-142">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="bd36b-142">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="bd36b-143">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="bd36b-143">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="bd36b-144">Профилирование</span><span class="sxs-lookup"><span data-stu-id="bd36b-144">Profiling</span></span>](index.md)
