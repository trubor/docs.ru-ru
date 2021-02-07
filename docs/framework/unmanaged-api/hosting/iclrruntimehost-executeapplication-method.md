---
description: 'Дополнительные сведения о методе: ICLRRuntimeHost:: ExecuteApplication'
title: Метод ICLRRuntimeHost::ExecuteApplication
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
ms.openlocfilehash: 1511cc3dcf05c3f2243f4080143789e456c39167
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688979"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="579de-103">Метод ICLRRuntimeHost::ExecuteApplication</span><span class="sxs-lookup"><span data-stu-id="579de-103">ICLRRuntimeHost::ExecuteApplication Method</span></span>

<span data-ttu-id="579de-104">Используется в сценариях развертывания ClickOnce на основе манифеста для указания приложения, которое должно быть активировано в новом домене.</span><span class="sxs-lookup"><span data-stu-id="579de-104">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="579de-105">Дополнительные сведения об этих сценариях см. в разделе [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="579de-105">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="579de-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="579de-106">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="579de-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="579de-107">Parameters</span></span>  

 `pwzAppFullName`  
 <span data-ttu-id="579de-108">окне Полное имя приложения, определенное для <xref:System.ApplicationIdentity> .</span><span class="sxs-lookup"><span data-stu-id="579de-108">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="579de-109">окне Число строк, содержащихся в `ppwzManifestPaths` массиве.</span><span class="sxs-lookup"><span data-stu-id="579de-109">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="579de-110">[в] Необязательно.</span><span class="sxs-lookup"><span data-stu-id="579de-110">[in] Optional.</span></span> <span data-ttu-id="579de-111">Массив строк, содержащий пути манифеста для приложения.</span><span class="sxs-lookup"><span data-stu-id="579de-111">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="579de-112">окне Число строк, содержащихся в `ppwzActivationData` массиве.</span><span class="sxs-lookup"><span data-stu-id="579de-112">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="579de-113">[в] Необязательно.</span><span class="sxs-lookup"><span data-stu-id="579de-113">[in] Optional.</span></span> <span data-ttu-id="579de-114">Массив строк, содержащий данные активации приложения, такие как часть строки запроса URL-адреса для приложений, развернутых через Интернет.</span><span class="sxs-lookup"><span data-stu-id="579de-114">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="579de-115">заполняет Значение, возвращаемое из точки входа приложения.</span><span class="sxs-lookup"><span data-stu-id="579de-115">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="579de-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="579de-116">Return Value</span></span>  
  
|<span data-ttu-id="579de-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="579de-117">HRESULT</span></span>|<span data-ttu-id="579de-118">Описание:</span><span class="sxs-lookup"><span data-stu-id="579de-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="579de-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="579de-119">S_OK</span></span>|<span data-ttu-id="579de-120">`ExecuteApplication` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="579de-120">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="579de-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="579de-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="579de-122">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="579de-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="579de-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="579de-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="579de-124">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="579de-124">The call timed out.</span></span>|  
|<span data-ttu-id="579de-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="579de-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="579de-126">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="579de-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="579de-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="579de-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="579de-128">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="579de-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="579de-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="579de-129">E_FAIL</span></span>|<span data-ttu-id="579de-130">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="579de-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="579de-131">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="579de-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="579de-132">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="579de-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="579de-133">Remarks</span><span class="sxs-lookup"><span data-stu-id="579de-133">Remarks</span></span>  

 <span data-ttu-id="579de-134">`ExecuteApplication` используется для активации приложений ClickOnce в только что созданном домене приложения.</span><span class="sxs-lookup"><span data-stu-id="579de-134">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="579de-135">`pReturnValue`Параметру OUTPUT задается значение, возвращаемое приложением.</span><span class="sxs-lookup"><span data-stu-id="579de-135">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="579de-136">Если для задано значение null, то `pReturnValue` не `ExecuteApplication` завершается ошибкой, но не возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="579de-136">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="579de-137">Не вызывайте метод [метода Start](iclrruntimehost-start-method.md) перед вызовом `ExecuteApplication` метода для активации приложения на основе манифеста.</span><span class="sxs-lookup"><span data-stu-id="579de-137">Do not call the [Start Method](iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="579de-138">Если `Start` метод вызывается первым, `ExecuteApplication` вызов метода завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="579de-138">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="579de-139">Требования</span><span class="sxs-lookup"><span data-stu-id="579de-139">Requirements</span></span>  

 <span data-ttu-id="579de-140">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="579de-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="579de-141">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="579de-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="579de-142">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="579de-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="579de-143">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="579de-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="579de-144">См. также</span><span class="sxs-lookup"><span data-stu-id="579de-144">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="579de-145">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="579de-145">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="579de-146">Метод SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="579de-146">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="579de-147">Пошаговое руководство. Загрузка сборок по запросу с помощью API развертывания ClickOnce в конструкторе</span><span class="sxs-lookup"><span data-stu-id="579de-147">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
