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
ms.openlocfilehash: b07e456f7fa9c328217b8779733d45dfe2793fe2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753280"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="0f108-103">Метод ICorProfilerInfo10:: Исфрозенобжект</span><span class="sxs-lookup"><span data-stu-id="0f108-103">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="0f108-104">Определяет, находится ли объект в сегменте, доступном только для чтения.</span><span class="sxs-lookup"><span data-stu-id="0f108-104">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f108-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0f108-105">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="0f108-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0f108-106">Parameters</span></span>

- `objectId`

  <span data-ttu-id="0f108-107">\[в] объект для проверки.</span><span class="sxs-lookup"><span data-stu-id="0f108-107">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="0f108-108">\[out] значение `BOOL` , указывающее, находится ли объект в сегменте, доступном только для чтения.</span><span class="sxs-lookup"><span data-stu-id="0f108-108">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f108-109">Требования</span><span class="sxs-lookup"><span data-stu-id="0f108-109">Requirements</span></span>

<span data-ttu-id="0f108-110">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="0f108-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="0f108-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0f108-111">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="0f108-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f108-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0f108-113">**Версии .NET:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f108-113">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0f108-114">См. также</span><span class="sxs-lookup"><span data-stu-id="0f108-114">See also</span></span>

- [<span data-ttu-id="0f108-115">Интерфейс ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="0f108-115">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
