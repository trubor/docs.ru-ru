---
description: 'Дополнительные сведения о методе: ICorDebugHeapValue3:: Жетмониторевентваитлист'
title: Метод ICorDebugHeapValue3::GetMonitorEventWaitList
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
ms.openlocfilehash: ffc849e83151719062133382989344a8f0057caf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791456"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="59ecb-103">Метод ICorDebugHeapValue3::GetMonitorEventWaitList</span><span class="sxs-lookup"><span data-stu-id="59ecb-103">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>

<span data-ttu-id="59ecb-104">Предоставляет упорядоченный список потоков, поставленных в очередь на событие, связанное с блокировкой монитора.</span><span class="sxs-lookup"><span data-stu-id="59ecb-104">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ecb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="59ecb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59ecb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="59ecb-106">Parameters</span></span>  

 `ppThreadEnum`  
 <span data-ttu-id="59ecb-107">заполняет Перечислитель Икордебугсреаденум, предоставляющий упорядоченный список потоков.</span><span class="sxs-lookup"><span data-stu-id="59ecb-107">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59ecb-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="59ecb-108">Return Value</span></span>  

 <span data-ttu-id="59ecb-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="59ecb-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="59ecb-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="59ecb-110">HRESULT</span></span>|<span data-ttu-id="59ecb-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="59ecb-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="59ecb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="59ecb-112">S_OK</span></span>|<span data-ttu-id="59ecb-113">Список не пуст.</span><span class="sxs-lookup"><span data-stu-id="59ecb-113">The list is not empty.</span></span>|  
|<span data-ttu-id="59ecb-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="59ecb-114">S_FALSE</span></span>|<span data-ttu-id="59ecb-115">Список пуст.</span><span class="sxs-lookup"><span data-stu-id="59ecb-115">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="59ecb-116">Исключения</span><span class="sxs-lookup"><span data-stu-id="59ecb-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59ecb-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="59ecb-117">Remarks</span></span>  

 <span data-ttu-id="59ecb-118">Первый поток в списке является первым потоком, который освобождается при следующем вызове метода <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="59ecb-118">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="59ecb-119">Следующий поток в списке освобождается в следующем вызове и т. д.</span><span class="sxs-lookup"><span data-stu-id="59ecb-119">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="59ecb-120">Если список не пуст, этот метод возвращает S_OK.</span><span class="sxs-lookup"><span data-stu-id="59ecb-120">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="59ecb-121">Если список пуст, метод возвращает S_FALSE; в этом случае перечисление по-прежнему является допустимым, хотя оно пустое.</span><span class="sxs-lookup"><span data-stu-id="59ecb-121">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="59ecb-122">В любом случае интерфейс перечисления можно использовать только в течение текущего синхронизированного состояния.</span><span class="sxs-lookup"><span data-stu-id="59ecb-122">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="59ecb-123">Тем не менее, высветка интерфейсов потока является допустимой, пока поток не завершит работу.</span><span class="sxs-lookup"><span data-stu-id="59ecb-123">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="59ecb-124">Если не `ppThreadEnum` является допустимым указателем, результат не определен.</span><span class="sxs-lookup"><span data-stu-id="59ecb-124">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="59ecb-125">Если возникает ошибка, которая не может определить, какие потоки ожидают монитор, метод возвращает значение HRESULT, указывающее на сбой.</span><span class="sxs-lookup"><span data-stu-id="59ecb-125">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59ecb-126">Требования</span><span class="sxs-lookup"><span data-stu-id="59ecb-126">Requirements</span></span>  

 <span data-ttu-id="59ecb-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59ecb-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59ecb-128">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59ecb-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59ecb-129">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59ecb-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59ecb-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59ecb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ecb-131">См. также</span><span class="sxs-lookup"><span data-stu-id="59ecb-131">See also</span></span>

- [<span data-ttu-id="59ecb-132">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="59ecb-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="59ecb-133">Отладка</span><span class="sxs-lookup"><span data-stu-id="59ecb-133">Debugging</span></span>](index.md)
