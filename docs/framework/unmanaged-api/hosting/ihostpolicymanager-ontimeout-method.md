---
description: 'Дополнительные сведения о методе: IHostPolicyManager:: untime'
title: Метод IHostPolicyManager::OnTimeout
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
ms.openlocfilehash: 3a4b1dcf632a0a67c541cacf7c872b3f994e8a07
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671832"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="57166-103">Метод IHostPolicyManager::OnTimeout</span><span class="sxs-lookup"><span data-stu-id="57166-103">IHostPolicyManager::OnTimeout Method</span></span>

<span data-ttu-id="57166-104">Уведомляет основное приложение о том, что среда CLR собирается выполнить действие, заданное вызовом метода [ICLRPolicyManager:: сетактиононтимеаут](iclrpolicymanager-setactionontimeout-method.md) в ответ на время ожидания.</span><span class="sxs-lookup"><span data-stu-id="57166-104">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57166-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="57166-105">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57166-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="57166-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="57166-107">окне Одно из значений [еклроператион](eclroperation-enumeration.md) , указывающее тип операции, для которой истекло время ожидания.</span><span class="sxs-lookup"><span data-stu-id="57166-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="57166-108">окне Одно из значений [еполициактион](epolicyaction-enumeration.md) , указывающее действие, ВЫПОЛНЯЕМое средой CLR в ответ на время ожидания.</span><span class="sxs-lookup"><span data-stu-id="57166-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57166-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="57166-109">Return Value</span></span>  
  
|<span data-ttu-id="57166-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57166-110">HRESULT</span></span>|<span data-ttu-id="57166-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="57166-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57166-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="57166-112">S_OK</span></span>|<span data-ttu-id="57166-113">`OnTimeout` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="57166-113">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="57166-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57166-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57166-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="57166-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57166-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57166-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57166-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="57166-117">The call timed out.</span></span>|  
|<span data-ttu-id="57166-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57166-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57166-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="57166-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57166-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57166-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57166-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="57166-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57166-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57166-122">E_FAIL</span></span>|<span data-ttu-id="57166-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="57166-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57166-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="57166-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57166-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57166-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57166-126">Требования</span><span class="sxs-lookup"><span data-stu-id="57166-126">Requirements</span></span>  

 <span data-ttu-id="57166-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57166-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57166-128">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="57166-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57166-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57166-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57166-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57166-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57166-131">См. также</span><span class="sxs-lookup"><span data-stu-id="57166-131">See also</span></span>

- [<span data-ttu-id="57166-132">Перечисление EClrOperation</span><span class="sxs-lookup"><span data-stu-id="57166-132">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="57166-133">Перечисление EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="57166-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="57166-134">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="57166-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="57166-135">Интерфейс IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="57166-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
