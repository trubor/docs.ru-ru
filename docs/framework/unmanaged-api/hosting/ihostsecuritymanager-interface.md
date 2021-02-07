---
description: 'Дополнительные сведения о: интерфейс IHostSecurityManager'
title: Интерфейс IHostSecurityManager
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
ms.openlocfilehash: 76ba26443fa2a4e65459dd073eb6d22031548112
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671547"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="764f3-103">Интерфейс IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="764f3-103">IHostSecurityManager Interface</span></span>

<span data-ttu-id="764f3-104">Предоставляет методы, позволяющие получить доступ к контексту безопасности выполняющегося потока и управлять им.</span><span class="sxs-lookup"><span data-stu-id="764f3-104">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="764f3-105">Методы</span><span class="sxs-lookup"><span data-stu-id="764f3-105">Methods</span></span>  
  
|<span data-ttu-id="764f3-106">Метод</span><span class="sxs-lookup"><span data-stu-id="764f3-106">Method</span></span>|<span data-ttu-id="764f3-107">Описание</span><span class="sxs-lookup"><span data-stu-id="764f3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="764f3-108">Метод GetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="764f3-108">GetSecurityContext Method</span></span>](ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="764f3-109">Возвращает запрошенный [IHostSecurityContext](ihostsecuritycontext-interface.md) из узла.</span><span class="sxs-lookup"><span data-stu-id="764f3-109">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="764f3-110">Метод ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="764f3-110">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="764f3-111">Запрашивает выполнение кода с использованием учетных данных удостоверения текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="764f3-111">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="764f3-112">Метод OpenThreadToken</span><span class="sxs-lookup"><span data-stu-id="764f3-112">OpenThreadToken Method</span></span>](ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="764f3-113">Открывает маркер доступа на уровне пользователей, связанный с текущим потоком.</span><span class="sxs-lookup"><span data-stu-id="764f3-113">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="764f3-114">Метод RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="764f3-114">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="764f3-115">Завершает олицетворение текущего удостоверения пользователя и возвращает исходный маркер потока.</span><span class="sxs-lookup"><span data-stu-id="764f3-115">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="764f3-116">Метод SetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="764f3-116">SetSecurityContext Method</span></span>](ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="764f3-117">Задает контекст безопасности для выполняющегося в данный момент потока.</span><span class="sxs-lookup"><span data-stu-id="764f3-117">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="764f3-118">Метод SetThreadToken</span><span class="sxs-lookup"><span data-stu-id="764f3-118">SetThreadToken Method</span></span>](ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="764f3-119">Задает обработчик для текущего выполняющегося потока.</span><span class="sxs-lookup"><span data-stu-id="764f3-119">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="764f3-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="764f3-120">Remarks</span></span>  

 <span data-ttu-id="764f3-121">Узел может управлять доступом кода к маркерам потоков как средой CLR, так и кодом пользователя.</span><span class="sxs-lookup"><span data-stu-id="764f3-121">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="764f3-122">Он также может гарантировать, что полные сведения о контексте безопасности передаются по асинхронным операциям или кодовым точкам с ограниченным доступом к коду.</span><span class="sxs-lookup"><span data-stu-id="764f3-122">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="764f3-123">`IHostSecurityContext` инкапсулирует эти сведения о контексте безопасности, которые непрозрачны для среды CLR.</span><span class="sxs-lookup"><span data-stu-id="764f3-123">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="764f3-124">Среда CLR внутренне обрабатывает контекст управляемого потока.</span><span class="sxs-lookup"><span data-stu-id="764f3-124">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="764f3-125">Он запрашивает особенности конкретного процесса `IHostSecurityManager` в следующих ситуациях:</span><span class="sxs-lookup"><span data-stu-id="764f3-125">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="764f3-126">В потоке метода завершения во время выполнения метода завершения.</span><span class="sxs-lookup"><span data-stu-id="764f3-126">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="764f3-127">Во время выполнения конструктора класса и модуля.</span><span class="sxs-lookup"><span data-stu-id="764f3-127">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="764f3-128">В асинхронных точках в рабочем потоке при вызове метода [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) .</span><span class="sxs-lookup"><span data-stu-id="764f3-128">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="764f3-129">При обслуживании портов завершения ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="764f3-129">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="764f3-130">Требования</span><span class="sxs-lookup"><span data-stu-id="764f3-130">Requirements</span></span>  

 <span data-ttu-id="764f3-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="764f3-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="764f3-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="764f3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="764f3-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="764f3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="764f3-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="764f3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764f3-135">См. также</span><span class="sxs-lookup"><span data-stu-id="764f3-135">See also</span></span>

- [<span data-ttu-id="764f3-136">Интерфейс IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="764f3-136">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="764f3-137">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="764f3-137">Hosting Interfaces</span></span>](hosting-interfaces.md)
