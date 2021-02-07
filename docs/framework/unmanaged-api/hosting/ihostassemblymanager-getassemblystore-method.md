---
description: 'Дополнительные сведения о методе: IHostAssemblyManager:: Жетассемблисторе'
title: Метод IHostAssemblyManager::GetAssemblyStore
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
ms.openlocfilehash: 5edfdc5481803ce0dd3a6f8f400b18e3f1600ea8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709117"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="dedf1-103">Метод IHostAssemblyManager::GetAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="dedf1-103">IHostAssemblyManager::GetAssemblyStore Method</span></span>

<span data-ttu-id="dedf1-104">Возвращает указатель интерфейса на объект [IHostAssemblyStore](ihostassemblystore-interface.md) , представляющий список сборок, загруженных узлом.</span><span class="sxs-lookup"><span data-stu-id="dedf1-104">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dedf1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dedf1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dedf1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dedf1-106">Parameters</span></span>  

 `ppAssemblyStore`  
 <span data-ttu-id="dedf1-107">заполняет Указатель функции на `IHostAssemblyStore` экземпляр или значение null, если узел не реализует `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="dedf1-107">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dedf1-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dedf1-108">Return Value</span></span>  
  
|<span data-ttu-id="dedf1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dedf1-109">HRESULT</span></span>|<span data-ttu-id="dedf1-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="dedf1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dedf1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dedf1-111">S_OK</span></span>|<span data-ttu-id="dedf1-112">`GetAssemblyStore` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="dedf1-112">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="dedf1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dedf1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dedf1-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="dedf1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dedf1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dedf1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dedf1-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="dedf1-116">The call timed out.</span></span>|  
|<span data-ttu-id="dedf1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dedf1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dedf1-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="dedf1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dedf1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dedf1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dedf1-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="dedf1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dedf1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dedf1-121">E_FAIL</span></span>|<span data-ttu-id="dedf1-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="dedf1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dedf1-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="dedf1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dedf1-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dedf1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dedf1-125">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="dedf1-125">E_NOINTERFACE</span></span>|<span data-ttu-id="dedf1-126">Узел не предоставляет реализацию `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="dedf1-126">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dedf1-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="dedf1-127">Remarks</span></span>  

 <span data-ttu-id="dedf1-128">`IHostAssemblyStore` предоставляет методы, позволяющие узлу выполнять привязку к сборкам и модулям независимо от среды CLR.</span><span class="sxs-lookup"><span data-stu-id="dedf1-128">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="dedf1-129">Узлы обычно предоставляют хранилища сборок, позволяющие загружать сборки из форматов, отличных от файловой системы.</span><span class="sxs-lookup"><span data-stu-id="dedf1-129">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dedf1-130">Если узел не реализует `IHostAssemblyStore` , `GetAssemblyStore` должен возвращать значение HRESULT E_NOINTERFACE и должно иметь значение `ppAssemblyStore` null.</span><span class="sxs-lookup"><span data-stu-id="dedf1-130">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dedf1-131">Требования</span><span class="sxs-lookup"><span data-stu-id="dedf1-131">Requirements</span></span>  

 <span data-ttu-id="dedf1-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dedf1-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dedf1-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dedf1-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dedf1-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dedf1-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dedf1-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dedf1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dedf1-136">См. также</span><span class="sxs-lookup"><span data-stu-id="dedf1-136">See also</span></span>

- [<span data-ttu-id="dedf1-137">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="dedf1-137">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="dedf1-138">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="dedf1-138">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
