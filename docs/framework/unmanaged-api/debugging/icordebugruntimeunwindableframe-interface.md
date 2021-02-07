---
description: 'Дополнительные сведения о: интерфейс Икордебугрунтимеунвиндаблефраме'
title: Интерфейс ICorDebugRuntimeUnwindableFrame
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
ms.openlocfilehash: e83ede8265a400b30f2202115bf47aed6ea43e5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717814"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="bc6fc-103">Интерфейс ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="bc6fc-103">ICorDebugRuntimeUnwindableFrame Interface</span></span>

<span data-ttu-id="bc6fc-104">Предоставляет поддержку для неуправляемых методов, которым требуется среда CLR для раскручивания кадра.</span><span class="sxs-lookup"><span data-stu-id="bc6fc-104">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc6fc-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="bc6fc-105">Remarks</span></span>  

 <span data-ttu-id="bc6fc-106">`ICorDebugRuntimeUnwindableFrame` — Это специализированная версия интерфейса ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="bc6fc-106">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="bc6fc-107">Он используется неуправляемыми методами, требующими от среды выполнения очистки кадра в текущем стеке.</span><span class="sxs-lookup"><span data-stu-id="bc6fc-107">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="bc6fc-108">Существующие правила очистки не работают, так как они не используют JIT-скомпилированный код.</span><span class="sxs-lookup"><span data-stu-id="bc6fc-108">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="bc6fc-109">Когда отладчик видит неотображаемый кадр, он должен использовать метод [икордебугстакквалк:: Next](icordebugstackwalk-next-method.md) для его очистки, но должен выполнить проверку.</span><span class="sxs-lookup"><span data-stu-id="bc6fc-109">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="bc6fc-110">Когда отладчик получает объект `ICorDebugRuntimeUnwindableFrame` , он может вызвать метод [икордебугстакквалк:: oncontext](icordebugstackwalk-getcontext-method.md) для получения контекста кадра.</span><span class="sxs-lookup"><span data-stu-id="bc6fc-110">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc6fc-111">Требования</span><span class="sxs-lookup"><span data-stu-id="bc6fc-111">Requirements</span></span>  

 <span data-ttu-id="bc6fc-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc6fc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc6fc-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc6fc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc6fc-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc6fc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc6fc-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc6fc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6fc-116">См. также</span><span class="sxs-lookup"><span data-stu-id="bc6fc-116">See also</span></span>

- [<span data-ttu-id="bc6fc-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="bc6fc-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bc6fc-118">Отладка</span><span class="sxs-lookup"><span data-stu-id="bc6fc-118">Debugging</span></span>](index.md)
