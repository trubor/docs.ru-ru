---
description: 'Дополнительные сведения о методе: метод icorprofilerinfo4:: GetFunctionFromIP2'
title: Метод ICorProfilerInfo4::GetFunctionFromIP2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
ms.openlocfilehash: f6abda7c9e7d4abcc0f0b256d6a7785cea205d7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686808"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="e91a5-103">Метод ICorProfilerInfo4::GetFunctionFromIP2</span><span class="sxs-lookup"><span data-stu-id="e91a5-103">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>

<span data-ttu-id="e91a5-104">Сопоставляет указатель инструкции управляемого кода с JIT-повторно скомпилированной версией функции.</span><span class="sxs-lookup"><span data-stu-id="e91a5-104">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e91a5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e91a5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e91a5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e91a5-106">Parameters</span></span>  

 `ip`  
 <span data-ttu-id="e91a5-107">окне Указатель инструкции в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="e91a5-107">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="e91a5-108">заполняет Идентификатор функции.</span><span class="sxs-lookup"><span data-stu-id="e91a5-108">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="e91a5-109">заполняет Удостоверение JIT-повторно скомпилированной версии функции.</span><span class="sxs-lookup"><span data-stu-id="e91a5-109">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e91a5-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="e91a5-110">Remarks</span></span>  

 <span data-ttu-id="e91a5-111">`GetFunctionFromIP2` функция похожа на `GetFunctionFromIP` , за исключением того, что он получает JIT-перекомпилированный идентификатор вместо идентификатора функции функции, которая содержит указанный IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="e91a5-111">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e91a5-112">`GetFunctionFromIP2` может запустить сборку мусора, тогда как это `GetFunctionFromIP` не будет.</span><span class="sxs-lookup"><span data-stu-id="e91a5-112">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="e91a5-113">Дополнительные сведения см. в разделе [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="e91a5-113">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e91a5-114">Требования</span><span class="sxs-lookup"><span data-stu-id="e91a5-114">Requirements</span></span>  

 <span data-ttu-id="e91a5-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e91a5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e91a5-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e91a5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e91a5-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e91a5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e91a5-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e91a5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e91a5-119">См. также</span><span class="sxs-lookup"><span data-stu-id="e91a5-119">See also</span></span>

- [<span data-ttu-id="e91a5-120">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="e91a5-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
