---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: CurrentDomain'
title: Метод ICorRuntimeHost::CurrentDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
ms.openlocfilehash: fd75028b57475a620cc88a75016911dd0ab55b2e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784903"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="0347c-103">Метод ICorRuntimeHost::CurrentDomain</span><span class="sxs-lookup"><span data-stu-id="0347c-103">ICorRuntimeHost::CurrentDomain Method</span></span>

<span data-ttu-id="0347c-104">Возвращает указатель интерфейса типа <xref:System.AppDomain?displayProperty=nameWithType> , который представляет домен, загруженный в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="0347c-104">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0347c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0347c-105">Syntax</span></span>  
  
```cpp  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0347c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0347c-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="0347c-107">заполняет Указатель типа <xref:System.AppDomain?displayProperty=nameWithType> , представляющий текущий домен приложения потока.</span><span class="sxs-lookup"><span data-stu-id="0347c-107">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="0347c-108">Этот указатель типизирован `IUnknown` , поэтому вызывающие объекты должны, как правило, вызывать `QueryInterface` для получения указателя типа <xref:System._AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="0347c-108">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0347c-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0347c-109">Return Value</span></span>  
  
|<span data-ttu-id="0347c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0347c-110">HRESULT</span></span>|<span data-ttu-id="0347c-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="0347c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0347c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0347c-112">S_OK</span></span>|<span data-ttu-id="0347c-113">Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="0347c-113">The operation was successful.</span></span>|  
|<span data-ttu-id="0347c-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0347c-114">S_FALSE</span></span>|<span data-ttu-id="0347c-115">Не удалось завершить операцию.</span><span class="sxs-lookup"><span data-stu-id="0347c-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="0347c-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0347c-116">E_FAIL</span></span>|<span data-ttu-id="0347c-117">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="0347c-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0347c-118">Если метод возвращает E_FAIL, общеязыковая среда выполнения (CLR) больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="0347c-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="0347c-119">Последующие вызовы любых API размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0347c-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0347c-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0347c-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0347c-121">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="0347c-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0347c-122">Требования</span><span class="sxs-lookup"><span data-stu-id="0347c-122">Requirements</span></span>  

 <span data-ttu-id="0347c-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0347c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0347c-124">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0347c-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0347c-125">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0347c-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0347c-126">**Платформа .NET Framework версии:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="0347c-126">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0347c-127">См. также</span><span class="sxs-lookup"><span data-stu-id="0347c-127">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="0347c-128">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0347c-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
