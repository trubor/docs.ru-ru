---
description: 'Дополнительные сведения о: структура Дакпжетмодулеаддресс'
title: Структура DacpGetModuleAddress
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3de76cc4f15bffd35d7a43ae25a313eb2fe59b82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661601"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="cc7ce-103">Структура DacpGetModuleAddress</span><span class="sxs-lookup"><span data-stu-id="cc7ce-103">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="cc7ce-104">Определяет контейнер для запроса адреса модуля.</span><span class="sxs-lookup"><span data-stu-id="cc7ce-104">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="cc7ce-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cc7ce-105">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="cc7ce-106">Члены</span><span class="sxs-lookup"><span data-stu-id="cc7ce-106">Members</span></span>

| <span data-ttu-id="cc7ce-107">Член</span><span class="sxs-lookup"><span data-stu-id="cc7ce-107">Member</span></span>      | <span data-ttu-id="cc7ce-108">Описание</span><span class="sxs-lookup"><span data-stu-id="cc7ce-108">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="cc7ce-109">Указатель на модуль.</span><span class="sxs-lookup"><span data-stu-id="cc7ce-109">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="cc7ce-110">Методы</span><span class="sxs-lookup"><span data-stu-id="cc7ce-110">Methods</span></span>

| <span data-ttu-id="cc7ce-111">Метод</span><span class="sxs-lookup"><span data-stu-id="cc7ce-111">Method</span></span>                                                                                               | <span data-ttu-id="cc7ce-112">Описание</span><span class="sxs-lookup"><span data-stu-id="cc7ce-112">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="cc7ce-113">Запрос</span><span class="sxs-lookup"><span data-stu-id="cc7ce-113">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="cc7ce-114">Выполняет запрос на заполнение структуры из заданной структуры среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="cc7ce-114">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="cc7ce-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="cc7ce-115">Remarks</span></span>

<span data-ttu-id="cc7ce-116">Эта структура находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="cc7ce-116">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="cc7ce-117">Чтобы использовать его, определите структуру, как указано выше, где `CLRDATA_ADDRESS` — это 64-разрядное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="cc7ce-117">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="cc7ce-118">Требования</span><span class="sxs-lookup"><span data-stu-id="cc7ce-118">Requirements</span></span>

<span data-ttu-id="cc7ce-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc7ce-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="cc7ce-120">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="cc7ce-120">**Header:** None</span></span>  
<span data-ttu-id="cc7ce-121">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="cc7ce-121">**Library:** None</span></span>  
<span data-ttu-id="cc7ce-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cc7ce-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="cc7ce-123">См. также</span><span class="sxs-lookup"><span data-stu-id="cc7ce-123">See also</span></span>

- [<span data-ttu-id="cc7ce-124">Отладка</span><span class="sxs-lookup"><span data-stu-id="cc7ce-124">Debugging</span></span>](index.md)
- [<span data-ttu-id="cc7ce-125">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="cc7ce-125">Debugging Structures</span></span>](debugging-structures.md)
