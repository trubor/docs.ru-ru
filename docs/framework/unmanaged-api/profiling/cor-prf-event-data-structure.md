---
description: 'Дополнительные сведения: перечисление COR_PRF_EVENT_DATA'
title: Перечисление COR_PRF_EVENT_DATA
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENT_DATA
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 477f36476deb9c0d74e263703e36b134c91b5327
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805573"
---
# <a name="cor_prf_event_data-enumeration"></a><span data-ttu-id="225b1-103">Перечисление COR_PRF_EVENT_DATA</span><span class="sxs-lookup"><span data-stu-id="225b1-103">COR_PRF_EVENT_DATA Enumeration</span></span>

<span data-ttu-id="225b1-104">Описывает данные события для записываемого события Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="225b1-104">Describes the event data for an EventPipe event being written.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="225b1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="225b1-105">Syntax</span></span>  
  
```cpp  
typedef struct
{
    UINT64 ptr;
    UINT32 size;
    UINT32 reserved;
} COR_PRF_EVENT_DATA;
```  
  
## <a name="members"></a><span data-ttu-id="225b1-106">Участники</span><span class="sxs-lookup"><span data-stu-id="225b1-106">Members</span></span>  
  
|<span data-ttu-id="225b1-107">Член</span><span class="sxs-lookup"><span data-stu-id="225b1-107">Member</span></span>|<span data-ttu-id="225b1-108">Описание</span><span class="sxs-lookup"><span data-stu-id="225b1-108">Description</span></span>|  
|------------|-----------------|  
|`ptr`|<span data-ttu-id="225b1-109">Указатель на данные.</span><span class="sxs-lookup"><span data-stu-id="225b1-109">A pointer to the data.</span></span>|  
|`size`|<span data-ttu-id="225b1-110">Размер данных, на которые указывает `ptr` .</span><span class="sxs-lookup"><span data-stu-id="225b1-110">The size of the data pointed to by `ptr`.</span></span>|  
|`reserved`|<span data-ttu-id="225b1-111">Зарезервированное поле для конкретной реализации.</span><span class="sxs-lookup"><span data-stu-id="225b1-111">An reserved implementation specific field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="225b1-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="225b1-112">Remarks</span></span>  

 <span data-ttu-id="225b1-113">`COR_PRF_EVENT_DATA`Структура используется методом [ICorProfilerInfo12:: евентпипевритивент](icorprofilerinfo12-eventpipewriteevent-method.md) , чтобы провидате полезные данные для записываемого события.</span><span class="sxs-lookup"><span data-stu-id="225b1-113">The `COR_PRF_EVENT_DATA` structure is used by the [ICorProfilerInfo12::EventPipeWriteEvent](icorprofilerinfo12-eventpipewriteevent-method.md) method to providate the data payload for the event being written.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="225b1-114">Требования</span><span class="sxs-lookup"><span data-stu-id="225b1-114">Requirements</span></span>  

<span data-ttu-id="225b1-115">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="225b1-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="225b1-116">**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="225b1-116">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="225b1-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="225b1-117">See also</span></span>

- [<span data-ttu-id="225b1-118">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="225b1-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="225b1-119">ICorProfilerInfo12:: Евентпипевритивент</span><span class="sxs-lookup"><span data-stu-id="225b1-119">ICorProfilerInfo12::EventPipeWriteEvent</span></span>](icorprofilerinfo12-eventpipewriteevent-method.md)
