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
ms.openlocfilehash: 139edeed3e078668974382f1719c8e03f83e2a09
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759082"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="dd6f2-103">Метод ICorProfilerInfo8:: Исфунктиондинамик</span><span class="sxs-lookup"><span data-stu-id="dd6f2-103">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="dd6f2-104">Определяет, имеет ли функция связанные метаданные.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-104">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="dd6f2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dd6f2-105">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="dd6f2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dd6f2-106">Parameters</span></span>

<span data-ttu-id="dd6f2-107">`functionId` окне  Объект `FunctionID` , определяющий рассматриваемую функцию.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-107">`functionId` [in]  The `FunctionID` that identifies the function in question.</span></span>

<span data-ttu-id="dd6f2-108">`isDynamic` заполняет Указатель на объект `BOOL` , который будет содержать значение, указывающее, имеет ли функция метаданные.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-108">`isDynamic` [out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="dd6f2-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="dd6f2-109">Remarks</span></span>

<span data-ttu-id="dd6f2-110">Функция считается динамической, если она не имеет метаданных.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-110">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="dd6f2-111">Некоторые методы, такие как заглушки IL или методы LCG, не имеют связанных метаданных, которые можно получить с помощью API-интерфейсов интерфейса IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-111">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="dd6f2-112">Эти методы могут быть обнаружены профилировщиками с помощью указателей инструкций или путем прослушивания в [ICorProfilerCallback::D инамикмесоджиткомпилатионстартед](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="dd6f2-112">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="dd6f2-113">Требования</span><span class="sxs-lookup"><span data-stu-id="dd6f2-113">Requirements</span></span>

<span data-ttu-id="dd6f2-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd6f2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="dd6f2-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dd6f2-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="dd6f2-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd6f2-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="dd6f2-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dd6f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dd6f2-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dd6f2-118">See also</span></span>

- [<span data-ttu-id="dd6f2-119">Интерфейс ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="dd6f2-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
