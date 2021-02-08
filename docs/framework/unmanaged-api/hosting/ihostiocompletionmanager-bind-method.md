---
description: 'Дополнительные сведения о методе: IHostIoCompletionManager:: BIND'
title: Метод IHostIoCompletionManager::Bind
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
ms.openlocfilehash: 2105bf06c23f70588d0c1bc0cd849b8e810d121e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784864"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="d9b75-103">Метод IHostIoCompletionManager::Bind</span><span class="sxs-lookup"><span data-stu-id="d9b75-103">IHostIoCompletionManager::Bind Method</span></span>

<span data-ttu-id="d9b75-104">Привязывает указанный маркер к порту завершения ввода-вывода, созданному предыдущим вызовом метода [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="d9b75-104">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b75-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9b75-105">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9b75-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d9b75-106">Parameters</span></span>  

 `hPort`  
 <span data-ttu-id="d9b75-107">окне Порт завершения ввода-вывода, к которому выполняется привязка `hHandle` .</span><span class="sxs-lookup"><span data-stu-id="d9b75-107">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="d9b75-108">Если значение `hPort` равно null, `hHandle` привязывается к порту завершения ввода-вывода по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d9b75-108">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="d9b75-109">окне Обработчик операционной системы для привязки `hPort` .</span><span class="sxs-lookup"><span data-stu-id="d9b75-109">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9b75-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d9b75-110">Return Value</span></span>  
  
|<span data-ttu-id="d9b75-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9b75-111">HRESULT</span></span>|<span data-ttu-id="d9b75-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="d9b75-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9b75-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9b75-113">S_OK</span></span>|<span data-ttu-id="d9b75-114">`Bind` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="d9b75-114">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="d9b75-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9b75-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9b75-116">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="d9b75-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9b75-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9b75-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9b75-118">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="d9b75-118">The call timed out.</span></span>|  
|<span data-ttu-id="d9b75-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9b75-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9b75-120">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="d9b75-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9b75-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9b75-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9b75-122">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="d9b75-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9b75-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9b75-123">E_FAIL</span></span>|<span data-ttu-id="d9b75-124">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="d9b75-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9b75-125">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="d9b75-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9b75-126">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d9b75-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9b75-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="d9b75-127">Remarks</span></span>  

 <span data-ttu-id="d9b75-128">Порт завершения ввода-вывода создается с помощью вызова `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="d9b75-128">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="d9b75-129">Среда CLR вызывает `Bind` для привязки маркера к этому порту.</span><span class="sxs-lookup"><span data-stu-id="d9b75-129">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9b75-130">По завершении запроса ввода-вывода узел должен вызвать метод [ICLRIoCompletionManager:: OnComplete](iclriocompletionmanager-oncomplete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d9b75-130">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9b75-131">Требования</span><span class="sxs-lookup"><span data-stu-id="d9b75-131">Requirements</span></span>  

 <span data-ttu-id="d9b75-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9b75-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9b75-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d9b75-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9b75-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9b75-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9b75-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9b75-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b75-136">См. также</span><span class="sxs-lookup"><span data-stu-id="d9b75-136">See also</span></span>

- [<span data-ttu-id="d9b75-137">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="d9b75-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
