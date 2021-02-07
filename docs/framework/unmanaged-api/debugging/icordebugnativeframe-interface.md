---
description: 'Дополнительные сведения о: интерфейс ICorDebugNativeFrame'
title: Интерфейс ICorDebugNativeFrame
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: e417184c9f1ca5136e1b4dba07820fd8242ae932
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729137"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="8298c-103">Интерфейс ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="8298c-103">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="8298c-104">Специализированная реализация ICorDebugFrame, используемая для кадров машинного кода.</span><span class="sxs-lookup"><span data-stu-id="8298c-104">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8298c-105">Методы</span><span class="sxs-lookup"><span data-stu-id="8298c-105">Methods</span></span>  
  
|<span data-ttu-id="8298c-106">Метод</span><span class="sxs-lookup"><span data-stu-id="8298c-106">Method</span></span>|<span data-ttu-id="8298c-107">Описание</span><span class="sxs-lookup"><span data-stu-id="8298c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8298c-108">Метод CanSetIP</span><span class="sxs-lookup"><span data-stu-id="8298c-108">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="8298c-109">Возвращает значение, указывающее, может ли быть ненадежным устанавливать указатель инструкции на указанное расположение смещения в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="8298c-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="8298c-110">Метод GetIP</span><span class="sxs-lookup"><span data-stu-id="8298c-110">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="8298c-111">Возвращает смещение кадра стека в машинный код.</span><span class="sxs-lookup"><span data-stu-id="8298c-111">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="8298c-112">Метод GetLocalDoubleRegisterValue</span><span class="sxs-lookup"><span data-stu-id="8298c-112">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="8298c-113">Возвращает указатель на объект ICorDebugValue, представляющий значение аргумента или локальной переменной, хранящейся в двух регистрах памяти в машинном кадре.</span><span class="sxs-lookup"><span data-stu-id="8298c-113">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="8298c-114">Метод GetLocalMemoryRegisterValue</span><span class="sxs-lookup"><span data-stu-id="8298c-114">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="8298c-115">Возвращает указатель на объект `ICorDebugValue` , представляющий значение локальной переменной, для которой младшие биты хранятся в указанном регистре, а старшие биты хранятся по указанному адресу памяти.</span><span class="sxs-lookup"><span data-stu-id="8298c-115">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="8298c-116">Метод GetLocalMemoryValue</span><span class="sxs-lookup"><span data-stu-id="8298c-116">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="8298c-117">Возвращает указатель на объект `ICorDebugValue` , представляющий значение локальной переменной, хранящейся по указанному адресу памяти.</span><span class="sxs-lookup"><span data-stu-id="8298c-117">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="8298c-118">Метод GetLocalRegisterMemoryValue</span><span class="sxs-lookup"><span data-stu-id="8298c-118">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="8298c-119">Возвращает указатель на объект `ICorDebugValue` , представляющий значение локальной переменной, для которой старшие биты хранятся в указанном регистре, а младшие биты хранятся по указанному адресу памяти.</span><span class="sxs-lookup"><span data-stu-id="8298c-119">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="8298c-120">Метод GetLocalRegisterValue</span><span class="sxs-lookup"><span data-stu-id="8298c-120">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="8298c-121">Возвращает указатель на объект `ICorDebugValue` , представляющий значение аргумента или локальную переменную, хранящуюся в указанном собственном регистре.</span><span class="sxs-lookup"><span data-stu-id="8298c-121">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="8298c-122">Метод GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="8298c-122">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="8298c-123">Возвращает указатель на объект [ICorDebugRegisterSet](icordebugregisterset-interface.md) , представляющий набор регистров для этого объекта `ICorDebugNativeFrame` .</span><span class="sxs-lookup"><span data-stu-id="8298c-123">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="8298c-124">Метод SetIP</span><span class="sxs-lookup"><span data-stu-id="8298c-124">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="8298c-125">Задает указатель инструкции в указанном расположении смещения в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="8298c-125">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8298c-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="8298c-126">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8298c-127">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="8298c-127">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8298c-128">Требования</span><span class="sxs-lookup"><span data-stu-id="8298c-128">Requirements</span></span>  

 <span data-ttu-id="8298c-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8298c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8298c-130">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8298c-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8298c-131">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8298c-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8298c-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8298c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8298c-133">См. также</span><span class="sxs-lookup"><span data-stu-id="8298c-133">See also</span></span>

- [<span data-ttu-id="8298c-134">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="8298c-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
