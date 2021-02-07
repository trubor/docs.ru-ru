---
description: 'Дополнительные сведения о методе: IHostMemoryManager:: CreateMAlloc'
title: Метод IHostMemoryManager::CreateMAlloc
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.CreateMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type:
- apiref
ms.openlocfilehash: de73490a5c8b4e1672beb4750bcc617c2371f07b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707893"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="583c1-103">Метод IHostMemoryManager::CreateMAlloc</span><span class="sxs-lookup"><span data-stu-id="583c1-103">IHostMemoryManager::CreateMAlloc Method</span></span>

<span data-ttu-id="583c1-104">Возвращает указатель интерфейса на экземпляр [IHostMAlloc](ihostmalloc-interface.md) , который используется для выполнения запросов на выделение из кучи, созданной узлом.</span><span class="sxs-lookup"><span data-stu-id="583c1-104">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="583c1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="583c1-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="583c1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="583c1-106">Parameters</span></span>  

 `dwMallocType`  
 <span data-ttu-id="583c1-107">окне Сочетание флагов [MALLOC_TYPE](malloc-type-enumeration.md) , определяющих характеристики выделяемой памяти.</span><span class="sxs-lookup"><span data-stu-id="583c1-107">[in] A combination of [MALLOC_TYPE](malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="583c1-108">заполняет Указатель на адрес `IHostMAlloc` экземпляра, предоставленного узлом.</span><span class="sxs-lookup"><span data-stu-id="583c1-108">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="583c1-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="583c1-109">Return Value</span></span>  
  
|<span data-ttu-id="583c1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="583c1-110">HRESULT</span></span>|<span data-ttu-id="583c1-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="583c1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="583c1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="583c1-112">S_OK</span></span>|<span data-ttu-id="583c1-113">`CreateMAlloc` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="583c1-113">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="583c1-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="583c1-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="583c1-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="583c1-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="583c1-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="583c1-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="583c1-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="583c1-117">The call timed out.</span></span>|  
|<span data-ttu-id="583c1-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="583c1-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="583c1-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="583c1-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="583c1-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="583c1-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="583c1-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="583c1-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="583c1-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="583c1-122">E_FAIL</span></span>|<span data-ttu-id="583c1-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="583c1-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="583c1-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="583c1-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="583c1-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="583c1-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="583c1-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="583c1-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="583c1-127">Недостаточно физической памяти для завершения запроса на выделение.</span><span class="sxs-lookup"><span data-stu-id="583c1-127">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="583c1-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="583c1-128">Remarks</span></span>  

 <span data-ttu-id="583c1-129">`CreateMAlloc` Возвращает объект, позволяющий среде CLR выполнять запросы на выделение через основное приложение, а не использовать стандартные функции Win32.</span><span class="sxs-lookup"><span data-stu-id="583c1-129">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="583c1-130">Требования</span><span class="sxs-lookup"><span data-stu-id="583c1-130">Requirements</span></span>  

 <span data-ttu-id="583c1-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="583c1-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="583c1-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="583c1-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="583c1-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="583c1-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="583c1-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="583c1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="583c1-135">См. также</span><span class="sxs-lookup"><span data-stu-id="583c1-135">See also</span></span>

- [<span data-ttu-id="583c1-136">Интерфейс IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="583c1-136">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="583c1-137">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="583c1-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
