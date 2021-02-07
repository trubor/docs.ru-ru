---
description: 'Дополнительные сведения о методе: IHostPolicyManager:: onFailure'
title: Метод IHostPolicyManager::OnFailure
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
ms.openlocfilehash: 9fb359d4ba1b1b89e029a0772a0f67a49b2b380b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671845"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="b567f-103">Метод IHostPolicyManager::OnFailure</span><span class="sxs-lookup"><span data-stu-id="b567f-103">IHostPolicyManager::OnFailure Method</span></span>

<span data-ttu-id="b567f-104">Уведомляет основное приложение о том, что среда CLR собирается выполнить действие, заданное вызовом метода [ICLRPolicyManager:: сетактиононфаилуре](iclrpolicymanager-setactiononfailure-method.md) в ответ на выделение ресурсов или сбой при реорганизации.</span><span class="sxs-lookup"><span data-stu-id="b567f-104">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b567f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b567f-105">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b567f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b567f-106">Parameters</span></span>  

 `failure`  
 <span data-ttu-id="b567f-107">окне Одно из значений [еклрфаилуре](eclrfailure-enumeration.md) , указывающее тип сбоя, на который отвечает среда CLR.</span><span class="sxs-lookup"><span data-stu-id="b567f-107">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="b567f-108">окне Одно из значений [еполициактион](epolicyaction-enumeration.md) , указывающее действие, ВЫПОЛНЯЕМое средой CLR в ответ на запрос `failure` .</span><span class="sxs-lookup"><span data-stu-id="b567f-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b567f-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b567f-109">Return Value</span></span>  
  
|<span data-ttu-id="b567f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b567f-110">HRESULT</span></span>|<span data-ttu-id="b567f-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="b567f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b567f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b567f-112">S_OK</span></span>|<span data-ttu-id="b567f-113">`OnFailure` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="b567f-113">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="b567f-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b567f-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b567f-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="b567f-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b567f-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b567f-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b567f-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="b567f-117">The call timed out.</span></span>|  
|<span data-ttu-id="b567f-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b567f-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b567f-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="b567f-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b567f-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b567f-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b567f-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="b567f-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b567f-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b567f-122">E_FAIL</span></span>|<span data-ttu-id="b567f-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="b567f-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b567f-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="b567f-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b567f-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b567f-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b567f-126">Требования</span><span class="sxs-lookup"><span data-stu-id="b567f-126">Requirements</span></span>  

 <span data-ttu-id="b567f-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b567f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b567f-128">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b567f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b567f-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b567f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b567f-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b567f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b567f-131">См. также</span><span class="sxs-lookup"><span data-stu-id="b567f-131">See also</span></span>

- [<span data-ttu-id="b567f-132">Перечисление EClrFailure</span><span class="sxs-lookup"><span data-stu-id="b567f-132">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="b567f-133">Перечисление EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="b567f-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="b567f-134">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="b567f-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="b567f-135">Интерфейс IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="b567f-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
