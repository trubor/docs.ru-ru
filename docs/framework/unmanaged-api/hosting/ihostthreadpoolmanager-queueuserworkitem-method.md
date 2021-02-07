---
description: 'Дополнительные сведения о методе: IHostThreadPoolManager:: QueueUserWorkItem'
title: Метод IHostThreadPoolManager::QueueUserWorkItem
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.QueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type:
- apiref
ms.openlocfilehash: edfbf5cfb34473a5fd920307981237fd5deab9aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753787"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="295f1-103">Метод IHostThreadPoolManager::QueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="295f1-103">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>

<span data-ttu-id="295f1-104">Ставит в очередь функцию для выполнения и указывает объект, содержащий данные, которые будут использоваться этой функцией.</span><span class="sxs-lookup"><span data-stu-id="295f1-104">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="295f1-105">Функция выполняется, когда поток станет доступным.</span><span class="sxs-lookup"><span data-stu-id="295f1-105">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="295f1-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="295f1-106">Syntax</span></span>  
  
```cpp  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="295f1-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="295f1-107">Parameters</span></span>  

 `Function`  
 <span data-ttu-id="295f1-108">окне Указатель функции, представляющий функцию для выполнения.</span><span class="sxs-lookup"><span data-stu-id="295f1-108">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="295f1-109">окне Объект, содержащий данные, которые будут использоваться `Function` .</span><span class="sxs-lookup"><span data-stu-id="295f1-109">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="295f1-110">окне Одно из значений флагов, определенное для `QueueUserWorkItem` метода Win32, которое управляет выполнением.</span><span class="sxs-lookup"><span data-stu-id="295f1-110">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="295f1-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="295f1-111">Return Value</span></span>  
  
|<span data-ttu-id="295f1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="295f1-112">HRESULT</span></span>|<span data-ttu-id="295f1-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="295f1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="295f1-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="295f1-114">S_OK</span></span>|<span data-ttu-id="295f1-115">`QueueUserWorkItem` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="295f1-115">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="295f1-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="295f1-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="295f1-117">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="295f1-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="295f1-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="295f1-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="295f1-119">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="295f1-119">The call timed out.</span></span>|  
|<span data-ttu-id="295f1-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="295f1-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="295f1-121">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="295f1-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="295f1-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="295f1-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="295f1-123">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="295f1-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="295f1-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="295f1-124">E_FAIL</span></span>|<span data-ttu-id="295f1-125">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="295f1-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="295f1-126">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="295f1-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="295f1-127">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="295f1-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="295f1-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="295f1-128">Remarks</span></span>  

 <span data-ttu-id="295f1-129">`QueueUserWorkItem` помещает рабочий элемент в очередь в рабочий поток в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="295f1-129">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="295f1-130">Его сигнатура и типы параметров идентичны параметрам соответствующей функции Win32, которая имеет то же имя.</span><span class="sxs-lookup"><span data-stu-id="295f1-130">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="295f1-131">Дополнительные сведения см. в документации по платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="295f1-131">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="295f1-132">Требования</span><span class="sxs-lookup"><span data-stu-id="295f1-132">Requirements</span></span>  

 <span data-ttu-id="295f1-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="295f1-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="295f1-134">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="295f1-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="295f1-135">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="295f1-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="295f1-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="295f1-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="295f1-137">См. также</span><span class="sxs-lookup"><span data-stu-id="295f1-137">See also</span></span>

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="295f1-138">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="295f1-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
