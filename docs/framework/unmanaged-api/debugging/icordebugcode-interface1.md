---
description: Дополнительные сведения о интерфейсе ICorDebugCode
title: Интерфейс ICorDebugCode
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
ms.openlocfilehash: ce67c48501783bbe00152f0ba2c224e6e7dde6d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711158"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="e74c0-103">Интерфейс ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="e74c0-103">ICorDebugCode Interface</span></span>

<span data-ttu-id="e74c0-104">Представляет сегмент кода на языке MSIL или сегмент машинного кода.</span><span class="sxs-lookup"><span data-stu-id="e74c0-104">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e74c0-105">Методы</span><span class="sxs-lookup"><span data-stu-id="e74c0-105">Methods</span></span>  
  
|<span data-ttu-id="e74c0-106">Метод</span><span class="sxs-lookup"><span data-stu-id="e74c0-106">Method</span></span>|<span data-ttu-id="e74c0-107">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e74c0-108">Метод CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="e74c0-108">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="e74c0-109">Создает точку останова по указанному смещению.</span><span class="sxs-lookup"><span data-stu-id="e74c0-109">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="e74c0-110">Метод GetAddress</span><span class="sxs-lookup"><span data-stu-id="e74c0-110">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="e74c0-111">Возвращает относительный виртуальный адрес (RVA) сегмента кода, который представляет этот объект `ICorDebugCode` .</span><span class="sxs-lookup"><span data-stu-id="e74c0-111">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="e74c0-112">Метод GetCode</span><span class="sxs-lookup"><span data-stu-id="e74c0-112">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="e74c0-113">Возвращает весь код для указанной функции, отформатированный для дизассемблирования.</span><span class="sxs-lookup"><span data-stu-id="e74c0-113">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="e74c0-114">Этот метод не рекомендуется к использованию. Вместо этого используйте [ICorDebugCode2:: жеткодечункс](icordebugcode2-getcodechunks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e74c0-114">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="e74c0-115">Метод GetEnCRemapSequencePoints</span><span class="sxs-lookup"><span data-stu-id="e74c0-115">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="e74c0-116">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="e74c0-116">Not implemented.</span></span>|  
|[<span data-ttu-id="e74c0-117">Метод GetFunction</span><span class="sxs-lookup"><span data-stu-id="e74c0-117">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="e74c0-118">Возвращает "ICorDebugFunction", связанный с этим `ICorDebugCode` .</span><span class="sxs-lookup"><span data-stu-id="e74c0-118">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="e74c0-119">Метод GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="e74c0-119">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="e74c0-120">Возвращает массив экземпляров "COR_DEBUG_IL_TO_NATIVE_MAP", которые представляют сопоставления от смещений MSIL до собственных смещений.</span><span class="sxs-lookup"><span data-stu-id="e74c0-120">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="e74c0-121">Метод GetSize</span><span class="sxs-lookup"><span data-stu-id="e74c0-121">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="e74c0-122">Возвращает размер двоичного кода, представленного этим объектом, в байтах `ICorDebugCode` .</span><span class="sxs-lookup"><span data-stu-id="e74c0-122">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="e74c0-123">Метод GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="e74c0-123">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="e74c0-124">Возвращает номер, отсчитываемый от единицы, определяющий версию кода, который представляет данный объект `ICorDebugCode` .</span><span class="sxs-lookup"><span data-stu-id="e74c0-124">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="e74c0-125">Метод IsIL</span><span class="sxs-lookup"><span data-stu-id="e74c0-125">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="e74c0-126">Возвращает значение, указывающее, `ICorDebugCode` компилируется ли это в MSIL.</span><span class="sxs-lookup"><span data-stu-id="e74c0-126">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e74c0-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="e74c0-127">Remarks</span></span>  

 <span data-ttu-id="e74c0-128">`ICorDebugCode` может представлять язык MSIL или машинный код.</span><span class="sxs-lookup"><span data-stu-id="e74c0-128">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="e74c0-129">Объект "ICorDebugFunction", представляющий код MSIL, может быть связан с нулем или `ICorDebugCode` с одним объектом.</span><span class="sxs-lookup"><span data-stu-id="e74c0-129">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="e74c0-130">Объект "ICorDebugFunction", представляющий машинный код, может иметь любое количество `ICorDebugCode` связанных с ним объектов.</span><span class="sxs-lookup"><span data-stu-id="e74c0-130">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e74c0-131">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="e74c0-131">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e74c0-132">Требования</span><span class="sxs-lookup"><span data-stu-id="e74c0-132">Requirements</span></span>  

 <span data-ttu-id="e74c0-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e74c0-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e74c0-134">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e74c0-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e74c0-135">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e74c0-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e74c0-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e74c0-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e74c0-137">См. также</span><span class="sxs-lookup"><span data-stu-id="e74c0-137">See also</span></span>

- [<span data-ttu-id="e74c0-138">Интерфейс ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="e74c0-138">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="e74c0-139">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="e74c0-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
