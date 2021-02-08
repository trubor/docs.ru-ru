---
description: 'Дополнительные сведения о методе: ICLRRuntimeHost:: останавливаться'
title: Метод ICLRRuntimeHost::Stop
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
ms.openlocfilehash: 3e6b1cf2aee95af6354905f6dcdcb678ff785aa6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799739"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="7fb87-103">Метод ICLRRuntimeHost::Stop</span><span class="sxs-lookup"><span data-stu-id="7fb87-103">ICLRRuntimeHost::Stop Method</span></span>

<span data-ttu-id="7fb87-104">Останавливает выполнение кода средой CLR.</span><span class="sxs-lookup"><span data-stu-id="7fb87-104">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7fb87-105">Этот метод не освобождает ресурсы для узла, выгружает домены приложений или уничтожает потоки.</span><span class="sxs-lookup"><span data-stu-id="7fb87-105">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="7fb87-106">Необходимо завершить процесс, чтобы освободить эти ресурсы.</span><span class="sxs-lookup"><span data-stu-id="7fb87-106">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fb87-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7fb87-107">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7fb87-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7fb87-108">Return Value</span></span>  
  
|<span data-ttu-id="7fb87-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7fb87-109">HRESULT</span></span>|<span data-ttu-id="7fb87-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="7fb87-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fb87-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7fb87-111">S_OK</span></span>|<span data-ttu-id="7fb87-112">`Stop` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="7fb87-112">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="7fb87-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7fb87-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7fb87-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7fb87-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7fb87-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7fb87-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7fb87-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="7fb87-116">The call timed out.</span></span>|  
|<span data-ttu-id="7fb87-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7fb87-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7fb87-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="7fb87-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7fb87-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7fb87-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7fb87-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="7fb87-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7fb87-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7fb87-121">E_FAIL</span></span>|<span data-ttu-id="7fb87-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="7fb87-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7fb87-123">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="7fb87-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7fb87-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7fb87-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7fb87-125">Требования</span><span class="sxs-lookup"><span data-stu-id="7fb87-125">Requirements</span></span>  

 <span data-ttu-id="7fb87-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fb87-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fb87-127">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7fb87-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fb87-128">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7fb87-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fb87-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fb87-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fb87-130">См. также</span><span class="sxs-lookup"><span data-stu-id="7fb87-130">See also</span></span>

- [<span data-ttu-id="7fb87-131">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="7fb87-131">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
