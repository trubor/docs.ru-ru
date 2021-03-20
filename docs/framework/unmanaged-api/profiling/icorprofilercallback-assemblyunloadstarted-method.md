---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ассемблюнлоадстартед'
title: Метод ICorProfilerCallback::AssemblyUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
ms.openlocfilehash: 91c0b6a600a1c7c12905a7a9817e6e7e9601c3c0
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759473"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a>Метод ICorProfilerCallback::AssemblyUnloadStarted

Уведомляет профилировщик о выгрузке сборки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a>Параметры

`assemblyId` окне Определяет выгрузку сборки.

## <a name="remarks"></a>Remarks  

 Значение недопустимо `assemblyId` для информационного запроса после `AssemblyUnloadStarted` возврата метода — это последний шанс профилировщика получить сведения об этой сборке.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
- [Метод AssemblyUnloadFinished](icorprofilercallback-assemblyunloadfinished-method.md)
