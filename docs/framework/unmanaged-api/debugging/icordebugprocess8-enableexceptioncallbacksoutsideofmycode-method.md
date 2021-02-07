---
description: 'Дополнительные сведения о методе: ICorDebugProcess8:: Енабликсцептионкаллбакксаутсидеофмикоде'
title: Метод ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: a85c9d62e5fb62fe620f0901509afa5a03504d4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691280"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="cc6e9-103">Метод ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode</span><span class="sxs-lookup"><span data-stu-id="cc6e9-103">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>

<span data-ttu-id="cc6e9-104">[Поддерживается в платформа .NET Framework 4,6 и более поздних версиях]</span><span class="sxs-lookup"><span data-stu-id="cc6e9-104">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="cc6e9-105">Включает или отключает определенные типы обратных вызовов исключений [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="cc6e9-105">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc6e9-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cc6e9-106">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc6e9-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="cc6e9-107">Parameters</span></span>  

 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="cc6e9-108">[in]</span><span class="sxs-lookup"><span data-stu-id="cc6e9-108">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc6e9-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="cc6e9-109">Remarks</span></span>  

 <span data-ttu-id="cc6e9-110">Если `enableExceptionsOutsideOfJMC` имеет значение `false`:</span><span class="sxs-lookup"><span data-stu-id="cc6e9-110">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="cc6e9-111">Исключение DEBUG_EXCEPTION_FIRST_CHANCE не будет приводить к обратному вызову отладчика.</span><span class="sxs-lookup"><span data-stu-id="cc6e9-111">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="cc6e9-112">Исключение DEBUG_EXCEPTION_CATCH_HANDLER_FOUND не приводит к обратному вызову отладчика, если исключение никогда не попадает в пользовательский код (то есть путь от источника исключения в обработчик исключений не имеет методов, помеченных как JustMyCode или JMC).</span><span class="sxs-lookup"><span data-stu-id="cc6e9-112">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="cc6e9-113">Значением свойства `enableExceptionsOutsideOfJMC` по умолчанию является `true`.</span><span class="sxs-lookup"><span data-stu-id="cc6e9-113">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc6e9-114">Требования</span><span class="sxs-lookup"><span data-stu-id="cc6e9-114">Requirements</span></span>  

 <span data-ttu-id="cc6e9-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc6e9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc6e9-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc6e9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc6e9-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc6e9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc6e9-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc6e9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc6e9-119">См. также</span><span class="sxs-lookup"><span data-stu-id="cc6e9-119">See also</span></span>

- [<span data-ttu-id="cc6e9-120">Интерфейс ICorDebugProcess8</span><span class="sxs-lookup"><span data-stu-id="cc6e9-120">ICorDebugProcess8 Interface</span></span>](icordebugprocess8-interface.md)
- [<span data-ttu-id="cc6e9-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="cc6e9-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
