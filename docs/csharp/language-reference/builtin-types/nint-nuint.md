---
description: Сведения о встроенных типах nint и nuint в C#
title: Справочник по C#. Типы nint и nuint
ms.date: 03/15/2021
f1_keywords:
- nint_CSharpKeyword
- nuint_CSharpKeyword
helpviewer_keywords:
- nint data type [C#]
- nuint data type [C#]
ms.openlocfilehash: fc779731d7f67fd0239f095d1dd17217a56622f6
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760826"
---
# <a name="nint-and-nuint-types-c-reference"></a>Типы `nint` и `nuint` (справочник по C#)

Начиная с C# 9.0, вы можете использовать ключевые слова `nint` и `nuint` для определения *целых чисел собственного размера*. Эти целые числа будут 32-разрядными при использовании в 32-битных процессах и 64-разрядными при использовании в 64-битных процессах. Их можно использовать для сценариев взаимодействия, с низкоуровневыми библиотеками и для оптимизации производительности в сценариях, где часто выполняются математические операции с целыми числами.

Целочисленные типы собственного размера представляются внутренне как типы .NET <xref:System.IntPtr?displayProperty=nameWithType> и <xref:System.UIntPtr?displayProperty=nameWithType>. В отличие от других числовых типов, эти ключевые слова — не просто псевдонимы для типов. Следующие инструкции не являются эквивалентными:

```csharp
nint a = 1;
System.IntPtr a = 1;
```

Для `nint` и `nuint` компилятор предоставляет такие же преобразования и операции, как для всех целочисленных типов.

## <a name="run-time-native-integer-size"></a>Собственный размер целого числа во время выполнения

Чтобы узнать размер целого числа собственного размера во время выполнения, используйте `sizeof()`. Но код должен компилироваться в контексте unsafe. Пример:

:::code language="csharp" source="snippets/shared/NativeIntegerTypes.cs" id="SizeOf":::

Такое же значение можно получить с помощью статических свойств <xref:System.IntPtr.Size?displayProperty=nameWithType> и <xref:System.UIntPtr.Size?displayProperty=nameWithType>.

## <a name="minvalue-and-maxvalue"></a>MinValue и MaxValue

Чтобы получить минимальное и максимальное значения целых чисел собственного размера во время выполнения, используйте `MinValue` и `MaxValue` в качестве статических свойств с ключевыми словами `nint` и `nuint`, как показано в следующем примере:

:::code language="csharp" source="snippets/shared/NativeIntegerTypes.cs" id="MinMax":::

## <a name="constants"></a>Константы

Значения констант можно использовать в таких диапазонах:

* для `nint`: <xref:System.Int32.MinValue?displayProperty=nameWithType>–<xref:System.Int32.MaxValue?displayProperty=nameWithType>;
* для `nuint`: <xref:System.UInt32.MinValue?displayProperty=nameWithType>–<xref:System.UInt32.MaxValue?displayProperty=nameWithType>.

## <a name="conversions"></a>Преобразования

Компилятор предоставляет неявные и явные преобразования в другие числовые типы. Для получения дополнительной информации см. статью [Встроенные числовые преобразования](numeric-conversions.md).

## <a name="literals"></a>Литералы

Для целочисленных литералов собственного размера не поддерживается прямой синтаксис. Суффикса, указывающего на то, что литерал является целым числом собственного размера (например, `L` для обозначения `long`), нет. Вместо этого можно использовать явные или неявные приведения других целочисленных значений. Пример:

```csharp
nint a = 42
nint a = (nint)42;
```

## <a name="unsupported-intptruintptr-members"></a>Неподдерживаемые элементы IntPtr и UIntPtr

Следующие элементы структур <xref:System.IntPtr> и <xref:System.UIntPtr> не поддерживаются для типов `nint` и `nuint`:

* Параметризованные конструкторы.
* <xref:System.IntPtr.Add(System.IntPtr,System.Int32)>
* <xref:System.IntPtr.CompareTo%2A>
* <xref:System.IntPtr.Size>. Вместо этого используйте [sizeOf()](#run-time-native-integer-size). Хотя `nint.Size` не поддерживается, можно получить эквивалентное значение с помощью `IntPtr.Size`.
* <xref:System.IntPtr.Subtract(System.IntPtr,System.Int32)>
* <xref:System.IntPtr.ToInt32%2A>
* <xref:System.IntPtr.ToInt64%2A>
* <xref:System.IntPtr.ToPointer%2A>
* <xref:System.IntPtr.Zero>. Вместо этого используйте 0.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в статье о [спецификации языка C#](~/_csharplang/spec/introduction.md) и в статье [Целые числа собственного размера](~/_csharplang/proposals/csharp-9.0/native-integers.md) в предложениях по функциям C# 9.0.

## <a name="see-also"></a>См. также раздел

- [справочник по C#](../index.md)
- [Типы значений](value-types.md)
- [Целочисленные типы](integral-numeric-types.md)
- [Встроенные числовые преобразования](numeric-conversions.md)
