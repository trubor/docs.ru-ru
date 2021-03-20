---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Комклассиквтаблекреатед'
title: Метод ICorProfilerCallback::COMClassicVTableCreated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type:
- apiref
ms.openlocfilehash: 04ba37b9c1307539c9fdf299f4667e7026d571be
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760578"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a>Метод ICorProfilerCallback::COMClassicVTableCreated

Уведомляет профилировщик о том, что для указанного IID и класса был создан объект vtable COM-взаимодействия.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a>Параметры

`wrappedClasId` окне Идентификатор класса, для которого была создана таблица vtable.

`implementedIID` окне Идентификатор интерфейса, реализуемого классом. Это значение может быть равно NULL, если интерфейс является только внутренним.

`pVTable` окне Указатель на начало таблицы vtable.

`cSlots` окне Число слотов в таблице vtable.

## <a name="remarks"></a>Remarks  

 Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора. Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.  
  
 Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
- [Метод COMClassicVTableDestroyed](icorprofilercallback-comclassicvtabledestroyed-method.md)
