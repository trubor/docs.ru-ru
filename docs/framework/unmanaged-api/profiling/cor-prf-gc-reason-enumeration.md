---
description: 'Дополнительные сведения: перечисление COR_PRF_GC_REASON'
title: Перечисление COR_PRF_GC_REASON
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
ms.openlocfilehash: f5c8201f2023e07f9bb9d540f6d5f8fca1c19419
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648802"
---
# <a name="cor_prf_gc_reason-enumeration"></a><span data-ttu-id="703e1-103">Перечисление COR_PRF_GC_REASON</span><span class="sxs-lookup"><span data-stu-id="703e1-103">COR_PRF_GC_REASON Enumeration</span></span>

<span data-ttu-id="703e1-104">Указывает причину возникновения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="703e1-104">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="703e1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="703e1-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="703e1-106">Члены</span><span class="sxs-lookup"><span data-stu-id="703e1-106">Members</span></span>  
  
|<span data-ttu-id="703e1-107">Член</span><span class="sxs-lookup"><span data-stu-id="703e1-107">Member</span></span>|<span data-ttu-id="703e1-108">Описание</span><span class="sxs-lookup"><span data-stu-id="703e1-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="703e1-109">Сборка мусора была вызвана <xref:System.GC.Collect%2A> методом.</span><span class="sxs-lookup"><span data-stu-id="703e1-109">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="703e1-110">Причина не указана.</span><span class="sxs-lookup"><span data-stu-id="703e1-110">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="703e1-111">Требования</span><span class="sxs-lookup"><span data-stu-id="703e1-111">Requirements</span></span>  

 <span data-ttu-id="703e1-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="703e1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="703e1-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="703e1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="703e1-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="703e1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="703e1-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="703e1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="703e1-116">См. также</span><span class="sxs-lookup"><span data-stu-id="703e1-116">See also</span></span>

- [<span data-ttu-id="703e1-117">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="703e1-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
