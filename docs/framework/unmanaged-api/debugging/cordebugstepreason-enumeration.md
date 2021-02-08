---
description: Дополнительные сведения о перечислении Кордебугстепреасон
title: Перечисление CorDebugStepReason
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 2a331b09709ffb6179f2e481baf4bf421d60ea99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801544"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="1b545-103">Перечисление CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="1b545-103">CorDebugStepReason Enumeration</span></span>

<span data-ttu-id="1b545-104">Указывает результат отдельного шага.</span><span class="sxs-lookup"><span data-stu-id="1b545-104">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b545-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1b545-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a><span data-ttu-id="1b545-106">Члены</span><span class="sxs-lookup"><span data-stu-id="1b545-106">Members</span></span>  
  
|<span data-ttu-id="1b545-107">Член</span><span class="sxs-lookup"><span data-stu-id="1b545-107">Member</span></span>|<span data-ttu-id="1b545-108">Описание</span><span class="sxs-lookup"><span data-stu-id="1b545-108">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="1b545-109">Пошаговое завершение нормального выполнения в одной и той же функции.</span><span class="sxs-lookup"><span data-stu-id="1b545-109">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="1b545-110">Пошаговое продолжение обычно после возвращения функции.</span><span class="sxs-lookup"><span data-stu-id="1b545-110">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="1b545-111">Пошаговое продолжение обычно в начале вновь вызванной функции.</span><span class="sxs-lookup"><span data-stu-id="1b545-111">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="1b545-112">Было создано исключение, и управление было передано в фильтр исключений.</span><span class="sxs-lookup"><span data-stu-id="1b545-112">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="1b545-113">Было создано исключение, а Управление было передано обработчику исключений.</span><span class="sxs-lookup"><span data-stu-id="1b545-113">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="1b545-114">Элемент управления передан перехватчику.</span><span class="sxs-lookup"><span data-stu-id="1b545-114">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="1b545-115">Поток завершил работу до завершения шага.</span><span class="sxs-lookup"><span data-stu-id="1b545-115">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b545-116">Требования</span><span class="sxs-lookup"><span data-stu-id="1b545-116">Requirements</span></span>  

 <span data-ttu-id="1b545-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b545-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b545-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b545-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b545-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b545-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b545-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b545-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b545-121">См. также</span><span class="sxs-lookup"><span data-stu-id="1b545-121">See also</span></span>

- [<span data-ttu-id="1b545-122">Метод StepComplete</span><span class="sxs-lookup"><span data-stu-id="1b545-122">StepComplete Method</span></span>](icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="1b545-123">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="1b545-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
