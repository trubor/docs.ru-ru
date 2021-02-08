---
description: 'Дополнительные сведения о: интерфейс ICLROnEventManager'
title: Интерфейс ICLROnEventManager
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: 7a9c0beec5083bc93f5361bb0e701da5beeedea2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789831"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="dd1cf-103">Интерфейс ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="dd1cf-103">ICLROnEventManager Interface</span></span>

<span data-ttu-id="dd1cf-104">Предоставляет методы, позволяющие основному приложению регистрировать и отменять регистрацию обратных вызовов для событий среды CLR.</span><span class="sxs-lookup"><span data-stu-id="dd1cf-104">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd1cf-105">Методы</span><span class="sxs-lookup"><span data-stu-id="dd1cf-105">Methods</span></span>  
  
|<span data-ttu-id="dd1cf-106">Метод</span><span class="sxs-lookup"><span data-stu-id="dd1cf-106">Method</span></span>|<span data-ttu-id="dd1cf-107">Описание</span><span class="sxs-lookup"><span data-stu-id="dd1cf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd1cf-108">Метод RegisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="dd1cf-108">RegisterActionOnEvent Method</span></span>](iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="dd1cf-109">Регистрирует указатель обратного вызова для указанного события.</span><span class="sxs-lookup"><span data-stu-id="dd1cf-109">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="dd1cf-110">Метод UnregisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="dd1cf-110">UnregisterActionOnEvent Method</span></span>](iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="dd1cf-111">Отменяет регистрацию ранее зарегистрированного указателя обратного вызова для указанного события.</span><span class="sxs-lookup"><span data-stu-id="dd1cf-111">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd1cf-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="dd1cf-112">Remarks</span></span>  

 <span data-ttu-id="dd1cf-113">Для регистрации и отмены регистрации обратных вызовов событий узел получает ссылку на `ICLROnEventManager` , вызывая метод [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dd1cf-113">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd1cf-114">События, описанные [еклревент](eclrevent-enumeration.md) , можно инициировать несколько раз и из разных потоков, чтобы сообщить о выгрузке или отключении среды CLR.</span><span class="sxs-lookup"><span data-stu-id="dd1cf-114">The events described by [EClrEvent](eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd1cf-115">Требования</span><span class="sxs-lookup"><span data-stu-id="dd1cf-115">Requirements</span></span>  

 <span data-ttu-id="dd1cf-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd1cf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd1cf-117">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dd1cf-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd1cf-118">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd1cf-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd1cf-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd1cf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd1cf-120">См. также</span><span class="sxs-lookup"><span data-stu-id="dd1cf-120">See also</span></span>

- [<span data-ttu-id="dd1cf-121">Перечисление EClrEvent</span><span class="sxs-lookup"><span data-stu-id="dd1cf-121">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="dd1cf-122">Интерфейс IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="dd1cf-122">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="dd1cf-123">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="dd1cf-123">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="dd1cf-124">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="dd1cf-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
