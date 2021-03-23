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
ms.openlocfilehash: 7b2ca813d610c2b41d97d8cd76dac22ca38802d7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805640"
---
# <a name="icorprofilercallback10eventpipeeventdelivered-method"></a><span data-ttu-id="22b46-103">Метод ICorProfilerCallback10:: Евентпипивентделиверед</span><span class="sxs-lookup"><span data-stu-id="22b46-103">ICorProfilerCallback10::EventPipeEventDelivered Method</span></span>

<span data-ttu-id="22b46-104">Уведомляет профилировщик о том, что событие Евентпипе доставлено в текущий активный сеанс профилировщика.</span><span class="sxs-lookup"><span data-stu-id="22b46-104">Notifies the profiler whenever an EventPipe event has been delivered to the profiler's currently active session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22b46-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="22b46-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="22b46-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="22b46-106">Parameters</span></span>

<span data-ttu-id="22b46-107">`provider` окне Поставщик, от которого поступило это событие.</span><span class="sxs-lookup"><span data-stu-id="22b46-107">`provider` [in] The provider that this event originated from.</span></span>

<span data-ttu-id="22b46-108">`eventId` окне Идентификатор доставляемого события.</span><span class="sxs-lookup"><span data-stu-id="22b46-108">`eventId` [in] The ID of the event being delivered.</span></span>

<span data-ttu-id="22b46-109">`eventVersion` окне Версия доставляемого события.</span><span class="sxs-lookup"><span data-stu-id="22b46-109">`eventVersion` [in] The version of the event being delivered.</span></span>

<span data-ttu-id="22b46-110">`cbMetadataBlob` окне Длина (в байтах) `metadataBlob` .</span><span class="sxs-lookup"><span data-stu-id="22b46-110">`cbMetadataBlob` [in] The length, in bytes, of `metadataBlob`.</span></span>

<span data-ttu-id="22b46-111">`metadataBlob` окне Указатель на большой двоичный объект метаданных для события.</span><span class="sxs-lookup"><span data-stu-id="22b46-111">`metadataBlob` [in] A pointer to the metadata blob for the event.</span></span>

<span data-ttu-id="22b46-112">`cbEventData` окне Длина (в байтах) `eventData` .</span><span class="sxs-lookup"><span data-stu-id="22b46-112">`cbEventData` [in] The length, in bytes, of `eventData`.</span></span>

<span data-ttu-id="22b46-113">`eventData` окне Полезная нагрузка для события.</span><span class="sxs-lookup"><span data-stu-id="22b46-113">`eventData` [in] The payload for the event.</span></span>

<span data-ttu-id="22b46-114">`pActivityId` окне Указатель на идентификатор GUID, представляющий идентификатор действия события, или значение NULL.</span><span class="sxs-lookup"><span data-stu-id="22b46-114">`pActivityId` [in] A pointer to the GUID that represents the event's activity ID, or NULL.</span></span>

<span data-ttu-id="22b46-115">`pRelatedActivityId` окне Указатель на идентификатор GUID, представляющий идентификатор действия, связанного с событием, или значение NULL.</span><span class="sxs-lookup"><span data-stu-id="22b46-115">`pRelatedActivityId` [in] A pointer to the GUID that represents the event's related activity ID, or NULL.</span></span>

<span data-ttu-id="22b46-116">`eventThread` окне Идентификатор потока, в котором произошло событие.</span><span class="sxs-lookup"><span data-stu-id="22b46-116">`eventThread` [in] The ID of the thread the event occurred on.</span></span>

<span data-ttu-id="22b46-117">`numStackFrames` окне Число элементов в `stackFrames` массиве.</span><span class="sxs-lookup"><span data-stu-id="22b46-117">`numStackFrames` [in] The number of elements in the `stackFrames` array.</span></span>

<span data-ttu-id="22b46-118">`stackFrames` окне Массив адресов кода, представляющих управляемый стек вызовов события.</span><span class="sxs-lookup"><span data-stu-id="22b46-118">`stackFrames` [in] An array of code addresses representing the managed callstack of the event.</span></span>

## <a name="requirements"></a><span data-ttu-id="22b46-119">Требования</span><span class="sxs-lookup"><span data-stu-id="22b46-119">Requirements</span></span>  

<span data-ttu-id="22b46-120">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="22b46-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="22b46-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="22b46-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="22b46-122">**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22b46-122">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22b46-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="22b46-123">See also</span></span>

- [<span data-ttu-id="22b46-124">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="22b46-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="22b46-125">Интерфейс ICorProfilerCallback10</span><span class="sxs-lookup"><span data-stu-id="22b46-125">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="22b46-126">Интерфейс ICorProfilerInfo12</span><span class="sxs-lookup"><span data-stu-id="22b46-126">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="22b46-127">ICorProfilerInfo12. Евентпипестартсессион, метод</span><span class="sxs-lookup"><span data-stu-id="22b46-127">ICorProfilerInfo12.EventPipeStartSession Method</span></span>](icorprofilerinfo12-eventpipestartsession-method.md)
