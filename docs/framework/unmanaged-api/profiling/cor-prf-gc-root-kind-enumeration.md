---
description: 'Дополнительные сведения: перечисление COR_PRF_GC_ROOT_KIND'
title: Перечисление COR_PRF_GC_ROOT_KIND
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
ms.openlocfilehash: 148d48458c906974d76b9e0ec0cb6b4d15ee49ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648783"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="8f69a-103">Перечисление COR_PRF_GC_ROOT_KIND</span><span class="sxs-lookup"><span data-stu-id="8f69a-103">COR_PRF_GC_ROOT_KIND Enumeration</span></span>

<span data-ttu-id="8f69a-104">Указывает тип корневого элемента сборки мусора, предоставляемый обратным вызовом [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8f69a-104">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f69a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8f69a-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="8f69a-106">Члены</span><span class="sxs-lookup"><span data-stu-id="8f69a-106">Members</span></span>  
  
|<span data-ttu-id="8f69a-107">Член</span><span class="sxs-lookup"><span data-stu-id="8f69a-107">Member</span></span>|<span data-ttu-id="8f69a-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8f69a-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="8f69a-109">Корень — это переменная в стеке.</span><span class="sxs-lookup"><span data-stu-id="8f69a-109">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="8f69a-110">Корень — это запись в очереди метода завершения.</span><span class="sxs-lookup"><span data-stu-id="8f69a-110">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="8f69a-111">Корень является обработчиком сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="8f69a-111">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="8f69a-112">Тип корня не указан.</span><span class="sxs-lookup"><span data-stu-id="8f69a-112">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f69a-113">Требования</span><span class="sxs-lookup"><span data-stu-id="8f69a-113">Requirements</span></span>  

 <span data-ttu-id="8f69a-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f69a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f69a-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8f69a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f69a-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f69a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f69a-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f69a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f69a-118">См. также</span><span class="sxs-lookup"><span data-stu-id="8f69a-118">See also</span></span>

- [<span data-ttu-id="8f69a-119">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="8f69a-119">Profiling Enumerations</span></span>](profiling-enumerations.md)
