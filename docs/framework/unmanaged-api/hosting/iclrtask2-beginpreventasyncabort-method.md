---
description: 'Дополнительные сведения о методе: ICLRTask2:: BeginPreventAsyncAbort'
title: Метод ICLRTask2::BeginPreventAsyncAbort
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
ms.openlocfilehash: 1e25cb0e6157d77efc6a04016dc49d9d5d0bf116
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728653"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="8c7ca-103">Метод ICLRTask2::BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="8c7ca-103">ICLRTask2::BeginPreventAsyncAbort Method</span></span>

<span data-ttu-id="8c7ca-104">Откладывает запросы на прерывание нового потока от результирующего прерывания потока в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-104">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c7ca-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8c7ca-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8c7ca-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8c7ca-106">Return Value</span></span>  

 <span data-ttu-id="8c7ca-107">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-107">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8c7ca-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c7ca-108">HRESULT</span></span>|<span data-ttu-id="8c7ca-109">Описание:</span><span class="sxs-lookup"><span data-stu-id="8c7ca-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c7ca-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c7ca-110">S_OK</span></span>|<span data-ttu-id="8c7ca-111">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-111">The method completed successfully.</span></span>|  
|<span data-ttu-id="8c7ca-112">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="8c7ca-112">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="8c7ca-113">Метод был вызван в потоке, который не является текущим потоком.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-113">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c7ca-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="8c7ca-114">Remarks</span></span>  

 <span data-ttu-id="8c7ca-115">При вызове этого метода значение счетчика "задержка — прерывание потока" для текущего потока увеличивается на единицу.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-115">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="8c7ca-116">Вызовы функций `BeginPreventAsyncAbort` и [ICLRTask2:: EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md) могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-116">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="8c7ca-117">Пока значение счетчика больше нуля, прерывания потока для текущего потока откладываются.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-117">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="8c7ca-118">Если этот вызов не связан с вызовом `EndPreventAsyncAbort` метода, можно достичь состояния, в котором прерывания потока не могут быть доставлены в текущий поток.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-118">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="8c7ca-119">Задержка не учитывается для потока, который прерывает работу.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-119">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="8c7ca-120">Функциональные возможности, предоставляемые этой функцией, используются внутри виртуальной машины (ВМ).</span><span class="sxs-lookup"><span data-stu-id="8c7ca-120">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="8c7ca-121">Неправильное использование этих методов может привести к неопределенному поведению в виртуальной машине.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-121">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="8c7ca-122">Например, при вызове `EndPreventAsyncAbort` без первого вызова `BeginPreventAsyncAbort` значение счетчика может равняться нулю, когда виртуальная машина ранее увеличила ее.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-122">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="8c7ca-123">Аналогично, внутренний счетчик не проверяется на переполнение.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-123">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="8c7ca-124">Если он превышает его предельное значение, так как он увеличивается как узлом, так и виртуальной машиной, результирующее поведение не определено.</span><span class="sxs-lookup"><span data-stu-id="8c7ca-124">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c7ca-125">Требования</span><span class="sxs-lookup"><span data-stu-id="8c7ca-125">Requirements</span></span>  

 <span data-ttu-id="8c7ca-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c7ca-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c7ca-127">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8c7ca-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c7ca-128">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c7ca-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c7ca-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c7ca-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c7ca-130">См. также</span><span class="sxs-lookup"><span data-stu-id="8c7ca-130">See also</span></span>

- [<span data-ttu-id="8c7ca-131">Метод EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="8c7ca-131">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="8c7ca-132">Интерфейс ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="8c7ca-132">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="8c7ca-133">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="8c7ca-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8c7ca-134">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="8c7ca-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8c7ca-135">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="8c7ca-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="8c7ca-136">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="8c7ca-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
