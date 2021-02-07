---
description: Дополнительные сведения о перечислении Кордебугстатечанже
title: Перечисление CorDebugStateChange
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
ms.openlocfilehash: 1900baa77432daa10d0f1a32dd9cb25198b86ed1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661822"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="5a728-103">Перечисление CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="5a728-103">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="5a728-104">Описывает объем кэшированных данных, которые должны быть отброшены на основе изменений, внесенных в процесс.</span><span class="sxs-lookup"><span data-stu-id="5a728-104">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="5a728-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5a728-105">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="5a728-106">Члены</span><span class="sxs-lookup"><span data-stu-id="5a728-106">Members</span></span>

| <span data-ttu-id="5a728-107">Член</span><span class="sxs-lookup"><span data-stu-id="5a728-107">Member</span></span>            | <span data-ttu-id="5a728-108">Описание</span><span class="sxs-lookup"><span data-stu-id="5a728-108">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="5a728-109">Процесс достиг нового состояния памяти с помощью механизма прямого выполнения.</span><span class="sxs-lookup"><span data-stu-id="5a728-109">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="5a728-110">Память процесса может отличаться произвольным образом от предыдущего варианта.</span><span class="sxs-lookup"><span data-stu-id="5a728-110">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="5a728-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="5a728-111">Remarks</span></span>

 <span data-ttu-id="5a728-112">Член `CorDebugStateChange` перечисления предоставляется в качестве аргумента, когда отладчик вызывает `ProcessStateChanged` метод с помощью [ICorDebugProcess4::P роцессстатечанжед](icordebugprocess4-processstatechanged-method.md) или [ICorDebugProcess6::P роцессстатечанжед](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="5a728-112">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="5a728-113">Требования</span><span class="sxs-lookup"><span data-stu-id="5a728-113">Requirements</span></span>

 <span data-ttu-id="5a728-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a728-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="5a728-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a728-115">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="5a728-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a728-116">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="5a728-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a728-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5a728-118">См. также</span><span class="sxs-lookup"><span data-stu-id="5a728-118">See also</span></span>

- [<span data-ttu-id="5a728-119">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="5a728-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="5a728-120">Отладка</span><span class="sxs-lookup"><span data-stu-id="5a728-120">Debugging</span></span>](index.md)
