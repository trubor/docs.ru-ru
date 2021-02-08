---
description: Дополнительные сведения о перечислении Кордебугдекодивентфлагсвиндовс
title: Перечисление CorDebugDecodeEventFlagsWindows
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
ms.openlocfilehash: 765ce4b967d00bd70becca666e2ed418614d6fe3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801700"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="3edbb-103">Перечисление CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="3edbb-103">CorDebugDecodeEventFlagsWindows Enumeration</span></span>

<span data-ttu-id="3edbb-104">Предоставляет дополнительную информацию о событиях отладки на платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="3edbb-104">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3edbb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3edbb-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="3edbb-106">Члены</span><span class="sxs-lookup"><span data-stu-id="3edbb-106">Members</span></span>  
  
|<span data-ttu-id="3edbb-107">Член</span><span class="sxs-lookup"><span data-stu-id="3edbb-107">Member</span></span>|<span data-ttu-id="3edbb-108">Описание</span><span class="sxs-lookup"><span data-stu-id="3edbb-108">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="3edbb-109">Указывает, что событие отладки является первичным исключением.</span><span class="sxs-lookup"><span data-stu-id="3edbb-109">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3edbb-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="3edbb-110">Remarks</span></span>  

 <span data-ttu-id="3edbb-111">Метод [ICorDebugProcess6::D екодивент](icordebugprocess6-decodeevent-method.md) включает `dwFlags` параметр, предоставляющий дополнительные сведения о событии отладки, значение которого зависит от целевой архитектуры.</span><span class="sxs-lookup"><span data-stu-id="3edbb-111">The [ICorDebugProcess6::DecodeEvent](icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="3edbb-112">Перечисление `CorDebugDecodeEventFlagsWindows` можно использовать с событиями отладки на платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="3edbb-112">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3edbb-113">Это перечисление предназначено для использования только в сценариях отладки .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3edbb-113">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3edbb-114">Требования</span><span class="sxs-lookup"><span data-stu-id="3edbb-114">Requirements</span></span>  

 <span data-ttu-id="3edbb-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3edbb-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3edbb-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3edbb-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3edbb-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3edbb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3edbb-118">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3edbb-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3edbb-119">См. также</span><span class="sxs-lookup"><span data-stu-id="3edbb-119">See also</span></span>

- [<span data-ttu-id="3edbb-120">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="3edbb-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
