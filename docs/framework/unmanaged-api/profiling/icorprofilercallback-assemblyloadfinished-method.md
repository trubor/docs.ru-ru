---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: AssemblyLoadFinished'
title: Метод ICorProfilerCallback::AssemblyLoadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: accddef08f3cb76ef2cb1b70993aee24cf83ae50
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760674"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a>Метод ICorProfilerCallback::AssemblyLoadFinished

Уведомляет профилировщик о том, что загрузка сборки завершена.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Параметры

`assemblyId` окне Определяет загруженную сборку.

`hrStatus` окне Значение HRESULT, указывающее, успешно ли завершена загрузка сборки.

## <a name="remarks"></a>Remarks  

 Значение недопустимо `assemblyId` для информационного запроса до `AssemblyLoadFinished` вызова метода.  
  
 Некоторые части загрузки сборки могут продолжаться после `AssemblyLoadFinished` обратного вызова. Ошибка HRESULT в `hrStatus` указывает на сбой. Однако значение HRESULT в случае успеха в `hrStatus` указывает только на то, что первая часть загрузки сборки завершилась успешно.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
