---
description: 'Дополнительные сведения о методе: IHostSecurityManager:: Сетсреадтокен'
title: Метод IHostSecurityManager::SetThreadToken
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
ms.openlocfilehash: 96fb8d487cecc0e62d9b7787c686c74898d99d70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671403"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="ca5dd-103">Метод IHostSecurityManager::SetThreadToken</span><span class="sxs-lookup"><span data-stu-id="ca5dd-103">IHostSecurityManager::SetThreadToken Method</span></span>

<span data-ttu-id="ca5dd-104">Задает обработчик для текущего выполняющегося потока.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-104">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca5dd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ca5dd-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca5dd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ca5dd-106">Parameters</span></span>  

 `hToken`  
 <span data-ttu-id="ca5dd-107">окне Маркер, который задается для выполняемого в данный момент потока.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-107">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca5dd-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ca5dd-108">Return Value</span></span>  
  
|<span data-ttu-id="ca5dd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca5dd-109">HRESULT</span></span>|<span data-ttu-id="ca5dd-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="ca5dd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca5dd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca5dd-111">S_OK</span></span>|<span data-ttu-id="ca5dd-112">`SetThreadToken` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-112">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="ca5dd-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca5dd-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca5dd-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ca5dd-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca5dd-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca5dd-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-116">The call timed out.</span></span>|  
|<span data-ttu-id="ca5dd-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca5dd-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca5dd-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca5dd-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca5dd-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca5dd-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca5dd-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca5dd-121">E_FAIL</span></span>|<span data-ttu-id="ca5dd-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca5dd-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca5dd-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca5dd-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="ca5dd-125">Remarks</span></span>  

 <span data-ttu-id="ca5dd-126">`IHostSecurityManager::SetThreadToken` ведет себя аналогично соответствующей функции Win32 с тем же именем, за исключением того, что функция Win32 позволяет вызывающему объекту передать маркер произвольному потоку, в то время как он `IHostSecurityManager::SetThreadToken` может связать маркер только с текущим выполняющимся потоком.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-126">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="ca5dd-127">`HANDLE`Тип не совместим с COM, то есть его размер зависит от операционной системы и требует настраиваемого маршалирования.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-127">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="ca5dd-128">Таким же маркер предназначен только для использования внутри процесса между средой CLR и узлом.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-128">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca5dd-129">Требования</span><span class="sxs-lookup"><span data-stu-id="ca5dd-129">Requirements</span></span>  

 <span data-ttu-id="ca5dd-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca5dd-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca5dd-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ca5dd-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca5dd-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca5dd-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca5dd-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca5dd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca5dd-134">См. также</span><span class="sxs-lookup"><span data-stu-id="ca5dd-134">See also</span></span>

- [<span data-ttu-id="ca5dd-135">Интерфейс IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="ca5dd-135">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="ca5dd-136">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="ca5dd-136">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
