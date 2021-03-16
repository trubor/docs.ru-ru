---
title: Значения по умолчанию типов C# — справка по C#
description: Ознакомьтесь со значениями по умолчанию таких типов C#, как bool, char, int, float, double и др.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 72d6249ed56ae6ae34a6f51102e1e7bbd3f64ab7
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104119"
---
# <a name="default-values-of-c-types-c-reference"></a>Значения по умолчанию типов C# (справка по C#)

В следующей таблице показаны значения по умолчанию для типов C#:

|Type|Значение по умолчанию|
|---------|------------------|
|Любой [ссылочный тип](../keywords/reference-types.md)|`null`|
|Любой [встроенный целочисленный тип](integral-numeric-types.md)|Ноль (0)|
|Любой [встроенный тип с плавающей запятой](floating-point-numeric-types.md)|Ноль (0)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'` (U+0000)|
|[enum](enum.md)|Значение, создаваемое выражением `(E)0`, где `E` — это идентификатор перечисления.|
|[struct](struct.md)|Значение, создаваемое путем установки значений по умолчанию для всех полей с типами значений и значений `null` для всех полей ссылочного типа.|
|Любой [тип значения, допускающий значение NULL](nullable-value-types.md)|Экземпляр, свойство `false` которого имеет значение <xref:System.Nullable%601.HasValue%2A>, а свойство <xref:System.Nullable%601.Value%2A> не определено. Это значение по умолчанию также называется значением *NULL* типа значения, допускающего значение NULL.|

Используйте [оператор `default`](../operators/default.md#default-operator), чтобы получить значение по умолчанию для типа, как показано в следующем примере:

```csharp
int a = default(int);
```

Начиная с C# 7.1 вы можете использовать литерал [`default`](../operators/default.md#default-literal) для инициализации переменной со значением по умолчанию для ее типа:

```csharp
int a = default;
```

Для типа значения неявный конструктор без параметров также создает значение по умолчанию для типа, как показано в следующем примере:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

Если экземпляр <xref:System.Type?displayProperty=nameWithType> представляет тип значения, во время выполнения можно использовать метод <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType>, чтобы вызвать конструктор без параметров и получить значение типа по умолчанию.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):

- [Значения по умолчанию](~/_csharplang/spec/variables.md#default-values)
- [Конструкторы по умолчанию](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Конструкторы](../../programming-guide/classes-and-structs/constructors.md)
