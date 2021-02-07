---
description: 'Дополнительные сведения о методе: ICorDebugCode2:: Жеткодечункс'
title: Метод ICorDebugCode2::GetCodeChunks
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
ms.openlocfilehash: 371d077466ff2390293d9d4e320d4c95a992fe54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764974"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="0e8c2-103">Метод ICorDebugCode2::GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="0e8c2-103">ICorDebugCode2::GetCodeChunks Method</span></span>

<span data-ttu-id="0e8c2-104">Возвращает фрагменты кода, из которого состоит этот объект кода.</span><span class="sxs-lookup"><span data-stu-id="0e8c2-104">Gets the chunks of code that this code object is composed of.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e8c2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0e8c2-105">Syntax</span></span>

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a><span data-ttu-id="0e8c2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0e8c2-106">Parameters</span></span>

`cbufSize`  
<span data-ttu-id="0e8c2-107">окне Размер `chunks` массива.</span><span class="sxs-lookup"><span data-stu-id="0e8c2-107">[in] Size of the `chunks` array.</span></span>

`pcnumChunks`  
<span data-ttu-id="0e8c2-108">заполняет Количество блоков, возвращаемых в `chunks` массиве.</span><span class="sxs-lookup"><span data-stu-id="0e8c2-108">[out] The number of chunks returned in the `chunks` array.</span></span>

`chunks`  
<span data-ttu-id="0e8c2-109">заполняет Массив структур "Кодечункинфо", каждый из которых представляет отдельный фрагмент кода.</span><span class="sxs-lookup"><span data-stu-id="0e8c2-109">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="0e8c2-110">Если значение `cbufSize` равно 0, этот параметр может принимать значение null.</span><span class="sxs-lookup"><span data-stu-id="0e8c2-110">If the value of `cbufSize` is 0, this parameter can be null.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e8c2-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="0e8c2-111">Remarks</span></span>

<span data-ttu-id="0e8c2-112">Фрагменты кода никогда не перекрываются, и они будут следовать порядку, в котором они были сцеплены с помощью [ICorDebugCode:: Code](icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="0e8c2-112">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="0e8c2-113">Объект кода на языке MSIL в платформа .NET Framework версии 2,0 будет состоять из одного фрагмента кода.</span><span class="sxs-lookup"><span data-stu-id="0e8c2-113">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e8c2-114">Требования</span><span class="sxs-lookup"><span data-stu-id="0e8c2-114">Requirements</span></span>

<span data-ttu-id="0e8c2-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e8c2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="0e8c2-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e8c2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="0e8c2-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e8c2-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0e8c2-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e8c2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
