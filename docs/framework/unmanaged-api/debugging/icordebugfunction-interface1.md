---
description: Дополнительные сведения о интерфейсе ICorDebugFunction
title: Интерфейс ICorDebugFunction
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
ms.openlocfilehash: 835625341889e89e15ceb66ca71531cf7b8311c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692387"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="7826f-103">Интерфейс ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="7826f-103">ICorDebugFunction Interface</span></span>

<span data-ttu-id="7826f-104">Представляет управляемую функцию или метод.</span><span class="sxs-lookup"><span data-stu-id="7826f-104">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7826f-105">Методы</span><span class="sxs-lookup"><span data-stu-id="7826f-105">Methods</span></span>  
  
|<span data-ttu-id="7826f-106">Метод</span><span class="sxs-lookup"><span data-stu-id="7826f-106">Method</span></span>|<span data-ttu-id="7826f-107">Описание</span><span class="sxs-lookup"><span data-stu-id="7826f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7826f-108">Метод CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7826f-108">CreateBreakpoint Method</span></span>](icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="7826f-109">Создает точку останова в начале этой функции.</span><span class="sxs-lookup"><span data-stu-id="7826f-109">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="7826f-110">Метод GetClass</span><span class="sxs-lookup"><span data-stu-id="7826f-110">GetClass Method</span></span>](icordebugfunction-getclass-method.md)|<span data-ttu-id="7826f-111">Возвращает объект ICorDebugClass, представляющий класс, членом которого является эта функция.</span><span class="sxs-lookup"><span data-stu-id="7826f-111">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="7826f-112">Метод GetCurrentVersionNumber</span><span class="sxs-lookup"><span data-stu-id="7826f-112">GetCurrentVersionNumber Method</span></span>](icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="7826f-113">Возвращает номер версии последнего изменения, внесенного в эту функцию.</span><span class="sxs-lookup"><span data-stu-id="7826f-113">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="7826f-114">Метод GetILCode</span><span class="sxs-lookup"><span data-stu-id="7826f-114">GetILCode Method</span></span>](icordebugfunction-getilcode-method.md)|<span data-ttu-id="7826f-115">Возвращает код MSIL для этой функции.</span><span class="sxs-lookup"><span data-stu-id="7826f-115">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="7826f-116">Метод GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="7826f-116">GetLocalVarSigToken Method</span></span>](icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="7826f-117">Возвращает маркер метаданных для сигнатуры локальной переменной функции, представленной этим `ICorDebugFunction` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="7826f-117">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="7826f-118">Метод GetModule</span><span class="sxs-lookup"><span data-stu-id="7826f-118">GetModule Method</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="7826f-119">Возвращает модуль, в котором определена эта функция.</span><span class="sxs-lookup"><span data-stu-id="7826f-119">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="7826f-120">Метод GetNativeCode</span><span class="sxs-lookup"><span data-stu-id="7826f-120">GetNativeCode Method</span></span>](icordebugfunction-getnativecode-method.md)|<span data-ttu-id="7826f-121">Получает машинный код для этой функции.</span><span class="sxs-lookup"><span data-stu-id="7826f-121">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="7826f-122">Метод GetToken</span><span class="sxs-lookup"><span data-stu-id="7826f-122">GetToken Method</span></span>](icordebugfunction-gettoken-method.md)|<span data-ttu-id="7826f-123">Возвращает маркер метаданных для этой функции.</span><span class="sxs-lookup"><span data-stu-id="7826f-123">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7826f-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="7826f-124">Remarks</span></span>  

 <span data-ttu-id="7826f-125">`ICorDebugFunction`Интерфейс не представляет функцию с параметрами универсального типа.</span><span class="sxs-lookup"><span data-stu-id="7826f-125">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="7826f-126">Например, `ICorDebugFunction` экземпляр будет представлять, `Func<T>` но не `Func<string>` .</span><span class="sxs-lookup"><span data-stu-id="7826f-126">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="7826f-127">Вызовите метод [ICorDebugILFrame2:: енумератетипепараметерс](icordebugilframe2-enumeratetypeparameters-method.md) , чтобы получить параметры универсального типа.</span><span class="sxs-lookup"><span data-stu-id="7826f-127">Call [ICorDebugILFrame2::EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="7826f-128">Связь между маркером метаданных метода, `mdMethodDef` и `ICorDebugFunction` объектом метода зависит от того, разрешена ли функция "изменить и продолжить" для функции:</span><span class="sxs-lookup"><span data-stu-id="7826f-128">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="7826f-129">Если функция "изменить и продолжить" не разрешена для функции, между `ICorDebugFunction` объектом и токеном существует связь "один к одному" `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="7826f-129">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="7826f-130">То есть функция имеет один `ICorDebugFunction` объект и один `mdMethodDef` токен.</span><span class="sxs-lookup"><span data-stu-id="7826f-130">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="7826f-131">Если для функции разрешен режим "изменить и продолжить", между `ICorDebugFunction` объектом и токеном существует связь "многие к одному" `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="7826f-131">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="7826f-132">Это значит, что функция может иметь много экземпляров `ICorDebugFunction` , по одной для каждой версии функции, но только один `mdMethodDef` токен.</span><span class="sxs-lookup"><span data-stu-id="7826f-132">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7826f-133">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="7826f-133">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7826f-134">Требования</span><span class="sxs-lookup"><span data-stu-id="7826f-134">Requirements</span></span>  

 <span data-ttu-id="7826f-135">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7826f-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7826f-136">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7826f-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7826f-137">**Библиотека:**  Коргуидс. lib</span><span class="sxs-lookup"><span data-stu-id="7826f-137">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="7826f-138">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7826f-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7826f-139">См. также</span><span class="sxs-lookup"><span data-stu-id="7826f-139">See also</span></span>

- [<span data-ttu-id="7826f-140">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7826f-140">Debugging Interfaces</span></span>](debugging-interfaces.md)
