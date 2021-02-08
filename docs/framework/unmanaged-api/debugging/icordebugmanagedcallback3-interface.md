---
description: 'Дополнительные сведения о: интерфейс ICorDebugManagedCallback3'
title: Интерфейс ICorDebugManagedCallback3
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: 9fb3d44b1d793935ac997e8e4d8d86de4466f7b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801193"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="49528-103">Интерфейс ICorDebugManagedCallback3</span><span class="sxs-lookup"><span data-stu-id="49528-103">ICorDebugManagedCallback3 Interface</span></span>

<span data-ttu-id="49528-104">Предоставляет метод обратного вызова, указывающий, что создано включенное пользовательское уведомление отладчика.</span><span class="sxs-lookup"><span data-stu-id="49528-104">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49528-105">Методы</span><span class="sxs-lookup"><span data-stu-id="49528-105">Methods</span></span>  
  
|<span data-ttu-id="49528-106">Метод</span><span class="sxs-lookup"><span data-stu-id="49528-106">Method</span></span>|<span data-ttu-id="49528-107">Описание</span><span class="sxs-lookup"><span data-stu-id="49528-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49528-108">Метод CustomNotification</span><span class="sxs-lookup"><span data-stu-id="49528-108">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="49528-109">Указывает, что создано включенное пользовательское уведомление отладчика.</span><span class="sxs-lookup"><span data-stu-id="49528-109">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49528-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="49528-110">Remarks</span></span>  

 <span data-ttu-id="49528-111">Этот интерфейс является логическим расширением интерфейсов [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) и [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="49528-111">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49528-112">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="49528-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49528-113">Требования</span><span class="sxs-lookup"><span data-stu-id="49528-113">Requirements</span></span>  

 <span data-ttu-id="49528-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49528-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49528-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49528-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49528-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49528-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49528-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49528-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49528-118">См. также</span><span class="sxs-lookup"><span data-stu-id="49528-118">See also</span></span>

- [<span data-ttu-id="49528-119">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="49528-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="49528-120">Интерфейс ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="49528-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="49528-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="49528-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="49528-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="49528-122">Debugging</span></span>](index.md)
