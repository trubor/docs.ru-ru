---
description: Дополнительные сведения о перечислении Кордебугнженполици
title: Перечисление CorDebugNGenPolicy
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
ms.openlocfilehash: 529a5979bacef32ce78262c122004a66b54156ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801583"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="6ac61-103">Перечисление CorDebugNGenPolicy</span><span class="sxs-lookup"><span data-stu-id="6ac61-103">CorDebugNGenPolicy Enumeration</span></span>

<span data-ttu-id="6ac61-104">Предоставляет значение, который определяет, загружает ли отладчик образы в машинном коде (NGen) из кэша образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="6ac61-104">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ac61-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6ac61-105">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="6ac61-106">Члены</span><span class="sxs-lookup"><span data-stu-id="6ac61-106">Members</span></span>  
  
|<span data-ttu-id="6ac61-107">Имя участника</span><span class="sxs-lookup"><span data-stu-id="6ac61-107">Member name</span></span>|<span data-ttu-id="6ac61-108">Описание</span><span class="sxs-lookup"><span data-stu-id="6ac61-108">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="6ac61-109">В приложении для Магазина Windows 8. x использование образов из локального кэша образов в машинном кодах отключено.</span><span class="sxs-lookup"><span data-stu-id="6ac61-109">In a Windows 8.x Store app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="6ac61-110">В классическом приложении этот параметр не действует.</span><span class="sxs-lookup"><span data-stu-id="6ac61-110">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ac61-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="6ac61-111">Remarks</span></span>  

 <span data-ttu-id="6ac61-112">`CorDebugNGENPolicy`Перечисление используется методом [метод ICorDebugProcess5:: EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6ac61-112">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="6ac61-113">Отключение использования образов из локального кэша образов в машинном код обеспечивает единообразную отладку, гарантируя, что отладчик загружает отладочные скомпилированные КОМПИЛЯТОРом изображения вместо оптимизированных образов в машинном код.</span><span class="sxs-lookup"><span data-stu-id="6ac61-113">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ac61-114">Требования</span><span class="sxs-lookup"><span data-stu-id="6ac61-114">Requirements</span></span>  

 <span data-ttu-id="6ac61-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ac61-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ac61-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ac61-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ac61-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ac61-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ac61-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ac61-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac61-119">См. также</span><span class="sxs-lookup"><span data-stu-id="6ac61-119">See also</span></span>

- [<span data-ttu-id="6ac61-120">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="6ac61-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
