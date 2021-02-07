---
description: 'Дополнительные сведения о методе: Икордебугхеапенум:: Next'
title: Метод ICorDebugHeapEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 22e81b9b0c4ac2027f932187b6f860d08adf6f97
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691956"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="7a060-103">Метод ICorDebugHeapEnum::Next</span><span class="sxs-lookup"><span data-stu-id="7a060-103">ICorDebugHeapEnum::Next Method</span></span>

<span data-ttu-id="7a060-104">Возвращает указанное число экземпляров [COR_HEAPOBJECT](cor-heapobject-structure.md) , содержащих сведения об объектах в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="7a060-104">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a060-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7a060-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a060-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7a060-106">Parameters</span></span>  

 <span data-ttu-id="7a060-107">celt</span><span class="sxs-lookup"><span data-stu-id="7a060-107">celt</span></span>  
 <span data-ttu-id="7a060-108">[in] Количество объектов, которые должны быть получены.</span><span class="sxs-lookup"><span data-stu-id="7a060-108">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="7a060-109">объекты</span><span class="sxs-lookup"><span data-stu-id="7a060-109">objects</span></span>  
 <span data-ttu-id="7a060-110">заполняет Массив указателей, каждый из которых указывает на объект [COR_HEAPOBJECT](cor-heapobject-structure.md) , предоставляющий сведения об объекте в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="7a060-110">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="7a060-111">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="7a060-111">pceltFetched</span></span>  
 <span data-ttu-id="7a060-112">заполняет Указатель на число объектов [COR_HEAPOBJECT](cor-heapobject-structure.md) , фактически возвращаемых в `objects` .</span><span class="sxs-lookup"><span data-stu-id="7a060-112">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="7a060-113">Это значение может быть `null`, если параметр `celt` имеет значение 1.</span><span class="sxs-lookup"><span data-stu-id="7a060-113">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a060-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="7a060-114">Remarks</span></span>  

 <span data-ttu-id="7a060-115">Поле `COR_HEAPOBJECT.type` является идентификатором вложенного COM-интерфейса с подсчетом ссылок.</span><span class="sxs-lookup"><span data-stu-id="7a060-115">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="7a060-116">Эта ссылка должна быть выпущена вызывающим объектом `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="7a060-116">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a060-117">Требования</span><span class="sxs-lookup"><span data-stu-id="7a060-117">Requirements</span></span>  

 <span data-ttu-id="7a060-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a060-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a060-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a060-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a060-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a060-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a060-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a060-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a060-122">См. также</span><span class="sxs-lookup"><span data-stu-id="7a060-122">See also</span></span>

- [<span data-ttu-id="7a060-123">Интерфейс ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="7a060-123">ICorDebugHeapEnum Interface</span></span>](icordebugheapenum-interface.md)
- [<span data-ttu-id="7a060-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7a060-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
