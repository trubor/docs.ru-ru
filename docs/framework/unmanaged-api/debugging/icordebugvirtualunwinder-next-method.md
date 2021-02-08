---
description: 'Дополнительные сведения о методе: ICorDebugVirtualUnwinder:: Next'
title: Метод ICorDebugVirtualUnwinder::Next
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: b509e8e4fb24c66764999e67ba7e36299ce7f570
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790520"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="6732c-103">Метод ICorDebugVirtualUnwinder::Next</span><span class="sxs-lookup"><span data-stu-id="6732c-103">ICorDebugVirtualUnwinder::Next Method</span></span>

<span data-ttu-id="6732c-104">Переходит в контекст вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="6732c-104">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6732c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6732c-105">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="6732c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6732c-106">Parameters</span></span>  

 <span data-ttu-id="6732c-107">Нет.</span><span class="sxs-lookup"><span data-stu-id="6732c-107">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6732c-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6732c-108">Return Value</span></span>  

 <span data-ttu-id="6732c-109">Значение `S_OK`, если очистка произошла успешно, или значение `CORDBG_S_AT_END_OF_STACK`, если не удалось завершить очистку, поскольку больше нет фреймов.</span><span class="sxs-lookup"><span data-stu-id="6732c-109">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="6732c-110">Если возвращается значение HRESULT, указывающее на ошибку, API ICorDebug будут возвращать `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="6732c-110">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6732c-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="6732c-111">Remarks</span></span>  

 <span data-ttu-id="6732c-112">Обходчик стека должен проверять, что он продвигается вперед, поэтому в конечном итоге вызов `Next` вернет значение HRESULT, указывающее на ошибку, или значение `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="6732c-112">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="6732c-113">Неопределенный возврат `S_OK` может привести к бесконечному циклу.</span><span class="sxs-lookup"><span data-stu-id="6732c-113">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6732c-114">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="6732c-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6732c-115">Требования</span><span class="sxs-lookup"><span data-stu-id="6732c-115">Requirements</span></span>  

 <span data-ttu-id="6732c-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6732c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6732c-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6732c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6732c-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6732c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6732c-119">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6732c-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6732c-120">См. также</span><span class="sxs-lookup"><span data-stu-id="6732c-120">See also</span></span>

- [<span data-ttu-id="6732c-121">Интерфейс ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="6732c-121">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="6732c-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6732c-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
