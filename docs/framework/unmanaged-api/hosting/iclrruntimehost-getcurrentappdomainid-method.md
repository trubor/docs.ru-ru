---
description: 'Дополнительные сведения о методе: ICLRRuntimeHost:: Жеткуррентаппдомаинид'
title: Метод ICLRRuntimeHost::GetCurrentAppDomainId
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
ms.openlocfilehash: 88d5288e2e8ee7d8d1f5430261e21052334240be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799734"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="77616-103">Метод ICLRRuntimeHost::GetCurrentAppDomainId</span><span class="sxs-lookup"><span data-stu-id="77616-103">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>

<span data-ttu-id="77616-104">Возвращает числовой идентификатор объекта <xref:System.AppDomain> , который выполняется в данный момент.</span><span class="sxs-lookup"><span data-stu-id="77616-104">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77616-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77616-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77616-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="77616-106">Parameters</span></span>  

 `pdwAppDomainId`  
 <span data-ttu-id="77616-107">заполняет Числовой идентификатор объекта <xref:System.AppDomain> , который выполняется в данный момент.</span><span class="sxs-lookup"><span data-stu-id="77616-107">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77616-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="77616-108">Return Value</span></span>  
  
|<span data-ttu-id="77616-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77616-109">HRESULT</span></span>|<span data-ttu-id="77616-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="77616-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77616-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="77616-111">S_OK</span></span>|<span data-ttu-id="77616-112">`GetCurrentAppDomainId` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="77616-112">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="77616-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77616-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77616-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="77616-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77616-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77616-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77616-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="77616-116">The call timed out.</span></span>|  
|<span data-ttu-id="77616-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77616-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77616-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="77616-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77616-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77616-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77616-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="77616-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77616-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77616-121">E_FAIL</span></span>|<span data-ttu-id="77616-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="77616-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77616-123">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="77616-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77616-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="77616-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77616-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="77616-125">Remarks</span></span>  

 <span data-ttu-id="77616-126">`pdwAppDomainId`Параметру присваивается значение <xref:System.AppDomain.Id%2A> свойства объекта, <xref:System.AppDomain> в котором выполняется текущий поток.</span><span class="sxs-lookup"><span data-stu-id="77616-126">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77616-127">Требования</span><span class="sxs-lookup"><span data-stu-id="77616-127">Requirements</span></span>  

 <span data-ttu-id="77616-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77616-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77616-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="77616-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77616-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77616-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77616-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77616-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77616-132">См. также</span><span class="sxs-lookup"><span data-stu-id="77616-132">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="77616-133">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="77616-133">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
