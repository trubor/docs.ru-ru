---
description: 'Дополнительные сведения о методе: ICorProfilerInfo10:: Суспендрунтиме'
title: 'ICorProfilerInfo10:: Суспендрунтиме'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.SuspendRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: d019b163c8c71331b2d9a77fc0384d42a04c1fbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794563"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="5ca97-103">Метод ICorProfilerInfo10:: Суспендрунтиме</span><span class="sxs-lookup"><span data-stu-id="5ca97-103">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="5ca97-104">Приостанавливает выполнение среды выполнения без выполнения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="5ca97-104">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ca97-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5ca97-105">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="5ca97-106">Требования</span><span class="sxs-lookup"><span data-stu-id="5ca97-106">Requirements</span></span>

<span data-ttu-id="5ca97-107">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="5ca97-107">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="5ca97-108">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ca97-108">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5ca97-109">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ca97-109">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5ca97-110">**Версии .NET:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ca97-110">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5ca97-111">См. также</span><span class="sxs-lookup"><span data-stu-id="5ca97-111">See also</span></span>

- [<span data-ttu-id="5ca97-112">Интерфейс ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="5ca97-112">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
