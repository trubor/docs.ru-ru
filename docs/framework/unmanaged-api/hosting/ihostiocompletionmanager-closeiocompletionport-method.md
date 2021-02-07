---
description: 'Дополнительные сведения о методе: IHostIoCompletionManager:: CloseIoCompletionPort'
title: Метод IHostIoCompletionManager::CloseIoCompletionPort
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
ms.openlocfilehash: 987b9f4e0fa22fa977fa1b14c77c8c0381e3e399
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728513"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="9951a-103">Метод IHostIoCompletionManager::CloseIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="9951a-103">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>

<span data-ttu-id="9951a-104">Запрашивает, что узел закрывает порт, Открытый с помощью предыдущего вызова [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="9951a-104">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9951a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9951a-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9951a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9951a-106">Parameters</span></span>  

 `hPort`  
 <span data-ttu-id="9951a-107">окне Маркер порта, который необходимо закрыть.</span><span class="sxs-lookup"><span data-stu-id="9951a-107">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9951a-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9951a-108">Return Value</span></span>  
  
|<span data-ttu-id="9951a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9951a-109">HRESULT</span></span>|<span data-ttu-id="9951a-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="9951a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9951a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9951a-111">S_OK</span></span>|<span data-ttu-id="9951a-112">`CloseIoCompletionPort` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="9951a-112">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="9951a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9951a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9951a-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="9951a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9951a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9951a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9951a-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="9951a-116">The call timed out.</span></span>|  
|<span data-ttu-id="9951a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9951a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9951a-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="9951a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9951a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9951a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9951a-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="9951a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9951a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9951a-121">E_FAIL</span></span>|<span data-ttu-id="9951a-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="9951a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9951a-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="9951a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9951a-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9951a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9951a-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9951a-125">E_INVALIDARG</span></span>|<span data-ttu-id="9951a-126">Передан недопустимый маркер порта.</span><span class="sxs-lookup"><span data-stu-id="9951a-126">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9951a-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="9951a-127">Remarks</span></span>  

 <span data-ttu-id="9951a-128">`hPort` должен быть маркером для порта, созданного предыдущим вызовом метода `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="9951a-128">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9951a-129">Требования</span><span class="sxs-lookup"><span data-stu-id="9951a-129">Requirements</span></span>  

 <span data-ttu-id="9951a-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9951a-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9951a-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9951a-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9951a-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9951a-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9951a-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9951a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9951a-134">См. также</span><span class="sxs-lookup"><span data-stu-id="9951a-134">See also</span></span>

- [<span data-ttu-id="9951a-135">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="9951a-135">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="9951a-136">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="9951a-136">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
