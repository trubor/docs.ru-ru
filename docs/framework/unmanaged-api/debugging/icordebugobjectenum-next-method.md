---
description: 'Дополнительные сведения о методе: Икордебугобжектенум:: Next'
title: Метод ICorDebugObjectEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
ms.openlocfilehash: dd7d4240827e14962edf7573b59b273f65231bcf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729046"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="1fe55-103">Метод ICorDebugObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="1fe55-103">ICorDebugObjectEnum::Next Method</span></span>

<span data-ttu-id="1fe55-104">Возвращает относительные виртуальные адреса (RVA) указанного числа объектов из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="1fe55-104">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fe55-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1fe55-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fe55-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1fe55-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="1fe55-107">[in] Количество объектов, которые должны быть получены.</span><span class="sxs-lookup"><span data-stu-id="1fe55-107">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="1fe55-108">заполняет Массив указателей, каждый из которых указывает на объект CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="1fe55-108">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1fe55-109">заполняет Указатель на число фактически возвращенных объектов.</span><span class="sxs-lookup"><span data-stu-id="1fe55-109">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="1fe55-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="1fe55-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fe55-111">Требования</span><span class="sxs-lookup"><span data-stu-id="1fe55-111">Requirements</span></span>  

 <span data-ttu-id="1fe55-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fe55-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fe55-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1fe55-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1fe55-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fe55-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fe55-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fe55-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe55-116">См. также</span><span class="sxs-lookup"><span data-stu-id="1fe55-116">See also</span></span>
