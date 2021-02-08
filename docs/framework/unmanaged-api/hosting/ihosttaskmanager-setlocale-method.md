---
description: 'Дополнительные сведения о методе: IHostTaskManager:: SetLocale'
title: Метод IHostTaskManager::SetLocale
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
ms.openlocfilehash: 522a3da9bcd8d61754684091f6de3f11f7ed478c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789415"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="77a15-103">Метод IHostTaskManager::SetLocale</span><span class="sxs-lookup"><span data-stu-id="77a15-103">IHostTaskManager::SetLocale Method</span></span>

<span data-ttu-id="77a15-104">Уведомляет основное приложение о том, что среда CLR изменила языковой стандарт, или культуру, в текущей выполняемой задаче.</span><span class="sxs-lookup"><span data-stu-id="77a15-104">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77a15-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77a15-105">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77a15-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="77a15-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="77a15-107">окне Значение идентификатора локали, сопоставляемое с новым назначенным географическим языком и региональными параметрами.</span><span class="sxs-lookup"><span data-stu-id="77a15-107">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77a15-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="77a15-108">Return Value</span></span>  
  
|<span data-ttu-id="77a15-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77a15-109">HRESULT</span></span>|<span data-ttu-id="77a15-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="77a15-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77a15-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="77a15-111">S_OK</span></span>|<span data-ttu-id="77a15-112">`SetLocale` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="77a15-112">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="77a15-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77a15-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77a15-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="77a15-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77a15-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77a15-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77a15-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="77a15-116">The call timed out.</span></span>|  
|<span data-ttu-id="77a15-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77a15-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77a15-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="77a15-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77a15-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77a15-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77a15-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="77a15-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77a15-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77a15-121">E_FAIL</span></span>|<span data-ttu-id="77a15-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="77a15-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77a15-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="77a15-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77a15-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="77a15-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="77a15-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="77a15-125">E_NOTIMPL</span></span>|<span data-ttu-id="77a15-126">Узел не позволяет управляемому пользовательскому коду изменять языковой стандарт.</span><span class="sxs-lookup"><span data-stu-id="77a15-126">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77a15-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="77a15-127">Remarks</span></span>  

 <span data-ttu-id="77a15-128">Среда выполнения вызывает `SetLocale` , когда значение <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> свойства изменяется управляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="77a15-128">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="77a15-129">Этот метод предоставляет узлу возможность выполнять любые механизмы, которые могут потребоваться для синхронизации языковых стандартов.</span><span class="sxs-lookup"><span data-stu-id="77a15-129">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="77a15-130">Если узел не позволяет изменить языковой стандарт из управляемого кода или не реализует механизм для синхронизации языковых стандартов, он должен возвращать E_NOTIMPL из этого метода.</span><span class="sxs-lookup"><span data-stu-id="77a15-130">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77a15-131">Требования</span><span class="sxs-lookup"><span data-stu-id="77a15-131">Requirements</span></span>  

 <span data-ttu-id="77a15-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77a15-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77a15-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="77a15-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77a15-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77a15-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77a15-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77a15-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a15-136">См. также</span><span class="sxs-lookup"><span data-stu-id="77a15-136">See also</span></span>

- [<span data-ttu-id="77a15-137">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="77a15-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="77a15-138">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="77a15-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="77a15-139">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="77a15-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="77a15-140">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="77a15-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="77a15-141">Метод SetUILocale</span><span class="sxs-lookup"><span data-stu-id="77a15-141">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)
