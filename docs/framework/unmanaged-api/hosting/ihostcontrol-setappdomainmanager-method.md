---
description: 'Дополнительные сведения о методе: IHostControl:: SetAppDomainManager'
title: Метод IHostControl::SetAppDomainManager
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
ms.openlocfilehash: 1fc5efc0afad73d1805338140f186a50913ca542
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708904"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="e5ae9-103">Метод IHostControl::SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="e5ae9-103">IHostControl::SetAppDomainManager Method</span></span>

<span data-ttu-id="e5ae9-104">Уведомляет узел о том, что домен приложения создан.</span><span class="sxs-lookup"><span data-stu-id="e5ae9-104">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5ae9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e5ae9-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5ae9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e5ae9-106">Parameters</span></span>  

 `dwAppDomainID`  
 <span data-ttu-id="e5ae9-107">окне Числовой идентификатор выбранного объекта <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="e5ae9-107">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="e5ae9-108">окне Указатель на <xref:System.AppDomainManager> объект, который реализуется узлом как `IUnknown` .</span><span class="sxs-lookup"><span data-stu-id="e5ae9-108">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5ae9-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e5ae9-109">Return Value</span></span>  
  
|<span data-ttu-id="e5ae9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5ae9-110">HRESULT</span></span>|<span data-ttu-id="e5ae9-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="e5ae9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5ae9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5ae9-112">S_OK</span></span>|<span data-ttu-id="e5ae9-113">`SetAppDomainManager` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="e5ae9-113">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="e5ae9-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e5ae9-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e5ae9-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="e5ae9-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e5ae9-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e5ae9-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e5ae9-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="e5ae9-117">The call timed out.</span></span>|  
|<span data-ttu-id="e5ae9-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e5ae9-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e5ae9-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="e5ae9-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e5ae9-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e5ae9-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e5ae9-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="e5ae9-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e5ae9-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e5ae9-122">E_FAIL</span></span>|<span data-ttu-id="e5ae9-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="e5ae9-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e5ae9-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="e5ae9-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e5ae9-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e5ae9-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5ae9-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="e5ae9-126">Remarks</span></span>  

 <span data-ttu-id="e5ae9-127"><xref:System.AppDomainManager>Предоставляет ведущему приложению механизм для начальной загрузки в управляемый код и управления созданием и параметрами каждого из них <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="e5ae9-127">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="e5ae9-128">Объект <xref:System.AppDomainManager> загружается в каждый <xref:System.AppDomain> при <xref:System.AppDomain> создании.</span><span class="sxs-lookup"><span data-stu-id="e5ae9-128">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="e5ae9-129">Если он выбран, среда CLR уведомляет узел о том, что домен приложения был создан, задав значение `pUnkAppDomainManager` параметра.</span><span class="sxs-lookup"><span data-stu-id="e5ae9-129">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="e5ae9-130">В своей реализации `SetAppDomainManager` метода узел может задать имя и тип сборки для диспетчера домена приложения.</span><span class="sxs-lookup"><span data-stu-id="e5ae9-130">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5ae9-131">Требования</span><span class="sxs-lookup"><span data-stu-id="e5ae9-131">Requirements</span></span>  

 <span data-ttu-id="e5ae9-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5ae9-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ae9-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e5ae9-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e5ae9-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5ae9-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5ae9-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ae9-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ae9-136">См. также</span><span class="sxs-lookup"><span data-stu-id="e5ae9-136">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="e5ae9-137">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="e5ae9-137">IHostControl Interface</span></span>](ihostcontrol-interface.md)
