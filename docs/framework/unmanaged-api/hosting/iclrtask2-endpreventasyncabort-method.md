---
description: 'Дополнительные сведения о методе: ICLRTask2:: EndPreventAsyncAbort'
title: Метод ICLRTask2::EndPreventAsyncAbort
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 964a68c1ad6d5aa6a95560d2870e135640283590
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799503"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="02129-103">Метод ICLRTask2::EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="02129-103">ICLRTask2::EndPreventAsyncAbort Method</span></span>

<span data-ttu-id="02129-104">Разрешает новые или ожидающие запросы на прерывание потока в результате прерывания потока в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="02129-104">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02129-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="02129-105">Syntax</span></span>  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="02129-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="02129-106">Return Value</span></span>  

 <span data-ttu-id="02129-107">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="02129-107">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="02129-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="02129-108">HRESULT</span></span>|<span data-ttu-id="02129-109">Описание:</span><span class="sxs-lookup"><span data-stu-id="02129-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="02129-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="02129-110">S_OK</span></span>|<span data-ttu-id="02129-111">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="02129-111">The method completed successfully.</span></span>|  
|<span data-ttu-id="02129-112">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="02129-112">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="02129-113">Метод был вызван в потоке, который не является текущим потоком.</span><span class="sxs-lookup"><span data-stu-id="02129-113">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02129-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="02129-114">Remarks</span></span>  

 <span data-ttu-id="02129-115">При вызове этого метода счетчик "задержка — прерывание потока" для текущего потока уменьшается на один.</span><span class="sxs-lookup"><span data-stu-id="02129-115">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="02129-116">Вызовы [ICLRTask2:: BeginPreventAsyncAbort](iclrtask2-beginpreventasyncabort-method.md) и `EndPreventAsyncAbort` могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="02129-116">Calls to [ICLRTask2::BeginPreventAsyncAbort](iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="02129-117">Пока значение счетчика больше нуля, прерывания потока для текущего потока откладываются.</span><span class="sxs-lookup"><span data-stu-id="02129-117">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="02129-118">Функциональные возможности, предоставляемые этой функцией, используются внутри виртуальной машины (ВМ).</span><span class="sxs-lookup"><span data-stu-id="02129-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="02129-119">Неправильное использование этих методов может привести к неопределенному поведению в виртуальной машине.</span><span class="sxs-lookup"><span data-stu-id="02129-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="02129-120">Например, при вызове `EndPreventAsyncAbort` без первого вызова `BeginPreventAsyncAbort` значение счетчика может равняться нулю, когда виртуальная машина ранее увеличила ее.</span><span class="sxs-lookup"><span data-stu-id="02129-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="02129-121">Аналогично, внутренний счетчик не проверяется на переполнение.</span><span class="sxs-lookup"><span data-stu-id="02129-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="02129-122">Если он превышает его предельное значение, так как он увеличивается как узлом, так и виртуальной машиной, результирующее поведение не определено.</span><span class="sxs-lookup"><span data-stu-id="02129-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02129-123">Требования</span><span class="sxs-lookup"><span data-stu-id="02129-123">Requirements</span></span>  

 <span data-ttu-id="02129-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02129-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02129-125">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="02129-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02129-126">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02129-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02129-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02129-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02129-128">См. также</span><span class="sxs-lookup"><span data-stu-id="02129-128">See also</span></span>

- [<span data-ttu-id="02129-129">Метод BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="02129-129">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="02129-130">Интерфейс ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="02129-130">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="02129-131">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="02129-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="02129-132">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="02129-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="02129-133">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="02129-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="02129-134">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="02129-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
