---
description: Дополнительные сведения о перечислении Етасктипе
title: Перечисление ETaskType
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: 7cb241765b2ff3b4a3402221c6b3e2b7ff6305c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785410"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="8f542-103">Перечисление ETaskType</span><span class="sxs-lookup"><span data-stu-id="8f542-103">ETaskType Enumeration</span></span>

<span data-ttu-id="8f542-104">Содержит значения, указывающие тип задачи, представленной интерфейсом [ICLRTask](iclrtask-interface.md) или [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8f542-104">Contains values that indicate the type of task that is represented by either an [ICLRTask](iclrtask-interface.md) or an [IHostTask](ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f542-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8f542-105">Syntax</span></span>  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a><span data-ttu-id="8f542-106">Члены</span><span class="sxs-lookup"><span data-stu-id="8f542-106">Members</span></span>  
  
|<span data-ttu-id="8f542-107">Член</span><span class="sxs-lookup"><span data-stu-id="8f542-107">Member</span></span>|<span data-ttu-id="8f542-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8f542-108">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="8f542-109">Интерфейс представляет задачу выгрузки домена приложения.</span><span class="sxs-lookup"><span data-stu-id="8f542-109">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="8f542-110">Интерфейс представляет вспомогательную задачу отладчика.</span><span class="sxs-lookup"><span data-stu-id="8f542-110">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="8f542-111">Интерфейс представляет задачу финализатора.</span><span class="sxs-lookup"><span data-stu-id="8f542-111">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="8f542-112">Интерфейс представляет задачу сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="8f542-112">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="8f542-113">Интерфейс представляет задачу потока шлюза.</span><span class="sxs-lookup"><span data-stu-id="8f542-113">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="8f542-114">Интерфейс представляет задачу потока ввода-вывода или задачи потока порта завершения.</span><span class="sxs-lookup"><span data-stu-id="8f542-114">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="8f542-115">Интерфейс представляет задачу потока таймера.</span><span class="sxs-lookup"><span data-stu-id="8f542-115">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="8f542-116">Интерфейс представляет задачу потока ожидания.</span><span class="sxs-lookup"><span data-stu-id="8f542-116">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="8f542-117">Интерфейс представляет задачу рабочего потока.</span><span class="sxs-lookup"><span data-stu-id="8f542-117">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="8f542-118">Задача неизвестна.</span><span class="sxs-lookup"><span data-stu-id="8f542-118">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="8f542-119">Интерфейс представляет задачу пользователя.</span><span class="sxs-lookup"><span data-stu-id="8f542-119">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f542-120">Требования</span><span class="sxs-lookup"><span data-stu-id="8f542-120">Requirements</span></span>  

 <span data-ttu-id="8f542-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f542-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f542-122">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8f542-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f542-123">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f542-123">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f542-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f542-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f542-125">См. также</span><span class="sxs-lookup"><span data-stu-id="8f542-125">See also</span></span>

- [<span data-ttu-id="8f542-126">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="8f542-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
