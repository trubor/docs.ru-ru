---
description: Дополнительные сведения о перечислении Кордебугблоккингреасон
title: Перечисление CorDebugBlockingReason
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
ms.openlocfilehash: c2d9c805549d046fe40ab5ea00f30e2fd0a680a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747114"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="ede0c-103">Перечисление CorDebugBlockingReason</span><span class="sxs-lookup"><span data-stu-id="ede0c-103">CorDebugBlockingReason Enumeration</span></span>

<span data-ttu-id="ede0c-104">Указывает возможные причины блокировки потока на данном объекте.</span><span class="sxs-lookup"><span data-stu-id="ede0c-104">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ede0c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ede0c-105">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="ede0c-106">Члены</span><span class="sxs-lookup"><span data-stu-id="ede0c-106">Members</span></span>  
  
|<span data-ttu-id="ede0c-107">Член</span><span class="sxs-lookup"><span data-stu-id="ede0c-107">Member</span></span>|<span data-ttu-id="ede0c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ede0c-108">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="ede0c-109">Только для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="ede0c-109">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="ede0c-110">Поток пытается получить критическую секцию, связанную с блокировкой монитора для объекта.</span><span class="sxs-lookup"><span data-stu-id="ede0c-110">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="ede0c-111">Как правило, это происходит при вызове одного из <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> методов или.</span><span class="sxs-lookup"><span data-stu-id="ede0c-111">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="ede0c-112">Поток ожидает события, связанного с блокировкой монитора для объекта.</span><span class="sxs-lookup"><span data-stu-id="ede0c-112">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="ede0c-113">Как правило, это происходит при вызове одного из <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` методов.</span><span class="sxs-lookup"><span data-stu-id="ede0c-113">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ede0c-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="ede0c-114">Remarks</span></span>  

 <span data-ttu-id="ede0c-115">Если `BLOCKING_MONITOR_CRITICAL_SECTION` элемент или `BLOCKING_MONITOR_EVENT` используется в структуре [CorDebugBlockingObject](cordebugblockingobject-structure.md) , `pBlockingObject` элемент структуры указывает на интерфейс "ICorDebugValue", представляющий объект, который необходимо указать.</span><span class="sxs-lookup"><span data-stu-id="ede0c-115">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="ede0c-116">Также гарантируется реализация интерфейса [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ede0c-116">It is also guaranteed to implement the [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ede0c-117">Требования</span><span class="sxs-lookup"><span data-stu-id="ede0c-117">Requirements</span></span>  

 <span data-ttu-id="ede0c-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ede0c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ede0c-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ede0c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ede0c-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ede0c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ede0c-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ede0c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede0c-122">См. также</span><span class="sxs-lookup"><span data-stu-id="ede0c-122">See also</span></span>

- [<span data-ttu-id="ede0c-123">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="ede0c-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="ede0c-124">Отладка</span><span class="sxs-lookup"><span data-stu-id="ede0c-124">Debugging</span></span>](index.md)
