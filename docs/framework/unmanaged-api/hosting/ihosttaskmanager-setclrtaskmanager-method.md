---
description: 'Дополнительные сведения о методе: IHostTaskManager:: SetCLRTaskManager'
title: Метод IHostTaskManager::SetCLRTaskManager
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
ms.openlocfilehash: 438a5b56afd42eceafb484bdf0020efbad86d052
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680880"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="065ad-103">Метод IHostTaskManager::SetCLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="065ad-103">IHostTaskManager::SetCLRTaskManager Method</span></span>

<span data-ttu-id="065ad-104">Предоставляет узлу указатель интерфейса на экземпляр [ICLRTaskManager](iclrtaskmanager-interface.md) , реализованный средой CLR.</span><span class="sxs-lookup"><span data-stu-id="065ad-104">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="065ad-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="065ad-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="065ad-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="065ad-106">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="065ad-107">окне Указатель на `ICLRTaskManager` экземпляр, реализованный средой CLR.</span><span class="sxs-lookup"><span data-stu-id="065ad-107">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="065ad-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="065ad-108">Return Value</span></span>  
  
|<span data-ttu-id="065ad-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="065ad-109">HRESULT</span></span>|<span data-ttu-id="065ad-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="065ad-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="065ad-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="065ad-111">S_OK</span></span>|<span data-ttu-id="065ad-112">`SetCLRTaskManager` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="065ad-112">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="065ad-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="065ad-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="065ad-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="065ad-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="065ad-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="065ad-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="065ad-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="065ad-116">The call timed out.</span></span>|  
|<span data-ttu-id="065ad-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="065ad-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="065ad-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="065ad-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="065ad-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="065ad-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="065ad-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="065ad-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="065ad-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="065ad-121">E_FAIL</span></span>|<span data-ttu-id="065ad-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="065ad-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="065ad-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="065ad-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="065ad-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="065ad-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="065ad-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="065ad-125">Remarks</span></span>  

 <span data-ttu-id="065ad-126">Среда выполнения вызывает метод `SetCLRTaskManager` , чтобы предоставить узлу указатель интерфейса на `ICLRTaskManager` экземпляр.</span><span class="sxs-lookup"><span data-stu-id="065ad-126">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="065ad-127">Требования</span><span class="sxs-lookup"><span data-stu-id="065ad-127">Requirements</span></span>  

 <span data-ttu-id="065ad-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="065ad-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="065ad-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="065ad-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="065ad-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="065ad-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="065ad-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="065ad-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="065ad-132">См. также</span><span class="sxs-lookup"><span data-stu-id="065ad-132">See also</span></span>

- [<span data-ttu-id="065ad-133">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="065ad-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="065ad-134">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="065ad-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="065ad-135">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="065ad-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="065ad-136">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="065ad-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
