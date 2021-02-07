---
description: Дополнительные сведения о перечислении Кордебужексцептионунвиндкаллбакктипе
title: Перечисление CorDebugExceptionUnwindCallbackType
ms.date: 03/30/2017
api_name:
- CorDebugExceptionUnwindCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionUnwindCallbackType
helpviewer_keywords:
- CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type:
- apiref
ms.openlocfilehash: 3e12cffcdf1eb921330f658215c52501dce83eff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747028"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="9e0f2-103">Перечисление CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="9e0f2-103">CorDebugExceptionUnwindCallbackType Enumeration</span></span>

<span data-ttu-id="9e0f2-104">Указывает событие, о котором сообщает обратный вызов во время фазы перемотки.</span><span class="sxs-lookup"><span data-stu-id="9e0f2-104">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e0f2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9e0f2-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="9e0f2-106">Члены</span><span class="sxs-lookup"><span data-stu-id="9e0f2-106">Members</span></span>  
  
|<span data-ttu-id="9e0f2-107">Член</span><span class="sxs-lookup"><span data-stu-id="9e0f2-107">Member</span></span>|<span data-ttu-id="9e0f2-108">Описание</span><span class="sxs-lookup"><span data-stu-id="9e0f2-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="9e0f2-109">Начало процесса очистки.</span><span class="sxs-lookup"><span data-stu-id="9e0f2-109">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="9e0f2-110">Исключение перехвачено.</span><span class="sxs-lookup"><span data-stu-id="9e0f2-110">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e0f2-111">Требования</span><span class="sxs-lookup"><span data-stu-id="9e0f2-111">Requirements</span></span>  

 <span data-ttu-id="9e0f2-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e0f2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e0f2-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e0f2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e0f2-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e0f2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e0f2-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e0f2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0f2-116">См. также</span><span class="sxs-lookup"><span data-stu-id="9e0f2-116">See also</span></span>

- [<span data-ttu-id="9e0f2-117">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="9e0f2-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
