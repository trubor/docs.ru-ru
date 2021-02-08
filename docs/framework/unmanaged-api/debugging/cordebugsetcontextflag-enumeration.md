---
description: Дополнительные сведения о перечислении Кордебугсетконтекстфлаг
title: Перечисление CorDebugSetContextFlag
ms.date: 03/30/2017
api_name:
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
ms.openlocfilehash: 625f24e516ff462cf3d0e628dfff6c08793807ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801557"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="c735f-103">Перечисление CorDebugSetContextFlag</span><span class="sxs-lookup"><span data-stu-id="c735f-103">CorDebugSetContextFlag Enumeration</span></span>

<span data-ttu-id="c735f-104">Указывает происхождение контекста: взят из активного (или листового) кадра в стеке или был вычислен в результате освобождения другого кадра.</span><span class="sxs-lookup"><span data-stu-id="c735f-104">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c735f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c735f-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="c735f-106">Члены</span><span class="sxs-lookup"><span data-stu-id="c735f-106">Members</span></span>  
  
|<span data-ttu-id="c735f-107">Член</span><span class="sxs-lookup"><span data-stu-id="c735f-107">Member</span></span>|<span data-ttu-id="c735f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c735f-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c735f-109">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="c735f-109">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="c735f-110">Контекст является активным контекстом потока.</span><span class="sxs-lookup"><span data-stu-id="c735f-110">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="c735f-111">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="c735f-111">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="c735f-112">Контекст был вычислен путем очистки от другого кадра.</span><span class="sxs-lookup"><span data-stu-id="c735f-112">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c735f-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="c735f-113">Remarks</span></span>  

 <span data-ttu-id="c735f-114">`CorDebugSetContextFlag` предоставляет значения, используемые методом [икордебугстакквалк:: SetContext](icordebugstackwalk-setcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c735f-114">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c735f-115">Требования</span><span class="sxs-lookup"><span data-stu-id="c735f-115">Requirements</span></span>  

 <span data-ttu-id="c735f-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c735f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c735f-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c735f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c735f-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c735f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c735f-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c735f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c735f-120">См. также</span><span class="sxs-lookup"><span data-stu-id="c735f-120">See also</span></span>

- [<span data-ttu-id="c735f-121">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="c735f-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="c735f-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="c735f-122">Debugging</span></span>](index.md)
