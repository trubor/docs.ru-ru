---
description: 'Дополнительные сведения: перечисление COR_PRF_REJIT_FLAGS'
title: Перечисление COR_PRF_REJIT_FLAGS
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: a27b6d90b51254560f25fbadb18ac95fe838ab2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789025"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="867be-103">Перечисление COR_PRF_REJIT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="867be-103">COR_PRF_REJIT_FLAGS Enumeration</span></span>

<span data-ttu-id="867be-104">Содержит значения, указывающие поведение API [ICorProfilerInfo10:: рекуестрежитвисинлинерс](icorprofilerinfo10-requestrejitwithinliners-method.md) .</span><span class="sxs-lookup"><span data-stu-id="867be-104">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="867be-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="867be-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="867be-106">Члены</span><span class="sxs-lookup"><span data-stu-id="867be-106">Members</span></span>  
  
|<span data-ttu-id="867be-107">Член</span><span class="sxs-lookup"><span data-stu-id="867be-107">Member</span></span>|<span data-ttu-id="867be-108">Описание</span><span class="sxs-lookup"><span data-stu-id="867be-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="867be-109">Методы Режиттед будут заблокированы из встроенных в другие методы.</span><span class="sxs-lookup"><span data-stu-id="867be-109">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="867be-110">Получение `GetFunctionParameters` обратных вызовов для всех методов, которые подставляемые методы режиттед.</span><span class="sxs-lookup"><span data-stu-id="867be-110">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="867be-111">Требования</span><span class="sxs-lookup"><span data-stu-id="867be-111">Requirements</span></span>  

 <span data-ttu-id="867be-112">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="867be-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="867be-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="867be-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="867be-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="867be-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="867be-115">**Платформа .NET Framework версии:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="867be-115">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="867be-116">См. также</span><span class="sxs-lookup"><span data-stu-id="867be-116">See also</span></span>

- [<span data-ttu-id="867be-117">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="867be-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
