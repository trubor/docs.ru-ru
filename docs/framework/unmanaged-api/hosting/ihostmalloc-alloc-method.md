---
description: 'Дополнительные сведения о методе: IHostMAlloc:: Alloc'
title: Метод IHostMAlloc::Alloc
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
ms.openlocfilehash: e0349c273ef9e3194bb8bad167510dd8fefcab62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708242"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="cd696-103">Метод IHostMAlloc::Alloc</span><span class="sxs-lookup"><span data-stu-id="cd696-103">IHostMAlloc::Alloc Method</span></span>

<span data-ttu-id="cd696-104">Запрашивает, что узел выделяет указанный объем памяти из кучи.</span><span class="sxs-lookup"><span data-stu-id="cd696-104">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd696-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cd696-105">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd696-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cd696-106">Parameters</span></span>  

 `cbSize`  
 <span data-ttu-id="cd696-107">окне Размер (в байтах) текущего запроса на выделение памяти.</span><span class="sxs-lookup"><span data-stu-id="cd696-107">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="cd696-108">окне Одно из значений [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) , указывающее влияние сбоя выделения.</span><span class="sxs-lookup"><span data-stu-id="cd696-108">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="cd696-109">заполняет Указатель на выделенную память или значение null, если не удалось завершить запрос.</span><span class="sxs-lookup"><span data-stu-id="cd696-109">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd696-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cd696-110">Return Value</span></span>  
  
|<span data-ttu-id="cd696-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd696-111">HRESULT</span></span>|<span data-ttu-id="cd696-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="cd696-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd696-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd696-113">S_OK</span></span>|<span data-ttu-id="cd696-114">`Alloc` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="cd696-114">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="cd696-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cd696-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cd696-116">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="cd696-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cd696-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cd696-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cd696-118">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="cd696-118">The call timed out.</span></span>|  
|<span data-ttu-id="cd696-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cd696-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cd696-120">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="cd696-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cd696-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cd696-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cd696-122">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="cd696-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cd696-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cd696-123">E_FAIL</span></span>|<span data-ttu-id="cd696-124">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="cd696-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cd696-125">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="cd696-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cd696-126">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cd696-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cd696-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cd696-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cd696-128">Недостаточно памяти для завершения запроса на выделение.</span><span class="sxs-lookup"><span data-stu-id="cd696-128">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd696-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="cd696-129">Remarks</span></span>  

 <span data-ttu-id="cd696-130">Среда CLR получает указатель интерфейса на `IHostMalloc` экземпляр, вызывая метод [IHostMemoryManager:: CreateMalloc](ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cd696-130">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd696-131">Требования</span><span class="sxs-lookup"><span data-stu-id="cd696-131">Requirements</span></span>  

 <span data-ttu-id="cd696-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd696-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd696-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cd696-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd696-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd696-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd696-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd696-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd696-136">См. также</span><span class="sxs-lookup"><span data-stu-id="cd696-136">See also</span></span>

- [<span data-ttu-id="cd696-137">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="cd696-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="cd696-138">Интерфейс IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="cd696-138">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
