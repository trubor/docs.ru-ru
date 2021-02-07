---
description: 'Дополнительные сведения о: интерфейс ICorDebugProcess2'
title: Интерфейс ICorDebugProcess2
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
ms.openlocfilehash: 47e94ee8ee4f45e365fa9efe888cb706f8bb1dfd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746598"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="fa66d-103">Интерфейс ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="fa66d-103">ICorDebugProcess2 Interface</span></span>

<span data-ttu-id="fa66d-104">Логическое расширение интерфейса ICorDebugProcess, представляющее процесс, выполняющий управляемый код.</span><span class="sxs-lookup"><span data-stu-id="fa66d-104">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa66d-105">Методы</span><span class="sxs-lookup"><span data-stu-id="fa66d-105">Methods</span></span>  
  
|<span data-ttu-id="fa66d-106">Метод</span><span class="sxs-lookup"><span data-stu-id="fa66d-106">Method</span></span>|<span data-ttu-id="fa66d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="fa66d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa66d-108">Метод ClearUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fa66d-108">ClearUnmanagedBreakpoint Method</span></span>](icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="fa66d-109">Удаляет точку останова с указанным смещением, которое было задано предыдущим вызовом метода `ICorDebugProcess2::SetUnmanagedBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="fa66d-109">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="fa66d-110">Метод GetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="fa66d-110">GetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="fa66d-111">Возвращает флаги, которые должны быть установлены в среде CLR для загрузки изображения в процесс, на который ссылается this `ICorDebugProcess2` .</span><span class="sxs-lookup"><span data-stu-id="fa66d-111">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="fa66d-112">Метод GetReferenceValueFromGCHandle</span><span class="sxs-lookup"><span data-stu-id="fa66d-112">GetReferenceValueFromGCHandle Method</span></span>](icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="fa66d-113">Возвращает указатель ссылки на указанный управляемый объект, который имеет обработчик сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="fa66d-113">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="fa66d-114">Метод GetThreadForTaskID</span><span class="sxs-lookup"><span data-stu-id="fa66d-114">GetThreadForTaskID Method</span></span>](icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="fa66d-115">Возвращает поток, в котором выполняется задача с указанным идентификатором.</span><span class="sxs-lookup"><span data-stu-id="fa66d-115">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="fa66d-116">Метод GetVersion</span><span class="sxs-lookup"><span data-stu-id="fa66d-116">GetVersion Method</span></span>](icordebugprocess2-getversion-method.md)|<span data-ttu-id="fa66d-117">Возвращает версию среды CLR, на основе которой выполняется отлаживаемый процесс.</span><span class="sxs-lookup"><span data-stu-id="fa66d-117">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="fa66d-118">Метод SetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="fa66d-118">SetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="fa66d-119">Задает флаги, которые требуются для JIT-компилятора при загрузке изображения в отлаживаемый процесс.</span><span class="sxs-lookup"><span data-stu-id="fa66d-119">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="fa66d-120">Метод SetUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fa66d-120">SetUnmanagedBreakpoint Method</span></span>](icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="fa66d-121">Задает неуправляемую точку останова в указанном смещении машинного образа.</span><span class="sxs-lookup"><span data-stu-id="fa66d-121">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa66d-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="fa66d-122">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa66d-123">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="fa66d-123">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa66d-124">Требования</span><span class="sxs-lookup"><span data-stu-id="fa66d-124">Requirements</span></span>  

 <span data-ttu-id="fa66d-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa66d-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa66d-126">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa66d-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa66d-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa66d-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa66d-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa66d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa66d-129">См. также</span><span class="sxs-lookup"><span data-stu-id="fa66d-129">See also</span></span>

- [<span data-ttu-id="fa66d-130">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="fa66d-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
