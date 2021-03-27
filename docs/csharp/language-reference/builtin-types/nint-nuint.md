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
# <a name="nint-and-nuint-types-c-reference"></a><span data-ttu-id="f384f-103">Типы `nint` и `nuint` (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="f384f-103">`nint` and `nuint` types (C# reference)</span></span>

<span data-ttu-id="f384f-104">Начиная с C# 9.0, вы можете использовать ключевые слова `nint` и `nuint` для определения *целых чисел собственного размера*.</span><span class="sxs-lookup"><span data-stu-id="f384f-104">Starting in C# 9.0, you can use the `nint` and `nuint` keywords to define *native-sized integers*.</span></span> <span data-ttu-id="f384f-105">Эти целые числа будут 32-разрядными при использовании в 32-битных процессах и 64-разрядными при использовании в 64-битных процессах.</span><span class="sxs-lookup"><span data-stu-id="f384f-105">These are 32-bit integers when running in a 32-bit process, or 64-bit integers when running in a 64-bit process.</span></span> <span data-ttu-id="f384f-106">Их можно использовать для сценариев взаимодействия, с низкоуровневыми библиотеками и для оптимизации производительности в сценариях, где часто выполняются математические операции с целыми числами.</span><span class="sxs-lookup"><span data-stu-id="f384f-106">They can be used for interop scenarios, low-level libraries, and to optimize performance in scenarios where integer math is used extensively.</span></span>

<span data-ttu-id="f384f-107">Целочисленные типы собственного размера представляются внутренне как типы .NET <xref:System.IntPtr?displayProperty=nameWithType> и <xref:System.UIntPtr?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f384f-107">The native-sized integer types are represented internally as the .NET types <xref:System.IntPtr?displayProperty=nameWithType> and <xref:System.UIntPtr?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f384f-108">В отличие от других числовых типов, эти ключевые слова — не просто псевдонимы для типов.</span><span class="sxs-lookup"><span data-stu-id="f384f-108">Unlike other numeric types, the keywords are not simply aliases for the types.</span></span> <span data-ttu-id="f384f-109">Следующие инструкции не являются эквивалентными:</span><span class="sxs-lookup"><span data-stu-id="f384f-109">The following statements are not equivalent:</span></span>

```csharp
nint a = 1;
System.IntPtr a = 1;
```

<span data-ttu-id="f384f-110">Для `nint` и `nuint` компилятор предоставляет такие же преобразования и операции, как для всех целочисленных типов.</span><span class="sxs-lookup"><span data-stu-id="f384f-110">The compiler provides operations and conversions for `nint` and `nuint` that are appropriate for integer types.</span></span>

## <a name="run-time-native-integer-size"></a><span data-ttu-id="f384f-111">Собственный размер целого числа во время выполнения</span><span class="sxs-lookup"><span data-stu-id="f384f-111">Run-time native integer size</span></span>

<span data-ttu-id="f384f-112">Чтобы узнать размер целого числа собственного размера во время выполнения, используйте `sizeof()`.</span><span class="sxs-lookup"><span data-stu-id="f384f-112">To get the size of a native-sized integer at run time, you can use `sizeof()`.</span></span> <span data-ttu-id="f384f-113">Но код должен компилироваться в контексте unsafe.</span><span class="sxs-lookup"><span data-stu-id="f384f-113">However, the code must be compiled in an unsafe context.</span></span> <span data-ttu-id="f384f-114">Пример:</span><span class="sxs-lookup"><span data-stu-id="f384f-114">For example:</span></span>

:::code language="csharp" source="snippets/shared/NativeIntegerTypes.cs" id="SizeOf":::

<span data-ttu-id="f384f-115">Такое же значение можно получить с помощью статических свойств <xref:System.IntPtr.Size?displayProperty=nameWithType> и <xref:System.UIntPtr.Size?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f384f-115">You can also get the equivalent value from the static <xref:System.IntPtr.Size?displayProperty=nameWithType> and <xref:System.UIntPtr.Size?displayProperty=nameWithType> properties.</span></span>

## <a name="minvalue-and-maxvalue"></a><span data-ttu-id="f384f-116">MinValue и MaxValue</span><span class="sxs-lookup"><span data-stu-id="f384f-116">MinValue and MaxValue</span></span>

<span data-ttu-id="f384f-117">Чтобы получить минимальное и максимальное значения целых чисел собственного размера во время выполнения, используйте `MinValue` и `MaxValue` в качестве статических свойств с ключевыми словами `nint` и `nuint`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="f384f-117">To get the minimum and maximum values of native-sized integers at run time, use `MinValue` and `MaxValue` as static properties with the `nint` and `nuint` keywords, as in the following example:</span></span>

:::code language="csharp" source="snippets/shared/NativeIntegerTypes.cs" id="MinMax":::

## <a name="constants"></a><span data-ttu-id="f384f-118">Константы</span><span class="sxs-lookup"><span data-stu-id="f384f-118">Constants</span></span>

<span data-ttu-id="f384f-119">Значения констант можно использовать в таких диапазонах:</span><span class="sxs-lookup"><span data-stu-id="f384f-119">You can use constant values in the following ranges:</span></span>

* <span data-ttu-id="f384f-120">для `nint`: <xref:System.Int32.MinValue?displayProperty=nameWithType>–<xref:System.Int32.MaxValue?displayProperty=nameWithType>;</span><span class="sxs-lookup"><span data-stu-id="f384f-120">For `nint`: <xref:System.Int32.MinValue?displayProperty=nameWithType> to <xref:System.Int32.MaxValue?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="f384f-121">для `nuint`: <xref:System.UInt32.MinValue?displayProperty=nameWithType>–<xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f384f-121">For `nuint`: <xref:System.UInt32.MinValue?displayProperty=nameWithType> to <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

