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
ms.openlocfilehash: c4d31c96fd7470a153437ffb0125e81ca8ea77bd
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759759"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="66a40-103">Метод ICorProfilerInfo10:: Исфрозенобжект</span><span class="sxs-lookup"><span data-stu-id="66a40-103">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="66a40-104">Определяет, находится ли объект в сегменте, доступном только для чтения.</span><span class="sxs-lookup"><span data-stu-id="66a40-104">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="66a40-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="66a40-105">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="66a40-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="66a40-106">Parameters</span></span>

<span data-ttu-id="66a40-107">`objectId` окне Объект для проверки.</span><span class="sxs-lookup"><span data-stu-id="66a40-107">`objectId` [in] The object to examine.</span></span>

<span data-ttu-id="66a40-108">`pbFrozen` заполняет Значение типа `BOOL` , указывающее, находится ли объект в сегменте, доступном только для чтения.</span><span class="sxs-lookup"><span data-stu-id="66a40-108">`pbFrozen` [out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="66a40-109">Требования</span><span class="sxs-lookup"><span data-stu-id="66a40-109">Requirements</span></span>

<span data-ttu-id="66a40-110">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="66a40-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="66a40-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66a40-111">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="66a40-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66a40-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="66a40-113">**Версии .NET:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66a40-113">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="66a40-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="66a40-114">See also</span></span>

- [<span data-ttu-id="66a40-115">Интерфейс ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="66a40-115">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
