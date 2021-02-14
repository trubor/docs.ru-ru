---
title: Числовые типы с плавающей запятой — справочник по C#
description: 'Дополнительные сведения о встроенных типах C# с плавающей запятой: float, double и decimal'
ms.date: 02/04/2021
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: a086e8de60bbb63408c3f2cd557feb36c4baa0f8
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585758"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="0ac4e-103">Числовые типы с плавающей запятой (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="0ac4e-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="0ac4e-104">*Числовые типы с плавающей запятой* представляют действительные числа.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="0ac4e-105">Все числовые типы с плавающей запятой являются [типами значений](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="0ac4e-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="0ac4e-106">Они также представляют собой [простые типы](value-types.md#built-in-value-types) и могут быть инициализированы [литералами](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="0ac4e-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="0ac4e-107">Все числовые типы с плавающей запятой поддерживают [арифметические](../operators/arithmetic-operators.md) операторы, а также операторы [сравнения](../operators/comparison-operators.md) и [равенства](../operators/equality-operators.md).</span><span class="sxs-lookup"><span data-stu-id="0ac4e-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="0ac4e-108">Характеристики типов с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="0ac4e-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="0ac4e-109">C# поддерживает следующие предварительно определенные типы с плавающей запятой:</span><span class="sxs-lookup"><span data-stu-id="0ac4e-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="0ac4e-110">Ключевое слово или тип C#</span><span class="sxs-lookup"><span data-stu-id="0ac4e-110">C# type/keyword</span></span>|<span data-ttu-id="0ac4e-111">Приблизительный диапазон значений</span><span class="sxs-lookup"><span data-stu-id="0ac4e-111">Approximate range</span></span>|<span data-ttu-id="0ac4e-112">Точность</span><span class="sxs-lookup"><span data-stu-id="0ac4e-112">Precision</span></span>|<span data-ttu-id="0ac4e-113">Размер</span><span class="sxs-lookup"><span data-stu-id="0ac4e-113">Size</span></span>|<span data-ttu-id="0ac4e-114">Тип .NET</span><span class="sxs-lookup"><span data-stu-id="0ac4e-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="0ac4e-115">От ±1,5 x 10<sup>−45</sup> до ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="0ac4e-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="0ac4e-116">6–9 цифр</span><span class="sxs-lookup"><span data-stu-id="0ac4e-116">~6-9 digits</span></span>|<span data-ttu-id="0ac4e-117">4 байта</span><span class="sxs-lookup"><span data-stu-id="0ac4e-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="0ac4e-118">от ±5,0 × 10<sup>−324</sup> до ±1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="0ac4e-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="0ac4e-119">15–17 цифр</span><span class="sxs-lookup"><span data-stu-id="0ac4e-119">~15-17 digits</span></span>|<span data-ttu-id="0ac4e-120">8 байт</span><span class="sxs-lookup"><span data-stu-id="0ac4e-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="0ac4e-121">от ±1,0 x 10<sup>-28</sup> до ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="0ac4e-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="0ac4e-122">28-29 знаков</span><span class="sxs-lookup"><span data-stu-id="0ac4e-122">28-29 digits</span></span>|<span data-ttu-id="0ac4e-123">16 байт</span><span class="sxs-lookup"><span data-stu-id="0ac4e-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="0ac4e-124">В приведенной выше таблице каждый тип ключевого слова C# из крайнего левого столбца является псевдонимом для соответствующего типа .NET.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="0ac4e-125">Они взаимозаменяемые.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-125">They are interchangeable.</span></span> <span data-ttu-id="0ac4e-126">Например, следующие объявления объявляют переменные одного типа:</span><span class="sxs-lookup"><span data-stu-id="0ac4e-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="0ac4e-127">По умолчанию все типы с плавающей запятой имеют значение `0`.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="0ac4e-128">Все типы с плавающей запятой имеют константы `MinValue` и `MaxValue` с минимальным и максимальными итоговыми значениями этого типа.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="0ac4e-129">Типы `float` и `double` также предоставляют константы, обозначающие бесконечные и нечисловые значения.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="0ac4e-130">Например, тип `double` предоставляет следующие константы: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> и <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0ac4e-131">Тип `decimal` подходит, если требуемая степень точности определяется числом цифр справа от десятичной запятой.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-131">The `decimal` type is appropriate when the required degree of precision is determined by the number of digits to the right of the decimal point.</span></span> <span data-ttu-id="0ac4e-132">Такие числа обычно используются в финансовых приложениях для денежных сумм (например, 1,00 долл. США), процентных ставок (например, 2,625 %) и т. д.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-132">Such numbers are commonly used in financial applications, for currency amounts (for example, $1.00), interest rates (for example, 2.625%), and so forth.</span></span> <span data-ttu-id="0ac4e-133">Даже числа, точные только до одной десятичной цифры, точнее обрабатываются типом `decimal`: 0,1, например, можно в точности представить экземпляром `decimal`. При этом не существует экземпляра `double` или `float`, который точно представляет 0,1.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-133">Even numbers that are precise to only one decimal digit are handled more accurately by the `decimal` type: 0.1, for example, can be exactly represented by a `decimal` instance, while there's no `double` or `float` instance that exactly represents 0.1.</span></span> <span data-ttu-id="0ac4e-134">Из-за этой разницы в числовых типах в арифметических вычислениях могут возникать непредвиденные ошибки округления при использовании `double` или `float` для десятичных данных.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-134">Because of this difference in numeric types, unexpected rounding errors can occur in arithmetic calculations when you use `double` or `float` for decimal data.</span></span> <span data-ttu-id="0ac4e-135">Вы можете использовать `double` вместо `decimal`, если оптимизация производительности важнее, чем обеспечение точности.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-135">You can use `double` instead of `decimal` when optimizing performance is more important than ensuring accuracy.</span></span> <span data-ttu-id="0ac4e-136">Но любая разница в производительности останется незамеченной для всех приложений, кроме самых требовательных к вычислениям.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-136">However, any difference in performance would go unnoticed by all but the most calculation-intensive applications.</span></span> <span data-ttu-id="0ac4e-137">Еще одна возможная причина, по которой следует избегать `decimal`, — это минимальные требования к хранилищу.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-137">Another possible reason to avoid `decimal` is to minimize storage requirements.</span></span> <span data-ttu-id="0ac4e-138">Например, [ML.NET](../../../machine-learning/how-does-mldotnet-work.md) использует `float`, так как разница между 4 байтами и 16 байтами суммируется для очень больших наборов данных.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-138">For example, [ML.NET](../../../machine-learning/how-does-mldotnet-work.md) uses `float` because the difference between 4 bytes and 16 bytes adds up for very large data sets.</span></span> <span data-ttu-id="0ac4e-139">Для получения дополнительной информации см. <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-139">For more information, see <xref:System.Decimal?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0ac4e-140">В одном и том же выражении можно сочетать и [целочисленные](integral-numeric-types.md) типы, и типы `float` и `double`.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-140">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="0ac4e-141">В этом случае целочисленные типы неявно преобразуются в один из типов с плавающей запятой. При необходимости тип `float` неявно преобразуется в `double`.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-141">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="0ac4e-142">Выражение вычисляется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-142">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="0ac4e-143">Если в выражении есть тип `double`, оно оценивается как `double` или [`bool`](bool.md) в реляционных сравнениях или сравнениях на равенство.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-143">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="0ac4e-144">Если в выражении нет типа `double`, оно оценивается как `float` или `bool` в реляционных сравнениях или сравнениях на равенство.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-144">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="0ac4e-145">Можно также смешивать целочисленные типы и тип `decimal` в выражении.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-145">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="0ac4e-146">В этом случае целочисленные типы неявно преобразуются в тип `decimal`, а выражение вычисляется как `decimal` или `bool` в реляционных сравнениях и сравнениях на равенство.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-146">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="0ac4e-147">Тип `decimal` нельзя смешивать с типами `float` и `double` в выражении.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-147">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="0ac4e-148">В этом случае, если требуется выполнить арифметические операции или операции сравнения или равенства, необходимо явно преобразовать операнды из типа или в тип `decimal`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="0ac4e-148">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="0ac4e-149">Можно использовать [строки стандартных числовых форматов](../../../standard/base-types/standard-numeric-format-strings.md) или [строки пользовательских числовых форматов](../../../standard/base-types/custom-numeric-format-strings.md) для форматирования значения с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-149">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="0ac4e-150">Вещественные литералы</span><span class="sxs-lookup"><span data-stu-id="0ac4e-150">Real literals</span></span>

<span data-ttu-id="0ac4e-151">Тип реального литерала определяется его суффиксом следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0ac4e-151">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="0ac4e-152">Литерал без суффикса или с суффиксом `d` или `D` имеет тип `double`.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-152">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="0ac4e-153">Литерал с суффиксом `f` или `F` имеет тип `float`.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-153">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="0ac4e-154">Литерал с суффиксом `m` или `M` имеет тип `decimal`.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-154">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="0ac4e-155">В приведенном ниже коде показан пример каждого из них.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-155">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="0ac4e-156">В предыдущем примере также показано использование `_` в качестве *цифрового разделителя*, который поддерживается, начиная с версии C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-156">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="0ac4e-157">Цифровой разделитель можно использовать со всеми видами числовых литералов.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-157">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="0ac4e-158">Можно также использовать экспоненциальное представление, то есть указать экспоненту вещественного литерала, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="0ac4e-158">You can also use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="0ac4e-159">Преобразования</span><span class="sxs-lookup"><span data-stu-id="0ac4e-159">Conversions</span></span>

<span data-ttu-id="0ac4e-160">Существует только одно неявное преобразование между числовыми типами с плавающей запятой: из `float` в `double`.</span><span class="sxs-lookup"><span data-stu-id="0ac4e-160">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="0ac4e-161">Однако можно преобразовать любой тип с плавающей запятой в любой другой тип с плавающей запятой с помощью[явного приведения](../operators/type-testing-and-cast.md#cast-expression).</span><span class="sxs-lookup"><span data-stu-id="0ac4e-161">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="0ac4e-162">Для получения дополнительной информации см. статью [Встроенные числовые преобразования](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="0ac4e-162">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0ac4e-163">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="0ac4e-163">C# language specification</span></span>

<span data-ttu-id="0ac4e-164">Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="0ac4e-164">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="0ac4e-165">Типы с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="0ac4e-165">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- <span data-ttu-id="0ac4e-166">Тип [decimal](~/_csharplang/spec/types.md#the-decimal-type)</span><span class="sxs-lookup"><span data-stu-id="0ac4e-166">[The decimal type](~/_csharplang/spec/types.md#the-decimal-type)</span></span>
- [<span data-ttu-id="0ac4e-167">Вещественные литералы</span><span class="sxs-lookup"><span data-stu-id="0ac4e-167">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="0ac4e-168">См. также</span><span class="sxs-lookup"><span data-stu-id="0ac4e-168">See also</span></span>

- [<span data-ttu-id="0ac4e-169">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="0ac4e-169">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0ac4e-170">Типы значений</span><span class="sxs-lookup"><span data-stu-id="0ac4e-170">Value types</span></span>](value-types.md)
- [<span data-ttu-id="0ac4e-171">Целочисленные типы</span><span class="sxs-lookup"><span data-stu-id="0ac4e-171">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="0ac4e-172">Строки стандартных числовых форматов</span><span class="sxs-lookup"><span data-stu-id="0ac4e-172">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="0ac4e-173">Числовые значения в .NET</span><span class="sxs-lookup"><span data-stu-id="0ac4e-173">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
