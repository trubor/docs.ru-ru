---
description: 'Дополнительные сведения о методе: ICLRDebugManager:: IsDebuggerAttached'
title: Метод ICLRDebugManager::IsDebuggerAttached
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
ms.openlocfilehash: 74305989797bcb553feb727a133e24bd308ac715
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772137"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="13fa5-103">Метод ICLRDebugManager::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="13fa5-103">ICLRDebugManager::IsDebuggerAttached Method</span></span>

<span data-ttu-id="13fa5-104">Получает значение, показывающее, присоединен ли отладчик к процессу.</span><span class="sxs-lookup"><span data-stu-id="13fa5-104">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13fa5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="13fa5-105">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13fa5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="13fa5-106">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="13fa5-107">[out] `true` значение, если отладчик присоединен к процессу; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="13fa5-107">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13fa5-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="13fa5-108">Return Value</span></span>  
  
|<span data-ttu-id="13fa5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13fa5-109">HRESULT</span></span>|<span data-ttu-id="13fa5-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="13fa5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13fa5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="13fa5-111">S_OK</span></span>|<span data-ttu-id="13fa5-112">`IsDebuggerAttached` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="13fa5-112">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="13fa5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13fa5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13fa5-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="13fa5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="13fa5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13fa5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13fa5-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="13fa5-116">The call timed out.</span></span>|  
|<span data-ttu-id="13fa5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13fa5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13fa5-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="13fa5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13fa5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13fa5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13fa5-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="13fa5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13fa5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13fa5-121">E_FAIL</span></span>|<span data-ttu-id="13fa5-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="13fa5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="13fa5-123">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="13fa5-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13fa5-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="13fa5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13fa5-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="13fa5-125">Remarks</span></span>  

 <span data-ttu-id="13fa5-126">`IsDebuggerAttached` позволяет основному приложению запрашивать среду CLR, чтобы определить, присоединен ли отладчик к процессу.</span><span class="sxs-lookup"><span data-stu-id="13fa5-126">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13fa5-127">Требования</span><span class="sxs-lookup"><span data-stu-id="13fa5-127">Requirements</span></span>  

 <span data-ttu-id="13fa5-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13fa5-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13fa5-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="13fa5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13fa5-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13fa5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13fa5-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13fa5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13fa5-132">См. также</span><span class="sxs-lookup"><span data-stu-id="13fa5-132">See also</span></span>

- [<span data-ttu-id="13fa5-133">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="13fa5-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="13fa5-134">Интерфейс ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="13fa5-134">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="13fa5-135">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="13fa5-135">IHostControl Interface</span></span>](ihostcontrol-interface.md)
