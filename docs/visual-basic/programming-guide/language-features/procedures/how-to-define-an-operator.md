---
description: 'Дополнительные сведения о: инструкции: определение оператора (Visual Basic)'
title: Практическое руководство. Определение оператора
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: ead96a302426c6f5b1667bb030aab56afe3284c8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462715"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="a7882-103">Практическое руководство. Определение оператора (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7882-103">How to: Define an Operator (Visual Basic)</span></span>

<span data-ttu-id="a7882-104">Если вы определили класс или структуру, то можете определить поведение стандартного оператора (такого как `*` , `<>` или `And` ), если один или оба операнда имеют тип класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="a7882-104">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="a7882-105">Определите стандартный оператор в качестве процедуры оператора внутри класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="a7882-105">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="a7882-106">Все процедуры оператора должны иметь `Public` `Shared` .</span><span class="sxs-lookup"><span data-stu-id="a7882-106">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="a7882-107">Определение оператора для класса или структуры также называется *перегрузкой* оператора.</span><span class="sxs-lookup"><span data-stu-id="a7882-107">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7882-108">Пример</span><span class="sxs-lookup"><span data-stu-id="a7882-108">Example</span></span>  

 <span data-ttu-id="a7882-109">В следующем примере определяется `+` оператор для структуры с именем `height` .</span><span class="sxs-lookup"><span data-stu-id="a7882-109">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="a7882-110">Структура использует высоту, измеряемую в футах и дюймах.</span><span class="sxs-lookup"><span data-stu-id="a7882-110">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="a7882-111">Один *дюйм* — 2,54 сантиметра, а *одна —* 12 дюймов.</span><span class="sxs-lookup"><span data-stu-id="a7882-111">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="a7882-112">Чтобы обеспечить нормализованные значения (дюймы < 12,0), конструктор выполняет арифметический расчет по *модулю* 12.</span><span class="sxs-lookup"><span data-stu-id="a7882-112">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="a7882-113">`+`Оператор использует конструктор для создания нормализованных значений.</span><span class="sxs-lookup"><span data-stu-id="a7882-113">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="a7882-114">Структуру можно проверить `height` с помощью следующего кода.</span><span class="sxs-lookup"><span data-stu-id="a7882-114">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="a7882-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a7882-115">See also</span></span>

- [<span data-ttu-id="a7882-116">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="a7882-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a7882-117">Практическое руководство. Определение оператора преобразования</span><span class="sxs-lookup"><span data-stu-id="a7882-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="a7882-118">Практическое руководство. Вызов процедуры оператора</span><span class="sxs-lookup"><span data-stu-id="a7882-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="a7882-119">Практическое руководство. Использование класса, в котором определяются операторы</span><span class="sxs-lookup"><span data-stu-id="a7882-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="a7882-120">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="a7882-120">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="a7882-121">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="a7882-121">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="a7882-122">Практическое руководство. Объявление структуры</span><span class="sxs-lookup"><span data-stu-id="a7882-122">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="a7882-123">Оператор Mod</span><span class="sxs-lookup"><span data-stu-id="a7882-123">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)
