---
description: 'Дополнительные сведения о методе: Иактиононклревент:: oneven'
title: Метод IActionOnCLREvent::OnEvent
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
ms.openlocfilehash: 163956ab319eb34d58da23d2c4ef2a6b592aab0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785150"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="e8a40-103">Метод IActionOnCLREvent::OnEvent</span><span class="sxs-lookup"><span data-stu-id="e8a40-103">IActionOnCLREvent::OnEvent Method</span></span>

<span data-ttu-id="e8a40-104">Выполняет обратные вызовы для событий, зарегистрированных с помощью вызова метода [ICLROnEventManager:: регистерактиононевент](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e8a40-104">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8a40-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e8a40-105">Syntax</span></span>  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8a40-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e8a40-106">Parameters</span></span>  

 `event`  
 <span data-ttu-id="e8a40-107">окне Одно из значений [еклревент](eclrevent-enumeration.md) , указывающее тип события.</span><span class="sxs-lookup"><span data-stu-id="e8a40-107">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="e8a40-108">окне Указатель на объект, содержащий сведения о `event` .</span><span class="sxs-lookup"><span data-stu-id="e8a40-108">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8a40-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e8a40-109">Return Value</span></span>  
  
|<span data-ttu-id="e8a40-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8a40-110">HRESULT</span></span>|<span data-ttu-id="e8a40-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="e8a40-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8a40-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8a40-112">S_OK</span></span>|<span data-ttu-id="e8a40-113">`OnEvent` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="e8a40-113">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="e8a40-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8a40-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8a40-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="e8a40-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8a40-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8a40-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8a40-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="e8a40-117">The call timed out.</span></span>|  
|<span data-ttu-id="e8a40-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8a40-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8a40-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="e8a40-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8a40-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8a40-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8a40-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="e8a40-121">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8a40-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8a40-122">E_FAIL</span></span>|<span data-ttu-id="e8a40-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="e8a40-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8a40-124">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="e8a40-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8a40-125">Последующие вызовы метода размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e8a40-125">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8a40-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="e8a40-126">Remarks</span></span>  

 <span data-ttu-id="e8a40-127">`data`Параметр является указателем на объект неопределенного типа.</span><span class="sxs-lookup"><span data-stu-id="e8a40-127">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="e8a40-128">Если `event` параметр имеет значение `Event_DomainUnload` , то `data` является числовым идентификатором для <xref:System.AppDomain> выгрузки.</span><span class="sxs-lookup"><span data-stu-id="e8a40-128">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="e8a40-129">Узел может предпринять соответствующие действия, используя этот идентификатор в качестве ключа.</span><span class="sxs-lookup"><span data-stu-id="e8a40-129">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="e8a40-130">Если `event` имеет значение `Event_MDAFired` , `data` то является указателем на экземпляр [мдаинфо](mdainfo-structure.md) , который содержит выходные данные сообщения от помощника по отладке управляемого кода (MDA).</span><span class="sxs-lookup"><span data-stu-id="e8a40-130">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="e8a40-131">MDA — это функция среды CLR, которая помогает разработчикам выполнять отладку путем создания сообщений XML о событиях, которые в противном случае сложны для перехвата.</span><span class="sxs-lookup"><span data-stu-id="e8a40-131">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="e8a40-132">Такие сообщения могут быть особенно полезны при отладке переходов между управляемым и неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="e8a40-132">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="e8a40-133">Дополнительные сведения см. в разделе [Диагностика ошибок с помощью помощников по отладке управляемого](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)кода.</span><span class="sxs-lookup"><span data-stu-id="e8a40-133">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8a40-134">Требования</span><span class="sxs-lookup"><span data-stu-id="e8a40-134">Requirements</span></span>  

 <span data-ttu-id="e8a40-135">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8a40-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8a40-136">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e8a40-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8a40-137">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8a40-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8a40-138">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8a40-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a40-139">См. также</span><span class="sxs-lookup"><span data-stu-id="e8a40-139">See also</span></span>

- [<span data-ttu-id="e8a40-140">Диагностика ошибок посредством управляемых помощников по отладке</span><span class="sxs-lookup"><span data-stu-id="e8a40-140">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e8a40-141">Перечисление EClrEvent</span><span class="sxs-lookup"><span data-stu-id="e8a40-141">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="e8a40-142">Интерфейс IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="e8a40-142">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="e8a40-143">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="e8a40-143">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="e8a40-144">Интерфейс ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="e8a40-144">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="e8a40-145">Структура MDAInfo</span><span class="sxs-lookup"><span data-stu-id="e8a40-145">MDAInfo Structure</span></span>](mdainfo-structure.md)
