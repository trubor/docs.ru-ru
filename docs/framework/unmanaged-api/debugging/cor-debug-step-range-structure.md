---
description: 'Дополнительные сведения: структура COR_DEBUG_STEP_RANGE'
title: Структура COR_DEBUG_STEP_RANGE
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
ms.openlocfilehash: 40462be4b165351b3265fa0833d19f18e0fa3a37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801843"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="a504f-103">Структура COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="a504f-103">COR_DEBUG_STEP_RANGE Structure</span></span>

<span data-ttu-id="a504f-104">Содержит сведения о смещении для диапазона кода.</span><span class="sxs-lookup"><span data-stu-id="a504f-104">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="a504f-105">Эта структура используется методом [ICorDebugStepper:: степранже](icordebugstepper-steprange-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a504f-105">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a504f-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a504f-106">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="a504f-107">Члены</span><span class="sxs-lookup"><span data-stu-id="a504f-107">Members</span></span>  
  
|<span data-ttu-id="a504f-108">Член</span><span class="sxs-lookup"><span data-stu-id="a504f-108">Member</span></span>|<span data-ttu-id="a504f-109">Описание</span><span class="sxs-lookup"><span data-stu-id="a504f-109">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="a504f-110">Смещение начала диапазона.</span><span class="sxs-lookup"><span data-stu-id="a504f-110">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="a504f-111">Смещение конца диапазона.</span><span class="sxs-lookup"><span data-stu-id="a504f-111">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a504f-112">Требования</span><span class="sxs-lookup"><span data-stu-id="a504f-112">Requirements</span></span>  

 <span data-ttu-id="a504f-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a504f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a504f-114">**Заголовок:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="a504f-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="a504f-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a504f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a504f-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a504f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a504f-117">См. также</span><span class="sxs-lookup"><span data-stu-id="a504f-117">See also</span></span>

- [<span data-ttu-id="a504f-118">Метод StepRange</span><span class="sxs-lookup"><span data-stu-id="a504f-118">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="a504f-119">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="a504f-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="a504f-120">Отладка</span><span class="sxs-lookup"><span data-stu-id="a504f-120">Debugging</span></span>](index.md)
