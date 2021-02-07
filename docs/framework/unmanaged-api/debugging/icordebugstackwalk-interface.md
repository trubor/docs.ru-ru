---
description: 'Дополнительные сведения о: интерфейс Икордебугстакквалк'
title: Интерфейс ICorDebugStackWalk
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
ms.openlocfilehash: 27dcdfc90829a3a28d81ad28dce0cd4d1d674948
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738095"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="6c976-103">Интерфейс ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="6c976-103">ICorDebugStackWalk Interface</span></span>

<span data-ttu-id="6c976-104">Обеспечивает методы для получения управляемых методов или кадров в стеке потока.</span><span class="sxs-lookup"><span data-stu-id="6c976-104">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c976-105">Методы</span><span class="sxs-lookup"><span data-stu-id="6c976-105">Methods</span></span>  
  
|<span data-ttu-id="6c976-106">Метод</span><span class="sxs-lookup"><span data-stu-id="6c976-106">Method</span></span>|<span data-ttu-id="6c976-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6c976-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c976-108">Метод GetContext</span><span class="sxs-lookup"><span data-stu-id="6c976-108">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="6c976-109">Возвращает контекст для текущего кадра в `ICorDebugStackWalk` объекте.</span><span class="sxs-lookup"><span data-stu-id="6c976-109">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="6c976-110">Метод SetContext</span><span class="sxs-lookup"><span data-stu-id="6c976-110">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="6c976-111">Задает `ICorDebugStackWalk` для текущего контекста объекта допустимый контекст для потока.</span><span class="sxs-lookup"><span data-stu-id="6c976-111">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="6c976-112">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="6c976-112">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="6c976-113">Перемещает `ICorDebugStackWalk` объект на следующий кадр.</span><span class="sxs-lookup"><span data-stu-id="6c976-113">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="6c976-114">Метод GetFrame</span><span class="sxs-lookup"><span data-stu-id="6c976-114">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="6c976-115">Возвращает текущий кадр в `ICorDebugStackWalk` объекте.</span><span class="sxs-lookup"><span data-stu-id="6c976-115">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c976-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="6c976-116">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c976-117">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="6c976-117">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c976-118">Требования</span><span class="sxs-lookup"><span data-stu-id="6c976-118">Requirements</span></span>  

 <span data-ttu-id="6c976-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c976-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c976-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c976-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c976-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c976-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c976-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c976-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c976-123">См. также</span><span class="sxs-lookup"><span data-stu-id="6c976-123">See also</span></span>

- [<span data-ttu-id="6c976-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6c976-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6c976-125">Отладка</span><span class="sxs-lookup"><span data-stu-id="6c976-125">Debugging</span></span>](index.md)
