---
description: 'Дополнительные сведения о методе: ICorProfilerInfo12:: Евентпипеаддпровидертосессион'
title: 'Метод ICorProfilerInfo12:: Евентпипеаддпровидертосессион'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeAddProviderToSession
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 70654660c496211c20459ef9ba37dfbd96b829b3
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805692"
---
# <a name="icorprofilerinfo12eventpipeaddprovidertosession-method"></a>Метод ICorProfilerInfo12:: Евентпипеаддпровидертосессион

Добавляет поставщик в существующий сеанс Евентпипе.
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
    HRESULT EventPipeAddProviderToSession(
        [in] EVENTPIPE_SESSION                 session,
        [in] COR_PRF_EVENTPIPE_PROVIDER_CONFIG providerConfig);
```  
  
## <a name="parameters"></a>Параметры

`session` окне Идентификатор сеанса, в который добавляется поставщик.

`providerConfig` окне Объект, `COR_PRF_EVENTPIPE_PROVIDER_CONFIG` описывающий поставщика для добавления в сеанс.

## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).
**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>См. также раздел

- [Общие сведения об EventPipe](../../../core/diagnostics/eventpipe.md)
- [Хорошо известные Евентпровидерс](../../../core/diagnostics/well-known-event-providers.md)
- [Профилирующие интерфейсы](profiling-interfaces.md)
- [Интерфейс ICorProfilerCallback10](icorprofilercallback10-interface.md)
- [Интерфейс ICorProfilerInfo12](icorprofilerinfo12-interface.md)
- [Структура COR_PRF_EVENTPIPE_PROVIDER_CONFIG](cor-prf-eventpipe-provider-config-structure.md)
