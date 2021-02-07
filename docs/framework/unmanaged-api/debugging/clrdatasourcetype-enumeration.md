---
description: Дополнительные сведения о перечислении Клрдатасаурцетипе
title: Перечисление Клрдатасаурцетипе
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 06590e21aa4cdf6e89977a79da36a413d5ff4f1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747246"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="96d0e-103">Перечисление Клрдатасаурцетипе</span><span class="sxs-lookup"><span data-stu-id="96d0e-103">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="96d0e-104">Предоставляет значения, используемые структурой CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="96d0e-104">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="96d0e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="96d0e-105">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="96d0e-106">Члены</span><span class="sxs-lookup"><span data-stu-id="96d0e-106">Members</span></span>

| <span data-ttu-id="96d0e-107">Член</span><span class="sxs-lookup"><span data-stu-id="96d0e-107">Member</span></span>                        | <span data-ttu-id="96d0e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="96d0e-108">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="96d0e-109">Указание того, что ничего еще не применимо</span><span class="sxs-lookup"><span data-stu-id="96d0e-109">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="96d0e-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="96d0e-110">Remarks</span></span>

<span data-ttu-id="96d0e-111">Это перечисление находится внутри среды выполнения и не предоставляется через заголовки или файлы библиотек.</span><span class="sxs-lookup"><span data-stu-id="96d0e-111">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="96d0e-112">Чтобы использовать его, определите перечисление, как определено выше в коде.</span><span class="sxs-lookup"><span data-stu-id="96d0e-112">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="96d0e-113">Это также называется псевдонимом, `CLRDATA_ENUM` как упоминалось в [общих типах данных](../common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="96d0e-113">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="96d0e-114">Требования</span><span class="sxs-lookup"><span data-stu-id="96d0e-114">Requirements</span></span>

<span data-ttu-id="96d0e-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96d0e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="96d0e-116">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="96d0e-116">**Header:** None</span></span>  
<span data-ttu-id="96d0e-117">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="96d0e-117">**Library:** None</span></span>  
<span data-ttu-id="96d0e-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="96d0e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="96d0e-119">См. также</span><span class="sxs-lookup"><span data-stu-id="96d0e-119">See also</span></span>

- [<span data-ttu-id="96d0e-120">Отладка</span><span class="sxs-lookup"><span data-stu-id="96d0e-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="96d0e-121">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="96d0e-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
