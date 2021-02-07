---
description: 'Дополнительные сведения о методе: ICLRPolicyManager:: SetUnhandledExceptionPolicy'
title: Метод ICLRPolicyManager::SetUnhandledExceptionPolicy
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
ms.openlocfilehash: 489127bb00b2b65466460baa3cfd31439672cd1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716553"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="5c083-103">Метод ICLRPolicyManager::SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="5c083-103">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>

<span data-ttu-id="5c083-104">Задает поведение среды CLR при возникновении необработанного исключения.</span><span class="sxs-lookup"><span data-stu-id="5c083-104">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c083-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5c083-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c083-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5c083-106">Parameters</span></span>  

 `policy`  
 <span data-ttu-id="5c083-107">окне Одно из значений [еклрунхандледексцептион](eclrunhandledexception-enumeration.md) , указывающее, задано ли поведение средой CLR или узлом.</span><span class="sxs-lookup"><span data-stu-id="5c083-107">[in] One of the [EClrUnhandledException](eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c083-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5c083-108">Return Value</span></span>  
  
|<span data-ttu-id="5c083-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c083-109">HRESULT</span></span>|<span data-ttu-id="5c083-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="5c083-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c083-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c083-111">S_OK</span></span>|<span data-ttu-id="5c083-112">`SetUnhandledExceptionPolicy` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="5c083-112">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="5c083-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c083-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c083-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="5c083-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c083-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c083-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c083-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="5c083-116">The call timed out.</span></span>|  
|<span data-ttu-id="5c083-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c083-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c083-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="5c083-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c083-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c083-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c083-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="5c083-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c083-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c083-121">E_FAIL</span></span>|<span data-ttu-id="5c083-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="5c083-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c083-123">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="5c083-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c083-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5c083-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c083-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="5c083-125">Remarks</span></span>  

 <span data-ttu-id="5c083-126">По умолчанию CLR является окончательным обработчиком для всех необработанных исключений, и его поведение по умолчанию заключается в том, чтобы разорвать этот процесс.</span><span class="sxs-lookup"><span data-stu-id="5c083-126">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="5c083-127">Узел может изменить это поведение, задав `policy` значение ехостдетерминедполици.</span><span class="sxs-lookup"><span data-stu-id="5c083-127">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="5c083-128">Это значение позволяет ведущему приложению реализовать собственное поведение по умолчанию, как в предыдущих версиях среды CLR.</span><span class="sxs-lookup"><span data-stu-id="5c083-128">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c083-129">Требования</span><span class="sxs-lookup"><span data-stu-id="5c083-129">Requirements</span></span>  

 <span data-ttu-id="5c083-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c083-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c083-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5c083-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c083-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c083-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c083-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c083-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c083-134">См. также</span><span class="sxs-lookup"><span data-stu-id="5c083-134">See also</span></span>

- [<span data-ttu-id="5c083-135">Перечисление EClrUnhandledException</span><span class="sxs-lookup"><span data-stu-id="5c083-135">EClrUnhandledException Enumeration</span></span>](eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="5c083-136">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="5c083-136">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="5c083-137">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="5c083-137">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="5c083-138">Интерфейс IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="5c083-138">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
