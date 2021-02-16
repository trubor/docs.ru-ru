---
description: 'Дополнительные сведения: основные сведения о наследовании (Visual Basic)'
title: Основы наследования
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: facaa9a21fe3f99fc6e923ecb59dd977d72275ad
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485748"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="44f11-103">Основы наследования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44f11-103">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="44f11-104">`Inherits`Оператор используется для объявления нового класса, называемого *производным классом*, на основе существующего класса, называемого *базовым классом*.</span><span class="sxs-lookup"><span data-stu-id="44f11-104">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="44f11-105">Производные классы наследуют и могут расширять, свойства, методы, события, поля и константы, определенные в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="44f11-105">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="44f11-106">В следующем разделе описаны некоторые правила наследования, а также модификаторы, которые можно использовать для изменения способа наследования или наследования классов.</span><span class="sxs-lookup"><span data-stu-id="44f11-106">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="44f11-107">По умолчанию все классы наследуются, если только они не помечены `NotInheritable` ключевым словом.</span><span class="sxs-lookup"><span data-stu-id="44f11-107">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="44f11-108">Классы могут наследовать от других классов в проекте или из классов в других сборках, на которые ссылается проект.</span><span class="sxs-lookup"><span data-stu-id="44f11-108">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="44f11-109">В отличие от языков, допускающих множественное наследование, Visual Basic допускает только одно наследование в классах; то есть производные классы могут иметь только один базовый класс.</span><span class="sxs-lookup"><span data-stu-id="44f11-109">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="44f11-110">Хотя множественное наследование не разрешено в классах, классы могут реализовывать несколько интерфейсов, что может эффективно выполнять те же самые концы.</span><span class="sxs-lookup"><span data-stu-id="44f11-110">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="44f11-111">Чтобы предотвратить предоставление ограниченных элементов в базовом классе, тип доступа производного класса должен быть равным или более ограничивающим, чем его базовый класс.</span><span class="sxs-lookup"><span data-stu-id="44f11-111">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="44f11-112">Например, `Public` класс не может наследовать `Friend` `Private` класс или, а `Friend` класс не может наследовать `Private` класс.</span><span class="sxs-lookup"><span data-stu-id="44f11-112">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="44f11-113">Модификаторы наследования</span><span class="sxs-lookup"><span data-stu-id="44f11-113">Inheritance Modifiers</span></span>

