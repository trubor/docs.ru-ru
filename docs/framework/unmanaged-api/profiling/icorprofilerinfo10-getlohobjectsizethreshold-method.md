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
ms.openlocfilehash: 7dca887f6d0ff5f9360b0edaa1568bc4b1bb42ac
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759772"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="da7f0-103">Метод ICorProfilerInfo10:: Жетлохобжектсизесрешолд</span><span class="sxs-lookup"><span data-stu-id="da7f0-103">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="da7f0-104">Возвращает значение заданного порога кучи больших объектов (LOH).</span><span class="sxs-lookup"><span data-stu-id="da7f0-104">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="da7f0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="da7f0-105">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="da7f0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="da7f0-106">Parameters</span></span>

<span data-ttu-id="da7f0-107">`pThreshold` заполняет Пороговое значение кучи больших объектов в байтах.</span><span class="sxs-lookup"><span data-stu-id="da7f0-107">`pThreshold` [out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="da7f0-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="da7f0-108">Remarks</span></span>

<span data-ttu-id="da7f0-109">Объекты, превышающие пороговое значение кучи больших объектов, будут выделены в куче больших объектов.</span><span class="sxs-lookup"><span data-stu-id="da7f0-109">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="da7f0-110">Начиная с .NET Core 3,0, порог кучи больших объектов можно настроить, он `pThreshold` будет содержать пороговое значение активной кучи больших объектов в байтах.</span><span class="sxs-lookup"><span data-stu-id="da7f0-110">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="da7f0-111">Требования</span><span class="sxs-lookup"><span data-stu-id="da7f0-111">Requirements</span></span>

<span data-ttu-id="da7f0-112">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="da7f0-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="da7f0-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="da7f0-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="da7f0-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da7f0-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="da7f0-115">**Версии .NET:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da7f0-115">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="da7f0-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="da7f0-116">See also</span></span>

- [<span data-ttu-id="da7f0-117">Интерфейс ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="da7f0-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
