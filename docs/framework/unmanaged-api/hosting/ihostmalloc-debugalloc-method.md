---
description: 'Дополнительные сведения о методе: IHostMAlloc::D Ебугаллок'
title: Метод IHostMAlloc::DebugAlloc
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: f94ff0d6cc1e25daee12c67c38167f7f14829510
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708220"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="ecd57-103">Метод IHostMAlloc::DebugAlloc</span><span class="sxs-lookup"><span data-stu-id="ecd57-103">IHostMAlloc::DebugAlloc Method</span></span>

<span data-ttu-id="ecd57-104">Запрашивает, что узел выделяет указанный объем памяти из кучи, и дополнительно следит за местом выделения памяти.</span><span class="sxs-lookup"><span data-stu-id="ecd57-104">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecd57-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ecd57-105">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecd57-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ecd57-106">Parameters</span></span>  

 `cbSize`  
 <span data-ttu-id="ecd57-107">окне Размер (в байтах) текущего запроса на выделение памяти.</span><span class="sxs-lookup"><span data-stu-id="ecd57-107">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="ecd57-108">окне Одно из значений [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) , указывающее влияние сбоя выделения.</span><span class="sxs-lookup"><span data-stu-id="ecd57-108">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="ecd57-109">окне Файл исходного кода отлаживаемого объекта.</span><span class="sxs-lookup"><span data-stu-id="ecd57-109">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="ecd57-110">окне Номер строки, в `pszFileName` которой было запрошено выделение.</span><span class="sxs-lookup"><span data-stu-id="ecd57-110">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="ecd57-111">заполняет Указатель на выделенную память или значение null, если не удалось завершить запрос.</span><span class="sxs-lookup"><span data-stu-id="ecd57-111">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecd57-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ecd57-112">Return Value</span></span>  
  
|<span data-ttu-id="ecd57-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecd57-113">HRESULT</span></span>|<span data-ttu-id="ecd57-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="ecd57-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecd57-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecd57-115">S_OK</span></span>|<span data-ttu-id="ecd57-116">`DebugAlloc` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="ecd57-116">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="ecd57-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecd57-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecd57-118">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="ecd57-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecd57-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecd57-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecd57-120">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="ecd57-120">The call timed out.</span></span>|  
|<span data-ttu-id="ecd57-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecd57-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecd57-122">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="ecd57-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecd57-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecd57-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecd57-124">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="ecd57-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecd57-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecd57-125">E_FAIL</span></span>|<span data-ttu-id="ecd57-126">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="ecd57-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecd57-127">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="ecd57-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecd57-128">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ecd57-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ecd57-129">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ecd57-129">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ecd57-130">Недостаточно памяти для завершения запроса на выделение.</span><span class="sxs-lookup"><span data-stu-id="ecd57-130">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecd57-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="ecd57-131">Remarks</span></span>  

 <span data-ttu-id="ecd57-132">Среда CLR получает указатель интерфейса на экземпляр [IHostMalloc](ihostmalloc-interface.md) , вызывая метод [IHostMemoryManager:: CreateMalloc](ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ecd57-132">The CLR gets an interface pointer to an [IHostMalloc](ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="ecd57-133">`DebugAlloc` позволяет среде выполнения получать сведения о файле кода для использования во время отладки.</span><span class="sxs-lookup"><span data-stu-id="ecd57-133">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecd57-134">Требования</span><span class="sxs-lookup"><span data-stu-id="ecd57-134">Requirements</span></span>  

 <span data-ttu-id="ecd57-135">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecd57-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecd57-136">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ecd57-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecd57-137">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecd57-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecd57-138">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecd57-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd57-139">См. также</span><span class="sxs-lookup"><span data-stu-id="ecd57-139">See also</span></span>

- [<span data-ttu-id="ecd57-140">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="ecd57-140">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="ecd57-141">Интерфейс IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="ecd57-141">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
