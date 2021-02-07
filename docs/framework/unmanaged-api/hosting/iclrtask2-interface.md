---
description: 'Дополнительные сведения о: интерфейс ICLRTask2'
title: Интерфейс ICLRTask2
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
ms.openlocfilehash: 835b01e1c808c071e9393c5117d5e38415ec8eba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728654"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="3c075-103">Интерфейс ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="3c075-103">ICLRTask2 Interface</span></span>

<span data-ttu-id="3c075-104">Предоставляет все функциональные возможности интерфейса [ICLRTask](iclrtask-interface.md) ; Кроме того, предоставляет методы, которые позволяют задерживать прерывания потока в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="3c075-104">Provides all the functionality of the [ICLRTask](iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c075-105">Методы</span><span class="sxs-lookup"><span data-stu-id="3c075-105">Methods</span></span>  
  
|<span data-ttu-id="3c075-106">Метод</span><span class="sxs-lookup"><span data-stu-id="3c075-106">Method</span></span>|<span data-ttu-id="3c075-107">Описание</span><span class="sxs-lookup"><span data-stu-id="3c075-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c075-108">Метод BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="3c075-108">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="3c075-109">Откладывает запросы на прерывание нового потока в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="3c075-109">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="3c075-110">Метод EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="3c075-110">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="3c075-111">Разрешает новые или ожидающие запросы на прерывание потока в результате прерывания потока в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="3c075-111">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c075-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="3c075-112">Remarks</span></span>  

 <span data-ttu-id="3c075-113">`ICLRTask2`Интерфейс наследует `ICLRTask` интерфейс и добавляет методы, позволяющие узлу откладывать прерывания потока, чтобы защитить область кода, которая не должна завершаться ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3c075-113">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="3c075-114">Вызов `BeginPreventAsyncAbort` увеличивает счетчик прерывания задержки потока для текущего потока и вызывает метод `EndPreventAsyncAbort` декремента.</span><span class="sxs-lookup"><span data-stu-id="3c075-114">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="3c075-115">Вызовы `BeginPreventAsyncAbort` и `EndPreventAsyncAbort` могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="3c075-115">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="3c075-116">Пока значение счетчика больше нуля, прерывания потока для текущего потока откладываются.</span><span class="sxs-lookup"><span data-stu-id="3c075-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="3c075-117">Если вызовы `BeginPreventAsyncAbort` и `EndPreventAsyncAbort` не являются парными, то можно достичь состояния, в котором прерывания потока не могут быть доставлены в текущий поток.</span><span class="sxs-lookup"><span data-stu-id="3c075-117">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="3c075-118">Задержка не учитывается для потока, который прерывает работу.</span><span class="sxs-lookup"><span data-stu-id="3c075-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="3c075-119">Функциональные возможности, предоставляемые этой функцией, используются внутри виртуальной машины (ВМ).</span><span class="sxs-lookup"><span data-stu-id="3c075-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="3c075-120">Неправильное использование этих методов может привести к неопределенному поведению в виртуальной машине.</span><span class="sxs-lookup"><span data-stu-id="3c075-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="3c075-121">Например, при вызове `EndPreventAsyncAbort` без первого вызова `BeginPreventAsyncAbort` значение счетчика может равняться нулю, когда виртуальная машина ранее увеличила ее.</span><span class="sxs-lookup"><span data-stu-id="3c075-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="3c075-122">Аналогично, внутренний счетчик не проверяется на переполнение.</span><span class="sxs-lookup"><span data-stu-id="3c075-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="3c075-123">Если он превышает его предельное значение, так как он увеличивается как узлом, так и виртуальной машиной, результирующее поведение не определено.</span><span class="sxs-lookup"><span data-stu-id="3c075-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="3c075-124">Сведения о членах, унаследованных от `ICLRTask` и о других применениях этого интерфейса, см. в разделе интерфейс [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3c075-124">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c075-125">Требования</span><span class="sxs-lookup"><span data-stu-id="3c075-125">Requirements</span></span>  

 <span data-ttu-id="3c075-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c075-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c075-127">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3c075-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c075-128">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c075-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c075-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c075-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c075-130">См. также</span><span class="sxs-lookup"><span data-stu-id="3c075-130">See also</span></span>

- [<span data-ttu-id="3c075-131">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="3c075-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="3c075-132">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="3c075-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="3c075-133">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="3c075-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="3c075-134">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="3c075-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="3c075-135">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="3c075-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
