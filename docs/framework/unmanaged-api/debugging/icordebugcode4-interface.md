---
description: 'Дополнительные сведения о: интерфейс ICorDebugCode4'
title: Интерфейс ICorDebugCode4
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
ms.openlocfilehash: 1276db5c55c3d98e5ffa379f6126f700d93c1670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764727"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="ecda3-103">Интерфейс ICorDebugCode4</span><span class="sxs-lookup"><span data-stu-id="ecda3-103">ICorDebugCode4 Interface</span></span>

<span data-ttu-id="ecda3-104">Предоставляет метод, позволяющий отладчику перечислить локальные переменные и аргументы в функции.</span><span class="sxs-lookup"><span data-stu-id="ecda3-104">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ecda3-105">Методы</span><span class="sxs-lookup"><span data-stu-id="ecda3-105">Methods</span></span>  
  
|<span data-ttu-id="ecda3-106">Метод</span><span class="sxs-lookup"><span data-stu-id="ecda3-106">Method</span></span>|<span data-ttu-id="ecda3-107">Описание</span><span class="sxs-lookup"><span data-stu-id="ecda3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ecda3-108">Метод EnumerateVariableHomes</span><span class="sxs-lookup"><span data-stu-id="ecda3-108">EnumerateVariableHomes Method</span></span>](icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="ecda3-109">Возвращает перечислитель для локальных переменных и аргументов в функции.</span><span class="sxs-lookup"><span data-stu-id="ecda3-109">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecda3-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="ecda3-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecda3-111">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="ecda3-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecda3-112">Требования</span><span class="sxs-lookup"><span data-stu-id="ecda3-112">Requirements</span></span>  

 <span data-ttu-id="ecda3-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecda3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecda3-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ecda3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ecda3-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ecda3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecda3-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecda3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecda3-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ecda3-117">See also</span></span>

- [<span data-ttu-id="ecda3-118">Интерфейс ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="ecda3-118">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="ecda3-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="ecda3-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
