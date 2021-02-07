---
description: 'Дополнительные сведения о методе: IHostMemoryManager:: VirtualFree'
title: Метод IHostMemoryManager::VirtualFree
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
ms.openlocfilehash: 987661ce1b7bfd08f757f53082313b8eb60ff282
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707546"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="17c75-103">Метод IHostMemoryManager::VirtualFree</span><span class="sxs-lookup"><span data-stu-id="17c75-103">IHostMemoryManager::VirtualFree Method</span></span>

<span data-ttu-id="17c75-104">Служит логической оболочкой для соответствующей функции Win32.</span><span class="sxs-lookup"><span data-stu-id="17c75-104">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="17c75-105">Реализация в Win32 `VirtualFree` выпусков, снятие фиксаций, освобождение и отменяет фиксацию области страниц в виртуальном адресном пространстве вызывающего процесса.</span><span class="sxs-lookup"><span data-stu-id="17c75-105">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17c75-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17c75-106">Syntax</span></span>  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17c75-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="17c75-107">Parameters</span></span>  

 `lpAddress`  
 <span data-ttu-id="17c75-108">окне Указатель на базовый адрес страниц виртуальной памяти, которые должны быть освобождены.</span><span class="sxs-lookup"><span data-stu-id="17c75-108">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="17c75-109">окне Размер (в байтах) области, которая должна быть освобождена.</span><span class="sxs-lookup"><span data-stu-id="17c75-109">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="17c75-110">окне Тип операции освобождения.</span><span class="sxs-lookup"><span data-stu-id="17c75-110">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17c75-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="17c75-111">Return Value</span></span>  
  
|<span data-ttu-id="17c75-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17c75-112">HRESULT</span></span>|<span data-ttu-id="17c75-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="17c75-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17c75-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="17c75-114">S_OK</span></span>|<span data-ttu-id="17c75-115">`VirtualFree` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="17c75-115">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="17c75-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="17c75-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="17c75-117">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="17c75-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="17c75-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="17c75-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="17c75-119">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="17c75-119">The call timed out.</span></span>|  
|<span data-ttu-id="17c75-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="17c75-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="17c75-121">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="17c75-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="17c75-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="17c75-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="17c75-123">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="17c75-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="17c75-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="17c75-124">E_FAIL</span></span>|<span data-ttu-id="17c75-125">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="17c75-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="17c75-126">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="17c75-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="17c75-127">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="17c75-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="17c75-128">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="17c75-128">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="17c75-129">Предпринята попытка освободить память, которая не была выделена через узел.</span><span class="sxs-lookup"><span data-stu-id="17c75-129">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17c75-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="17c75-130">Remarks</span></span>  

 <span data-ttu-id="17c75-131">`VirtualFree` Освобождает страницы виртуальной памяти, связанные с `lpAddress` параметром, с помощью предыдущего вызова функции [IHostMemoryManager:: VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="17c75-131">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="17c75-132">Пытается освободить память, которая не была выделена с помощью узла, должна возвращать HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="17c75-132">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="17c75-133">Семантика идентична реализации Win32 `VirtualFree` .</span><span class="sxs-lookup"><span data-stu-id="17c75-133">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="17c75-134">Дополнительные сведения см. в документации по платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="17c75-134">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17c75-135">Требования</span><span class="sxs-lookup"><span data-stu-id="17c75-135">Requirements</span></span>  

 <span data-ttu-id="17c75-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17c75-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17c75-137">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17c75-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17c75-138">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17c75-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17c75-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17c75-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17c75-140">См. также</span><span class="sxs-lookup"><span data-stu-id="17c75-140">See also</span></span>

- [<span data-ttu-id="17c75-141">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="17c75-141">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="17c75-142">Интерфейс IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="17c75-142">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
