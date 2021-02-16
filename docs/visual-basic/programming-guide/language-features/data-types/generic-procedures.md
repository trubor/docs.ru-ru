---
description: Дополнительные сведения об общих процедурах см. в Visual Basic
title: Универсальные процедуры
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: c8f26d66f7b657e00382ea94ed0d6093211a3e96
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434710"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="4cafe-103">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4cafe-103">Generic Procedures in Visual Basic</span></span>

<span data-ttu-id="4cafe-104">*Универсальная процедура*, также называемая *универсальным методом*, представляет собой процедуру, определенную по крайней мере с одним параметром типа.</span><span class="sxs-lookup"><span data-stu-id="4cafe-104">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="4cafe-105">Это позволяет вызывающему коду адаптировать типы данных к их требованиям при каждом вызове процедуры.</span><span class="sxs-lookup"><span data-stu-id="4cafe-105">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="4cafe-106">Процедура не является универсальной просто путем определения внутри универсального класса или универсальной структуры.</span><span class="sxs-lookup"><span data-stu-id="4cafe-106">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="4cafe-107">Как универсальное, процедура должна принимать по крайней мере один параметр типа в дополнение к обычным параметрам, которые он может принимать.</span><span class="sxs-lookup"><span data-stu-id="4cafe-107">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="4cafe-108">Универсальный класс или структура может содержать неуниверсальные процедуры, а неуниверсальный класс, структура или модуль могут содержать универсальные процедуры.</span><span class="sxs-lookup"><span data-stu-id="4cafe-108">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="4cafe-109">Универсальная процедура может использовать свои параметры-типы в его стандартном списке параметров, в его возвращаемом типе, если он есть, и в коде процедуры.</span><span class="sxs-lookup"><span data-stu-id="4cafe-109">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="4cafe-110">Вывод типа</span><span class="sxs-lookup"><span data-stu-id="4cafe-110">Type Inference</span></span>  

 <span data-ttu-id="4cafe-111">Можно вызвать универсальную процедуру без указания каких-либо аргументов типа.</span><span class="sxs-lookup"><span data-stu-id="4cafe-111">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="4cafe-112">При таком вызове компилятор пытается определить подходящие типы данных для передачи аргументам типа процедуры.</span><span class="sxs-lookup"><span data-stu-id="4cafe-112">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="4cafe-113">Это называется *выводом типа*.</span><span class="sxs-lookup"><span data-stu-id="4cafe-113">This is called *type inference*.</span></span> <span data-ttu-id="4cafe-114">В следующем коде показан вызов, в котором компилятор определяет, что он должен передать тип `String` в параметр типа `t` .</span><span class="sxs-lookup"><span data-stu-id="4cafe-114">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 <span data-ttu-id="4cafe-115">Если компилятор не может вывести аргументы типа из контекста вызова, он сообщает об ошибке.</span><span class="sxs-lookup"><span data-stu-id="4cafe-115">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="4cafe-116">Одной из возможных причин такой ошибки является несоответствие ранга массива.</span><span class="sxs-lookup"><span data-stu-id="4cafe-116">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="4cafe-117">Например, предположим, что вы определили нормальный параметр в качестве массива параметра типа.</span><span class="sxs-lookup"><span data-stu-id="4cafe-117">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="4cafe-118">При вызове универсальной процедуры, предоставляющей массив другого ранга (число измерений), несоответствие приводит к сбою определения типа.</span><span class="sxs-lookup"><span data-stu-id="4cafe-118">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="4cafe-119">В следующем коде показан вызов, в котором двумерный массив передается в процедуру, которая принимает одномерный массив.</span><span class="sxs-lookup"><span data-stu-id="4cafe-119">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="4cafe-120">Вывод типа можно вызвать только путем пропуска всех аргументов типа.</span><span class="sxs-lookup"><span data-stu-id="4cafe-120">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="4cafe-121">При указании одного аргумента типа необходимо указать все эти аргументы.</span><span class="sxs-lookup"><span data-stu-id="4cafe-121">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="4cafe-122">Вывод типа поддерживается только для универсальных процедур.</span><span class="sxs-lookup"><span data-stu-id="4cafe-122">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="4cafe-123">Невозможно вызвать определение типа в универсальных классах, структурах, интерфейсах или делегатах.</span><span class="sxs-lookup"><span data-stu-id="4cafe-123">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cafe-124">Пример</span><span class="sxs-lookup"><span data-stu-id="4cafe-124">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4cafe-125">Описание</span><span class="sxs-lookup"><span data-stu-id="4cafe-125">Description</span></span>  

 <span data-ttu-id="4cafe-126">В следующем примере определяется универсальная `Function` процедура поиска определенного элемента в массиве.</span><span class="sxs-lookup"><span data-stu-id="4cafe-126">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="4cafe-127">Он определяет один параметр типа и использует его для создания двух параметров в списке параметров.</span><span class="sxs-lookup"><span data-stu-id="4cafe-127">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4cafe-128">Код</span><span class="sxs-lookup"><span data-stu-id="4cafe-128">Code</span></span>  

 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a><span data-ttu-id="4cafe-129">Комментарии</span><span class="sxs-lookup"><span data-stu-id="4cafe-129">Comments</span></span>  

 <span data-ttu-id="4cafe-130">В предыдущем примере требуется возможность сравнения с `searchValue` каждым элементом `searchArray` .</span><span class="sxs-lookup"><span data-stu-id="4cafe-130">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="4cafe-131">Чтобы гарантировать эту возможность, он ограничивает параметр типа `T` для реализации <xref:System.IComparable%601> интерфейса.</span><span class="sxs-lookup"><span data-stu-id="4cafe-131">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="4cafe-132">В коде используется <xref:System.IComparable%601.CompareTo%2A> метод вместо `=` оператора, поскольку нет никакой гарантии, что аргумент типа предоставляется для `T` поддержки `=` оператора.</span><span class="sxs-lookup"><span data-stu-id="4cafe-132">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="4cafe-133">Процедуру можно проверить `findElement` с помощью следующего кода.</span><span class="sxs-lookup"><span data-stu-id="4cafe-133">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 <span data-ttu-id="4cafe-134">Предыдущие вызовы для `MsgBox` отображают "0", "1" и "-1" соответственно.</span><span class="sxs-lookup"><span data-stu-id="4cafe-134">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cafe-135">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4cafe-135">See also</span></span>

- [<span data-ttu-id="4cafe-136">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4cafe-136">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="4cafe-137">Практическое руководство. Определение класса, реализующего одинаковую функциональность для разных типов данных</span><span class="sxs-lookup"><span data-stu-id="4cafe-137">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="4cafe-138">Практическое руководство. Использование универсального класса</span><span class="sxs-lookup"><span data-stu-id="4cafe-138">How to: Use a Generic Class</span></span>](how-to-use-a-generic-class.md)
- [<span data-ttu-id="4cafe-139">Процедуры</span><span class="sxs-lookup"><span data-stu-id="4cafe-139">Procedures</span></span>](../procedures/index.md)
- [<span data-ttu-id="4cafe-140">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="4cafe-140">Procedure Parameters and Arguments</span></span>](../procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="4cafe-141">Type List</span><span class="sxs-lookup"><span data-stu-id="4cafe-141">Type List</span></span>](../../../language-reference/statements/type-list.md)
- [<span data-ttu-id="4cafe-142">Список параметров</span><span class="sxs-lookup"><span data-stu-id="4cafe-142">Parameter List</span></span>](../../../language-reference/statements/parameter-list.md)
