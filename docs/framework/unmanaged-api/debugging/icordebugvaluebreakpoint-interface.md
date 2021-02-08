---
description: 'Дополнительные сведения о: интерфейс ICorDebugValueBreakpoint'
title: Интерфейс ICorDebugValueBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
ms.openlocfilehash: ff53b1f6e1557a3e98cc642f80eaaa2feaeac473
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790689"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="2485f-103">Интерфейс ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2485f-103">ICorDebugValueBreakpoint Interface</span></span>

<span data-ttu-id="2485f-104">Расширяет интерфейс Икордебугбреакпоинт для предоставления доступа к конкретным значениям.</span><span class="sxs-lookup"><span data-stu-id="2485f-104">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2485f-105">Методы</span><span class="sxs-lookup"><span data-stu-id="2485f-105">Methods</span></span>  
  
|<span data-ttu-id="2485f-106">Метод</span><span class="sxs-lookup"><span data-stu-id="2485f-106">Method</span></span>|<span data-ttu-id="2485f-107">Описание</span><span class="sxs-lookup"><span data-stu-id="2485f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2485f-108">Метод GetValue</span><span class="sxs-lookup"><span data-stu-id="2485f-108">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="2485f-109">Возвращает указатель интерфейса на объект ICorDebugValue, представляющий значение объекта, для которого задана точка останова.</span><span class="sxs-lookup"><span data-stu-id="2485f-109">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2485f-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="2485f-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2485f-111">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="2485f-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2485f-112">Требования</span><span class="sxs-lookup"><span data-stu-id="2485f-112">Requirements</span></span>  

 <span data-ttu-id="2485f-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2485f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2485f-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2485f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2485f-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2485f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2485f-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2485f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2485f-117">См. также</span><span class="sxs-lookup"><span data-stu-id="2485f-117">See also</span></span>

- [<span data-ttu-id="2485f-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="2485f-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
