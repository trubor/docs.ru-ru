---
description: 'Дополнительные сведения о:  <<= operator (Visual Basic)'
title: Оператор <<=
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: 40d0b69c3af672383230db5beadbcd3f3391db7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665644"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="bb396-103">\<\<Оператор = (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb396-103">\<\<= Operator (Visual Basic)</span></span>

<span data-ttu-id="bb396-104">Выполняет арифметическое смещение влево для значения переменной или свойства и присваивает результат переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="bb396-104">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb396-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bb396-105">Syntax</span></span>  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="bb396-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="bb396-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="bb396-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="bb396-107">Required.</span></span> <span data-ttu-id="bb396-108">Переменная или свойство целочисленного типа ( `SByte` ,, `Byte` , `Short` , `UShort` `Integer` , `UInteger` , `Long` или `ULong` ).</span><span class="sxs-lookup"><span data-stu-id="bb396-108">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="bb396-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="bb396-109">Required.</span></span> <span data-ttu-id="bb396-110">Числовое выражение типа данных, которое расширяется до `Integer` .</span><span class="sxs-lookup"><span data-stu-id="bb396-110">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb396-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="bb396-111">Remarks</span></span>  

 <span data-ttu-id="bb396-112">Элемент в левой части `<<=` оператора может быть простой скалярной переменной, свойством или элементом массива.</span><span class="sxs-lookup"><span data-stu-id="bb396-112">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="bb396-113">Переменная или свойство не может быть [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="bb396-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="bb396-114">`<<=`Оператор сначала выполняет арифметический сдвиг влево для значения переменной или свойства.</span><span class="sxs-lookup"><span data-stu-id="bb396-114">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="bb396-115">Затем оператор присваивает результат этой операции с переменной или свойством.</span><span class="sxs-lookup"><span data-stu-id="bb396-115">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="bb396-116">Арифметические сдвиги не являются циклическими, то есть биты, сдвинутые за пределы результата, не переносятся на другой конец.</span><span class="sxs-lookup"><span data-stu-id="bb396-116">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="bb396-117">При выполнении арифметического сдвига влево биты, сдвинутые за пределы диапазона результирующего типа данных, отбрасываются, а позиции битов, освобожденные справа, устанавливаются в ноль.</span><span class="sxs-lookup"><span data-stu-id="bb396-117">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="bb396-118">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="bb396-118">Overloading</span></span>  

 <span data-ttu-id="bb396-119">[Оператор<<](left-shift-operator.md) может быть *перегружен*, что означает, что класс или структура может переопределить свое поведение, если операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="bb396-119">The [<< Operator](left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bb396-120">Перегрузка `<<` оператора влияет на поведение `<<=` оператора.</span><span class="sxs-lookup"><span data-stu-id="bb396-120">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="bb396-121">Если ваш код использует `<<=` класс или структуру, перегрузки `<<` , убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="bb396-121">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bb396-122">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bb396-122">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb396-123">Пример</span><span class="sxs-lookup"><span data-stu-id="bb396-123">Example</span></span>  

 <span data-ttu-id="bb396-124">В следующем примере оператор используется `<<=` для сдвига битового шаблона `Integer` переменной влево на указанное значение и присваивает результат переменной.</span><span class="sxs-lookup"><span data-stu-id="bb396-124">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="bb396-125">См. также</span><span class="sxs-lookup"><span data-stu-id="bb396-125">See also</span></span>

- [<span data-ttu-id="bb396-126"> Оператор<< </span><span class="sxs-lookup"><span data-stu-id="bb396-126"><< Operator</span></span>](left-shift-operator.md)
- [<span data-ttu-id="bb396-127">Операторы присваивания</span><span class="sxs-lookup"><span data-stu-id="bb396-127">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="bb396-128">Операторы сдвига битов</span><span class="sxs-lookup"><span data-stu-id="bb396-128">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="bb396-129">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb396-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="bb396-130">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="bb396-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="bb396-131">Операторы</span><span class="sxs-lookup"><span data-stu-id="bb396-131">Statements</span></span>](../../programming-guide/language-features/statements.md)
