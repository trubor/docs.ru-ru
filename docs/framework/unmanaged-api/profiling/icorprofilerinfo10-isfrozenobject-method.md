---
description: 'Дополнительные сведения о методе: ICorProfilerInfo10:: Исфрозенобжект'
title: 'ICorProfilerInfo10:: Исфрозенобжект'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 3b47204630056e2797b5cf126bd7c291830cea05
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103456"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="e8ea1-103">Метод ICorProfilerInfo10:: Исфрозенобжект</span><span class="sxs-lookup"><span data-stu-id="e8ea1-103">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="e8ea1-104">Определяет, находится ли объект в сегменте, доступном только для чтения.</span><span class="sxs-lookup"><span data-stu-id="e8ea1-104">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8ea1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e8ea1-105">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="e8ea1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e8ea1-106">Parameters</span></span>

- `objectId`

  <span data-ttu-id="e8ea1-107">\[в] объект для проверки.</span><span class="sxs-lookup"><span data-stu-id="e8ea1-107">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="e8ea1-108">\[out] значение `BOOL` , указывающее, находится ли объект в сегменте, доступном только для чтения.</span><span class="sxs-lookup"><span data-stu-id="e8ea1-108">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8ea1-109">Требования</span><span class="sxs-lookup"><span data-stu-id="e8ea1-109">Requirements</span></span>

<span data-ttu-id="e8ea1-110">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="e8ea1-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="e8ea1-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8ea1-111">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e8ea1-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8ea1-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e8ea1-113">**Версии .NET:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8ea1-113">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e8ea1-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e8ea1-114">See also</span></span>

- [<span data-ttu-id="e8ea1-115">Интерфейс ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="e8ea1-115">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
