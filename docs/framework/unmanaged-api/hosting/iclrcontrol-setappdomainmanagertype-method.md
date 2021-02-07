---
description: 'Дополнительные сведения о методе: ICLRControl:: SetAppDomainManagerType'
title: Метод ICLRControl::SetAppDomainManagerType
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
ms.openlocfilehash: 20d45a0ab14904c778a6ea821fcd63f85b6b0921
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716670"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="7b411-103">Метод ICLRControl::SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="7b411-103">ICLRControl::SetAppDomainManagerType Method</span></span>

<span data-ttu-id="7b411-104">Задает тип, производный от <xref:System.AppDomainManager> типа для диспетчеров доменов приложений.</span><span class="sxs-lookup"><span data-stu-id="7b411-104">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b411-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7b411-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b411-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7b411-106">Parameters</span></span>  

 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="7b411-107">окне Имя сборки, в которой реализован запрошенный тип, производный от <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="7b411-107">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="7b411-108">окне Имя типа, реализованного в `pwzAppDomainManagerAssembly` параметре, который реализует возможности <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="7b411-108">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b411-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7b411-109">Return Value</span></span>  
  
|<span data-ttu-id="7b411-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b411-110">HRESULT</span></span>|<span data-ttu-id="7b411-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="7b411-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b411-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b411-112">S_OK</span></span>|<span data-ttu-id="7b411-113">Метод возвратился успешно.</span><span class="sxs-lookup"><span data-stu-id="7b411-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="7b411-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7b411-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7b411-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7b411-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7b411-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7b411-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7b411-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="7b411-117">The call timed out.</span></span>|  
|<span data-ttu-id="7b411-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7b411-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7b411-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="7b411-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7b411-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7b411-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7b411-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="7b411-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7b411-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b411-122">E_FAIL</span></span>|<span data-ttu-id="7b411-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="7b411-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7b411-124">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="7b411-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7b411-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7b411-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b411-126">Требования</span><span class="sxs-lookup"><span data-stu-id="7b411-126">Requirements</span></span>  

 <span data-ttu-id="7b411-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b411-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b411-128">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7b411-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b411-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7b411-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b411-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b411-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b411-131">См. также</span><span class="sxs-lookup"><span data-stu-id="7b411-131">See also</span></span>

- [<span data-ttu-id="7b411-132">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="7b411-132">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="7b411-133">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="7b411-133">IHostControl Interface</span></span>](ihostcontrol-interface.md)
