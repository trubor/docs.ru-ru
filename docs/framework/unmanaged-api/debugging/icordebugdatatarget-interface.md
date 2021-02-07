---
description: 'Дополнительные сведения о: интерфейс ICorDebugDataTarget'
title: Интерфейс ICorDebugDataTarget
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
ms.openlocfilehash: 34121b56080a8adc17543ce5716962c17c1a156d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764428"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="51164-103">Интерфейс ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="51164-103">ICorDebugDataTarget Interface</span></span>

<span data-ttu-id="51164-104">Предоставляет интерфейс обратного вызова, обеспечивающий доступ к конкретному целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="51164-104">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51164-105">Методы</span><span class="sxs-lookup"><span data-stu-id="51164-105">Methods</span></span>  
  
|<span data-ttu-id="51164-106">Метод</span><span class="sxs-lookup"><span data-stu-id="51164-106">Method</span></span>|<span data-ttu-id="51164-107">Описание</span><span class="sxs-lookup"><span data-stu-id="51164-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51164-108">Метод GetPlatform</span><span class="sxs-lookup"><span data-stu-id="51164-108">GetPlatform Method</span></span>](icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="51164-109">Предоставляет сведения о платформе, включая архитектуру процессора и операционную систему, на которых выполняется целевой процесс.</span><span class="sxs-lookup"><span data-stu-id="51164-109">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="51164-110">Метод ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="51164-110">ReadVirtual Method</span></span>](icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="51164-111">Возвращает блок непрерывной памяти, начиная с указанного адреса, и возвращает его в указанном буфере.</span><span class="sxs-lookup"><span data-stu-id="51164-111">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="51164-112">Метод GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="51164-112">GetThreadContext Method</span></span>](icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="51164-113">Запрашивает текущий контекст потока для указанного потока.</span><span class="sxs-lookup"><span data-stu-id="51164-113">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51164-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="51164-114">Remarks</span></span>  

 <span data-ttu-id="51164-115">`ICorDebugDataTarget` и его методы имеют следующие характеристики.</span><span class="sxs-lookup"><span data-stu-id="51164-115">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
- <span data-ttu-id="51164-116">Службы отладки вызывают методы этого интерфейса для доступа к памяти и другим данным в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="51164-116">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
- <span data-ttu-id="51164-117">Клиент отладчика должен реализовать этот интерфейс в соответствии с конкретным целевым объектом (например, в реальном процессе или дампе памяти).</span><span class="sxs-lookup"><span data-stu-id="51164-117">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
- <span data-ttu-id="51164-118">`ICorDebugDataTarget`Методы могут вызываться только в методах, реализованных в других `ICorDebug*` интерфейсах.</span><span class="sxs-lookup"><span data-stu-id="51164-118">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="51164-119">Это гарантирует, что клиент отладчика будет контролировать, в каком потоке он вызывается, и когда.</span><span class="sxs-lookup"><span data-stu-id="51164-119">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
- <span data-ttu-id="51164-120">`ICorDebugDataTarget`Реализация всегда должна возвращать актуальные сведения о целевом объекте.</span><span class="sxs-lookup"><span data-stu-id="51164-120">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="51164-121">Целевой процесс должен быть остановлен и не изменяется каким-либо образом при `ICorDebug*` вызове интерфейсов (и, следовательно, `ICorDebugDataTarget` методов).</span><span class="sxs-lookup"><span data-stu-id="51164-121">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="51164-122">Если целевой объект является динамическим процессом и изменяется его состояние, метод [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) необходимо вызвать снова, чтобы предоставить экземпляр ICorDebugProcess для замены.</span><span class="sxs-lookup"><span data-stu-id="51164-122">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51164-123">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="51164-123">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51164-124">Требования</span><span class="sxs-lookup"><span data-stu-id="51164-124">Requirements</span></span>  

 <span data-ttu-id="51164-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51164-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51164-126">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51164-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51164-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51164-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51164-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51164-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51164-129">См. также</span><span class="sxs-lookup"><span data-stu-id="51164-129">See also</span></span>

- [<span data-ttu-id="51164-130">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="51164-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="51164-131">Отладка</span><span class="sxs-lookup"><span data-stu-id="51164-131">Debugging</span></span>](index.md)
