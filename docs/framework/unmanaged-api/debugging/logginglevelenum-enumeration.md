---
description: Дополнительные сведения о перечислении Логгинглевеленум
title: Перечисление LoggingLevelEnum
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
ms.openlocfilehash: 7c9676fef83ea44f45a25350a2b3d325c1c22f98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800619"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="c8916-103">Перечисление LoggingLevelEnum</span><span class="sxs-lookup"><span data-stu-id="c8916-103">LoggingLevelEnum Enumeration</span></span>

<span data-ttu-id="c8916-104">Указывает уровень важности описательного сообщения, записанного в журнале событий при регистрации события управляемым потоком.</span><span class="sxs-lookup"><span data-stu-id="c8916-104">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8916-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c8916-105">Syntax</span></span>  
  
```cpp  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a><span data-ttu-id="c8916-106">Члены</span><span class="sxs-lookup"><span data-stu-id="c8916-106">Members</span></span>  
  
|<span data-ttu-id="c8916-107">Член</span><span class="sxs-lookup"><span data-stu-id="c8916-107">Member</span></span>|<span data-ttu-id="c8916-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c8916-108">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="c8916-109">Сообщение является уровнем трассировки 0.</span><span class="sxs-lookup"><span data-stu-id="c8916-109">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="c8916-110">Сообщение является уровнем трассировки 1.</span><span class="sxs-lookup"><span data-stu-id="c8916-110">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="c8916-111">Сообщение является уровнем трассировки 2.</span><span class="sxs-lookup"><span data-stu-id="c8916-111">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="c8916-112">Сообщение имеет уровень трассировки 3.</span><span class="sxs-lookup"><span data-stu-id="c8916-112">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="c8916-113">Сообщение имеет уровень трассировки 4.</span><span class="sxs-lookup"><span data-stu-id="c8916-113">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="c8916-114">Сообщение имеет уровень состояния 0.</span><span class="sxs-lookup"><span data-stu-id="c8916-114">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="c8916-115">Сообщение имеет уровень состояния 1.</span><span class="sxs-lookup"><span data-stu-id="c8916-115">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="c8916-116">Сообщение имеет уровень состояния 2.</span><span class="sxs-lookup"><span data-stu-id="c8916-116">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="c8916-117">Сообщение имеет уровень состояния 3.</span><span class="sxs-lookup"><span data-stu-id="c8916-117">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="c8916-118">Сообщение имеет уровень состояния 4.</span><span class="sxs-lookup"><span data-stu-id="c8916-118">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="c8916-119">Сообщение является уровнем предупреждения.</span><span class="sxs-lookup"><span data-stu-id="c8916-119">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="c8916-120">Сообщение имеет уровень ошибки.</span><span class="sxs-lookup"><span data-stu-id="c8916-120">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="c8916-121">Сообщение имеет уровень тревоги.</span><span class="sxs-lookup"><span data-stu-id="c8916-121">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8916-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="c8916-122">Remarks</span></span>  

 <span data-ttu-id="c8916-123">Среда CLR вызывает метод [ICorDebugManagedCallback:: LogMessage](icordebugmanagedcallback-logmessage-method.md) , чтобы уведомить отладчик о том, что управляемый поток зарегистрировал событие.</span><span class="sxs-lookup"><span data-stu-id="c8916-123">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="c8916-124">Среда CLR передает значение `LoggingLevelEnum` перечисления, чтобы указать степень серьезности сообщения, которое управляемый поток записал в журнал событий.</span><span class="sxs-lookup"><span data-stu-id="c8916-124">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8916-125">Требования</span><span class="sxs-lookup"><span data-stu-id="c8916-125">Requirements</span></span>  

 <span data-ttu-id="c8916-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8916-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8916-127">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8916-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8916-128">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8916-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8916-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8916-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8916-130">См. также</span><span class="sxs-lookup"><span data-stu-id="c8916-130">See also</span></span>

- <xref:System.Diagnostics.EventLog>
- [<span data-ttu-id="c8916-131">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="c8916-131">Debugging Enumerations</span></span>](debugging-enumerations.md)
