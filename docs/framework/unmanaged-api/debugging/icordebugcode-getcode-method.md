---
description: 'Дополнительные сведения о методе ICorDebugCode:: с кодом.'
title: Метод ICorDebugCode::GetCode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
ms.openlocfilehash: 329770fac4f2b375c01dd68e4ea7114e59c609b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711288"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="c73b6-103">Метод ICorDebugCode::GetCode</span><span class="sxs-lookup"><span data-stu-id="c73b6-103">ICorDebugCode::GetCode Method</span></span>

<span data-ttu-id="c73b6-104">Возвращает весь код для указанной функции, отформатированный для дизассемблирования.</span><span class="sxs-lookup"><span data-stu-id="c73b6-104">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="c73b6-105">Этот метод не рекомендуется к использованию в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="c73b6-105">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c73b6-106">Вместо этого используйте [ICorDebugCode2:: жеткодечункс](icordebugcode2-getcodechunks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c73b6-106">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c73b6-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c73b6-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c73b6-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="c73b6-108">Parameters</span></span>  

 `startOffset`  
 <span data-ttu-id="c73b6-109">окне Смещение начала функции.</span><span class="sxs-lookup"><span data-stu-id="c73b6-109">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="c73b6-110">окне Смещение конца функции.</span><span class="sxs-lookup"><span data-stu-id="c73b6-110">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="c73b6-111">окне Размер `buffer` массива, в который будет возвращен код.</span><span class="sxs-lookup"><span data-stu-id="c73b6-111">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="c73b6-112">заполняет Массив, в который будет возвращен код.</span><span class="sxs-lookup"><span data-stu-id="c73b6-112">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="c73b6-113">заполняет Число возвращаемых байтов.</span><span class="sxs-lookup"><span data-stu-id="c73b6-113">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c73b6-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="c73b6-114">Remarks</span></span>  

 <span data-ttu-id="c73b6-115">Если код функции делится на несколько блоков, они объединяются в порядке возрастания смещения в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="c73b6-115">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="c73b6-116">Границы инструкций не проверяются.</span><span class="sxs-lookup"><span data-stu-id="c73b6-116">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c73b6-117">Требования</span><span class="sxs-lookup"><span data-stu-id="c73b6-117">Requirements</span></span>  

 <span data-ttu-id="c73b6-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c73b6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c73b6-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c73b6-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c73b6-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c73b6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c73b6-121">**Платформа .NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="c73b6-121">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c73b6-122">См. также</span><span class="sxs-lookup"><span data-stu-id="c73b6-122">See also</span></span>

- [<span data-ttu-id="c73b6-123">Метод GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="c73b6-123">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
