---
description: 'Дополнительные сведения о методе: Иклрхостпротектионманажер:: SetProtectedCategories'
title: Метод ICLRHostProtectionManager::SetProtectedCategories
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
ms.openlocfilehash: 9138c31ea1a2d9b7ebeaeac8ef5ef9305eabef8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637538"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="8ed0f-103">Метод ICLRHostProtectionManager::SetProtectedCategories</span><span class="sxs-lookup"><span data-stu-id="8ed0f-103">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>

<span data-ttu-id="8ed0f-104">Указывает, какие категории управляемых типов и членов следует блокировать при выполнении в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="8ed0f-104">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ed0f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8ed0f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ed0f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8ed0f-106">Parameters</span></span>  

 `categories`  
 <span data-ttu-id="8ed0f-107">окне Сочетание значений [еапикатегориес](eapicategories-enumeration.md) , указывающих, какие категории управляемых типов и членов должны блокироваться в коде с частичным доверием.</span><span class="sxs-lookup"><span data-stu-id="8ed0f-107">[in] A combination of [EApiCategories](eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ed0f-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8ed0f-108">Return Value</span></span>  
  
|<span data-ttu-id="8ed0f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ed0f-109">HRESULT</span></span>|<span data-ttu-id="8ed0f-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="8ed0f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ed0f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ed0f-111">S_OK</span></span>|<span data-ttu-id="8ed0f-112">`SetProtectedCategories` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="8ed0f-112">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="8ed0f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ed0f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ed0f-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="8ed0f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ed0f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ed0f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ed0f-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="8ed0f-116">The call timed out.</span></span>|  
|<span data-ttu-id="8ed0f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ed0f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ed0f-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="8ed0f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ed0f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ed0f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ed0f-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="8ed0f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ed0f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ed0f-121">E_FAIL</span></span>|<span data-ttu-id="8ed0f-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="8ed0f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8ed0f-123">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="8ed0f-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ed0f-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8ed0f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ed0f-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="8ed0f-125">Remarks</span></span>  

 <span data-ttu-id="8ed0f-126">Каждое `EApiCategories` значение ссылается на список управляемых типов и членов.</span><span class="sxs-lookup"><span data-stu-id="8ed0f-126">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="8ed0f-127">`EApiCategories`Перечисление и `SetProtectedCategories` метод напрямую связаны с управляемым <xref:System.Security.Permissions.HostProtectionAttribute> классом, который используется для пометки управляемых типов и членов, которые предоставляют возможности, соответствующие категориям, описанным в `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="8ed0f-127">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="8ed0f-128">Дополнительные сведения см <xref:System.Security.Permissions.HostProtectionAttribute> . в разделе и <xref:System.Security.Permissions.HostProtectionResource> перечисление, которое непосредственно соответствует `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="8ed0f-128">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ed0f-129">Требования</span><span class="sxs-lookup"><span data-stu-id="8ed0f-129">Requirements</span></span>  

 <span data-ttu-id="8ed0f-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ed0f-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ed0f-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8ed0f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ed0f-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ed0f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ed0f-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ed0f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed0f-134">См. также</span><span class="sxs-lookup"><span data-stu-id="8ed0f-134">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="8ed0f-135">Перечисление EApiCategories</span><span class="sxs-lookup"><span data-stu-id="8ed0f-135">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="8ed0f-136">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="8ed0f-136">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="8ed0f-137">Интерфейс ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="8ed0f-137">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
