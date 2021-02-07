---
description: 'Дополнительные сведения: перечисление WAIT_OPTION'
title: Перечисление WAIT_OPTION
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
ms.openlocfilehash: 1d651909e0f62f2db7478a6e0b37139d1f953196
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679138"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="0727a-103">Перечисление WAIT_OPTION</span><span class="sxs-lookup"><span data-stu-id="0727a-103">WAIT_OPTION Enumeration</span></span>

<span data-ttu-id="0727a-104">Содержит значения, указывающие действие, которое должен выполнить узел при выполнении операции, запрашиваемой блоками среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0727a-104">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0727a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0727a-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="0727a-106">Члены</span><span class="sxs-lookup"><span data-stu-id="0727a-106">Members</span></span>  
  
|<span data-ttu-id="0727a-107">Член</span><span class="sxs-lookup"><span data-stu-id="0727a-107">Member</span></span>|<span data-ttu-id="0727a-108">Описание</span><span class="sxs-lookup"><span data-stu-id="0727a-108">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="0727a-109">Уведомляет узел о том, что задача должна быть пробуждена, если среда CLR вызывает метод [IHostTask:: Alert](ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0727a-109">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="0727a-110">Уведомляет узел о том, что он должен передавать сообщения в текущем потоке операционной системы, если поток блокируется.</span><span class="sxs-lookup"><span data-stu-id="0727a-110">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="0727a-111">Среда выполнения задает это значение только в <xref:System.Threading.ApartmentState.STA> потоке.</span><span class="sxs-lookup"><span data-stu-id="0727a-111">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="0727a-112">Сообщает узлу, что указанный запрос на синхронизацию не может быть разбит узлом.</span><span class="sxs-lookup"><span data-stu-id="0727a-112">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="0727a-113">Это значит, что узел не может вернуть `HOST_E_DEADLOCK` .</span><span class="sxs-lookup"><span data-stu-id="0727a-113">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0727a-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="0727a-114">Remarks</span></span>  

 <span data-ttu-id="0727a-115">Методы [IHostTaskManager:: Sleep](ihosttaskmanager-sleep-method.md) и [IHostTaskManager:: свитчтотаск](ihosttaskmanager-switchtotask-method.md) принимают параметр этого типа.</span><span class="sxs-lookup"><span data-stu-id="0727a-115">The [IHostTaskManager::Sleep](ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0727a-116">Требования</span><span class="sxs-lookup"><span data-stu-id="0727a-116">Requirements</span></span>  

 <span data-ttu-id="0727a-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0727a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0727a-118">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0727a-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0727a-119">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0727a-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0727a-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0727a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0727a-121">См. также</span><span class="sxs-lookup"><span data-stu-id="0727a-121">See also</span></span>

- [<span data-ttu-id="0727a-122">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="0727a-122">Hosting Enumerations</span></span>](hosting-enumerations.md)