<span data-ttu-id="44f11-114">Visual Basic вводит следующие операторы и модификаторы уровня класса для поддержки наследования:</span><span class="sxs-lookup"><span data-stu-id="44f11-114">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="44f11-115">`Inherits` оператор — указывает базовый класс.</span><span class="sxs-lookup"><span data-stu-id="44f11-115">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="44f11-116">`NotInheritable` модификатор — не позволяет программистам использовать класс в качестве базового класса.</span><span class="sxs-lookup"><span data-stu-id="44f11-116">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="44f11-117">`MustInherit` модификатор — указывает, что класс предназначен для использования только в качестве базового класса.</span><span class="sxs-lookup"><span data-stu-id="44f11-117">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="44f11-118">Экземпляры `MustInherit` классов нельзя создавать напрямую; они могут быть созданы только как экземпляры базового класса производного класса.</span><span class="sxs-lookup"><span data-stu-id="44f11-118">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="44f11-119">(Другие языки программирования, такие как C++ и C#, используют термин *абстрактный класс* для описания такого класса.)</span><span class="sxs-lookup"><span data-stu-id="44f11-119">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="44f11-120">Переопределение свойств и методов в производных классах</span><span class="sxs-lookup"><span data-stu-id="44f11-120">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="44f11-121">По умолчанию производный класс наследует свойства и методы от своего базового класса.</span><span class="sxs-lookup"><span data-stu-id="44f11-121">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="44f11-122">Если унаследованное свойство или метод должны вести себя по-разному в производном классе, его можно *переопределить*.</span><span class="sxs-lookup"><span data-stu-id="44f11-122">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="44f11-123">То есть можно определить новую реализацию метода в производном классе.</span><span class="sxs-lookup"><span data-stu-id="44f11-123">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="44f11-124">Следующие модификаторы используются для управления переопределением свойств и методов.</span><span class="sxs-lookup"><span data-stu-id="44f11-124">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="44f11-125">`Overridable` — Позволяет переопределять свойство или метод в классе в производном классе.</span><span class="sxs-lookup"><span data-stu-id="44f11-125">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="44f11-126">`Overrides` — Переопределяет `Overridable` свойство или метод, определенный в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="44f11-126">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="44f11-127">`NotOverridable` — Предотвращает переопределение свойства или метода в наследующем классе.</span><span class="sxs-lookup"><span data-stu-id="44f11-127">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="44f11-128">По умолчанию `Public` методы имеют значение `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="44f11-128">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="44f11-129">`MustOverride` — Требует, чтобы производный класс переопределял свойство или метод.</span><span class="sxs-lookup"><span data-stu-id="44f11-129">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="44f11-130">При `MustOverride` использовании ключевого слова определение метода состоит только из `Sub` `Function` оператора, или `Property` .</span><span class="sxs-lookup"><span data-stu-id="44f11-130">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="44f11-131">Другие инструкции не допускаются, а в частности нет `End Sub` оператора или `End Function` .</span><span class="sxs-lookup"><span data-stu-id="44f11-131">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="44f11-132">`MustOverride` методы должны быть объявлены в `MustInherit` классах.</span><span class="sxs-lookup"><span data-stu-id="44f11-132">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="44f11-133">Предположим, необходимо определить классы для работы с Payroll.</span><span class="sxs-lookup"><span data-stu-id="44f11-133">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="44f11-134">Можно определить универсальный `Payroll` класс, содержащий `RunPayroll` метод, который вычисляет зарплату для типичной недели.</span><span class="sxs-lookup"><span data-stu-id="44f11-134">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="44f11-135">Затем можно использовать `Payroll` в качестве базового класса для более специализированного `BonusPayroll` класса, который можно использовать при распределении премий сотрудников.</span><span class="sxs-lookup"><span data-stu-id="44f11-135">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="44f11-136">`BonusPayroll`Класс может наследовать и переопределять метод, `PayEmployee` определенный в базовом `Payroll` классе.</span><span class="sxs-lookup"><span data-stu-id="44f11-136">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="44f11-137">В следующем примере определяется базовый класс `Payroll,` и производный класс, `BonusPayroll` который переопределяет унаследованный метод `PayEmployee` .</span><span class="sxs-lookup"><span data-stu-id="44f11-137">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="44f11-138">Процедура, `RunPayroll` , создает и передает `Payroll` объект и `BonusPayroll` объект в функцию, `Pay` которая выполняет `PayEmployee` метод обоих объектов.</span><span class="sxs-lookup"><span data-stu-id="44f11-138">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="44f11-139">Ключевое слово MyBase</span><span class="sxs-lookup"><span data-stu-id="44f11-139">The MyBase Keyword</span></span>

<span data-ttu-id="44f11-140">`MyBase`Ключевое слово ведет себя как объектная переменная, которая ссылается на базовый класс текущего экземпляра класса.</span><span class="sxs-lookup"><span data-stu-id="44f11-140">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="44f11-141">`MyBase` часто используется для доступа к членам базового класса, которые переопределяются или переобъявляются в производном классе.</span><span class="sxs-lookup"><span data-stu-id="44f11-141">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="44f11-142">В частности, `MyBase.New` используется для явного вызова конструктора базового класса из конструктора производного класса.</span><span class="sxs-lookup"><span data-stu-id="44f11-142">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="44f11-143">Например, предположим, что вы разрабатываете производный класс, переопределяющий метод, унаследованный от базового класса.</span><span class="sxs-lookup"><span data-stu-id="44f11-143">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="44f11-144">Переопределенный метод может вызвать метод в базовом классе и изменить возвращаемое значение, как показано в следующем фрагменте кода:</span><span class="sxs-lookup"><span data-stu-id="44f11-144">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="44f11-145">В следующем списке описаны ограничения на использование `MyBase` :</span><span class="sxs-lookup"><span data-stu-id="44f11-145">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="44f11-146">`MyBase` ссылается на непосредственный базовый класс и его унаследованные члены.</span><span class="sxs-lookup"><span data-stu-id="44f11-146">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="44f11-147">Его нельзя использовать для доступа к `Private` членам в классе.</span><span class="sxs-lookup"><span data-stu-id="44f11-147">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="44f11-148">`MyBase` — Это ключевое слово, а не реальный объект.</span><span class="sxs-lookup"><span data-stu-id="44f11-148">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="44f11-149">`MyBase` нельзя присвоить значение переменной, передать ее процедурам или использовать в `Is` сравнении.</span><span class="sxs-lookup"><span data-stu-id="44f11-149">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="44f11-150">Метод, который `MyBase` не обязательно должен быть определен в непосредственном базовом классе; он может быть определен в косвенно наследуемом базовом классе.</span><span class="sxs-lookup"><span data-stu-id="44f11-150">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="44f11-151">Чтобы обеспечить `MyBase` правильную компиляцию ссылки, в некоторых базовых классах должен содержаться метод, соответствующий имени и типам параметров, которые отображаются в вызове.</span><span class="sxs-lookup"><span data-stu-id="44f11-151">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="44f11-152">Нельзя использовать `MyBase` для вызова `MustOverride` методов базового класса.</span><span class="sxs-lookup"><span data-stu-id="44f11-152">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="44f11-153">`MyBase` не может использоваться для уточнения самого себя.</span><span class="sxs-lookup"><span data-stu-id="44f11-153">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="44f11-154">Поэтому следующий код является недопустимым:</span><span class="sxs-lookup"><span data-stu-id="44f11-154">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="44f11-155">`MyBase` не может использоваться в модулях.</span><span class="sxs-lookup"><span data-stu-id="44f11-155">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="44f11-156">`MyBase` не может использоваться для доступа к членам базового класса, помеченным как, `Friend` Если базовый класс находится в другой сборке.</span><span class="sxs-lookup"><span data-stu-id="44f11-156">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="44f11-157">Дополнительные сведения и другой пример см. в разделе [как получить доступ к переменной, скрытой производным классом](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="44f11-157">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="44f11-158">Ключевое слово MyClass</span><span class="sxs-lookup"><span data-stu-id="44f11-158">The MyClass Keyword</span></span>

<span data-ttu-id="44f11-159">`MyClass`Ключевое слово ведет себя как объектная переменная, которая ссылается на текущий экземпляр класса как изначально реализованный.</span><span class="sxs-lookup"><span data-stu-id="44f11-159">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="44f11-160">`MyClass` Похоже `Me` на, но каждый вызов метода и свойства в обрабатывается `MyClass` так, как если бы метод или свойство были [NotOverridable](../../../language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="44f11-160">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="44f11-161">Таким образом, переопределение в производном классе не влияет на метод или свойство.</span><span class="sxs-lookup"><span data-stu-id="44f11-161">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="44f11-162">`MyClass` — Это ключевое слово, а не реальный объект.</span><span class="sxs-lookup"><span data-stu-id="44f11-162">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="44f11-163">`MyClass` нельзя присвоить значение переменной, передать ее процедурам или использовать в `Is` сравнении.</span><span class="sxs-lookup"><span data-stu-id="44f11-163">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="44f11-164">`MyClass` ссылается на содержащий класс и его унаследованные члены.</span><span class="sxs-lookup"><span data-stu-id="44f11-164">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="44f11-165">`MyClass` может использоваться в качестве квалификатора для `Shared` членов.</span><span class="sxs-lookup"><span data-stu-id="44f11-165">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="44f11-166">`MyClass` не может использоваться внутри `Shared` метода, но может использоваться внутри метода экземпляра для доступа к общему члену класса.</span><span class="sxs-lookup"><span data-stu-id="44f11-166">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="44f11-167">`MyClass` не может использоваться в стандартных модулях.</span><span class="sxs-lookup"><span data-stu-id="44f11-167">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="44f11-168">`MyClass` можно использовать для определения метода, который определен в базовом классе и не имеет реализации метода, предоставленного в этом классе.</span><span class="sxs-lookup"><span data-stu-id="44f11-168">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="44f11-169">Такая ссылка имеет то же значение, что и `MyBase.` *метод*.</span><span class="sxs-lookup"><span data-stu-id="44f11-169">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="44f11-170">В следующем примере сравниваются `Me` и `MyClass` .</span><span class="sxs-lookup"><span data-stu-id="44f11-170">The following example compares `Me` and `MyClass`.</span></span>

```vb
Class baseClass
    Public Overridable Sub testMethod()
        MsgBox("Base class string")
    End Sub
    Public Sub useMe()
        ' The following call uses the calling class's method, even if
        ' that method is an override.
        Me.testMethod()
    End Sub
    Public Sub useMyClass()
        ' The following call uses this instance's method and not any
        ' override.
        MyClass.testMethod()
    End Sub
End Class
Class derivedClass : Inherits baseClass
    Public Overrides Sub testMethod()
        MsgBox("Derived class string")
    End Sub
End Class
Class testClasses
    Sub startHere()
        Dim testObj As derivedClass = New derivedClass()
        ' The following call displays "Derived class string".
        testObj.useMe()
        ' The following call displays "Base class string".
        testObj.useMyClass()
    End Sub
End Class
```

<span data-ttu-id="44f11-171">Несмотря на `derivedClass` то `testMethod` что переопределения, `MyClass` ключевое слово в `useMyClass` сводят последствия переопределения, и компилятор разрешает вызов к версии базового класса `testMethod` .</span><span class="sxs-lookup"><span data-stu-id="44f11-171">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="44f11-172">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="44f11-172">See also</span></span>

- [<span data-ttu-id="44f11-173">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="44f11-173">Inherits Statement</span></span>](../../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="44f11-174">Me, My, MyBase и MyClass</span><span class="sxs-lookup"><span data-stu-id="44f11-174">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
