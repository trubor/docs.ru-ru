---
description: 'Дополнительные сведения о методе: ICorProfilerInfo12:: Евентпипежетпровидеринфо'
title: 'Метод ICorProfilerInfo12:: Евентпипежетпровидеринфо'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeGetProviderInfo
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 7bc7ffe1c31e88dc1c65f1670f9bd179e732abfe
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805705"
---
# <a name="icorprofilerinfo12eventpipegetproviderinfo-method"></a>Метод ICorProfilerInfo12:: Евентпипежетпровидеринфо

Создает поставщик Евентпипе, который профилировщик может использовать для записи событий для получения других прослушивателей Евентпипе.
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
    HRESULT EventPipeGetProviderInfo(
                [in] EVENTPIPE_PROVIDER provider,
                [in]  ULONG      cchName,
                [out] ULONG      *pcchName,
                [out, annotation("_Out_writes_to_(cchName, *pcchName)")]
                      WCHAR      providerName[]);
```  
  
## <a name="parameters"></a>Параметры

`provider` окне Идентификатор поставщика, для которого необходимо предоставить имя.

`cchName` окне Размер (в символах) `providerName` .

`pcchName` заполняет Указатель на общую длину символов `providerName` .

`providerName` заполняет Вызывающий объект предоставил широкий буфер символов. Когда функция возвращает буфер, будет содержать имя поставщика.

## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).
**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>См. также раздел

- [Общие сведения об EventPipe](../../../core/diagnostics/eventpipe.md)
- [Хорошо известные Евентпровидерс](../../../core/diagnostics/well-known-event-providers.md)
- [Профилирующие интерфейсы](profiling-interfaces.md)
- [Интерфейс ICorProfilerCallback10](icorprofilercallback10-interface.md)
- [Интерфейс ICorProfilerInfo12](icorprofilerinfo12-interface.md)
