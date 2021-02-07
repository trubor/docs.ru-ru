---
description: 'Дополнительные сведения о методе: IHostSecurityContext:: Capture'
title: Метод IHostSecurityContext::Capture
ms.date: 03/30/2017
api_name:
- IHostSecurityContext.Capture
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type:
- apiref
ms.openlocfilehash: d46bbae7b94dcad6d1356243c938c9d3690f26a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671715"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="dcfce-103">Метод IHostSecurityContext::Capture</span><span class="sxs-lookup"><span data-stu-id="dcfce-103">IHostSecurityContext::Capture Method</span></span>

<span data-ttu-id="dcfce-104">Возвращает клон экземпляра [IHostSecurityContext](ihostsecuritycontext-interface.md) , возвращенный из вызова [IHostSecurityManager:: getsecuritycontext-](ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="dcfce-104">Gets a clone of the [IHostSecurityContext](ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcfce-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dcfce-105">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcfce-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcfce-106">Parameters</span></span>  

 `ppClonedContext`  
 <span data-ttu-id="dcfce-107">заполняет Указатель на адрес клона `IHostSecurityContext` объекта, который необходимо записать.</span><span class="sxs-lookup"><span data-stu-id="dcfce-107">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcfce-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcfce-108">Return Value</span></span>  
  
|<span data-ttu-id="dcfce-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dcfce-109">HRESULT</span></span>|<span data-ttu-id="dcfce-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="dcfce-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dcfce-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dcfce-111">S_OK</span></span>|<span data-ttu-id="dcfce-112">`Capture` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="dcfce-112">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="dcfce-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dcfce-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dcfce-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="dcfce-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dcfce-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dcfce-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dcfce-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="dcfce-116">The call timed out.</span></span>|  
|<span data-ttu-id="dcfce-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dcfce-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dcfce-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="dcfce-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dcfce-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dcfce-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dcfce-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="dcfce-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dcfce-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dcfce-121">E_FAIL</span></span>|<span data-ttu-id="dcfce-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="dcfce-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dcfce-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="dcfce-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dcfce-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dcfce-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcfce-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="dcfce-125">Remarks</span></span>  

 <span data-ttu-id="dcfce-126">Указатель интерфейса, возвращенный из `Capture` , является клоном захваченного контекста.</span><span class="sxs-lookup"><span data-stu-id="dcfce-126">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="dcfce-127">Когда эта информация перемещается по асинхронной кодовой точке, ее время существования отделяется от указателя, на который был сделан вызов.</span><span class="sxs-lookup"><span data-stu-id="dcfce-127">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="dcfce-128">Таким образом, исходный указатель может быть освобожден.</span><span class="sxs-lookup"><span data-stu-id="dcfce-128">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcfce-129">Требования</span><span class="sxs-lookup"><span data-stu-id="dcfce-129">Requirements</span></span>  

 <span data-ttu-id="dcfce-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcfce-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcfce-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dcfce-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dcfce-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dcfce-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcfce-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcfce-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcfce-134">См. также</span><span class="sxs-lookup"><span data-stu-id="dcfce-134">See also</span></span>

- [<span data-ttu-id="dcfce-135">Интерфейс IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="dcfce-135">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="dcfce-136">Интерфейс IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="dcfce-136">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
