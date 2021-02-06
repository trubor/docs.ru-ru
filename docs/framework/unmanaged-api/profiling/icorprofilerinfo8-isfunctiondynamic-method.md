---
description: 'Дополнительные сведения о методе: ICorProfilerInfo8:: Исфунктиондинамик'
title: 'ICorProfilerInfo8:: Исфунктиондинамик'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 8ab942e6919f8029ef0d1c20336917622a1d22ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646534"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="b83a1-103">Метод ICorProfilerInfo8:: Исфунктиондинамик</span><span class="sxs-lookup"><span data-stu-id="b83a1-103">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="b83a1-104">Определяет, имеет ли функция связанные метаданные.</span><span class="sxs-lookup"><span data-stu-id="b83a1-104">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="b83a1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b83a1-105">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="b83a1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b83a1-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="b83a1-107">\[в] `FunctionID` , который определяет рассматриваемую функцию.</span><span class="sxs-lookup"><span data-stu-id="b83a1-107">\[in]  The `FunctionID` that identifies the function in question.</span></span>

- `isDynamic`

  <span data-ttu-id="b83a1-108">\[out] указатель на объект `BOOL` , который будет содержать значение, указывающее, имеет ли функция метаданные.</span><span class="sxs-lookup"><span data-stu-id="b83a1-108">\[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="b83a1-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="b83a1-109">Remarks</span></span>

<span data-ttu-id="b83a1-110">Функция считается динамической, если она не имеет метаданных.</span><span class="sxs-lookup"><span data-stu-id="b83a1-110">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="b83a1-111">Некоторые методы, такие как заглушки IL или методы LCG, не имеют связанных метаданных, которые можно получить с помощью API-интерфейсов интерфейса IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="b83a1-111">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="b83a1-112">Эти методы могут быть обнаружены профилировщиками с помощью указателей инструкций или путем прослушивания в [ICorProfilerCallback::D инамикмесоджиткомпилатионстартед](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="b83a1-112">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b83a1-113">Требования</span><span class="sxs-lookup"><span data-stu-id="b83a1-113">Requirements</span></span>

<span data-ttu-id="b83a1-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b83a1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="b83a1-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b83a1-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b83a1-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b83a1-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b83a1-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b83a1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b83a1-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b83a1-118">See also</span></span>

- [<span data-ttu-id="b83a1-119">Интерфейс ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="b83a1-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
