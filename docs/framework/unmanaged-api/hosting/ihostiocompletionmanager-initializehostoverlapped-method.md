---
description: 'Дополнительные сведения о методе: IHostIoCompletionManager:: Инитиализехостоверлаппед'
title: Метод IHostIoCompletionManager::InitializeHostOverlapped
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
ms.openlocfilehash: 10be7edb67143937dec6efc6e35466466374d32d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708467"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="730ed-103">Метод IHostIoCompletionManager::InitializeHostOverlapped</span><span class="sxs-lookup"><span data-stu-id="730ed-103">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>

<span data-ttu-id="730ed-104">Предоставляет узлу возможность инициализировать любые пользовательские данные, добавляемые в `OVERLAPPED` структуру Win32, которая используется для асинхронных запросов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="730ed-104">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="730ed-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="730ed-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="730ed-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="730ed-106">Parameters</span></span>  

 `pvOverlapped`  
 <span data-ttu-id="730ed-107">окне Указатель на структуру Win32, `OVERLAPPED` которая будет включена в запрос ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="730ed-107">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="730ed-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="730ed-108">Return Value</span></span>  
  
|<span data-ttu-id="730ed-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="730ed-109">HRESULT</span></span>|<span data-ttu-id="730ed-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="730ed-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="730ed-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="730ed-111">S_OK</span></span>|<span data-ttu-id="730ed-112">`InitializeHostOverlapped` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="730ed-112">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="730ed-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="730ed-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="730ed-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="730ed-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="730ed-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="730ed-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="730ed-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="730ed-116">The call timed out.</span></span>|  
|<span data-ttu-id="730ed-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="730ed-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="730ed-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="730ed-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="730ed-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="730ed-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="730ed-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="730ed-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="730ed-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="730ed-121">E_FAIL</span></span>|<span data-ttu-id="730ed-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="730ed-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="730ed-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="730ed-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="730ed-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="730ed-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="730ed-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="730ed-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="730ed-126">Недостаточно памяти для выделения запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="730ed-126">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="730ed-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="730ed-127">Remarks</span></span>  

 <span data-ttu-id="730ed-128">Функции платформы Windows используют `OVERLAPPED` структуру для хранения состояния асинхронных запросов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="730ed-128">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="730ed-129">Среда CLR вызывает `InitializeHostOverlapped` метод, чтобы предоставить узлу возможность добавлять пользовательские данные в `OVERLAPPED` экземпляр.</span><span class="sxs-lookup"><span data-stu-id="730ed-129">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="730ed-130">Чтобы перейти к началу пользовательского блока данных, узлы должны задать смещение до размера `OVERLAPPED` структуры ( `sizeof(OVERLAPPED)` ).</span><span class="sxs-lookup"><span data-stu-id="730ed-130">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="730ed-131">Возвращаемое значение E_OUTOFMEMORY указывает, что узлу не удалось инициализировать свои пользовательские данные.</span><span class="sxs-lookup"><span data-stu-id="730ed-131">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="730ed-132">В этом случае среда CLR сообщает об ошибке и вызове завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="730ed-132">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="730ed-133">Требования</span><span class="sxs-lookup"><span data-stu-id="730ed-133">Requirements</span></span>  

 <span data-ttu-id="730ed-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="730ed-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="730ed-135">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="730ed-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="730ed-136">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="730ed-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="730ed-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="730ed-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="730ed-138">См. также</span><span class="sxs-lookup"><span data-stu-id="730ed-138">See also</span></span>

- [<span data-ttu-id="730ed-139">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="730ed-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="730ed-140">Метод GetHostOverlappedSize</span><span class="sxs-lookup"><span data-stu-id="730ed-140">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="730ed-141">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="730ed-141">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
