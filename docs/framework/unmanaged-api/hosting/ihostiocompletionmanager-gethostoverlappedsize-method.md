---
description: 'Дополнительные сведения о методе: IHostIoCompletionManager:: Жесостоверлаппедсизе'
title: Метод IHostIoCompletionManager::GetHostOverlappedSize
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
ms.openlocfilehash: 2a2ebe1da82c5702269b634eadfe98b72739e3df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708571"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="5b18c-103">Метод IHostIoCompletionManager::GetHostOverlappedSize</span><span class="sxs-lookup"><span data-stu-id="5b18c-103">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>

<span data-ttu-id="5b18c-104">Возвращает размер любых пользовательских данных, которые узел намеревается добавить к запросам ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="5b18c-104">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b18c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5b18c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b18c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5b18c-106">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="5b18c-107">заполняет Указатель на число байтов, которое должна выделить среда CLR в дополнение к размеру `OVERLAPPED` объекта Win32.</span><span class="sxs-lookup"><span data-stu-id="5b18c-107">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b18c-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5b18c-108">Return Value</span></span>  
  
|<span data-ttu-id="5b18c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b18c-109">HRESULT</span></span>|<span data-ttu-id="5b18c-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="5b18c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b18c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5b18c-111">S_OK</span></span>|<span data-ttu-id="5b18c-112">`GetHostOverlappedSize` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="5b18c-112">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="5b18c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5b18c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5b18c-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="5b18c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5b18c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5b18c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5b18c-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="5b18c-116">The call timed out.</span></span>|  
|<span data-ttu-id="5b18c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5b18c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5b18c-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="5b18c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5b18c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5b18c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5b18c-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="5b18c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5b18c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5b18c-121">E_FAIL</span></span>|<span data-ttu-id="5b18c-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="5b18c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5b18c-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="5b18c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5b18c-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5b18c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b18c-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="5b18c-125">Remarks</span></span>  

 <span data-ttu-id="5b18c-126">Все асинхронные вызовы операций ввода-вывода в API платформы Windows принимают `OVERLAPPED` объект Win32, который предоставляет такую информацию, как расположение указателя файла.</span><span class="sxs-lookup"><span data-stu-id="5b18c-126">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="5b18c-127">Для поддержания состояния приложения, которые выполняют асинхронные вызовы операций ввода-вывода, обычно добавляют в структуру пользовательские данные.</span><span class="sxs-lookup"><span data-stu-id="5b18c-127">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="5b18c-128">`GetHostOverlappedSize` и [IHostIoCompletionManager:: инитиализехостоверлаппед](ihostiocompletionmanager-initializehostoverlapped-method.md) предоставляют возможность ведущему приложению включать такие пользовательские данные.</span><span class="sxs-lookup"><span data-stu-id="5b18c-128">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="5b18c-129">Среда CLR вызывает `GetHostOverlappedSize` метод, чтобы определить размер пользовательских данных, которые узел намеревается добавить к `OVERLAPPED` объекту.</span><span class="sxs-lookup"><span data-stu-id="5b18c-129">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b18c-130">`GetHostOverlappedSize` вызывается только один раз.</span><span class="sxs-lookup"><span data-stu-id="5b18c-130">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="5b18c-131">Пользовательские данные узла должны иметь одинаковый размер для каждого запроса ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="5b18c-131">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5b18c-132">Размер `OVERLAPPED` самого объекта не включается в значение `pcbSize` .</span><span class="sxs-lookup"><span data-stu-id="5b18c-132">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="5b18c-133">Дополнительные сведения о `OVERLAPPED` структуре см. в документации по платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="5b18c-133">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b18c-134">Требования</span><span class="sxs-lookup"><span data-stu-id="5b18c-134">Requirements</span></span>  

 <span data-ttu-id="5b18c-135">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b18c-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b18c-136">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5b18c-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b18c-137">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b18c-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b18c-138">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b18c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b18c-139">См. также</span><span class="sxs-lookup"><span data-stu-id="5b18c-139">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="5b18c-140">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="5b18c-140">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="5b18c-141">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="5b18c-141">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
