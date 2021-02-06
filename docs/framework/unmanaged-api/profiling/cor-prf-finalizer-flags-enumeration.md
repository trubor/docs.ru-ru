---
description: 'Дополнительные сведения: перечисление COR_PRF_FINALIZER_FLAGS'
title: Перечисление COR_PRF_FINALIZER_FLAGS
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
ms.openlocfilehash: 96430b1ba3a38cce2801ed55f030395154c78dab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649188"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="4ea80-103">Перечисление COR_PRF_FINALIZER_FLAGS</span><span class="sxs-lookup"><span data-stu-id="4ea80-103">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>

<span data-ttu-id="4ea80-104">Описывает метод завершения для объекта.</span><span class="sxs-lookup"><span data-stu-id="4ea80-104">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ea80-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4ea80-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="4ea80-106">Члены</span><span class="sxs-lookup"><span data-stu-id="4ea80-106">Members</span></span>  
  
|<span data-ttu-id="4ea80-107">Член</span><span class="sxs-lookup"><span data-stu-id="4ea80-107">Member</span></span>|<span data-ttu-id="4ea80-108">Описание</span><span class="sxs-lookup"><span data-stu-id="4ea80-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="4ea80-109">Метод завершения является критическим.</span><span class="sxs-lookup"><span data-stu-id="4ea80-109">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ea80-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="4ea80-110">Remarks</span></span>  

 <span data-ttu-id="4ea80-111">`COR_PRF_FINALIZER_FLAGS`Перечисление используется методом [ICorProfilerCallback2:: финализеаблеобжекткуеуед](icorprofilercallback2-finalizeableobjectqueued-method.md) для описания метода завершения для объекта.</span><span class="sxs-lookup"><span data-stu-id="4ea80-111">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ea80-112">Требования</span><span class="sxs-lookup"><span data-stu-id="4ea80-112">Requirements</span></span>  

 <span data-ttu-id="4ea80-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ea80-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ea80-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4ea80-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ea80-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ea80-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ea80-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ea80-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea80-117">См. также</span><span class="sxs-lookup"><span data-stu-id="4ea80-117">See also</span></span>

- [<span data-ttu-id="4ea80-118">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="4ea80-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
