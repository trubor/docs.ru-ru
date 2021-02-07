---
description: 'Дополнительные сведения о методе: метод icorprofilerinfo4:: GetCodeInfo3'
title: Метод ICorProfilerInfo4::GetCodeInfo3
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
ms.openlocfilehash: 6bc2beb291101257448ab58ac9a93362005fecbe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686832"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="bee8e-103">Метод ICorProfilerInfo4::GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="bee8e-103">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>

<span data-ttu-id="bee8e-104">Получает экстенты машинного кода, связанного с перекомпилированной с помощью JIT-компилятора версией указанной функции.</span><span class="sxs-lookup"><span data-stu-id="bee8e-104">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bee8e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bee8e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bee8e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bee8e-106">Parameters</span></span>  

 `functionID`  
 <span data-ttu-id="bee8e-107">[in] Идентификатор функции, с которым связан машинный код.</span><span class="sxs-lookup"><span data-stu-id="bee8e-107">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="bee8e-108">[in] Идентификатор функции, перекомпилированной с помощью JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="bee8e-108">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="bee8e-109">[in] Размер массива `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="bee8e-109">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="bee8e-110">заполняет Указатель на общее число доступных структур [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="bee8e-110">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="bee8e-111">[out] Буфер, предоставляемый вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="bee8e-111">[out] A caller-provided buffer.</span></span> <span data-ttu-id="bee8e-112">После возврата метода он содержит массив структур `COR_PRF_CODE_INFO`, каждая из которых описывает блок машинного кода.</span><span class="sxs-lookup"><span data-stu-id="bee8e-112">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bee8e-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="bee8e-113">Remarks</span></span>  

 <span data-ttu-id="bee8e-114">`GetCodeInfo3`Метод аналогичен [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md), за исключением того, что он получает JIT-перекомпилированный идентификатор функции, которая содержит указанный IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="bee8e-114">The `GetCodeInfo3` method is similar to [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bee8e-115">`GetCodeInfo3` может запустить сборку мусора, в то время как [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) не будет.</span><span class="sxs-lookup"><span data-stu-id="bee8e-115">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="bee8e-116">Дополнительные сведения см. в [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="bee8e-116">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="bee8e-117">Расширения сортируются в порядке возрастания смещения общих промежуточного языка (CIL).</span><span class="sxs-lookup"><span data-stu-id="bee8e-117">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="bee8e-118">После `GetCodeInfo3` возврата необходимо убедиться, что `codeInfos` буфер достаточно велик, чтобы вместить все структуры [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="bee8e-118">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="bee8e-119">Для этого сравните значение параметра `cCodeInfos` со значением параметра `cchName`.</span><span class="sxs-lookup"><span data-stu-id="bee8e-119">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="bee8e-120">При `cCodeInfos` делении на размер структуры [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) меньше `pcCodeInfos` , выделяет буфер большего размера `codeInfos` , обновляет `cCodeInfos` новый, больший размер и вызывается `GetCodeInfo3` снова.</span><span class="sxs-lookup"><span data-stu-id="bee8e-120">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="bee8e-121">Кроме того, сначала можно вызвать метод `GetCodeInfo3` с буфером `codeInfos` нулевой длины для получения правильного размера буфера.</span><span class="sxs-lookup"><span data-stu-id="bee8e-121">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="bee8e-122">Затем можно присвоить `codeInfos` Размер буфера значению, возвращенному в `pcCodeInfos` , умноженному на размер структуры [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) и вызывать `GetCodeInfo3` повторно.</span><span class="sxs-lookup"><span data-stu-id="bee8e-122">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bee8e-123">Требования</span><span class="sxs-lookup"><span data-stu-id="bee8e-123">Requirements</span></span>  

 <span data-ttu-id="bee8e-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bee8e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bee8e-125">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bee8e-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bee8e-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bee8e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bee8e-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bee8e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bee8e-128">См. также</span><span class="sxs-lookup"><span data-stu-id="bee8e-128">See also</span></span>

- [<span data-ttu-id="bee8e-129">Метод GetCodeInfo2</span><span class="sxs-lookup"><span data-stu-id="bee8e-129">GetCodeInfo2 Method</span></span>](icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="bee8e-130">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="bee8e-130">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="bee8e-131">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="bee8e-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="bee8e-132">Профилирование</span><span class="sxs-lookup"><span data-stu-id="bee8e-132">Profiling</span></span>](index.md)
