---
description: 'Дополнительные сведения о:  >>= operator (Visual Basic)'
title: '>>Оператор ='
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: 80f614042403ad9179de0025b289bd83c71008b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795317"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="a184b-103">Оператор >>= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a184b-103">>>= Operator (Visual Basic)</span></span>

<span data-ttu-id="a184b-104">Выполняет арифметическое смещение вправо для значения переменной или свойства и присваивает результат переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="a184b-104">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a184b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a184b-105">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="a184b-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="a184b-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="a184b-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="a184b-107">Required.</span></span> <span data-ttu-id="a184b-108">Переменная или свойство целочисленного типа ( `SByte` ,, `Byte` , `Short` , `UShort` `Integer` , `UInteger` , `Long` или `ULong` ).</span><span class="sxs-lookup"><span data-stu-id="a184b-108">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="a184b-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="a184b-109">Required.</span></span> <span data-ttu-id="a184b-110">Числовое выражение типа данных, которое расширяется до `Integer` .</span><span class="sxs-lookup"><span data-stu-id="a184b-110">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a184b-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a184b-111">Remarks</span></span>  

 <span data-ttu-id="a184b-112">Элемент в левой части `>>=` оператора может быть простой скалярной переменной, свойством или элементом массива.</span><span class="sxs-lookup"><span data-stu-id="a184b-112">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="a184b-113">Переменная или свойство не может быть [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="a184b-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="a184b-114">`>>=`Оператор сначала выполняет арифметический сдвиг значения переменной или свойства вправо.</span><span class="sxs-lookup"><span data-stu-id="a184b-114">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="a184b-115">Затем оператор присваивает результат этой операции с переменной или свойством.</span><span class="sxs-lookup"><span data-stu-id="a184b-115">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="a184b-116">Арифметические сдвиги не являются циклическими, то есть биты, сдвинутые за пределы результата, не переносятся на другой конец.</span><span class="sxs-lookup"><span data-stu-id="a184b-116">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="a184b-117">При арифметическом сдвиге вправо биты, сдвинутые за пределы крайней правой позиции, отбрасываются, а крайний левый бит передается в позиции, освобожденные слева.</span><span class="sxs-lookup"><span data-stu-id="a184b-117">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="a184b-118">Это означает, что если `variableorproperty` имеет отрицательное значение, освобождаемые позиции устанавливаются в единицу.</span><span class="sxs-lookup"><span data-stu-id="a184b-118">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="a184b-119">Если `variableorproperty` имеет положительное значение или тип данных имеет тип без знака, освобождаемые позиции устанавливаются в ноль.</span><span class="sxs-lookup"><span data-stu-id="a184b-119">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a184b-120">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="a184b-120">Overloading</span></span>  

 <span data-ttu-id="a184b-121">[Оператор>>](right-shift-operator.md) может быть *перегружен*, что означает, что класс или структура может переопределить свое поведение, если операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="a184b-121">The [>> Operator](right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a184b-122">Перегрузка `>>` оператора влияет на поведение `>>=` оператора.</span><span class="sxs-lookup"><span data-stu-id="a184b-122">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="a184b-123">Если ваш код использует `>>=` класс или структуру, перегрузки `>>` , убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="a184b-123">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a184b-124">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a184b-124">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a184b-125">Пример</span><span class="sxs-lookup"><span data-stu-id="a184b-125">Example</span></span>  

 <span data-ttu-id="a184b-126">В следующем примере оператор используется `>>=` для сдвига битового шаблона `Integer` переменной вправо на указанное значение и присваивает результат переменной.</span><span class="sxs-lookup"><span data-stu-id="a184b-126">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="a184b-127">См. также</span><span class="sxs-lookup"><span data-stu-id="a184b-127">See also</span></span>

- [<span data-ttu-id="a184b-128"> Оператор>> </span><span class="sxs-lookup"><span data-stu-id="a184b-128">>> Operator</span></span>](right-shift-operator.md)
- [<span data-ttu-id="a184b-129">Операторы присваивания</span><span class="sxs-lookup"><span data-stu-id="a184b-129">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="a184b-130">Операторы сдвига битов</span><span class="sxs-lookup"><span data-stu-id="a184b-130">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="a184b-131">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a184b-131">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="a184b-132">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="a184b-132">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="a184b-133">Операторы</span><span class="sxs-lookup"><span data-stu-id="a184b-133">Statements</span></span>](../../programming-guide/language-features/statements.md)
