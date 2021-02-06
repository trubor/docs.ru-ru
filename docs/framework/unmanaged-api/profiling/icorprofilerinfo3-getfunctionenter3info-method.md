---
description: 'Дополнительные сведения о методе: ICorProfilerInfo3:: GetFunctionEnter3Info'
title: Метод ICorProfilerInfo3::GetFunctionEnter3Info
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
ms.openlocfilehash: 3e6c0cfbf2518301e62ed5c57e956190066504ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646820"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="8a9dc-103">Метод ICorProfilerInfo3::GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="8a9dc-103">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>

<span data-ttu-id="8a9dc-104">Предоставляет кадр стека и сведения о аргументах функции, о которой сообщается профилировщику функцией [FunctionEnter3WithInfo](functionenter3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="8a9dc-104">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="8a9dc-105">Этот метод может быть вызван только во время обратного вызова `FunctionEnter3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="8a9dc-105">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a9dc-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8a9dc-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a9dc-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="8a9dc-107">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="8a9dc-108">[in] `FunctionID` функции, которая вводится.</span><span class="sxs-lookup"><span data-stu-id="8a9dc-108">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="8a9dc-109">[in] Непрозрачный дескриптор, представляющий сведения об указанном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="8a9dc-109">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="8a9dc-110">Профилировщик должен предоставить те же данные `eltInfo` , что и функция [FunctionEnter3WithInfo](functionenter3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="8a9dc-110">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="8a9dc-111">[out] Непрозрачный дескриптор, представляющий универсальные сведения об указанном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="8a9dc-111">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="8a9dc-112">Этот дескриптор допустим только во время обратного вызова `FunctionEnter3WithInfo`, в котором профилировщик вызывал метод `GetFunctionEnter3Info`.</span><span class="sxs-lookup"><span data-stu-id="8a9dc-112">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="8a9dc-113">[вход, выход] Указатель на общий размер (в байтах) структуры [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) (плюс все дополнительные структуры [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) для диапазонов аргументов, на которые указывает параметр `pArgumentInfo` ).</span><span class="sxs-lookup"><span data-stu-id="8a9dc-113">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="8a9dc-114">Если указанный размер недостаточен, то возвращается значение ERROR_INSUFFICIENT_BUFFER, и ожидаемый размер сохраняется в `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="8a9dc-114">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="8a9dc-115">Чтобы вызвать `GetFunctionEnter3Info` только для получения ожидаемого значения для `*pcbArgumentInfo`, установите `*pcbArgumentInfo`= 0 и `pArgumentInfo`= NULL.</span><span class="sxs-lookup"><span data-stu-id="8a9dc-115">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="8a9dc-116">заполняет Указатель на структуру [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) , описывающую расположения аргументов функции в памяти в порядке слева направо.</span><span class="sxs-lookup"><span data-stu-id="8a9dc-116">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a9dc-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="8a9dc-117">Remarks</span></span>  

 <span data-ttu-id="8a9dc-118">Профилировщик должен выделить достаточно места для структуры `COR_PRF_FUNCTION_ARGUMENT_INFO` проверяемой функции, и должен указать размер в параметре `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="8a9dc-118">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a9dc-119">Требования</span><span class="sxs-lookup"><span data-stu-id="8a9dc-119">Requirements</span></span>  

 <span data-ttu-id="8a9dc-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a9dc-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a9dc-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a9dc-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a9dc-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a9dc-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a9dc-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a9dc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a9dc-124">См. также</span><span class="sxs-lookup"><span data-stu-id="8a9dc-124">See also</span></span>

- [<span data-ttu-id="8a9dc-125">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="8a9dc-125">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="8a9dc-126">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="8a9dc-126">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="8a9dc-127">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="8a9dc-127">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="8a9dc-128">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="8a9dc-128">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="8a9dc-129">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="8a9dc-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="8a9dc-130">Профилирование</span><span class="sxs-lookup"><span data-stu-id="8a9dc-130">Profiling</span></span>](index.md)
