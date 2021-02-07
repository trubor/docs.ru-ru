---
description: 'Дополнительные сведения о: интерфейс Икордебугбреакпоинт'
title: Интерфейс ICorDebugBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 63917512cceeccedea37acdf2ba7ab3b849d9fad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711808"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="67225-103">Интерфейс ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="67225-103">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="67225-104">Представляет точку останова в функции или точку контрольного значения.</span><span class="sxs-lookup"><span data-stu-id="67225-104">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="67225-105">Методы</span><span class="sxs-lookup"><span data-stu-id="67225-105">Methods</span></span>  
  
|<span data-ttu-id="67225-106">Метод</span><span class="sxs-lookup"><span data-stu-id="67225-106">Method</span></span>|<span data-ttu-id="67225-107">Описание</span><span class="sxs-lookup"><span data-stu-id="67225-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="67225-108">Метод Activate</span><span class="sxs-lookup"><span data-stu-id="67225-108">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="67225-109">Задает активное состояние этого объекта `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="67225-109">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="67225-110">Метод IsActive</span><span class="sxs-lookup"><span data-stu-id="67225-110">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="67225-111">Возвращает значение, указывающее, является ли этот объект `ICorDebugBreakpoint` активным.</span><span class="sxs-lookup"><span data-stu-id="67225-111">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67225-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="67225-112">Remarks</span></span>  

 <span data-ttu-id="67225-113">Точки останова не поддерживают непосредственно условные выражения.</span><span class="sxs-lookup"><span data-stu-id="67225-113">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="67225-114">Если требуется такая функциональность, отладчик должен реализовать его поверх `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="67225-114">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="67225-115">Интерфейс ICorDebugFunctionBreakpoint расширяется `ICorDebugBreakpoint` для поддержки точек останова в функциях.</span><span class="sxs-lookup"><span data-stu-id="67225-115">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67225-116">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="67225-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67225-117">Требования</span><span class="sxs-lookup"><span data-stu-id="67225-117">Requirements</span></span>  

 <span data-ttu-id="67225-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67225-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67225-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67225-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67225-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67225-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67225-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67225-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67225-122">См. также</span><span class="sxs-lookup"><span data-stu-id="67225-122">See also</span></span>

- [<span data-ttu-id="67225-123">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="67225-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
