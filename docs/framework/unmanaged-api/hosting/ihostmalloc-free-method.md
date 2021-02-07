---
description: 'Дополнительные сведения о методе: IHostMAlloc:: Free'
title: Метод IHostMAlloc::Free
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
ms.openlocfilehash: 097e2e95b6dfb9d6a1bae68f9e0455a96383159e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708207"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="74b8b-103">Метод IHostMAlloc::Free</span><span class="sxs-lookup"><span data-stu-id="74b8b-103">IHostMAlloc::Free Method</span></span>

<span data-ttu-id="74b8b-104">Освобождает память, выделенную с помощью функции [Alloc](ihostmalloc-alloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="74b8b-104">Frees memory that was allocated by using the [Alloc](ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74b8b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="74b8b-105">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74b8b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="74b8b-106">Parameters</span></span>  

 `pMem`  
 <span data-ttu-id="74b8b-107">окне Указатель на память, которую необходимо освободить.</span><span class="sxs-lookup"><span data-stu-id="74b8b-107">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74b8b-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="74b8b-108">Return Value</span></span>  
  
|<span data-ttu-id="74b8b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74b8b-109">HRESULT</span></span>|<span data-ttu-id="74b8b-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="74b8b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74b8b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="74b8b-111">S_OK</span></span>|<span data-ttu-id="74b8b-112">`Free` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="74b8b-112">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="74b8b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="74b8b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="74b8b-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="74b8b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="74b8b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="74b8b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="74b8b-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="74b8b-116">The call timed out.</span></span>|  
|<span data-ttu-id="74b8b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="74b8b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="74b8b-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="74b8b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="74b8b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="74b8b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="74b8b-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="74b8b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="74b8b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="74b8b-121">E_FAIL</span></span>|<span data-ttu-id="74b8b-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="74b8b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="74b8b-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="74b8b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="74b8b-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="74b8b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="74b8b-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="74b8b-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="74b8b-126">Предпринята попытка освободить память, которая не была выделена через узел.</span><span class="sxs-lookup"><span data-stu-id="74b8b-126">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74b8b-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="74b8b-127">Remarks</span></span>  

 <span data-ttu-id="74b8b-128">Если `pMem` параметр ссылается на область памяти, которая не была выделена с помощью вызова `Alloc` , узел должен возвращать HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="74b8b-128">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74b8b-129">Требования</span><span class="sxs-lookup"><span data-stu-id="74b8b-129">Requirements</span></span>  

 <span data-ttu-id="74b8b-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74b8b-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74b8b-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="74b8b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74b8b-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74b8b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74b8b-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74b8b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b8b-134">См. также</span><span class="sxs-lookup"><span data-stu-id="74b8b-134">See also</span></span>

- [<span data-ttu-id="74b8b-135">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="74b8b-135">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="74b8b-136">Интерфейс IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="74b8b-136">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
