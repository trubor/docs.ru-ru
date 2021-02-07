---
description: Дополнительные сведения о перечислении CorDebugIntercept
title: Перечисление CorDebugIntercept
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
ms.openlocfilehash: ddd17aff309396fdcda37c731ff907224ee17db2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661978"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="61210-103">Перечисление CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="61210-103">CorDebugIntercept Enumeration</span></span>

<span data-ttu-id="61210-104">Указывает типы кода, которые могут быть перехвачены (то есть типы, для которых возможно пошаговое выполнение).</span><span class="sxs-lookup"><span data-stu-id="61210-104">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61210-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="61210-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a><span data-ttu-id="61210-106">Члены</span><span class="sxs-lookup"><span data-stu-id="61210-106">Members</span></span>  
  
|<span data-ttu-id="61210-107">Член</span><span class="sxs-lookup"><span data-stu-id="61210-107">Member</span></span>|<span data-ttu-id="61210-108">Описание</span><span class="sxs-lookup"><span data-stu-id="61210-108">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="61210-109">Перехват кода невозможен.</span><span class="sxs-lookup"><span data-stu-id="61210-109">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="61210-110">Допускается перехват конструктора.</span><span class="sxs-lookup"><span data-stu-id="61210-110">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="61210-111">Допускается перехват исключения.</span><span class="sxs-lookup"><span data-stu-id="61210-111">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="61210-112">Допускается перехват кода, который принудительно включает систему безопасности.</span><span class="sxs-lookup"><span data-stu-id="61210-112">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="61210-113">Допускается перехват политики контекста.</span><span class="sxs-lookup"><span data-stu-id="61210-113">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="61210-114">Не используется.</span><span class="sxs-lookup"><span data-stu-id="61210-114">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="61210-115">Возможен перехват любого кода.</span><span class="sxs-lookup"><span data-stu-id="61210-115">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61210-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="61210-116">Remarks</span></span>  

 <span data-ttu-id="61210-117">Используйте метод [ICorDebugStepper:: сетинтерцептмаск](icordebugstepper-setinterceptmask-method.md) , чтобы установить типы кода, которые могут быть перехвачены.</span><span class="sxs-lookup"><span data-stu-id="61210-117">Use the [ICorDebugStepper::SetInterceptMask](icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61210-118">Требования</span><span class="sxs-lookup"><span data-stu-id="61210-118">Requirements</span></span>  

 <span data-ttu-id="61210-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61210-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61210-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61210-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61210-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61210-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61210-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61210-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61210-123">См. также</span><span class="sxs-lookup"><span data-stu-id="61210-123">See also</span></span>

- [<span data-ttu-id="61210-124">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="61210-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
