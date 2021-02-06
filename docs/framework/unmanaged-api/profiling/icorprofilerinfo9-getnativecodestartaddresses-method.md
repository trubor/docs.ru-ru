---
description: 'Дополнительные сведения о методе: ICorProfilerInfo9:: Жетнативекодестартаддрессес'
title: 'ICorProfilerInfo9:: Жетнативекодестартаддрессес'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 1ca686cef4a45ebb9e05190fa790ed5300c0d816
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646495"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="cf25d-103">Метод ICorProfilerInfo9:: Жетнативекодестартаддрессес</span><span class="sxs-lookup"><span data-stu-id="cf25d-103">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="cf25d-104">При наличии кода functionId и Режитид перечисляются начальные адреса всех откомпилированных версий этого кода, которые в настоящее время существуют.</span><span class="sxs-lookup"><span data-stu-id="cf25d-104">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="cf25d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cf25d-105">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="cf25d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cf25d-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="cf25d-107">\[in] идентификатор функции, для которой должны возвращаться начальные адреса машинного кода.</span><span class="sxs-lookup"><span data-stu-id="cf25d-107">\[in] The ID of the function whose native code start addresses should be returned.</span></span>

- `reJitId`

  <span data-ttu-id="cf25d-108">\[in] Идентификация JIT-повторно скомпилированной функции.</span><span class="sxs-lookup"><span data-stu-id="cf25d-108">\[in] The identity of the JIT-recompiled function.</span></span>

- `cCodeStartAddresses`

  <span data-ttu-id="cf25d-109">\[in] максимальный размер `codeStartAddresses` массива.</span><span class="sxs-lookup"><span data-stu-id="cf25d-109">\[in] The maximum size of the `codeStartAddresses` array.</span></span>

- `pcCodeStartAddresses`

  <span data-ttu-id="cf25d-110">\[out] количество доступных адресов.</span><span class="sxs-lookup"><span data-stu-id="cf25d-110">\[out] The number of available addresses.</span></span>

- `codeStartAddresses`

  <span data-ttu-id="cf25d-111">\[out] массив `UINT_PTR` , каждый из которых является начальным адресом для собственного тела для указанной функции.</span><span class="sxs-lookup"><span data-stu-id="cf25d-111">\[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf25d-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="cf25d-112">Remarks</span></span>

<span data-ttu-id="cf25d-113">Если включена многоуровневая компиляция, функция может иметь более одного тела машинного кода.</span><span class="sxs-lookup"><span data-stu-id="cf25d-113">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="cf25d-114">Требования</span><span class="sxs-lookup"><span data-stu-id="cf25d-114">Requirements</span></span>

<span data-ttu-id="cf25d-115">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="cf25d-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="cf25d-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cf25d-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="cf25d-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf25d-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="cf25d-118">**Версии .NET:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf25d-118">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cf25d-119">См. также</span><span class="sxs-lookup"><span data-stu-id="cf25d-119">See also</span></span>

- [<span data-ttu-id="cf25d-120">Интерфейс ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="cf25d-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
