---
description: 'Дополнительные сведения о: интерфейс ICorDebugFunction2'
title: Интерфейс ICorDebugFunction2
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
ms.openlocfilehash: e5297d46acb9b174537363fc185fa2d540d55a75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692203"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="6d2bf-103">Интерфейс ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="6d2bf-103">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="6d2bf-104">Логически расширяет интерфейс ICorDebugFunction, чтобы обеспечить поддержку Только мой код пошаговой отладке, которая пропускает код, не являющийся пользовательским.</span><span class="sxs-lookup"><span data-stu-id="6d2bf-104">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d2bf-105">Методы</span><span class="sxs-lookup"><span data-stu-id="6d2bf-105">Methods</span></span>  
  
|<span data-ttu-id="6d2bf-106">Метод</span><span class="sxs-lookup"><span data-stu-id="6d2bf-106">Method</span></span>|<span data-ttu-id="6d2bf-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6d2bf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d2bf-108">Метод EnumerateNativeCode</span><span class="sxs-lookup"><span data-stu-id="6d2bf-108">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="6d2bf-109">(Еще не реализовано.) Возвращает указатель интерфейса на Икордебугкодинум, содержащий операторы машинного кода в функции, на которую ссылается этот объект ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="6d2bf-109">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="6d2bf-110">Метод GetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="6d2bf-110">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="6d2bf-111">Возвращает значение, указывающее, помечена ли эта функция как пользовательский код.</span><span class="sxs-lookup"><span data-stu-id="6d2bf-111">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="6d2bf-112">Метод GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="6d2bf-112">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="6d2bf-113">Возвращает версию функции "изменить и продолжить".</span><span class="sxs-lookup"><span data-stu-id="6d2bf-113">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="6d2bf-114">Метод SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="6d2bf-114">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="6d2bf-115">Помечает эту функцию для Только мой код пошагового выполнения.</span><span class="sxs-lookup"><span data-stu-id="6d2bf-115">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d2bf-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="6d2bf-116">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d2bf-117">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="6d2bf-117">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d2bf-118">Требования</span><span class="sxs-lookup"><span data-stu-id="6d2bf-118">Requirements</span></span>  

 <span data-ttu-id="6d2bf-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d2bf-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d2bf-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d2bf-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d2bf-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d2bf-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d2bf-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d2bf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2bf-123">См. также</span><span class="sxs-lookup"><span data-stu-id="6d2bf-123">See also</span></span>

- [<span data-ttu-id="6d2bf-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6d2bf-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
