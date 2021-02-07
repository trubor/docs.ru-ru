---
description: Дополнительные сведения о перечислении Кордебугхандлетипе
title: Перечисление CorDebugHandleType
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
ms.openlocfilehash: 294fd7b04018331489e51d12930bcbbb81ec340a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662121"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="8a472-103">Перечисление CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="8a472-103">CorDebugHandleType Enumeration</span></span>

<span data-ttu-id="8a472-104">Указывает тип обработки.</span><span class="sxs-lookup"><span data-stu-id="8a472-104">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a472-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8a472-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="8a472-106">Члены</span><span class="sxs-lookup"><span data-stu-id="8a472-106">Members</span></span>  
  
|<span data-ttu-id="8a472-107">Член</span><span class="sxs-lookup"><span data-stu-id="8a472-107">Member</span></span>|<span data-ttu-id="8a472-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8a472-108">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="8a472-109">Этот маркер является строгим, что предотвращает освобождение объекта при сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="8a472-109">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="8a472-110">Этот маркер является слабым, который не предотвращает освобождение объекта при сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="8a472-110">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="8a472-111">При сборе объекта этот маркер становится недействительным.</span><span class="sxs-lookup"><span data-stu-id="8a472-111">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a472-112">Требования</span><span class="sxs-lookup"><span data-stu-id="8a472-112">Requirements</span></span>  

 <span data-ttu-id="8a472-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a472-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a472-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a472-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a472-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a472-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a472-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a472-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a472-117">См. также</span><span class="sxs-lookup"><span data-stu-id="8a472-117">See also</span></span>

- [<span data-ttu-id="8a472-118">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="8a472-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
