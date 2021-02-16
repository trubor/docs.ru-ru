---
description: Дополнительные сведения см. в статье как определить оператор преобразования (Visual Basic)
title: Практическое руководство. Определение оператора преобразования
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: c090e183e809974163625c4bfcf33536b1082b66
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481991"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="4504f-103">Практическое руководство. Определение оператора преобразования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4504f-103">How to: Define a Conversion Operator (Visual Basic)</span></span>

<span data-ttu-id="4504f-104">Если вы определили класс или структуру, можно определить оператор преобразования типа между типом класса или структуры и другим типом данных (например `Integer` ,, `Double` или `String` ).</span><span class="sxs-lookup"><span data-stu-id="4504f-104">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="4504f-105">Определите преобразование типа как процедуру [функции CType](../../../language-reference/functions/ctype-function.md) в классе или структуре.</span><span class="sxs-lookup"><span data-stu-id="4504f-105">Define the type conversion as a [CType Function](../../../language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="4504f-106">Все процедуры преобразования должны иметь `Public Shared` значение, и каждая из них должна указывать [расширение](../../../language-reference/modifiers/widening.md) или [сужение](../../../language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="4504f-106">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../language-reference/modifiers/widening.md) or [Narrowing](../../../language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="4504f-107">Определение оператора для класса или структуры также называется *перегрузкой* оператора.</span><span class="sxs-lookup"><span data-stu-id="4504f-107">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4504f-108">Пример</span><span class="sxs-lookup"><span data-stu-id="4504f-108">Example</span></span>  

 <span data-ttu-id="4504f-109">В следующем примере определяются операторы преобразования между структурой `digit` и `Byte` .</span><span class="sxs-lookup"><span data-stu-id="4504f-109">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="4504f-110">Структуру можно проверить `digit` с помощью следующего кода.</span><span class="sxs-lookup"><span data-stu-id="4504f-110">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="4504f-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4504f-111">See also</span></span>

- [<span data-ttu-id="4504f-112">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="4504f-112">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="4504f-113">Практическое руководство. Определение оператора</span><span class="sxs-lookup"><span data-stu-id="4504f-113">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="4504f-114">Практическое руководство. Вызов процедуры оператора</span><span class="sxs-lookup"><span data-stu-id="4504f-114">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="4504f-115">Практическое руководство. Использование класса, в котором определяются операторы</span><span class="sxs-lookup"><span data-stu-id="4504f-115">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="4504f-116">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="4504f-116">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="4504f-117">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="4504f-117">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="4504f-118">Практическое руководство. Объявление структуры</span><span class="sxs-lookup"><span data-stu-id="4504f-118">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="4504f-119">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="4504f-119">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="4504f-120">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="4504f-120">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
