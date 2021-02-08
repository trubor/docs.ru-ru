---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: Енумдомаинс'
title: Метод ICorRuntimeHost::EnumDomains
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.EnumDomains
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type:
- apiref
ms.openlocfilehash: e581fe95a78a4f55d50a99e4925e03a1777268a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784877"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="966a5-103">Метод ICorRuntimeHost::EnumDomains</span><span class="sxs-lookup"><span data-stu-id="966a5-103">ICorRuntimeHost::EnumDomains Method</span></span>

<span data-ttu-id="966a5-104">Возвращает перечислитель для доменов в текущем процессе.</span><span class="sxs-lookup"><span data-stu-id="966a5-104">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="966a5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="966a5-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="966a5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="966a5-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="966a5-107">заполняет Перечислитель для доменов.</span><span class="sxs-lookup"><span data-stu-id="966a5-107">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="966a5-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="966a5-108">Return Value</span></span>  
  
|<span data-ttu-id="966a5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="966a5-109">HRESULT</span></span>|<span data-ttu-id="966a5-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="966a5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="966a5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="966a5-111">S_OK</span></span>|<span data-ttu-id="966a5-112">Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="966a5-112">The operation was successful.</span></span>|  
|<span data-ttu-id="966a5-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="966a5-113">S_FALSE</span></span>|<span data-ttu-id="966a5-114">Не удалось завершить операцию.</span><span class="sxs-lookup"><span data-stu-id="966a5-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="966a5-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="966a5-115">E_FAIL</span></span>|<span data-ttu-id="966a5-116">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="966a5-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="966a5-117">Если метод возвращает E_FAIL, общеязыковая среда выполнения (CLR) больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="966a5-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="966a5-118">Последующие вызовы любых API размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="966a5-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="966a5-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="966a5-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="966a5-120">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="966a5-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="966a5-121">Требования</span><span class="sxs-lookup"><span data-stu-id="966a5-121">Requirements</span></span>  

 <span data-ttu-id="966a5-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="966a5-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="966a5-123">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="966a5-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="966a5-124">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="966a5-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="966a5-125">**Версия платформа .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="966a5-125">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="966a5-126">См. также</span><span class="sxs-lookup"><span data-stu-id="966a5-126">See also</span></span>

- [<span data-ttu-id="966a5-127">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="966a5-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
