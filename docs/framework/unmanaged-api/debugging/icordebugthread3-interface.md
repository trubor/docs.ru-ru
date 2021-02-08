---
description: 'Дополнительные сведения о: интерфейс ICorDebugThread3'
title: Интерфейс ICorDebugThread3
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 88c668f1e08d0843f26d231937c85d80e03bee6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800972"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="04056-103">Интерфейс ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="04056-103">ICorDebugThread3 Interface</span></span>

<span data-ttu-id="04056-104">Предоставляет точку входа для [икордебугстакквалк](icordebugstackwalk-interface.md) и соответствующих интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="04056-104">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04056-105">Методы</span><span class="sxs-lookup"><span data-stu-id="04056-105">Methods</span></span>  
  
|<span data-ttu-id="04056-106">Метод</span><span class="sxs-lookup"><span data-stu-id="04056-106">Method</span></span>|<span data-ttu-id="04056-107">Описание</span><span class="sxs-lookup"><span data-stu-id="04056-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04056-108">Метод CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="04056-108">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="04056-109">Создает объект [икордебугстакквалк](icordebugstackwalk-interface.md) для потока, стек которого нужно очистить.</span><span class="sxs-lookup"><span data-stu-id="04056-109">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="04056-110">Метод GetActiveInternalFrames</span><span class="sxs-lookup"><span data-stu-id="04056-110">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="04056-111">Возвращает массив внутренних кадров (объектов[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) в стеке.</span><span class="sxs-lookup"><span data-stu-id="04056-111">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04056-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="04056-112">Remarks</span></span>  

 <span data-ttu-id="04056-113">`ICorDebugThread3` является логическим расширением для интерфейса ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="04056-113">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04056-114">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="04056-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04056-115">Требования</span><span class="sxs-lookup"><span data-stu-id="04056-115">Requirements</span></span>  

 <span data-ttu-id="04056-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04056-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04056-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04056-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04056-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04056-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04056-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04056-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04056-120">См. также</span><span class="sxs-lookup"><span data-stu-id="04056-120">See also</span></span>

- [<span data-ttu-id="04056-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="04056-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="04056-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="04056-122">Debugging</span></span>](index.md)
