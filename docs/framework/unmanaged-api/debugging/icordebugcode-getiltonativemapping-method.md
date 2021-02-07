---
description: 'Дополнительные сведения: метод ICorDebugCode:: GetILToNativeMapping'
title: Метод ICorDebugCode::GetILToNativeMapping
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
ms.openlocfilehash: 808ed450fced8afecc2b637a3b990a894897b350
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711197"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="fd5c5-103">Метод ICorDebugCode::GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="fd5c5-103">ICorDebugCode::GetILToNativeMapping Method</span></span>

<span data-ttu-id="fd5c5-104">Возвращает массив экземпляров "COR_DEBUG_IL_TO_NATIVE_MAP", которые представляют сопоставления из смещений MSIL к собственным смещениям.</span><span class="sxs-lookup"><span data-stu-id="fd5c5-104">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd5c5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fd5c5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd5c5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fd5c5-106">Parameters</span></span>  

 `cMap`  
 <span data-ttu-id="fd5c5-107">[in] Размер массива `map`.</span><span class="sxs-lookup"><span data-stu-id="fd5c5-107">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="fd5c5-108">заполняет Указатель на фактическое число элементов, возвращаемых в `map` массиве.</span><span class="sxs-lookup"><span data-stu-id="fd5c5-108">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="fd5c5-109">заполняет Массив `COR_DEBUG_IL_TO_NATIVE_MAP` структур, каждый из которых представляет сопоставление смещения MSIL со смещением в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="fd5c5-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="fd5c5-110">Порядок для массива возвращаемых элементов отсутствует.</span><span class="sxs-lookup"><span data-stu-id="fd5c5-110">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd5c5-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="fd5c5-111">Remarks</span></span>  

 <span data-ttu-id="fd5c5-112">`GetILToNativeMapping`Метод возвращает значимые результаты только в том случае, если этот экземпляр "ICorDebugCode" представляет машинный код, который был скомпилирован из кода MSIL в JIT-режиме.</span><span class="sxs-lookup"><span data-stu-id="fd5c5-112">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd5c5-113">Требования</span><span class="sxs-lookup"><span data-stu-id="fd5c5-113">Requirements</span></span>  

 <span data-ttu-id="fd5c5-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd5c5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd5c5-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd5c5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd5c5-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd5c5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd5c5-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd5c5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5c5-118">См. также</span><span class="sxs-lookup"><span data-stu-id="fd5c5-118">See also</span></span>

- [<span data-ttu-id="fd5c5-119">Интерфейс ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="fd5c5-119">ICorDebugCode Interface</span></span>](icordebugcode-interface1.md)
