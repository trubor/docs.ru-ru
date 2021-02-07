---
description: Дополнительные сведения см. в статье приоритет операторов в Visual Basic
title: Приоритет операторов
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: 7aa4677549328d450834f3a1ecb047d405893f69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665293"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="6402a-103">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6402a-103">Operator Precedence in Visual Basic</span></span>

<span data-ttu-id="6402a-104">Если в выражении встречается несколько операций, каждая часть вычисляется и разрешается в заранее определенном порядке, который называется *приоритетом операторов*.</span><span class="sxs-lookup"><span data-stu-id="6402a-104">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>

## <a name="precedence-rules"></a><span data-ttu-id="6402a-105">Правила приоритета</span><span class="sxs-lookup"><span data-stu-id="6402a-105">Precedence Rules</span></span>

 <span data-ttu-id="6402a-106">Если выражения содержат операторы из более чем одной категории, они оцениваются в соответствии со следующими правилами.</span><span class="sxs-lookup"><span data-stu-id="6402a-106">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>

- <span data-ttu-id="6402a-107">Арифметические и операторы объединения имеют порядок приоритета, описанный в следующем разделе, и имеют более высокий приоритет, чем операторы сравнения, логического и побитового оператора.</span><span class="sxs-lookup"><span data-stu-id="6402a-107">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>

- <span data-ttu-id="6402a-108">Все операторы сравнения имеют одинаковый приоритет, а все имеют более высокий приоритет, чем логические операторы and, но имеют более низкий приоритет, чем операторы арифметического и объединения.</span><span class="sxs-lookup"><span data-stu-id="6402a-108">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>

- <span data-ttu-id="6402a-109">Логические и побитовые операторы имеют порядок приоритета, описанный в следующем разделе, и все имеют более низкий приоритет, чем арифметические операторы, операции объединения и сравнения.</span><span class="sxs-lookup"><span data-stu-id="6402a-109">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>

- <span data-ttu-id="6402a-110">Операторы с одинаковым приоритетом вычисляются слева направо в том порядке, в котором они отображаются в выражении.</span><span class="sxs-lookup"><span data-stu-id="6402a-110">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>

## <a name="precedence-order"></a><span data-ttu-id="6402a-111">Порядок очередности</span><span class="sxs-lookup"><span data-stu-id="6402a-111">Precedence Order</span></span>

 <span data-ttu-id="6402a-112">Операторы оцениваются в следующем порядке приоритета.</span><span class="sxs-lookup"><span data-stu-id="6402a-112">Operators are evaluated in the following order of precedence:</span></span>

### <a name="await-operator"></a><span data-ttu-id="6402a-113">Оператор Await</span><span class="sxs-lookup"><span data-stu-id="6402a-113">Await Operator</span></span>

 <span data-ttu-id="6402a-114">Ожидать</span><span class="sxs-lookup"><span data-stu-id="6402a-114">Await</span></span>

### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="6402a-115">Арифметические и операторы объединения</span><span class="sxs-lookup"><span data-stu-id="6402a-115">Arithmetic and Concatenation Operators</span></span>

 <span data-ttu-id="6402a-116">Возведение в степень ( `^` )</span><span class="sxs-lookup"><span data-stu-id="6402a-116">Exponentiation (`^`)</span></span>

 <span data-ttu-id="6402a-117">Унарное удостоверение и отрицание ( `+` , `–` )</span><span class="sxs-lookup"><span data-stu-id="6402a-117">Unary identity and negation (`+`, `–`)</span></span>

 <span data-ttu-id="6402a-118">Умножение и деление с плавающей запятой ( `*` , `/` )</span><span class="sxs-lookup"><span data-stu-id="6402a-118">Multiplication and floating-point division (`*`, `/`)</span></span>

 <span data-ttu-id="6402a-119">Целочисленное деление ( `\` )</span><span class="sxs-lookup"><span data-stu-id="6402a-119">Integer division (`\`)</span></span>

 <span data-ttu-id="6402a-120">Модульная арифметика ( `Mod` )</span><span class="sxs-lookup"><span data-stu-id="6402a-120">Modular arithmetic (`Mod`)</span></span>

 <span data-ttu-id="6402a-121">Сложение и вычитание ( `+` , `–` )</span><span class="sxs-lookup"><span data-stu-id="6402a-121">Addition and subtraction (`+`, `–`)</span></span>

 <span data-ttu-id="6402a-122">Объединение строк ( `&` )</span><span class="sxs-lookup"><span data-stu-id="6402a-122">String concatenation (`&`)</span></span>

 <span data-ttu-id="6402a-123">Арифметический сдвиг битов ( `<<` , `>>` )</span><span class="sxs-lookup"><span data-stu-id="6402a-123">Arithmetic bit shift (`<<`, `>>`)</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="6402a-124">Операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="6402a-124">Comparison Operators</span></span>

 <span data-ttu-id="6402a-125">Все операторы сравнения ( `=` , `<>` , `<` , `<=` , `>` , `>=` , `Is` , `IsNot` , `Like` , `TypeOf` ... `Is` )</span><span class="sxs-lookup"><span data-stu-id="6402a-125">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>

### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="6402a-126">Логические и побитовые операторы</span><span class="sxs-lookup"><span data-stu-id="6402a-126">Logical and Bitwise Operators</span></span>

 <span data-ttu-id="6402a-127">Отрицание ( `Not` )</span><span class="sxs-lookup"><span data-stu-id="6402a-127">Negation (`Not`)</span></span>

 <span data-ttu-id="6402a-128">Умножение ( `And` , `AndAlso` )</span><span class="sxs-lookup"><span data-stu-id="6402a-128">Conjunction (`And`, `AndAlso`)</span></span>

 <span data-ttu-id="6402a-129">Включающее сложение ( `Or` , `OrElse` )</span><span class="sxs-lookup"><span data-stu-id="6402a-129">Inclusive disjunction (`Or`, `OrElse`)</span></span>

 <span data-ttu-id="6402a-130">Эксклюзивное сложение ( `Xor` )</span><span class="sxs-lookup"><span data-stu-id="6402a-130">Exclusive disjunction (`Xor`)</span></span>

### <a name="comments"></a><span data-ttu-id="6402a-131">Комментарии</span><span class="sxs-lookup"><span data-stu-id="6402a-131">Comments</span></span>

 <span data-ttu-id="6402a-132">`=`Оператор является только оператором сравнения на равенство, а не оператором присваивания.</span><span class="sxs-lookup"><span data-stu-id="6402a-132">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="6402a-133">Оператор объединения строк ( `&` ) не является арифметическим оператором, но в приоритете он сгруппирован с арифметическими операторами.</span><span class="sxs-lookup"><span data-stu-id="6402a-133">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>

 <span data-ttu-id="6402a-134">`Is`Операторы и `IsNot` являются операторами сравнения ссылок на объекты.</span><span class="sxs-lookup"><span data-stu-id="6402a-134">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="6402a-135">Они не сравнивают значения двух объектов; они только определяют, ссылаются ли две объектные переменные на один и тот же экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="6402a-135">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>

## <a name="associativity"></a><span data-ttu-id="6402a-136">Ассоциативность</span><span class="sxs-lookup"><span data-stu-id="6402a-136">Associativity</span></span>

 <span data-ttu-id="6402a-137">Если операторы с одинаковым приоритетом отображаются вместе в выражении, например умножение и деление, компилятор вычисляет каждую операцию в том виде, в котором она встретилась слева направо.</span><span class="sxs-lookup"><span data-stu-id="6402a-137">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="6402a-138">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6402a-138">The following example illustrates this.</span></span>

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 <span data-ttu-id="6402a-139">Первое выражение вычисляет деление 96/8 (что приводит к 12), а затем деление на 12/4, что приводит к трем.</span><span class="sxs-lookup"><span data-stu-id="6402a-139">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="6402a-140">Поскольку компилятор вычисляет операции в `n1` порядке слева направо, вычисление будет таким же, когда порядок явно указан для `n2` .</span><span class="sxs-lookup"><span data-stu-id="6402a-140">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="6402a-141">`n1`И `n2` имеют результат 3.</span><span class="sxs-lookup"><span data-stu-id="6402a-141">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="6402a-142">В отличие от, `n3` имеет результат 48, так как круглые скобки передают компилятору сначала выполнить оценку 8/4.</span><span class="sxs-lookup"><span data-stu-id="6402a-142">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>

 <span data-ttu-id="6402a-143">Из-за такого поведения операторы говорят о том, что в Visual Basic не используется *ассоциативность* .</span><span class="sxs-lookup"><span data-stu-id="6402a-143">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>

## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="6402a-144">Переопределение приоритета и ассоциативности</span><span class="sxs-lookup"><span data-stu-id="6402a-144">Overriding Precedence and Associativity</span></span>

 <span data-ttu-id="6402a-145">Можно использовать круглые скобки, чтобы принудительно вычислить некоторые части выражения перед другими.</span><span class="sxs-lookup"><span data-stu-id="6402a-145">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="6402a-146">Это может переопределять порядок приоритета и левую ассоциативность.</span><span class="sxs-lookup"><span data-stu-id="6402a-146">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="6402a-147">Visual Basic всегда выполняет операции, заключенные в круглые скобки, прежде чем они выходят за пределы.</span><span class="sxs-lookup"><span data-stu-id="6402a-147">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="6402a-148">Однако в круглых скобках он поддерживает обычный приоритет и ассоциативность, если в круглых скобках не используются скобки.</span><span class="sxs-lookup"><span data-stu-id="6402a-148">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="6402a-149">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6402a-149">The following example illustrates this.</span></span>

```vb
Dim a, b, c, d, e, f, g As Double
a = 8.0
b = 3.0
c = 4.0
d = 2.0
e = 1.0
f = a - b + c / d * e
' The preceding line sets f to 7.0. Because of natural operator
' precedence and associativity, it is exactly equivalent to the
' following line.
f = (a - b) + ((c / d) * e)
' The following line overrides the natural operator precedence
' and left associativity.
g = (a - (b + c)) / (d * e)
' The preceding line sets g to 0.5.
```

## <a name="see-also"></a><span data-ttu-id="6402a-150">См. также</span><span class="sxs-lookup"><span data-stu-id="6402a-150">See also</span></span>

- [<span data-ttu-id="6402a-151">Оператор =</span><span class="sxs-lookup"><span data-stu-id="6402a-151">= Operator</span></span>](assignment-operator.md)
- [<span data-ttu-id="6402a-152">Оператор Is</span><span class="sxs-lookup"><span data-stu-id="6402a-152">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="6402a-153">Оператор IsNot</span><span class="sxs-lookup"><span data-stu-id="6402a-153">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="6402a-154">Оператор Like</span><span class="sxs-lookup"><span data-stu-id="6402a-154">Like Operator</span></span>](like-operator.md)
- [<span data-ttu-id="6402a-155">Оператор TypeOf</span><span class="sxs-lookup"><span data-stu-id="6402a-155">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="6402a-156">Оператор Await</span><span class="sxs-lookup"><span data-stu-id="6402a-156">Await Operator</span></span>](await-operator.md)
- [<span data-ttu-id="6402a-157">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="6402a-157">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="6402a-158">Операторы и выражения</span><span class="sxs-lookup"><span data-stu-id="6402a-158">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
