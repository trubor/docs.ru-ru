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
# <a name="icorprofilercallback10eventpipeeventdelivered-method"></a>Метод ICorProfilerCallback10:: Евентпипивентделиверед

Уведомляет профилировщик о том, что событие Евентпипе доставлено в текущий активный сеанс профилировщика.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
## <a name="parameters"></a>Параметры

`provider` окне Поставщик, от которого поступило это событие.

`eventId` окне Идентификатор доставляемого события.

`eventVersion` окне Версия доставляемого события.

`cbMetadataBlob` окне Длина (в байтах) `metadataBlob` .

`metadataBlob` окне Указатель на большой двоичный объект метаданных для события.

`cbEventData` окне Длина (в байтах) `eventData` .

`eventData` окне Полезная нагрузка для события.

`pActivityId` окне Указатель на идентификатор GUID, представляющий идентификатор действия события, или значение NULL.

`pRelatedActivityId` окне Указатель на идентификатор GUID, представляющий идентификатор действия, связанного с событием, или значение NULL.

`eventThread` окне Идентификатор потока, в котором произошло событие.

`numStackFrames` окне Число элементов в `stackFrames` массиве.

`stackFrames` окне Массив адресов кода, представляющих управляемый стек вызовов события.

## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).  
**Заголовок:** CorProf.idl, CorProf.h  
**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Профилирующие интерфейсы](profiling-interfaces.md)
- [Интерфейс ICorProfilerCallback10](icorprofilercallback10-interface.md)
- [Интерфейс ICorProfilerInfo12](icorprofilerinfo12-interface.md)
- [ICorProfilerInfo12. Евентпипестартсессион, метод](icorprofilerinfo12-eventpipestartsession-method.md)
