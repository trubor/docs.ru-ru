---
description: 'Дополнительные сведения о операторе: + (Visual Basic)'
title: + Оператор
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 9a6517847945cb2edcbd97adac6a013498dde174
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700693"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="26fe0-103">Оператор + (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26fe0-103">+ Operator (Visual Basic)</span></span>

<span data-ttu-id="26fe0-104">Складывает два числа или возвращает положительное значение числового выражения.</span><span class="sxs-lookup"><span data-stu-id="26fe0-104">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="26fe0-105">Также можно использовать для сцепления двух строковых выражений.</span><span class="sxs-lookup"><span data-stu-id="26fe0-105">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26fe0-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="26fe0-106">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="26fe0-107">or</span><span class="sxs-lookup"><span data-stu-id="26fe0-107">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="26fe0-108">Компоненты</span><span class="sxs-lookup"><span data-stu-id="26fe0-108">Parts</span></span>  
  
|<span data-ttu-id="26fe0-109">Термин</span><span class="sxs-lookup"><span data-stu-id="26fe0-109">Term</span></span>|<span data-ttu-id="26fe0-110">Определение</span><span class="sxs-lookup"><span data-stu-id="26fe0-110">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="26fe0-111">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="26fe0-111">Required.</span></span> <span data-ttu-id="26fe0-112">Любое числовое или строковое выражение.</span><span class="sxs-lookup"><span data-stu-id="26fe0-112">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="26fe0-113">Требуется, если `+` оператор не вычисляет отрицательное значение.</span><span class="sxs-lookup"><span data-stu-id="26fe0-113">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="26fe0-114">Любое числовое или строковое выражение.</span><span class="sxs-lookup"><span data-stu-id="26fe0-114">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="26fe0-115">Результат</span><span class="sxs-lookup"><span data-stu-id="26fe0-115">Result</span></span>  

 <span data-ttu-id="26fe0-116">Если `expression1` и `expression2` являются числовыми, результатом является их арифметическая сумма.</span><span class="sxs-lookup"><span data-stu-id="26fe0-116">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="26fe0-117">Если параметр отсутствует `expression2` , `+` оператор является *унарным* оператором идентификации для неизменного значения выражения.</span><span class="sxs-lookup"><span data-stu-id="26fe0-117">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="26fe0-118">В этом смысле операция состоит из удержания знака `expression1` , поэтому результат будет отрицательным, если `expression1` имеет отрицательное значение.</span><span class="sxs-lookup"><span data-stu-id="26fe0-118">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="26fe0-119">Если `expression1` и `expression2` являются строками, результатом является объединение их значений.</span><span class="sxs-lookup"><span data-stu-id="26fe0-119">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="26fe0-120">Если `expression1` и `expression2` имеют смешанные типы, то выполняемое действие зависит от их типов, их содержимого и значения, установленного в [операторе Option](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="26fe0-120">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="26fe0-121">Дополнительные сведения см. в таблицах в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="26fe0-121">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="26fe0-122">Поддерживаемые типы</span><span class="sxs-lookup"><span data-stu-id="26fe0-122">Supported Types</span></span>  

 <span data-ttu-id="26fe0-123">Все числовые типы, включая неподписанные и типы с плавающей запятой `Decimal` , и `String` .</span><span class="sxs-lookup"><span data-stu-id="26fe0-123">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26fe0-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="26fe0-124">Remarks</span></span>  

 <span data-ttu-id="26fe0-125">Как правило, `+` выполняет арифметическое сложение, когда это возможно, и объединяет только в том случае, если оба выражения являются строками.</span><span class="sxs-lookup"><span data-stu-id="26fe0-125">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="26fe0-126">Если ни одно из выражений не является `Object` , Visual Basic выполняет следующие действия.</span><span class="sxs-lookup"><span data-stu-id="26fe0-126">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="26fe0-127">Типы данных выражений</span><span class="sxs-lookup"><span data-stu-id="26fe0-127">Data types of expressions</span></span>|<span data-ttu-id="26fe0-128">Действие по компилятору</span><span class="sxs-lookup"><span data-stu-id="26fe0-128">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="26fe0-129">Оба выражения являются числовыми типами данных ( `SByte` ,, `Byte` ,, `Short` `UShort` `Integer` , `UInteger` , `Long` , `ULong` , `Decimal` , `Single` или `Double` ).</span><span class="sxs-lookup"><span data-stu-id="26fe0-129">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="26fe0-130">Добавить.</span><span class="sxs-lookup"><span data-stu-id="26fe0-130">Add.</span></span> <span data-ttu-id="26fe0-131">Тип данных result является числовым типом, подходящим для типов данных `expression1` и `expression2` .</span><span class="sxs-lookup"><span data-stu-id="26fe0-131">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="26fe0-132">См. таблицу "целочисленные арифметические операции" в [типах данных результатов операторов](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="26fe0-132">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="26fe0-133">Оба выражения имеют тип `String`</span><span class="sxs-lookup"><span data-stu-id="26fe0-133">Both expressions are of type `String`</span></span>|<span data-ttu-id="26fe0-134">Объединения.</span><span class="sxs-lookup"><span data-stu-id="26fe0-134">Concatenate.</span></span>|  
|<span data-ttu-id="26fe0-135">Одно выражение является числовым типом данных, а второй — строкой</span><span class="sxs-lookup"><span data-stu-id="26fe0-135">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="26fe0-136">Если `Option Strict` имеет значение `On` , то генерируется ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="26fe0-136">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="26fe0-137">Если `Option Strict` имеет значение `Off` , то неявно преобразует в `String` `Double` и добавьте.</span><span class="sxs-lookup"><span data-stu-id="26fe0-137">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="26fe0-138">Если `String` не удается преобразовать в `Double` , вызовите <xref:System.InvalidCastException> исключение.</span><span class="sxs-lookup"><span data-stu-id="26fe0-138">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="26fe0-139">Одно выражение имеет числовой тип данных, а другой — [Nothing](../nothing.md) .</span><span class="sxs-lookup"><span data-stu-id="26fe0-139">One expression is a numeric data type, and the other is [Nothing](../nothing.md)</span></span>|<span data-ttu-id="26fe0-140">Добавьте со `Nothing` значением 0.</span><span class="sxs-lookup"><span data-stu-id="26fe0-140">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="26fe0-141">Одно выражение — строка, а другая — `Nothing`</span><span class="sxs-lookup"><span data-stu-id="26fe0-141">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="26fe0-142">Объединение со `Nothing` значением "".</span><span class="sxs-lookup"><span data-stu-id="26fe0-142">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="26fe0-143">Если одно выражение является `Object` выражением, Visual Basic выполняет следующие действия.</span><span class="sxs-lookup"><span data-stu-id="26fe0-143">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="26fe0-144">Типы данных выражений</span><span class="sxs-lookup"><span data-stu-id="26fe0-144">Data types of expressions</span></span>|<span data-ttu-id="26fe0-145">Действие по компилятору</span><span class="sxs-lookup"><span data-stu-id="26fe0-145">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="26fe0-146">`Object` выражение содержит числовое значение, а другое — числовой тип данных</span><span class="sxs-lookup"><span data-stu-id="26fe0-146">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="26fe0-147">Если `Option Strict` имеет значение `On` , то генерируется ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="26fe0-147">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="26fe0-148">Если `Option Strict` имеет значение `Off` , добавьте.</span><span class="sxs-lookup"><span data-stu-id="26fe0-148">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="26fe0-149">`Object` выражение содержит числовое значение, а другое имеет тип `String`</span><span class="sxs-lookup"><span data-stu-id="26fe0-149">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="26fe0-150">Если `Option Strict` имеет значение `On` , то генерируется ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="26fe0-150">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="26fe0-151">Если `Option Strict` имеет значение `Off` , то неявно преобразует в `String` `Double` и добавьте.</span><span class="sxs-lookup"><span data-stu-id="26fe0-151">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="26fe0-152">Если `String` не удается преобразовать в `Double` , вызовите <xref:System.InvalidCastException> исключение.</span><span class="sxs-lookup"><span data-stu-id="26fe0-152">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="26fe0-153">`Object` выражение содержит строку, а другая — числовой тип данных</span><span class="sxs-lookup"><span data-stu-id="26fe0-153">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="26fe0-154">Если `Option Strict` имеет значение `On` , то генерируется ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="26fe0-154">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="26fe0-155">Если `Option Strict` имеет значение `Off` , то неявно преобразует строку `Object` в `Double` и добавьте.</span><span class="sxs-lookup"><span data-stu-id="26fe0-155">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="26fe0-156">Если строка `Object` не может быть преобразована в `Double` , возникает <xref:System.InvalidCastException> исключение.</span><span class="sxs-lookup"><span data-stu-id="26fe0-156">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="26fe0-157">`Object` выражение содержит строку, а другая — тип `String`</span><span class="sxs-lookup"><span data-stu-id="26fe0-157">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="26fe0-158">Если `Option Strict` имеет значение `On` , то генерируется ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="26fe0-158">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="26fe0-159">Если `Option Strict` имеет значение `Off` , то неявное преобразование `Object` в `String` и сцепление.</span><span class="sxs-lookup"><span data-stu-id="26fe0-159">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="26fe0-160">Если оба выражения являются `Object` выражениями, Visual Basic выполняет следующие действия ( `Option Strict Off` только).</span><span class="sxs-lookup"><span data-stu-id="26fe0-160">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="26fe0-161">Типы данных выражений</span><span class="sxs-lookup"><span data-stu-id="26fe0-161">Data types of expressions</span></span>|<span data-ttu-id="26fe0-162">Действие по компилятору</span><span class="sxs-lookup"><span data-stu-id="26fe0-162">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="26fe0-163">Оба `Object` выражения содержат числовые значения</span><span class="sxs-lookup"><span data-stu-id="26fe0-163">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="26fe0-164">Добавить.</span><span class="sxs-lookup"><span data-stu-id="26fe0-164">Add.</span></span>|  
|<span data-ttu-id="26fe0-165">Оба `Object` выражения имеют тип `String`</span><span class="sxs-lookup"><span data-stu-id="26fe0-165">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="26fe0-166">Объединения.</span><span class="sxs-lookup"><span data-stu-id="26fe0-166">Concatenate.</span></span>|  
|<span data-ttu-id="26fe0-167">Одно `Object` выражение содержит числовое значение, а другое содержит строку.</span><span class="sxs-lookup"><span data-stu-id="26fe0-167">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="26fe0-168">Неявным образом Преобразуйте строку `Object` в `Double` и добавьте.</span><span class="sxs-lookup"><span data-stu-id="26fe0-168">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="26fe0-169">Если строка `Object` не может быть преобразована в числовое значение, то возникает <xref:System.InvalidCastException> исключение.</span><span class="sxs-lookup"><span data-stu-id="26fe0-169">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="26fe0-170">Если любое из `Object` выражений имеет значение [Nothing](../nothing.md) или <xref:System.DBNull> , `+` оператор обрабатывает его как `String` со значением "".</span><span class="sxs-lookup"><span data-stu-id="26fe0-170">If either `Object` expression evaluates to [Nothing](../nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26fe0-171">При использовании `+` оператора может быть невозможно определить, будет ли выполняться сложение или объединение строк.</span><span class="sxs-lookup"><span data-stu-id="26fe0-171">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="26fe0-172">Используйте `&` оператор для объединения, чтобы исключить неоднозначность и предоставить код для самостоятельного документирования.</span><span class="sxs-lookup"><span data-stu-id="26fe0-172">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="26fe0-173">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="26fe0-173">Overloading</span></span>  

 <span data-ttu-id="26fe0-174">`+`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="26fe0-174">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="26fe0-175">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="26fe0-175">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="26fe0-176">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="26fe0-176">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26fe0-177">Пример</span><span class="sxs-lookup"><span data-stu-id="26fe0-177">Example</span></span>  

 <span data-ttu-id="26fe0-178">В следующем примере оператор используется `+` для добавления чисел.</span><span class="sxs-lookup"><span data-stu-id="26fe0-178">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="26fe0-179">Если операнды являются числовыми, Visual Basic вычислит арифметический результат.</span><span class="sxs-lookup"><span data-stu-id="26fe0-179">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="26fe0-180">Арифметический результат представляет сумму двух операндов.</span><span class="sxs-lookup"><span data-stu-id="26fe0-180">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="26fe0-181">Можно также использовать `+` оператор для сцепления строк.</span><span class="sxs-lookup"><span data-stu-id="26fe0-181">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="26fe0-182">Если операнды являются строками, Visual Basic сцепляет их.</span><span class="sxs-lookup"><span data-stu-id="26fe0-182">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="26fe0-183">Результат объединения представляет собой одну строку, состоящую из содержимого двух операндов, один за другим.</span><span class="sxs-lookup"><span data-stu-id="26fe0-183">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="26fe0-184">Если операнды имеют смешанные типы, результат зависит от значения параметра [Option Case](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="26fe0-184">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="26fe0-185">В следующем примере показан результат, если `Option Strict` имеет значение `On` .</span><span class="sxs-lookup"><span data-stu-id="26fe0-185">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="26fe0-186">В следующем примере показан результат, если `Option Strict` имеет значение `Off` .</span><span class="sxs-lookup"><span data-stu-id="26fe0-186">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="26fe0-187">Чтобы избежать неоднозначности, следует использовать `&` оператор вместо `+` для объединения.</span><span class="sxs-lookup"><span data-stu-id="26fe0-187">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26fe0-188">См. также</span><span class="sxs-lookup"><span data-stu-id="26fe0-188">See also</span></span>

- [<span data-ttu-id="26fe0-189"> Оператор&</span><span class="sxs-lookup"><span data-stu-id="26fe0-189">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="26fe0-190">Операторы объединения</span><span class="sxs-lookup"><span data-stu-id="26fe0-190">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="26fe0-191">Арифметические операторы</span><span class="sxs-lookup"><span data-stu-id="26fe0-191">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="26fe0-192">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="26fe0-192">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="26fe0-193">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26fe0-193">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="26fe0-194">Арифметические операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26fe0-194">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="26fe0-195">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="26fe0-195">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
