---
description: 'Дополнительные сведения: структура COR_PRF_FUNCTION'
title: Структура COR_PRF_FUNCTION
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
ms.openlocfilehash: 494f3cfe6d1e3641645ef0050c06014e67bf4475
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648978"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="4fcaa-103">Структура COR_PRF_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="4fcaa-103">COR_PRF_FUNCTION Structure</span></span>

<span data-ttu-id="4fcaa-104">Выдает уникальное представление функции, объединяя ее идентификатор с идентификатором перекомпилированной версии этой функции.</span><span class="sxs-lookup"><span data-stu-id="4fcaa-104">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fcaa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4fcaa-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="4fcaa-106">Члены</span><span class="sxs-lookup"><span data-stu-id="4fcaa-106">Members</span></span>  
  
|<span data-ttu-id="4fcaa-107">Член</span><span class="sxs-lookup"><span data-stu-id="4fcaa-107">Member</span></span>|<span data-ttu-id="4fcaa-108">Описание</span><span class="sxs-lookup"><span data-stu-id="4fcaa-108">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="4fcaa-109">Идентификатор функции.</span><span class="sxs-lookup"><span data-stu-id="4fcaa-109">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="4fcaa-110">Идентификатор перекомпилированной функции.</span><span class="sxs-lookup"><span data-stu-id="4fcaa-110">The ID of the recompiled function.</span></span> <span data-ttu-id="4fcaa-111">Значение 0 (ноль) представляет исходную версию функции.</span><span class="sxs-lookup"><span data-stu-id="4fcaa-111">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fcaa-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="4fcaa-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fcaa-113">Требования</span><span class="sxs-lookup"><span data-stu-id="4fcaa-113">Requirements</span></span>  

 <span data-ttu-id="4fcaa-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fcaa-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fcaa-115">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="4fcaa-115">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4fcaa-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fcaa-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fcaa-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fcaa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fcaa-118">См. также</span><span class="sxs-lookup"><span data-stu-id="4fcaa-118">See also</span></span>

- [<span data-ttu-id="4fcaa-119">Структуры профилирования</span><span class="sxs-lookup"><span data-stu-id="4fcaa-119">Profiling Structures</span></span>](profiling-structures.md)
