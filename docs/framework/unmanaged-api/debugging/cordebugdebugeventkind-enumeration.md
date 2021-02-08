---
description: Дополнительные сведения о перечислении CorDebugDebugEventKind
title: Перечисление CorDebugDebugEventKind
ms.date: 03/30/2017
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
ms.openlocfilehash: 62094c934873a74fdab01fad87c42126e28cb0f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801713"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="50ccc-103">Перечисление CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="50ccc-103">CorDebugDebugEventKind Enumeration</span></span>

<span data-ttu-id="50ccc-104">Указывает тип события, сведения о котором декодированы методом [DecodeEvent](icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="50ccc-104">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50ccc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="50ccc-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="50ccc-106">Члены</span><span class="sxs-lookup"><span data-stu-id="50ccc-106">Members</span></span>  
  
|<span data-ttu-id="50ccc-107">Член</span><span class="sxs-lookup"><span data-stu-id="50ccc-107">Member</span></span>|<span data-ttu-id="50ccc-108">Описание</span><span class="sxs-lookup"><span data-stu-id="50ccc-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="50ccc-109">Событие загрузки модуля.</span><span class="sxs-lookup"><span data-stu-id="50ccc-109">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="50ccc-110">Событие выгрузки модуля.</span><span class="sxs-lookup"><span data-stu-id="50ccc-110">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="50ccc-111">Первичное исключение.</span><span class="sxs-lookup"><span data-stu-id="50ccc-111">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="50ccc-112">Первичное исключение пользователя.</span><span class="sxs-lookup"><span data-stu-id="50ccc-112">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="50ccc-113">Исключение, для которого существует обработчик `catch`.</span><span class="sxs-lookup"><span data-stu-id="50ccc-113">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="50ccc-114">Необработанное исключение.</span><span class="sxs-lookup"><span data-stu-id="50ccc-114">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50ccc-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="50ccc-115">Remarks</span></span>  

 <span data-ttu-id="50ccc-116">Член `CorDebugDebugEventKind` перечисления возвращается путем вызова метода [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="50ccc-116">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50ccc-117">Это перечисление предназначено для использования только в сценариях отладки .NET Native.</span><span class="sxs-lookup"><span data-stu-id="50ccc-117">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50ccc-118">Требования</span><span class="sxs-lookup"><span data-stu-id="50ccc-118">Requirements</span></span>  

 <span data-ttu-id="50ccc-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50ccc-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50ccc-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50ccc-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50ccc-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50ccc-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50ccc-122">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50ccc-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50ccc-123">См. также</span><span class="sxs-lookup"><span data-stu-id="50ccc-123">See also</span></span>

- [<span data-ttu-id="50ccc-124">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="50ccc-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
