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
# <a name="icorprofilerinfo12eventpipewriteevent-method"></a>Метод ICorProfilerInfo12:: Евентпипевритивент

Записывает событие Евентпипе в любые прослушиватели, которые включили это событие.
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
    HRESULT EventPipeWriteEvent(
                [in] EVENTPIPE_EVENT    event,
                [in] UINT32             cData,
                [in, size_is(cData)]
                     COR_PRF_EVENT_DATA data[],
                [in] LPCGUID            pActivityId,
                [in] LPCGUID            pRelatedActivityId);
```  
  
## <a name="parameters"></a>Параметры

`event` окне Идентификатор записываемого события.

`cData` окне Количество элементов в `data` .

`data` окне Массив, `COR_PRF_EVENT_DATA` содержащий аргументы события.

`pActivityId` окне Указатель на идентификатор GUID, указывающий идентификатор действия события.

`pRelatedActivityId` окне Указатель на идентификатор GUID, указывающий идентификатор связанного действия события.

## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).
**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>См. также раздел

- [Профилирующие интерфейсы](profiling-interfaces.md)
- [Интерфейс ICorProfilerCallback10](icorprofilercallback10-interface.md)
- [Интерфейс ICorProfilerInfo12](icorprofilerinfo12-interface.md)
- [Структура COR_PRF_EVENT_DATA](cor-prf-event-data-structure.md)
