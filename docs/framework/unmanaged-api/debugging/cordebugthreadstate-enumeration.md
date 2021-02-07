---
description: Дополнительные сведения о перечислении Кордебугсреадстате
title: Перечисление CorDebugThreadState
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 0cf83ee31547e49ccc7d09e0ab4ee85548688b36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661812"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="704d4-103">Перечисление CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="704d4-103">CorDebugThreadState Enumeration</span></span>

<span data-ttu-id="704d4-104">Указывает состояние потока для отладки.</span><span class="sxs-lookup"><span data-stu-id="704d4-104">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="704d4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="704d4-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="704d4-106">Члены</span><span class="sxs-lookup"><span data-stu-id="704d4-106">Members</span></span>  
  
|<span data-ttu-id="704d4-107">Член</span><span class="sxs-lookup"><span data-stu-id="704d4-107">Member</span></span>|<span data-ttu-id="704d4-108">Описание</span><span class="sxs-lookup"><span data-stu-id="704d4-108">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="704d4-109">Поток выполняется свободно, если не происходит событие отладки.</span><span class="sxs-lookup"><span data-stu-id="704d4-109">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="704d4-110">Поток не может быть запущен.</span><span class="sxs-lookup"><span data-stu-id="704d4-110">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="704d4-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="704d4-111">Remarks</span></span>  

 <span data-ttu-id="704d4-112">Отладчик использует `CorDebugThreadState` перечисление для управления выполнением потока.</span><span class="sxs-lookup"><span data-stu-id="704d4-112">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="704d4-113">Состояние потока можно задать с помощью метода [ICorDebugThread:: SetDebugState](icordebugthread-setdebugstate-method.md) или [ICorDebugController:: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="704d4-113">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="704d4-114">Обратный вызов, предоставленный [API размещения](../hosting/index.md) , позволяет передавать сообщения, поэтому прерывание состояния не требуется.</span><span class="sxs-lookup"><span data-stu-id="704d4-114">A callback provided to the [hosting API](../hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="704d4-115">Требования</span><span class="sxs-lookup"><span data-stu-id="704d4-115">Requirements</span></span>  

 <span data-ttu-id="704d4-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="704d4-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="704d4-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="704d4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="704d4-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="704d4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="704d4-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="704d4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="704d4-120">См. также</span><span class="sxs-lookup"><span data-stu-id="704d4-120">See also</span></span>

- [<span data-ttu-id="704d4-121">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="704d4-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