## <a name="conversions"></a><span data-ttu-id="f384f-122">Преобразования</span><span class="sxs-lookup"><span data-stu-id="f384f-122">Conversions</span></span>

<span data-ttu-id="f384f-123">Компилятор предоставляет неявные и явные преобразования в другие числовые типы.</span><span class="sxs-lookup"><span data-stu-id="f384f-123">The compiler provides implicit and explicit conversions to other numeric types.</span></span> <span data-ttu-id="f384f-124">Для получения дополнительной информации см. статью [Встроенные числовые преобразования](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="f384f-124">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="literals"></a><span data-ttu-id="f384f-125">Литералы</span><span class="sxs-lookup"><span data-stu-id="f384f-125">Literals</span></span>

<span data-ttu-id="f384f-126">Для целочисленных литералов собственного размера не поддерживается прямой синтаксис.</span><span class="sxs-lookup"><span data-stu-id="f384f-126">There's no direct syntax for native-sized integer literals.</span></span> <span data-ttu-id="f384f-127">Суффикса, указывающего на то, что литерал является целым числом собственного размера (например, `L` для обозначения `long`), нет.</span><span class="sxs-lookup"><span data-stu-id="f384f-127">There's no suffix to indicate that a literal is a native-sized integer, such as `L` to indicate a `long`.</span></span> <span data-ttu-id="f384f-128">Вместо этого можно использовать явные или неявные приведения других целочисленных значений.</span><span class="sxs-lookup"><span data-stu-id="f384f-128">You can use implicit or explicit casts of other integer values instead.</span></span> <span data-ttu-id="f384f-129">Пример:</span><span class="sxs-lookup"><span data-stu-id="f384f-129">For example:</span></span>

```csharp
nint a = 42
nint a = (nint)42;
```

## <a name="unsupported-intptruintptr-members"></a><span data-ttu-id="f384f-130">Неподдерживаемые элементы IntPtr и UIntPtr</span><span class="sxs-lookup"><span data-stu-id="f384f-130">Unsupported IntPtr/UIntPtr members</span></span>

<span data-ttu-id="f384f-131">Следующие элементы структур <xref:System.IntPtr> и <xref:System.UIntPtr> не поддерживаются для типов `nint` и `nuint`:</span><span class="sxs-lookup"><span data-stu-id="f384f-131">The following members of <xref:System.IntPtr> and <xref:System.UIntPtr> aren't supported for `nint` and `nuint` types:</span></span>

* <span data-ttu-id="f384f-132">Параметризованные конструкторы.</span><span class="sxs-lookup"><span data-stu-id="f384f-132">Parameterized constructors</span></span>
* <xref:System.IntPtr.Add(System.IntPtr,System.Int32)>
* <xref:System.IntPtr.CompareTo%2A>
* <span data-ttu-id="f384f-133"><xref:System.IntPtr.Size>. Вместо этого используйте [sizeOf()](#run-time-native-integer-size).</span><span class="sxs-lookup"><span data-stu-id="f384f-133"><xref:System.IntPtr.Size> - Use [sizeOf()](#run-time-native-integer-size) instead.</span></span> <span data-ttu-id="f384f-134">Хотя `nint.Size` не поддерживается, можно получить эквивалентное значение с помощью `IntPtr.Size`.</span><span class="sxs-lookup"><span data-stu-id="f384f-134">Although `nint.Size` isn't supported, you can use `IntPtr.Size` to get an equivalent value.</span></span>
* <xref:System.IntPtr.Subtract(System.IntPtr,System.Int32)>
* <xref:System.IntPtr.ToInt32%2A>
* <xref:System.IntPtr.ToInt64%2A>
* <xref:System.IntPtr.ToPointer%2A>
* <span data-ttu-id="f384f-135"><xref:System.IntPtr.Zero>. Вместо этого используйте 0.</span><span class="sxs-lookup"><span data-stu-id="f384f-135"><xref:System.IntPtr.Zero> - Use 0 instead.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f384f-136">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="f384f-136">C# language specification</span></span>

<span data-ttu-id="f384f-137">Дополнительные сведения см. в статье о [спецификации языка C#](~/_csharplang/spec/introduction.md) и в статье [Целые числа собственного размера](~/_csharplang/proposals/csharp-9.0/native-integers.md) в предложениях по функциям C# 9.0.</span><span class="sxs-lookup"><span data-stu-id="f384f-137">For more information, see the [C# language specification](~/_csharplang/spec/introduction.md) and the [Native-sized integers](~/_csharplang/proposals/csharp-9.0/native-integers.md) section of the C# 9.0 feature proposal notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="f384f-138">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f384f-138">See also</span></span>

- [<span data-ttu-id="f384f-139">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="f384f-139">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f384f-140">Типы значений</span><span class="sxs-lookup"><span data-stu-id="f384f-140">Value types</span></span>](value-types.md)
- [<span data-ttu-id="f384f-141">Целочисленные типы</span><span class="sxs-lookup"><span data-stu-id="f384f-141">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="f384f-142">Встроенные числовые преобразования</span><span class="sxs-lookup"><span data-stu-id="f384f-142">Built-in numeric conversions</span></span>](numeric-conversions.md)
