---
description: 'Дополнительные сведения: структура COR_PRF_FUNCTION_ARGUMENT_RANGE'
title: Структура COR_PRF_FUNCTION_ARGUMENT_RANGE
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
ms.openlocfilehash: 65d762ba4513341b20426ea56d423a2066f6e714
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649030"
---
# <a name="cor_prf_function_argument_range-structure"></a><span data-ttu-id="8180b-103">Структура COR_PRF_FUNCTION_ARGUMENT_RANGE</span><span class="sxs-lookup"><span data-stu-id="8180b-103">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>

<span data-ttu-id="8180b-104">Представляет блок аргументов функции, которые сохраняются в памяти последовательно слева направо.</span><span class="sxs-lookup"><span data-stu-id="8180b-104">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8180b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8180b-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="8180b-106">Члены</span><span class="sxs-lookup"><span data-stu-id="8180b-106">Members</span></span>  
  
|<span data-ttu-id="8180b-107">Элементы</span><span class="sxs-lookup"><span data-stu-id="8180b-107">Members</span></span>|<span data-ttu-id="8180b-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8180b-108">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="8180b-109">Начальный адрес блока.</span><span class="sxs-lookup"><span data-stu-id="8180b-109">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="8180b-110">Длина непрерывного блока.</span><span class="sxs-lookup"><span data-stu-id="8180b-110">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8180b-111">Требования</span><span class="sxs-lookup"><span data-stu-id="8180b-111">Requirements</span></span>  

 <span data-ttu-id="8180b-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8180b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8180b-113">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="8180b-113">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="8180b-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8180b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8180b-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8180b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8180b-116">См. также</span><span class="sxs-lookup"><span data-stu-id="8180b-116">See also</span></span>

- [<span data-ttu-id="8180b-117">Структуры профилирования</span><span class="sxs-lookup"><span data-stu-id="8180b-117">Profiling Structures</span></span>](profiling-structures.md)
