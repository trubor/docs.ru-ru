---
title: Справочник по C#. Целочисленные типы
description: Сведения о диапазоне значений, размере занимаемой памяти и способах использования каждого из целочисленных типов.
ms.date: 04/10/2021
f1_keywords:
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- short_CSharpKeyword
- ushort_CSharpKeyword
- int_CSharpKeyword
- uint_CSharpKeyword
- long_CSharpKeyword
- ulong_CSharpKeyword
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 21e6595e477fd48d0e5f39f5b4f1f7c5893a8840
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369586"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="d9c77-103">Целочисленные типы (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="d9c77-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="d9c77-104">*Целочисленные типы* представляют целые числа.</span><span class="sxs-lookup"><span data-stu-id="d9c77-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="d9c77-105">Все целочисленные типы являются [типами значений](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="d9c77-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="d9c77-106">Они также представляют собой [простые типы](value-types.md#built-in-value-types) и могут быть инициализированы [литералами](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="d9c77-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="d9c77-107">Все целочисленные типы поддерживают [арифметические](../operators/arithmetic-operators.md) операторы, [побитовые логические](../operators/bitwise-and-shift-operators.md) операторы, операторы [сравнения](../operators/comparison-operators.md) и [равенства](../operators/equality-operators.md).</span><span class="sxs-lookup"><span data-stu-id="d9c77-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="d9c77-108">Характеристики целочисленных типов</span><span class="sxs-lookup"><span data-stu-id="d9c77-108">Characteristics of the integral types</span></span>

<span data-ttu-id="d9c77-109">C# поддерживает следующие предварительно определенные целочисленные типы:</span><span class="sxs-lookup"><span data-stu-id="d9c77-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="d9c77-110">Ключевое слово или тип C#</span><span class="sxs-lookup"><span data-stu-id="d9c77-110">C# type/keyword</span></span>|<span data-ttu-id="d9c77-111">Диапазон</span><span class="sxs-lookup"><span data-stu-id="d9c77-111">Range</span></span>|<span data-ttu-id="d9c77-112">Размер</span><span class="sxs-lookup"><span data-stu-id="d9c77-112">Size</span></span>|<span data-ttu-id="d9c77-113">Тип .NET</span><span class="sxs-lookup"><span data-stu-id="d9c77-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="d9c77-114">От -128 до 127</span><span class="sxs-lookup"><span data-stu-id="d9c77-114">-128 to 127</span></span>|<span data-ttu-id="d9c77-115">8-разрядное целое число со знаком</span><span class="sxs-lookup"><span data-stu-id="d9c77-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="d9c77-116">От 0 до 255</span><span class="sxs-lookup"><span data-stu-id="d9c77-116">0 to 255</span></span>|<span data-ttu-id="d9c77-117">8-разрядное целое число без знака</span><span class="sxs-lookup"><span data-stu-id="d9c77-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="d9c77-118">От -32 768 до 32 767</span><span class="sxs-lookup"><span data-stu-id="d9c77-118">-32,768 to 32,767</span></span>|<span data-ttu-id="d9c77-119">16-разрядное целое число со знаком</span><span class="sxs-lookup"><span data-stu-id="d9c77-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="d9c77-120">От 0 до 65 535</span><span class="sxs-lookup"><span data-stu-id="d9c77-120">0 to 65,535</span></span>|<span data-ttu-id="d9c77-121">16-разрядное целое число без знака</span><span class="sxs-lookup"><span data-stu-id="d9c77-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="d9c77-122">От -2 147 483 648 до 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="d9c77-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="d9c77-123">32-разрядное целое число со знаком</span><span class="sxs-lookup"><span data-stu-id="d9c77-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="d9c77-124">От 0 до 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="d9c77-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="d9c77-125">32-разрядное целое число без знака</span><span class="sxs-lookup"><span data-stu-id="d9c77-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="d9c77-126">От -9 223 372 036 854 775 808 до 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="d9c77-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="d9c77-127">64-разрядное целое число со знаком</span><span class="sxs-lookup"><span data-stu-id="d9c77-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="d9c77-128">От 0 до 18 446 744 073 709 551 615</span><span class="sxs-lookup"><span data-stu-id="d9c77-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="d9c77-129">64-разрядное целое число без знака</span><span class="sxs-lookup"><span data-stu-id="d9c77-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|`nint`|<span data-ttu-id="d9c77-130">Зависит от платформы</span><span class="sxs-lookup"><span data-stu-id="d9c77-130">Depends on platform</span></span>|<span data-ttu-id="d9c77-131">32- или 64-разрядное целое число со знаком</span><span class="sxs-lookup"><span data-stu-id="d9c77-131">Signed 32-bit or 64-bit integer</span></span>|<xref:System.IntPtr?displayProperty=nameWithType>|
|`nuint`|<span data-ttu-id="d9c77-132">Зависит от платформы</span><span class="sxs-lookup"><span data-stu-id="d9c77-132">Depends on platform</span></span>|<span data-ttu-id="d9c77-133">32- или 64-разрядное целое число без знака</span><span class="sxs-lookup"><span data-stu-id="d9c77-133">Unsigned 32-bit or 64-bit integer</span></span>|<xref:System.UIntPtr?displayProperty=nameWithType>|

<span data-ttu-id="d9c77-134">Во всех строках таблицы, кроме двух последних, каждое ключевое слово типа C# из крайнего левого столбца является псевдонимом для соответствующего типа .NET.</span><span class="sxs-lookup"><span data-stu-id="d9c77-134">In all of the table rows except the last two, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="d9c77-135">Ключевое слово и имя типа .NET являются взаимозаменяемыми.</span><span class="sxs-lookup"><span data-stu-id="d9c77-135">The keyword and .NET type name are interchangeable.</span></span> <span data-ttu-id="d9c77-136">Например, следующие объявления объявляют переменные одного типа:</span><span class="sxs-lookup"><span data-stu-id="d9c77-136">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="d9c77-137">Типы `nint` и `nuint` в последних двух строках таблицы являются целыми числами собственного размера.</span><span class="sxs-lookup"><span data-stu-id="d9c77-137">The `nint` and `nuint` types in the last two rows of the table are native-sized integers.</span></span> <span data-ttu-id="d9c77-138">В коде такие числа представлены определенными типами .NET, но в каждом случае ключевое слово и тип .NET не взаимозаменяемы.</span><span class="sxs-lookup"><span data-stu-id="d9c77-138">They are represented internally by the indicated .NET types, but in each case the keyword and the .NET type are not interchangeable.</span></span> <span data-ttu-id="d9c77-139">Для `nint` и `nuint` компилятор предоставляет преобразования и операции, как для целочисленных типов. Они отличаются от преобразований и операций для типов указателей `System.IntPtr` и `System.UIntPtr`.</span><span class="sxs-lookup"><span data-stu-id="d9c77-139">The compiler provides operations and conversions for `nint` and `nuint` as integer types that it doesn't provide for the pointer types `System.IntPtr` and `System.UIntPtr`.</span></span> <span data-ttu-id="d9c77-140">Дополнительные сведения см. в статье о [типах `nint` и `nuint`](nint-nuint.md).</span><span class="sxs-lookup"><span data-stu-id="d9c77-140">For more information, see [`nint` and `nuint` types](nint-nuint.md).</span></span>

<span data-ttu-id="d9c77-141">По умолчанию все целочисленные типы имеют значение `0`.</span><span class="sxs-lookup"><span data-stu-id="d9c77-141">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="d9c77-142">Все целочисленные типы, кроме целых чисел собственного размера, имеют константы `MinValue` и `MaxValue` с минимальным и максимальным значением этого типа.</span><span class="sxs-lookup"><span data-stu-id="d9c77-142">Each of the integral types except the native-sized types has `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="d9c77-143">Используйте структуру <xref:System.Numerics.BigInteger?displayProperty=nameWithType>, чтобы представить целое число со знаком без верхней и нижней границ.</span><span class="sxs-lookup"><span data-stu-id="d9c77-143">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="d9c77-144">Целочисленные литералы</span><span class="sxs-lookup"><span data-stu-id="d9c77-144">Integer literals</span></span>

<span data-ttu-id="d9c77-145">Целочисленные литералы могут быть:</span><span class="sxs-lookup"><span data-stu-id="d9c77-145">Integer literals can be</span></span>

- <span data-ttu-id="d9c77-146">*десятичным числом*: без префикса;</span><span class="sxs-lookup"><span data-stu-id="d9c77-146">*decimal*: without any prefix</span></span>
- <span data-ttu-id="d9c77-147">*шестнадцатеричным числом*: с префиксом `0x` или `0X`;</span><span class="sxs-lookup"><span data-stu-id="d9c77-147">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="d9c77-148">*двоичными*: с префиксом `0b` или `0B` (доступно в C# 7.0 и более поздних версиях).</span><span class="sxs-lookup"><span data-stu-id="d9c77-148">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="d9c77-149">В приведенном ниже коде показан пример каждого из них.</span><span class="sxs-lookup"><span data-stu-id="d9c77-149">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="d9c77-150">В предыдущем примере также показано использование `_` в качестве *цифрового разделителя*, который поддерживается, начиная с версии C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="d9c77-150">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="d9c77-151">Цифровой разделитель можно использовать со всеми видами числовых литералов.</span><span class="sxs-lookup"><span data-stu-id="d9c77-151">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="d9c77-152">Тип целочисленного литерала определяется его суффиксом следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d9c77-152">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="d9c77-153">Если литерал не имеет суффикса, его типом будет первый из следующих типов, в котором может быть представлено его значение: `int`, `uint`, `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="d9c77-153">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d9c77-154">Литералы интерпретируется как положительные значения.</span><span class="sxs-lookup"><span data-stu-id="d9c77-154">Literals are interpreted as positive values.</span></span> <span data-ttu-id="d9c77-155">Например, литерал `0xFF_FF_FF_FF` представляет число `4294967295` типа `uint`, хотя он имеет то же битовое представление, что и число `-1` типа `int`.</span><span class="sxs-lookup"><span data-stu-id="d9c77-155">For example, the literal `0xFF_FF_FF_FF` represents the number `4294967295` of the `uint` type, though it has the same bit representation as the number `-1` of the `int` type.</span></span> <span data-ttu-id="d9c77-156">Если вам требуется значение определенного типа, приведите литерал к этому типу.</span><span class="sxs-lookup"><span data-stu-id="d9c77-156">If you need a value of a certain type, cast a literal to that type.</span></span> <span data-ttu-id="d9c77-157">Используйте оператор `unchecked`, если представить значение литерала в целевом типе невозможно.</span><span class="sxs-lookup"><span data-stu-id="d9c77-157">Use the `unchecked` operator, if a literal value cannot be represented in the target type.</span></span> <span data-ttu-id="d9c77-158">Например, `unchecked((int)0xFF_FF_FF_FF)` выдает `-1`.</span><span class="sxs-lookup"><span data-stu-id="d9c77-158">For example, `unchecked((int)0xFF_FF_FF_FF)` produces `-1`.</span></span>

- <span data-ttu-id="d9c77-159">Если у литерала есть суффикс `U` или `u`, его типом будет первый из следующих типов, в котором может быть представлено его значение: `uint`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="d9c77-159">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="d9c77-160">Если у литерала есть суффикс `L` или `l`, его типом будет первый из следующих типов, в котором может быть представлено его значение: `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="d9c77-160">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d9c77-161">Строчную букву `l` можно использовать в качестве суффикса.</span><span class="sxs-lookup"><span data-stu-id="d9c77-161">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="d9c77-162">Однако при этом выдается предупреждение компилятора, так как букву `l` можно перепутать с цифрой `1`.</span><span class="sxs-lookup"><span data-stu-id="d9c77-162">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="d9c77-163">Для ясности используйте `L`.</span><span class="sxs-lookup"><span data-stu-id="d9c77-163">Use `L` for clarity.</span></span>

- <span data-ttu-id="d9c77-164">Если у литерала есть суффикс `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU` или `lu`, его тип — `ulong`.</span><span class="sxs-lookup"><span data-stu-id="d9c77-164">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="d9c77-165">Если значение, представленное целочисленным литералом, превышает <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, происходит ошибка компиляции [CS1021](../../misc/cs1021.md).</span><span class="sxs-lookup"><span data-stu-id="d9c77-165">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="d9c77-166">Если определенный тип целочисленного литерала — `int`, а значение, представленное литералом, находится в диапазоне целевого типа, значение можно неявно преобразовать в `sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, `nint` или `nuint`:</span><span class="sxs-lookup"><span data-stu-id="d9c77-166">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, `nint` or `nuint`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="d9c77-167">Как показано в предыдущем примере, если значение литерала выходит за пределы диапазона целевого типа, возникает ошибка компилятора [CS0031](../../misc/cs0031.md).</span><span class="sxs-lookup"><span data-stu-id="d9c77-167">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="d9c77-168">Можно также использовать приведение для преобразования значения, представленного целочисленным литералом, в тип, отличный от определенного типа литерала:</span><span class="sxs-lookup"><span data-stu-id="d9c77-168">You can also use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="d9c77-169">Преобразования</span><span class="sxs-lookup"><span data-stu-id="d9c77-169">Conversions</span></span>

<span data-ttu-id="d9c77-170">Любой целочисленный тип можно преобразовать в любой другой целочисленный тип.</span><span class="sxs-lookup"><span data-stu-id="d9c77-170">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="d9c77-171">Если целевой тип может хранить все значения исходного типа, преобразование является неявным.</span><span class="sxs-lookup"><span data-stu-id="d9c77-171">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="d9c77-172">В противном случае необходимо использовать [выражение приведения](../operators/type-testing-and-cast.md#cast-expression) для выполнения явного преобразования.</span><span class="sxs-lookup"><span data-stu-id="d9c77-172">Otherwise, you need to use a [cast expression](../operators/type-testing-and-cast.md#cast-expression) to perform an explicit conversion.</span></span> <span data-ttu-id="d9c77-173">Для получения дополнительной информации см. статью [Встроенные числовые преобразования](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="d9c77-173">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d9c77-174">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="d9c77-174">C# language specification</span></span>

<span data-ttu-id="d9c77-175">Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="d9c77-175">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d9c77-176">Целочисленные типы</span><span class="sxs-lookup"><span data-stu-id="d9c77-176">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="d9c77-177">Целочисленные литералы</span><span class="sxs-lookup"><span data-stu-id="d9c77-177">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="d9c77-178">См. также</span><span class="sxs-lookup"><span data-stu-id="d9c77-178">See also</span></span>

- [<span data-ttu-id="d9c77-179">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="d9c77-179">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d9c77-180">Типы значений</span><span class="sxs-lookup"><span data-stu-id="d9c77-180">Value types</span></span>](value-types.md)
- [<span data-ttu-id="d9c77-181">Типы с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="d9c77-181">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="d9c77-182">Строки стандартных числовых форматов</span><span class="sxs-lookup"><span data-stu-id="d9c77-182">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="d9c77-183">Числовые значения в .NET</span><span class="sxs-lookup"><span data-stu-id="d9c77-183">Numerics in .NET</span></span>](../../../standard/numerics.md)
