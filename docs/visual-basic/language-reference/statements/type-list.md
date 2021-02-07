---
description: Дополнительные сведения о списке типов (Visual Basic)
title: Type List
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: d4c8bcab4a39af0ac0747d6be0d04408edd98a55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740903"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="ff9b6-103">Список типов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff9b6-103">Type List (Visual Basic)</span></span>

<span data-ttu-id="ff9b6-104">Задает *Параметры типа* для *универсального* программного элемента.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-104">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="ff9b6-105">Несколько параметров разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-105">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="ff9b6-106">Ниже приведен синтаксис для одного параметра типа.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-106">Following is the syntax for one type parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="ff9b6-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ff9b6-107">Syntax</span></span>

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a><span data-ttu-id="ff9b6-108">Компоненты</span><span class="sxs-lookup"><span data-stu-id="ff9b6-108">Parts</span></span>

|<span data-ttu-id="ff9b6-109">Термин</span><span class="sxs-lookup"><span data-stu-id="ff9b6-109">Term</span></span>|<span data-ttu-id="ff9b6-110">Определение</span><span class="sxs-lookup"><span data-stu-id="ff9b6-110">Definition</span></span>|
|---|---|
|`genericmodifier`|<span data-ttu-id="ff9b6-111">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-111">Optional.</span></span> <span data-ttu-id="ff9b6-112">Может использоваться только в универсальных интерфейсах и делегатах.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-112">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="ff9b6-113">Ковариантность типа можно объявить с помощью ключевого слова [out](../modifiers/out-generic-modifier.md) или контравариантного с помощью ключевого слова [in](../modifiers/in-generic-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="ff9b6-113">You can declare a type covariant by using the [Out](../modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="ff9b6-114">См. раздел [Ковариация и контрвариация](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="ff9b6-114">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|
|`typename`|<span data-ttu-id="ff9b6-115">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-115">Required.</span></span> <span data-ttu-id="ff9b6-116">Имя параметра типа.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-116">Name of the type parameter.</span></span> <span data-ttu-id="ff9b6-117">Это заполнитель, заменяемый определенным типом, предоставленным соответствующим аргументом типа.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-117">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|
|`constraintlist`|<span data-ttu-id="ff9b6-118">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-118">Optional.</span></span> <span data-ttu-id="ff9b6-119">Список требований, ограничивающих тип данных, который может быть представлен для `typename` .</span><span class="sxs-lookup"><span data-stu-id="ff9b6-119">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="ff9b6-120">При наличии нескольких ограничений заключите их в фигурные скобки ( `{ }` ) и разделите их запятыми.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-120">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="ff9b6-121">Список ограничений необходимо ввести с помощью ключевого слова [as](as-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="ff9b6-121">You must introduce the constraint list with the [As](as-clause.md) keyword.</span></span> <span data-ttu-id="ff9b6-122">Используется `As` только один раз в начале списка.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-122">You use `As` only once, at the beginning of the list.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ff9b6-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="ff9b6-123">Remarks</span></span>

<span data-ttu-id="ff9b6-124">Каждый универсальный программный элемент должен принимать по крайней мере один параметр типа.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-124">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="ff9b6-125">Параметр типа — это заполнитель для определенного типа ( *сконструированного элемента*), который клиентский код указывает при создании экземпляра универсального типа.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-125">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="ff9b6-126">Можно определить универсальный класс, структуру, интерфейс, процедуру или делегат.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-126">You can define a generic class, structure, interface, procedure, or delegate.</span></span>

<span data-ttu-id="ff9b6-127">Дополнительные сведения о том, когда следует определять универсальный тип, см. [в разделе Универсальные типы в Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="ff9b6-127">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="ff9b6-128">Дополнительные сведения об именах параметров типов см. в разделе [Имена объявленных элементов](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="ff9b6-128">For more information on type parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="rules"></a><span data-ttu-id="ff9b6-129">Правила</span><span class="sxs-lookup"><span data-stu-id="ff9b6-129">Rules</span></span>

- <span data-ttu-id="ff9b6-130">**Скобки.**</span><span class="sxs-lookup"><span data-stu-id="ff9b6-130">**Parentheses.**</span></span> <span data-ttu-id="ff9b6-131">Если вы представите список параметров типа, необходимо заключить его в круглые скобки и ввести в список ключевое слово [of](of-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="ff9b6-131">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](of-clause.md) keyword.</span></span> <span data-ttu-id="ff9b6-132">Используется `Of` только один раз в начале списка.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-132">You use `Of` only once, at the beginning of the list.</span></span>

- <span data-ttu-id="ff9b6-133">**Учитывая.**</span><span class="sxs-lookup"><span data-stu-id="ff9b6-133">**Constraints.**</span></span> <span data-ttu-id="ff9b6-134">Список *ограничений* для параметра типа может включать в себя следующие элементы в любом сочетании:</span><span class="sxs-lookup"><span data-stu-id="ff9b6-134">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>

  - <span data-ttu-id="ff9b6-135">Любое количество интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-135">Any number of interfaces.</span></span> <span data-ttu-id="ff9b6-136">Указанный тип должен реализовывать каждый интерфейс в этом списке.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-136">The supplied type must implement every interface in this list.</span></span>

  - <span data-ttu-id="ff9b6-137">Не более одного класса.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-137">At most one class.</span></span> <span data-ttu-id="ff9b6-138">Указанный тип должен наследоваться от этого класса.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-138">The supplied type must inherit from that class.</span></span>

  - <span data-ttu-id="ff9b6-139">ключевое слово `New`;</span><span class="sxs-lookup"><span data-stu-id="ff9b6-139">The `New` keyword.</span></span> <span data-ttu-id="ff9b6-140">Предоставленный тип должен предоставлять конструктор без параметров, к которому имеет доступ универсальный тип.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-140">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="ff9b6-141">Это полезно, если параметр типа ограничивается одним или несколькими интерфейсами.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-141">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="ff9b6-142">Тип, реализующий интерфейсы, не обязательно предоставляет конструктор, и в зависимости от уровня доступа конструктора код в универсальном типе может не иметь возможности получить к нему доступ.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-142">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>

  - <span data-ttu-id="ff9b6-143">`Class`Ключевое слово или `Structure` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-143">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="ff9b6-144">`Class`Ключевое слово ограничивает параметр универсального типа, требуя, чтобы любой передаваемый аргумент типа был ссылочным типом, например строкой, массивом или делегатом, или объектом, созданным из класса.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-144">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="ff9b6-145">`Structure`Ключевое слово ограничивает параметр универсального типа, требуя, чтобы любой передаваемый аргумент типа был типом значения, например структурой, перечислением или простым типом данных.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-145">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="ff9b6-146">Нельзя включать `Class` и `Structure` в, и в одном и том же `constraintlist` .</span><span class="sxs-lookup"><span data-stu-id="ff9b6-146">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>

  <span data-ttu-id="ff9b6-147">Указанный тип должен отвечать всем требованиям, включенным в `constraintlist` .</span><span class="sxs-lookup"><span data-stu-id="ff9b6-147">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>

  <span data-ttu-id="ff9b6-148">Ограничения для каждого параметра типа не зависят от ограничений для других параметров типа.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-148">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>

## <a name="behavior"></a><span data-ttu-id="ff9b6-149">Поведение</span><span class="sxs-lookup"><span data-stu-id="ff9b6-149">Behavior</span></span>

- <span data-ttu-id="ff9b6-150">**Подстановка во время компиляции.**</span><span class="sxs-lookup"><span data-stu-id="ff9b6-150">**Compile-Time Substitution.**</span></span> <span data-ttu-id="ff9b6-151">При создании сконструированного типа на основе универсального программного элемента вы предоставляете определенный тип для каждого параметра типа.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-151">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="ff9b6-152">Компилятор Visual Basic замещает указанный тип для каждого вхождения `typename` в пределах универсального элемента.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-152">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>

- <span data-ttu-id="ff9b6-153">**Отсутствие ограничений.**</span><span class="sxs-lookup"><span data-stu-id="ff9b6-153">**Absence of Constraints.**</span></span> <span data-ttu-id="ff9b6-154">Если не указать какие-либо ограничения на параметр типа, код будет ограничен операциями и элементами, поддерживаемыми [типом данных Object](../data-types/object-data-type.md) для этого параметра типа.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-154">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../data-types/object-data-type.md) for that type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="ff9b6-155">Пример</span><span class="sxs-lookup"><span data-stu-id="ff9b6-155">Example</span></span>

<span data-ttu-id="ff9b6-156">В следующем примере показано определение каркаса универсального класса Dictionary, включая скелет функции для добавления новой записи в словарь.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-156">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a><span data-ttu-id="ff9b6-157">Пример</span><span class="sxs-lookup"><span data-stu-id="ff9b6-157">Example</span></span>

<span data-ttu-id="ff9b6-158">Поскольку `dictionary` является универсальным, код, который использует его, может создавать разнообразные объекты, каждый из которых имеет одинаковые функциональные возможности, но работает с другим типом данных.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-158">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="ff9b6-159">В следующем примере показана строка кода, создающая `dictionary` объект с `String` записями и `Integer` ключами.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-159">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a><span data-ttu-id="ff9b6-160">Пример</span><span class="sxs-lookup"><span data-stu-id="ff9b6-160">Example</span></span>

<span data-ttu-id="ff9b6-161">В следующем примере показано эквивалентное определение скелета, созданное в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="ff9b6-161">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="ff9b6-162">См. также</span><span class="sxs-lookup"><span data-stu-id="ff9b6-162">See also</span></span>

- [<span data-ttu-id="ff9b6-163">Окна</span><span class="sxs-lookup"><span data-stu-id="ff9b6-163">Of</span></span>](of-clause.md)
- [<span data-ttu-id="ff9b6-164">Создание оператора</span><span class="sxs-lookup"><span data-stu-id="ff9b6-164">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="ff9b6-165">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff9b6-165">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="ff9b6-166">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="ff9b6-166">Object Data Type</span></span>](../data-types/object-data-type.md)
- [<span data-ttu-id="ff9b6-167">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="ff9b6-167">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="ff9b6-168">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="ff9b6-168">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="ff9b6-169">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="ff9b6-169">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="ff9b6-170">Практическое руководство. Использование универсального класса</span><span class="sxs-lookup"><span data-stu-id="ff9b6-170">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="ff9b6-171">Ковариация и контрвариантность</span><span class="sxs-lookup"><span data-stu-id="ff9b6-171">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="ff9b6-172">Где</span><span class="sxs-lookup"><span data-stu-id="ff9b6-172">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="ff9b6-173">Out</span><span class="sxs-lookup"><span data-stu-id="ff9b6-173">Out</span></span>](../modifiers/out-generic-modifier.md)
