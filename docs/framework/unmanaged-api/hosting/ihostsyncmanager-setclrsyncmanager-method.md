---
description: 'Дополнительные сведения о методе: метод ihostsyncmanager:: Сетклрсинкманажер'
title: Метод IHostSyncManager::SetCLRSyncManager
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
ms.openlocfilehash: e2a6a54334f7b8a63696ead918f4f34e0c36e438
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784721"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="20950-103">Метод IHostSyncManager::SetCLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="20950-103">IHostSyncManager::SetCLRSyncManager Method</span></span>

<span data-ttu-id="20950-104">Задает экземпляр [ICLRSyncManager](iclrsyncmanager-interface.md) , связываемый с текущим экземпляром [метод ihostsyncmanager](ihostsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="20950-104">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20950-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="20950-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20950-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="20950-106">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="20950-107">окне Указатель на `ICLRSyncManager` экземпляр, предоставленный средой CLR.</span><span class="sxs-lookup"><span data-stu-id="20950-107">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20950-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="20950-108">Return Value</span></span>  
  
|<span data-ttu-id="20950-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20950-109">HRESULT</span></span>|<span data-ttu-id="20950-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="20950-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20950-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="20950-111">S_OK</span></span>|<span data-ttu-id="20950-112">`SetCLRSyncManager` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="20950-112">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="20950-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="20950-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="20950-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="20950-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="20950-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="20950-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="20950-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="20950-116">The call timed out.</span></span>|  
|<span data-ttu-id="20950-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="20950-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="20950-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="20950-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="20950-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="20950-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="20950-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="20950-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="20950-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20950-121">E_FAIL</span></span>|<span data-ttu-id="20950-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="20950-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="20950-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="20950-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="20950-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="20950-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20950-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="20950-125">Remarks</span></span>  

 <span data-ttu-id="20950-126">Для упрощения обмена данными между узлом и средой CLR интерфейсы размещения обычно бывают парными.</span><span class="sxs-lookup"><span data-stu-id="20950-126">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="20950-127">Один член пары реализуется узлом, а другой — средой CLR.</span><span class="sxs-lookup"><span data-stu-id="20950-127">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="20950-128">В качестве реализации на стороне узла `IHostSyncManager` интерфейс соответствует `ICLRSyncManager` интерфейсу, РЕАЛИЗОВАНному средой CLR.</span><span class="sxs-lookup"><span data-stu-id="20950-128">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="20950-129">Среда CLR вызывает метод, `SetCLRSyncManager` чтобы предоставить `ICLRSyncManager` узлу экземпляр, связываемый с текущим `IHostSyncManager` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="20950-129">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20950-130">Требования</span><span class="sxs-lookup"><span data-stu-id="20950-130">Requirements</span></span>  

 <span data-ttu-id="20950-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20950-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20950-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="20950-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20950-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20950-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20950-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20950-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20950-135">См. также</span><span class="sxs-lookup"><span data-stu-id="20950-135">See also</span></span>

- [<span data-ttu-id="20950-136">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="20950-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="20950-137">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="20950-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
