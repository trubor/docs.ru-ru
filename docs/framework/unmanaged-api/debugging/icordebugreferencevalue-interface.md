---
description: 'Дополнительные сведения о: интерфейс ICorDebugReferenceValue'
title: Интерфейс ICorDebugReferenceValue
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: e516b1178b4f4268472dedd37d6443e673e16af6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690968"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="40583-103">Интерфейс ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="40583-103">ICorDebugReferenceValue Interface</span></span>

<span data-ttu-id="40583-104">Предоставляет методы, управляющие значением, которое является ссылкой на объект.</span><span class="sxs-lookup"><span data-stu-id="40583-104">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="40583-105">(Т. е. Этот интерфейс предоставляет методы, управляющие указателем.) Этот интерфейс реализует "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="40583-105">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40583-106">Методы</span><span class="sxs-lookup"><span data-stu-id="40583-106">Methods</span></span>  
  
|<span data-ttu-id="40583-107">Метод</span><span class="sxs-lookup"><span data-stu-id="40583-107">Method</span></span>|<span data-ttu-id="40583-108">Описание</span><span class="sxs-lookup"><span data-stu-id="40583-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40583-109">Метод Dereference</span><span class="sxs-lookup"><span data-stu-id="40583-109">Dereference Method</span></span>](icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="40583-110">Возвращает объект, на который указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="40583-110">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="40583-111">Метод DereferenceStrong</span><span class="sxs-lookup"><span data-stu-id="40583-111">DereferenceStrong Method</span></span>](icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="40583-112">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="40583-112">Not implemented.</span></span> <span data-ttu-id="40583-113">Этот метод не следует вызывать.</span><span class="sxs-lookup"><span data-stu-id="40583-113">Do not call this method.</span></span>|  
|[<span data-ttu-id="40583-114">Метод GetValue</span><span class="sxs-lookup"><span data-stu-id="40583-114">GetValue Method</span></span>](icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="40583-115">Возвращает текущий адрес памяти объекта, на который указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="40583-115">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="40583-116">Метод IsNull</span><span class="sxs-lookup"><span data-stu-id="40583-116">IsNull Method</span></span>](icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="40583-117">Возвращает значение, указывающее, является ли `ICorDebugReferenceValue` значение значением NULL, в этом случае, не `ICorDebugReferenceValue` указывает на объект.</span><span class="sxs-lookup"><span data-stu-id="40583-117">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="40583-118">Метод SetValue</span><span class="sxs-lookup"><span data-stu-id="40583-118">SetValue Method</span></span>](icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="40583-119">Задает текущий адрес памяти.</span><span class="sxs-lookup"><span data-stu-id="40583-119">Sets the current memory address.</span></span> <span data-ttu-id="40583-120">Это значит, что этот метод задает `ICorDebugReferenceValue` значение, которое указывает на объект.</span><span class="sxs-lookup"><span data-stu-id="40583-120">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40583-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="40583-121">Remarks</span></span>  

 <span data-ttu-id="40583-122">Среда CLR может выполнять сборку мусора для объектов при продолжении отлаживаемого процесса.</span><span class="sxs-lookup"><span data-stu-id="40583-122">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="40583-123">Сборка мусора может перемещать объекты в памяти.</span><span class="sxs-lookup"><span data-stu-id="40583-123">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="40583-124">Либо взаимодействуют `ICorDebugReferenceValue` со сборкой мусора, так что ее сведения обновляются после сборки мусора, или же она становится неявной до сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="40583-124">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="40583-125">`ICorDebugReferenceValue`После продолжения отлаживаемого процесса объект может быть неявно недействительным.</span><span class="sxs-lookup"><span data-stu-id="40583-125">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="40583-126">Производный "ICorDebugHandleValue" не является недействительным до тех пор, пока он не будет явно освобожден или открыт.</span><span class="sxs-lookup"><span data-stu-id="40583-126">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40583-127">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="40583-127">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40583-128">Требования</span><span class="sxs-lookup"><span data-stu-id="40583-128">Requirements</span></span>  

 <span data-ttu-id="40583-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40583-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40583-130">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40583-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40583-131">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40583-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40583-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40583-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40583-133">См. также</span><span class="sxs-lookup"><span data-stu-id="40583-133">See also</span></span>

- [<span data-ttu-id="40583-134">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="40583-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
