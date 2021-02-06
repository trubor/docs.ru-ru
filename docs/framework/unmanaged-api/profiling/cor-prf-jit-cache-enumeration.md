---
description: 'Дополнительные сведения: перечисление COR_PRF_JIT_CACHE'
title: Перечисление COR_PRF_JIT_CACHE
ms.date: 03/30/2017
api_name:
- COR_PRF_JIT_CACHE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_JIT_CACHE
helpviewer_keywords:
- COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type:
- apiref
ms.openlocfilehash: 94b04b42504760be826f78cee0da3066f1936f32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648757"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="49969-103">Перечисление COR_PRF_JIT_CACHE</span><span class="sxs-lookup"><span data-stu-id="49969-103">COR_PRF_JIT_CACHE Enumeration</span></span>

<span data-ttu-id="49969-104">Указывает результат кэшированной функции поиска.</span><span class="sxs-lookup"><span data-stu-id="49969-104">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49969-105">`COR_PRF_CACHED_FUNCTION_FOUND` имеет нулевое значение, поэтому `COR_PRF_JIT_CACHE` не может использоваться в качестве логического суррогата.</span><span class="sxs-lookup"><span data-stu-id="49969-105">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49969-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="49969-106">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="49969-107">Члены</span><span class="sxs-lookup"><span data-stu-id="49969-107">Members</span></span>  
  
|<span data-ttu-id="49969-108">Член</span><span class="sxs-lookup"><span data-stu-id="49969-108">Member</span></span>|<span data-ttu-id="49969-109">Описание</span><span class="sxs-lookup"><span data-stu-id="49969-109">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="49969-110">Поиск обнаружил функцию.</span><span class="sxs-lookup"><span data-stu-id="49969-110">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="49969-111">Поиск не нашел функцию.</span><span class="sxs-lookup"><span data-stu-id="49969-111">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49969-112">Требования</span><span class="sxs-lookup"><span data-stu-id="49969-112">Requirements</span></span>  

 <span data-ttu-id="49969-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49969-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49969-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="49969-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="49969-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49969-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49969-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49969-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49969-117">См. также</span><span class="sxs-lookup"><span data-stu-id="49969-117">See also</span></span>

- [<span data-ttu-id="49969-118">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="49969-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
