---
description: 'Дополнительные сведения о методе: ICLRAppDomainResourceMonitor:: GetCurrentSurvived'
title: Метод ICLRAppDomainResourceMonitor::GetCurrentSurvived
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
ms.openlocfilehash: 20aea8583da207144aa0ffe29591a113da789fa8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753917"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="1c6ac-103">Метод ICLRAppDomainResourceMonitor::GetCurrentSurvived</span><span class="sxs-lookup"><span data-stu-id="1c6ac-103">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>

<span data-ttu-id="1c6ac-104">Возвращает число байтов, сохранившихся последней полной блокирующей сборки мусора, на которые ссылается текущий домен приложения.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-104">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c6ac-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1c6ac-105">Syntax</span></span>  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c6ac-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1c6ac-106">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="1c6ac-107">окне ИДЕНТИФИКАТОР запрошенного домена приложения.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-107">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="1c6ac-108">заполняет Указатель на число байтов, сохранившихся после последней сборки мусора, удерживаемых этим доменом приложения.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-108">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="1c6ac-109">После полного сбора это число является точным и полным.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-109">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="1c6ac-110">После эфемерной коллекции это число может быть неполным.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-110">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="1c6ac-111">Этот параметр может иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-111">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="1c6ac-112">заполняет Указатель на общее число байтов, сохранившихся из последней сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-112">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="1c6ac-113">После полной сборки мусора это число представляет число байтов, хранящихся в управляемых кучах.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-113">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="1c6ac-114">После эфемерной коллекции это число представляет число байтов, которые удерживаются в режиме эфемерного поколения.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-114">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="1c6ac-115">Этот параметр может иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-115">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c6ac-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1c6ac-116">Return Value</span></span>  

 <span data-ttu-id="1c6ac-117">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-117">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1c6ac-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c6ac-118">HRESULT</span></span>|<span data-ttu-id="1c6ac-119">Описание:</span><span class="sxs-lookup"><span data-stu-id="1c6ac-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1c6ac-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="1c6ac-120">S_OK</span></span>|<span data-ttu-id="1c6ac-121">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="1c6ac-122">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="1c6ac-122">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="1c6ac-123">Домен приложения был выгружен или не существует.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-123">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c6ac-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="1c6ac-124">Remarks</span></span>  

 <span data-ttu-id="1c6ac-125">Статистика обновляется только после полной блокированной сборки мусора; то есть коллекция, включающая все поколения и останавливающая работу приложения во время сбора.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-125">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="1c6ac-126">Например, <xref:System.GC.Collect?displayProperty=nameWithType> перегрузка метода выполняет полную блокированную коллекцию.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-126">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="1c6ac-127">Параллельная сборка мусора выполняется в фоновом режиме и не блокирует приложение.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-127">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="1c6ac-128">`GetCurrentSurvived`Метод является неуправляемым эквивалентом управляемого <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> Свойства.</span><span class="sxs-lookup"><span data-stu-id="1c6ac-128">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c6ac-129">Требования</span><span class="sxs-lookup"><span data-stu-id="1c6ac-129">Requirements</span></span>  

 <span data-ttu-id="1c6ac-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c6ac-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c6ac-131">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="1c6ac-131">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1c6ac-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1c6ac-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c6ac-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c6ac-133">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c6ac-134">См. также</span><span class="sxs-lookup"><span data-stu-id="1c6ac-134">See also</span></span>

- [<span data-ttu-id="1c6ac-135">Интерфейс ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="1c6ac-135">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="1c6ac-136">Мониторинг ресурсов домена приложения</span><span class="sxs-lookup"><span data-stu-id="1c6ac-136">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="1c6ac-137">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="1c6ac-137">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="1c6ac-138">Размещение</span><span class="sxs-lookup"><span data-stu-id="1c6ac-138">Hosting</span></span>](index.md)
