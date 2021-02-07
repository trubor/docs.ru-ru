---
description: 'Дополнительные сведения о методе: ICorDebugTypeEnum:: Next'
title: Метод ICorDebugTypeEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
ms.openlocfilehash: 9260f5f2d1a2d6943a705f7e7ef1ead3d2924cdc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690591"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="6b531-103">Метод ICorDebugTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="6b531-103">ICorDebugTypeEnum::Next Method</span></span>

<span data-ttu-id="6b531-104">Возвращает количество экземпляров "ICorDebugType", заданных `celt` из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="6b531-104">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b531-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6b531-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b531-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6b531-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="6b531-107">окне Число `ICorDebugType` извлекаемых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="6b531-107">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="6b531-108">заполняет Массив указателей, каждый из которых указывает на `ICorDebugType` объект.</span><span class="sxs-lookup"><span data-stu-id="6b531-108">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6b531-109">заполняет Указатель на число `ICorDebugType` фактически возвращенных экземпляров.</span><span class="sxs-lookup"><span data-stu-id="6b531-109">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="6b531-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="6b531-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b531-111">Требования</span><span class="sxs-lookup"><span data-stu-id="6b531-111">Requirements</span></span>  

 <span data-ttu-id="6b531-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b531-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b531-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b531-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b531-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b531-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b531-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b531-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b531-116">См. также</span><span class="sxs-lookup"><span data-stu-id="6b531-116">See also</span></span>
