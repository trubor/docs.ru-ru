---
description: 'Дополнительные сведения о операторе: * (Visual Basic)'
title: '* Оператор'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 9a9f7eff9468fd6784b705a50871bc79fd6c1faa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665397"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="f84c9-103">Оператор \* (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f84c9-103">\* Operator (Visual Basic)</span></span>

<span data-ttu-id="f84c9-104">Перемножает два числа.</span><span class="sxs-lookup"><span data-stu-id="f84c9-104">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f84c9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f84c9-105">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="f84c9-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="f84c9-106">Parts</span></span>  
  
|<span data-ttu-id="f84c9-107">Термин</span><span class="sxs-lookup"><span data-stu-id="f84c9-107">Term</span></span>|<span data-ttu-id="f84c9-108">Определение</span><span class="sxs-lookup"><span data-stu-id="f84c9-108">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="f84c9-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="f84c9-109">Required.</span></span> <span data-ttu-id="f84c9-110">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="f84c9-110">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="f84c9-111">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="f84c9-111">Required.</span></span> <span data-ttu-id="f84c9-112">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="f84c9-112">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="f84c9-113">Результат</span><span class="sxs-lookup"><span data-stu-id="f84c9-113">Result</span></span>  

 <span data-ttu-id="f84c9-114">Результатом является произведение `number1` и `number2` .</span><span class="sxs-lookup"><span data-stu-id="f84c9-114">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="f84c9-115">Поддерживаемые типы</span><span class="sxs-lookup"><span data-stu-id="f84c9-115">Supported Types</span></span>  

 <span data-ttu-id="f84c9-116">Все числовые типы, включая неподписанные и типы с плавающей запятой, и `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="f84c9-116">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f84c9-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="f84c9-117">Remarks</span></span>  

 <span data-ttu-id="f84c9-118">Тип данных результата зависит от типов операндов.</span><span class="sxs-lookup"><span data-stu-id="f84c9-118">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="f84c9-119">В следующей таблице показано, как определяется тип данных результата.</span><span class="sxs-lookup"><span data-stu-id="f84c9-119">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="f84c9-120">Типы данных операндов</span><span class="sxs-lookup"><span data-stu-id="f84c9-120">Operand data types</span></span>|<span data-ttu-id="f84c9-121">Тип данных результата</span><span class="sxs-lookup"><span data-stu-id="f84c9-121">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="f84c9-122">Оба выражения являются целочисленными типами данных ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ulong](../data-types/ulong-data-type.md)).</span><span class="sxs-lookup"><span data-stu-id="f84c9-122">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="f84c9-123">Числовой тип данных, подходящий для типов данных `number1` и `number2` .</span><span class="sxs-lookup"><span data-stu-id="f84c9-123">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="f84c9-124">См. таблицу "целочисленные арифметические операции" в [типах данных результатов операторов](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="f84c9-124">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="f84c9-125">Оба выражения являются [десятичными](../data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="f84c9-125">Both expressions are [Decimal](../data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="f84c9-126">Оба выражения являются [одиночными](../data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="f84c9-126">Both expressions are [Single](../data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="f84c9-127">Одно из выражений является типом данных с плавающей запятой ( `Single` или [Double](../data-types/double-data-type.md)), но не оба `Single` (Обратите внимание `Decimal` , что это не тип данных с плавающей запятой).</span><span class="sxs-lookup"><span data-stu-id="f84c9-127">Either expression is a floating-point data type (`Single` or [Double](../data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="f84c9-128">Если выражение принимает значение [Nothing](../nothing.md), оно считается нулевым.</span><span class="sxs-lookup"><span data-stu-id="f84c9-128">If an expression evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f84c9-129">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="f84c9-129">Overloading</span></span>  

 <span data-ttu-id="f84c9-130">`*`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="f84c9-130">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f84c9-131">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="f84c9-131">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f84c9-132">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f84c9-132">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f84c9-133">Пример</span><span class="sxs-lookup"><span data-stu-id="f84c9-133">Example</span></span>  

 <span data-ttu-id="f84c9-134">В этом примере `*` оператор используется для умножения двух чисел.</span><span class="sxs-lookup"><span data-stu-id="f84c9-134">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="f84c9-135">Результатом является произведение двух операндов.</span><span class="sxs-lookup"><span data-stu-id="f84c9-135">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="f84c9-136">См. также</span><span class="sxs-lookup"><span data-stu-id="f84c9-136">See also</span></span>

- [<span data-ttu-id="f84c9-137">Оператор \* =</span><span class="sxs-lookup"><span data-stu-id="f84c9-137">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="f84c9-138">Арифметические операторы</span><span class="sxs-lookup"><span data-stu-id="f84c9-138">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="f84c9-139">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f84c9-139">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f84c9-140">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="f84c9-140">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f84c9-141">Арифметические операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f84c9-141">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
