---
description: 'Дополнительные сведения о методе: ICorProfilerInfo12:: Евентпипедефинивент'
title: 'Метод ICorProfilerInfo12:: Евентпипедефинивент'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeDefineEvent
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 845f7f26dce7aa0f4b7d895b9f04cc89e7ac7192
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805757"
---
# <a name="icorprofilerinfo12eventpipedefineevent-method"></a><span data-ttu-id="ffcb8-103">Метод ICorProfilerInfo12:: Евентпипедефинивент</span><span class="sxs-lookup"><span data-stu-id="ffcb8-103">ICorProfilerInfo12::EventPipeDefineEvent Method</span></span>

<span data-ttu-id="ffcb8-104">Определяет событие Евентпипе для существующего поставщика.</span><span class="sxs-lookup"><span data-stu-id="ffcb8-104">Defines an EventPipe event on an existing provider.</span></span> <span data-ttu-id="ffcb8-105">Этот поставщик можно использовать для записи событий Евентпипе, которые могут получать другие прослушиватели.</span><span class="sxs-lookup"><span data-stu-id="ffcb8-105">This provider can be used to write EventPipe events that other listeners can receive.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="ffcb8-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ffcb8-106">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeDefineEvent(
                [in] EVENTPIPE_PROVIDER     provider,
                [in, string] const WCHAR   *eventName,
                [in] UINT32                 eventID,
                [in] UINT64                 keywords,
                [in] UINT32                 eventVersion,
                [in] UINT32                 level,
                [in] UINT8                  opcode,
                [in] BOOL                   needStack,
                [in] UINT32                 cParamDescs,
                [in, size_is(cParamDescs)]
                     COR_PRF_EVENTPIPE_PARAM_DESC pParamDescs[],
                [out] EVENTPIPE_EVENT      *pEvent);
```  
  
## <a name="parameters"></a><span data-ttu-id="ffcb8-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="ffcb8-107">Parameters</span></span>

<span data-ttu-id="ffcb8-108">`provider` окне Идентификатор поставщика, для которого определяется событие.</span><span class="sxs-lookup"><span data-stu-id="ffcb8-108">`provider` [in] The ID of the provider to define an event on.</span></span>

<span data-ttu-id="ffcb8-109">`eventName` окне Указатель на строку расширенных символов, заканчивающуюся нулем, которая содержит имя события.</span><span class="sxs-lookup"><span data-stu-id="ffcb8-109">`eventName` [in] A pointer to a null terminated wide character string that contains the event name.</span></span>

<span data-ttu-id="ffcb8-110">`eventID` окне Идентификатор определяемого события.</span><span class="sxs-lookup"><span data-stu-id="ffcb8-110">`eventID` [in] The ID of the event being defined.</span></span>

<span data-ttu-id="ffcb8-111">`keywords` окне Ключевые слова определяемого события.</span><span class="sxs-lookup"><span data-stu-id="ffcb8-111">`keywords` [in] The keywords of the event being defined.</span></span>

<span data-ttu-id="ffcb8-112">`eventVersion` окне Версия определяемого события.</span><span class="sxs-lookup"><span data-stu-id="ffcb8-112">`eventVersion` [in] The version of the event being defined.</span></span>

<span data-ttu-id="ffcb8-113">`level` окне Уровень определяемого события.</span><span class="sxs-lookup"><span data-stu-id="ffcb8-113">`level` [in] The level of the event being defined.</span></span>

<span data-ttu-id="ffcb8-114">`opcode` окне Код операции для определяемого события.</span><span class="sxs-lookup"><span data-stu-id="ffcb8-114">`opcode` [in] The opcode of the event being defined.</span></span>

<span data-ttu-id="ffcb8-115">`needStack` окне Значение типа `BOOL` , указывающее, должны ли собираться управляемые стеки при каждом срабатывании этого события.</span><span class="sxs-lookup"><span data-stu-id="ffcb8-115">`needStack` [in] A `BOOL` indicating whether managed stacks should be collected each time this event fires.</span></span>

<span data-ttu-id="ffcb8-116">`cParamDescs` окне Число параметров в `pParamDescs` .</span><span class="sxs-lookup"><span data-stu-id="ffcb8-116">`cParamDescs` [in] The count of the number of parameters in `pParamDescs`.</span></span>

<span data-ttu-id="ffcb8-117">`pParamDescs` окне Массив, `COR_PRF_EVENTPIPE_PARAM_DESC` определяющий типы параметров для определяемого события.</span><span class="sxs-lookup"><span data-stu-id="ffcb8-117">`pParamDescs` [in] An array of `COR_PRF_EVENTPIPE_PARAM_DESC` defining the parameter types to the event being defined.</span></span>

<span data-ttu-id="ffcb8-118">`pEvent` заполняет Предоставленный вызывающим объектом указатель, который будет заполнен ИДЕНТИФИКАТОРом события, которое определяется при возврате функции.</span><span class="sxs-lookup"><span data-stu-id="ffcb8-118">`pEvent` [out] A caller provided pointer that will be filled with the ID of the event being defined when the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="ffcb8-119">Требования</span><span class="sxs-lookup"><span data-stu-id="ffcb8-119">Requirements</span></span>  

<span data-ttu-id="ffcb8-120">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="ffcb8-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="ffcb8-121">**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffcb8-121">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ffcb8-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ffcb8-122">See also</span></span>

- [<span data-ttu-id="ffcb8-123">Общие сведения об EventPipe</span><span class="sxs-lookup"><span data-stu-id="ffcb8-123">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="ffcb8-124">Хорошо известные Евентпровидерс</span><span class="sxs-lookup"><span data-stu-id="ffcb8-124">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="ffcb8-125">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="ffcb8-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ffcb8-126">Интерфейс ICorProfilerCallback10</span><span class="sxs-lookup"><span data-stu-id="ffcb8-126">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="ffcb8-127">Интерфейс ICorProfilerInfo12</span><span class="sxs-lookup"><span data-stu-id="ffcb8-127">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="ffcb8-128">Структура COR_PRF_EVENTPIPE_PARAM_DESC</span><span class="sxs-lookup"><span data-stu-id="ffcb8-128">COR_PRF_EVENTPIPE_PARAM_DESC Structure</span></span>](cor-prf-eventpipe-param-desc-structure.md)
