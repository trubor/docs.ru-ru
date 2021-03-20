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
ms.openlocfilehash: c7897e266fbb84d44df719c127e24bd375b560bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759095"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="0981f-103">Метод ICorProfilerInfo9:: GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="0981f-103">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="0981f-104">При наличии начального адреса машинного кода возвращает блоки виртуальной памяти, в которых хранится этот код.</span><span class="sxs-lookup"><span data-stu-id="0981f-104">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="0981f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0981f-105">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="0981f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0981f-106">Parameters</span></span>

<span data-ttu-id="0981f-107">`pNativeCodeStartAddress` окне Указатель на начало собственной функции.</span><span class="sxs-lookup"><span data-stu-id="0981f-107">`pNativeCodeStartAddress` [in] A pointer to the start of a native function.</span></span>

<span data-ttu-id="0981f-108">`cCodeInfos` окне Размер `codeInfos` массива.</span><span class="sxs-lookup"><span data-stu-id="0981f-108">`cCodeInfos` [in] The size of the `codeInfos` array.</span></span>

<span data-ttu-id="0981f-109">`pcCodeInfos` заполняет Указатель на общее число доступных структур [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="0981f-109">`pcCodeInfos` [out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

<span data-ttu-id="0981f-110">`codeInfos` заполняет Предоставленный вызывающим объектом буфер.</span><span class="sxs-lookup"><span data-stu-id="0981f-110">`codeInfos` [out] A caller-provided buffer.</span></span> <span data-ttu-id="0981f-111">После возврата метода он содержит массив структур `COR_PRF_CODE_INFO`, каждая из которых описывает блок машинного кода.</span><span class="sxs-lookup"><span data-stu-id="0981f-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0981f-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="0981f-112">Remarks</span></span>

<span data-ttu-id="0981f-113">`GetCodeInfo4`Метод аналогичен [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), за исключением того, что он может искать информацию о коде для различных версий метода.</span><span class="sxs-lookup"><span data-stu-id="0981f-113">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="0981f-114">`GetCodeInfo4` может запустить сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="0981f-114">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="0981f-115">Расширения сортируются в порядке возрастания смещения общих промежуточного языка (CIL).</span><span class="sxs-lookup"><span data-stu-id="0981f-115">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="0981f-116">После `GetCodeInfo4` возврата необходимо убедиться, что `codeInfos` буфер достаточно велик, чтобы вместить все структуры [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="0981f-116">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="0981f-117">Для этого сравните значение параметра `cCodeInfos` со значением параметра `cchName`.</span><span class="sxs-lookup"><span data-stu-id="0981f-117">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="0981f-118">При `cCodeInfos` делении на размер структуры [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) меньше `pcCodeInfos` , выделяет буфер большего размера `codeInfos` , обновляет `cCodeInfos` новый, больший размер и вызывается `GetCodeInfo4` снова.</span><span class="sxs-lookup"><span data-stu-id="0981f-118">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="0981f-119">Кроме того, сначала можно вызвать метод `GetCodeInfo4` с буфером `codeInfos` нулевой длины для получения правильного размера буфера.</span><span class="sxs-lookup"><span data-stu-id="0981f-119">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="0981f-120">Затем можно присвоить `codeInfos` Размер буфера значению, возвращенному в `pcCodeInfos` , умноженному на размер структуры [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) и вызывать `GetCodeInfo4` повторно.</span><span class="sxs-lookup"><span data-stu-id="0981f-120">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="0981f-121">Требования</span><span class="sxs-lookup"><span data-stu-id="0981f-121">Requirements</span></span>

<span data-ttu-id="0981f-122">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="0981f-122">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="0981f-123">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0981f-123">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="0981f-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0981f-124">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0981f-125">**Версии .NET:**[!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0981f-125">**.NET Versions:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0981f-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0981f-126">See also</span></span>

- [<span data-ttu-id="0981f-127">Интерфейс ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="0981f-127">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)
