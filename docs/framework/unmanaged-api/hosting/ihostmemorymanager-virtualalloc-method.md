---
description: 'Дополнительные сведения о методе: IHostMemoryManager:: VirtualAlloc'
title: Метод IHostMemoryManager::VirtualAlloc
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
ms.openlocfilehash: 28682aea5e6e7951b3b8f0a9af946a3f3828601b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707856"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="7b3a5-103">Метод IHostMemoryManager::VirtualAlloc</span><span class="sxs-lookup"><span data-stu-id="7b3a5-103">IHostMemoryManager::VirtualAlloc Method</span></span>

<span data-ttu-id="7b3a5-104">Служит логической оболочкой для соответствующей функции Win32.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-104">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="7b3a5-105">Реализация Win32 `VirtualAlloc` резервирует или фиксирует область страниц в виртуальном адресном пространстве вызывающего процесса.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-105">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b3a5-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7b3a5-106">Syntax</span></span>  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b3a5-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="7b3a5-107">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="7b3a5-108">окне Указатель на начальный адрес области для выделения.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-108">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="7b3a5-109">окне Размер области в байтах.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-109">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="7b3a5-110">окне Тип выделения памяти.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-110">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="7b3a5-111">окне Защита памяти для выделяемого региона страниц.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-111">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="7b3a5-112">окне Значение [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) , указывающее влияние сбоя выделения.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-112">[in] An [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="7b3a5-113">заполняет Указатель на начальный адрес выделенной памяти или значение null, если запрос не может быть удовлетворен.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-113">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b3a5-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7b3a5-114">Return Value</span></span>  
  
|<span data-ttu-id="7b3a5-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b3a5-115">HRESULT</span></span>|<span data-ttu-id="7b3a5-116">Описание:</span><span class="sxs-lookup"><span data-stu-id="7b3a5-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b3a5-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b3a5-117">S_OK</span></span>|<span data-ttu-id="7b3a5-118">`VirtualAlloc` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-118">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="7b3a5-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7b3a5-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7b3a5-120">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7b3a5-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7b3a5-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7b3a5-122">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-122">The call timed out.</span></span>|  
|<span data-ttu-id="7b3a5-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7b3a5-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7b3a5-124">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7b3a5-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7b3a5-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7b3a5-126">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7b3a5-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b3a5-127">E_FAIL</span></span>|<span data-ttu-id="7b3a5-128">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7b3a5-129">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7b3a5-130">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7b3a5-131">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7b3a5-131">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7b3a5-132">Недостаточно памяти для завершения запроса на выделение</span><span class="sxs-lookup"><span data-stu-id="7b3a5-132">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b3a5-133">Remarks</span><span class="sxs-lookup"><span data-stu-id="7b3a5-133">Remarks</span></span>  

 <span data-ttu-id="7b3a5-134">Чтобы зарезервировать регион в адресном пространстве процесса, вызовите метод `VirtualAlloc` .</span><span class="sxs-lookup"><span data-stu-id="7b3a5-134">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="7b3a5-135">`pAddress`Параметр содержит начальный адрес требуемого блока памяти.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-135">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="7b3a5-136">Обычно этот параметр имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-136">This parameter is typically set to null.</span></span> <span data-ttu-id="7b3a5-137">Операционная система хранит записи доступных диапазонов свободных адресов для вашего процесса.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-137">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="7b3a5-138">`pAddress`Значение NULL предписывает системе зарезервировать регион везде, где он видит.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-138">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="7b3a5-139">Кроме того, можно указать конкретный начальный адрес для блока памяти.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-139">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="7b3a5-140">В обоих случаях выходной параметр возвращается в `ppMem` виде указателя на выделенную память.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-140">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="7b3a5-141">Сама функция возвращает значение HRESULT.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-141">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="7b3a5-142">Функция Win32 `VirtualAlloc` не имеет `ppMem` параметра и вместо нее возвращает указатель на выделенную память.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-142">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="7b3a5-143">Дополнительные сведения см. в документации по платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="7b3a5-143">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b3a5-144">Требования</span><span class="sxs-lookup"><span data-stu-id="7b3a5-144">Requirements</span></span>  

 <span data-ttu-id="7b3a5-145">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b3a5-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b3a5-146">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7b3a5-146">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b3a5-147">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7b3a5-147">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b3a5-148">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b3a5-148">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b3a5-149">См. также</span><span class="sxs-lookup"><span data-stu-id="7b3a5-149">See also</span></span>

- [<span data-ttu-id="7b3a5-150">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="7b3a5-150">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
