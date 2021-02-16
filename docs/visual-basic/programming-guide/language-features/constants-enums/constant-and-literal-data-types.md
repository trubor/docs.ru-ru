---
description: 'Дополнительные сведения: константные и литеральные типы данных (Visual Basic)'
title: Типы данных констант и литералов
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: e750b1e5746f935c7878e186d064060d0fa055dc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475439"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="047a5-103">Типы данных констант и литералов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="047a5-103">Constant and Literal Data Types (Visual Basic)</span></span>

<span data-ttu-id="047a5-104">Литерал — это значение, которое выражено как само по себе, а не как значение переменной или результат выражения, например число 3 или строка "Hello".</span><span class="sxs-lookup"><span data-stu-id="047a5-104">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="047a5-105">Константа — это понятное имя, которое принимает место литерала и сохраняется в программе в отличие от переменной, значение которой может измениться.</span><span class="sxs-lookup"><span data-stu-id="047a5-105">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="047a5-106">Если [параметр Infer](../../../language-reference/statements/option-infer-statement.md) имеет значение `Off` и [параметр Option строго](../../../language-reference/statements/option-strict-statement.md) имеет значение `On` , необходимо явно объявить все константы с типом данных.</span><span class="sxs-lookup"><span data-stu-id="047a5-106">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="047a5-107">В следующем примере тип данных `MyByte` явно объявлен как тип данных `Byte` :</span><span class="sxs-lookup"><span data-stu-id="047a5-107">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 <span data-ttu-id="047a5-108">Если `Option Infer` имеет значение `On` или `Option Strict` является `Off` , можно объявить константу без указания типа данных с `As` предложением.</span><span class="sxs-lookup"><span data-stu-id="047a5-108">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="047a5-109">Компилятор определяет тип константы на основе типа выражения.</span><span class="sxs-lookup"><span data-stu-id="047a5-109">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="047a5-110">Числовой целочисленный литерал по умолчанию приводится к `Integer` типу данных.</span><span class="sxs-lookup"><span data-stu-id="047a5-110">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="047a5-111">Тип данных по умолчанию для чисел с плавающей запятой — `Double` , и ключевые слова `True` и `False` задают `Boolean` константу.</span><span class="sxs-lookup"><span data-stu-id="047a5-111">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="047a5-112">Литералы и приведение типов</span><span class="sxs-lookup"><span data-stu-id="047a5-112">Literals and Type Coercion</span></span>  

 <span data-ttu-id="047a5-113">В некоторых случаях может потребоваться принудительно применить литерал к конкретному типу данных. Например, при присваивании особо большого целочисленного значения литерала переменной типа `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="047a5-113">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="047a5-114">Следующий пример приводит к ошибке:</span><span class="sxs-lookup"><span data-stu-id="047a5-114">The following example produces an error:</span></span>  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="047a5-115">Эта ошибка возникает из представления литерала.</span><span class="sxs-lookup"><span data-stu-id="047a5-115">The error results from the representation of the literal.</span></span> <span data-ttu-id="047a5-116">`Decimal`Тип данных может содержать это значение, но литерал неявно представляется как `Long` , что не может.</span><span class="sxs-lookup"><span data-stu-id="047a5-116">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="047a5-117">Можно привести литерал к определенному типу данных двумя способами: путем добавления к нему символа типа или путем помещения его в окружающие символы.</span><span class="sxs-lookup"><span data-stu-id="047a5-117">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="047a5-118">Символ типа или заключенные в него символы должны находиться непосредственно перед и/или следовать за литералом без промежуточного пробела или символов какого-либо типа.</span><span class="sxs-lookup"><span data-stu-id="047a5-118">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="047a5-119">Чтобы предыдущий пример работал, можно добавить `D` символ типа к литералу, что приводит к представлению в виде `Decimal` :</span><span class="sxs-lookup"><span data-stu-id="047a5-119">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 <span data-ttu-id="047a5-120">В следующем примере показано правильное использование символов типа и окружающих символов:</span><span class="sxs-lookup"><span data-stu-id="047a5-120">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 <span data-ttu-id="047a5-121">В следующей таблице показаны окружающие символы и символы типа, доступные в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="047a5-121">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="047a5-122">Тип данных</span><span class="sxs-lookup"><span data-stu-id="047a5-122">Data type</span></span>|<span data-ttu-id="047a5-123">Вложенный символ</span><span class="sxs-lookup"><span data-stu-id="047a5-123">Enclosing character</span></span>|<span data-ttu-id="047a5-124">Символ добавленного типа</span><span class="sxs-lookup"><span data-stu-id="047a5-124">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="047a5-125">(нет)</span><span class="sxs-lookup"><span data-stu-id="047a5-125">(none)</span></span>|<span data-ttu-id="047a5-126">(нет)</span><span class="sxs-lookup"><span data-stu-id="047a5-126">(none)</span></span>|  
|`Byte`|<span data-ttu-id="047a5-127">(нет)</span><span class="sxs-lookup"><span data-stu-id="047a5-127">(none)</span></span>|<span data-ttu-id="047a5-128">(нет)</span><span class="sxs-lookup"><span data-stu-id="047a5-128">(none)</span></span>|  
|`Char`|<span data-ttu-id="047a5-129">"</span><span class="sxs-lookup"><span data-stu-id="047a5-129">"</span></span>|<span data-ttu-id="047a5-130">C</span><span class="sxs-lookup"><span data-stu-id="047a5-130">C</span></span>|  
|`Date`|#|<span data-ttu-id="047a5-131">(нет)</span><span class="sxs-lookup"><span data-stu-id="047a5-131">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="047a5-132">(нет)</span><span class="sxs-lookup"><span data-stu-id="047a5-132">(none)</span></span>|<span data-ttu-id="047a5-133">D или @</span><span class="sxs-lookup"><span data-stu-id="047a5-133">D or @</span></span>|  
|`Double`|<span data-ttu-id="047a5-134">(нет)</span><span class="sxs-lookup"><span data-stu-id="047a5-134">(none)</span></span>|<span data-ttu-id="047a5-135">R или #</span><span class="sxs-lookup"><span data-stu-id="047a5-135">R or #</span></span>|  
|`Integer`|<span data-ttu-id="047a5-136">(нет)</span><span class="sxs-lookup"><span data-stu-id="047a5-136">(none)</span></span>|<span data-ttu-id="047a5-137">I или%</span><span class="sxs-lookup"><span data-stu-id="047a5-137">I or %</span></span>|  
|`Long`|<span data-ttu-id="047a5-138">(нет)</span><span class="sxs-lookup"><span data-stu-id="047a5-138">(none)</span></span>|<span data-ttu-id="047a5-139">L или &</span><span class="sxs-lookup"><span data-stu-id="047a5-139">L or &</span></span>|  
|`Short`|<span data-ttu-id="047a5-140">(нет)</span><span class="sxs-lookup"><span data-stu-id="047a5-140">(none)</span></span>|<span data-ttu-id="047a5-141">S</span><span class="sxs-lookup"><span data-stu-id="047a5-141">S</span></span>|  
|`Single`|<span data-ttu-id="047a5-142">(нет)</span><span class="sxs-lookup"><span data-stu-id="047a5-142">(none)</span></span>|<span data-ttu-id="047a5-143">F или!</span><span class="sxs-lookup"><span data-stu-id="047a5-143">F or !</span></span>|  
|`String`|<span data-ttu-id="047a5-144">"</span><span class="sxs-lookup"><span data-stu-id="047a5-144">"</span></span>|<span data-ttu-id="047a5-145">(нет)</span><span class="sxs-lookup"><span data-stu-id="047a5-145">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="047a5-146">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="047a5-146">See also</span></span>

- [<span data-ttu-id="047a5-147">Константы, определенные пользователем</span><span class="sxs-lookup"><span data-stu-id="047a5-147">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="047a5-148">Практическое руководство. Объявление константы</span><span class="sxs-lookup"><span data-stu-id="047a5-148">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="047a5-149">Общие сведения о константах</span><span class="sxs-lookup"><span data-stu-id="047a5-149">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="047a5-150">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="047a5-150">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="047a5-151">Оператор Option Explicit</span><span class="sxs-lookup"><span data-stu-id="047a5-151">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="047a5-152">Общие сведения о перечислениях</span><span class="sxs-lookup"><span data-stu-id="047a5-152">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="047a5-153">Практическое руководство. Объявление перечисления</span><span class="sxs-lookup"><span data-stu-id="047a5-153">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="047a5-154">Перечисления и уточнение имен</span><span class="sxs-lookup"><span data-stu-id="047a5-154">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="047a5-155">Типы данных</span><span class="sxs-lookup"><span data-stu-id="047a5-155">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="047a5-156">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="047a5-156">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
