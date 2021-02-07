---
description: 'Дополнительные сведения о методе: ICorDebugValueEnum:: Next'
title: Метод ICorDebugValueEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: 9a02c769f69651227669eb4b3f8c5ce41b670a73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690110"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="b26d1-103">Метод ICorDebugValueEnum::Next</span><span class="sxs-lookup"><span data-stu-id="b26d1-103">ICorDebugValueEnum::Next Method</span></span>

<span data-ttu-id="b26d1-104">Возвращает указанное число экземпляров "ICorDebugValue" из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="b26d1-104">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b26d1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b26d1-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b26d1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b26d1-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="b26d1-107">окне Число `ICorDebugValue` извлекаемых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="b26d1-107">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="b26d1-108">заполняет Массив указателей, каждый из которых указывает на `ICorDebugValue` объект.</span><span class="sxs-lookup"><span data-stu-id="b26d1-108">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b26d1-109">заполняет Указатель на число `ICorDebugValue` фактически возвращенных экземпляров.</span><span class="sxs-lookup"><span data-stu-id="b26d1-109">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="b26d1-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="b26d1-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b26d1-111">Требования</span><span class="sxs-lookup"><span data-stu-id="b26d1-111">Requirements</span></span>  

 <span data-ttu-id="b26d1-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b26d1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b26d1-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b26d1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b26d1-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b26d1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b26d1-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b26d1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b26d1-116">См. также</span><span class="sxs-lookup"><span data-stu-id="b26d1-116">See also</span></span>
