---
description: 'Узнайте подробнее о: Разработка конструктора'
title: Разработка конструктора
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: 2a5c85e1dea3349f897c24fa5d40d73c6e1f9d7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642322"
---
# <a name="constructor-design"></a><span data-ttu-id="2c4f8-103">Разработка конструктора</span><span class="sxs-lookup"><span data-stu-id="2c4f8-103">Constructor Design</span></span>

<span data-ttu-id="2c4f8-104">Существует два вида конструкторов: конструкторы типов и конструкторы экземпляров.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-104">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="2c4f8-105">Конструкторы типов являются статическими и выполняются средой CLR перед использованием типа.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-105">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="2c4f8-106">Конструкторы экземпляров запускаются при создании экземпляра типа.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-106">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="2c4f8-107">Конструкторы типов не могут принимать параметры, в отличие от</span><span class="sxs-lookup"><span data-stu-id="2c4f8-107">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="2c4f8-108">конструкторов экземпляров.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-108">Instance constructors can.</span></span> <span data-ttu-id="2c4f8-109">Конструкторы экземпляров, которые не принимают никакие параметры, часто называются конструкторами без параметров.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-109">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="2c4f8-110">Конструкторы предоставляют наиболее удобный способ создания экземпляров типа.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-110">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="2c4f8-111">Большинство разработчиков прежде всего будут искать и пытаться использовать конструктор, а не рассматривать альтернативные способы создания экземпляров (например, фабричные методы).</span><span class="sxs-lookup"><span data-stu-id="2c4f8-111">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="2c4f8-112">✔️ РЕКОМЕНДУЕТСЯ указать простые конструкторы, которые идеально подходят для использования по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-112">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="2c4f8-113">Простой конструктор имеет очень мало параметров, и все параметры являются примитивами или перечислениями.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-113">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="2c4f8-114">Такие простые конструкторы повышают удобство использования платформы.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-114">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="2c4f8-115">✔️ РЕКОМЕНДУЕТСЯ использовать статический фабричный метод вместо конструктора, если семантика требуемой операции не сопоставляется непосредственно с конструктором нового экземпляра или если следовать рекомендациям по разработке конструктора кажется противоестественным.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-115">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="2c4f8-116">✔ РЕКОМЕНДУЕТСЯ использовать параметры конструктора, чтобы быстрее задать основные свойства.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-116">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="2c4f8-117">Семантика использования пустого конструктора, за которым следуют некоторые наборы свойств, и использования конструктора с несколькими аргументами не должна отличаться.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-117">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="2c4f8-118">✔️ РЕКОМЕНДУЕТСЯ использовать одно и то же имя для параметров конструктора и свойства, если параметры конструктора используются просто для установки свойства.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-118">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="2c4f8-119">Единственное различие между такими параметрами и свойствами должно быть в регистре.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-119">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="2c4f8-120">✔️ ВЫПОЛНИТЕ минимальную работу в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-120">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="2c4f8-121">Конструкторы не должны выполнять много операций, отличных от захвата параметров конструктора.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-121">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="2c4f8-122">Затраты на любую другую обработку следует отложить до тех пор, пока это не понадобится.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-122">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="2c4f8-123">✔️ РЕКОМЕНДУЕТСЯ вызвать исключения из конструкторов экземпляров, если это применимо.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-123">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="2c4f8-124">✔️ РЕКОМЕНДУЕТСЯ явно объявить в классах открытый конструктор без параметров, если такой конструктор необходим.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-124">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="2c4f8-125">Если вы не объявили явно какие-либо конструкторы для типа, многие языки (например, C#) автоматически добавят открытый конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-125">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="2c4f8-126">(Абстрактные классы получают защищенный конструктор.)</span><span class="sxs-lookup"><span data-stu-id="2c4f8-126">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="2c4f8-127">Добавление параметризованного конструктора в класс не позволяет компилятору добавить конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-127">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="2c4f8-128">Это часто приводит к случайным критическим изменениям.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-128">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="2c4f8-129">❌ ИЗБЕГАЙТЕ явного определения конструкторов без параметров для структур.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-129">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="2c4f8-130">Это помогает создать массив быстрее, так как если конструктор без параметров не определен, он не должен выполняться в каждом слоте массива.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-130">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="2c4f8-131">Обратите внимание, что по этой причине многие компиляторы, включая C#, запрещают структурам использовать конструкторы без параметров.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-131">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="2c4f8-132">❌ НЕ вызывайте виртуальные элементы для объекта внутри конструктора.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-132">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="2c4f8-133">Вызов виртуального элемента приведет к вызову переопределения самого дальнего в цепочке объекта, даже если конструктор типа более низкого уровня иерархии еще не был полностью выполнен.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-133">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="2c4f8-134">Рекомендации по конструктору типов</span><span class="sxs-lookup"><span data-stu-id="2c4f8-134">Type Constructor Guidelines</span></span>

<span data-ttu-id="2c4f8-135">✔️ РЕКОМЕНДУЕТСЯ сделать статические конструкторы частными.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-135">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="2c4f8-136">Статический конструктор, также называемый конструктором класса, используется для инициализации типа.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-136">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="2c4f8-137">Среда CLR вызывает статический конструктор перед созданием первого экземпляра типа или вызывается статическими элементами для этого типа.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-137">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="2c4f8-138">Пользователь не управляет моментом вызова статического конструктора.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-138">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="2c4f8-139">Если статический конструктор не является частным, он может быть вызван кодом, находящимся за пределами среды CLR.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-139">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="2c4f8-140">В зависимости от операций, выполняемых в конструкторе, это может стать причиной непредвиденного поведения.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-140">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="2c4f8-141">Компилятор C# принудительно делает статические конструкторы частными.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-141">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="2c4f8-142">❌ НЕ создавайте исключения из статических конструкторов.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-142">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="2c4f8-143">Если исключение создается из конструктора типа, этот тип нельзя использовать в текущем домене приложения.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-143">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="2c4f8-144">✔️ РАССМОТРИТЕ возможность инициализации статических полей встроенными средствами вместо явного использования статических конструкторов, так как среда выполнения может оптимизировать производительность типов, у которых нет явно определенного статического конструктора.</span><span class="sxs-lookup"><span data-stu-id="2c4f8-144">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="2c4f8-145">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="2c4f8-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="2c4f8-146">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2c4f8-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="2c4f8-147">См. также</span><span class="sxs-lookup"><span data-stu-id="2c4f8-147">See also</span></span>

- [<span data-ttu-id="2c4f8-148">Правила разработки членов</span><span class="sxs-lookup"><span data-stu-id="2c4f8-148">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="2c4f8-149">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="2c4f8-149">Framework Design Guidelines</span></span>](index.md)
