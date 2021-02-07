---
description: 'Дополнительные сведения о методе: ICLRAppDomainResourceMonitor:: GetCurrentCpuTime'
title: Метод ICLRAppDomainResourceMonitor::GetCurrentCpuTime
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
ms.openlocfilehash: ce36bf4ab88f953834d3ff12404bcaadcb42812d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753933"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="2cd24-103">Метод ICLRAppDomainResourceMonitor::GetCurrentCpuTime</span><span class="sxs-lookup"><span data-stu-id="2cd24-103">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>

<span data-ttu-id="2cd24-104">Возвращает общее время процессора, которое использовалось всеми потоками во время выполнения в текущем домене приложения, так как был создан домен приложения.</span><span class="sxs-lookup"><span data-stu-id="2cd24-104">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cd24-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2cd24-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cd24-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2cd24-106">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="2cd24-107">окне ИДЕНТИФИКАТОР запрошенного домена приложения.</span><span class="sxs-lookup"><span data-stu-id="2cd24-107">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="2cd24-108">заполняет Указатель на общее время процессора, которое использовалось всеми потоками при выполнении в текущем домене приложения с момента создания домена приложения.</span><span class="sxs-lookup"><span data-stu-id="2cd24-108">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="2cd24-109">Этот параметр может иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="2cd24-109">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cd24-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2cd24-110">Return Value</span></span>  
  
|<span data-ttu-id="2cd24-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2cd24-111">HRESULT</span></span>|<span data-ttu-id="2cd24-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="2cd24-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2cd24-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2cd24-113">S_OK</span></span>|<span data-ttu-id="2cd24-114">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="2cd24-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="2cd24-115">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="2cd24-115">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="2cd24-116">Домен приложения был выгружен или не существует.</span><span class="sxs-lookup"><span data-stu-id="2cd24-116">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="2cd24-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2cd24-117">E_FAIL</span></span>|<span data-ttu-id="2cd24-118">Отслеживание ресурсов домена приложений не включено.</span><span class="sxs-lookup"><span data-stu-id="2cd24-118">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="2cd24-119">-или-</span><span class="sxs-lookup"><span data-stu-id="2cd24-119">-or-</span></span><br /><br /> <span data-ttu-id="2cd24-120">Все остальные сбои.</span><span class="sxs-lookup"><span data-stu-id="2cd24-120">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cd24-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="2cd24-121">Remarks</span></span>  

 <span data-ttu-id="2cd24-122">Этот метод является неуправляемым эквивалентом управляемого <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> Свойства.</span><span class="sxs-lookup"><span data-stu-id="2cd24-122">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cd24-123">Требования</span><span class="sxs-lookup"><span data-stu-id="2cd24-123">Requirements</span></span>  

 <span data-ttu-id="2cd24-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cd24-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cd24-125">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="2cd24-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2cd24-126">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2cd24-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cd24-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cd24-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd24-128">См. также</span><span class="sxs-lookup"><span data-stu-id="2cd24-128">See also</span></span>

- [<span data-ttu-id="2cd24-129">Интерфейс ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="2cd24-129">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="2cd24-130">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="2cd24-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="2cd24-131">Мониторинг ресурсов домена приложения</span><span class="sxs-lookup"><span data-stu-id="2cd24-131">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="2cd24-132">Размещение</span><span class="sxs-lookup"><span data-stu-id="2cd24-132">Hosting</span></span>](index.md)
