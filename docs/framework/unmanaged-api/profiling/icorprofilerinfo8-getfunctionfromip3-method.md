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
ms.openlocfilehash: 3ce0a0964e26254ab09e515826b6bceb657e07bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783837"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="916b4-103">Метод ICorProfilerInfo8:: GetFunctionFromIP3</span><span class="sxs-lookup"><span data-stu-id="916b4-103">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="916b4-104">Сопоставляет указатель инструкции управляемого кода с FunctionID.</span><span class="sxs-lookup"><span data-stu-id="916b4-104">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="916b4-105">Этот метод работает как с динамическими, так и с нединамическими методами.</span><span class="sxs-lookup"><span data-stu-id="916b4-105">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="916b4-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="916b4-106">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="916b4-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="916b4-107">Parameters</span></span>

- `ip`

  <span data-ttu-id="916b4-108">\[in] указатель инструкций в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="916b4-108">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="916b4-109">\[out] идентификатор функции.</span><span class="sxs-lookup"><span data-stu-id="916b4-109">\[out] The function ID.</span></span>

- `pReJitId`

  <span data-ttu-id="916b4-110">\[out] удостоверение JIT-повторно скомпилированной версии функции.</span><span class="sxs-lookup"><span data-stu-id="916b4-110">\[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="916b4-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="916b4-111">Remarks</span></span>

<span data-ttu-id="916b4-112">Этот метод работает как с динамическими, так и с нединамическими методами.</span><span class="sxs-lookup"><span data-stu-id="916b4-112">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="916b4-113">Это надмножество [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), который работает только для функций с метаданными.</span><span class="sxs-lookup"><span data-stu-id="916b4-113">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="916b4-114">Требования</span><span class="sxs-lookup"><span data-stu-id="916b4-114">Requirements</span></span>

<span data-ttu-id="916b4-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="916b4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="916b4-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="916b4-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="916b4-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="916b4-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="916b4-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="916b4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="916b4-119">См. также</span><span class="sxs-lookup"><span data-stu-id="916b4-119">See also</span></span>

- [<span data-ttu-id="916b4-120">Интерфейс ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="916b4-120">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
