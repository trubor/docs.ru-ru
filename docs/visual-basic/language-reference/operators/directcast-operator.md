---
description: Дополнительные сведения о операторе DirectCast (Visual Basic)
title: Оператор DirectCast
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: be1eb4885940571788769bae968b1a094e256c79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773905"
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="af190-103">Оператор DirectCast (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af190-103">DirectCast Operator (Visual Basic)</span></span>

<span data-ttu-id="af190-104">Вводит операцию преобразования типов на основе наследования или реализации.</span><span class="sxs-lookup"><span data-stu-id="af190-104">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af190-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="af190-105">Remarks</span></span>  

 <span data-ttu-id="af190-106">`DirectCast` не использует подпрограммы вспомогательной среды выполнения Visual Basic для преобразования, поэтому она может обеспечить более высокую производительность, чем `CType` при преобразовании в тип данных и из него `Object` .</span><span class="sxs-lookup"><span data-stu-id="af190-106">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="af190-107">Используйте `DirectCast` ключевое слово, аналогичное тому, как используется [Функция CType](../functions/ctype-function.md) и ключевое слово [оператора TryCast](trycast-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="af190-107">You use the `DirectCast` keyword similar to the way you use the [CType Function](../functions/ctype-function.md) and the [TryCast Operator](trycast-operator.md) keyword.</span></span> <span data-ttu-id="af190-108">Укажите выражение в качестве первого аргумента и тип, чтобы преобразовать его в качестве второго аргумента.</span><span class="sxs-lookup"><span data-stu-id="af190-108">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="af190-109">`DirectCast` требует отношения наследования или реализации между типами данных двух аргументов.</span><span class="sxs-lookup"><span data-stu-id="af190-109">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="af190-110">Это означает, что один тип должен наследовать или реализовывать другой.</span><span class="sxs-lookup"><span data-stu-id="af190-110">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="af190-111">Ошибки и сбои</span><span class="sxs-lookup"><span data-stu-id="af190-111">Errors and Failures</span></span>  

 <span data-ttu-id="af190-112">`DirectCast` выдает ошибку компилятора, если обнаруживается, что связь наследования или реализации не существует.</span><span class="sxs-lookup"><span data-stu-id="af190-112">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="af190-113">Но отсутствие ошибки компилятора не гарантирует успешного преобразования.</span><span class="sxs-lookup"><span data-stu-id="af190-113">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="af190-114">Если требуемое преобразование является узким, оно может привести к сбою во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="af190-114">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="af190-115">Если это происходит, среда выполнения выдает <xref:System.InvalidCastException> ошибку.</span><span class="sxs-lookup"><span data-stu-id="af190-115">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="af190-116">Ключевые слова преобразований</span><span class="sxs-lookup"><span data-stu-id="af190-116">Conversion Keywords</span></span>  

 <span data-ttu-id="af190-117">Ниже приведены сравнения ключевых слов преобразования типов.</span><span class="sxs-lookup"><span data-stu-id="af190-117">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="af190-118">Ключевое слово</span><span class="sxs-lookup"><span data-stu-id="af190-118">Keyword</span></span>|<span data-ttu-id="af190-119">Типы данных</span><span class="sxs-lookup"><span data-stu-id="af190-119">Data types</span></span>|<span data-ttu-id="af190-120">Отношение аргумента</span><span class="sxs-lookup"><span data-stu-id="af190-120">Argument relationship</span></span>|<span data-ttu-id="af190-121">Сбой во время выполнения</span><span class="sxs-lookup"><span data-stu-id="af190-121">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="af190-122">CType Function</span><span class="sxs-lookup"><span data-stu-id="af190-122">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="af190-123">Любые типы данных</span><span class="sxs-lookup"><span data-stu-id="af190-123">Any data types</span></span>|<span data-ttu-id="af190-124">Для двух типов данных должно быть определено расширяющее или суженное преобразование.</span><span class="sxs-lookup"><span data-stu-id="af190-124">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="af190-125">Создает <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="af190-125">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="af190-126">Любые типы данных</span><span class="sxs-lookup"><span data-stu-id="af190-126">Any data types</span></span>|<span data-ttu-id="af190-127">Один тип должен наследовать или реализовывать другой тип</span><span class="sxs-lookup"><span data-stu-id="af190-127">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="af190-128">Создает <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="af190-128">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="af190-129">Оператор TryCast</span><span class="sxs-lookup"><span data-stu-id="af190-129">TryCast Operator</span></span>](trycast-operator.md)|<span data-ttu-id="af190-130">Только ссылочные типы</span><span class="sxs-lookup"><span data-stu-id="af190-130">Reference types only</span></span>|<span data-ttu-id="af190-131">Один тип должен наследовать или реализовывать другой тип</span><span class="sxs-lookup"><span data-stu-id="af190-131">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="af190-132">[Ничего не](../nothing.md) возвращает</span><span class="sxs-lookup"><span data-stu-id="af190-132">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="af190-133">Пример</span><span class="sxs-lookup"><span data-stu-id="af190-133">Example</span></span>  

 <span data-ttu-id="af190-134">В следующем примере демонстрируются два применения `DirectCast` , один из которых завершается сбоем во время выполнения и один успешно.</span><span class="sxs-lookup"><span data-stu-id="af190-134">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 <span data-ttu-id="af190-135">В предыдущем примере типом времени выполнения `q` является `Double` .</span><span class="sxs-lookup"><span data-stu-id="af190-135">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="af190-136">`CType` выполнено, так как `Double` может быть преобразовано в `Integer` .</span><span class="sxs-lookup"><span data-stu-id="af190-136">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="af190-137">Однако первый `DirectCast` сбой во время выполнения, так как тип времени выполнения `Double` не имеет отношения наследования с `Integer` , даже если существует преобразование.</span><span class="sxs-lookup"><span data-stu-id="af190-137">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="af190-138">Вторая `DirectCast` успешна, так как она преобразует тип <xref:System.Windows.Forms.Form> в тип <xref:System.Windows.Forms.Control> , от которого <xref:System.Windows.Forms.Form> наследует.</span><span class="sxs-lookup"><span data-stu-id="af190-138">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af190-139">См. также</span><span class="sxs-lookup"><span data-stu-id="af190-139">See also</span></span>

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="af190-140">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="af190-140">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="af190-141">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="af190-141">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
