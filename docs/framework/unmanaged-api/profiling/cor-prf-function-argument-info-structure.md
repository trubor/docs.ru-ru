---
description: 'Дополнительные сведения: структура COR_PRF_FUNCTION_ARGUMENT_INFO'
title: Структура COR_PRF_FUNCTION_ARGUMENT_INFO
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
ms.openlocfilehash: c40c9b20dad79fa36a1ed4471106a54f2c55b422
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649069"
---
# <a name="cor_prf_function_argument_info-structure"></a><span data-ttu-id="d5d11-103">Структура COR_PRF_FUNCTION_ARGUMENT_INFO</span><span class="sxs-lookup"><span data-stu-id="d5d11-103">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>

<span data-ttu-id="d5d11-104">Представляет аргументы функции слева направо.</span><span class="sxs-lookup"><span data-stu-id="d5d11-104">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5d11-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d5d11-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d5d11-106">Члены</span><span class="sxs-lookup"><span data-stu-id="d5d11-106">Members</span></span>  
  
|<span data-ttu-id="d5d11-107">Член</span><span class="sxs-lookup"><span data-stu-id="d5d11-107">Member</span></span>|<span data-ttu-id="d5d11-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d5d11-108">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="d5d11-109">Число блоков аргументов.</span><span class="sxs-lookup"><span data-stu-id="d5d11-109">The number of blocks of arguments.</span></span> <span data-ttu-id="d5d11-110">То есть это значение равно количеству структур [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) в `ranges` массиве.</span><span class="sxs-lookup"><span data-stu-id="d5d11-110">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="d5d11-111">Общий размер всех аргументов.</span><span class="sxs-lookup"><span data-stu-id="d5d11-111">The total size of all arguments.</span></span> <span data-ttu-id="d5d11-112">Иными словами, это значение является суммой длин аргументов.</span><span class="sxs-lookup"><span data-stu-id="d5d11-112">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="d5d11-113">Массив `COR_PRF_FUNCTION_ARGUMENT_RANGE` структур, каждый из которых представляет один блок аргументов функции.</span><span class="sxs-lookup"><span data-stu-id="d5d11-113">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5d11-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="d5d11-114">Remarks</span></span>  

 <span data-ttu-id="d5d11-115">У функции может быть несколько аргументов.</span><span class="sxs-lookup"><span data-stu-id="d5d11-115">A function may have many arguments.</span></span> <span data-ttu-id="d5d11-116">Эти аргументы могут не храниться непрерывно в памяти.</span><span class="sxs-lookup"><span data-stu-id="d5d11-116">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="d5d11-117">У вас может быть блок из трех аргументов в одном месте, блок из двух аргументов в другом месте и последний блок одного аргумента в другом месте.</span><span class="sxs-lookup"><span data-stu-id="d5d11-117">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="d5d11-118">Все эти аргументы используются для одной и той же функции. они просто хранятся в разных местах.</span><span class="sxs-lookup"><span data-stu-id="d5d11-118">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="d5d11-119">`COR_PRF_FUNCTION_ARGUMENT_INFO`Структура представляет все аргументы одной функции.</span><span class="sxs-lookup"><span data-stu-id="d5d11-119">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="d5d11-120">Он использует массив для ссылки на все блоки аргументов функции.</span><span class="sxs-lookup"><span data-stu-id="d5d11-120">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="d5d11-121">Таким образом, для одной функции имеется одна `COR_PRF_FUNCTION_ARGUMENT_INFO` структура, которая ссылается на несколько `COR_PRF_FUNCTION_ARGUMENT_RANGE` структур, каждая из которых указывает на один или несколько аргументов функции.</span><span class="sxs-lookup"><span data-stu-id="d5d11-121">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="d5d11-122">Аргументы, хранимые в регистрах, загружаются в память для построения структур.</span><span class="sxs-lookup"><span data-stu-id="d5d11-122">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5d11-123">Требования</span><span class="sxs-lookup"><span data-stu-id="d5d11-123">Requirements</span></span>  

 <span data-ttu-id="d5d11-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5d11-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5d11-125">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="d5d11-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d5d11-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5d11-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5d11-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5d11-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d11-128">См. также</span><span class="sxs-lookup"><span data-stu-id="d5d11-128">See also</span></span>

- [<span data-ttu-id="d5d11-129">Структуры профилирования</span><span class="sxs-lookup"><span data-stu-id="d5d11-129">Profiling Structures</span></span>](profiling-structures.md)
