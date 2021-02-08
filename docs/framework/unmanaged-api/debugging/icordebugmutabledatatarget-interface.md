---
description: 'Дополнительные сведения о: интерфейс Икордебугмутабледататаржет'
title: Интерфейс ICorDebugMutableDataTarget
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: 387c5317bea015459e306994c36761571b427628
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790702"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="4fe0c-103">Интерфейс ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="4fe0c-103">ICorDebugMutableDataTarget Interface</span></span>

<span data-ttu-id="4fe0c-104">Расширяет интерфейс [ICorDebugDataTarget](icordebugdatatarget-interface.md) для поддержки целевых объектов данных.</span><span class="sxs-lookup"><span data-stu-id="4fe0c-104">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4fe0c-105">Методы</span><span class="sxs-lookup"><span data-stu-id="4fe0c-105">Methods</span></span>  
  
|<span data-ttu-id="4fe0c-106">Метод</span><span class="sxs-lookup"><span data-stu-id="4fe0c-106">Method</span></span>|<span data-ttu-id="4fe0c-107">Описание</span><span class="sxs-lookup"><span data-stu-id="4fe0c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4fe0c-108">Метод ContinueStatusChanged</span><span class="sxs-lookup"><span data-stu-id="4fe0c-108">ContinueStatusChanged Method</span></span>](icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="4fe0c-109">Изменяет состояние продолжения для незавершенных событий отладки в указанном потоке.</span><span class="sxs-lookup"><span data-stu-id="4fe0c-109">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="4fe0c-110">Метод SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="4fe0c-110">SetThreadContext Method</span></span>](icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="4fe0c-111">Задает контекст (значения регистра) для потока.</span><span class="sxs-lookup"><span data-stu-id="4fe0c-111">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="4fe0c-112">Метод WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="4fe0c-112">WriteVirtual Method</span></span>](icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="4fe0c-113">Записывает память в адресное пространство целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="4fe0c-113">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fe0c-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="4fe0c-114">Remarks</span></span>  

 <span data-ttu-id="4fe0c-115">Это расширение интерфейса [ICorDebugDataTarget](icordebugdatatarget-interface.md) может быть реализовано средствами отладки, которые хотят изменить целевой процесс (например, для выполнения динамической отладки).</span><span class="sxs-lookup"><span data-stu-id="4fe0c-115">This extension to the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="4fe0c-116">Все эти методы являются необязательными в том смысле, что никакая функциональность отладки на основе проверки ядра не будет потеряна, если этот интерфейс не будет реализован или если произойдет сбой вызова этих методов.</span><span class="sxs-lookup"><span data-stu-id="4fe0c-116">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="4fe0c-117">Любое свидетельствующее об ошибке значение `HRESULT` из этих методов будет исключаться, как и значение `HRESULT` из вызова метода ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="4fe0c-117">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="4fe0c-118">Обратите внимание, что единственный вызов метода ICorDebug может привести к нескольким изменениям, и механизм гарантированного применения соответствующих изменений в транзакции (все или ничего) не предусмотрен.</span><span class="sxs-lookup"><span data-stu-id="4fe0c-118">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="4fe0c-119">Это означает, что в случае сбоя изменения после успешного применения других изменений (для того же вызова ICorDebug) целевой процесс может остаться в несогласованном состоянии, и отладка может оказаться ненадежной.</span><span class="sxs-lookup"><span data-stu-id="4fe0c-119">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fe0c-120">Требования</span><span class="sxs-lookup"><span data-stu-id="4fe0c-120">Requirements</span></span>  

 <span data-ttu-id="4fe0c-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fe0c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fe0c-122">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fe0c-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fe0c-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fe0c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fe0c-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fe0c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe0c-125">См. также</span><span class="sxs-lookup"><span data-stu-id="4fe0c-125">See also</span></span>

- [<span data-ttu-id="4fe0c-126">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="4fe0c-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4fe0c-127">Отладка</span><span class="sxs-lookup"><span data-stu-id="4fe0c-127">Debugging</span></span>](index.md)
