---
description: 'Дополнительные сведения о методе: IHostMemoryManager:: Жетмеморилоад'
title: Метод IHostMemoryManager::GetMemoryLoad
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
ms.openlocfilehash: 82288e6a705b014c2768c75e15376f7e6a0af428
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707850"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="b3842-103">Метод IHostMemoryManager::GetMemoryLoad</span><span class="sxs-lookup"><span data-stu-id="b3842-103">IHostMemoryManager::GetMemoryLoad Method</span></span>

<span data-ttu-id="b3842-104">Возвращает объем физической памяти, используемой в данный момент, и, следовательно, недоступен, сообщаемый узлом.</span><span class="sxs-lookup"><span data-stu-id="b3842-104">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3842-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b3842-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3842-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b3842-106">Parameters</span></span>  

 `pMemoryLoad`  
 <span data-ttu-id="b3842-107">заполняет Указатель на Приблизительный процент общего объема физической памяти, который используется в данный момент.</span><span class="sxs-lookup"><span data-stu-id="b3842-107">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="b3842-108">заполняет Указатель на число байтов, доступных для среды CLR.</span><span class="sxs-lookup"><span data-stu-id="b3842-108">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3842-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b3842-109">Return Value</span></span>  
  
|<span data-ttu-id="b3842-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3842-110">HRESULT</span></span>|<span data-ttu-id="b3842-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="b3842-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3842-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3842-112">S_OK</span></span>|<span data-ttu-id="b3842-113">`GetMemoryLoad` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="b3842-113">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="b3842-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b3842-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b3842-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="b3842-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b3842-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b3842-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b3842-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="b3842-117">The call timed out.</span></span>|  
|<span data-ttu-id="b3842-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3842-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b3842-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="b3842-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b3842-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b3842-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b3842-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="b3842-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b3842-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b3842-122">E_FAIL</span></span>|<span data-ttu-id="b3842-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="b3842-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b3842-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="b3842-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b3842-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b3842-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3842-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="b3842-126">Remarks</span></span>  

 <span data-ttu-id="b3842-127">`GetMemoryLoad` заключает в оболочку `GlobalMemoryStatus` функцию Win32.</span><span class="sxs-lookup"><span data-stu-id="b3842-127">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="b3842-128">Значение `pMemoryLoad` является эквивалентом `dwMemoryLoad` поля в `MEMORYSTATUS` структуре, возвращаемой из `GlobalMemoryStatus` .</span><span class="sxs-lookup"><span data-stu-id="b3842-128">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="b3842-129">Среда выполнения использует возвращаемое значение в качестве эвристики для сборщика мусора.</span><span class="sxs-lookup"><span data-stu-id="b3842-129">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="b3842-130">Например, если основное приложение сообщает о том, что используется большая часть памяти, сборщик мусора может выбрать сбор данных из нескольких поколений, чтобы увеличить объем памяти, который потенциально может стать доступным.</span><span class="sxs-lookup"><span data-stu-id="b3842-130">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3842-131">Требования</span><span class="sxs-lookup"><span data-stu-id="b3842-131">Requirements</span></span>  

 <span data-ttu-id="b3842-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3842-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3842-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b3842-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3842-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3842-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3842-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3842-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3842-136">См. также</span><span class="sxs-lookup"><span data-stu-id="b3842-136">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="b3842-137">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="b3842-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
