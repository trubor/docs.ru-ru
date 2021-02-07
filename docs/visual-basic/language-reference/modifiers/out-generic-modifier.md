---
description: 'Дополнительные сведения о: out (универсальный модификатор) (Visual Basic)'
title: out (универсальный модификатор)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: cdf80439fbae0d2411eecff1c7e8438534fcfdc1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730542"
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="6fd1a-103">Out (универсальный модификатор) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fd1a-103">Out (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="6fd1a-104">Для параметров универсального типа `Out` ключевое слово указывает, что тип является ковариантным.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-104">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="6fd1a-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="6fd1a-105">Remarks</span></span>

<span data-ttu-id="6fd1a-106">Ковариация позволяет использовать производные типы со степенью наследования больше, нежели у типа, заданного универсальным параметром.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-106">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="6fd1a-107">Благодаря этому можно осуществлять неявное преобразование классов, реализующих вариантные интерфейсы, и неявное преобразование типов делегатов.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-107">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="6fd1a-108">Дополнительные сведения см. в разделе [Ковариация и контравариантность](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="6fd1a-108">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="6fd1a-109">Правила</span><span class="sxs-lookup"><span data-stu-id="6fd1a-109">Rules</span></span>

<span data-ttu-id="6fd1a-110">Ключевое слово `Out` может применяться в универсальных интерфейсах и делегатах.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-110">You can use the `Out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="6fd1a-111">В универсальном интерфейсе параметр типа может быть объявлен ковариантным, если он удовлетворяет следующим условиям:</span><span class="sxs-lookup"><span data-stu-id="6fd1a-111">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="6fd1a-112">Параметр типа используется только в качестве типа значения, возвращаемого методами интерфейса, и не используется в качестве типа аргументов метода.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-112">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6fd1a-113">Существует одно исключение из данного правила.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-113">There is one exception to this rule.</span></span> <span data-ttu-id="6fd1a-114">Если в ковариантном интерфейсе в качестве параметра метода используется контравариантный универсальный делегат, ковариантный тип можно использовать в качестве параметра универсального типа для этого делегата.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-114">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="6fd1a-115">Дополнительные сведения о ковариантных и контравариантных универсальных методах-делегатах см. в разделе [Вариативность в делегатах](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) и [Использование вариативности в универсальных методах-делегатах Func и Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="6fd1a-115">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="6fd1a-116">Параметр типа не используется в качестве универсального ограничения для методов интерфейса.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-116">The type parameter is not used as a generic constraint for the interface methods.</span></span>

<span data-ttu-id="6fd1a-117">В универсальном делегате параметр типа может быть объявлен ковариантным, если он используется только в качестве возвращаемого типа метода и не используется для аргументов метода.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-117">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

<span data-ttu-id="6fd1a-118">Ковариация и контравариантность поддерживаются для ссылочных типов, но не для типов значений.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-118">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="6fd1a-119">В Visual Basic нельзя объявлять события в ковариантных интерфейсах без указания типа делегата.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-119">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="6fd1a-120">Кроме того, ковариантные интерфейсы не могут иметь вложенные классы, перечисления или структуры, но они могут иметь вложенные интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-120">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="6fd1a-121">Поведение</span><span class="sxs-lookup"><span data-stu-id="6fd1a-121">Behavior</span></span>

<span data-ttu-id="6fd1a-122">Интерфейс с параметром ковариантного типа позволяет своим методам возвращать аргументы производных типов, степень наследования у которых больше, чем у параметра типа.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-122">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="6fd1a-123">Например, так как в .NET Framework 4 в <xref:System.Collections.Generic.IEnumerable%601> тип T является ковариантным, можно назначить объект типа `IEnumerable(Of String)` объекту типа `IEnumerable(Of Object)` без применения каких-либо специальных методов преобразования.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-123">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="6fd1a-124">Ковариантный делегат может быть назначен другому делегату того же типа, но с производным параметром универсального типа большей степени.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-124">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="6fd1a-125">Пример</span><span class="sxs-lookup"><span data-stu-id="6fd1a-125">Example</span></span>

<span data-ttu-id="6fd1a-126">В следующем примере показано, как объявить, расширить и реализовать ковариантный универсальный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-126">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="6fd1a-127">В нем также показано, как использовать неявное преобразование для классов, реализующих ковариантный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-127">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="6fd1a-128">Пример</span><span class="sxs-lookup"><span data-stu-id="6fd1a-128">Example</span></span>

<span data-ttu-id="6fd1a-129">В следующем примере кода показано, как объявить ковариантный универсальный метод-делегат.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-129">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="6fd1a-130">Здесь также показано, как можно использовать неявное преобразование для типов делегатов.</span><span class="sxs-lookup"><span data-stu-id="6fd1a-130">It also shows how you can use implicit conversion for delegate types.</span></span>

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="6fd1a-131">См. также</span><span class="sxs-lookup"><span data-stu-id="6fd1a-131">See also</span></span>

- [<span data-ttu-id="6fd1a-132">Вариативность в универсальных интерфейсах</span><span class="sxs-lookup"><span data-stu-id="6fd1a-132">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="6fd1a-133">Где</span><span class="sxs-lookup"><span data-stu-id="6fd1a-133">In</span></span>](in-generic-modifier.md)
