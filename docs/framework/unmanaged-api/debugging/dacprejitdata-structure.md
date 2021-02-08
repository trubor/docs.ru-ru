---
description: 'Дополнительные сведения о: структура Дакпрежитдата'
title: Структура DacpReJitData
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 8e8d506856dbc6579ac6ea0eee2b2088a980a315
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801440"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="808ac-103">Структура DacpReJitData</span><span class="sxs-lookup"><span data-stu-id="808ac-103">DacpReJitData Structure</span></span>

<span data-ttu-id="808ac-104">Определяет основные сведения о конкретном инструментированном методе профилирования.</span><span class="sxs-lookup"><span data-stu-id="808ac-104">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="808ac-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="808ac-105">Syntax</span></span>

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a><span data-ttu-id="808ac-106">Члены</span><span class="sxs-lookup"><span data-stu-id="808ac-106">Members</span></span>

| <span data-ttu-id="808ac-107">Член</span><span class="sxs-lookup"><span data-stu-id="808ac-107">Member</span></span>           | <span data-ttu-id="808ac-108">Описание</span><span class="sxs-lookup"><span data-stu-id="808ac-108">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="808ac-109">Номер редакции ReJit для метода.</span><span class="sxs-lookup"><span data-stu-id="808ac-109">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="808ac-110">Флаг, указывающий текущее состояние инструментирования ReJit метода для данной версии.</span><span class="sxs-lookup"><span data-stu-id="808ac-110">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="808ac-111">Базовый адрес реализации режиттед метода.</span><span class="sxs-lookup"><span data-stu-id="808ac-111">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="808ac-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="808ac-112">Remarks</span></span>

<span data-ttu-id="808ac-113">Эта структура находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="808ac-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="808ac-114">Чтобы использовать его, определите структуру, как указано выше.</span><span class="sxs-lookup"><span data-stu-id="808ac-114">To use it, define the structure as specified above.</span></span> <span data-ttu-id="808ac-115">Структура также должна быть определена с помощью `ms_struct` упаковки, если не используется компиляторы Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="808ac-115">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="808ac-116">Требования</span><span class="sxs-lookup"><span data-stu-id="808ac-116">Requirements</span></span>

<span data-ttu-id="808ac-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="808ac-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="808ac-118">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="808ac-118">**Header:** None</span></span>  
<span data-ttu-id="808ac-119">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="808ac-119">**Library:** None</span></span>  
<span data-ttu-id="808ac-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="808ac-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="808ac-121">См. также</span><span class="sxs-lookup"><span data-stu-id="808ac-121">See also</span></span>

- [<span data-ttu-id="808ac-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="808ac-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="808ac-123">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="808ac-123">Debugging Structures</span></span>](debugging-structures.md)
