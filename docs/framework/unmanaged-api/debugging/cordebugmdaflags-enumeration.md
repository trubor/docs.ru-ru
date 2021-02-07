---
description: Дополнительные сведения о перечислении Кордебугмдафлагс
title: Перечисление CorDebugMDAFlags
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
ms.openlocfilehash: d7e9178d76286b112035729e997b1f68e2a93fb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661939"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="95621-103">Перечисление CorDebugMDAFlags</span><span class="sxs-lookup"><span data-stu-id="95621-103">CorDebugMDAFlags Enumeration</span></span>

<span data-ttu-id="95621-104">Указывает состояние потока, по которому был вызван помощник по отладке управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="95621-104">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95621-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="95621-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="95621-106">Члены</span><span class="sxs-lookup"><span data-stu-id="95621-106">Members</span></span>  
  
|<span data-ttu-id="95621-107">Член</span><span class="sxs-lookup"><span data-stu-id="95621-107">Member</span></span>|<span data-ttu-id="95621-108">Описание</span><span class="sxs-lookup"><span data-stu-id="95621-108">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="95621-109">Поток, в котором был запущен MDA, был в запаздывания с момента запуска MDA.</span><span class="sxs-lookup"><span data-stu-id="95621-109">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95621-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="95621-110">Remarks</span></span>  

 <span data-ttu-id="95621-111">Если стек вызовов больше не описывает место первоначального создания MDA, обсуждение считается *, что он* находится в недоступном месте.</span><span class="sxs-lookup"><span data-stu-id="95621-111">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="95621-112">Это необычное обстоятельство, вызванное выполнением недействительной операции потока при выходе.</span><span class="sxs-lookup"><span data-stu-id="95621-112">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95621-113">Требования</span><span class="sxs-lookup"><span data-stu-id="95621-113">Requirements</span></span>  

 <span data-ttu-id="95621-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95621-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95621-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95621-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95621-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95621-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95621-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95621-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95621-118">См. также</span><span class="sxs-lookup"><span data-stu-id="95621-118">See also</span></span>

- [<span data-ttu-id="95621-119">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="95621-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
