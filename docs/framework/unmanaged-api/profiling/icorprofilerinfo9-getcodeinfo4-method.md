---
description: 'Дополнительные сведения о методе: ICorProfilerInfo9:: GetCodeInfo4'
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: c7897e266fbb84d44df719c127e24bd375b560bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759095"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a>Метод ICorProfilerInfo9:: GetCodeInfo4

При наличии начального адреса машинного кода возвращает блоки виртуальной памяти, в которых хранится этот код.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a>Параметры

`pNativeCodeStartAddress` окне Указатель на начало собственной функции.

`cCodeInfos` окне Размер `codeInfos` массива.

`pcCodeInfos` заполняет Указатель на общее число доступных структур [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .

`codeInfos` заполняет Предоставленный вызывающим объектом буфер. После возврата метода он содержит массив структур `COR_PRF_CODE_INFO`, каждая из которых описывает блок машинного кода.

## <a name="remarks"></a>Remarks

`GetCodeInfo4`Метод аналогичен [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), за исключением того, что он может искать информацию о коде для различных версий метода.

> [!NOTE]
> `GetCodeInfo4` может запустить сборку мусора.

Расширения сортируются в порядке возрастания смещения общих промежуточного языка (CIL).

После `GetCodeInfo4` возврата необходимо убедиться, что `codeInfos` буфер достаточно велик, чтобы вместить все структуры [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) . Для этого сравните значение параметра `cCodeInfos` со значением параметра `cchName`. При `cCodeInfos` делении на размер структуры [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) меньше `pcCodeInfos` , выделяет буфер большего размера `codeInfos` , обновляет `cCodeInfos` новый, больший размер и вызывается `GetCodeInfo4` снова.

Кроме того, сначала можно вызвать метод `GetCodeInfo4` с буфером `codeInfos` нулевой длины для получения правильного размера буфера. Затем можно присвоить `codeInfos` Размер буфера значению, возвращенному в `pcCodeInfos` , умноженному на размер структуры [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) и вызывать `GetCodeInfo4` повторно.

## <a name="requirements"></a>Требования

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).

**Заголовок:** CorProf.idl, CorProf.h

**Библиотека:** CorGuids.lib

**Версии .NET:**[!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]

## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerInfo9](ICorProfilerInfo9-interface.md)
