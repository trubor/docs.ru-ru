---
title: Справочник по C#. Встроенные типы
description: Сведения о встроенных типах значений и ссылочных типах C#.
ms.date: 03/15/2021
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.openlocfilehash: c2b1c736e17e55913ef1c593813717dd33efd6c3
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759720"
---
# <a name="built-in-types-c-reference"></a><span data-ttu-id="dca50-103">Встроенные типы (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="dca50-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="dca50-104">В следующей таблице приведены встроенные типы [значений](value-types.md) языка C#:</span><span class="sxs-lookup"><span data-stu-id="dca50-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="dca50-105">Ключевое слово типа C#</span><span class="sxs-lookup"><span data-stu-id="dca50-105">C# type keyword</span></span>|<span data-ttu-id="dca50-106">Тип .NET</span><span class="sxs-lookup"><span data-stu-id="dca50-106">.NET type</span></span>|
|--------------|-------------------------|
|[`bool`](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|
|[`byte`](integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|
|[`sbyte`](integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|
|[`char`](char.md)|<xref:System.Char?displayProperty=nameWithType>|
|[`decimal`](floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|
|[`double`](floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|
|[`float`](floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|
|[`int`](integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|
|[`uint`](integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|
|[`nint`](nint-nuint.md)|<xref:System.IntPtr?displayProperty=nameWithType>|
|[`nuint`](nint-nuint.md)|<xref:System.UIntPtr?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

<span data-ttu-id="dca50-107">В следующей таблице приведены встроенные [ссылочные](../keywords/reference-types.md) типы языка C#:</span><span class="sxs-lookup"><span data-stu-id="dca50-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="dca50-108">Ключевое слово типа C#</span><span class="sxs-lookup"><span data-stu-id="dca50-108">C# type keyword</span></span>|<span data-ttu-id="dca50-109">Тип .NET</span><span class="sxs-lookup"><span data-stu-id="dca50-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|
|[`dynamic`](reference-types.md#the-dynamic-type)|<xref:System.Object?displayProperty=nameWithType>|

<span data-ttu-id="dca50-110">В таблицах выше каждое ключевое слово типа C# в левом столбце (кроме [nint и nuint](nint-nuint.md)) является псевдонимом для соответствующего типа .NET.</span><span class="sxs-lookup"><span data-stu-id="dca50-110">In the preceding tables, each C# type keyword from the left column (except [nint and nuint](nint-nuint.md)) is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="dca50-111">Они взаимозаменяемые.</span><span class="sxs-lookup"><span data-stu-id="dca50-111">They are interchangeable.</span></span> <span data-ttu-id="dca50-112">Например, следующие объявления объявляют переменные одного типа:</span><span class="sxs-lookup"><span data-stu-id="dca50-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="dca50-113">Типы `nint` и `nuint` в последних двух строках первой таблицы являются целыми числами собственного размера.</span><span class="sxs-lookup"><span data-stu-id="dca50-113">The `nint` and `nuint` types in the last two rows of the first table are native-sized integers.</span></span> <span data-ttu-id="dca50-114">В коде такие числа представлены определенными типами .NET, но в каждом случае ключевое слово и тип .NET не взаимозаменяемы.</span><span class="sxs-lookup"><span data-stu-id="dca50-114">They are represented internally by the indicated .NET types, but in each case the keyword and the .NET type are not interchangeable.</span></span> <span data-ttu-id="dca50-115">Для `nint` и `nuint` компилятор предоставляет преобразования и операции, как для целочисленных типов. Они отличаются от преобразований и операций для типов указателей `System.IntPtr` и `System.UIntPtr`.</span><span class="sxs-lookup"><span data-stu-id="dca50-115">The compiler provides operations and conversions for `nint` and `nuint` as integer types that it doesn't provide for the pointer types `System.IntPtr` and `System.UIntPtr`.</span></span> <span data-ttu-id="dca50-116">Дополнительные сведения см. в статье о [типах `nint` и `nuint`](nint-nuint.md).</span><span class="sxs-lookup"><span data-stu-id="dca50-116">For more information, see [`nint` and `nuint` types](nint-nuint.md).</span></span>

<span data-ttu-id="dca50-117">Ключевое слово [`void`](void.md) представляет отсутствие типа.</span><span class="sxs-lookup"><span data-stu-id="dca50-117">The [`void`](void.md) keyword represents the absence of a type.</span></span> <span data-ttu-id="dca50-118">Оно используется в качестве возвращаемого типа метода, который не возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="dca50-118">You use it as the return type of a method that doesn't return a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="dca50-119">См. также</span><span class="sxs-lookup"><span data-stu-id="dca50-119">See also</span></span>

- [<span data-ttu-id="dca50-120">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="dca50-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="dca50-121">Значения по умолчанию типов C#</span><span class="sxs-lookup"><span data-stu-id="dca50-121">Default values of C# types</span></span>](default-values.md)
