---
description: 'Дополнительные сведения о: интерфейс ICorDebugCode3'
title: Интерфейс ICorDebugCode3
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: 378141395ab4d23e3e33a84c3b14ca4a75d847dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764844"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="bc510-103">Интерфейс ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="bc510-103">ICorDebugCode3 Interface</span></span>

<span data-ttu-id="bc510-104">Предоставляет метод, который расширяет "ICorDebugCode" и "ICorDebugCode2" для предоставления сведений об управляемом возвращаемом значении.</span><span class="sxs-lookup"><span data-stu-id="bc510-104">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc510-105">Методы</span><span class="sxs-lookup"><span data-stu-id="bc510-105">Methods</span></span>  
  
|<span data-ttu-id="bc510-106">Метод</span><span class="sxs-lookup"><span data-stu-id="bc510-106">Method</span></span>|<span data-ttu-id="bc510-107">Описание</span><span class="sxs-lookup"><span data-stu-id="bc510-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc510-108">Метод GetReturnValueLiveOffset</span><span class="sxs-lookup"><span data-stu-id="bc510-108">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="bc510-109">Для указанного смещения IL получает машинные смещения, в которых должна быть помещена точка останова, чтобы отладчик мог получить возвращаемое значение из функции.</span><span class="sxs-lookup"><span data-stu-id="bc510-109">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc510-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="bc510-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc510-111">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="bc510-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc510-112">Требования</span><span class="sxs-lookup"><span data-stu-id="bc510-112">Requirements</span></span>  

 <span data-ttu-id="bc510-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc510-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc510-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc510-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc510-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc510-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc510-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc510-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc510-117">См. также</span><span class="sxs-lookup"><span data-stu-id="bc510-117">See also</span></span>

- [<span data-ttu-id="bc510-118">Интерфейс ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="bc510-118">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="bc510-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="bc510-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
