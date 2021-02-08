---
description: 'Дополнительные сведения о: Интерфейс ICorDebugRegisterSet2'
title: Интерфейс ICorDebugRegisterSet2
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: 3501325df188879f5687347ef329f490b487d9d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803611"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="76519-103">Интерфейс ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="76519-103">ICorDebugRegisterSet2 Interface</span></span>

<span data-ttu-id="76519-104">Расширяет возможности интерфейса [ICorDebugRegisterSet](icordebugregisterset-interface.md) для аппаратных платформ, имеющих более 64 регистров.</span><span class="sxs-lookup"><span data-stu-id="76519-104">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="76519-105">Методы</span><span class="sxs-lookup"><span data-stu-id="76519-105">Methods</span></span>  
  
|<span data-ttu-id="76519-106">Метод</span><span class="sxs-lookup"><span data-stu-id="76519-106">Method</span></span>|<span data-ttu-id="76519-107">Описание</span><span class="sxs-lookup"><span data-stu-id="76519-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="76519-108">Метод GetRegisters</span><span class="sxs-lookup"><span data-stu-id="76519-108">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="76519-109">Возвращает значение каждого регистра (на компьютере, выполняющем в данный момент код), который задается битовой маской.</span><span class="sxs-lookup"><span data-stu-id="76519-109">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="76519-110">Метод GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="76519-110">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="76519-111">Возвращает массив байтов, предоставляющий битовую карту доступных регистров.</span><span class="sxs-lookup"><span data-stu-id="76519-111">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="76519-112">Метод SetRegisters</span><span class="sxs-lookup"><span data-stu-id="76519-112">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="76519-113">Не реализовано в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="76519-113">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76519-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="76519-114">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76519-115">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="76519-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76519-116">Требования</span><span class="sxs-lookup"><span data-stu-id="76519-116">Requirements</span></span>  

 <span data-ttu-id="76519-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76519-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76519-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76519-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76519-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76519-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76519-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76519-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76519-121">См. также</span><span class="sxs-lookup"><span data-stu-id="76519-121">See also</span></span>

- [<span data-ttu-id="76519-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="76519-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="76519-123">Интерфейс ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="76519-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
