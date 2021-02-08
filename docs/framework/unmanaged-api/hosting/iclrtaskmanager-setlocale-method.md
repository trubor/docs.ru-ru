---
description: 'Дополнительные сведения о методе: ICLRTaskManager:: SetLocale'
title: Метод ICLRTaskManager::SetLocale
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
ms.openlocfilehash: 401f227f900ab4b89cd6fc5b7902b4314a7687e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799483"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="db4c2-103">Метод ICLRTaskManager::SetLocale</span><span class="sxs-lookup"><span data-stu-id="db4c2-103">ICLRTaskManager::SetLocale Method</span></span>

<span data-ttu-id="db4c2-104">Уведомляет среду CLR о том, что узел изменил значение идентификатора локали (который сопоставляется с географическим языком и региональными параметрами) в текущей выполняемой задаче.</span><span class="sxs-lookup"><span data-stu-id="db4c2-104">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db4c2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="db4c2-105">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db4c2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="db4c2-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="db4c2-107">окне Значение идентификатора локали, сопоставляемое с новым назначенным географическим языком и региональными параметрами.</span><span class="sxs-lookup"><span data-stu-id="db4c2-107">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db4c2-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="db4c2-108">Return Value</span></span>  
  
|<span data-ttu-id="db4c2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db4c2-109">HRESULT</span></span>|<span data-ttu-id="db4c2-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="db4c2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db4c2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="db4c2-111">S_OK</span></span>|<span data-ttu-id="db4c2-112">Метод возвратился успешно.</span><span class="sxs-lookup"><span data-stu-id="db4c2-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="db4c2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db4c2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db4c2-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="db4c2-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db4c2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db4c2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db4c2-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="db4c2-116">The call timed out.</span></span>|  
|<span data-ttu-id="db4c2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db4c2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db4c2-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="db4c2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db4c2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db4c2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db4c2-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="db4c2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db4c2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db4c2-121">E_FAIL</span></span>|<span data-ttu-id="db4c2-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="db4c2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db4c2-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="db4c2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db4c2-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="db4c2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db4c2-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="db4c2-125">Remarks</span></span>  

 <span data-ttu-id="db4c2-126">`SetLocale` Предоставляет узлу возможность выполнения любых механизмов, которые могут потребоваться для синхронизации языковых стандартов.</span><span class="sxs-lookup"><span data-stu-id="db4c2-126">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db4c2-127">Требования</span><span class="sxs-lookup"><span data-stu-id="db4c2-127">Requirements</span></span>  

 <span data-ttu-id="db4c2-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db4c2-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db4c2-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="db4c2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db4c2-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db4c2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db4c2-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db4c2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db4c2-132">См. также</span><span class="sxs-lookup"><span data-stu-id="db4c2-132">See also</span></span>

- [<span data-ttu-id="db4c2-133">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="db4c2-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="db4c2-134">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="db4c2-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="db4c2-135">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="db4c2-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="db4c2-136">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="db4c2-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
