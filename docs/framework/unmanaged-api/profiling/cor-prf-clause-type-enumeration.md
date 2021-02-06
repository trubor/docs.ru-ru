---
description: 'Дополнительные сведения: перечисление COR_PRF_CLAUSE_TYPE'
title: Перечисление COR_PRF_CLAUSE_TYPE
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
ms.openlocfilehash: 413dbc0ad94e4ab670cd7cd9537bbd1735ffd7cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649290"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="409ae-103">Перечисление COR_PRF_CLAUSE_TYPE</span><span class="sxs-lookup"><span data-stu-id="409ae-103">COR_PRF_CLAUSE_TYPE Enumeration</span></span>

<span data-ttu-id="409ae-104">Указывает тип предложения исключения, код которого был только что введен или удален.</span><span class="sxs-lookup"><span data-stu-id="409ae-104">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="409ae-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="409ae-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="409ae-106">Члены</span><span class="sxs-lookup"><span data-stu-id="409ae-106">Members</span></span>  
  
|<span data-ttu-id="409ae-107">Член</span><span class="sxs-lookup"><span data-stu-id="409ae-107">Member</span></span>|<span data-ttu-id="409ae-108">Описание</span><span class="sxs-lookup"><span data-stu-id="409ae-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="409ae-109">Недопустимое предложение исключения.</span><span class="sxs-lookup"><span data-stu-id="409ae-109">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="409ae-110">Предложение Exception является критерием фильтра.</span><span class="sxs-lookup"><span data-stu-id="409ae-110">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="409ae-111">Предложение Exception является `catch` оператором.</span><span class="sxs-lookup"><span data-stu-id="409ae-111">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="409ae-112">Предложение Exception является `finally` оператором.</span><span class="sxs-lookup"><span data-stu-id="409ae-112">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="409ae-113">Требования</span><span class="sxs-lookup"><span data-stu-id="409ae-113">Requirements</span></span>  

 <span data-ttu-id="409ae-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="409ae-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="409ae-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="409ae-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="409ae-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="409ae-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="409ae-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="409ae-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="409ae-118">См. также</span><span class="sxs-lookup"><span data-stu-id="409ae-118">See also</span></span>

- [<span data-ttu-id="409ae-119">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="409ae-119">Profiling Enumerations</span></span>](profiling-enumerations.md)
