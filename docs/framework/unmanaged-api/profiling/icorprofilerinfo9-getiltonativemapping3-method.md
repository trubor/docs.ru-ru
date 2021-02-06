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
ms.openlocfilehash: 867375d57f9d166ed08bf68ada81fb5cdbb8afe3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646521"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="c7afc-103">Метод ICorProfilerInfo9:: GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="c7afc-103">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="c7afc-104">С учетом начального адреса машинного кода возвращает сведения о сопоставлении IL для этой откомпилированной версии кода.</span><span class="sxs-lookup"><span data-stu-id="c7afc-104">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7afc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c7afc-105">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a><span data-ttu-id="c7afc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c7afc-106">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="c7afc-107">\[in] указатель на начало собственной функции.</span><span class="sxs-lookup"><span data-stu-id="c7afc-107">\[in] A pointer to the start of a native function.</span></span>

- `cMap`

  <span data-ttu-id="c7afc-108">\[in] максимальный размер `map` массива.</span><span class="sxs-lookup"><span data-stu-id="c7afc-108">\[in] The maximum size of the `map` array.</span></span>

- `pcMap`

  <span data-ttu-id="c7afc-109">\[out] общее число доступных структур COR_DEBUG_IL_TO_NATIVE_MAP.</span><span class="sxs-lookup"><span data-stu-id="c7afc-109">\[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

- `map`

  <span data-ttu-id="c7afc-110">\[out] массив структур [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , каждый из которых задает смещения.</span><span class="sxs-lookup"><span data-stu-id="c7afc-110">\[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="c7afc-111">После возврата метода `GetILToNativeMapping3` параметр `map` будет содержать все или некоторые из структур `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="c7afc-111">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7afc-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="c7afc-112">Remarks</span></span>

<span data-ttu-id="c7afc-113">Если включена многоуровневая компиляция, метод может иметь более одного тела машинного кода.</span><span class="sxs-lookup"><span data-stu-id="c7afc-113">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="c7afc-114">[ICorProfilerInfo9:: жетнативекодестартаддрессес](icorprofilerinfo9-getnativecodestartaddresses-method.md) будет возвращать начальные адреса для всех частей машинного кода.</span><span class="sxs-lookup"><span data-stu-id="c7afc-114">[ICorProfilerInfo9::GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7afc-115">Требования</span><span class="sxs-lookup"><span data-stu-id="c7afc-115">Requirements</span></span>

<span data-ttu-id="c7afc-116">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c7afc-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="c7afc-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c7afc-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c7afc-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7afc-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c7afc-119">**Платформа .NET Framework версии:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7afc-119">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c7afc-120">См. также</span><span class="sxs-lookup"><span data-stu-id="c7afc-120">See also</span></span>

- [<span data-ttu-id="c7afc-121">Интерфейс ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="c7afc-121">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
