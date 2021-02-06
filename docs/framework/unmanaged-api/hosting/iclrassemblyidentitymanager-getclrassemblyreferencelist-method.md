---
description: 'Дополнительные сведения о методе: ICLRAssemblyIdentityManager:: Getclrassemblyreferencelist-'
title: Метод ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type:
- apiref
ms.openlocfilehash: 91f7b9eaacee559c5e404b5dda0f8b4201f91a66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649563"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="3c55d-103">Метод ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="3c55d-103">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>

<span data-ttu-id="3c55d-104">Возвращает указатель интерфейса на экземпляр [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) из заданного списка частичных идентификаторов сборки.</span><span class="sxs-lookup"><span data-stu-id="3c55d-104">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c55d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3c55d-105">Syntax</span></span>  
  
```cpp  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c55d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3c55d-106">Parameters</span></span>  

 `ppwzAssemblyReferences`  
 <span data-ttu-id="3c55d-107">окне Массив строк с завершающим нулем в форме "имя, свойство = значение..." , задающих список частичных идентификаторов сборки.</span><span class="sxs-lookup"><span data-stu-id="3c55d-107">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="3c55d-108">окне Количество элементов в `ppwzAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="3c55d-108">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="3c55d-109">заполняет Указатель интерфейса на `ICLRAssemblyReferenceList` объект, содержащий данные удостоверения сборки для списка сборок, указанных в параметре `ppwzAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="3c55d-109">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c55d-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3c55d-110">Return Value</span></span>  
  
|<span data-ttu-id="3c55d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c55d-111">HRESULT</span></span>|<span data-ttu-id="3c55d-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="3c55d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c55d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c55d-113">S_OK</span></span>|<span data-ttu-id="3c55d-114">Метод возвратился успешно.</span><span class="sxs-lookup"><span data-stu-id="3c55d-114">The method returned successfully.</span></span>|  
|<span data-ttu-id="3c55d-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3c55d-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3c55d-116">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="3c55d-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3c55d-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3c55d-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3c55d-118">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="3c55d-118">The call timed out.</span></span>|  
|<span data-ttu-id="3c55d-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3c55d-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3c55d-120">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="3c55d-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3c55d-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3c55d-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3c55d-122">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="3c55d-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3c55d-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3c55d-123">E_FAIL</span></span>|<span data-ttu-id="3c55d-124">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="3c55d-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3c55d-125">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="3c55d-125">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3c55d-126">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3c55d-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c55d-127">Требования</span><span class="sxs-lookup"><span data-stu-id="3c55d-127">Requirements</span></span>  

 <span data-ttu-id="3c55d-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c55d-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c55d-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3c55d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c55d-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c55d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c55d-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c55d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c55d-132">См. также</span><span class="sxs-lookup"><span data-stu-id="3c55d-132">See also</span></span>

- [<span data-ttu-id="3c55d-133">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="3c55d-133">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="3c55d-134">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="3c55d-134">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
