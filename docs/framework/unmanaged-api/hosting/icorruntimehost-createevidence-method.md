---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: Креативиденце'
title: Метод ICorRuntimeHost::CreateEvidence
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 34694f7e867066430a28120b412237ef9c64c740
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789675"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="1544b-103">Метод ICorRuntimeHost::CreateEvidence</span><span class="sxs-lookup"><span data-stu-id="1544b-103">ICorRuntimeHost::CreateEvidence Method</span></span>

<span data-ttu-id="1544b-104">Возвращает указатель интерфейса типа <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> , который позволяет основному приложению создавать доказательства безопасности для передачи в метод [CreateDomain](icorruntimehost-createdomain-method.md) или [CreateDomainEx](icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1544b-104">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1544b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1544b-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1544b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1544b-106">Parameters</span></span>  

 `pEvidence`  
 <span data-ttu-id="1544b-107">заполняет Указатель интерфейса на экземпляр, <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> используемый для создания свидетельств безопасности.</span><span class="sxs-lookup"><span data-stu-id="1544b-107">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="1544b-108">Этот указатель типизирован `IUnknown` , поэтому вызывающие объекты обычно должны вызывать `QueryInterface` этот интерфейс для получения указателя на <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1544b-108">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1544b-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1544b-109">Return Value</span></span>  
  
|<span data-ttu-id="1544b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1544b-110">HRESULT</span></span>|<span data-ttu-id="1544b-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="1544b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1544b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1544b-112">S_OK</span></span>|<span data-ttu-id="1544b-113">Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="1544b-113">The operation was successful.</span></span>|  
|<span data-ttu-id="1544b-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1544b-114">S_FALSE</span></span>|<span data-ttu-id="1544b-115">Не удалось завершить операцию.</span><span class="sxs-lookup"><span data-stu-id="1544b-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1544b-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1544b-116">E_FAIL</span></span>|<span data-ttu-id="1544b-117">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="1544b-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1544b-118">Если метод возвращает E_FAIL, общеязыковая среда выполнения (CLR) больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="1544b-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1544b-119">Последующие вызовы любых API размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1544b-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1544b-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1544b-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1544b-121">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="1544b-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1544b-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="1544b-122">Remarks</span></span>  

 <span data-ttu-id="1544b-123">Этот метод возвращает пустую коллекцию, которая не может быть заполнена из машинного кода.</span><span class="sxs-lookup"><span data-stu-id="1544b-123">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="1544b-124">Вместо этого следует использовать <xref:System.Security.Policy.Evidence> метод.</span><span class="sxs-lookup"><span data-stu-id="1544b-124">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1544b-125">Требования</span><span class="sxs-lookup"><span data-stu-id="1544b-125">Requirements</span></span>  

 <span data-ttu-id="1544b-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1544b-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1544b-127">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1544b-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1544b-128">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1544b-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1544b-129">**Версия платформа .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="1544b-129">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1544b-130">См. также</span><span class="sxs-lookup"><span data-stu-id="1544b-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="1544b-131">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="1544b-131">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
