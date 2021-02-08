---
description: 'Дополнительные сведения о методе: ICLRTaskManager:: SetUILocale'
title: Метод ICLRTaskManager::SetUILocale
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
ms.openlocfilehash: f4fcc916c520489bd1e39f6a44bc1bb971df4bba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799464"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="2cb4a-103">Метод ICLRTaskManager::SetUILocale</span><span class="sxs-lookup"><span data-stu-id="2cb4a-103">ICLRTaskManager::SetUILocale Method</span></span>

<span data-ttu-id="2cb4a-104">Уведомляет среду CLR о том, что узел изменил языковой стандарт пользовательского интерфейса (UI) или язык и региональные параметры, в текущей выполняемой задаче.</span><span class="sxs-lookup"><span data-stu-id="2cb4a-104">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb4a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2cb4a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cb4a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2cb4a-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="2cb4a-107">окне Значение идентификатора локали, сопоставленное с вновь назначенным географическим языком и региональными параметрами пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="2cb4a-107">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cb4a-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2cb4a-108">Return Value</span></span>  
  
|<span data-ttu-id="2cb4a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2cb4a-109">HRESULT</span></span>|<span data-ttu-id="2cb4a-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="2cb4a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2cb4a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2cb4a-111">S_OK</span></span>|<span data-ttu-id="2cb4a-112">`SetUILocale` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="2cb4a-112">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="2cb4a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2cb4a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2cb4a-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="2cb4a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2cb4a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2cb4a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2cb4a-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="2cb4a-116">The call timed out.</span></span>|  
|<span data-ttu-id="2cb4a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2cb4a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2cb4a-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="2cb4a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2cb4a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2cb4a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2cb4a-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="2cb4a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2cb4a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2cb4a-121">E_FAIL</span></span>|<span data-ttu-id="2cb4a-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="2cb4a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2cb4a-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="2cb4a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2cb4a-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2cb4a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cb4a-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="2cb4a-125">Remarks</span></span>  

 <span data-ttu-id="2cb4a-126">`SetUILocale` Предоставляет узлу возможность выполнять любые механизмы, необходимые для синхронизации языковых стандартов.</span><span class="sxs-lookup"><span data-stu-id="2cb4a-126">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cb4a-127">Требования</span><span class="sxs-lookup"><span data-stu-id="2cb4a-127">Requirements</span></span>  

 <span data-ttu-id="2cb4a-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cb4a-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cb4a-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2cb4a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cb4a-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2cb4a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cb4a-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cb4a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb4a-132">См. также</span><span class="sxs-lookup"><span data-stu-id="2cb4a-132">See also</span></span>

- [<span data-ttu-id="2cb4a-133">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="2cb4a-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2cb4a-134">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="2cb4a-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2cb4a-135">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="2cb4a-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2cb4a-136">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="2cb4a-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
