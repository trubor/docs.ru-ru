---
description: 'Дополнительные сведения о: интерфейс ICorDebugThread2'
title: Интерфейс ICorDebugThread2
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: 81f687f6daff9ffa7298ec6d818a214b8934bcc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658507"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="893ee-103">Интерфейс ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="893ee-103">ICorDebugThread2 Interface</span></span>

<span data-ttu-id="893ee-104">Служит логическим расширением интерфейса ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="893ee-104">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="893ee-105">Методы</span><span class="sxs-lookup"><span data-stu-id="893ee-105">Methods</span></span>  
  
|<span data-ttu-id="893ee-106">Метод</span><span class="sxs-lookup"><span data-stu-id="893ee-106">Method</span></span>|<span data-ttu-id="893ee-107">Описание</span><span class="sxs-lookup"><span data-stu-id="893ee-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="893ee-108">Метод GetActiveFunctions</span><span class="sxs-lookup"><span data-stu-id="893ee-108">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="893ee-109">Возвращает массив экземпляров COR_ACTIVE_FUNCTION, содержащих данные об активных функциях в кадрах потока.</span><span class="sxs-lookup"><span data-stu-id="893ee-109">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="893ee-110">Метод GetConnectionID</span><span class="sxs-lookup"><span data-stu-id="893ee-110">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="893ee-111">Возвращает идентификатор соединения для этого `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="893ee-111">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="893ee-112">Метод GetTaskID</span><span class="sxs-lookup"><span data-stu-id="893ee-112">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="893ee-113">Возвращает идентификатор задачи для этого `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="893ee-113">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="893ee-114">Метод GetVolatileOSThreadID</span><span class="sxs-lookup"><span data-stu-id="893ee-114">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="893ee-115">Возвращает идентификатор потока операционной системы для этого `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="893ee-115">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="893ee-116">Метод InterceptCurrentException</span><span class="sxs-lookup"><span data-stu-id="893ee-116">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="893ee-117">Позволяет отладчику перехватывать текущее исключение в потоке.</span><span class="sxs-lookup"><span data-stu-id="893ee-117">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="893ee-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="893ee-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="893ee-119">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="893ee-119">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="893ee-120">Требования</span><span class="sxs-lookup"><span data-stu-id="893ee-120">Requirements</span></span>  

 <span data-ttu-id="893ee-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="893ee-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="893ee-122">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="893ee-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="893ee-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="893ee-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="893ee-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="893ee-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="893ee-125">См. также</span><span class="sxs-lookup"><span data-stu-id="893ee-125">See also</span></span>

- [<span data-ttu-id="893ee-126">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="893ee-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
