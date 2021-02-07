---
description: 'Дополнительные сведения о: структура Дакпмодуледата'
title: Структура DacpModuleData
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 376a49ab78db08e5906e8d33389cdc45fe76e81e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661588"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="bdc00-103">Структура DacpModuleData</span><span class="sxs-lookup"><span data-stu-id="bdc00-103">DacpModuleData Structure</span></span>

<span data-ttu-id="bdc00-104">Определяет транспортный буфер для сведений о среде выполнения модуля.</span><span class="sxs-lookup"><span data-stu-id="bdc00-104">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bdc00-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bdc00-105">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="bdc00-106">Члены</span><span class="sxs-lookup"><span data-stu-id="bdc00-106">Members</span></span>

| <span data-ttu-id="bdc00-107">Член</span><span class="sxs-lookup"><span data-stu-id="bdc00-107">Member</span></span>    | <span data-ttu-id="bdc00-108">Описание</span><span class="sxs-lookup"><span data-stu-id="bdc00-108">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="bdc00-109">Адрес объекта модуля.</span><span class="sxs-lookup"><span data-stu-id="bdc00-109">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="bdc00-110">Указатель на переносимый исполняемый файл (PE).</span><span class="sxs-lookup"><span data-stu-id="bdc00-110">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="bdc00-111">Адрес базы загруженного образа.</span><span class="sxs-lookup"><span data-stu-id="bdc00-111">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="bdc00-112">Буфер полезных данных для дополнительных сведений о модулях, используемых средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="bdc00-112">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="bdc00-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="bdc00-113">Remarks</span></span>

<span data-ttu-id="bdc00-114">Эта структура находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="bdc00-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="bdc00-115">Чтобы использовать его, определите структуру, как указано выше.</span><span class="sxs-lookup"><span data-stu-id="bdc00-115">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="bdc00-116">Требования</span><span class="sxs-lookup"><span data-stu-id="bdc00-116">Requirements</span></span>

<span data-ttu-id="bdc00-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdc00-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="bdc00-118">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="bdc00-118">**Header:** None</span></span>  
<span data-ttu-id="bdc00-119">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="bdc00-119">**Library:** None</span></span>  
<span data-ttu-id="bdc00-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bdc00-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bdc00-121">См. также</span><span class="sxs-lookup"><span data-stu-id="bdc00-121">See also</span></span>

- [<span data-ttu-id="bdc00-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="bdc00-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="bdc00-123">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="bdc00-123">Debugging Structures</span></span>](debugging-structures.md)
