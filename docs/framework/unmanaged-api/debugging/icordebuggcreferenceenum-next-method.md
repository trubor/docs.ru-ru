---
description: 'Дополнительные сведения о методе: ICorDebugGCReferenceEnum:: Next'
title: Метод ICorDebugGCReferenceEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
ms.openlocfilehash: aec135fcb737a200d5a267529fa812c0852a24df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803702"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="d43e5-103">Метод ICorDebugGCReferenceEnum::Next</span><span class="sxs-lookup"><span data-stu-id="d43e5-103">ICorDebugGCReferenceEnum::Next Method</span></span>

<span data-ttu-id="d43e5-104">Возвращает указанное число экземпляров [COR_GC_REFERENCE](cor-gc-reference-structure.md) , содержащих сведения об объектах, которые будут собираться сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="d43e5-104">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d43e5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d43e5-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d43e5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d43e5-106">Parameters</span></span>  

 <span data-ttu-id="d43e5-107">celt</span><span class="sxs-lookup"><span data-stu-id="d43e5-107">celt</span></span>  
 <span data-ttu-id="d43e5-108">окне Число извлекаемых корневых элементов.</span><span class="sxs-lookup"><span data-stu-id="d43e5-108">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="d43e5-109">корня</span><span class="sxs-lookup"><span data-stu-id="d43e5-109">roots</span></span>  
 <span data-ttu-id="d43e5-110">заполняет Массив указателей, каждый из которых указывает на объект [COR_GC_REFERENCE](cor-gc-reference-structure.md) , представляющий корень объекта, который должен быть собран сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="d43e5-110">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="d43e5-111">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="d43e5-111">pceltFetched</span></span>  
 <span data-ttu-id="d43e5-112">заполняет Указатель на число объектов [COR_GC_REFERENCE](cor-gc-reference-structure.md) , фактически возвращаемых в `roots` .</span><span class="sxs-lookup"><span data-stu-id="d43e5-112">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="d43e5-113">Это значение может быть `null`, если параметр `celt` имеет значение 1.</span><span class="sxs-lookup"><span data-stu-id="d43e5-113">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d43e5-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="d43e5-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d43e5-115">Требования</span><span class="sxs-lookup"><span data-stu-id="d43e5-115">Requirements</span></span>  

 <span data-ttu-id="d43e5-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d43e5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d43e5-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d43e5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d43e5-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d43e5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d43e5-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d43e5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d43e5-120">См. также</span><span class="sxs-lookup"><span data-stu-id="d43e5-120">See also</span></span>

- [<span data-ttu-id="d43e5-121">Интерфейс ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="d43e5-121">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="d43e5-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="d43e5-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
