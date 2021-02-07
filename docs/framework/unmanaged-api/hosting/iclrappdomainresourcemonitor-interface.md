---
description: 'Дополнительные сведения о: интерфейс ICLRAppDomainResourceMonitor'
title: Интерфейс ICLRAppDomainResourceMonitor
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
ms.openlocfilehash: 85321eabedb6912efabe57553732f8c6a4063155
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753904"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="d09ae-103">Интерфейс ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="d09ae-103">ICLRAppDomainResourceMonitor Interface</span></span>

<span data-ttu-id="d09ae-104">Предоставляет методы для проверки использования памяти и ЦП домена приложения.</span><span class="sxs-lookup"><span data-stu-id="d09ae-104">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d09ae-105">Методы</span><span class="sxs-lookup"><span data-stu-id="d09ae-105">Methods</span></span>  
  
|<span data-ttu-id="d09ae-106">Метод</span><span class="sxs-lookup"><span data-stu-id="d09ae-106">Method</span></span>|<span data-ttu-id="d09ae-107">Описание</span><span class="sxs-lookup"><span data-stu-id="d09ae-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d09ae-108">Метод GetCurrentAllocated</span><span class="sxs-lookup"><span data-stu-id="d09ae-108">GetCurrentAllocated Method</span></span>](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="d09ae-109">Возвращает общий размер (в байтах) всех выделений памяти, сделанных доменом приложения с момента его создания, без вычитания памяти, которая была собрана сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="d09ae-109">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="d09ae-110">Метод GetCurrentSurvived</span><span class="sxs-lookup"><span data-stu-id="d09ae-110">GetCurrentSurvived Method</span></span>](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="d09ae-111">Возвращает число байтов, сохранившихся последней полной блокирующей сборки мусора, на которые ссылается текущий домен приложения.</span><span class="sxs-lookup"><span data-stu-id="d09ae-111">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="d09ae-112">Метод GetCurrentCpuTime</span><span class="sxs-lookup"><span data-stu-id="d09ae-112">GetCurrentCpuTime Method</span></span>](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="d09ae-113">Возвращает общее время процессора, которое использовалось всеми потоками во время выполнения в текущем домене приложения, так как был создан домен приложения.</span><span class="sxs-lookup"><span data-stu-id="d09ae-113">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d09ae-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="d09ae-114">Remarks</span></span>  

 <span data-ttu-id="d09ae-115">`ICLRAppDomainResourceMonitor`Интерфейс предоставляет функциональные возможности, аналогичные следующим управляемым свойствам:</span><span class="sxs-lookup"><span data-stu-id="d09ae-115">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="d09ae-116">Требования</span><span class="sxs-lookup"><span data-stu-id="d09ae-116">Requirements</span></span>  

 <span data-ttu-id="d09ae-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d09ae-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d09ae-118">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="d09ae-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d09ae-119">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d09ae-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d09ae-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d09ae-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09ae-121">См. также</span><span class="sxs-lookup"><span data-stu-id="d09ae-121">See also</span></span>

- [<span data-ttu-id="d09ae-122">\<appDomainResourceMonitoring> Элемент</span><span class="sxs-lookup"><span data-stu-id="d09ae-122">\<appDomainResourceMonitoring> Element</span></span>](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="d09ae-123">Мониторинг ресурсов домена приложения</span><span class="sxs-lookup"><span data-stu-id="d09ae-123">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="d09ae-124">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="d09ae-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="d09ae-125">Размещение</span><span class="sxs-lookup"><span data-stu-id="d09ae-125">Hosting</span></span>](index.md)
