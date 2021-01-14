---
title: Руководство по программированию на C#. Преобразование шестнадцатеричных значений из строкового типа в числовой тип
description: Сведения о преобразовании из шестнадцатеричных строк в числовые типы. Изучите примеры кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 35cf1af661071c70b8d68de2e47ce555be7b9fef
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025411"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="c9a1e-104">Руководство по программированию на C#. Преобразование шестнадцатеричных значений из строкового типа в числовой тип</span><span class="sxs-lookup"><span data-stu-id="c9a1e-104">How to convert between hexadecimal strings and numeric types (C# Programming Guide)</span></span>

<span data-ttu-id="c9a1e-105">В следующих примерах кода показано выполнение указанных ниже задач.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-105">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="c9a1e-106">Получение шестнадцатеричного значения каждого символа в [string](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="c9a1e-106">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="c9a1e-107">Получение [char](../../language-reference/builtin-types/char.md), соответствующего каждому значению в шестнадцатеричной строке.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-107">Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="c9a1e-108">Преобразование шестнадцатеричного значения `string` в [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="c9a1e-108">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="c9a1e-109">Преобразование шестнадцатеричного значения `string` в [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="c9a1e-109">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="c9a1e-110">Преобразование массива [byte](../../language-reference/builtin-types/integral-numeric-types.md) в шестнадцатеричное значение `string`.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-110">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9a1e-111">Пример</span><span class="sxs-lookup"><span data-stu-id="c9a1e-111">Example</span></span>  

 <span data-ttu-id="c9a1e-112">Результатом следующего примера является шестнадцатеричное значение каждого символа в `string`.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-112">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="c9a1e-113">Сначала выполняется разбор `string` до массива символов.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-113">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="c9a1e-114">Затем, чтобы получить числовое значение каждого символа, для каждого из них вызывается метод <xref:System.Convert.ToInt32%28System.Char%29>.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-114">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="c9a1e-115">В конце формат числа меняется на шестнадцатеричный в `string`.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-115">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="c9a1e-116">Пример</span><span class="sxs-lookup"><span data-stu-id="c9a1e-116">Example</span></span>  

 <span data-ttu-id="c9a1e-117">В этом примере анализируется `string` шестнадцатеричных значений и выводится символ, соответствующий каждому шестнадцатеричному значению.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-117">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="c9a1e-118">Сначала вызывается метод [Split(Char\[\])](xref:System.String.Split(System.Char[])) для получения каждого шестнадцатеричного значения как отдельной `string` в массиве.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-118">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="c9a1e-119">Затем вызывается метод <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29>, который преобразует шестнадцатеричное значение в десятичное, представленное в [целое число](../../language-reference/builtin-types/integral-numeric-types.md). В примере показано два разных способа получения символа, соответствующего этому коду символа.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-119">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="c9a1e-120">В первом случае используется <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, который возвращает символ, соответствующий целочисленному аргументу, в виде `string`.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-120">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="c9a1e-121">По второму способу выполняется явное приведение `int` к [char](../../language-reference/builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="c9a1e-121">The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="c9a1e-122">Пример</span><span class="sxs-lookup"><span data-stu-id="c9a1e-122">Example</span></span>  

 <span data-ttu-id="c9a1e-123">В этом примере показан еще один способ преобразования шестнадцатеричного `string` в целое число — с помощью метода <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> .</span><span class="sxs-lookup"><span data-stu-id="c9a1e-123">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="c9a1e-124">Пример</span><span class="sxs-lookup"><span data-stu-id="c9a1e-124">Example</span></span>  

 <span data-ttu-id="c9a1e-125">В следующем примере показано преобразование шестнадцатеричного `string` в [число с плавающей запятой](../../language-reference/builtin-types/floating-point-numeric-types.md) с помощью класса <xref:System.BitConverter?displayProperty=nameWithType> и метод <xref:System.UInt32.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-125">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="c9a1e-126">Пример</span><span class="sxs-lookup"><span data-stu-id="c9a1e-126">Example</span></span>  

 <span data-ttu-id="c9a1e-127">В следующем примере показано преобразование массива [байтов](../../language-reference/builtin-types/integral-numeric-types.md) в шестнадцатеричную строку с помощью класса <xref:System.BitConverter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-127">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="example"></a><span data-ttu-id="c9a1e-128">Пример</span><span class="sxs-lookup"><span data-stu-id="c9a1e-128">Example</span></span>  

 <span data-ttu-id="c9a1e-129">В следующем примере показано преобразование массива [байтов](../../language-reference/builtin-types/integral-numeric-types.md) в шестнадцатеричную строку посредством вызова метода <xref:System.Convert.ToHexString%2A?displayProperty=nameWithType>, который был представлен в .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-129">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by calling the <xref:System.Convert.ToHexString%2A?displayProperty=nameWithType> method introduced in .NET 5.0.</span></span>
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="see-also"></a><span data-ttu-id="c9a1e-130">См. также</span><span class="sxs-lookup"><span data-stu-id="c9a1e-130">See also</span></span>

- [<span data-ttu-id="c9a1e-131">Строки стандартных числовых форматов</span><span class="sxs-lookup"><span data-stu-id="c9a1e-131">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="c9a1e-132">Типы</span><span class="sxs-lookup"><span data-stu-id="c9a1e-132">Types</span></span>](./index.md)
- [<span data-ttu-id="c9a1e-133">Определение представления числового значения в строке</span><span class="sxs-lookup"><span data-stu-id="c9a1e-133">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
