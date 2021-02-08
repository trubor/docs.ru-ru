---
description: Дополнительные сведения о перечислении Емеморяваилабле
title: Перечисление EMemoryAvailable
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
ms.openlocfilehash: fdb33b45c354d39b1a52fd815a44041b659181ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785452"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="9e506-103">Перечисление EMemoryAvailable</span><span class="sxs-lookup"><span data-stu-id="9e506-103">EMemoryAvailable Enumeration</span></span>

<span data-ttu-id="9e506-104">Содержит значения, указывающие объем свободной физической памяти на компьютере.</span><span class="sxs-lookup"><span data-stu-id="9e506-104">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="9e506-105">Эти значения логически сопоставляются с событиями для высокой и нехватки памяти, возвращаемой `CreateMemoryResourceNotification` функцией в Windows API.</span><span class="sxs-lookup"><span data-stu-id="9e506-105">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e506-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9e506-106">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="9e506-107">Члены</span><span class="sxs-lookup"><span data-stu-id="9e506-107">Members</span></span>  
  
|<span data-ttu-id="9e506-108">Член</span><span class="sxs-lookup"><span data-stu-id="9e506-108">Member</span></span>|<span data-ttu-id="9e506-109">Описание</span><span class="sxs-lookup"><span data-stu-id="9e506-109">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="9e506-110">Доступно достаточно физической памяти.</span><span class="sxs-lookup"><span data-stu-id="9e506-110">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="9e506-111">Доступно очень мало физической памяти.</span><span class="sxs-lookup"><span data-stu-id="9e506-111">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="9e506-112">Доступная физическая память не является нейтральной.</span><span class="sxs-lookup"><span data-stu-id="9e506-112">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e506-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="9e506-113">Remarks</span></span>  

 <span data-ttu-id="9e506-114">Это значение передается узлом в среду CLR с помощью вызова метода [ICLRMemoryNotificationCallback:: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9e506-114">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e506-115">Требования</span><span class="sxs-lookup"><span data-stu-id="9e506-115">Requirements</span></span>  

 <span data-ttu-id="9e506-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e506-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e506-117">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9e506-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e506-118">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9e506-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e506-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e506-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e506-120">См. также</span><span class="sxs-lookup"><span data-stu-id="9e506-120">See also</span></span>

- [<span data-ttu-id="9e506-121">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="9e506-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
