---
description: Дополнительные сведения о перечислении Еконтексттипе
title: Перечисление EContextType
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
ms.openlocfilehash: b7d6ddb385386bb0616a01ef6fcc432f2c925d51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785540"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="90353-103">Перечисление EContextType</span><span class="sxs-lookup"><span data-stu-id="90353-103">EContextType Enumeration</span></span>

<span data-ttu-id="90353-104">Описывает контекст безопасности выполняющегося в данный момент потока.</span><span class="sxs-lookup"><span data-stu-id="90353-104">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90353-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="90353-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="90353-106">Члены</span><span class="sxs-lookup"><span data-stu-id="90353-106">Members</span></span>  
  
|<span data-ttu-id="90353-107">Член</span><span class="sxs-lookup"><span data-stu-id="90353-107">Member</span></span>|<span data-ttu-id="90353-108">Описание</span><span class="sxs-lookup"><span data-stu-id="90353-108">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="90353-109">Указывает контекст текущего потока во время вызова средой CLR метода [IHostSecurityManager:: getsecuritycontext-](ihostsecuritymanager-getsecuritycontext-method.md) или контекста, ЗАПРАШИВАЕМого средой CLR при вызове метода [IHostSecurityManager:: SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="90353-109">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="90353-110">Указывает контекст, для которого узел имеет более низкий уровень привилегий, например сборщик мусора, конструктор класса или модуля.</span><span class="sxs-lookup"><span data-stu-id="90353-110">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90353-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="90353-111">Remarks</span></span>  

 <span data-ttu-id="90353-112">Среда CLR предоставляет одно из `EContextType` значений в качестве значения параметра в вызовах `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` методов и.</span><span class="sxs-lookup"><span data-stu-id="90353-112">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90353-113">Требования</span><span class="sxs-lookup"><span data-stu-id="90353-113">Requirements</span></span>  

 <span data-ttu-id="90353-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90353-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90353-115">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="90353-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90353-116">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90353-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90353-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90353-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90353-118">См. также</span><span class="sxs-lookup"><span data-stu-id="90353-118">See also</span></span>

- [<span data-ttu-id="90353-119">Интерфейс IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="90353-119">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="90353-120">Интерфейс IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="90353-120">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="90353-121">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="90353-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
