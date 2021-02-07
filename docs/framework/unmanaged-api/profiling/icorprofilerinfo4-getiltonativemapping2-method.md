---
description: 'Дополнительные сведения о методе: метод icorprofilerinfo4:: GetILToNativeMapping2'
title: Метод ICorProfilerInfo4::GetILToNativeMapping2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
ms.openlocfilehash: f548dbef3444c6e63e51cd5f3db79e567b2630b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686795"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="fdb20-103">Метод ICorProfilerInfo4::GetILToNativeMapping2</span><span class="sxs-lookup"><span data-stu-id="fdb20-103">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>

<span data-ttu-id="fdb20-104">Получает сопоставление из смещений MSIL в собственные смещения для кода, содержащегося в версии указанной функции, перекомпилированной с помощью JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="fdb20-104">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdb20-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fdb20-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdb20-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fdb20-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="fdb20-107">[in] Идентификатор функции, которая содержит код.</span><span class="sxs-lookup"><span data-stu-id="fdb20-107">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="fdb20-108">[in] Идентификатор функции, перекомпилированной с помощью JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="fdb20-108">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="fdb20-109">Удостоверение должно быть равно нулю в платформа .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="fdb20-109">The identity must be zero in the .NET Framework 4.5.</span></span>  
  
 `cMap`  
 <span data-ttu-id="fdb20-110">[in] Максимальный размер массива `map`.</span><span class="sxs-lookup"><span data-stu-id="fdb20-110">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="fdb20-111">[out] Общее количество доступных структур COR_DEBUG_IL_TO_NATIVE_MAP.</span><span class="sxs-lookup"><span data-stu-id="fdb20-111">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="fdb20-112">[out] Массив структур `COR_DEBUG_IL_TO_NATIVE_MAP`, каждая из которых задает смещения.</span><span class="sxs-lookup"><span data-stu-id="fdb20-112">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="fdb20-113">После возврата метода `GetILToNativeMapping2` параметр `map` будет содержать все или некоторые из структур `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="fdb20-113">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdb20-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="fdb20-114">Remarks</span></span>  

 <span data-ttu-id="fdb20-115">`GetILToNativeMapping2` аналогичен методу [ICorProfilerInfo:: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) , за исключением того, что он позволяет профилировщику указать идентификатор перекомпилированной функции в будущих выпусках.</span><span class="sxs-lookup"><span data-stu-id="fdb20-115">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fdb20-116">Метод [икорпрофилерфунктионконтрол:: сетилинструментедкодемап](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) не реализован в платформа .NET Framework 4,5, поэтому функции, которые были JIT-скомпилированы, не могут иметь сопоставление с IL-кодом, которое отличается от первоначально скомпилированной функции.</span><span class="sxs-lookup"><span data-stu-id="fdb20-116">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="fdb20-117">Таким образом, `GetILToNativeMapping2` не может вызываться с ненулевым JIT-перекомпилированным идентификатором в платформа .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="fdb20-117">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="fdb20-118">Метод `GetILToNativeMapping2` возвращает массив структур `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="fdb20-118">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="fdb20-119">Чтобы убедиться, что определенные диапазоны машинных инструкций соответствуют специальным областям кода (например, прологу), в качестве поля в массиве можно `ilOffset` задать значение перечисления [кордебугилтонативемаппингтипес](../debugging/cordebugiltonativemappingtypes-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="fdb20-119">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="fdb20-120">После возврата метода `GetILToNativeMapping2` необходимо убедиться, что буфер `map` был достаточно велик, чтобы вместить в себя все структуры `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="fdb20-120">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="fdb20-121">Для этого сравните значение параметра `cMap` со значением параметра `pcMap`.</span><span class="sxs-lookup"><span data-stu-id="fdb20-121">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="fdb20-122">Если значение `pcMap`, умноженное на размер структуры `COR_DEBUG_IL_TO_NATIVE_MAP`COR_PRF_CODE_INFO, больше значения `cMap`, выделите буфер `map` большего размера, обновите параметр `cMap`, задав новый, больший размер, и вызовите метод `GetILToNativeMapping2` снова.</span><span class="sxs-lookup"><span data-stu-id="fdb20-122">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="fdb20-123">Кроме того, сначала можно вызвать метод `GetILToNativeMapping2` с буфером `map` нулевой длины для получения правильного размера буфера.</span><span class="sxs-lookup"><span data-stu-id="fdb20-123">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="fdb20-124">Затем можно задать размер буфера равным значению, возвращенному в параметре `pcMap`, и вызвать метод `GetILToNativeMapping2` снова.</span><span class="sxs-lookup"><span data-stu-id="fdb20-124">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdb20-125">Требования</span><span class="sxs-lookup"><span data-stu-id="fdb20-125">Requirements</span></span>  

 <span data-ttu-id="fdb20-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdb20-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdb20-127">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fdb20-127">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fdb20-128">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdb20-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdb20-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdb20-129">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb20-130">См. также</span><span class="sxs-lookup"><span data-stu-id="fdb20-130">See also</span></span>

- [<span data-ttu-id="fdb20-131">Метод GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="fdb20-131">GetILToNativeMapping Method</span></span>](icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="fdb20-132">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="fdb20-132">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="fdb20-133">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="fdb20-133">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="fdb20-134">Профилирование</span><span class="sxs-lookup"><span data-stu-id="fdb20-134">Profiling</span></span>](index.md)
