---
description: 'Дополнительные сведения о: интерфейс IHostIoCompletionManager'
title: Интерфейс IHostIoCompletionManager
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
ms.openlocfilehash: 30cb0ecbfd9645bc0374e3570751832d6fa8eced
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708324"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="490c5-103">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="490c5-103">IHostIoCompletionManager Interface</span></span>

<span data-ttu-id="490c5-104">Предоставляет методы, позволяющие среде CLR взаимодействовать с портами завершения ввода-вывода, предоставляемыми узлом.</span><span class="sxs-lookup"><span data-stu-id="490c5-104">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="490c5-105">Методы</span><span class="sxs-lookup"><span data-stu-id="490c5-105">Methods</span></span>  
  
|<span data-ttu-id="490c5-106">Метод</span><span class="sxs-lookup"><span data-stu-id="490c5-106">Method</span></span>|<span data-ttu-id="490c5-107">Описание</span><span class="sxs-lookup"><span data-stu-id="490c5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="490c5-108">Метод Bind</span><span class="sxs-lookup"><span data-stu-id="490c5-108">Bind Method</span></span>](ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="490c5-109">Привязывает маркер к порту завершения ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="490c5-109">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="490c5-110">Метод CloseIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="490c5-110">CloseIoCompletionPort Method</span></span>](ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="490c5-111">Закрывает порт, созданный с помощью предыдущего вызова метода `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="490c5-111">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="490c5-112">Метод CreateIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="490c5-112">CreateIoCompletionPort Method</span></span>](ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="490c5-113">Запрашивает создание узлом нового порта завершения ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="490c5-113">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="490c5-114">Метод GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="490c5-114">GetAvailableThreads Method</span></span>](ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="490c5-115">Возвращает число потоков завершения ввода-вывода, которые в настоящий момент не обрабатывают запросы.</span><span class="sxs-lookup"><span data-stu-id="490c5-115">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="490c5-116">Метод GetHostOverlappedSize</span><span class="sxs-lookup"><span data-stu-id="490c5-116">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="490c5-117">Возвращает размер любых пользовательских данных, которые узел намеревается добавить к запросам ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="490c5-117">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="490c5-118">Метод GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="490c5-118">GetMaxThreads Method</span></span>](ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="490c5-119">Возвращает максимальное число потоков, которое узел может выделить для обслуживания запросов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="490c5-119">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="490c5-120">Метод GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="490c5-120">GetMinThreads Method</span></span>](ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="490c5-121">Возвращает минимальное число потоков, предоставляемых узлом для обслуживания запросов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="490c5-121">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="490c5-122">Метод InitializeHostOverlapped</span><span class="sxs-lookup"><span data-stu-id="490c5-122">InitializeHostOverlapped Method</span></span>](ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="490c5-123">Предоставляет узлу возможность инициализировать любые пользовательские данные о запросе ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="490c5-123">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="490c5-124">Метод SetCLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="490c5-124">SetCLRIoCompletionManager Method</span></span>](ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="490c5-125">Предоставляет узлу указатель интерфейса на экземпляр [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) , РЕАЛИЗУЕМый средой CLR.</span><span class="sxs-lookup"><span data-stu-id="490c5-125">Provides the host with an interface pointer to an [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="490c5-126">Метод SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="490c5-126">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="490c5-127">Задает максимальное число потоков, которое узел запрашивает для обслуживания запросов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="490c5-127">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="490c5-128">Метод SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="490c5-128">SetMinThreads Method</span></span>](ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="490c5-129">Задает минимальное число потоков, которое узел должен выделить при завершении ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="490c5-129">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="490c5-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="490c5-130">Remarks</span></span>  

 <span data-ttu-id="490c5-131">`IHostIoCompletionManager` соответствует `ICLRIoCompletionManager` интерфейсу, реализованному средой CLR.</span><span class="sxs-lookup"><span data-stu-id="490c5-131">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="490c5-132">Среда CLR вызывает методы `IHostIoCompletionManager` для привязки дескрипторов к портам, предоставляемым узлом, и узел вызывает методы `ICLRIoCompletionManager` для сообщения о завершении запросов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="490c5-132">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="490c5-133">Требования</span><span class="sxs-lookup"><span data-stu-id="490c5-133">Requirements</span></span>  

 <span data-ttu-id="490c5-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="490c5-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="490c5-135">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="490c5-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="490c5-136">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="490c5-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="490c5-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="490c5-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="490c5-138">См. также</span><span class="sxs-lookup"><span data-stu-id="490c5-138">See also</span></span>

- [<span data-ttu-id="490c5-139">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="490c5-139">Hosting Interfaces</span></span>](hosting-interfaces.md)
