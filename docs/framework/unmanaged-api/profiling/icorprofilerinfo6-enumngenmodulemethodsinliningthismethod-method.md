---
description: 'Дополнительные сведения о методе: ICorProfilerInfo6:: Енумнженмодулемесодсинлинингсисмесод'
title: Метод ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 236aaa820162dcc1d5c6c8ade1e8da78f5f4acb0
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759134"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>Метод ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod

Возвращает перечислитель для всех методов, определенных в заданном модуле NGen, и встроенный метод.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a>Параметры

`inlinersModuleId` окне Идентификатор модуля NGen.

`inlineeModuleId` окне Идентификатор модуля, который определяет `inlineeMethodId` . Дополнительные сведения см. в разделе "Примечания".

`inlineeMethodId` окне Идентификатор встроенного метода. Дополнительные сведения см. в разделе "Примечания".

`incompleteData` заполняет Флаг, указывающий, `ppEnum` содержит ли все методы выравнивание данного метода.  Дополнительные сведения см. в разделе "Примечания".

`ppEnum` заполняет Указатель на адрес перечислителя

## <a name="remarks"></a>Remarks

`inlineeModuleId``inlineeMethodId`вместе образуют полный идентификатор для метода, который может быть встроенным. Например, пусть модуль `A` определяет метод `Simple.Add` :

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

а модуль B определяет `Fancy.AddTwice` :

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

Также можно предположить, что `Fancy.AddTwice` встроенный вызов `SimpleAdd` . Профилировщик может использовать этот перечислитель для поиска всех методов, определенных в модуле B, которые являются встроенными `Simple.Add` , и результат будет перечисляться `AddTwice` .  `inlineeModuleId` Идентификатор модуля `A` , а `inlineeMethodId` — идентификатор `Simple.Add(int a, int b)` .

Если `incompleteData` параметр имеет значение true после возвращения функции, перечислитель не содержит всех методов, выставляемых в данном методе. Это может произойти, если одна или несколько непосредственных или косвенных зависимостей модуля "вкладыши" еще не загружены. Если профилировщику требуются точные данные, необходимо повторить попытку позже, когда загрузится больше модулей, лучше при каждой загрузке модуля.

`EnumNgenModuleMethodsInliningThisMethod`Метод можно использовать для обхода ограничений встраивания для ReJIT. ReJIT позволяет профилировщику изменить реализацию метода, а затем создать новый код для него в режиме реального времени. Например, можно изменить следующим образом `Simple.Add` :

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

Тем не менее `Fancy.AddTwice` , поскольку уже встроено `Simple.Add` , он по-разному будет иметь такое же поведение, как и раньше. Чтобы обойти это ограничение, вызывающий должен найти все методы во всех модулях, которые встроены `Simple.Add` и используются `ICorProfilerInfo5::RequestRejit` в каждом из этих методов. При повторной компиляции методов они будут иметь новое поведение, `Simple.Add` а не старое поведение.

## <a name="requirements"></a>Требования

**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).

**Заголовок:** CorProf.idl, CorProf.h

**Библиотека:** CorGuids.lib

**Платформа .NET Framework версии:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]

## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerInfo6](icorprofilerinfo6-interface.md)
