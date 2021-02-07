---
description: 'Дополнительные сведения о: интерфейс IHostPolicyManager'
title: Интерфейс IHostPolicyManager
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: d823ee2526019188afd17df903b61a720e18207f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671936"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="33a7d-103">Интерфейс IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="33a7d-103">IHostPolicyManager Interface</span></span>

<span data-ttu-id="33a7d-104">Предоставляет методы, уведомляющие узел о действиях, выполняемых средой CLR в случае прерываний, времени ожидания или сбоев.</span><span class="sxs-lookup"><span data-stu-id="33a7d-104">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33a7d-105">Методы</span><span class="sxs-lookup"><span data-stu-id="33a7d-105">Methods</span></span>  
  
|<span data-ttu-id="33a7d-106">Метод</span><span class="sxs-lookup"><span data-stu-id="33a7d-106">Method</span></span>|<span data-ttu-id="33a7d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="33a7d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33a7d-108">Метод OnDefaultAction</span><span class="sxs-lookup"><span data-stu-id="33a7d-108">OnDefaultAction Method</span></span>](ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="33a7d-109">Уведомляет основное приложение о том, что среда CLR собирается принять действие по умолчанию, заданное вызовом метода [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) в ответ на прерывание или <xref:System.AppDomain> выгрузку потока.</span><span class="sxs-lookup"><span data-stu-id="33a7d-109">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="33a7d-110">Метод OnFailure</span><span class="sxs-lookup"><span data-stu-id="33a7d-110">OnFailure Method</span></span>](ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="33a7d-111">Уведомляет основное приложение о том, что среда CLR собирается выполнить действие, заданное вызовом [ICLRPolicyManager:: сетактиононфаилуре](iclrpolicymanager-setactiononfailure-method.md) в ответ на выделение ресурсов или сбой при реорганизации.</span><span class="sxs-lookup"><span data-stu-id="33a7d-111">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="33a7d-112">Метод OnTimeout</span><span class="sxs-lookup"><span data-stu-id="33a7d-112">OnTimeout Method</span></span>](ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="33a7d-113">Уведомляет основное приложение о том, что среда CLR собирается выполнить действие, заданное вызовом метода [ICLRPolicyManager:: сетактиононтимеаут](iclrpolicymanager-setactionontimeout-method.md) в ответ на время ожидания.</span><span class="sxs-lookup"><span data-stu-id="33a7d-113">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33a7d-114">Требования</span><span class="sxs-lookup"><span data-stu-id="33a7d-114">Requirements</span></span>  

 <span data-ttu-id="33a7d-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33a7d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33a7d-116">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="33a7d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33a7d-117">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33a7d-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33a7d-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33a7d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a7d-119">См. также</span><span class="sxs-lookup"><span data-stu-id="33a7d-119">See also</span></span>

- [<span data-ttu-id="33a7d-120">Перечисление EClrFailure</span><span class="sxs-lookup"><span data-stu-id="33a7d-120">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="33a7d-121">Перечисление EClrOperation</span><span class="sxs-lookup"><span data-stu-id="33a7d-121">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="33a7d-122">Перечисление EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="33a7d-122">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="33a7d-123">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="33a7d-123">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="33a7d-124">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="33a7d-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
