---
description: Дополнительные сведения о перечислении CorDebugGCType
title: Перечисление CorDebugGCType
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
ms.openlocfilehash: 4be835a9a028a882fa050991beb31d2a8dec5354
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801661"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="a2603-103">Перечисление CorDebugGCType</span><span class="sxs-lookup"><span data-stu-id="a2603-103">CorDebugGCType Enumeration</span></span>

<span data-ttu-id="a2603-104">Указывает, где выполняется сборщик мусора: на рабочей станции или на сервере.</span><span class="sxs-lookup"><span data-stu-id="a2603-104">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2603-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a2603-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2603-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a2603-106">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="a2603-107">Элементы</span><span class="sxs-lookup"><span data-stu-id="a2603-107">Members</span></span>  
  
|<span data-ttu-id="a2603-108">Имя участника</span><span class="sxs-lookup"><span data-stu-id="a2603-108">Member name</span></span>|<span data-ttu-id="a2603-109">Описание</span><span class="sxs-lookup"><span data-stu-id="a2603-109">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="a2603-110">Сборщик мусора работает на рабочей станции.</span><span class="sxs-lookup"><span data-stu-id="a2603-110">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="a2603-111">Сборщик мусора работает на сервере.</span><span class="sxs-lookup"><span data-stu-id="a2603-111">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2603-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="a2603-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2603-113">Требования</span><span class="sxs-lookup"><span data-stu-id="a2603-113">Requirements</span></span>  

 <span data-ttu-id="a2603-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2603-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2603-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2603-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2603-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2603-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2603-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2603-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2603-118">См. также</span><span class="sxs-lookup"><span data-stu-id="a2603-118">See also</span></span>

- [<span data-ttu-id="a2603-119">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="a2603-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
