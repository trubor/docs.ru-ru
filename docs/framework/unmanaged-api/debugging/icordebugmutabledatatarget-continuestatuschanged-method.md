---
description: 'Дополнительные сведения о методе: Икордебугмутабледататаржет:: Континуестатусчанжед'
title: Метод ICorDebugMutableDataTarget::ContinueStatusChanged
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: 6655d6f1a115b4879c73e356faa8e8785a110078
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722507"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="ebc62-103">Метод ICorDebugMutableDataTarget::ContinueStatusChanged</span><span class="sxs-lookup"><span data-stu-id="ebc62-103">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>

<span data-ttu-id="ebc62-104">Изменяет состояние продолжения для незавершенных событий отладки в указанном потоке.</span><span class="sxs-lookup"><span data-stu-id="ebc62-104">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebc62-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ebc62-105">Syntax</span></span>  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebc62-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ebc62-106">Parameters</span></span>  

 `dwThreadId`  
 <span data-ttu-id="ebc62-107">Идентификатор потока, определяемый операционной системой.</span><span class="sxs-lookup"><span data-stu-id="ebc62-107">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="ebc62-108">Значение [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md), которое представляет новое запрошенное состояние продолжения.</span><span class="sxs-lookup"><span data-stu-id="ebc62-108">A [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebc62-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="ebc62-109">Remarks</span></span>  

 <span data-ttu-id="ebc62-110">Отладчик вызывает метод `ContinueStatusChanged` при вызове метода ICorDebug, требующего, чтобы способ обработки текущего события отладки потенциально отличался от способа, которым оно обычно обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="ebc62-110">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="ebc62-111">Например, если имеется незавершенное исключение и отладчик запрашивает операцию, которая будет отменять это исключение (например, [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) или `FuncEval`), этот API используется для запроса отмены исключения.</span><span class="sxs-lookup"><span data-stu-id="ebc62-111">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebc62-112">Требования</span><span class="sxs-lookup"><span data-stu-id="ebc62-112">Requirements</span></span>  

 <span data-ttu-id="ebc62-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebc62-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebc62-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebc62-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebc62-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebc62-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebc62-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebc62-116">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc62-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ebc62-117">See also</span></span>

- [<span data-ttu-id="ebc62-118">Интерфейс ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="ebc62-118">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="ebc62-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="ebc62-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
