---
description: 'Дополнительные сведения: перечисление COR_PRF_SNAPSHOT_INFO'
title: Перечисление COR_PRF_SNAPSHOT_INFO
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: fcdaeeb6170cb9998281100c5628b3d95f9e9326
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753345"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="185d7-103">Перечисление COR_PRF_SNAPSHOT_INFO</span><span class="sxs-lookup"><span data-stu-id="185d7-103">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>

<span data-ttu-id="185d7-104">Указывает объем данных, которые необходимо передать обратно с помощью моментального снимка стека при каждом вызове функции [стаккснапшоткаллбакк](stacksnapshotcallback-function.md) профилировщика.</span><span class="sxs-lookup"><span data-stu-id="185d7-104">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="185d7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="185d7-105">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="185d7-106">Члены</span><span class="sxs-lookup"><span data-stu-id="185d7-106">Members</span></span>  
  
|<span data-ttu-id="185d7-107">Элементы</span><span class="sxs-lookup"><span data-stu-id="185d7-107">Members</span></span>|<span data-ttu-id="185d7-108">Описание</span><span class="sxs-lookup"><span data-stu-id="185d7-108">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="185d7-109">Указывает, что значения должны передаваться для всех `StackSnapshotCallback` параметров, кроме `context` параметра.</span><span class="sxs-lookup"><span data-stu-id="185d7-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="185d7-110">Указывает, что значения должны передаваться для всех `StackSnapshotCallback` параметров, включая `context` параметр.</span><span class="sxs-lookup"><span data-stu-id="185d7-110">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="185d7-111">Указывает, что будет использоваться более простой и альтернативный алгоритм анализа стека.</span><span class="sxs-lookup"><span data-stu-id="185d7-111">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="185d7-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="185d7-112">Remarks</span></span>  

 <span data-ttu-id="185d7-113">Значения, предоставляемые `COR_PRF_SNAPSHOT_INFO` перечислением, передаются в качестве параметров в метод [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="185d7-113">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="185d7-114">Требования</span><span class="sxs-lookup"><span data-stu-id="185d7-114">Requirements</span></span>  

 <span data-ttu-id="185d7-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="185d7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="185d7-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="185d7-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="185d7-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="185d7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="185d7-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="185d7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="185d7-119">См. также</span><span class="sxs-lookup"><span data-stu-id="185d7-119">See also</span></span>

- [<span data-ttu-id="185d7-120">Метод DoStackSnapshot</span><span class="sxs-lookup"><span data-stu-id="185d7-120">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="185d7-121">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="185d7-121">Profiling Enumerations</span></span>](profiling-enumerations.md)
