---
description: 'Дополнительные сведения о методе: IHostIoCompletionManager:: Сетклриокомплетионманажер'
title: Метод IHostIoCompletionManager::SetCLRIoCompletionManager
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
ms.openlocfilehash: 1075c33d6de4f5edf34364d67cbc0a21c4f19802
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708298"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="890e1-103">Метод IHostIoCompletionManager::SetCLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="890e1-103">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>

<span data-ttu-id="890e1-104">Предоставляет узлу указатель интерфейса на экземпляр [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) , реализованный средой CLR.</span><span class="sxs-lookup"><span data-stu-id="890e1-104">Provides the host with an interface pointer to the [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="890e1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="890e1-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="890e1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="890e1-106">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="890e1-107">окне Указатель интерфейса на экземпляр, `ICLRIoCompletionManager` предоставляемый средой CLR.</span><span class="sxs-lookup"><span data-stu-id="890e1-107">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="890e1-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="890e1-108">Return Value</span></span>  
  
|<span data-ttu-id="890e1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="890e1-109">HRESULT</span></span>|<span data-ttu-id="890e1-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="890e1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="890e1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="890e1-111">S_OK</span></span>|<span data-ttu-id="890e1-112">`SetCLRIoCompletionManager` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="890e1-112">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="890e1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="890e1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="890e1-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="890e1-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="890e1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="890e1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="890e1-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="890e1-116">The call timed out.</span></span>|  
|<span data-ttu-id="890e1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="890e1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="890e1-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="890e1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="890e1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="890e1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="890e1-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="890e1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="890e1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="890e1-121">E_FAIL</span></span>|<span data-ttu-id="890e1-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="890e1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="890e1-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="890e1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="890e1-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="890e1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="890e1-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="890e1-125">Remarks</span></span>  

 <span data-ttu-id="890e1-126">После вызова CLR `SetCLRIoCompletionManager` узел должен вызвать [ICLRIoCompletionManager:: OnComplete](iclriocompletionmanager-oncomplete-method.md) , чтобы уведомить CLR о завершении запроса ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="890e1-126">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="890e1-127">Требования</span><span class="sxs-lookup"><span data-stu-id="890e1-127">Requirements</span></span>  

 <span data-ttu-id="890e1-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="890e1-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="890e1-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="890e1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="890e1-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="890e1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="890e1-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="890e1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="890e1-132">См. также</span><span class="sxs-lookup"><span data-stu-id="890e1-132">See also</span></span>

- [<span data-ttu-id="890e1-133">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="890e1-133">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="890e1-134">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="890e1-134">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
