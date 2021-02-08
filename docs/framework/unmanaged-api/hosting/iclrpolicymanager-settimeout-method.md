---
description: 'Дополнительные сведения о методе: ICLRPolicyManager:: SetTimeout'
title: Метод ICLRPolicyManager::SetTimeout
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type:
- apiref
ms.openlocfilehash: 5fb65e93cc6eea7826498ff6b03147773f06e0b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781900"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="c2787-103">Метод ICLRPolicyManager::SetTimeout</span><span class="sxs-lookup"><span data-stu-id="c2787-103">ICLRPolicyManager::SetTimeout Method</span></span>

<span data-ttu-id="c2787-104">Задает значение времени ожидания для указанной операции.</span><span class="sxs-lookup"><span data-stu-id="c2787-104">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2787-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c2787-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2787-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c2787-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="c2787-107">окне Одно из значений [еклроператион](eclroperation-enumeration.md) , указывающее на операцию среды CLR, для которой задается время ожидания.</span><span class="sxs-lookup"><span data-stu-id="c2787-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="c2787-108">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="c2787-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="c2787-109">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="c2787-109">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="c2787-110">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="c2787-110">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="c2787-111">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c2787-111">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="c2787-112">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c2787-112">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="c2787-113">окне Новое значение времени ожидания в миллисекундах.</span><span class="sxs-lookup"><span data-stu-id="c2787-113">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="c2787-114">Значение INFINITE приводит к тому, что время ожидания операции никогда не истекает.</span><span class="sxs-lookup"><span data-stu-id="c2787-114">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2787-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c2787-115">Return Value</span></span>  
  
|<span data-ttu-id="c2787-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2787-116">HRESULT</span></span>|<span data-ttu-id="c2787-117">Описание:</span><span class="sxs-lookup"><span data-stu-id="c2787-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2787-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2787-118">S_OK</span></span>|<span data-ttu-id="c2787-119">`SetTimeout` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="c2787-119">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="c2787-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c2787-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c2787-121">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="c2787-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c2787-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c2787-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c2787-123">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="c2787-123">The call timed out.</span></span>|  
|<span data-ttu-id="c2787-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c2787-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c2787-125">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="c2787-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c2787-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c2787-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c2787-127">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="c2787-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c2787-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2787-128">E_FAIL</span></span>|<span data-ttu-id="c2787-129">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="c2787-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2787-130">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="c2787-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c2787-131">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c2787-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c2787-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c2787-132">E_INVALIDARG</span></span>|<span data-ttu-id="c2787-133">Не удается задать время ожидания для указанного `operation` или указано недопустимое значение для `operation` .</span><span class="sxs-lookup"><span data-stu-id="c2787-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2787-134">Требования</span><span class="sxs-lookup"><span data-stu-id="c2787-134">Requirements</span></span>  

 <span data-ttu-id="c2787-135">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2787-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2787-136">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c2787-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2787-137">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2787-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2787-138">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2787-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2787-139">См. также</span><span class="sxs-lookup"><span data-stu-id="c2787-139">See also</span></span>

- [<span data-ttu-id="c2787-140">Перечисление EClrOperation</span><span class="sxs-lookup"><span data-stu-id="c2787-140">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="c2787-141">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="c2787-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="c2787-142">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="c2787-142">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
