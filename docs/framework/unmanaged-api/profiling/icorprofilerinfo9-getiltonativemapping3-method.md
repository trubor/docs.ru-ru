---
description: 'Дополнительные сведения о методе: ICorProfilerInfo9:: GetILToNativeMapping3'
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 865545e2352209447b3942da3a62f3733c165b35
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759330"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="e3d74-103">Метод ICorProfilerInfo9:: GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="e3d74-103">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="e3d74-104">С учетом начального адреса машинного кода возвращает сведения о сопоставлении IL для этой откомпилированной версии кода.</span><span class="sxs-lookup"><span data-stu-id="e3d74-104">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3d74-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e3d74-105">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a><span data-ttu-id="e3d74-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e3d74-106">Parameters</span></span>

<span data-ttu-id="e3d74-107">`pNativeCodeStartAddress` окне Указатель на начало собственной функции.</span><span class="sxs-lookup"><span data-stu-id="e3d74-107">`pNativeCodeStartAddress` [in] A pointer to the start of a native function.</span></span>

<span data-ttu-id="e3d74-108">`cMap` окне Максимальный размер `map` массива.</span><span class="sxs-lookup"><span data-stu-id="e3d74-108">`cMap` [in] The maximum size of the `map` array.</span></span>

<span data-ttu-id="e3d74-109">`pcMap` заполняет Общее число доступных структур COR_DEBUG_IL_TO_NATIVE_MAP.</span><span class="sxs-lookup"><span data-stu-id="e3d74-109">`pcMap` [out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

<span data-ttu-id="e3d74-110">`map` заполняет Массив структур [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , каждый из которых задает смещения.</span><span class="sxs-lookup"><span data-stu-id="e3d74-110">`map` [out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="e3d74-111">После возврата метода `GetILToNativeMapping3` параметр `map` будет содержать все или некоторые из структур `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="e3d74-111">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3d74-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="e3d74-112">Remarks</span></span>

<span data-ttu-id="e3d74-113">Если включена многоуровневая компиляция, метод может иметь более одного тела машинного кода.</span><span class="sxs-lookup"><span data-stu-id="e3d74-113">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="e3d74-114">[ICorProfilerInfo9:: жетнативекодестартаддрессес](icorprofilerinfo9-getnativecodestartaddresses-method.md) будет возвращать начальные адреса для всех частей машинного кода.</span><span class="sxs-lookup"><span data-stu-id="e3d74-114">[ICorProfilerInfo9::GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="e3d74-115">Требования</span><span class="sxs-lookup"><span data-stu-id="e3d74-115">Requirements</span></span>

<span data-ttu-id="e3d74-116">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="e3d74-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="e3d74-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e3d74-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e3d74-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3d74-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e3d74-119">**Платформа .NET Framework версии:**[!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3d74-119">**.NET Framework Versions:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e3d74-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e3d74-120">See also</span></span>

- [<span data-ttu-id="e3d74-121">Интерфейс ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="e3d74-121">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
