---
description: 'Дополнительные сведения о методе: ICLROnEventManager:: Унрегистерактиононевент'
title: Метод ICLROnEventManager::UnregisterActionOnEvent
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
ms.openlocfilehash: 8131c58669ff7be0fdc2b2e063c70d3b370921e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789818"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="aaafb-103">Метод ICLROnEventManager::UnregisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="aaafb-103">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>

<span data-ttu-id="aaafb-104">Отменяет регистрацию ранее зарегистрированного указателя обратного вызова для указанного события.</span><span class="sxs-lookup"><span data-stu-id="aaafb-104">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaafb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aaafb-105">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaafb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="aaafb-106">Parameters</span></span>  

 `event`  
 <span data-ttu-id="aaafb-107">окне Одно из значений [еклревент](eclrevent-enumeration.md) , указывающее событие, для которого отменяется регистрация указателя обратного вызова, описанного в `pAction` .</span><span class="sxs-lookup"><span data-stu-id="aaafb-107">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="aaafb-108">окне Указатель на объект [иактиононклревент](iactiononclrevent-interface.md) , переданный в качестве параметра в метод [регистерактиононевент](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="aaafb-108">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaafb-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="aaafb-109">Return Value</span></span>  
  
|<span data-ttu-id="aaafb-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aaafb-110">HRESULT</span></span>|<span data-ttu-id="aaafb-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="aaafb-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aaafb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="aaafb-112">S_OK</span></span>|<span data-ttu-id="aaafb-113">`UnregisterActionOnEvent` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="aaafb-113">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="aaafb-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aaafb-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aaafb-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="aaafb-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aaafb-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aaafb-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aaafb-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="aaafb-117">The call timed out.</span></span>|  
|<span data-ttu-id="aaafb-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aaafb-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aaafb-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="aaafb-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aaafb-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aaafb-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aaafb-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="aaafb-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aaafb-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aaafb-122">E_FAIL</span></span>|<span data-ttu-id="aaafb-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="aaafb-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aaafb-124">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="aaafb-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aaafb-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aaafb-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aaafb-126">Требования</span><span class="sxs-lookup"><span data-stu-id="aaafb-126">Requirements</span></span>  

 <span data-ttu-id="aaafb-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaafb-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaafb-128">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aaafb-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aaafb-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aaafb-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aaafb-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaafb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaafb-131">См. также</span><span class="sxs-lookup"><span data-stu-id="aaafb-131">See also</span></span>

- [<span data-ttu-id="aaafb-132">Перечисление EClrEvent</span><span class="sxs-lookup"><span data-stu-id="aaafb-132">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="aaafb-133">Интерфейс IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="aaafb-133">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="aaafb-134">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="aaafb-134">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="aaafb-135">Интерфейс ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="aaafb-135">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
