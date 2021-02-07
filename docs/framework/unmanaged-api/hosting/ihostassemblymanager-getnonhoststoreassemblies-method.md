---
description: 'Дополнительные сведения о методе: IHostAssemblyManager:: GetNonHostStoreAssemblies'
title: Метод IHostAssemblyManager::GetNonHostStoreAssemblies
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
ms.openlocfilehash: ef551db45428b2381dfeae8f722257241a4deaf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709052"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="7052f-103">Метод IHostAssemblyManager::GetNonHostStoreAssemblies</span><span class="sxs-lookup"><span data-stu-id="7052f-103">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>

<span data-ttu-id="7052f-104">Возвращает указатель интерфейса на объект [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , представляющий список сборок, которые должны загружаться хостом в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="7052f-104">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7052f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7052f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7052f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7052f-106">Parameters</span></span>  

 `ppReferenceList`  
 <span data-ttu-id="7052f-107">заполняет Указатель на адрес объекта `ICLRAssemblyReferenceList` , содержащий список ссылок на сборки, которые узел загружает в среду CLR.</span><span class="sxs-lookup"><span data-stu-id="7052f-107">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7052f-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7052f-108">Return Value</span></span>  
  
|<span data-ttu-id="7052f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7052f-109">HRESULT</span></span>|<span data-ttu-id="7052f-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="7052f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7052f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7052f-111">S_OK</span></span>|<span data-ttu-id="7052f-112">`GetNonHostStoreAssemblies` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="7052f-112">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="7052f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7052f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7052f-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7052f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7052f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7052f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7052f-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="7052f-116">The call timed out.</span></span>|  
|<span data-ttu-id="7052f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7052f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7052f-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="7052f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7052f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7052f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7052f-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="7052f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7052f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7052f-121">E_FAIL</span></span>|<span data-ttu-id="7052f-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="7052f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7052f-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="7052f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7052f-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7052f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7052f-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7052f-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7052f-126">Недостаточно свободной памяти для создания списка ссылок для запрошенного объекта `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="7052f-126">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7052f-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="7052f-127">Remarks</span></span>  

 <span data-ttu-id="7052f-128">Среда CLR разрешает ссылки с помощью следующего набора рекомендаций:</span><span class="sxs-lookup"><span data-stu-id="7052f-128">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="7052f-129">Во первых, он обращается к списку ссылок на сборки, возвращаемых `GetNonHostStoreAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="7052f-129">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="7052f-130">Если сборка отображается в списке, среда CLR привязывает ее к обычному.</span><span class="sxs-lookup"><span data-stu-id="7052f-130">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="7052f-131">Если сборка не отображается в списке и узел предоставил реализацию [IHostAssemblyStore](ihostassemblystore-interface.md), среда CLR вызывает [IHostAssemblyStore::P ровидеассембли](ihostassemblystore-provideassembly-method.md) , чтобы разрешить узлу предоставить сборку для привязки.</span><span class="sxs-lookup"><span data-stu-id="7052f-131">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="7052f-132">В противном случае среда CLR не сможет выполнить привязку к сборке.</span><span class="sxs-lookup"><span data-stu-id="7052f-132">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="7052f-133">Если узел `ppReferenceList` имеет значение null, среда CLR сначала проверяет глобальный кэш сборок, вызывает `ProvideAssembly` , а затем проверяет базу приложения для разрешения ссылки на сборку.</span><span class="sxs-lookup"><span data-stu-id="7052f-133">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7052f-134">После инициализации среда CLR вызывает `GetNonHostStoreAssemblies` только один раз.</span><span class="sxs-lookup"><span data-stu-id="7052f-134">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="7052f-135">Метод не вызывается снова.</span><span class="sxs-lookup"><span data-stu-id="7052f-135">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7052f-136">Требования</span><span class="sxs-lookup"><span data-stu-id="7052f-136">Requirements</span></span>  

 <span data-ttu-id="7052f-137">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7052f-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7052f-138">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7052f-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7052f-139">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7052f-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7052f-140">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7052f-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7052f-141">См. также</span><span class="sxs-lookup"><span data-stu-id="7052f-141">See also</span></span>

- [<span data-ttu-id="7052f-142">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="7052f-142">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="7052f-143">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="7052f-143">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="7052f-144">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="7052f-144">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
