---
description: 'Дополнительные сведения о: интерфейс ICorDebugValue3'
title: Интерфейс ICorDebugValue3
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
ms.openlocfilehash: e5868b91d23426a2d8dd8fed87b13ec61fef95ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794654"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="1bb4c-103">Интерфейс ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="1bb4c-103">ICorDebugValue3 Interface</span></span>

<span data-ttu-id="1bb4c-104">Расширяет интерфейсы "ICorDebugValue" и "ICorDebugValue2", чтобы обеспечить поддержку массивов, размер которых превышает 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="1bb4c-104">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1bb4c-105">Методы</span><span class="sxs-lookup"><span data-stu-id="1bb4c-105">Methods</span></span>  
  
|<span data-ttu-id="1bb4c-106">Метод</span><span class="sxs-lookup"><span data-stu-id="1bb4c-106">Method</span></span>|<span data-ttu-id="1bb4c-107">Описание</span><span class="sxs-lookup"><span data-stu-id="1bb4c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1bb4c-108">Метод GetSize64</span><span class="sxs-lookup"><span data-stu-id="1bb4c-108">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)|<span data-ttu-id="1bb4c-109">Возвращает размер данного объекта в байтах `ICorDebugValue3` .</span><span class="sxs-lookup"><span data-stu-id="1bb4c-109">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bb4c-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="1bb4c-110">Remarks</span></span>  

 <span data-ttu-id="1bb4c-111">Метод [ICorDebugValue::](icordebugvalue3-getsize64-method.md) GetBytes возвращает размер объекта в диапазоне от 0 до 2 147 483 647 байт.</span><span class="sxs-lookup"><span data-stu-id="1bb4c-111">The [ICorDebugValue::GetSize](icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="1bb4c-112">В платформа .NET Framework 4,5 размер массивов может превышать 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="1bb4c-112">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="1bb4c-113">`ICorDebugValue3`Интерфейс позволяет определить размер этих массивов.</span><span class="sxs-lookup"><span data-stu-id="1bb4c-113">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bb4c-114">Требования</span><span class="sxs-lookup"><span data-stu-id="1bb4c-114">Requirements</span></span>  

 <span data-ttu-id="1bb4c-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bb4c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bb4c-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bb4c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bb4c-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bb4c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bb4c-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bb4c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb4c-119">См. также</span><span class="sxs-lookup"><span data-stu-id="1bb4c-119">See also</span></span>

- [<span data-ttu-id="1bb4c-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="1bb4c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1bb4c-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="1bb4c-121">Debugging</span></span>](index.md)
