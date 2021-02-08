---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: Унлоаддомаин'
title: Метод ICorRuntimeHost::UnloadDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
ms.openlocfilehash: b191f2342778b2f2ed7ddb7b1fb548c73be96599
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799401"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="690aa-103">Метод ICorRuntimeHost::UnloadDomain</span><span class="sxs-lookup"><span data-stu-id="690aa-103">ICorRuntimeHost::UnloadDomain Method</span></span>

<span data-ttu-id="690aa-104">Выгружает указанный домен приложения из текущего процесса.</span><span class="sxs-lookup"><span data-stu-id="690aa-104">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="690aa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="690aa-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="690aa-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="690aa-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="690aa-107">окне Указатель типа <xref:System._AppDomain?displayProperty=nameWithType> , представляющий домен для выгрузки.</span><span class="sxs-lookup"><span data-stu-id="690aa-107">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="690aa-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="690aa-108">Return Value</span></span>  
  
|<span data-ttu-id="690aa-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="690aa-109">HRESULT</span></span>|<span data-ttu-id="690aa-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="690aa-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="690aa-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="690aa-111">S_OK</span></span>|<span data-ttu-id="690aa-112">Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="690aa-112">The operation was successful.</span></span>|  
|<span data-ttu-id="690aa-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="690aa-113">S_FALSE</span></span>|<span data-ttu-id="690aa-114">Не удалось завершить операцию.</span><span class="sxs-lookup"><span data-stu-id="690aa-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="690aa-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="690aa-115">E_FAIL</span></span>|<span data-ttu-id="690aa-116">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="690aa-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="690aa-117">Если метод возвращает E_FAIL, общеязыковая среда выполнения (CLR) больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="690aa-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="690aa-118">Последующие вызовы любых API размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="690aa-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="690aa-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="690aa-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="690aa-120">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="690aa-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="690aa-121">Требования</span><span class="sxs-lookup"><span data-stu-id="690aa-121">Requirements</span></span>  

 <span data-ttu-id="690aa-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="690aa-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="690aa-123">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="690aa-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="690aa-124">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="690aa-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="690aa-125">**Версия платформа .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="690aa-125">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="690aa-126">См. также</span><span class="sxs-lookup"><span data-stu-id="690aa-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="690aa-127">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="690aa-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
