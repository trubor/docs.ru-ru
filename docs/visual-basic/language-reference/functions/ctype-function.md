---
description: 'Дополнительные сведения: Функция CType (Visual Basic)'
title: CType Function
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 9732f52b40e5f762769ba5dc340c000e7e1ba17a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701265"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="b0654-103">Функция CType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0654-103">CType Function (Visual Basic)</span></span>

<span data-ttu-id="b0654-104">Возвращает результат явного преобразования выражения в указанный тип данных, объект, структуру, класс или интерфейс.</span><span class="sxs-lookup"><span data-stu-id="b0654-104">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0654-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b0654-105">Syntax</span></span>

```vb
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="b0654-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="b0654-106">Parts</span></span>

<span data-ttu-id="b0654-107">`expression` Любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="b0654-107">`expression` Any valid expression.</span></span> <span data-ttu-id="b0654-108">Если значение `expression` выходит за пределы диапазона, допустимого параметром `typename` , Visual Basic создает исключение.</span><span class="sxs-lookup"><span data-stu-id="b0654-108">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="b0654-109">`typename` Любое выражение, которое является допустимым в `As` предложении `Dim` оператора, то есть имя любого типа данных, объекта, структуры, класса или интерфейса.</span><span class="sxs-lookup"><span data-stu-id="b0654-109">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0654-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="b0654-110">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="b0654-111">Для преобразования типов также можно использовать следующие функции.</span><span class="sxs-lookup"><span data-stu-id="b0654-111">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="b0654-112">Функции преобразования типов, такие как `CByte` , `CDbl` и `CInt` , которые выполняют преобразование в конкретный тип данных.</span><span class="sxs-lookup"><span data-stu-id="b0654-112">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="b0654-113">Дополнительные сведения см. в разделе [Функции преобразования типов](type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="b0654-113">For more information, see [Type Conversion Functions](type-conversion-functions.md).</span></span>
> - <span data-ttu-id="b0654-114">Оператор [DirectCast](../operators/directcast-operator.md) или [Оператор TryCast](../operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b0654-114">[DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md).</span></span> <span data-ttu-id="b0654-115">Для этих операторов требуется, чтобы один тип наследовал или реализовывал другой тип.</span><span class="sxs-lookup"><span data-stu-id="b0654-115">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="b0654-116">Они могут обеспечить более высокую производительность, чем `CType` при преобразовании в тип данных и из него `Object` .</span><span class="sxs-lookup"><span data-stu-id="b0654-116">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="b0654-117">`CType` компилируется встроенным образом, что означает, что код преобразования является частью кода, который вычисляет выражение.</span><span class="sxs-lookup"><span data-stu-id="b0654-117">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="b0654-118">В некоторых случаях код выполняется быстрее, так как для выполнения преобразования не вызываются никакие процедуры.</span><span class="sxs-lookup"><span data-stu-id="b0654-118">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="b0654-119">Если преобразование не определено из `expression` в `typename` (например, из в `Integer` `Date` ), Visual Basic отображает сообщение об ошибке времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="b0654-119">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="b0654-120">Если во время выполнения происходит сбой преобразования, выдается соответствующее исключение.</span><span class="sxs-lookup"><span data-stu-id="b0654-120">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="b0654-121">Если понижающие преобразования не удается выполнить, <xref:System.OverflowException> наиболее распространенным результатом является.</span><span class="sxs-lookup"><span data-stu-id="b0654-121">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="b0654-122">Если преобразование не определено, <xref:System.InvalidCastException> в вызываемом элементе.</span><span class="sxs-lookup"><span data-stu-id="b0654-122">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="b0654-123">Например, это может произойти, если `expression` имеет тип `Object` , а тип времени выполнения не имеет преобразования в `typename` .</span><span class="sxs-lookup"><span data-stu-id="b0654-123">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="b0654-124">Если тип данных `expression` или `typename` является определенным классом или структурой, можно определить `CType` в этом классе или структуре как оператор преобразования.</span><span class="sxs-lookup"><span data-stu-id="b0654-124">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="b0654-125">Это делает работу `CType` в качестве *перегруженного оператора*.</span><span class="sxs-lookup"><span data-stu-id="b0654-125">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="b0654-126">В этом случае можно управлять поведением преобразований в класс или структуру, включая исключения, которые могут быть созданы.</span><span class="sxs-lookup"><span data-stu-id="b0654-126">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="b0654-127">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="b0654-127">Overloading</span></span>

<span data-ttu-id="b0654-128">`CType`Оператор также может быть перегружен для класса или структуры, определенной вне кода.</span><span class="sxs-lookup"><span data-stu-id="b0654-128">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="b0654-129">Если код преобразует в или из такого класса или структуры, убедитесь, что вы понимаете поведение его `CType` оператора.</span><span class="sxs-lookup"><span data-stu-id="b0654-129">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="b0654-130">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b0654-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="b0654-131">Преобразование динамических объектов</span><span class="sxs-lookup"><span data-stu-id="b0654-131">Converting Dynamic Objects</span></span>

<span data-ttu-id="b0654-132">Преобразования типов динамических объектов выполняются с помощью определяемых пользователем динамических преобразований, использующих <xref:System.Dynamic.DynamicObject.TryConvert%2A> <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> методы или.</span><span class="sxs-lookup"><span data-stu-id="b0654-132">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="b0654-133">При работе с динамическими объектами используйте <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> метод для преобразования динамического объекта.</span><span class="sxs-lookup"><span data-stu-id="b0654-133">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="b0654-134">Пример</span><span class="sxs-lookup"><span data-stu-id="b0654-134">Example</span></span>

<span data-ttu-id="b0654-135">В следующем примере функция используется `CType` для преобразования выражения в `Single` тип данных.</span><span class="sxs-lookup"><span data-stu-id="b0654-135">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="b0654-136">Дополнительные примеры см. в разделе [явные и неявные преобразования](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="b0654-136">For additional examples, see [Implicit and Explicit Conversions](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0654-137">См. также</span><span class="sxs-lookup"><span data-stu-id="b0654-137">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="b0654-138">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="b0654-138">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="b0654-139">Функции преобразования</span><span class="sxs-lookup"><span data-stu-id="b0654-139">Conversion Functions</span></span>](conversion-functions.md)
- [<span data-ttu-id="b0654-140">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="b0654-140">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="b0654-141">Практическое руководство. Определение оператора преобразования</span><span class="sxs-lookup"><span data-stu-id="b0654-141">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="b0654-142">Преобразование типов в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b0654-142">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
