---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: Креатедомаинсетуп'
title: Метод ICorRuntimeHost::CreateDomainSetup
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
ms.openlocfilehash: b7c2dc55fa9f0d3d5a5c18e38c2c825048ae5f53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789688"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="0eb29-103">Метод ICorRuntimeHost::CreateDomainSetup</span><span class="sxs-lookup"><span data-stu-id="0eb29-103">ICorRuntimeHost::CreateDomainSetup Method</span></span>

<span data-ttu-id="0eb29-104">Возвращает указатель интерфейса типа IAppDomainSetup на <xref:System.AppDomainSetup?displayProperty=nameWithType> экземпляр.</span><span class="sxs-lookup"><span data-stu-id="0eb29-104">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="0eb29-105">`IAppDomainSetup` предоставляет методы для настройки аспектов домена приложения перед его созданием.</span><span class="sxs-lookup"><span data-stu-id="0eb29-105">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eb29-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0eb29-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0eb29-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="0eb29-107">Parameters</span></span>  

 `pAppDomainSetup`  
 <span data-ttu-id="0eb29-108">заполняет Указатель интерфейса на <xref:System.AppDomainSetup?displayProperty=nameWithType> экземпляр.</span><span class="sxs-lookup"><span data-stu-id="0eb29-108">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="0eb29-109">Этот параметр типизирован как `IUnknown` , поэтому вызывающие объекты должны обычно вызывать `QueryInterface` этот указатель для получения указателя интерфейса типа `IAppDomainSetup` .</span><span class="sxs-lookup"><span data-stu-id="0eb29-109">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0eb29-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0eb29-110">Return Value</span></span>  
  
|<span data-ttu-id="0eb29-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0eb29-111">HRESULT</span></span>|<span data-ttu-id="0eb29-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="0eb29-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0eb29-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0eb29-113">S_OK</span></span>|<span data-ttu-id="0eb29-114">Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="0eb29-114">The operation was successful.</span></span>|  
|<span data-ttu-id="0eb29-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0eb29-115">S_FALSE</span></span>|<span data-ttu-id="0eb29-116">Не удалось завершить операцию.</span><span class="sxs-lookup"><span data-stu-id="0eb29-116">The operation failed to complete.</span></span>|  
|<span data-ttu-id="0eb29-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0eb29-117">E_FAIL</span></span>|<span data-ttu-id="0eb29-118">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="0eb29-118">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0eb29-119">Если метод возвращает E_FAIL, общеязыковая среда выполнения (CLR) больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="0eb29-119">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="0eb29-120">Последующие вызовы любых API размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0eb29-120">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0eb29-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0eb29-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0eb29-122">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="0eb29-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eb29-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="0eb29-123">Remarks</span></span>  

 <span data-ttu-id="0eb29-124">Указатель, возвращаемый из этого метода, обычно передается в качестве параметра в метод [CreateDomainEx](icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0eb29-124">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eb29-125">Требования</span><span class="sxs-lookup"><span data-stu-id="0eb29-125">Requirements</span></span>  

 <span data-ttu-id="0eb29-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0eb29-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eb29-127">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0eb29-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0eb29-128">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0eb29-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0eb29-129">**Версия платформа .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="0eb29-129">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb29-130">См. также</span><span class="sxs-lookup"><span data-stu-id="0eb29-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="0eb29-131">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0eb29-131">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
