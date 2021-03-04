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
ms.openlocfilehash: 8cc098e4ae5f139f729ca0593b51c25eaf031704
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106882"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="f94f8-103">Метод ICorProfilerInfo10:: Суспендрунтиме</span><span class="sxs-lookup"><span data-stu-id="f94f8-103">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="f94f8-104">Приостанавливает выполнение среды выполнения без выполнения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="f94f8-104">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="f94f8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f94f8-105">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="f94f8-106">Требования</span><span class="sxs-lookup"><span data-stu-id="f94f8-106">Requirements</span></span>

<span data-ttu-id="f94f8-107">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="f94f8-107">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="f94f8-108">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f94f8-108">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="f94f8-109">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f94f8-109">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f94f8-110">**Версии .NET:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f94f8-110">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f94f8-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f94f8-111">See also</span></span>

- [<span data-ttu-id="f94f8-112">Интерфейс ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="f94f8-112">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
