---
description: Дополнительные сведения о перечислении CorDebugExceptionCallbackType
title: Перечисление CorDebugExceptionCallbackType
ms.date: 03/30/2017
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
ms.openlocfilehash: 41b9cdf707de017703ee3756b3d04a38163bb03b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801687"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="c8047-103">Перечисление CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="c8047-103">CorDebugExceptionCallbackType Enumeration</span></span>

<span data-ttu-id="c8047-104">Указывает тип обратного вызова, сделанный из события [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c8047-104">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8047-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c8047-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="c8047-106">Члены</span><span class="sxs-lookup"><span data-stu-id="c8047-106">Members</span></span>  
  
|<span data-ttu-id="c8047-107">Член</span><span class="sxs-lookup"><span data-stu-id="c8047-107">Member</span></span>|<span data-ttu-id="c8047-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c8047-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="c8047-109">Возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="c8047-109">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="c8047-110">Процесс, виндуп исключение, вошел в пользовательский код.</span><span class="sxs-lookup"><span data-stu-id="c8047-110">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="c8047-111">Процесс виндуп исключения обнаружил `catch` блок в пользовательском коде.</span><span class="sxs-lookup"><span data-stu-id="c8047-111">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="c8047-112">Исключение не было обработано.</span><span class="sxs-lookup"><span data-stu-id="c8047-112">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8047-113">Требования</span><span class="sxs-lookup"><span data-stu-id="c8047-113">Requirements</span></span>  

 <span data-ttu-id="c8047-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8047-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8047-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8047-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8047-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8047-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8047-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8047-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8047-118">См. также</span><span class="sxs-lookup"><span data-stu-id="c8047-118">See also</span></span>

- [<span data-ttu-id="c8047-119">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="c8047-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
