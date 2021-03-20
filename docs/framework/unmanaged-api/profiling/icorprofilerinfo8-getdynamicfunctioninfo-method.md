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
ms.openlocfilehash: b38bd7a4f440edba0a7156176f223ba38c9807cf
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759121"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="3ca28-103">Метод ICorProfilerInfo8:: Жетдинамикфунктионинфо</span><span class="sxs-lookup"><span data-stu-id="3ca28-103">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="3ca28-104">Извлекает сведения о динамических методах.</span><span class="sxs-lookup"><span data-stu-id="3ca28-104">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ca28-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3ca28-105">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a><span data-ttu-id="3ca28-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3ca28-106">Parameters</span></span>

<span data-ttu-id="3ca28-107">`functionId` окне Идентификатор функции, для которой требуется получить сведения.</span><span class="sxs-lookup"><span data-stu-id="3ca28-107">`functionId` [in] The ID of the function for which to retrieve information.</span></span>

<span data-ttu-id="3ca28-108">`moduleId` окне Указатель на модуль, в котором определен родительский класс функции.</span><span class="sxs-lookup"><span data-stu-id="3ca28-108">`moduleId` [in] A pointer to the module in which the function's parent class is defined.</span></span>

<span data-ttu-id="3ca28-109">`ppvSig` заполняет Указатель на сигнатуру для функции.</span><span class="sxs-lookup"><span data-stu-id="3ca28-109">`ppvSig` [out] A pointer to the signature for the function.</span></span>

<span data-ttu-id="3ca28-110">`pbSig` заполняет Указатель на число байтов для сигнатуры функции.</span><span class="sxs-lookup"><span data-stu-id="3ca28-110">`pbSig` [out] A pointer to the count of bytes for the function signature.</span></span>

<span data-ttu-id="3ca28-111">`cchName` окне Максимальный размер `wszName` массива.</span><span class="sxs-lookup"><span data-stu-id="3ca28-111">`cchName` [in] The maximum size of the `wszName` array.</span></span>

<span data-ttu-id="3ca28-112">`pcchName` заполняет Число символов в `wszName` массиве.</span><span class="sxs-lookup"><span data-stu-id="3ca28-112">`pcchName` [out] The number of characters in the `wszName` array.</span></span>

<span data-ttu-id="3ca28-113">`wszName` заполняет Массив, содержащий `WCHAR` имя функции, если таковое существует.</span><span class="sxs-lookup"><span data-stu-id="3ca28-113">`wszName` [out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ca28-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="3ca28-114">Remarks</span></span>

<span data-ttu-id="3ca28-115">Некоторые методы, такие как заглушки IL или LCG, не имеют связанных метаданных, которые можно извлечь с помощью интерфейсов API [IMetaDataImport](../metadata/imetadataimport-interface.md) и [IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3ca28-115">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="3ca28-116">Такие методы могут быть обнаружены профилировщиками с помощью указателей инструкций или путем прослушивания [ICorProfilerCallback8::D инамикмесоджиткомпилатионстартед](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="3ca28-116">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="3ca28-117">Этот API можно использовать для получения сведений о динамических методах, включая понятное имя, если оно доступно.</span><span class="sxs-lookup"><span data-stu-id="3ca28-117">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ca28-118">Требования</span><span class="sxs-lookup"><span data-stu-id="3ca28-118">Requirements</span></span>

<span data-ttu-id="3ca28-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ca28-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3ca28-120">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3ca28-120">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="3ca28-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ca28-121">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3ca28-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3ca28-122">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3ca28-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3ca28-123">See also</span></span>

- [<span data-ttu-id="3ca28-124">Интерфейс ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="3ca28-124">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
