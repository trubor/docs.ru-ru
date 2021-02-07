---
description: Дополнительные сведения о перечислении Кордебугусерстате
title: Перечисление CorDebugUserState
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: c556e7943751fb8e159e3e0d0b9a71baf1f6b5b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661744"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="1372e-103">Перечисление CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="1372e-103">CorDebugUserState Enumeration</span></span>

<span data-ttu-id="1372e-104">Указывает состояние пользователя потока.</span><span class="sxs-lookup"><span data-stu-id="1372e-104">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1372e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1372e-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a><span data-ttu-id="1372e-106">Члены</span><span class="sxs-lookup"><span data-stu-id="1372e-106">Members</span></span>  
  
|<span data-ttu-id="1372e-107">Значение</span><span class="sxs-lookup"><span data-stu-id="1372e-107">Value</span></span>|<span data-ttu-id="1372e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="1372e-108">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="1372e-109">Запрошено завершение потока.</span><span class="sxs-lookup"><span data-stu-id="1372e-109">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="1372e-110">Запрошена приостановка потока.</span><span class="sxs-lookup"><span data-stu-id="1372e-110">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="1372e-111">Поток выполняется в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="1372e-111">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="1372e-112">Поток не начал выполнять.</span><span class="sxs-lookup"><span data-stu-id="1372e-112">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="1372e-113">Поток был завершен.</span><span class="sxs-lookup"><span data-stu-id="1372e-113">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="1372e-114">Поток ожидает завершения задачи другим потоком.</span><span class="sxs-lookup"><span data-stu-id="1372e-114">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="1372e-115">Поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="1372e-115">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="1372e-116">Поток находится в ненадежной точке.</span><span class="sxs-lookup"><span data-stu-id="1372e-116">The thread is at an unsafe point.</span></span> <span data-ttu-id="1372e-117">Это значит, что поток находится в точке выполнения, где он может блокировать сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="1372e-117">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="1372e-118">События отладки могут быть отправлены из ненадежных точек, но приостановка потока в незащищенной точке, скорее всего, вызовет взаимоблокировку до возобновления потока.</span><span class="sxs-lookup"><span data-stu-id="1372e-118">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="1372e-119">Надежные и незащищенные точки определяются реализацией JIT и сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="1372e-119">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="1372e-120">Поток из пула потоков.</span><span class="sxs-lookup"><span data-stu-id="1372e-120">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1372e-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="1372e-121">Remarks</span></span>  

 <span data-ttu-id="1372e-122">Пользовательское состояние потока — это состояние, которое поток имеет при его проверке отладчиком.</span><span class="sxs-lookup"><span data-stu-id="1372e-122">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="1372e-123">Поток может иметь сочетание пользовательских состояний.</span><span class="sxs-lookup"><span data-stu-id="1372e-123">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="1372e-124">Чтобы получить состояние пользователя потока, используйте метод [ICorDebugThread:: жетусерстате](icordebugthread-getuserstate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1372e-124">Use the [ICorDebugThread::GetUserState](icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1372e-125">Требования</span><span class="sxs-lookup"><span data-stu-id="1372e-125">Requirements</span></span>  

 <span data-ttu-id="1372e-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1372e-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1372e-127">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1372e-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1372e-128">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1372e-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1372e-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1372e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1372e-130">См. также</span><span class="sxs-lookup"><span data-stu-id="1372e-130">See also</span></span>

- [<span data-ttu-id="1372e-131">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="1372e-131">Debugging Enumerations</span></span>](debugging-enumerations.md)
