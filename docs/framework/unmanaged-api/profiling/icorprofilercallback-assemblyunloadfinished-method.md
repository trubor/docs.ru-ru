---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: AssemblyUnloadFinished'
title: Метод ICorProfilerCallback::AssemblyUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: c3c87644602ede3b849d13624b0cc0a2df71e2fd
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760673"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a>Метод ICorProfilerCallback::AssemblyUnloadFinished

Уведомляет профилировщик о том, что сборка была выгружена.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Параметры

`assemblyId` окне Определяет выгрузку сборки.

`hrStatus` окне Значение HRESULT, указывающее, успешно ли выгружена сборка.

## <a name="remarks"></a>Remarks  

 Значение недопустимо `assemblyId` для информационного запроса после возврата метода [ICorProfilerCallback:: ассемблюнлоадстартед](icorprofilercallback-assemblyunloadstarted-method.md) .  
  
 Некоторые части выгрузки сборки могут продолжаться после `AssemblyUnloadFinished` обратного вызова. Ошибка HRESULT в `hrStatus` указывает на сбой. Однако значение HRESULT в случае успеха в `hrStatus` указывает только на то, что первая часть выгрузки сборки завершилась успешно.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
