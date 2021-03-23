---
description: 'Дополнительные сведения о методе: ICorProfilerInfo12:: Евентпипевритивент'
title: 'Метод ICorProfilerInfo12:: Евентпипевритивент'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeWriteEvent
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a0a06ff0fa1c936518586834f4dfc73810ef0e44
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805744"
---
# <a name="icorprofilerinfo12eventpipewriteevent-method"></a><span data-ttu-id="710a4-103">Метод ICorProfilerInfo12:: Евентпипевритивент</span><span class="sxs-lookup"><span data-stu-id="710a4-103">ICorProfilerInfo12::EventPipeWriteEvent Method</span></span>

<span data-ttu-id="710a4-104">Записывает событие Евентпипе в любые прослушиватели, которые включили это событие.</span><span class="sxs-lookup"><span data-stu-id="710a4-104">Writes an EventPipe event to any listeners who have enabled this event.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="710a4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="710a4-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeWriteEvent(
                [in] EVENTPIPE_EVENT    event,
                [in] UINT32             cData,
                [in, size_is(cData)]
                     COR_PRF_EVENT_DATA data[],
                [in] LPCGUID            pActivityId,
                [in] LPCGUID            pRelatedActivityId);
```  
  
## <a name="parameters"></a><span data-ttu-id="710a4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="710a4-106">Parameters</span></span>

<span data-ttu-id="710a4-107">`event` окне Идентификатор записываемого события.</span><span class="sxs-lookup"><span data-stu-id="710a4-107">`event` [in] The ID of the event being written.</span></span>

<span data-ttu-id="710a4-108">`cData` окне Количество элементов в `data` .</span><span class="sxs-lookup"><span data-stu-id="710a4-108">`cData` [in] The number of elements in `data`.</span></span>

<span data-ttu-id="710a4-109">`data` окне Массив, `COR_PRF_EVENT_DATA` содержащий аргументы события.</span><span class="sxs-lookup"><span data-stu-id="710a4-109">`data` [in] An array of `COR_PRF_EVENT_DATA` containing the event arguments.</span></span>

<span data-ttu-id="710a4-110">`pActivityId` окне Указатель на идентификатор GUID, указывающий идентификатор действия события.</span><span class="sxs-lookup"><span data-stu-id="710a4-110">`pActivityId` [in] A pointer to a GUID specifying the event's activity ID.</span></span>

<span data-ttu-id="710a4-111">`pRelatedActivityId` окне Указатель на идентификатор GUID, указывающий идентификатор связанного действия события.</span><span class="sxs-lookup"><span data-stu-id="710a4-111">`pRelatedActivityId` [in] A pointer to a GUID specifying the event's related activity ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="710a4-112">Требования</span><span class="sxs-lookup"><span data-stu-id="710a4-112">Requirements</span></span>  

<span data-ttu-id="710a4-113">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="710a4-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="710a4-114">**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="710a4-114">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="710a4-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="710a4-115">See also</span></span>

- [<span data-ttu-id="710a4-116">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="710a4-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="710a4-117">Интерфейс ICorProfilerCallback10</span><span class="sxs-lookup"><span data-stu-id="710a4-117">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="710a4-118">Интерфейс ICorProfilerInfo12</span><span class="sxs-lookup"><span data-stu-id="710a4-118">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="710a4-119">Структура COR_PRF_EVENT_DATA</span><span class="sxs-lookup"><span data-stu-id="710a4-119">COR_PRF_EVENT_DATA Structure</span></span>](cor-prf-event-data-structure.md)
