---
description: 'Дополнительные сведения о методе: IHostMemoryManager:: VirtualQuery'
title: Метод IHostMemoryManager::VirtualQuery
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
ms.openlocfilehash: 8518ef71ad7d493fa04d4e2321f1f90ef8ecd18d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707556"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="1efe2-103">Метод IHostMemoryManager::VirtualQuery</span><span class="sxs-lookup"><span data-stu-id="1efe2-103">IHostMemoryManager::VirtualQuery Method</span></span>

<span data-ttu-id="1efe2-104">Служит логической оболочкой для соответствующей функции Win32.</span><span class="sxs-lookup"><span data-stu-id="1efe2-104">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="1efe2-105">Реализация Win32 `VirtualQuery` извлекает сведения о диапазоне страниц в виртуальном адресном пространстве вызывающего процесса.</span><span class="sxs-lookup"><span data-stu-id="1efe2-105">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1efe2-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1efe2-106">Syntax</span></span>  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1efe2-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="1efe2-107">Parameters</span></span>  

 `lpAddress`  
 <span data-ttu-id="1efe2-108">окне Указатель на адрес в виртуальной памяти для запроса.</span><span class="sxs-lookup"><span data-stu-id="1efe2-108">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="1efe2-109">заполняет Указатель на структуру, содержащую сведения о заданной области памяти.</span><span class="sxs-lookup"><span data-stu-id="1efe2-109">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="1efe2-110">окне Размер (в байтах) буфера, на который `lpBuffer` указывает.</span><span class="sxs-lookup"><span data-stu-id="1efe2-110">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="1efe2-111">заполняет Указатель на число байтов, возвращенных информационным буфером.</span><span class="sxs-lookup"><span data-stu-id="1efe2-111">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1efe2-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1efe2-112">Return Value</span></span>  
  
|<span data-ttu-id="1efe2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1efe2-113">HRESULT</span></span>|<span data-ttu-id="1efe2-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="1efe2-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1efe2-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1efe2-115">S_OK</span></span>|<span data-ttu-id="1efe2-116">`VirtualQuery` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="1efe2-116">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="1efe2-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1efe2-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1efe2-118">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="1efe2-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1efe2-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1efe2-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1efe2-120">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="1efe2-120">The call timed out.</span></span>|  
|<span data-ttu-id="1efe2-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1efe2-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1efe2-122">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="1efe2-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1efe2-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1efe2-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1efe2-124">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="1efe2-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1efe2-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1efe2-125">E_FAIL</span></span>|<span data-ttu-id="1efe2-126">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="1efe2-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1efe2-127">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="1efe2-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1efe2-128">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1efe2-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1efe2-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="1efe2-129">Remarks</span></span>  

 <span data-ttu-id="1efe2-130">`VirtualQuery` предоставляет сведения о диапазоне страниц в виртуальном адресном пространстве вызывающего процесса.</span><span class="sxs-lookup"><span data-stu-id="1efe2-130">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="1efe2-131">Эта реализация задает для параметра значение, `pResult` равное числу байтов, возвращаемых в информационном буфере, и возвращает значение HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1efe2-131">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="1efe2-132">В функции Win32 `VirtualQuery` возвращаемое значение — это размер буфера.</span><span class="sxs-lookup"><span data-stu-id="1efe2-132">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="1efe2-133">Дополнительные сведения см. в документации по платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="1efe2-133">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1efe2-134">Реализация операционной системы не вызывает `VirtualQuery` взаимоблокировок и может выполняться до завершения с помощью случайных потоков, приостановленных в пользовательском коде.</span><span class="sxs-lookup"><span data-stu-id="1efe2-134">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="1efe2-135">При реализации размещенной версии этого метода следует соблюдать осторожность.</span><span class="sxs-lookup"><span data-stu-id="1efe2-135">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1efe2-136">Требования</span><span class="sxs-lookup"><span data-stu-id="1efe2-136">Requirements</span></span>  

 <span data-ttu-id="1efe2-137">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1efe2-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1efe2-138">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1efe2-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1efe2-139">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1efe2-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1efe2-140">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1efe2-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1efe2-141">См. также</span><span class="sxs-lookup"><span data-stu-id="1efe2-141">See also</span></span>

- [<span data-ttu-id="1efe2-142">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="1efe2-142">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
