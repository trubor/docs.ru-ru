---
description: Дополнительные сведения о перечислении Кордебужексцептионфлагс
title: Перечисление CorDebugExceptionFlags
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
ms.openlocfilehash: c0036c2674f3202623da1a8fdeea14165a2a6e62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747053"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="3b395-103">Перечисление CorDebugExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="3b395-103">CorDebugExceptionFlags Enumeration</span></span>

<span data-ttu-id="3b395-104">Предоставляет дополнительные сведения об исключении.</span><span class="sxs-lookup"><span data-stu-id="3b395-104">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b395-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3b395-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="3b395-106">Члены</span><span class="sxs-lookup"><span data-stu-id="3b395-106">Members</span></span>  
  
|<span data-ttu-id="3b395-107">Член</span><span class="sxs-lookup"><span data-stu-id="3b395-107">Member</span></span>|<span data-ttu-id="3b395-108">Описание</span><span class="sxs-lookup"><span data-stu-id="3b395-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="3b395-109">Исключение отсутствует.</span><span class="sxs-lookup"><span data-stu-id="3b395-109">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="3b395-110">Исключение доступно для перехвата.</span><span class="sxs-lookup"><span data-stu-id="3b395-110">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="3b395-111">Время исключения все еще может быть таким, что отладчик не сможет его перехватить.</span><span class="sxs-lookup"><span data-stu-id="3b395-111">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="3b395-112">Например, если ниже текущего обратного вызова или события исключения, возникшего в результате JIT-вложения, нет никакого управляемого кода, такое исключение не может быть перехвачено.</span><span class="sxs-lookup"><span data-stu-id="3b395-112">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b395-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="3b395-113">Remarks</span></span>  

 <span data-ttu-id="3b395-114">В более поздних версиях для этого перечисления могут быть добавлены новые значения, поэтому следует подготовить код, использующий `CorDebugExceptionFlags` для неожиданных значений.</span><span class="sxs-lookup"><span data-stu-id="3b395-114">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b395-115">Требования</span><span class="sxs-lookup"><span data-stu-id="3b395-115">Requirements</span></span>  

 <span data-ttu-id="3b395-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b395-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b395-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b395-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b395-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b395-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b395-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b395-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b395-120">См. также</span><span class="sxs-lookup"><span data-stu-id="3b395-120">See also</span></span>

- [<span data-ttu-id="3b395-121">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="3b395-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
