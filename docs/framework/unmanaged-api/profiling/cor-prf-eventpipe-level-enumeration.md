---
description: 'Дополнительные сведения: перечисление COR_PRF_EVENTPIPE_LEVEL'
title: Перечисление COR_PRF_EVENTPIPE_LEVEL
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_LEVEL
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: da8211da1a9bb6262b078c5e56bee1d0c1f9342e
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805822"
---
# <a name="cor_prf_eventpipe_level-enumeration"></a><span data-ttu-id="c5cc1-103">Перечисление COR_PRF_EVENTPIPE_LEVEL</span><span class="sxs-lookup"><span data-stu-id="c5cc1-103">COR_PRF_EVENTPIPE_LEVEL Enumeration</span></span>

<span data-ttu-id="c5cc1-104">Описывает уровень события Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="c5cc1-104">Describes the level of an EventPipe event.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="c5cc1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c5cc1-105">Syntax</span></span>  
  
```cpp  
typedef enum
{
    COR_PRF_EVENTPIPE_LOGALWAYS = 0,
    COR_PRF_EVENTPIPE_CRITICAL = 1,
    COR_PRF_EVENTPIPE_ERROR = 2,
    COR_PRF_EVENTPIPE_WARNING = 3,
    COR_PRF_EVENTPIPE_INFORMATIONAL = 4,
    COR_PRF_EVENTPIPE_VERBOSE = 5
} COR_PRF_EVENTPIPE_LEVEL;
```  
  
## <a name="members"></a><span data-ttu-id="c5cc1-106">Участники</span><span class="sxs-lookup"><span data-stu-id="c5cc1-106">Members</span></span>  
  
|<span data-ttu-id="c5cc1-107">Член</span><span class="sxs-lookup"><span data-stu-id="c5cc1-107">Member</span></span>|<span data-ttu-id="c5cc1-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c5cc1-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_EVENTPIPE_LOGALWAYS`|<span data-ttu-id="c5cc1-109">Событие всегда заносится в журнал.</span><span class="sxs-lookup"><span data-stu-id="c5cc1-109">The event is always logged.</span></span>|
|`COR_PRF_EVENTPIPE_CRITICAL`|<span data-ttu-id="c5cc1-110">Событие представляет критическое сообщение.</span><span class="sxs-lookup"><span data-stu-id="c5cc1-110">The event represents a critical message.</span></span>|
|`COR_PRF_EVENTPIPE_ERROR`|<span data-ttu-id="c5cc1-111">Событие представляет сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="c5cc1-111">The event represents an error message.</span></span>|
|`COR_PRF_EVENTPIPE_WARNING`|<span data-ttu-id="c5cc1-112">Событие представляет предупреждающее сообщение.</span><span class="sxs-lookup"><span data-stu-id="c5cc1-112">The event represents a warning message.</span></span>|
|`COR_PRF_EVENTPIPE_INFORMATIONAL`|<span data-ttu-id="c5cc1-113">Событие представляет информационное сообщение.</span><span class="sxs-lookup"><span data-stu-id="c5cc1-113">The event represents an informational message.</span></span>|
|`COR_PRF_EVENTPIPE_VERBOSE`|<span data-ttu-id="c5cc1-114">Событие представляет подробное сообщение.</span><span class="sxs-lookup"><span data-stu-id="c5cc1-114">The event represents a verbose message.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="c5cc1-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="c5cc1-115">Remarks</span></span>  

 <span data-ttu-id="c5cc1-116">`COR_PRF_EVENTPIPE_LEVEL`Перечисление используется методом [ICorProfilerInfo12:: евентпипедефинивент](icorprofilerinfo12-eventpipedefineevent-method.md) для указания уровня определяемого события.</span><span class="sxs-lookup"><span data-stu-id="c5cc1-116">The `COR_PRF_EVENTPIPE_LEVEL` enumeration is used by the [ICorProfilerInfo12::EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) method to indicate the level of the event being defined.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="c5cc1-117">Требования</span><span class="sxs-lookup"><span data-stu-id="c5cc1-117">Requirements</span></span>  

<span data-ttu-id="c5cc1-118">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c5cc1-118">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="c5cc1-119">**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5cc1-119">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c5cc1-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c5cc1-120">See also</span></span>

- [<span data-ttu-id="c5cc1-121">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="c5cc1-121">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="c5cc1-122">ICorProfilerInfo12:: Евентпипедефинивент</span><span class="sxs-lookup"><span data-stu-id="c5cc1-122">ICorProfilerInfo12::EventPipeDefineEvent</span></span>](icorprofilerinfo12-eventpipedefineevent-method.md)
