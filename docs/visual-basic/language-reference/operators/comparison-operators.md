---
description: 'Дополнительные сведения: операторы сравнения (Visual Basic)'
title: Операторы сравнения
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 28eded0cfae54ec83ad9546b801243e4de0e45fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774113"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="180ba-103">Операторы сравнения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="180ba-103">Comparison Operators (Visual Basic)</span></span>

<span data-ttu-id="180ba-104">Ниже приведены операторы сравнения, определенные в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="180ba-104">The following are the comparison operators defined in Visual Basic.</span></span>

 <span data-ttu-id="180ba-105">`<` станции</span><span class="sxs-lookup"><span data-stu-id="180ba-105">`<` operator</span></span>

 <span data-ttu-id="180ba-106">`<=` станции</span><span class="sxs-lookup"><span data-stu-id="180ba-106">`<=` operator</span></span>

 <span data-ttu-id="180ba-107">`>` станции</span><span class="sxs-lookup"><span data-stu-id="180ba-107">`>` operator</span></span>

 <span data-ttu-id="180ba-108">`>=` станции</span><span class="sxs-lookup"><span data-stu-id="180ba-108">`>=` operator</span></span>

 <span data-ttu-id="180ba-109">`=` станции</span><span class="sxs-lookup"><span data-stu-id="180ba-109">`=` operator</span></span>

 <span data-ttu-id="180ba-110">`<>` станции</span><span class="sxs-lookup"><span data-stu-id="180ba-110">`<>` operator</span></span>

 [<span data-ttu-id="180ba-111">Оператор Is</span><span class="sxs-lookup"><span data-stu-id="180ba-111">Is Operator</span></span>](is-operator.md)

 [<span data-ttu-id="180ba-112">Оператор IsNot</span><span class="sxs-lookup"><span data-stu-id="180ba-112">IsNot Operator</span></span>](isnot-operator.md)

 [<span data-ttu-id="180ba-113">Оператор Like</span><span class="sxs-lookup"><span data-stu-id="180ba-113">Like Operator</span></span>](like-operator.md)

 <span data-ttu-id="180ba-114">Эти операторы сравнивают два выражения, чтобы определить, равны ли они, и если нет, то их отличия.</span><span class="sxs-lookup"><span data-stu-id="180ba-114">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="180ba-115">`Is`, `IsNot` и `Like` подробно обсуждаются на отдельных страницах справки.</span><span class="sxs-lookup"><span data-stu-id="180ba-115">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="180ba-116">Реляционные операторы сравнения подробно обсуждаются на этой странице.</span><span class="sxs-lookup"><span data-stu-id="180ba-116">The relational comparison operators are discussed in detail on this page.</span></span>

## <a name="syntax"></a><span data-ttu-id="180ba-117">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="180ba-117">Syntax</span></span>
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="180ba-118">Компоненты</span><span class="sxs-lookup"><span data-stu-id="180ba-118">Parts</span></span>

 `result`  
 <span data-ttu-id="180ba-119">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="180ba-119">Required.</span></span> <span data-ttu-id="180ba-120">`Boolean`Значение, представляющее результат сравнения.</span><span class="sxs-lookup"><span data-stu-id="180ba-120">A `Boolean` value representing the result of the comparison.</span></span>

 <span data-ttu-id="180ba-121">`expression1`, `expression2`</span><span class="sxs-lookup"><span data-stu-id="180ba-121">`expression1`, `expression2`</span></span>  
 <span data-ttu-id="180ba-122">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="180ba-122">Required.</span></span> <span data-ttu-id="180ba-123">Любое выражение.</span><span class="sxs-lookup"><span data-stu-id="180ba-123">Any expression.</span></span>

 `comparisonoperator`  
 <span data-ttu-id="180ba-124">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="180ba-124">Required.</span></span> <span data-ttu-id="180ba-125">Любой оператор реляционного сравнения.</span><span class="sxs-lookup"><span data-stu-id="180ba-125">Any relational comparison operator.</span></span>

 <span data-ttu-id="180ba-126">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="180ba-126">`object1`, `object2`</span></span>  
 <span data-ttu-id="180ba-127">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="180ba-127">Required.</span></span> <span data-ttu-id="180ba-128">Имена ссылочных объектов.</span><span class="sxs-lookup"><span data-stu-id="180ba-128">Any reference object names.</span></span>

 `string`  
 <span data-ttu-id="180ba-129">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="180ba-129">Required.</span></span> <span data-ttu-id="180ba-130">Произвольное выражение `String` .</span><span class="sxs-lookup"><span data-stu-id="180ba-130">Any `String` expression.</span></span>

 `pattern`  
 <span data-ttu-id="180ba-131">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="180ba-131">Required.</span></span> <span data-ttu-id="180ba-132">Любое `String` выражение или диапазон символов.</span><span class="sxs-lookup"><span data-stu-id="180ba-132">Any `String` expression or range of characters.</span></span>

