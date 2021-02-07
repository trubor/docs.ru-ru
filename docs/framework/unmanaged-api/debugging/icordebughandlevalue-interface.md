---
description: 'Дополнительные сведения о: интерфейс ICorDebugHandleValue'
title: Интерфейс ICorDebugHandleValue
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: 3bdb1f5668be283d8722c15f4779adfe4d7b3a2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692047"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="fc69d-103">Интерфейс ICorDebugHandleValue</span><span class="sxs-lookup"><span data-stu-id="fc69d-103">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="fc69d-104">Подкласс ICorDebugReferenceValue, представляющий ссылочное значение, в котором отладчик создал маркер для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="fc69d-104">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc69d-105">Методы</span><span class="sxs-lookup"><span data-stu-id="fc69d-105">Methods</span></span>  
  
|<span data-ttu-id="fc69d-106">Метод</span><span class="sxs-lookup"><span data-stu-id="fc69d-106">Method</span></span>|<span data-ttu-id="fc69d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="fc69d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc69d-108">Метод Dispose</span><span class="sxs-lookup"><span data-stu-id="fc69d-108">Dispose Method</span></span>](icordebughandlevalue-dispose-method.md)|<span data-ttu-id="fc69d-109">Освобождает дескриптор, на который ссылается этот `ICorDebugHandleValue` объект, без явного освобождения указателя интерфейса.</span><span class="sxs-lookup"><span data-stu-id="fc69d-109">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="fc69d-110">Метод GetHandleType</span><span class="sxs-lookup"><span data-stu-id="fc69d-110">GetHandleType Method</span></span>](icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="fc69d-111">Возвращает значение Кордебугхандлетипе, описывающее тип маркера, на который ссылается this `ICorDebugHandleValue` .</span><span class="sxs-lookup"><span data-stu-id="fc69d-111">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc69d-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="fc69d-112">Remarks</span></span>  

 <span data-ttu-id="fc69d-113">`ICorDebugReferenceValue`Объект становится недействительным при прерывании выполнения отлаживаемого кода.</span><span class="sxs-lookup"><span data-stu-id="fc69d-113">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="fc69d-114">`ICorDebugHandleValue`Сохраняет ссылку на разрывы и продолжения до тех пор, пока он не будет явно освобожден.</span><span class="sxs-lookup"><span data-stu-id="fc69d-114">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc69d-115">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="fc69d-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc69d-116">Требования</span><span class="sxs-lookup"><span data-stu-id="fc69d-116">Requirements</span></span>  

 <span data-ttu-id="fc69d-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc69d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc69d-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc69d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc69d-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc69d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc69d-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc69d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc69d-121">См. также</span><span class="sxs-lookup"><span data-stu-id="fc69d-121">See also</span></span>

- [<span data-ttu-id="fc69d-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="fc69d-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
