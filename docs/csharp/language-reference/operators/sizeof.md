---
description: Справочник по C#. Оператор sizeof
title: Справочник по C#. Оператор sizeof
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 6685cdb4fba2460ee4a47b004aa6911ab76235a4
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497376"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="093f3-103">Справочник по C#. Оператор sizeof</span><span class="sxs-lookup"><span data-stu-id="093f3-103">sizeof operator (C# reference)</span></span>

<span data-ttu-id="093f3-104">Оператор `sizeof` позволяет получать число байт, занятых переменной заданного типа.</span><span class="sxs-lookup"><span data-stu-id="093f3-104">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="093f3-105">Аргумент оператора `sizeof` должен быть именем [неуправляемого типа](../builtin-types/unmanaged-types.md) или параметром типа, к которому применяется [ограничение](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint), указывающее, что он является неуправляемым типом.</span><span class="sxs-lookup"><span data-stu-id="093f3-105">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="093f3-106">Для использования оператора `sizeof` требуется [небезопасный](../keywords/unsafe.md) контекст.</span><span class="sxs-lookup"><span data-stu-id="093f3-106">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="093f3-107">Однако выражения, приведенные в следующей таблице, вычисляются во время компиляции для получения соответствующих константных значений и им не требуется небезопасный контекст.</span><span class="sxs-lookup"><span data-stu-id="093f3-107">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="093f3-108">Выражение</span><span class="sxs-lookup"><span data-stu-id="093f3-108">Expression</span></span>|<span data-ttu-id="093f3-109">Константа</span><span class="sxs-lookup"><span data-stu-id="093f3-109">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="093f3-110">1</span><span class="sxs-lookup"><span data-stu-id="093f3-110">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="093f3-111">1</span><span class="sxs-lookup"><span data-stu-id="093f3-111">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="093f3-112">2</span><span class="sxs-lookup"><span data-stu-id="093f3-112">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="093f3-113">2</span><span class="sxs-lookup"><span data-stu-id="093f3-113">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="093f3-114">4</span><span class="sxs-lookup"><span data-stu-id="093f3-114">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="093f3-115">4</span><span class="sxs-lookup"><span data-stu-id="093f3-115">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="093f3-116">8</span><span class="sxs-lookup"><span data-stu-id="093f3-116">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="093f3-117">8</span><span class="sxs-lookup"><span data-stu-id="093f3-117">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="093f3-118">2</span><span class="sxs-lookup"><span data-stu-id="093f3-118">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="093f3-119">4</span><span class="sxs-lookup"><span data-stu-id="093f3-119">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="093f3-120">8</span><span class="sxs-lookup"><span data-stu-id="093f3-120">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="093f3-121">16</span><span class="sxs-lookup"><span data-stu-id="093f3-121">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="093f3-122">1</span><span class="sxs-lookup"><span data-stu-id="093f3-122">1</span></span>|

<span data-ttu-id="093f3-123">Небезопасный контекст также не требуется, если операнд оператора `sizeof` является именем [перечисляемого](../builtin-types/enum.md) типа.</span><span class="sxs-lookup"><span data-stu-id="093f3-123">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="093f3-124">В следующем примере иллюстрируется использование оператора `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="093f3-124">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](snippets/shared/SizeOfOperator.cs)]

<span data-ttu-id="093f3-125">Оператор `sizeof` возвращает число байт, выделяемых средой CLR в управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="093f3-125">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="093f3-126">Для типов [структуры](../builtin-types/struct.md) в это значение входит любое заполнение, как показано в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="093f3-126">For [struct](../builtin-types/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="093f3-127">Результат использования оператора `sizeof` может отличаться от результата работы метода <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, который возвращает размер типа в *неуправляемой* памяти.</span><span class="sxs-lookup"><span data-stu-id="093f3-127">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="093f3-128">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="093f3-128">C# language specification</span></span>

<span data-ttu-id="093f3-129">Дополнительные сведения см. в разделе [Оператор sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator)[спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="093f3-129">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="093f3-130">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="093f3-130">See also</span></span>

- [<span data-ttu-id="093f3-131">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="093f3-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="093f3-132">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="093f3-132">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="093f3-133">Операторы, связанные с указателем</span><span class="sxs-lookup"><span data-stu-id="093f3-133">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="093f3-134">Типы указателей</span><span class="sxs-lookup"><span data-stu-id="093f3-134">Pointer types</span></span>](../unsafe-code.md#pointer-types)
- [<span data-ttu-id="093f3-135">Типы, связанные с памятью и диапазонами</span><span class="sxs-lookup"><span data-stu-id="093f3-135">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="093f3-136">Универсальные шаблоны в .NET</span><span class="sxs-lookup"><span data-stu-id="093f3-136">Generics in .NET</span></span>](../../../standard/generics/index.md)
