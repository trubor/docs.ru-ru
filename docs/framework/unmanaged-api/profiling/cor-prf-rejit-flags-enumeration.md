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
ms.openlocfilehash: aad66285e9b31558a68b8ccdfc71f103d1772946
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106921"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="16ea9-103">Перечисление COR_PRF_REJIT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="16ea9-103">COR_PRF_REJIT_FLAGS Enumeration</span></span>

<span data-ttu-id="16ea9-104">Содержит значения, указывающие поведение API [ICorProfilerInfo10:: рекуестрежитвисинлинерс](icorprofilerinfo10-requestrejitwithinliners-method.md) .</span><span class="sxs-lookup"><span data-stu-id="16ea9-104">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16ea9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="16ea9-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="16ea9-106">Члены</span><span class="sxs-lookup"><span data-stu-id="16ea9-106">Members</span></span>  
  
|<span data-ttu-id="16ea9-107">Член</span><span class="sxs-lookup"><span data-stu-id="16ea9-107">Member</span></span>|<span data-ttu-id="16ea9-108">Описание</span><span class="sxs-lookup"><span data-stu-id="16ea9-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="16ea9-109">Методы Режиттед будут заблокированы из встроенных в другие методы.</span><span class="sxs-lookup"><span data-stu-id="16ea9-109">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="16ea9-110">Получение `GetFunctionParameters` обратных вызовов для всех методов, которые подставляемые методы режиттед.</span><span class="sxs-lookup"><span data-stu-id="16ea9-110">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="16ea9-111">Требования</span><span class="sxs-lookup"><span data-stu-id="16ea9-111">Requirements</span></span>  

 <span data-ttu-id="16ea9-112">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="16ea9-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="16ea9-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="16ea9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="16ea9-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16ea9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16ea9-115">**Платформа .NET Framework версии:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16ea9-115">**.NET Framework Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="16ea9-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="16ea9-116">See also</span></span>

- [<span data-ttu-id="16ea9-117">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="16ea9-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
