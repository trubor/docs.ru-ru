---
description: 'Дополнительные сведения о методе: ICorProfilerInfo8:: Жетдинамикфунктионинфо'
title: 'ICorProfilerInfo8:: Жетдинамикфунктионинфо'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 48c8dbe20ccafb3fb23e9e289f728d5e3370613a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646586"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="5ff10-103">Метод ICorProfilerInfo8:: Жетдинамикфунктионинфо</span><span class="sxs-lookup"><span data-stu-id="5ff10-103">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="5ff10-104">Извлекает сведения о динамических методах.</span><span class="sxs-lookup"><span data-stu-id="5ff10-104">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ff10-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5ff10-105">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a><span data-ttu-id="5ff10-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5ff10-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="5ff10-107">\[in] идентификатор функции, для которой требуется получить сведения.</span><span class="sxs-lookup"><span data-stu-id="5ff10-107">\[in] The ID of the function for which to retrieve information.</span></span>

- `moduleId`

  <span data-ttu-id="5ff10-108">\[in] указатель на модуль, в котором определен родительский класс функции.</span><span class="sxs-lookup"><span data-stu-id="5ff10-108">\[in] A pointer to the module in which the function's parent class is defined.</span></span>

- `ppvSig`

  <span data-ttu-id="5ff10-109">\[out] указатель на сигнатуру для функции.</span><span class="sxs-lookup"><span data-stu-id="5ff10-109">\[out] A pointer to the signature for the function.</span></span>

- `pbSig`

  <span data-ttu-id="5ff10-110">\[out] указатель на число байтов для сигнатуры функции.</span><span class="sxs-lookup"><span data-stu-id="5ff10-110">\[out] A pointer to the count of bytes for the function signature.</span></span>

- `cchName`

  <span data-ttu-id="5ff10-111">\[in] максимальный размер `wszName` массива.</span><span class="sxs-lookup"><span data-stu-id="5ff10-111">\[in] The maximum size of the `wszName` array.</span></span>

- `pcchName`

  <span data-ttu-id="5ff10-112">\[out] число символов в `wszName` массиве.</span><span class="sxs-lookup"><span data-stu-id="5ff10-112">\[out] The number of characters in the `wszName` array.</span></span>

- `wszName`

  <span data-ttu-id="5ff10-113">\[out] массив, `WCHAR` представляющий собой имя функции, если она существует.</span><span class="sxs-lookup"><span data-stu-id="5ff10-113">\[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ff10-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="5ff10-114">Remarks</span></span>

<span data-ttu-id="5ff10-115">Некоторые методы, такие как заглушки IL или LCG, не имеют связанных метаданных, которые можно извлечь с помощью интерфейсов API [IMetaDataImport](../metadata/imetadataimport-interface.md) и [IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5ff10-115">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="5ff10-116">Такие методы могут быть обнаружены профилировщиками с помощью указателей инструкций или путем прослушивания [ICorProfilerCallback8::D инамикмесоджиткомпилатионстартед](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="5ff10-116">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="5ff10-117">Этот API можно использовать для получения сведений о динамических методах, включая понятное имя, если оно доступно.</span><span class="sxs-lookup"><span data-stu-id="5ff10-117">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ff10-118">Требования</span><span class="sxs-lookup"><span data-stu-id="5ff10-118">Requirements</span></span>

<span data-ttu-id="5ff10-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ff10-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5ff10-120">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ff10-120">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5ff10-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ff10-121">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5ff10-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5ff10-122">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5ff10-123">См. также</span><span class="sxs-lookup"><span data-stu-id="5ff10-123">See also</span></span>

- [<span data-ttu-id="5ff10-124">Интерфейс ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="5ff10-124">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
