---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: GetCodeInfo2'
title: Метод ICorProfilerInfo2::GetCodeInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 69b877b2dfe3bf23cd2b13417386c45d51de44d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760523"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="e5988-103">Метод ICorProfilerInfo2::GetCodeInfo2</span><span class="sxs-lookup"><span data-stu-id="e5988-103">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>

<span data-ttu-id="e5988-104">Получает экстенты машинного кода, связанного с указанным `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="e5988-104">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5988-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e5988-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5988-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e5988-106">Parameters</span></span>  

 `functionID`  
 <span data-ttu-id="e5988-107">[in] Идентификатор функции, с которым связан машинный код.</span><span class="sxs-lookup"><span data-stu-id="e5988-107">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="e5988-108">[in] Размер массива `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="e5988-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="e5988-109">заполняет Указатель на общее число доступных структур [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="e5988-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="e5988-110">[out] Буфер, предоставляемый вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="e5988-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="e5988-111">После возврата метода он содержит массив структур `COR_PRF_CODE_INFO`, каждая из которых описывает блок машинного кода.</span><span class="sxs-lookup"><span data-stu-id="e5988-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5988-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="e5988-112">Remarks</span></span>  

 <span data-ttu-id="e5988-113">Экстенты сортируются в порядке возрастания смещения MCIL.</span><span class="sxs-lookup"><span data-stu-id="e5988-113">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="e5988-114">После возврата метода `GetCodeInfo2` необходимо убедиться, что буфер `codeInfos` был достаточно велик, чтобы вместить в себя все структуры `COR_PRF_CODE_INFO`.</span><span class="sxs-lookup"><span data-stu-id="e5988-114">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="e5988-115">Для этого сравните значение параметра `cCodeInfos` со значением параметра `cchName`.</span><span class="sxs-lookup"><span data-stu-id="e5988-115">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="e5988-116">Если значение `cCodeInfos`, деленное на размер структуры `COR_PRF_CODE_INFO`, меньше значения `pcCodeInfos`, выделите буфер `codeInfos` большего размера, обновите параметр `cCodeInfos`, задав новый, больший размер, и вызовите метод `GetCodeInfo2` снова.</span><span class="sxs-lookup"><span data-stu-id="e5988-116">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="e5988-117">Кроме того, сначала можно вызвать метод `GetCodeInfo2` с буфером `codeInfos` нулевой длины для получения правильного размера буфера.</span><span class="sxs-lookup"><span data-stu-id="e5988-117">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="e5988-118">Затем можно задать размер буфера `codeInfos` равным значению, возвращенному в параметре `pcCodeInfos` и умноженному на размер структуры `COR_PRF_CODE_INFO`, и вызвать метод `GetCodeInfo2` снова.</span><span class="sxs-lookup"><span data-stu-id="e5988-118">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5988-119">Требования</span><span class="sxs-lookup"><span data-stu-id="e5988-119">Requirements</span></span>  

 <span data-ttu-id="e5988-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5988-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5988-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e5988-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5988-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5988-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5988-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5988-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5988-124">См. также</span><span class="sxs-lookup"><span data-stu-id="e5988-124">See also</span></span>

- [<span data-ttu-id="e5988-125">Метод GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="e5988-125">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="e5988-126">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="e5988-126">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="e5988-127">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="e5988-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e5988-128">Профилирование</span><span class="sxs-lookup"><span data-stu-id="e5988-128">Profiling</span></span>](index.md)
