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
# <a name="icorprofilerinfo12eventpipedefineevent-method"></a>Метод ICorProfilerInfo12:: Евентпипедефинивент

Определяет событие Евентпипе для существующего поставщика. Этот поставщик можно использовать для записи событий Евентпипе, которые могут получать другие прослушиватели.
  
## <a name="syntax"></a>Синтаксис  
  
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
  
## <a name="parameters"></a>Параметры

`provider` окне Идентификатор поставщика, для которого определяется событие.

`eventName` окне Указатель на строку расширенных символов, заканчивающуюся нулем, которая содержит имя события.

`eventID` окне Идентификатор определяемого события.

`keywords` окне Ключевые слова определяемого события.

`eventVersion` окне Версия определяемого события.

`level` окне Уровень определяемого события.

`opcode` окне Код операции для определяемого события.

`needStack` окне Значение типа `BOOL` , указывающее, должны ли собираться управляемые стеки при каждом срабатывании этого события.

`cParamDescs` окне Число параметров в `pParamDescs` .

`pParamDescs` окне Массив, `COR_PRF_EVENTPIPE_PARAM_DESC` определяющий типы параметров для определяемого события.

`pEvent` заполняет Предоставленный вызывающим объектом указатель, который будет заполнен ИДЕНТИФИКАТОРом события, которое определяется при возврате функции.

## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).
**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>См. также раздел

- [Общие сведения об EventPipe](../../../core/diagnostics/eventpipe.md)
- [Хорошо известные Евентпровидерс](../../../core/diagnostics/well-known-event-providers.md)
- [Профилирующие интерфейсы](profiling-interfaces.md)
- [Интерфейс ICorProfilerCallback10](icorprofilercallback10-interface.md)
- [Интерфейс ICorProfilerInfo12](icorprofilerinfo12-interface.md)
- [Структура COR_PRF_EVENTPIPE_PARAM_DESC](cor-prf-eventpipe-param-desc-structure.md)
