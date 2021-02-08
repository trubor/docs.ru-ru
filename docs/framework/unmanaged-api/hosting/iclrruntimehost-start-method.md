---
description: 'Дополнительные сведения о методе: ICLRRuntimeHost:: Start'
title: Метод ICLRRuntimeHost::Start
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type:
- apiref
ms.openlocfilehash: 0ada729c9a90b23fb1573a2101845028e5e2fe76
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785085"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="b7053-103">Метод ICLRRuntimeHost::Start</span><span class="sxs-lookup"><span data-stu-id="b7053-103">ICLRRuntimeHost::Start Method</span></span>

<span data-ttu-id="b7053-104">Инициализирует среду CLR в процессе.</span><span class="sxs-lookup"><span data-stu-id="b7053-104">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7053-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b7053-105">Syntax</span></span>  
  
```cpp  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b7053-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b7053-106">Return Value</span></span>  
  
|<span data-ttu-id="b7053-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7053-107">HRESULT</span></span>|<span data-ttu-id="b7053-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="b7053-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7053-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7053-109">S_OK</span></span>|<span data-ttu-id="b7053-110">`Start` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="b7053-110">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="b7053-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b7053-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b7053-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="b7053-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b7053-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b7053-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b7053-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="b7053-114">The call timed out.</span></span>|  
|<span data-ttu-id="b7053-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7053-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b7053-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="b7053-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b7053-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b7053-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b7053-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="b7053-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b7053-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b7053-119">E_FAIL</span></span>|<span data-ttu-id="b7053-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="b7053-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b7053-121">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="b7053-121">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b7053-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b7053-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7053-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="b7053-123">Remarks</span></span>  

 <span data-ttu-id="b7053-124">Во многих случаях нет необходимости вызывать `Start` , так как среда выполнения инициализирует себя автоматически при первом запросе на выполнение управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="b7053-124">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="b7053-125">Однако можно использовать, `Start` чтобы точно указать, когда должна быть инициализирована среда выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7053-125">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7053-126">Требования</span><span class="sxs-lookup"><span data-stu-id="b7053-126">Requirements</span></span>  

 <span data-ttu-id="b7053-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7053-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7053-128">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b7053-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7053-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7053-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7053-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7053-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7053-131">См. также</span><span class="sxs-lookup"><span data-stu-id="b7053-131">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="b7053-132">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="b7053-132">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
