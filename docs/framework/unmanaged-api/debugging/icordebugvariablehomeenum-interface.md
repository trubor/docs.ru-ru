---
description: 'Дополнительные сведения о: интерфейс ICorDebugVariableHomeEnum'
title: Интерфейс ICorDebugVariableHomeEnum
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: c56c68a6b5f9d329fe8af23f47b40fa629bfe3ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790624"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="0f382-103">Интерфейс ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="0f382-103">ICorDebugVariableHomeEnum Interface</span></span>

<span data-ttu-id="0f382-104">Предоставляет перечислитель для локальных переменных и аргументов в функции.</span><span class="sxs-lookup"><span data-stu-id="0f382-104">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f382-105">Методы</span><span class="sxs-lookup"><span data-stu-id="0f382-105">Methods</span></span>  
  
|<span data-ttu-id="0f382-106">Метод</span><span class="sxs-lookup"><span data-stu-id="0f382-106">Method</span></span>|<span data-ttu-id="0f382-107">Описание</span><span class="sxs-lookup"><span data-stu-id="0f382-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f382-108">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="0f382-108">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="0f382-109">Возвращает указанное число экземпляров [ICorDebugVariableHome](icordebugvariablehome-interface.md) , содержащих сведения о локальных переменных и аргументах в функции.</span><span class="sxs-lookup"><span data-stu-id="0f382-109">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f382-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="0f382-110">Remarks</span></span>  

 <span data-ttu-id="0f382-111">`ICorDebugVariableHomeEnum`Интерфейс реализует интерфейс ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="0f382-111">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="0f382-112">`ICorDebugVariableHomeEnum`Экземпляр заполняется экземплярами [ICorDebugVariableHome](icordebugvariablehome-interface.md) путем вызова метода [ICorDebugCode4:: енумератевариаблехомес](icordebugcode4-enumeratevariablehomes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0f382-112">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="0f382-113">Каждый экземпляр [ICorDebugVariableHome](icordebugvariablehome-interface.md) в коллекции представляет локальную переменную или аргумент в функции.</span><span class="sxs-lookup"><span data-stu-id="0f382-113">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="0f382-114">Объекты  [ICorDebugVariableHome](icordebugvariablehome-interface.md) в коллекции можно перечислить, вызвав метод [ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0f382-114">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f382-115">Требования</span><span class="sxs-lookup"><span data-stu-id="0f382-115">Requirements</span></span>  

 <span data-ttu-id="0f382-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f382-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f382-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f382-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f382-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f382-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f382-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f382-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f382-120">См. также</span><span class="sxs-lookup"><span data-stu-id="0f382-120">See also</span></span>

- [<span data-ttu-id="0f382-121">Интерфейс ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="0f382-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="0f382-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="0f382-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
