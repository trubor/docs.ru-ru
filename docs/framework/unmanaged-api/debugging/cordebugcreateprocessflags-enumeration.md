---
description: Дополнительные сведения о перечислении Кордебугкреатепроцессфлагс
title: Перечисление CorDebugCreateProcessFlags
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
ms.openlocfilehash: 29363510c83873c7f367079857809c165bc55b1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801739"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="35ad8-103">Перечисление CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="35ad8-103">CorDebugCreateProcessFlags Enumeration</span></span>

<span data-ttu-id="35ad8-104">Предоставляет дополнительные параметры отладки, которые можно использовать при вызове метода [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="35ad8-104">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35ad8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="35ad8-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="35ad8-106">Члены</span><span class="sxs-lookup"><span data-stu-id="35ad8-106">Members</span></span>  
  
|<span data-ttu-id="35ad8-107">Член</span><span class="sxs-lookup"><span data-stu-id="35ad8-107">Member</span></span>|<span data-ttu-id="35ad8-108">Описание</span><span class="sxs-lookup"><span data-stu-id="35ad8-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="35ad8-109">Специальные параметры не заданы.</span><span class="sxs-lookup"><span data-stu-id="35ad8-109">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="35ad8-110">Требования</span><span class="sxs-lookup"><span data-stu-id="35ad8-110">Requirements</span></span>  

 <span data-ttu-id="35ad8-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35ad8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35ad8-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35ad8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35ad8-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35ad8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35ad8-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35ad8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ad8-115">См. также</span><span class="sxs-lookup"><span data-stu-id="35ad8-115">See also</span></span>

- [<span data-ttu-id="35ad8-116">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="35ad8-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
