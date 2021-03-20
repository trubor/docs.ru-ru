---
description: 'Дополнительные сведения о методе: ICorProfilerInfo8:: GetFunctionFromIP3'
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 1b753350f45f722d60099b17cfdd48bfd06e411a
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759108"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="5e393-103">Метод ICorProfilerInfo8:: GetFunctionFromIP3</span><span class="sxs-lookup"><span data-stu-id="5e393-103">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="5e393-104">Сопоставляет указатель инструкции управляемого кода с FunctionID.</span><span class="sxs-lookup"><span data-stu-id="5e393-104">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="5e393-105">Этот метод работает как с динамическими, так и с нединамическими методами.</span><span class="sxs-lookup"><span data-stu-id="5e393-105">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="5e393-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5e393-106">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="5e393-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="5e393-107">Parameters</span></span>

<span data-ttu-id="5e393-108">`ip` окне Указатель инструкции в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="5e393-108">`ip` [in] The instruction pointer in managed code.</span></span>

<span data-ttu-id="5e393-109">`pFunctionId` заполняет Идентификатор функции.</span><span class="sxs-lookup"><span data-stu-id="5e393-109">`pFunctionId` [out] The function ID.</span></span>

<span data-ttu-id="5e393-110">`pReJitId` заполняет Удостоверение JIT-повторно скомпилированной версии функции.</span><span class="sxs-lookup"><span data-stu-id="5e393-110">`pReJitId` [out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="5e393-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="5e393-111">Remarks</span></span>

<span data-ttu-id="5e393-112">Этот метод работает как с динамическими, так и с нединамическими методами.</span><span class="sxs-lookup"><span data-stu-id="5e393-112">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="5e393-113">Это надмножество [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), который работает только для функций с метаданными.</span><span class="sxs-lookup"><span data-stu-id="5e393-113">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="5e393-114">Требования</span><span class="sxs-lookup"><span data-stu-id="5e393-114">Requirements</span></span>

<span data-ttu-id="5e393-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e393-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5e393-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5e393-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5e393-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e393-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5e393-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5e393-118">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5e393-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5e393-119">See also</span></span>

- [<span data-ttu-id="5e393-120">Интерфейс ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="5e393-120">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
