---
description: 'Дополнительные сведения о: интерфейс ICorDebugFunctionBreakpoint'
title: Интерфейс ICorDebugFunctionBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
ms.openlocfilehash: 5d7597369241272d91de4b94a60d787304dc1c6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661133"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="39991-103">Интерфейс ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="39991-103">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="39991-104">Расширяет интерфейс Икордебугбреакпоинт для поддержки точек останова в функциях.</span><span class="sxs-lookup"><span data-stu-id="39991-104">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39991-105">Методы</span><span class="sxs-lookup"><span data-stu-id="39991-105">Methods</span></span>  
  
|<span data-ttu-id="39991-106">Метод</span><span class="sxs-lookup"><span data-stu-id="39991-106">Method</span></span>|<span data-ttu-id="39991-107">Описание</span><span class="sxs-lookup"><span data-stu-id="39991-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39991-108">Метод GetFunction</span><span class="sxs-lookup"><span data-stu-id="39991-108">GetFunction Method</span></span>](icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="39991-109">Возвращает указатель на интерфейс ICorDebugFunction, ссылающийся на функцию, в которой задана точка останова.</span><span class="sxs-lookup"><span data-stu-id="39991-109">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="39991-110">Метод GetOffset</span><span class="sxs-lookup"><span data-stu-id="39991-110">GetOffset Method</span></span>](icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="39991-111">Возвращает смещение точки останова внутри функции.</span><span class="sxs-lookup"><span data-stu-id="39991-111">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39991-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="39991-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39991-113">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="39991-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39991-114">Требования</span><span class="sxs-lookup"><span data-stu-id="39991-114">Requirements</span></span>  

 <span data-ttu-id="39991-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39991-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39991-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39991-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39991-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39991-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39991-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39991-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39991-119">См. также</span><span class="sxs-lookup"><span data-stu-id="39991-119">See also</span></span>

- [<span data-ttu-id="39991-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="39991-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
