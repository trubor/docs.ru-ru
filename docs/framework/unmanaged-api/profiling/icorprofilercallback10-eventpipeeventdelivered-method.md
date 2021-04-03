---
description: 'Дополнительные сведения о методе: ICorProfilerCallback10:: Евентпипивентделиверед'
title: 'Метод ICorProfilerCallback10:: Евентпипивентделиверед'
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10.EventPipeEventDelivered
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 73f3eb64671b22b1ec16b5a5b1b24115f7f65f6d
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231340"
---
# <a name="icorprofilercallback10eventpipeeventdelivered-method"></a><span data-ttu-id="a4b81-103">Метод ICorProfilerCallback10:: Евентпипивентделиверед</span><span class="sxs-lookup"><span data-stu-id="a4b81-103">ICorProfilerCallback10::EventPipeEventDelivered Method</span></span>

<span data-ttu-id="a4b81-104">Уведомляет профилировщик о том, что событие Евентпипе доставлено в текущий активный сеанс профилировщика.</span><span class="sxs-lookup"><span data-stu-id="a4b81-104">Notifies the profiler whenever an EventPipe event has been delivered to the profiler's currently active session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b81-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a4b81-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeEventDelivered(
        [in] EVENTPIPE_PROVIDER provider,
        [in] DWORD eventId,
        [in] DWORD eventVersion,
        [in] ULONG cbMetadataBlob,
        [in, size_is(cbMetadataBlob)] LPCBYTE metadataBlob,
        [in] ULONG cbEventData,
        [in, size_is(cbEventData)] LPCBYTE eventData,
        [in] LPCGUID pActivityId,
        [in] LPCGUID pRelatedActivityId,
        [in] ThreadID eventThread,
        [in] ULONG numStackFrames,
        [in, length_is(numStackFrames)] UINT_PTR stackFrames[]);
```  
  
## <a name="parameters"></a><span data-ttu-id="a4b81-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a4b81-106">Parameters</span></span>

<span data-ttu-id="a4b81-107">`provider` окне Поставщик, от которого поступило это событие.</span><span class="sxs-lookup"><span data-stu-id="a4b81-107">`provider` [in] The provider that this event originated from.</span></span>

<span data-ttu-id="a4b81-108">`eventId` окне Идентификатор доставляемого события.</span><span class="sxs-lookup"><span data-stu-id="a4b81-108">`eventId` [in] The ID of the event being delivered.</span></span>

<span data-ttu-id="a4b81-109">`eventVersion` окне Версия доставляемого события.</span><span class="sxs-lookup"><span data-stu-id="a4b81-109">`eventVersion` [in] The version of the event being delivered.</span></span>

<span data-ttu-id="a4b81-110">`cbMetadataBlob` окне Длина (в байтах) `metadataBlob` .</span><span class="sxs-lookup"><span data-stu-id="a4b81-110">`cbMetadataBlob` [in] The length, in bytes, of `metadataBlob`.</span></span>

<span data-ttu-id="a4b81-111">`metadataBlob` окне Указатель на большой двоичный объект метаданных для события.</span><span class="sxs-lookup"><span data-stu-id="a4b81-111">`metadataBlob` [in] A pointer to the metadata blob for the event.</span></span>

<span data-ttu-id="a4b81-112">`cbEventData` окне Длина (в байтах) `eventData` .</span><span class="sxs-lookup"><span data-stu-id="a4b81-112">`cbEventData` [in] The length, in bytes, of `eventData`.</span></span>

<span data-ttu-id="a4b81-113">`eventData` окне Полезная нагрузка для события.</span><span class="sxs-lookup"><span data-stu-id="a4b81-113">`eventData` [in] The payload for the event.</span></span>

<span data-ttu-id="a4b81-114">`pActivityId` окне Указатель на идентификатор GUID, представляющий идентификатор действия события, или значение NULL.</span><span class="sxs-lookup"><span data-stu-id="a4b81-114">`pActivityId` [in] A pointer to the GUID that represents the event's activity ID, or NULL.</span></span>

<span data-ttu-id="a4b81-115">`pRelatedActivityId` окне Указатель на идентификатор GUID, представляющий идентификатор действия, связанного с событием, или значение NULL.</span><span class="sxs-lookup"><span data-stu-id="a4b81-115">`pRelatedActivityId` [in] A pointer to the GUID that represents the event's related activity ID, or NULL.</span></span>

<span data-ttu-id="a4b81-116">`eventThread` окне Идентификатор потока, в котором произошло событие.</span><span class="sxs-lookup"><span data-stu-id="a4b81-116">`eventThread` [in] The ID of the thread the event occurred on.</span></span>

<span data-ttu-id="a4b81-117">`numStackFrames` окне Число элементов в `stackFrames` массиве.</span><span class="sxs-lookup"><span data-stu-id="a4b81-117">`numStackFrames` [in] The number of elements in the `stackFrames` array.</span></span>

<span data-ttu-id="a4b81-118">`stackFrames` окне Массив адресов кода, представляющих управляемый стек вызовов события.</span><span class="sxs-lookup"><span data-stu-id="a4b81-118">`stackFrames` [in] An array of code addresses representing the managed callstack of the event.</span></span>

## <a name="requirements"></a><span data-ttu-id="a4b81-119">Требования</span><span class="sxs-lookup"><span data-stu-id="a4b81-119">Requirements</span></span>  

<span data-ttu-id="a4b81-120">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="a4b81-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="a4b81-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a4b81-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="a4b81-122">**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4b81-122">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b81-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a4b81-123">See also</span></span>

- [<span data-ttu-id="a4b81-124">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="a4b81-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a4b81-125">Интерфейс ICorProfilerCallback10</span><span class="sxs-lookup"><span data-stu-id="a4b81-125">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="a4b81-126">Интерфейс ICorProfilerInfo12</span><span class="sxs-lookup"><span data-stu-id="a4b81-126">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="a4b81-127">ICorProfilerInfo12. Евентпипестартсессион, метод</span><span class="sxs-lookup"><span data-stu-id="a4b81-127">ICorProfilerInfo12.EventPipeStartSession Method</span></span>](icorprofilerinfo12-eventpipestartsession-method.md)
