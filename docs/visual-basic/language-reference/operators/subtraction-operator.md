---
description: Дополнительные сведения об операторе:-operator (Visual Basic)
title: '- Оператор'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 858e887fa7c5c0cc6129996c98bddb78bc53045c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795265"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="1be3c-103">Оператор - (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1be3c-103">- Operator (Visual Basic)</span></span>

<span data-ttu-id="1be3c-104">Возвращает разность между двумя числовыми выражениями или отрицательным значением числового выражения.</span><span class="sxs-lookup"><span data-stu-id="1be3c-104">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1be3c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1be3c-105">Syntax</span></span>  
  
```vb  
expression1 – expression2
```
  
<span data-ttu-id="1be3c-106">or</span><span class="sxs-lookup"><span data-stu-id="1be3c-106">or</span></span>

```vb  
–expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="1be3c-107">Компоненты</span><span class="sxs-lookup"><span data-stu-id="1be3c-107">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="1be3c-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="1be3c-108">Required.</span></span> <span data-ttu-id="1be3c-109">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="1be3c-109">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="1be3c-110">Требуется, если `–` оператор не вычисляет отрицательное значение.</span><span class="sxs-lookup"><span data-stu-id="1be3c-110">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="1be3c-111">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="1be3c-111">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="1be3c-112">Результат</span><span class="sxs-lookup"><span data-stu-id="1be3c-112">Result</span></span>  

 <span data-ttu-id="1be3c-113">Результатом является разница между `expression1` и `expression2` или отрицательным значением `expression1` .</span><span class="sxs-lookup"><span data-stu-id="1be3c-113">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="1be3c-114">Тип данных result является числовым типом, подходящим для типов данных `expression1` и `expression2` .</span><span class="sxs-lookup"><span data-stu-id="1be3c-114">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="1be3c-115">См. таблицу "целочисленные арифметические операции" в [типах данных результатов операторов](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="1be3c-115">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="1be3c-116">Поддерживаемые типы</span><span class="sxs-lookup"><span data-stu-id="1be3c-116">Supported Types</span></span>  

 <span data-ttu-id="1be3c-117">все числовые типы.</span><span class="sxs-lookup"><span data-stu-id="1be3c-117">All numeric types.</span></span> <span data-ttu-id="1be3c-118">К ним относятся типы без знака и тип с плавающей запятой и `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="1be3c-118">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1be3c-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="1be3c-119">Remarks</span></span>  

 <span data-ttu-id="1be3c-120">При первом использовании, показанном в приведенном выше синтаксисе, `–` оператор является *бинарным* арифметическим оператором вычитания для разности двух числовых выражений.</span><span class="sxs-lookup"><span data-stu-id="1be3c-120">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="1be3c-121">Во втором описании синтаксиса, показанного ранее, `–` оператор является *унарным* оператором отрицания для отрицательного значения выражения.</span><span class="sxs-lookup"><span data-stu-id="1be3c-121">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="1be3c-122">В этом смысле отрицание состоит в обратном знаке, `expression1` чтобы результат был положительным, если `expression1` является отрицательным.</span><span class="sxs-lookup"><span data-stu-id="1be3c-122">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="1be3c-123">Если любое из выражений имеет значение [Nothing](../nothing.md), `–` оператор обрабатывает его как ноль.</span><span class="sxs-lookup"><span data-stu-id="1be3c-123">If either expression evaluates to [Nothing](../nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1be3c-124">`–`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="1be3c-124">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1be3c-125">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="1be3c-125">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="1be3c-126">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1be3c-126">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1be3c-127">Пример</span><span class="sxs-lookup"><span data-stu-id="1be3c-127">Example</span></span>  

 <span data-ttu-id="1be3c-128">В следующем примере оператор используется `–` для вычисления и возврата разницы между двумя числами, а затем для отрицания числа.</span><span class="sxs-lookup"><span data-stu-id="1be3c-128">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="1be3c-129">После выполнения этих инструкций `binaryResult` содержит 124,45 и `unaryResult` содержит – 334,90.</span><span class="sxs-lookup"><span data-stu-id="1be3c-129">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be3c-130">См. также</span><span class="sxs-lookup"><span data-stu-id="1be3c-130">See also</span></span>

- [<span data-ttu-id="1be3c-131">Оператор-= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1be3c-131">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="1be3c-132">Арифметические операторы</span><span class="sxs-lookup"><span data-stu-id="1be3c-132">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="1be3c-133">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1be3c-133">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="1be3c-134">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="1be3c-134">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="1be3c-135">Арифметические операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1be3c-135">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
