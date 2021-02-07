---
description: 'Дополнительные сведения о методе: IHostPolicyManager:: OnDefaultAction'
title: Метод IHostPolicyManager::OnDefaultAction
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: ea474734f7bc0a5210c5aecf605452909b261a87
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671929"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="39740-103">Метод IHostPolicyManager::OnDefaultAction</span><span class="sxs-lookup"><span data-stu-id="39740-103">IHostPolicyManager::OnDefaultAction Method</span></span>

<span data-ttu-id="39740-104">Уведомляет основное приложение о том, что среда CLR собирается выполнить действие по умолчанию, заданное вызовом метода [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) в ответ на прерывание или <xref:System.AppDomain> выгрузку потока.</span><span class="sxs-lookup"><span data-stu-id="39740-104">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39740-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="39740-105">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39740-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="39740-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="39740-107">окне Одно из значений [еклроператион](eclroperation-enumeration.md) , указывающее тип события, на которое отвечает среда CLR.</span><span class="sxs-lookup"><span data-stu-id="39740-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="39740-108">окне Одно из значений [еполициактион](epolicyaction-enumeration.md) , указывающее действие, которое среда CLR принимает в ответ на событие.</span><span class="sxs-lookup"><span data-stu-id="39740-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39740-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="39740-109">Return Value</span></span>  
  
|<span data-ttu-id="39740-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="39740-110">HRESULT</span></span>|<span data-ttu-id="39740-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="39740-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="39740-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="39740-112">S_OK</span></span>|<span data-ttu-id="39740-113">`OnDefaultAction` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="39740-113">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="39740-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="39740-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="39740-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="39740-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="39740-116">успешность</span><span class="sxs-lookup"><span data-stu-id="39740-116">successfully</span></span>|  
|<span data-ttu-id="39740-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="39740-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="39740-118">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="39740-118">The call timed out.</span></span>|  
|<span data-ttu-id="39740-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="39740-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="39740-120">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="39740-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="39740-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="39740-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="39740-122">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="39740-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="39740-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="39740-123">E_FAIL</span></span>|<span data-ttu-id="39740-124">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="39740-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="39740-125">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="39740-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="39740-126">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="39740-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="39740-127">Требования</span><span class="sxs-lookup"><span data-stu-id="39740-127">Requirements</span></span>  

 <span data-ttu-id="39740-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39740-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39740-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="39740-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="39740-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="39740-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39740-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39740-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39740-132">См. также</span><span class="sxs-lookup"><span data-stu-id="39740-132">See also</span></span>

- [<span data-ttu-id="39740-133">Перечисление EClrOperation</span><span class="sxs-lookup"><span data-stu-id="39740-133">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="39740-134">Перечисление EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="39740-134">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="39740-135">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="39740-135">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="39740-136">Интерфейс IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="39740-136">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
