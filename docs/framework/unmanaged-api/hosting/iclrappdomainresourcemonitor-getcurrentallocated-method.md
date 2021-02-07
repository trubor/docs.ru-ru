---
description: 'Дополнительные сведения о методе: ICLRAppDomainResourceMonitor:: GetCurrentAllocated'
title: Метод ICLRAppDomainResourceMonitor::GetCurrentAllocated
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type:
- apiref
ms.openlocfilehash: d7aaf31f775a9d6e2af95cf1a832c78587a85fe1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753956"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="cb02d-103">Метод ICLRAppDomainResourceMonitor::GetCurrentAllocated</span><span class="sxs-lookup"><span data-stu-id="cb02d-103">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>

<span data-ttu-id="cb02d-104">Возвращает общий размер (в байтах) всех выделений памяти, сделанных доменом приложения с момента его создания, без вычитания памяти, которая была собрана сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="cb02d-104">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb02d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cb02d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb02d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cb02d-106">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="cb02d-107">окне ИДЕНТИФИКАТОР запрошенного домена приложения.</span><span class="sxs-lookup"><span data-stu-id="cb02d-107">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="cb02d-108">заполняет Указатель на общий размер всех выделений памяти.</span><span class="sxs-lookup"><span data-stu-id="cb02d-108">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb02d-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cb02d-109">Return Value</span></span>  

 <span data-ttu-id="cb02d-110">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="cb02d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cb02d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb02d-111">HRESULT</span></span>|<span data-ttu-id="cb02d-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="cb02d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb02d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb02d-113">S_OK</span></span>|<span data-ttu-id="cb02d-114">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="cb02d-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="cb02d-115">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="cb02d-115">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="cb02d-116">Домен приложения был выгружен или не существует.</span><span class="sxs-lookup"><span data-stu-id="cb02d-116">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb02d-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="cb02d-117">Remarks</span></span>  

 <span data-ttu-id="cb02d-118">Этот метод является неуправляемым эквивалентом управляемого <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> Свойства.</span><span class="sxs-lookup"><span data-stu-id="cb02d-118">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb02d-119">Требования</span><span class="sxs-lookup"><span data-stu-id="cb02d-119">Requirements</span></span>  

 <span data-ttu-id="cb02d-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb02d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb02d-121">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="cb02d-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cb02d-122">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb02d-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb02d-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb02d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb02d-124">См. также</span><span class="sxs-lookup"><span data-stu-id="cb02d-124">See also</span></span>

- [<span data-ttu-id="cb02d-125">Интерфейс ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="cb02d-125">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="cb02d-126">Мониторинг ресурсов домена приложения</span><span class="sxs-lookup"><span data-stu-id="cb02d-126">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="cb02d-127">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="cb02d-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="cb02d-128">Размещение</span><span class="sxs-lookup"><span data-stu-id="cb02d-128">Hosting</span></span>](index.md)
