---
title: Критическое изменение. Vector<T> создает исключение NotSupportedException
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где Vector<T> всегда вызывает исключение для неподдерживаемых параметров типа.
ms.date: 11/01/2020
ms.openlocfilehash: dccd39c01f4debd7d1432195e7f3cb14aeda5f65
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257015"
---
# <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a>Vector\<T> всегда вызывает исключение NotSupportedException для неподдерживаемых типов

<xref:System.Numerics.Vector%601?displayProperty=nameWithType> теперь всегда вызывает <xref:System.NotSupportedException> для неподдерживаемых параметров типа.

## <a name="change-description"></a>Описание изменений

Ранее члены <xref:System.Numerics.Vector%601> не всегда вызывали <xref:System.NotSupportedException>, если у `T` был [неподдерживаемый тип](#unsupported-types). Исключение не всегда вызывалось из-за путей к коду, поддерживающих аппаратное ускорение. Например, для `Vector<bool> + Vector<bool>` возвращалось `default` вместо вызова исключения на платформах без аппаратного ускорения, например ARM32. Для неподдерживаемых типов члены <xref:System.Numerics.Vector%601> демонстрируют несогласованное поведение на разных платформах и с разными конфигурациями оборудования.

Начиная с .NET 5, члены <xref:System.Numerics.Vector%601> всегда вызывают <xref:System.NotSupportedException> во всех конфигурациях оборудования, если `T` не является поддерживаемым типом.

### <a name="unsupported-types"></a>Неподдерживаемые типы

Поддерживаемые типы для параметра типа <xref:System.Numerics.Vector%601>:

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

Поддерживаемые типы не изменились, но могут измениться в будущем.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

Не используйте неподдерживаемый тип для параметра типа <xref:System.Numerics.Vector%601>.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Numerics.Vector%601?displayProperty=fullName> и все связанные члены

<!--

#### Category

Core .NET libraries

### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
