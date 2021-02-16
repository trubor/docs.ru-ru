---
description: Дополнительные сведения см. в статье как использовать класс, определяющий операторы (Visual Basic)
title: Практическое руководство. Использование класса, в котором определяются операторы
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 4bf5321fbf1868ad0214d0f4781df30dc8f92ac9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455747"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="137e2-103">Практическое руководство. Использование класса, в котором определяются операторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="137e2-103">How to: Use a Class that Defines Operators (Visual Basic)</span></span>

<span data-ttu-id="137e2-104">При использовании класса или структуры, определяющей собственные операторы, можно получить доступ к этим операторам из Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="137e2-104">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="137e2-105">Определение оператора для класса или структуры также называется *перегрузкой* оператора.</span><span class="sxs-lookup"><span data-stu-id="137e2-105">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="137e2-106">Пример</span><span class="sxs-lookup"><span data-stu-id="137e2-106">Example</span></span>  

 <span data-ttu-id="137e2-107">В следующем примере осуществляется доступ к структуре SQL <xref:System.Data.SqlTypes.SqlString> , которая определяет операторы преобразования ([Функция CType](../../../language-reference/functions/ctype-function.md)) в обоих направлениях между строкой SQL и строкой Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="137e2-107">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="137e2-108">Используйте `CType(` *строковое выражение SQL*, `String)` чтобы преобразовать строку SQL в Visual Basic строку и `CType(` *Visual Basic строковое выражение* <xref:System.Data.SqlTypes.SqlString> `)` для преобразования в другом направлении.</span><span class="sxs-lookup"><span data-stu-id="137e2-108">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="137e2-109"><xref:System.Data.SqlTypes.SqlString>Структура определяет оператор преобразования ([Функция CType](../../../language-reference/functions/ctype-function.md)) из `String` в <xref:System.Data.SqlTypes.SqlString> и другой из <xref:System.Data.SqlTypes.SqlString> в `String` .</span><span class="sxs-lookup"><span data-stu-id="137e2-109">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="137e2-110">Инструкция, которая назначается `title` для `jobTitle` использования первого оператора, а <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> вызов функции использует второй.</span><span class="sxs-lookup"><span data-stu-id="137e2-110">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="137e2-111">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="137e2-111">Compile the code</span></span>  

 <span data-ttu-id="137e2-112">Убедитесь, что используемый класс или структура определяет оператор, который вы хотите использовать.</span><span class="sxs-lookup"><span data-stu-id="137e2-112">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="137e2-113">Не следует считать, что класс или структура определили все операторы, доступные для перегрузки.</span><span class="sxs-lookup"><span data-stu-id="137e2-113">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="137e2-114">Список доступных операторов см. в разделе Оператор [operator](../../../language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="137e2-114">For a list of available operators, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="137e2-115">Включите соответствующую `Imports` инструкцию для строки SQL в начало исходного файла (в данном случае <xref:System.Data.SqlTypes> ).</span><span class="sxs-lookup"><span data-stu-id="137e2-115">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="137e2-116">Проект должен содержать ссылки на System. Data и System.XML.</span><span class="sxs-lookup"><span data-stu-id="137e2-116">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137e2-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="137e2-117">See also</span></span>

- [<span data-ttu-id="137e2-118">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="137e2-118">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="137e2-119">Практическое руководство. Определение оператора</span><span class="sxs-lookup"><span data-stu-id="137e2-119">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="137e2-120">Практическое руководство. Определение оператора преобразования</span><span class="sxs-lookup"><span data-stu-id="137e2-120">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="137e2-121">Практическое руководство. Вызов процедуры оператора</span><span class="sxs-lookup"><span data-stu-id="137e2-121">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="137e2-122">Widening</span><span class="sxs-lookup"><span data-stu-id="137e2-122">Widening</span></span>](../../../language-reference/modifiers/widening.md)
- [<span data-ttu-id="137e2-123">Narrowing</span><span class="sxs-lookup"><span data-stu-id="137e2-123">Narrowing</span></span>](../../../language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="137e2-124">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="137e2-124">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="137e2-125">Практическое руководство. Объявление структуры</span><span class="sxs-lookup"><span data-stu-id="137e2-125">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="137e2-126">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="137e2-126">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="137e2-127">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="137e2-127">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
