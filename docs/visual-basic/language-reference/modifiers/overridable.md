---
description: Дополнительные сведения о переопределяемых параметрах (Visual Basic)
title: Overridable
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: acbbd715113c836a3fb7f8a88bf74307c38ac682
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730503"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="c6566-103">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6566-103">Overridable (Visual Basic)</span></span>

<span data-ttu-id="c6566-104">Указывает, что свойство или процедура может быть переопределена свойством или процедурой с идентичным именем в производном классе.</span><span class="sxs-lookup"><span data-stu-id="c6566-104">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6566-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="c6566-105">Remarks</span></span>  

 <span data-ttu-id="c6566-106">`Overridable`Модификатор позволяет переопределять свойство или метод в производном классе.</span><span class="sxs-lookup"><span data-stu-id="c6566-106">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="c6566-107">Модификатор [NotOverridable](notoverridable.md) предотвращает переопределение свойства или метода в производном классе.</span><span class="sxs-lookup"><span data-stu-id="c6566-107">The [NotOverridable](notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="c6566-108">Дополнительные сведения см. в статье [Inheritance Basics (Visual Basic)](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md) (Основная информация о наследовании в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c6566-108">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="c6566-109">Если `Overridable` Модификатор или `NotOverridable` не задан, значение по умолчанию зависит от того, переопределяет ли свойство или метод свойство или метод базового класса.</span><span class="sxs-lookup"><span data-stu-id="c6566-109">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="c6566-110">Если свойство или метод переопределяет свойство или метод базового класса, параметр по умолчанию имеет значение `Overridable` ; в противном случае — `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="c6566-110">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="c6566-111">Можно выполнить затенение или переопределение, чтобы переопределить наследуемый элемент, но существуют значительные различия между этими двумя подходами.</span><span class="sxs-lookup"><span data-stu-id="c6566-111">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="c6566-112">Дополнительные сведения см. [в разделе теневая поддержка в Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="c6566-112">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="c6566-113">Элемент, который можно переопределить, иногда называется *виртуальным* элементом.</span><span class="sxs-lookup"><span data-stu-id="c6566-113">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="c6566-114">Если он может быть переопределен, но не обязательно должен быть, он иногда также называется *конкретным* элементом.</span><span class="sxs-lookup"><span data-stu-id="c6566-114">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="c6566-115">Можно использовать `Overridable` только в операторе объявления свойства или процедуры.</span><span class="sxs-lookup"><span data-stu-id="c6566-115">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="c6566-116">Комбинированные модификаторы</span><span class="sxs-lookup"><span data-stu-id="c6566-116">Combined Modifiers</span></span>  

 <span data-ttu-id="c6566-117">Нельзя указывать `Overridable` или `NotOverridable` для `Private` метода.</span><span class="sxs-lookup"><span data-stu-id="c6566-117">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="c6566-118">Нельзя указывать `Overridable` вместе с `MustOverride` , `NotOverridable` или `Shared` в одном объявлении.</span><span class="sxs-lookup"><span data-stu-id="c6566-118">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="c6566-119">Так как переопределяемый элемент является неявно переопределяемым, нельзя объединять `Overridable` с `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="c6566-119">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="c6566-120">Использование</span><span class="sxs-lookup"><span data-stu-id="c6566-120">Usage</span></span>  

 <span data-ttu-id="c6566-121">Модификатор `Overridable` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="c6566-121">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c6566-122">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="c6566-122">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="c6566-123">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c6566-123">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="c6566-124">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="c6566-124">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6566-125">См. также</span><span class="sxs-lookup"><span data-stu-id="c6566-125">See also</span></span>

- [<span data-ttu-id="c6566-126">Модификаторы</span><span class="sxs-lookup"><span data-stu-id="c6566-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="c6566-127">Основы наследования</span><span class="sxs-lookup"><span data-stu-id="c6566-127">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="c6566-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="c6566-128">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="c6566-129">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="c6566-129">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="c6566-130">Переопределения</span><span class="sxs-lookup"><span data-stu-id="c6566-130">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="c6566-131">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="c6566-131">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="c6566-132">Сокрытие в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6566-132">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
