---
description: 'Дополнительные сведения о методе: ICorProfilerInfo10:: Жетлохобжектсизесрешолд'
title: 'ICorProfilerInfo10:: Жетлохобжектсизесрешолд'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 96c502dba5b2807f9cd9c3c5cceb6b3b9985a406
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106960"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="c290b-103">Метод ICorProfilerInfo10:: Жетлохобжектсизесрешолд</span><span class="sxs-lookup"><span data-stu-id="c290b-103">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="c290b-104">Возвращает значение заданного порога кучи больших объектов (LOH).</span><span class="sxs-lookup"><span data-stu-id="c290b-104">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="c290b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c290b-105">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="c290b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c290b-106">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="c290b-107">\[out] пороговое значение кучи больших объектов в байтах.</span><span class="sxs-lookup"><span data-stu-id="c290b-107">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="c290b-108">Комментарии</span><span class="sxs-lookup"><span data-stu-id="c290b-108">Remarks</span></span>

<span data-ttu-id="c290b-109">Объекты, превышающие пороговое значение кучи больших объектов, будут выделены в куче больших объектов.</span><span class="sxs-lookup"><span data-stu-id="c290b-109">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="c290b-110">Начиная с .NET Core 3,0, порог кучи больших объектов можно настроить, он `pThreshold` будет содержать пороговое значение активной кучи больших объектов в байтах.</span><span class="sxs-lookup"><span data-stu-id="c290b-110">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="c290b-111">Требования</span><span class="sxs-lookup"><span data-stu-id="c290b-111">Requirements</span></span>

<span data-ttu-id="c290b-112">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c290b-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="c290b-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c290b-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c290b-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c290b-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c290b-115">**Версии .NET:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c290b-115">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c290b-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c290b-116">See also</span></span>

- [<span data-ttu-id="c290b-117">Интерфейс ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="c290b-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
