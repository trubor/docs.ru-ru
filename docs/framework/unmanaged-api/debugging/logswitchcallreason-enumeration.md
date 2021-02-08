---
description: Дополнительные сведения о перечислении Логсвитчкаллреасон
title: Перечисление LogSwitchCallReason
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
ms.openlocfilehash: 46c457ee4c12fe9a73796aa7b7a5f599d90c9c6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800618"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="ff2bc-103">Перечисление LogSwitchCallReason</span><span class="sxs-lookup"><span data-stu-id="ff2bc-103">LogSwitchCallReason Enumeration</span></span>

<span data-ttu-id="ff2bc-104">Указывает операцию, выполненную на переключателе отладки и трассировки.</span><span class="sxs-lookup"><span data-stu-id="ff2bc-104">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff2bc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ff2bc-105">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="ff2bc-106">Члены</span><span class="sxs-lookup"><span data-stu-id="ff2bc-106">Members</span></span>  
  
|<span data-ttu-id="ff2bc-107">Член</span><span class="sxs-lookup"><span data-stu-id="ff2bc-107">Member</span></span>|<span data-ttu-id="ff2bc-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ff2bc-108">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="ff2bc-109">Был создан переключатель отладки/трассировки.</span><span class="sxs-lookup"><span data-stu-id="ff2bc-109">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="ff2bc-110">Изменен параметр отладки/трассировки.</span><span class="sxs-lookup"><span data-stu-id="ff2bc-110">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="ff2bc-111">Удален параметр отладки/трассировки.</span><span class="sxs-lookup"><span data-stu-id="ff2bc-111">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ff2bc-112">Требования</span><span class="sxs-lookup"><span data-stu-id="ff2bc-112">Requirements</span></span>  

 <span data-ttu-id="ff2bc-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff2bc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff2bc-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff2bc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff2bc-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff2bc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff2bc-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff2bc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff2bc-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ff2bc-117">See also</span></span>

- [<span data-ttu-id="ff2bc-118">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="ff2bc-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
