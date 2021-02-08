---
description: 'Дополнительные сведения о методе: ICorProfilerInfo9:: GetCodeInfo4'
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 765f3dfee6c56148eb7807b0606e79d4b3a2e7a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783811"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="a38ff-103">Метод ICorProfilerInfo9:: GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="a38ff-103">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="a38ff-104">При наличии начального адреса машинного кода возвращает блоки виртуальной памяти, в которых хранится этот код.</span><span class="sxs-lookup"><span data-stu-id="a38ff-104">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="a38ff-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a38ff-105">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="a38ff-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a38ff-106">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="a38ff-107">\[in] указатель на начало собственной функции.</span><span class="sxs-lookup"><span data-stu-id="a38ff-107">\[in] A pointer to the start of a native function.</span></span>

- `cCodeInfos`

  <span data-ttu-id="a38ff-108">\[in] размер `codeInfos` массива.</span><span class="sxs-lookup"><span data-stu-id="a38ff-108">\[in] The size of the `codeInfos` array.</span></span>

- `pcCodeInfos`

  <span data-ttu-id="a38ff-109">\[out] указатель на общее число доступных структур [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="a38ff-109">\[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

- `codeInfos`

  <span data-ttu-id="a38ff-110">\[out] буфер, предоставленный вызывающей стороной.</span><span class="sxs-lookup"><span data-stu-id="a38ff-110">\[out] A caller-provided buffer.</span></span> <span data-ttu-id="a38ff-111">После возврата метода он содержит массив структур `COR_PRF_CODE_INFO`, каждая из которых описывает блок машинного кода.</span><span class="sxs-lookup"><span data-stu-id="a38ff-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a38ff-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="a38ff-112">Remarks</span></span>

<span data-ttu-id="a38ff-113">`GetCodeInfo4`Метод аналогичен [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), за исключением того, что он может искать информацию о коде для различных версий метода.</span><span class="sxs-lookup"><span data-stu-id="a38ff-113">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="a38ff-114">`GetCodeInfo4` может запустить сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="a38ff-114">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="a38ff-115">Расширения сортируются в порядке возрастания смещения общих промежуточного языка (CIL).</span><span class="sxs-lookup"><span data-stu-id="a38ff-115">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="a38ff-116">После `GetCodeInfo4` возврата необходимо убедиться, что `codeInfos` буфер достаточно велик, чтобы вместить все структуры [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="a38ff-116">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="a38ff-117">Для этого сравните значение параметра `cCodeInfos` со значением параметра `cchName`.</span><span class="sxs-lookup"><span data-stu-id="a38ff-117">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="a38ff-118">При `cCodeInfos` делении на размер структуры [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) меньше `pcCodeInfos` , выделяет буфер большего размера `codeInfos` , обновляет `cCodeInfos` новый, больший размер и вызывается `GetCodeInfo4` снова.</span><span class="sxs-lookup"><span data-stu-id="a38ff-118">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="a38ff-119">Кроме того, сначала можно вызвать метод `GetCodeInfo4` с буфером `codeInfos` нулевой длины для получения правильного размера буфера.</span><span class="sxs-lookup"><span data-stu-id="a38ff-119">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="a38ff-120">Затем можно присвоить `codeInfos` Размер буфера значению, возвращенному в `pcCodeInfos` , умноженному на размер структуры [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) и вызывать `GetCodeInfo4` повторно.</span><span class="sxs-lookup"><span data-stu-id="a38ff-120">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="a38ff-121">Требования</span><span class="sxs-lookup"><span data-stu-id="a38ff-121">Requirements</span></span>

<span data-ttu-id="a38ff-122">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="a38ff-122">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="a38ff-123">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a38ff-123">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a38ff-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a38ff-124">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a38ff-125">**Версии .NET:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a38ff-125">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a38ff-126">См. также</span><span class="sxs-lookup"><span data-stu-id="a38ff-126">See also</span></span>

- [<span data-ttu-id="a38ff-127">Интерфейс ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="a38ff-127">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)
