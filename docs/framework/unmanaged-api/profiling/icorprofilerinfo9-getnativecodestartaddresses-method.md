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
ms.openlocfilehash: 062aebf6d5bed208ea71b215bd9f857b82483673
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759054"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="24db6-103">Метод ICorProfilerInfo9:: Жетнативекодестартаддрессес</span><span class="sxs-lookup"><span data-stu-id="24db6-103">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="24db6-104">При наличии кода functionId и Режитид перечисляются начальные адреса всех откомпилированных версий этого кода, которые в настоящее время существуют.</span><span class="sxs-lookup"><span data-stu-id="24db6-104">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="24db6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="24db6-105">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="24db6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="24db6-106">Parameters</span></span>

<span data-ttu-id="24db6-107">`functionId` окне Идентификатор функции, для которой должны возвращаться начальные адреса машинного кода.</span><span class="sxs-lookup"><span data-stu-id="24db6-107">`functionId` [in] The ID of the function whose native code start addresses should be returned.</span></span>

<span data-ttu-id="24db6-108">`reJitId` окне Удостоверение JIT-повторно скомпилированной функции.</span><span class="sxs-lookup"><span data-stu-id="24db6-108">`reJitId` [in] The identity of the JIT-recompiled function.</span></span>

<span data-ttu-id="24db6-109">`cCodeStartAddresses` окне Максимальный размер `codeStartAddresses` массива.</span><span class="sxs-lookup"><span data-stu-id="24db6-109">`cCodeStartAddresses` [in] The maximum size of the `codeStartAddresses` array.</span></span>

<span data-ttu-id="24db6-110">`pcCodeStartAddresses` заполняет Количество доступных адресов.</span><span class="sxs-lookup"><span data-stu-id="24db6-110">`pcCodeStartAddresses` [out] The number of available addresses.</span></span>

<span data-ttu-id="24db6-111">`codeStartAddresses` заполняет Массив `UINT_PTR` , каждый из которых является начальным адресом для заданной функции в машинном тексте.</span><span class="sxs-lookup"><span data-stu-id="24db6-111">`codeStartAddresses` [out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="24db6-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="24db6-112">Remarks</span></span>

<span data-ttu-id="24db6-113">Если включена многоуровневая компиляция, функция может иметь более одного тела машинного кода.</span><span class="sxs-lookup"><span data-stu-id="24db6-113">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="24db6-114">Требования</span><span class="sxs-lookup"><span data-stu-id="24db6-114">Requirements</span></span>

<span data-ttu-id="24db6-115">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="24db6-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="24db6-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24db6-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="24db6-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24db6-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="24db6-118">**Версии .NET:**[!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24db6-118">**.NET Versions:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="24db6-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="24db6-119">See also</span></span>

- [<span data-ttu-id="24db6-120">Интерфейс ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="24db6-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
