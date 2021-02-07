---
description: Дополнительные сведения о операторе:/(Visual Basic)
title: Оператор /
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: 717c8fdc6abae02de555040a3aadb92fed2bfbee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666008"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="95a5e-103">Оператор / (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95a5e-103">/ Operator (Visual Basic)</span></span>

<span data-ttu-id="95a5e-104">Делит одно число на другое и возвращает результат в виде числа с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="95a5e-104">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a5e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="95a5e-105">Syntax</span></span>  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="95a5e-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="95a5e-106">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="95a5e-107">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="95a5e-107">Required.</span></span> <span data-ttu-id="95a5e-108">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="95a5e-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="95a5e-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="95a5e-109">Required.</span></span> <span data-ttu-id="95a5e-110">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="95a5e-110">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="95a5e-111">Поддерживаемые типы</span><span class="sxs-lookup"><span data-stu-id="95a5e-111">Supported Types</span></span>  

 <span data-ttu-id="95a5e-112">Все числовые типы, включая неподписанные и типы с плавающей запятой, и `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="95a5e-112">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="95a5e-113">Результат</span><span class="sxs-lookup"><span data-stu-id="95a5e-113">Result</span></span>  

 <span data-ttu-id="95a5e-114">Результатом является полное частное от деления на `expression1` `expression2` , включая остаток.</span><span class="sxs-lookup"><span data-stu-id="95a5e-114">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="95a5e-115">[Оператор \ (Visual Basic)](integer-division-operator.md) возвращает целочисленное частное, которое удаляет остаток.</span><span class="sxs-lookup"><span data-stu-id="95a5e-115">The [\ Operator (Visual Basic)](integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95a5e-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="95a5e-116">Remarks</span></span>  

 <span data-ttu-id="95a5e-117">Тип данных результата зависит от типов операндов.</span><span class="sxs-lookup"><span data-stu-id="95a5e-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="95a5e-118">В следующей таблице показано, как определяется тип данных результата.</span><span class="sxs-lookup"><span data-stu-id="95a5e-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="95a5e-119">Типы данных операндов</span><span class="sxs-lookup"><span data-stu-id="95a5e-119">Operand data types</span></span>|<span data-ttu-id="95a5e-120">Тип данных результата</span><span class="sxs-lookup"><span data-stu-id="95a5e-120">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="95a5e-121">Оба выражения являются целочисленными типами данных ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ulong](../data-types/ulong-data-type.md)).</span><span class="sxs-lookup"><span data-stu-id="95a5e-121">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="95a5e-122">Одно выражение имеет [один](../data-types/single-data-type.md) тип данных, а другой — не [Double](../data-types/double-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="95a5e-122">One expression is a [Single](../data-types/single-data-type.md) data type and the other is not a [Double](../data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="95a5e-123">Одно выражение имеет тип данных [Decimal](../data-types/decimal-data-type.md) , а второй не является [одиночным](../data-types/single-data-type.md) или [double](../data-types/double-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="95a5e-123">One expression is a [Decimal](../data-types/decimal-data-type.md) data type and the other is not a [Single](../data-types/single-data-type.md) or a [Double](../data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="95a5e-124">Любое выражение является типом данных [Double](../data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="95a5e-124">Either expression is a [Double](../data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="95a5e-125">Перед выполнением деления все целочисленные числовые выражения расширяются до `Double` .</span><span class="sxs-lookup"><span data-stu-id="95a5e-125">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="95a5e-126">Если результат присваивается целочисленному типу данных, Visual Basic пытается преобразовать результат из `Double` в этот тип.</span><span class="sxs-lookup"><span data-stu-id="95a5e-126">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="95a5e-127">Это может вызвать исключение, если результат не умещается в этом типе.</span><span class="sxs-lookup"><span data-stu-id="95a5e-127">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="95a5e-128">В частности, см. раздел "попыток деления на ноль" на этой странице справки.</span><span class="sxs-lookup"><span data-stu-id="95a5e-128">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="95a5e-129">Если `expression1` или `expression2` имеет значение [Nothing](../nothing.md), оно считается нулевым.</span><span class="sxs-lookup"><span data-stu-id="95a5e-129">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="95a5e-130">Попыток деления на ноль</span><span class="sxs-lookup"><span data-stu-id="95a5e-130">Attempted Division by Zero</span></span>  

 <span data-ttu-id="95a5e-131">Если `expression2` значение равно нулю, `/` оператор ведет себя по-разному для разных типов данных операндов.</span><span class="sxs-lookup"><span data-stu-id="95a5e-131">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="95a5e-132">В следующей таблице показаны возможные варианты поведения.</span><span class="sxs-lookup"><span data-stu-id="95a5e-132">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="95a5e-133">Типы данных операндов</span><span class="sxs-lookup"><span data-stu-id="95a5e-133">Operand data types</span></span>|<span data-ttu-id="95a5e-134">Поведение `expression2` , если равно нулю</span><span class="sxs-lookup"><span data-stu-id="95a5e-134">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="95a5e-135">С плавающей запятой ( `Single` или `Double` )</span><span class="sxs-lookup"><span data-stu-id="95a5e-135">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="95a5e-136">Возвращает бесконечное значение ( <xref:System.Double.PositiveInfinity> или <xref:System.Double.NegativeInfinity> ) или <xref:System.Double.NaN> (не число), если `expression1` равно нулю</span><span class="sxs-lookup"><span data-stu-id="95a5e-136">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="95a5e-137">Создает <xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="95a5e-137">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="95a5e-138">Интеграл (со знаком или без знака)</span><span class="sxs-lookup"><span data-stu-id="95a5e-138">Integral (signed or unsigned)</span></span>|<span data-ttu-id="95a5e-139">Попытка преобразования обратно в целочисленный тип вызывается <xref:System.OverflowException> из-за того, что целочисленные типы не могут принимать <xref:System.Double.PositiveInfinity> , <xref:System.Double.NegativeInfinity> или <xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="95a5e-139">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
> <span data-ttu-id="95a5e-140">`/`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="95a5e-140">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="95a5e-141">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="95a5e-141">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="95a5e-142">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="95a5e-142">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95a5e-143">Пример</span><span class="sxs-lookup"><span data-stu-id="95a5e-143">Example</span></span>  

 <span data-ttu-id="95a5e-144">В этом примере `/` оператор используется для выполнения деления с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="95a5e-144">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="95a5e-145">Результатом является частное двух операндов.</span><span class="sxs-lookup"><span data-stu-id="95a5e-145">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 <span data-ttu-id="95a5e-146">Выражения в предыдущем примере возвращают значения 2,5 и 3,333333.</span><span class="sxs-lookup"><span data-stu-id="95a5e-146">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="95a5e-147">Обратите внимание, что результат всегда имеет тип с плавающей запятой ( `Double` ), хотя оба операнда являются целочисленными константами.</span><span class="sxs-lookup"><span data-stu-id="95a5e-147">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a5e-148">См. также</span><span class="sxs-lookup"><span data-stu-id="95a5e-148">See also</span></span>

- [<span data-ttu-id="95a5e-149">Оператор/= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95a5e-149">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="95a5e-150">Оператор \ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95a5e-150">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="95a5e-151">Типы данных результатов оператора</span><span class="sxs-lookup"><span data-stu-id="95a5e-151">Data Types of Operator Results</span></span>](data-types-of-operator-results.md)
- [<span data-ttu-id="95a5e-152">Арифметические операторы</span><span class="sxs-lookup"><span data-stu-id="95a5e-152">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="95a5e-153">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="95a5e-153">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="95a5e-154">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="95a5e-154">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="95a5e-155">Арифметические операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="95a5e-155">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
