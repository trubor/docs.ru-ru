---
description: 'Дополнительные сведения о методе: Иклрдомаинманажер:: Сетпропертиесфордефаултаппдомаин'
title: Метод ICLRDomainManager::SetPropertiesForDefaultAppDomain
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
ms.openlocfilehash: 08e6c885d5d089fa22c30a4e3cef69480b840031
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689447"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="a3561-103">Метод ICLRDomainManager::SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="a3561-103">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>

<span data-ttu-id="a3561-104">Задает свойства, которые будут использоваться для инициализации домена приложения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a3561-104">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3561-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a3561-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3561-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a3561-106">Parameters</span></span>  

 `nProperties`  
 <span data-ttu-id="a3561-107">окне Число записей в `pwszPropertyNames` и `pwszPropertyValues` .</span><span class="sxs-lookup"><span data-stu-id="a3561-107">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="a3561-108">окне Массив имен свойств или значение null, если свойства отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="a3561-108">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="a3561-109">В настоящее время единственным именем свойства, распознаваемым этим методом, является "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="a3561-109">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="a3561-110">окне Массив значений свойств или значение null, если свойства отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="a3561-110">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3561-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a3561-111">Return Value</span></span>  

 <span data-ttu-id="a3561-112">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="a3561-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a3561-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3561-113">HRESULT</span></span>|<span data-ttu-id="a3561-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="a3561-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3561-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3561-115">S_OK</span></span>|<span data-ttu-id="a3561-116">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="a3561-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="a3561-117">HRESULT_FROM_WIN32 (ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="a3561-117">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="a3561-118">`pwszPropertyNames` содержит имя свойства, которое не распознается этим методом.</span><span class="sxs-lookup"><span data-stu-id="a3561-118">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3561-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="a3561-119">Remarks</span></span>  

 <span data-ttu-id="a3561-120">Значение свойства для "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" — это список сборок, имеющих условный <xref:System.Security.AllowPartiallyTrustedCallersAttribute> атрибут (APTCA) с <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> флагом, который должен быть видимым для частично доверенных вызывающих объектов в домене приложения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a3561-120">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3561-121">Требования</span><span class="sxs-lookup"><span data-stu-id="a3561-121">Requirements</span></span>  

 <span data-ttu-id="a3561-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3561-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3561-123">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="a3561-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a3561-124">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3561-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3561-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3561-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3561-126">См. также</span><span class="sxs-lookup"><span data-stu-id="a3561-126">See also</span></span>

- [<span data-ttu-id="a3561-127">Размещение</span><span class="sxs-lookup"><span data-stu-id="a3561-127">Hosting</span></span>](index.md)
- [<span data-ttu-id="a3561-128">Интерфейс ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="a3561-128">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
