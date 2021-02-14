---
description: 'Дополнительные сведения: эффективное использование типов данных (Visual Basic)'
title: Эффективное использование типов данных
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: e7660bbdec530ef18d663975e314d90b64e4b055
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476440"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="0accb-103">Эффективное использование типов данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0accb-103">Efficient Use of Data Types (Visual Basic)</span></span>

<span data-ttu-id="0accb-104">Тип данных назначается необъявленным переменным и переменным, объявленным без типа данных `Object` .</span><span class="sxs-lookup"><span data-stu-id="0accb-104">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="0accb-105">Это упрощает написание программ, но может привести к более медленному их выполнению.</span><span class="sxs-lookup"><span data-stu-id="0accb-105">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>

## <a name="strong-typing"></a><span data-ttu-id="0accb-106">Строгая типизация</span><span class="sxs-lookup"><span data-stu-id="0accb-106">Strong Typing</span></span>

 <span data-ttu-id="0accb-107">Указание типов данных для всех переменных называется *строгой типизацией*.</span><span class="sxs-lookup"><span data-stu-id="0accb-107">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="0accb-108">Использование строгой типизации имеет несколько преимуществ.</span><span class="sxs-lookup"><span data-stu-id="0accb-108">Using strong typing has several advantages:</span></span>

- <span data-ttu-id="0accb-109">Он обеспечивает поддержку IntelliSense для переменных.</span><span class="sxs-lookup"><span data-stu-id="0accb-109">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="0accb-110">Это позволяет просматривать их свойства и другие члены по мере ввода кода.</span><span class="sxs-lookup"><span data-stu-id="0accb-110">This allows you to see their properties and other members as you type in the code.</span></span>

- <span data-ttu-id="0accb-111">Он использует преимущества проверки типов компилятора.</span><span class="sxs-lookup"><span data-stu-id="0accb-111">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="0accb-112">Это перехватывает инструкции, которые могут завершиться ошибкой во время выполнения из-за таких ошибок, как переполнение.</span><span class="sxs-lookup"><span data-stu-id="0accb-112">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="0accb-113">Он также перехватывает вызовы методов для объектов, которые их не поддерживают.</span><span class="sxs-lookup"><span data-stu-id="0accb-113">It also catches calls to methods on objects that do not support them.</span></span>

- <span data-ttu-id="0accb-114">Это приводит к ускорению выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="0accb-114">It results in faster execution of your code.</span></span>

## <a name="most-efficient-data-types"></a><span data-ttu-id="0accb-115">Наиболее эффективные типы данных</span><span class="sxs-lookup"><span data-stu-id="0accb-115">Most Efficient Data Types</span></span>

 <span data-ttu-id="0accb-116">Для переменных, которые никогда не содержат дробей, целочисленные типы данных более эффективны, чем Нецелочисленные типы.</span><span class="sxs-lookup"><span data-stu-id="0accb-116">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="0accb-117">В Visual Basic `Integer` и `UInteger` являются наиболее эффективными числовыми типами.</span><span class="sxs-lookup"><span data-stu-id="0accb-117">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>

 <span data-ttu-id="0accb-118">Для дробных чисел `Double` является наиболее эффективным типом данных, так как процессоры на текущих платформах выполняют операции с плавающей запятой с двойной точностью.</span><span class="sxs-lookup"><span data-stu-id="0accb-118">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="0accb-119">Однако операции с `Double` не так быстро, как с целочисленными типами, такими как `Integer` .</span><span class="sxs-lookup"><span data-stu-id="0accb-119">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>

## <a name="specifying-data-type"></a><span data-ttu-id="0accb-120">Указание типа данных</span><span class="sxs-lookup"><span data-stu-id="0accb-120">Specifying Data Type</span></span>

 <span data-ttu-id="0accb-121">Используйте [оператор Dim](../../../language-reference/statements/dim-statement.md) для объявления переменной определенного типа.</span><span class="sxs-lookup"><span data-stu-id="0accb-121">Use the [Dim Statement](../../../language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="0accb-122">Уровень доступа можно указать одновременно с помощью ключевого слова [Public](../../../language-reference/modifiers/public.md), [protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md)или [Private](../../../language-reference/modifiers/private.md) , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0accb-122">You can simultaneously specify its access level by using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, as in the following example.</span></span>

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a><span data-ttu-id="0accb-123">Преобразование символов</span><span class="sxs-lookup"><span data-stu-id="0accb-123">Character Conversion</span></span>

 <span data-ttu-id="0accb-124">`AscW`Функции и `ChrW` работают в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="0accb-124">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="0accb-125">Их следует использовать в предпочтениях `Asc` и `Chr` , которые должны преобразовываться в Юникод и из него.</span><span class="sxs-lookup"><span data-stu-id="0accb-125">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>

## <a name="see-also"></a><span data-ttu-id="0accb-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0accb-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="0accb-127">Типы данных</span><span class="sxs-lookup"><span data-stu-id="0accb-127">Data Types</span></span>](index.md)
- [<span data-ttu-id="0accb-128">Числовые типы данных</span><span class="sxs-lookup"><span data-stu-id="0accb-128">Numeric Data Types</span></span>](numeric-data-types.md)
- [<span data-ttu-id="0accb-129">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="0accb-129">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="0accb-130">Использование технологии IntelliSense</span><span class="sxs-lookup"><span data-stu-id="0accb-130">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
