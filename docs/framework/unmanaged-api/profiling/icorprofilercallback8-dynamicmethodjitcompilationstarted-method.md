---
description: 'Дополнительные сведения о методе: ICorProfilerCallback8::D Инамикмесоджиткомпилатионстартед'
title: 'ICorProfilerCallback8: метод:D Инамикмесоджиткомпилатионстартед'
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c03251ab3120fd93cbb8e6c2f1bb62a4527a92bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759928"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8: метод:D Инамикмесоджиткомпилатионстартед

[Поддерживается в платформа .NET Framework 4,7 и более поздних версиях]  
  
Уведомляет профилировщик каждый раз, когда запускается JIT-компиляция динамического метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a>Параметры  

`functionId`  
окне Идентификатор функции в памяти, для которой запускается JIT-компиляция.

`fIsSafeToBlock` [входные] `true` чтобы указать, что блокировка может привести к тому, что среда выполнения будет ожидать возврата вызывающим потоком из этого обратного вызова. `false` чтобы указать, что блокировка не повлияет на работу среды выполнения.  

`pILHeader` окне Указатель на первый байт заголовка IL метода.

`cbILHeader` окне Число байтов в заголовке IL.

## <a name="remarks"></a>Remarks  

Этот обратный вызов активируется всякий раз, когда динамический метод компилируется JIT-компилятором. Сюда входят различные суррогаты IL и методы LCG. Его цель — предоставить средствам записи профилировщика достаточно информации для распознавания скомпилированного метода для пользователей.

> [!NOTE]
> `functionId` нельзя использовать значения для разрешения их маркеров метаданных, так как динамические методы не имеют метаданных.

`pILHeader`Указатель допустим только во время обратного вызова.

## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Метод DynamicMethodJITCompilationFinished](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [Интерфейс ICorProfilerCallback8](icorprofilercallback8-interface.md)
