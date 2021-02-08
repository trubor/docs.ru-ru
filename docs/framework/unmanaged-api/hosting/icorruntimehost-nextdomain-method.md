---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: Некстдомаин'
title: Метод ICorRuntimeHost::NextDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
ms.openlocfilehash: cfced9d1d3c91f4ec9508b86157ceebae9f95a56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789623"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="0bedd-103">Метод ICorRuntimeHost::NextDomain</span><span class="sxs-lookup"><span data-stu-id="0bedd-103">ICorRuntimeHost::NextDomain Method</span></span>

<span data-ttu-id="0bedd-104">Возвращает указатель интерфейса на следующий домен в перечислении.</span><span class="sxs-lookup"><span data-stu-id="0bedd-104">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bedd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0bedd-105">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bedd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0bedd-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="0bedd-107">окне Перечислитель, полученный при вызове [енумдомаинс](icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="0bedd-107">[in] The enumerator that was obtained through a call to [EnumDomains](icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="0bedd-108">заполняет Указатель интерфейса на <xref:System._AppDomain?displayProperty=nameWithType> тип, представляющий следующий домен в перечислении, или значение null, если другие домены не существуют.</span><span class="sxs-lookup"><span data-stu-id="0bedd-108">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bedd-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0bedd-109">Return Value</span></span>  
  
|<span data-ttu-id="0bedd-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0bedd-110">HRESULT</span></span>|<span data-ttu-id="0bedd-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="0bedd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0bedd-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0bedd-112">S_OK</span></span>|<span data-ttu-id="0bedd-113">Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="0bedd-113">The operation was successful.</span></span>|  
|<span data-ttu-id="0bedd-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0bedd-114">S_FALSE</span></span>|<span data-ttu-id="0bedd-115">Не удалось завершить операцию, или в перечислении больше нет доменов.</span><span class="sxs-lookup"><span data-stu-id="0bedd-115">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="0bedd-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0bedd-116">E_FAIL</span></span>|<span data-ttu-id="0bedd-117">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="0bedd-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0bedd-118">Если метод возвращает E_FAIL, общеязыковая среда выполнения (CLR) больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="0bedd-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="0bedd-119">Последующие вызовы любых API размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0bedd-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0bedd-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0bedd-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0bedd-121">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="0bedd-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0bedd-122">Требования</span><span class="sxs-lookup"><span data-stu-id="0bedd-122">Requirements</span></span>  

 <span data-ttu-id="0bedd-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bedd-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bedd-124">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0bedd-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0bedd-125">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0bedd-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0bedd-126">**Платформа .NET Framework версии:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="0bedd-126">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bedd-127">См. также</span><span class="sxs-lookup"><span data-stu-id="0bedd-127">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="0bedd-128">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0bedd-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
