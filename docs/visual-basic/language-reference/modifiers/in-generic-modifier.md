---
description: 'Дополнительные сведения о: in (универсальный модификатор) (Visual Basic)'
title: In (универсальный модификатор) — Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: e6ac95a77253b28e45a4be8a29623bdd76a231f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774542"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="dc748-103">In (универсальный модификатор) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc748-103">In (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="dc748-104">Для параметров универсального типа ключевое слово `In` указывает, что параметр типа является контравариантным.</span><span class="sxs-lookup"><span data-stu-id="dc748-104">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc748-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="dc748-105">Remarks</span></span>

<span data-ttu-id="dc748-106">Контравариантность позволяет использовать производные типы со степенью наследования меньше, чем у типа, заданного универсальным параметром.</span><span class="sxs-lookup"><span data-stu-id="dc748-106">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="dc748-107">Благодаря этому можно осуществлять неявное преобразование классов, реализующих вариантные интерфейсы, и неявное преобразование типов делегатов.</span><span class="sxs-lookup"><span data-stu-id="dc748-107">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="dc748-108">Дополнительные сведения см. в разделе [Ковариация и контравариантность](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="dc748-108">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="dc748-109">Правила</span><span class="sxs-lookup"><span data-stu-id="dc748-109">Rules</span></span>

<span data-ttu-id="dc748-110">Ключевое слово `In` может применяться в универсальных интерфейсах и делегатах.</span><span class="sxs-lookup"><span data-stu-id="dc748-110">You can use the `In` keyword in generic interfaces and delegates.</span></span>
  
<span data-ttu-id="dc748-111">Параметр типа может быть объявлен контравариантным в универсальном интерфейсе или делегате, если он используется только в качестве типа аргументов метода и не используется в качестве типа возвращаемого значения метода.</span><span class="sxs-lookup"><span data-stu-id="dc748-111">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="dc748-112">`ByRef` параметры не могут быть ковариантными или контравариантным.</span><span class="sxs-lookup"><span data-stu-id="dc748-112">`ByRef` parameters cannot be covariant or contravariant.</span></span>

<span data-ttu-id="dc748-113">Ковариация и контрвариация поддерживаются для ссылочных типов и не поддерживаются для типов значений.</span><span class="sxs-lookup"><span data-stu-id="dc748-113">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>

<span data-ttu-id="dc748-114">В Visual Basic нельзя объявлять события в контравариантные интерфейсах без указания типа делегата.</span><span class="sxs-lookup"><span data-stu-id="dc748-114">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="dc748-115">Кроме того, контравариантные интерфейсы не могут иметь вложенные классы, перечисления или структуры, но они могут иметь вложенные интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="dc748-115">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="dc748-116">Поведение</span><span class="sxs-lookup"><span data-stu-id="dc748-116">Behavior</span></span>

<span data-ttu-id="dc748-117">Интерфейс с параметром контравариантного типа позволяет своим методам принимать аргументы производных типов, степень наследования у которых меньше, чем у параметра типа интерфейса.</span><span class="sxs-lookup"><span data-stu-id="dc748-117">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="dc748-118">Например, поскольку в платформа .NET Framework 4 в <xref:System.Collections.Generic.IComparer%601> интерфейсе тип T является контравариантным, можно присвоить объект `IComparer(Of Person)` типа объекту `IComparer(Of Employee)` типа без использования каких-либо специальных методов преобразования, если `Employee` наследуется от `Person` .</span><span class="sxs-lookup"><span data-stu-id="dc748-118">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits from `Person`.</span></span>

<span data-ttu-id="dc748-119">Контравариантный делегат может быть назначен другому делегату того же типа, но с производным параметром универсального типа меньшей степени.</span><span class="sxs-lookup"><span data-stu-id="dc748-119">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

## <a name="example---contravariant-generic-interface"></a><span data-ttu-id="dc748-120">Пример — контравариантный универсальный интерфейс</span><span class="sxs-lookup"><span data-stu-id="dc748-120">Example - contravariant generic interface</span></span>

<span data-ttu-id="dc748-121">В следующем примере показано, как объявить, расширить и реализовать контравариантный универсальный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="dc748-121">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="dc748-122">В нем также показано, как можно использовать неявное преобразование для классов, реализующих этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="dc748-122">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]

## <a name="example---contravariant-generic-delegate"></a><span data-ttu-id="dc748-123">Пример — контравариантный универсальный делегат</span><span class="sxs-lookup"><span data-stu-id="dc748-123">Example - contravariant generic delegate</span></span>

<span data-ttu-id="dc748-124">В следующем примере кода показано, как объявить контравариантный универсальный делегат.</span><span class="sxs-lookup"><span data-stu-id="dc748-124">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="dc748-125">В нем также показано, как можно выполнить неявное преобразование типа делегата.</span><span class="sxs-lookup"><span data-stu-id="dc748-125">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="dc748-126">См. также</span><span class="sxs-lookup"><span data-stu-id="dc748-126">See also</span></span>

- [<span data-ttu-id="dc748-127">Вариативность в универсальных интерфейсах</span><span class="sxs-lookup"><span data-stu-id="dc748-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="dc748-128">Out</span><span class="sxs-lookup"><span data-stu-id="dc748-128">Out</span></span>](out-generic-modifier.md)
