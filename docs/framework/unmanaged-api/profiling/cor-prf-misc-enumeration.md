---
description: 'Дополнительные сведения: перечисление COR_PRF_MISC'
title: Перечисление COR_PRF_MISC
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
ms.openlocfilehash: 037ea040dfdf9f5be48369ab4d8e94b12aea51ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687601"
---
# <a name="cor_prf_misc-enumeration"></a><span data-ttu-id="d880e-103">Перечисление COR_PRF_MISC</span><span class="sxs-lookup"><span data-stu-id="d880e-103">COR_PRF_MISC Enumeration</span></span>

<span data-ttu-id="d880e-104">Содержит постоянные значения, которые указывают специальные идентификаторы.</span><span class="sxs-lookup"><span data-stu-id="d880e-104">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d880e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d880e-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="d880e-106">Члены</span><span class="sxs-lookup"><span data-stu-id="d880e-106">Members</span></span>  
  
|<span data-ttu-id="d880e-107">Член</span><span class="sxs-lookup"><span data-stu-id="d880e-107">Member</span></span>|<span data-ttu-id="d880e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d880e-108">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="d880e-109">Идентификатор по умолчанию, используемый [ICorProfilerInfo:: GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) для модуля, который еще не присоединен к сборке.</span><span class="sxs-lookup"><span data-stu-id="d880e-109">The default identifier used by [ICorProfilerInfo::GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="d880e-110">Идентификатор класса по умолчанию для глобальных констант, которые не принадлежат классу.</span><span class="sxs-lookup"><span data-stu-id="d880e-110">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="d880e-111">Идентификатор модуля по умолчанию для глобальных объектов, которые не принадлежат модулю.</span><span class="sxs-lookup"><span data-stu-id="d880e-111">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d880e-112">Требования</span><span class="sxs-lookup"><span data-stu-id="d880e-112">Requirements</span></span>  

 <span data-ttu-id="d880e-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d880e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d880e-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d880e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d880e-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d880e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d880e-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d880e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d880e-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d880e-117">See also</span></span>

- [<span data-ttu-id="d880e-118">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="d880e-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
