---
description: 'Дополнительные сведения о: интерфейс ICorDebugVirtualUnwinder'
title: Интерфейс ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: e941ace2e7f72c9f7956c03bae19f9b92094b338
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738082"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="07b67-103">Интерфейс ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="07b67-103">ICorDebugVirtualUnwinder Interface</span></span>

<span data-ttu-id="07b67-104">Предоставляет методы, помогающие очистить стек.</span><span class="sxs-lookup"><span data-stu-id="07b67-104">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07b67-105">Методы</span><span class="sxs-lookup"><span data-stu-id="07b67-105">Methods</span></span>  
  
|<span data-ttu-id="07b67-106">Метод</span><span class="sxs-lookup"><span data-stu-id="07b67-106">Method</span></span>|<span data-ttu-id="07b67-107">Имя</span><span class="sxs-lookup"><span data-stu-id="07b67-107">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="07b67-108">Метод GetContext</span><span class="sxs-lookup"><span data-stu-id="07b67-108">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="07b67-109">Получает текущий контекст этого средства очистки.</span><span class="sxs-lookup"><span data-stu-id="07b67-109">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="07b67-110">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="07b67-110">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="07b67-111">Переходит в контекст вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="07b67-111">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07b67-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="07b67-112">Remarks</span></span>  

 <span data-ttu-id="07b67-113">Элементы интерфейса `ICorDebugVirtualUnwinder` реализуются отладчиком для упрощения очистки стека.</span><span class="sxs-lookup"><span data-stu-id="07b67-113">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07b67-114">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="07b67-114">This interface is available with .NET Native only.</span></span> <span data-ttu-id="07b67-115">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="07b67-115">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07b67-116">Требования</span><span class="sxs-lookup"><span data-stu-id="07b67-116">Requirements</span></span>  

 <span data-ttu-id="07b67-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07b67-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07b67-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07b67-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07b67-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07b67-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07b67-120">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07b67-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07b67-121">См. также</span><span class="sxs-lookup"><span data-stu-id="07b67-121">See also</span></span>

- [<span data-ttu-id="07b67-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="07b67-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="07b67-123">Отладка</span><span class="sxs-lookup"><span data-stu-id="07b67-123">Debugging</span></span>](index.md)
