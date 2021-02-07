---
description: 'Дополнительные сведения о: интерфейс ICLRDataTarget'
title: Интерфейс ICLRDataTarget
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
ms.openlocfilehash: f24760f638705a1bde7e055069cbc3a18a0896fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738225"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="7e14f-103">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="7e14f-103">ICLRDataTarget Interface</span></span>

<span data-ttu-id="7e14f-104">Предоставляет методы для взаимодействия с целевым элементом общеязыковой среды выполнения (CLR).</span><span class="sxs-lookup"><span data-stu-id="7e14f-104">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e14f-105">Методы</span><span class="sxs-lookup"><span data-stu-id="7e14f-105">Methods</span></span>  
  
|<span data-ttu-id="7e14f-106">Метод</span><span class="sxs-lookup"><span data-stu-id="7e14f-106">Method</span></span>|<span data-ttu-id="7e14f-107">Описание</span><span class="sxs-lookup"><span data-stu-id="7e14f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e14f-108">Метод GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="7e14f-108">GetCurrentThreadID Method</span></span>](iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="7e14f-109">Возвращает идентификатор операционной системы для текущего потока.</span><span class="sxs-lookup"><span data-stu-id="7e14f-109">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="7e14f-110">Метод GetImageBase</span><span class="sxs-lookup"><span data-stu-id="7e14f-110">GetImageBase Method</span></span>](iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="7e14f-111">Возвращает адрес базовой памяти для указанного образа.</span><span class="sxs-lookup"><span data-stu-id="7e14f-111">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="7e14f-112">Метод GetMachineType</span><span class="sxs-lookup"><span data-stu-id="7e14f-112">GetMachineType Method</span></span>](iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="7e14f-113">Возвращает идентификатор для типа набора инструкций, используемого целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="7e14f-113">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="7e14f-114">Метод GetPointerSize</span><span class="sxs-lookup"><span data-stu-id="7e14f-114">GetPointerSize Method</span></span>](iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="7e14f-115">Возвращает размер (в байтах) указателя на текущий целевой объект.</span><span class="sxs-lookup"><span data-stu-id="7e14f-115">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="7e14f-116">Метод GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="7e14f-116">GetThreadContext Method</span></span>](iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="7e14f-117">Возвращает указатель на контекст потока с указанным идентификатором.</span><span class="sxs-lookup"><span data-stu-id="7e14f-117">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="7e14f-118">Метод GetTLSValue</span><span class="sxs-lookup"><span data-stu-id="7e14f-118">GetTLSValue Method</span></span>](iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="7e14f-119">Возвращает значение в локальном хранилище потока (TLS) по указанному индексу для указанного потока.</span><span class="sxs-lookup"><span data-stu-id="7e14f-119">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="7e14f-120">Метод ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="7e14f-120">ReadVirtual Method</span></span>](iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="7e14f-121">Считывает данные из указанного адреса виртуальной памяти в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="7e14f-121">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="7e14f-122">Метод Request</span><span class="sxs-lookup"><span data-stu-id="7e14f-122">Request Method</span></span>](iclrdatatarget-request-method.md)|<span data-ttu-id="7e14f-123">Вызывается службами доступа к данным среды CLR для запроса операции, как определено в реализации.</span><span class="sxs-lookup"><span data-stu-id="7e14f-123">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="7e14f-124">Метод SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="7e14f-124">SetThreadContext Method</span></span>](iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="7e14f-125">Задает текущий контекст указанного потока в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="7e14f-125">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="7e14f-126">Метод SetTLSValue</span><span class="sxs-lookup"><span data-stu-id="7e14f-126">SetTLSValue Method</span></span>](iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="7e14f-127">Задает значение в локальном хранилище потока (TLS) указанного потока в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="7e14f-127">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="7e14f-128">Метод WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="7e14f-128">WriteVirtual Method</span></span>](iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="7e14f-129">Записывает данные из указанного буфера в указанный адрес виртуальной памяти.</span><span class="sxs-lookup"><span data-stu-id="7e14f-129">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e14f-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="7e14f-130">Remarks</span></span>  

 <span data-ttu-id="7e14f-131">Клиент API (то есть отладчик) должен реализовать этот интерфейс в соответствии с конкретным целевым элементом.</span><span class="sxs-lookup"><span data-stu-id="7e14f-131">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="7e14f-132">Например, реализация активного процесса будет отличаться от реализации дампа памяти.</span><span class="sxs-lookup"><span data-stu-id="7e14f-132">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e14f-133">Требования</span><span class="sxs-lookup"><span data-stu-id="7e14f-133">Requirements</span></span>  

 <span data-ttu-id="7e14f-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e14f-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e14f-135">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="7e14f-135">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7e14f-136">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e14f-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e14f-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e14f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e14f-138">См. также</span><span class="sxs-lookup"><span data-stu-id="7e14f-138">See also</span></span>

- [<span data-ttu-id="7e14f-139">Интерфейс ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="7e14f-139">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="7e14f-140">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7e14f-140">Debugging Interfaces</span></span>](debugging-interfaces.md)
