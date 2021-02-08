---
description: 'Дополнительные сведения о методе: Икордебугхеапсегментенум:: Next'
title: Метод ICorDebugHeapSegmentEnum::Next
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 8d2ddfb4df82969fa9cf580ed8a7f903f9d6c260
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803680"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="96e1f-103">Метод ICorDebugHeapSegmentEnum::Next</span><span class="sxs-lookup"><span data-stu-id="96e1f-103">ICorDebugHeapSegmentEnum::Next Method</span></span>

<span data-ttu-id="96e1f-104">Возвращает указанное число экземпляров [COR_SEGMENT](cor-segment-structure.md) , содержащих сведения о регионах памяти управляемой кучи.</span><span class="sxs-lookup"><span data-stu-id="96e1f-104">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96e1f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="96e1f-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96e1f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="96e1f-106">Parameters</span></span>  

 <span data-ttu-id="96e1f-107">celt</span><span class="sxs-lookup"><span data-stu-id="96e1f-107">celt</span></span>  
 <span data-ttu-id="96e1f-108">окне Число извлекаемых сегментов.</span><span class="sxs-lookup"><span data-stu-id="96e1f-108">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="96e1f-109">сегменты</span><span class="sxs-lookup"><span data-stu-id="96e1f-109">segments</span></span>  
 <span data-ttu-id="96e1f-110">заполняет Массив указателей, каждый из которых указывает на объект [COR_SEGMENT](cor-segment-structure.md) , который предоставляет сведения о области памяти в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="96e1f-110">[out] An array of pointers, each of which points to a [COR_SEGMENT](cor-segment-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="96e1f-111">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="96e1f-111">pceltFetched</span></span>  
 <span data-ttu-id="96e1f-112">заполняет Указатель на число объектов [COR_SEGMENT](cor-segment-structure.md) , фактически возвращаемых в `segments` .</span><span class="sxs-lookup"><span data-stu-id="96e1f-112">[out] A pointer to the number of [COR_SEGMENT](cor-segment-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="96e1f-113">Это значение может быть `null`, если параметр `celt` имеет значение 1.</span><span class="sxs-lookup"><span data-stu-id="96e1f-113">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96e1f-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="96e1f-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96e1f-115">Требования</span><span class="sxs-lookup"><span data-stu-id="96e1f-115">Requirements</span></span>  

 <span data-ttu-id="96e1f-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96e1f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96e1f-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96e1f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96e1f-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96e1f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96e1f-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96e1f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e1f-120">См. также</span><span class="sxs-lookup"><span data-stu-id="96e1f-120">See also</span></span>

- [<span data-ttu-id="96e1f-121">Интерфейс ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="96e1f-121">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="96e1f-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="96e1f-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
