---
description: 'Дополнительные сведения: Оператор TryCast (Visual Basic)'
title: Оператор TryCast
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 5b941ec40c4ba0198fced64d0ef039605efad472
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795252"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="3c067-103">Оператор TryCast (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c067-103">TryCast Operator (Visual Basic)</span></span>

<span data-ttu-id="3c067-104">Вводит операцию преобразования типа, которая не создает исключение.</span><span class="sxs-lookup"><span data-stu-id="3c067-104">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c067-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="3c067-105">Remarks</span></span>  

 <span data-ttu-id="3c067-106">Если попытка преобразования завершается неудачно `CType` и возникает `DirectCast` <xref:System.InvalidCastException> ошибка.</span><span class="sxs-lookup"><span data-stu-id="3c067-106">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="3c067-107">Это может негативно сказаться на производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="3c067-107">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="3c067-108">`TryCast`[не возвращает ничего](../nothing.md), поэтому вместо того, чтобы выполнять обработку возможного исключения, необходимо только проверить возвращаемый результат для `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="3c067-108">`TryCast` returns [Nothing](../nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="3c067-109">`TryCast`Ключевое слово используется точно так же, как при использовании [функции CType](../functions/ctype-function.md) и ключевого слова [DirectCast operator](directcast-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="3c067-109">You use the `TryCast` keyword the same way you use the [CType Function](../functions/ctype-function.md) and the [DirectCast Operator](directcast-operator.md) keyword.</span></span> <span data-ttu-id="3c067-110">Укажите выражение в качестве первого аргумента и тип, чтобы преобразовать его в качестве второго аргумента.</span><span class="sxs-lookup"><span data-stu-id="3c067-110">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="3c067-111">`TryCast` работает только со ссылочными типами, такими как классы и интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="3c067-111">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="3c067-112">Для этого требуется отношение наследования или реализации между двумя типами.</span><span class="sxs-lookup"><span data-stu-id="3c067-112">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="3c067-113">Это означает, что один тип должен наследовать или реализовывать другой.</span><span class="sxs-lookup"><span data-stu-id="3c067-113">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="3c067-114">Ошибки и сбои</span><span class="sxs-lookup"><span data-stu-id="3c067-114">Errors and Failures</span></span>  

 <span data-ttu-id="3c067-115">`TryCast` выдает ошибку компилятора, если обнаруживается, что связь наследования или реализации не существует.</span><span class="sxs-lookup"><span data-stu-id="3c067-115">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="3c067-116">Но отсутствие ошибки компилятора не гарантирует успешного преобразования.</span><span class="sxs-lookup"><span data-stu-id="3c067-116">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="3c067-117">Если требуемое преобразование является узким, оно может привести к сбою во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="3c067-117">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="3c067-118">Если это происходит, `TryCast` возвращает [Nothing](../nothing.md).</span><span class="sxs-lookup"><span data-stu-id="3c067-118">If this happens, `TryCast` returns [Nothing](../nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="3c067-119">Ключевые слова преобразований</span><span class="sxs-lookup"><span data-stu-id="3c067-119">Conversion Keywords</span></span>  

 <span data-ttu-id="3c067-120">Ниже приведены сравнения ключевых слов преобразования типов.</span><span class="sxs-lookup"><span data-stu-id="3c067-120">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="3c067-121">Ключевое слово</span><span class="sxs-lookup"><span data-stu-id="3c067-121">Keyword</span></span>|<span data-ttu-id="3c067-122">Типы данных</span><span class="sxs-lookup"><span data-stu-id="3c067-122">Data types</span></span>|<span data-ttu-id="3c067-123">Отношение аргумента</span><span class="sxs-lookup"><span data-stu-id="3c067-123">Argument relationship</span></span>|<span data-ttu-id="3c067-124">Сбой во время выполнения</span><span class="sxs-lookup"><span data-stu-id="3c067-124">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="3c067-125">CType Function</span><span class="sxs-lookup"><span data-stu-id="3c067-125">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="3c067-126">Любые типы данных</span><span class="sxs-lookup"><span data-stu-id="3c067-126">Any data types</span></span>|<span data-ttu-id="3c067-127">Для двух типов данных должно быть определено расширяющее или суженное преобразование.</span><span class="sxs-lookup"><span data-stu-id="3c067-127">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="3c067-128">Создает <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="3c067-128">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="3c067-129">Оператор DirectCast</span><span class="sxs-lookup"><span data-stu-id="3c067-129">DirectCast Operator</span></span>](directcast-operator.md)|<span data-ttu-id="3c067-130">Любые типы данных</span><span class="sxs-lookup"><span data-stu-id="3c067-130">Any data types</span></span>|<span data-ttu-id="3c067-131">Один тип должен наследовать или реализовывать другой тип</span><span class="sxs-lookup"><span data-stu-id="3c067-131">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="3c067-132">Создает <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="3c067-132">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="3c067-133">Только ссылочные типы</span><span class="sxs-lookup"><span data-stu-id="3c067-133">Reference types only</span></span>|<span data-ttu-id="3c067-134">Один тип должен наследовать или реализовывать другой тип</span><span class="sxs-lookup"><span data-stu-id="3c067-134">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="3c067-135">[Ничего не](../nothing.md) возвращает</span><span class="sxs-lookup"><span data-stu-id="3c067-135">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3c067-136">Пример</span><span class="sxs-lookup"><span data-stu-id="3c067-136">Example</span></span>  

 <span data-ttu-id="3c067-137">В следующем примере показано, как использовать `TryCast`.</span><span class="sxs-lookup"><span data-stu-id="3c067-137">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="3c067-138">См. также</span><span class="sxs-lookup"><span data-stu-id="3c067-138">See also</span></span>

- [<span data-ttu-id="3c067-139">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="3c067-139">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="3c067-140">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="3c067-140">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
