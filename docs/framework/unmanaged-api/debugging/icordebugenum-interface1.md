---
description: 'Дополнительные сведения о: интерфейс ICorDebugEnum'
title: Интерфейс ICorDebugEnum
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
ms.openlocfilehash: 20d2bb14bddcaf40802567ec78a8e318ac1db380
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694478"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="4b102-103">Интерфейс ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="4b102-103">ICorDebugEnum Interface</span></span>

<span data-ttu-id="4b102-104">Служит абстрактным базовым интерфейсом для перечислителей, используемых приложением отладки.</span><span class="sxs-lookup"><span data-stu-id="4b102-104">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b102-105">Методы</span><span class="sxs-lookup"><span data-stu-id="4b102-105">Methods</span></span>  
  
|<span data-ttu-id="4b102-106">Метод</span><span class="sxs-lookup"><span data-stu-id="4b102-106">Method</span></span>|<span data-ttu-id="4b102-107">Описание</span><span class="sxs-lookup"><span data-stu-id="4b102-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b102-108">Метод Clone</span><span class="sxs-lookup"><span data-stu-id="4b102-108">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="4b102-109">Создает копию данного объекта `ICorDebugEnum`.</span><span class="sxs-lookup"><span data-stu-id="4b102-109">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="4b102-110">Метод GetCount</span><span class="sxs-lookup"><span data-stu-id="4b102-110">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="4b102-111">Возвращает число элементов в перечислении.</span><span class="sxs-lookup"><span data-stu-id="4b102-111">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="4b102-112">Метод Reset</span><span class="sxs-lookup"><span data-stu-id="4b102-112">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="4b102-113">Перемещает курсор в начало перечисления.</span><span class="sxs-lookup"><span data-stu-id="4b102-113">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="4b102-114">Метод Skip</span><span class="sxs-lookup"><span data-stu-id="4b102-114">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="4b102-115">Перемещает курсор вперед в перечислении на указанное число элементов.</span><span class="sxs-lookup"><span data-stu-id="4b102-115">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b102-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="4b102-116">Remarks</span></span>  

 <span data-ttu-id="4b102-117">Следующие перечислители являются производными от `ICorDebugEnum` :</span><span class="sxs-lookup"><span data-stu-id="4b102-117">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="4b102-118">"Икордебугаппдомаиненум"</span><span class="sxs-lookup"><span data-stu-id="4b102-118">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="4b102-119">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="4b102-119">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="4b102-120">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="4b102-120">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="4b102-121">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="4b102-121">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="4b102-122">"Икордебугчаиненум"</span><span class="sxs-lookup"><span data-stu-id="4b102-122">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="4b102-123">"Икордебугкодинум"</span><span class="sxs-lookup"><span data-stu-id="4b102-123">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="4b102-124">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="4b102-124">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="4b102-125">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="4b102-125">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="4b102-126">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="4b102-126">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="4b102-127">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="4b102-127">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="4b102-128">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="4b102-128">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="4b102-129">икордебугхеапенум</span><span class="sxs-lookup"><span data-stu-id="4b102-129">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="4b102-130">икордебугхеапсегментенум</span><span class="sxs-lookup"><span data-stu-id="4b102-130">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="4b102-131">"Икордебугмодулинум"</span><span class="sxs-lookup"><span data-stu-id="4b102-131">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="4b102-132">"Икордебугобжектенум"</span><span class="sxs-lookup"><span data-stu-id="4b102-132">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="4b102-133">"Икордебугпроцессенум"</span><span class="sxs-lookup"><span data-stu-id="4b102-133">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="4b102-134">"Икордебугстепперенум"</span><span class="sxs-lookup"><span data-stu-id="4b102-134">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="4b102-135">"Икордебугсреаденум"</span><span class="sxs-lookup"><span data-stu-id="4b102-135">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="4b102-136">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="4b102-136">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="4b102-137">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="4b102-137">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="4b102-138">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="4b102-138">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="4b102-139">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="4b102-139">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b102-140">Требования</span><span class="sxs-lookup"><span data-stu-id="4b102-140">Requirements</span></span>  

 <span data-ttu-id="4b102-141">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b102-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b102-142">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b102-142">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b102-143">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b102-143">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b102-144">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b102-144">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b102-145">См. также</span><span class="sxs-lookup"><span data-stu-id="4b102-145">See also</span></span>

- [<span data-ttu-id="4b102-146">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="4b102-146">Debugging Interfaces</span></span>](debugging-interfaces.md)