## <a name="remarks"></a><span data-ttu-id="180ba-133">Remarks</span><span class="sxs-lookup"><span data-stu-id="180ba-133">Remarks</span></span>

 <span data-ttu-id="180ba-134">В следующей таблице содержится список реляционных операторов сравнения и условий, определяющих, `result` является ли `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="180ba-134">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>

|<span data-ttu-id="180ba-135">Оператор</span><span class="sxs-lookup"><span data-stu-id="180ba-135">Operator</span></span>|<span data-ttu-id="180ba-136">`True`, если</span><span class="sxs-lookup"><span data-stu-id="180ba-136">`True` if</span></span>|<span data-ttu-id="180ba-137">`False`, если</span><span class="sxs-lookup"><span data-stu-id="180ba-137">`False` if</span></span>|
|--------------|---------------|----------------|
|<span data-ttu-id="180ba-138">`<` (Меньше)</span><span class="sxs-lookup"><span data-stu-id="180ba-138">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|
|<span data-ttu-id="180ba-139">`<=` (Меньше или равно)</span><span class="sxs-lookup"><span data-stu-id="180ba-139">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|
|<span data-ttu-id="180ba-140">`>` (Больше)</span><span class="sxs-lookup"><span data-stu-id="180ba-140">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|
|<span data-ttu-id="180ba-141">`>=` (Больше или равно)</span><span class="sxs-lookup"><span data-stu-id="180ba-141">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|
|<span data-ttu-id="180ba-142">`=` (Равно)</span><span class="sxs-lookup"><span data-stu-id="180ba-142">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|
|<span data-ttu-id="180ba-143">`<>` (Не равно)</span><span class="sxs-lookup"><span data-stu-id="180ba-143">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> <span data-ttu-id="180ba-144">[Оператор =](assignment-operator.md) также используется в качестве оператора присваивания.</span><span class="sxs-lookup"><span data-stu-id="180ba-144">The [= Operator](assignment-operator.md) is also used as an assignment operator.</span></span>

 <span data-ttu-id="180ba-145">`Is`Оператор, `IsNot` оператор и `Like` оператор имеют специальные функции сравнения, отличные от операторов в предыдущей таблице.</span><span class="sxs-lookup"><span data-stu-id="180ba-145">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>

## <a name="comparing-numbers"></a><span data-ttu-id="180ba-146">Сравнение чисел</span><span class="sxs-lookup"><span data-stu-id="180ba-146">Comparing Numbers</span></span>

 <span data-ttu-id="180ba-147">При сравнении выражения типа `Single` с одним из типов `Double` `Single` выражение преобразуется в `Double` .</span><span class="sxs-lookup"><span data-stu-id="180ba-147">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="180ba-148">Это поведение противоположено поведению, обнаруженному в Visual Basic 6.</span><span class="sxs-lookup"><span data-stu-id="180ba-148">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>

 <span data-ttu-id="180ba-149">Аналогично, при сравнении выражения типа `Decimal` с выражением типа `Single` или `Double` `Decimal` выражение преобразуется в тип `Single` или `Double` .</span><span class="sxs-lookup"><span data-stu-id="180ba-149">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="180ba-150">Для `Decimal` выражений любое значение дробной части меньше 1E-28 может быть потеряно.</span><span class="sxs-lookup"><span data-stu-id="180ba-150">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="180ba-151">Такая утрата дробных значений может привести к тому, что два значения будут сравниваться как равные, если это не так.</span><span class="sxs-lookup"><span data-stu-id="180ba-151">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="180ba-152">По этой причине следует соблюдать осторожность при использовании равенства ( `=` ) для сравнения двух переменных с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="180ba-152">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="180ba-153">Безопаснее проверить, является ли абсолютное значение разницы между двумя числами меньше, чем небольшая допустимая погрешность.</span><span class="sxs-lookup"><span data-stu-id="180ba-153">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>

### <a name="floating-point-imprecision"></a><span data-ttu-id="180ba-154">Точность чисел с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="180ba-154">Floating-point Imprecision</span></span>

 <span data-ttu-id="180ba-155">При работе с числами с плавающей запятой следует помнить, что они не всегда имеют точное представление в памяти.</span><span class="sxs-lookup"><span data-stu-id="180ba-155">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="180ba-156">Это может привести к непредвиденным результатам некоторых операций, таких как сравнение значений и [оператор Mod](mod-operator.md).</span><span class="sxs-lookup"><span data-stu-id="180ba-156">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](mod-operator.md).</span></span> <span data-ttu-id="180ba-157">Дополнительные сведения см. в разделе [Устранение неполадок типов данных](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="180ba-157">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="comparing-strings"></a><span data-ttu-id="180ba-158">Сравнение строк</span><span class="sxs-lookup"><span data-stu-id="180ba-158">Comparing Strings</span></span>

 <span data-ttu-id="180ba-159">При сравнении строк строковые выражения оцениваются на основе их порядка сортировки в алфавитном порядке, который зависит от `Option Compare` параметра.</span><span class="sxs-lookup"><span data-stu-id="180ba-159">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>

 <span data-ttu-id="180ba-160">`Option Compare Binary` базовые сравнения строк в порядке сортировки, производном от внутренних двоичных представлений символов.</span><span class="sxs-lookup"><span data-stu-id="180ba-160">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="180ba-161">Порядок сортировки определяется кодовой страницей.</span><span class="sxs-lookup"><span data-stu-id="180ba-161">The sort order is determined by the code page.</span></span> <span data-ttu-id="180ba-162">В следующем примере показан типичный порядок двоичной сортировки.</span><span class="sxs-lookup"><span data-stu-id="180ba-162">The following example shows a typical binary sort order.</span></span>

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 <span data-ttu-id="180ba-163">`Option Compare Text` сравнения строк при сравнении без учета регистра, порядок сортировки текста определяется языковым стандартом приложения.</span><span class="sxs-lookup"><span data-stu-id="180ba-163">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="180ba-164">При задании `Option Compare Text` и сортировке символов в предыдущем примере применяется следующий порядок сортировки текста:</span><span class="sxs-lookup"><span data-stu-id="180ba-164">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a><span data-ttu-id="180ba-165">Зависимость от локали</span><span class="sxs-lookup"><span data-stu-id="180ba-165">Locale Dependence</span></span>

 <span data-ttu-id="180ba-166">При установке `Option Compare Text` результат сравнения строк может зависеть от языкового стандарта, в котором выполняется приложение.</span><span class="sxs-lookup"><span data-stu-id="180ba-166">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="180ba-167">Два символа могут сравниваться как одинаковые в одном языковом стандарте, но не в другом.</span><span class="sxs-lookup"><span data-stu-id="180ba-167">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="180ba-168">Если вы используете сравнение строк для принятия важных решений, например, принимаете ли вы попытку входа в систему, вы должны быть извещены о конфиденциальности языкового стандарта.</span><span class="sxs-lookup"><span data-stu-id="180ba-168">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="180ba-169">Рекомендуется либо задать `Option Compare Binary` , либо вызвать метод <xref:Microsoft.VisualBasic.Strings.StrComp%2A> , который учитывает языковой стандарт.</span><span class="sxs-lookup"><span data-stu-id="180ba-169">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>

## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="180ba-170">Программирование без типов с помощью реляционных операторов сравнения</span><span class="sxs-lookup"><span data-stu-id="180ba-170">Typeless Programming with Relational Comparison Operators</span></span>

 <span data-ttu-id="180ba-171">Использование реляционных операторов сравнения с `Object` выражениями не допускается в `Option Strict On` .</span><span class="sxs-lookup"><span data-stu-id="180ba-171">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="180ba-172">Если `Option Strict` имеет значение `Off` , а `expression1` либо `expression2` является `Object` выражением, типы времени выполнения определяют, как они сравниваются.</span><span class="sxs-lookup"><span data-stu-id="180ba-172">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="180ba-173">В следующей таблице показано, как сравниваются выражения и результат сравнения, в зависимости от типа операндов среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="180ba-173">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>

|<span data-ttu-id="180ba-174">Если операнды</span><span class="sxs-lookup"><span data-stu-id="180ba-174">If operands are</span></span>|<span data-ttu-id="180ba-175">Сравнение:</span><span class="sxs-lookup"><span data-stu-id="180ba-175">Comparison is</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="180ba-176">Как `String`</span><span class="sxs-lookup"><span data-stu-id="180ba-176">Both `String`</span></span>|<span data-ttu-id="180ba-177">Сравнение сортировки на основе характеристик сортировки строк.</span><span class="sxs-lookup"><span data-stu-id="180ba-177">Sort comparison based on string sorting characteristics.</span></span>|
|<span data-ttu-id="180ba-178">Оба числовых</span><span class="sxs-lookup"><span data-stu-id="180ba-178">Both numeric</span></span>|<span data-ttu-id="180ba-179">Объекты, преобразованные в `Double` , числовое сравнение.</span><span class="sxs-lookup"><span data-stu-id="180ba-179">Objects converted to `Double`, numeric comparison.</span></span>|
|<span data-ttu-id="180ba-180">Один числовой и один `String`</span><span class="sxs-lookup"><span data-stu-id="180ba-180">One numeric and one `String`</span></span>|<span data-ttu-id="180ba-181">`String`Преобразуется в `Double` и выполняется числовое сравнение.</span><span class="sxs-lookup"><span data-stu-id="180ba-181">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="180ba-182">Если объект `String` не может быть преобразован в `Double` , <xref:System.InvalidCastException> создается исключение.</span><span class="sxs-lookup"><span data-stu-id="180ba-182">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|
|<span data-ttu-id="180ba-183">Один или оба являются ссылочными типами, отличными от `String`</span><span class="sxs-lookup"><span data-stu-id="180ba-183">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="180ba-184">Возникает исключение <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="180ba-184">An <xref:System.InvalidCastException> is thrown.</span></span>|

 <span data-ttu-id="180ba-185">Числовые сравнения обрабатываются `Nothing` как 0.</span><span class="sxs-lookup"><span data-stu-id="180ba-185">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="180ba-186">Сравнения строк обрабатываются `Nothing` как `""` (пустая строка).</span><span class="sxs-lookup"><span data-stu-id="180ba-186">String comparisons treat `Nothing` as `""` (an empty string).</span></span>

## <a name="overloading"></a><span data-ttu-id="180ba-187">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="180ba-187">Overloading</span></span>

 <span data-ttu-id="180ba-188">Реляционные операторы сравнения ( `<` .</span><span class="sxs-lookup"><span data-stu-id="180ba-188">The relational comparison operators (`<`.</span></span> <span data-ttu-id="180ba-189">`<=`, `>` , `>=` , `=` , `<>` ) могут быть *перегружены*. Это означает, что класс или структура могут переопределять их поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="180ba-189">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="180ba-190">Если в коде используются какие-либо из этих операторов в таком классе или структуре, убедитесь, что вы понимаете переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="180ba-190">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="180ba-191">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="180ba-191">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

 <span data-ttu-id="180ba-192">Обратите внимание, что [оператор =](assignment-operator.md) можно перегружать только как оператор реляционного сравнения, а не как оператор присваивания.</span><span class="sxs-lookup"><span data-stu-id="180ba-192">Notice that the [= Operator](assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>

## <a name="example"></a><span data-ttu-id="180ba-193">Пример</span><span class="sxs-lookup"><span data-stu-id="180ba-193">Example</span></span>

 <span data-ttu-id="180ba-194">В следующем примере показаны различные варианты использования реляционных операторов сравнения, которые используются для сравнения выражений.</span><span class="sxs-lookup"><span data-stu-id="180ba-194">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="180ba-195">Реляционные операторы сравнения возвращают `Boolean` результат, который представляет, принимает ли указанное выражение значение `True` .</span><span class="sxs-lookup"><span data-stu-id="180ba-195">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="180ba-196">При применении `>` `<` операторов and к строкам сравнение выполняется с использованием обычного алфавитного порядка сортировки строк.</span><span class="sxs-lookup"><span data-stu-id="180ba-196">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="180ba-197">Этот порядок может зависеть от настроек языкового стандарта.</span><span class="sxs-lookup"><span data-stu-id="180ba-197">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="180ba-198">Учитывается ли сортировка с учетом регистра или не зависит от параметра [параметра Compare](../statements/option-compare-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="180ba-198">Whether the sort is case-sensitive or not depends on the [Option Compare](../statements/option-compare-statement.md) setting.</span></span>

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 <span data-ttu-id="180ba-199">В предыдущем примере первое сравнение возвращает, `False` а оставшиеся сравнения возвращают `True` .</span><span class="sxs-lookup"><span data-stu-id="180ba-199">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>

## <a name="see-also"></a><span data-ttu-id="180ba-200">См. также</span><span class="sxs-lookup"><span data-stu-id="180ba-200">See also</span></span>

- <xref:System.InvalidCastException>
- [<span data-ttu-id="180ba-201">Оператор =</span><span class="sxs-lookup"><span data-stu-id="180ba-201">= Operator</span></span>](assignment-operator.md)
- [<span data-ttu-id="180ba-202">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="180ba-202">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="180ba-203">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="180ba-203">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="180ba-204">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="180ba-204">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="180ba-205">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="180ba-205">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
