---
description: 'Дополнительные сведения: структура CLRDATA_ADDRESS_RANGE'
title: Структура CLRDATA_ADDRESS_RANGE
ms.date: 01/16/2019
api.name:
- CLRDATA_ADDRESS_RANGE Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_ADDRESS_RANGE Structure
helpviewer.keywords:
- CLRDATA_ADDRESS_RANGE Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5d671a08064781b71756efc3c753468e6769d4ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662342"
---
# <a name="clrdata_address_range-structure"></a><span data-ttu-id="74217-103">Структура CLRDATA_ADDRESS_RANGE</span><span class="sxs-lookup"><span data-stu-id="74217-103">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="74217-104">Определяет диапазон адресов.</span><span class="sxs-lookup"><span data-stu-id="74217-104">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="74217-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="74217-105">Syntax</span></span>

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="74217-106">Члены</span><span class="sxs-lookup"><span data-stu-id="74217-106">Members</span></span>

| <span data-ttu-id="74217-107">Член</span><span class="sxs-lookup"><span data-stu-id="74217-107">Member</span></span>         | <span data-ttu-id="74217-108">Описание</span><span class="sxs-lookup"><span data-stu-id="74217-108">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="74217-109">Начальный адрес диапазона.</span><span class="sxs-lookup"><span data-stu-id="74217-109">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="74217-110">Конечный адрес диапазона.</span><span class="sxs-lookup"><span data-stu-id="74217-110">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="74217-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="74217-111">Remarks</span></span>

<span data-ttu-id="74217-112">Эта структура находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="74217-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="74217-113">Чтобы использовать его, определите структуру, как указано выше, где `CLRDATA_ADDRESS` — это 64-разрядное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="74217-113">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="74217-114">Требования</span><span class="sxs-lookup"><span data-stu-id="74217-114">Requirements</span></span>

<span data-ttu-id="74217-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74217-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="74217-116">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="74217-116">**Header:** None</span></span>  
<span data-ttu-id="74217-117">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="74217-117">**Library:** None</span></span>  
<span data-ttu-id="74217-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="74217-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="74217-119">См. также</span><span class="sxs-lookup"><span data-stu-id="74217-119">See also</span></span>

- [<span data-ttu-id="74217-120">Отладка</span><span class="sxs-lookup"><span data-stu-id="74217-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="74217-121">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="74217-121">Debugging Structures</span></span>](debugging-structures.md)
