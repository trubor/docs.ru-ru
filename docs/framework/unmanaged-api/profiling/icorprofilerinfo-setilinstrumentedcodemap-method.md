---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: Сетилинструментедкодемап'
title: Метод ICorProfilerInfo::SetILInstrumentedCodeMap
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: f9ed01b91f740a8bd95f4ad049076feb02363b8f
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760396"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>Метод ICorProfilerInfo::SetILInstrumentedCodeMap

Задает карту кода для указанной функции, используя указанные записи о сопоставлении языка MSIL.

> [!NOTE]
> В платформа .NET Framework версии 2,0 вызов `SetILInstrumentedCodeMap` для `FunctionID` , представляющий универсальную функцию в конкретном домене приложения, повлияет на все экземпляры этой функции в домене приложения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a>Параметры

`functionId` окне Идентификатор функции, для которой необходимо задать карту кода.

`fStartJit` окне Логическое значение, указывающее, является ли вызов `SetILInstrumentedCodeMap` метода первым для конкретного `FunctionID` . Задайте `fStartJit` для значение `true` в первом вызове `SetILInstrumentedCodeMap` для заданного `FunctionID` , а затем в `false` .

`cILMapEntries` окне Число элементов в `cILMapEntries` массиве.

`rgILMapEntries` окне Массив структур COR_IL_MAP, каждый из которых задает смещение MSIL.

## <a name="remarks"></a>Remarks

Профилировщик часто вставляет инструкции в исходном коде метода, чтобы инструментировать этот метод (например, уведомлять о достижении данной строки исходного кода). `SetILInstrumentedCodeMap` позволяет профилировщику сопоставлять исходные инструкции MSIL с их новыми расположениями. Профилировщик может использовать метод [ICorProfilerInfo:: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) , чтобы получить исходное смещение MSIL для заданного смещения в машинном коде.

Отладчик предполагает, что каждое старое смещение ссылается на смещение MSIL в исходном, неизмененном коде MSIL и что каждое новое смещение ссылается на смещение MSIL в новом, инструментированном коде. Карту следует сортировать в порядке возрастания. Чтобы пошаговое выполнение работало правильно, следуйте приведенным ниже рекомендациям.

- Не Переупорядочивайте инструментированный код MSIL.

- Не удаляйте исходный код MSIL.

- Включить записи для всех точек следования из файла базы данных программы (PDB) на карте. На карте не выполняется интерполяция отсутствующих записей. Итак, учитывая следующую карту:

  (0 старых, 0 новых)

  (5 старых, 10 новых)

  (9 старых, 20 новых)

  - Старое смещение 0, 1, 2, 3 или 4 будет сопоставлено с новым смещением 0.

  - Старое смещение 5, 6, 7 или 8 будет сопоставлено с новым смещением 10.

  - Старое смещение 9 или выше будет сопоставлено с новым смещением 20.

  - Новое смещение 0, 1, 2, 3, 4, 5, 6, 7, 8 или 9 будет сопоставлено со старым смещением 0.

  - Новое смещение, равное 10, 11, 12, 13, 14, 15, 16, 17, 18 или 19, будет сопоставлено со старым смещением 5.

  - Новое смещение, равное 20 или выше, будет сопоставлено старому смещению 9.

В платформа .NET Framework 3,5 и предыдущих версиях вы выделяете `rgILMapEntries` массив путем вызова метода [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) . Поскольку среда выполнения получает владение этой памятью, профилировщик не должен пытаться освободить его.

## <a name="requirements"></a>Требования

**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).

**Заголовок:** CorProf.idl, CorProf.h

**Библиотека:** CorGuids.lib

**Платформа .NET Framework версии:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerInfo](icorprofilerinfo-interface.md)
