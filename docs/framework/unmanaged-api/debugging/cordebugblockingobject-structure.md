---
description: 'Дополнительные сведения о: структура CorDebugBlockingObject'
title: Структура CorDebugBlockingObject
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
ms.openlocfilehash: 2b16af5eecb01067c2ee6811613f964af391f345
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712224"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="f3a86-103">Структура CorDebugBlockingObject</span><span class="sxs-lookup"><span data-stu-id="f3a86-103">CorDebugBlockingObject Structure</span></span>

<span data-ttu-id="f3a86-104">Определяет объект, который блокирует поток и конкретную причину блокировки потока.</span><span class="sxs-lookup"><span data-stu-id="f3a86-104">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3a86-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f3a86-105">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="f3a86-106">Члены</span><span class="sxs-lookup"><span data-stu-id="f3a86-106">Members</span></span>  
  
|<span data-ttu-id="f3a86-107">Член</span><span class="sxs-lookup"><span data-stu-id="f3a86-107">Member</span></span>|<span data-ttu-id="f3a86-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f3a86-108">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="f3a86-109">Объект, для которого блокируется поток.</span><span class="sxs-lookup"><span data-stu-id="f3a86-109">The object on which the thread is blocking.</span></span> <span data-ttu-id="f3a86-110">Этот объект допустим только в течение текущего синхронизированного состояния.</span><span class="sxs-lookup"><span data-stu-id="f3a86-110">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="f3a86-111">Если два потока блокируют один и тот же объект в одном и том же синхронизированном состоянии, то, возможно, предполагается, что метод [ICorDebugValue::](icordebugvalue-getaddress-method.md) GetObject возвратит одно и то же значение.</span><span class="sxs-lookup"><span data-stu-id="f3a86-111">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="f3a86-112">Однако интерфейсы могут и не быть эквивалентными указателями.</span><span class="sxs-lookup"><span data-stu-id="f3a86-112">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="f3a86-113">Время ожидания (в миллисекундах), по истечении которого операция блокирования истечет или бесконечное значение, которое указывает, что время ожидания не истечет. Значение времени ожидания указывает общий период времени для блокирующей операции, а не оставшееся время.</span><span class="sxs-lookup"><span data-stu-id="f3a86-113">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="f3a86-114">Причина, по которой поток блокируется для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="f3a86-114">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3a86-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="f3a86-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3a86-116">Требования</span><span class="sxs-lookup"><span data-stu-id="f3a86-116">Requirements</span></span>  

 <span data-ttu-id="f3a86-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3a86-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3a86-118">**Заголовок:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="f3a86-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="f3a86-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3a86-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3a86-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3a86-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a86-121">См. также</span><span class="sxs-lookup"><span data-stu-id="f3a86-121">See also</span></span>

- [<span data-ttu-id="f3a86-122">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="f3a86-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="f3a86-123">Отладка</span><span class="sxs-lookup"><span data-stu-id="f3a86-123">Debugging</span></span>](index.md)
