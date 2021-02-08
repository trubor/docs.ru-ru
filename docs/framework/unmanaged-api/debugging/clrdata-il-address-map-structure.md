---
description: 'Дополнительные сведения: структура CLRDATA_IL_ADDRESS_MAP'
title: Структура CLRDATA_IL_ADDRESS_MAP
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 02ee14154de0c1609e58cf6a2ad1ca62710567f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801856"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="cb356-103">Структура CLRDATA_IL_ADDRESS_MAP</span><span class="sxs-lookup"><span data-stu-id="cb356-103">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="cb356-104">Определяет IL для сопоставления адресов.</span><span class="sxs-lookup"><span data-stu-id="cb356-104">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="cb356-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cb356-105">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="cb356-106">Члены</span><span class="sxs-lookup"><span data-stu-id="cb356-106">Members</span></span>

| <span data-ttu-id="cb356-107">Член</span><span class="sxs-lookup"><span data-stu-id="cb356-107">Member</span></span>         | <span data-ttu-id="cb356-108">Описание</span><span class="sxs-lookup"><span data-stu-id="cb356-108">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="cb356-109">Смещение IL для диапазона входящих адресов</span><span class="sxs-lookup"><span data-stu-id="cb356-109">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="cb356-110">Начальный адрес диапазона.</span><span class="sxs-lookup"><span data-stu-id="cb356-110">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="cb356-111">Конечный адрес диапазона.</span><span class="sxs-lookup"><span data-stu-id="cb356-111">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="cb356-112">Тип данных.</span><span class="sxs-lookup"><span data-stu-id="cb356-112">The type of the data.</span></span> <span data-ttu-id="cb356-113">Это значение в настоящее время не используется</span><span class="sxs-lookup"><span data-stu-id="cb356-113">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="cb356-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="cb356-114">Remarks</span></span>

<span data-ttu-id="cb356-115">Эта структура находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="cb356-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="cb356-116">Чтобы использовать его, определите структуру, как указано выше, где `CLRDATA_ADDRESS` — это 64-разрядное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="cb356-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb356-117">Требования</span><span class="sxs-lookup"><span data-stu-id="cb356-117">Requirements</span></span>

<span data-ttu-id="cb356-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb356-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="cb356-119">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="cb356-119">**Header:** None</span></span>  
<span data-ttu-id="cb356-120">**Библиотека:** Нет **платформа .NET Framework версий:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cb356-120">**Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="cb356-121">См. также</span><span class="sxs-lookup"><span data-stu-id="cb356-121">See also</span></span>

- [<span data-ttu-id="cb356-122">Перечисление Клрдатасаурцетипе</span><span class="sxs-lookup"><span data-stu-id="cb356-122">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="cb356-123">Отладка</span><span class="sxs-lookup"><span data-stu-id="cb356-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="cb356-124">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="cb356-124">Debugging Structures</span></span>](debugging-structures.md)
