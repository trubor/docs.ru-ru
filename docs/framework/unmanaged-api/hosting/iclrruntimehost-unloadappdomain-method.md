---
description: 'Дополнительные сведения о методе: ICLRRuntimeHost:: Унлоадаппдомаин'
title: Метод ICLRRuntimeHost::UnloadAppDomain
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
ms.openlocfilehash: 2a47c6250434c3ee4122f8eeae75f25ee4c08a34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637291"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="06947-103">Метод ICLRRuntimeHost::UnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="06947-103">ICLRRuntimeHost::UnloadAppDomain Method</span></span>

<span data-ttu-id="06947-104">Выгружает управляемый объект <xref:System.AppDomain> , соответствующий указанному числовому идентификатору.</span><span class="sxs-lookup"><span data-stu-id="06947-104">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06947-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="06947-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06947-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="06947-106">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="06947-107">окне Числовой идентификатор домена приложения для выгрузки.</span><span class="sxs-lookup"><span data-stu-id="06947-107">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="06947-108">[входные] `true` чтобы указать, что общеязыковая среда выполнения (CLR) должна ожидать завершения выполнения текущего потока приложения перед попыткой выгрузить домен приложения.</span><span class="sxs-lookup"><span data-stu-id="06947-108">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06947-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="06947-109">Return Value</span></span>  
  
|<span data-ttu-id="06947-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="06947-110">HRESULT</span></span>|<span data-ttu-id="06947-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="06947-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06947-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="06947-112">S_OK</span></span>|<span data-ttu-id="06947-113">`UnloadAppDomain` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="06947-113">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="06947-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="06947-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="06947-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="06947-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="06947-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="06947-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="06947-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="06947-117">The call timed out.</span></span>|  
|<span data-ttu-id="06947-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="06947-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="06947-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="06947-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="06947-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="06947-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="06947-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="06947-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="06947-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="06947-122">E_FAIL</span></span>|<span data-ttu-id="06947-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="06947-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="06947-124">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="06947-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="06947-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="06947-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06947-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="06947-126">Remarks</span></span>  

 <span data-ttu-id="06947-127">Вы можете получить числовой идентификатор домена приложения, в котором выполняется текущий поток, вызвав [жеткуррентаппдомаинид](iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="06947-127">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="06947-128">Этот идентификатор соответствует <xref:System.AppDomain.Id%2A> свойству управляемого <xref:System.AppDomain> типа.</span><span class="sxs-lookup"><span data-stu-id="06947-128">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06947-129">Требования</span><span class="sxs-lookup"><span data-stu-id="06947-129">Requirements</span></span>  

 <span data-ttu-id="06947-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06947-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06947-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="06947-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="06947-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="06947-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06947-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06947-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06947-134">См. также</span><span class="sxs-lookup"><span data-stu-id="06947-134">See also</span></span>

- [<span data-ttu-id="06947-135">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="06947-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
