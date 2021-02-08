---
description: 'Дополнительные сведения о методе: ICLRRuntimeHost:: SetHostControl'
title: Метод ICLRRuntimeHost::SetHostControl
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
ms.openlocfilehash: e51c61666716badc7214f9a74ad11aa646f2316c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785114"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="e6a6b-103">Метод ICLRRuntimeHost::SetHostControl</span><span class="sxs-lookup"><span data-stu-id="e6a6b-103">ICLRRuntimeHost::SetHostControl Method</span></span>

<span data-ttu-id="e6a6b-104">Задает указатель интерфейса, который среда CLR может использовать для получения реализации [интерфейса IHostControl](ihostcontrol-interface.md)в узле.</span><span class="sxs-lookup"><span data-stu-id="e6a6b-104">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6a6b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e6a6b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6a6b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e6a6b-106">Parameters</span></span>  

 `pHostControl`  
 <span data-ttu-id="e6a6b-107">окне Указатель интерфейса на реализацию [интерфейса IHostControl](ihostcontrol-interface.md)узла.</span><span class="sxs-lookup"><span data-stu-id="e6a6b-107">[in] An interface pointer to the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6a6b-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e6a6b-108">Return Value</span></span>  
  
|<span data-ttu-id="e6a6b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6a6b-109">HRESULT</span></span>|<span data-ttu-id="e6a6b-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="e6a6b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6a6b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6a6b-111">S_OK</span></span>|<span data-ttu-id="e6a6b-112">`SetHostControl` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="e6a6b-112">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="e6a6b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e6a6b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e6a6b-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="e6a6b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e6a6b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e6a6b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e6a6b-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="e6a6b-116">The call timed out.</span></span>|  
|<span data-ttu-id="e6a6b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6a6b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e6a6b-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="e6a6b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e6a6b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e6a6b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e6a6b-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="e6a6b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e6a6b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e6a6b-121">E_FAIL</span></span>|<span data-ttu-id="e6a6b-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="e6a6b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e6a6b-123">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="e6a6b-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e6a6b-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e6a6b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e6a6b-125">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="e6a6b-125">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="e6a6b-126">Среда CLR уже инициализирована.</span><span class="sxs-lookup"><span data-stu-id="e6a6b-126">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6a6b-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="e6a6b-127">Remarks</span></span>  

 <span data-ttu-id="e6a6b-128">Необходимо вызвать `SetHostControl` перед инициализацией среды CLR, то есть до вызова [метода Start](iclrruntimehost-start-method.md) или использования любого [интерфейса метаданных](../metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="e6a6b-128">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="e6a6b-129">Рекомендуется вызывать `SetHostControl` немедленно после вызова [функции Корбиндтокуррентрунтиме](corbindtocurrentruntime-function.md) или [функции CorBindToRuntimeEx](corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="e6a6b-129">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6a6b-130">Требования</span><span class="sxs-lookup"><span data-stu-id="e6a6b-130">Requirements</span></span>  

 <span data-ttu-id="e6a6b-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6a6b-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6a6b-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e6a6b-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6a6b-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e6a6b-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6a6b-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6a6b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6a6b-135">См. также</span><span class="sxs-lookup"><span data-stu-id="e6a6b-135">See also</span></span>

- [<span data-ttu-id="e6a6b-136">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e6a6b-136">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="e6a6b-137">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="e6a6b-137">IHostControl Interface</span></span>](ihostcontrol-interface.md)
