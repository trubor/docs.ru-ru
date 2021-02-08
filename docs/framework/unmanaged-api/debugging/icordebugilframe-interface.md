---
description: 'Дополнительные сведения о: интерфейс ICorDebugILFrame'
title: Интерфейс ICorDebugILFrame
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
ms.openlocfilehash: 251fa18151ff286bee3e1bcf7707bf5f7145b4f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791365"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="9727b-103">Интерфейс ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="9727b-103">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="9727b-104">Представляет кадр стека кода промежуточного языка MSIL.</span><span class="sxs-lookup"><span data-stu-id="9727b-104">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="9727b-105">Этот интерфейс является подклассом интерфейса ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="9727b-105">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9727b-106">Методы</span><span class="sxs-lookup"><span data-stu-id="9727b-106">Methods</span></span>  
  
|<span data-ttu-id="9727b-107">Метод</span><span class="sxs-lookup"><span data-stu-id="9727b-107">Method</span></span>|<span data-ttu-id="9727b-108">Описание</span><span class="sxs-lookup"><span data-stu-id="9727b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9727b-109">Метод CanSetIP</span><span class="sxs-lookup"><span data-stu-id="9727b-109">CanSetIP Method</span></span>](icordebugilframe-cansetip-method.md)|<span data-ttu-id="9727b-110">Возвращает значение, указывающее, можно ли задать для указателя инструкции заданное расположение смещения.</span><span class="sxs-lookup"><span data-stu-id="9727b-110">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="9727b-111">Метод EnumerateArguments</span><span class="sxs-lookup"><span data-stu-id="9727b-111">EnumerateArguments Method</span></span>](icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="9727b-112">Возвращает перечислитель для аргументов в этом кадре.</span><span class="sxs-lookup"><span data-stu-id="9727b-112">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="9727b-113">Метод EnumerateLocalVariables</span><span class="sxs-lookup"><span data-stu-id="9727b-113">EnumerateLocalVariables Method</span></span>](icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="9727b-114">Возвращает перечислитель для локальных переменных в этом кадре.</span><span class="sxs-lookup"><span data-stu-id="9727b-114">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="9727b-115">Метод GetArgument</span><span class="sxs-lookup"><span data-stu-id="9727b-115">GetArgument Method</span></span>](icordebugilframe-getargument-method.md)|<span data-ttu-id="9727b-116">Возвращает значение указанного аргумента в этом кадре стека MSIL.</span><span class="sxs-lookup"><span data-stu-id="9727b-116">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="9727b-117">Метод GetIP</span><span class="sxs-lookup"><span data-stu-id="9727b-117">GetIP Method</span></span>](icordebugilframe-getip-method.md)|<span data-ttu-id="9727b-118">Возвращает значение указателя инструкции и битовое значение сочетания, которое описывает, как было получено значение указателя инструкции.</span><span class="sxs-lookup"><span data-stu-id="9727b-118">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="9727b-119">Метод GetLocalVariable</span><span class="sxs-lookup"><span data-stu-id="9727b-119">GetLocalVariable Method</span></span>](icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="9727b-120">Возвращает значение указанной локальной переменной в этом кадре стека MSIL.</span><span class="sxs-lookup"><span data-stu-id="9727b-120">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="9727b-121">Метод GetStackDepth</span><span class="sxs-lookup"><span data-stu-id="9727b-121">GetStackDepth Method</span></span>](icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="9727b-122">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="9727b-122">Not implemented.</span></span>|  
|[<span data-ttu-id="9727b-123">Метод GetStackValue</span><span class="sxs-lookup"><span data-stu-id="9727b-123">GetStackValue Method</span></span>](icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="9727b-124">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="9727b-124">Not implemented.</span></span>|  
|[<span data-ttu-id="9727b-125">Метод SetIP</span><span class="sxs-lookup"><span data-stu-id="9727b-125">SetIP Method</span></span>](icordebugilframe-setip-method.md)|<span data-ttu-id="9727b-126">Устанавливает указатель инструкции на указанное положение смещения в коде MSIL.</span><span class="sxs-lookup"><span data-stu-id="9727b-126">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9727b-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="9727b-127">Remarks</span></span>  

 <span data-ttu-id="9727b-128">`ICorDebugILFrame`Интерфейс является специализированным интерфейсом ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="9727b-128">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="9727b-129">Он используется либо для кадров кода MSIL, либо для кадров, скомпилированных JIT.</span><span class="sxs-lookup"><span data-stu-id="9727b-129">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="9727b-130">JIT-скомпилированные кадры реализуют `ICorDebugILFrame` интерфейс и интерфейс ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="9727b-130">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9727b-131">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="9727b-131">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9727b-132">Требования</span><span class="sxs-lookup"><span data-stu-id="9727b-132">Requirements</span></span>  

 <span data-ttu-id="9727b-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9727b-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9727b-134">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9727b-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9727b-135">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9727b-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9727b-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9727b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9727b-137">См. также</span><span class="sxs-lookup"><span data-stu-id="9727b-137">See also</span></span>

- [<span data-ttu-id="9727b-138">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="9727b-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
