---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: GetDefaultDomain'
title: Метод ICorRuntimeHost::GetDefaultDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
ms.openlocfilehash: 53be5e3db7bec396743edc728942ad54efc0ec16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753826"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="52268-103">Метод ICorRuntimeHost::GetDefaultDomain</span><span class="sxs-lookup"><span data-stu-id="52268-103">ICorRuntimeHost::GetDefaultDomain Method</span></span>

<span data-ttu-id="52268-104">Возвращает указатель интерфейса типа <xref:System._AppDomain?displayProperty=nameWithType> , представляющий домен по умолчанию для текущего процесса.</span><span class="sxs-lookup"><span data-stu-id="52268-104">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52268-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="52268-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52268-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="52268-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="52268-107">заполняет Указатель интерфейса типа <xref:System._AppDomain?displayProperty=nameWithType> на <xref:System.AppDomain> экземпляр, представляющий домен приложения по умолчанию для процесса.</span><span class="sxs-lookup"><span data-stu-id="52268-107">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="52268-108">Этот указатель типизирован `IUnknown` , поэтому вызывающие объекты должны, как правило, вызывать `QueryInterface` для получения указателя интерфейса типа <xref:System._AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="52268-108">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52268-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="52268-109">Return Value</span></span>  
  
|<span data-ttu-id="52268-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52268-110">HRESULT</span></span>|<span data-ttu-id="52268-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="52268-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52268-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="52268-112">S_OK</span></span>|<span data-ttu-id="52268-113">Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="52268-113">The operation was successful.</span></span>|  
|<span data-ttu-id="52268-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="52268-114">S_FALSE</span></span>|<span data-ttu-id="52268-115">Не удалось завершить операцию.</span><span class="sxs-lookup"><span data-stu-id="52268-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="52268-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="52268-116">E_FAIL</span></span>|<span data-ttu-id="52268-117">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="52268-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="52268-118">Если метод возвращает E_FAIL, общеязыковая среда выполнения (CLR) больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="52268-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="52268-119">Последующие вызовы любых API размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="52268-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="52268-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="52268-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="52268-121">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="52268-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52268-122">Требования</span><span class="sxs-lookup"><span data-stu-id="52268-122">Requirements</span></span>  

 <span data-ttu-id="52268-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52268-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52268-124">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="52268-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52268-125">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52268-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52268-126">**Платформа .NET Framework версии:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="52268-126">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52268-127">См. также</span><span class="sxs-lookup"><span data-stu-id="52268-127">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="52268-128">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="52268-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
