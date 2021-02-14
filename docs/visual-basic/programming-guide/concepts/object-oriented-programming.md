---
description: 'Дополнительные сведения: объектно-ориентированное программирование (Visual Basic)'
title: Объектно-ориентированное программирование
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: af2fbac16bfefc90876bf22bb8c67de162ee6459
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486801"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="b0589-103">Объектно-ориентированное программирование (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0589-103">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="b0589-104">Visual Basic обеспечивает полную поддержку объектно-ориентированного программирования, включая инкапсуляцию, наследование и полиморфизм.</span><span class="sxs-lookup"><span data-stu-id="b0589-104">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="b0589-105">*Инкапсуляция* означает, что группа связанных свойств, методов и других членов рассматривается как единый элемент или объект.</span><span class="sxs-lookup"><span data-stu-id="b0589-105">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="b0589-106">*Наследование* описывает возможность создания новых классов на основе существующих классов.</span><span class="sxs-lookup"><span data-stu-id="b0589-106">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="b0589-107">*Полиморфизм* означает, что можно иметь несколько взаимозаменяемых классов, даже если каждый класс реализует одни и те же свойства или методы разными способами.</span><span class="sxs-lookup"><span data-stu-id="b0589-107">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="b0589-108">В этом разделе рассматриваются следующие понятия.</span><span class="sxs-lookup"><span data-stu-id="b0589-108">This section describes the following concepts:</span></span>

- [<span data-ttu-id="b0589-109">Классы и объекты</span><span class="sxs-lookup"><span data-stu-id="b0589-109">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="b0589-110">Члены класса</span><span class="sxs-lookup"><span data-stu-id="b0589-110">Class members</span></span>](#class-members)
    - [<span data-ttu-id="b0589-111">Свойства и поля</span><span class="sxs-lookup"><span data-stu-id="b0589-111">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="b0589-112">Методы</span><span class="sxs-lookup"><span data-stu-id="b0589-112">Methods</span></span>](#methods)
    - [<span data-ttu-id="b0589-113">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="b0589-113">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="b0589-114">Деструкторы</span><span class="sxs-lookup"><span data-stu-id="b0589-114">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="b0589-115">События</span><span class="sxs-lookup"><span data-stu-id="b0589-115">Events</span></span>](#events)
    - [<span data-ttu-id="b0589-116">Вложенные классы</span><span class="sxs-lookup"><span data-stu-id="b0589-116">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="b0589-117">Модификаторы доступа и уровни доступа</span><span class="sxs-lookup"><span data-stu-id="b0589-117">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="b0589-118">Создание экземпляров классов</span><span class="sxs-lookup"><span data-stu-id="b0589-118">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="b0589-119">Общие классы и члены</span><span class="sxs-lookup"><span data-stu-id="b0589-119">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="b0589-120">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="b0589-120">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="b0589-121">Наследование</span><span class="sxs-lookup"><span data-stu-id="b0589-121">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="b0589-122">Переопределение членов</span><span class="sxs-lookup"><span data-stu-id="b0589-122">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="b0589-123">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="b0589-123">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="b0589-124">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="b0589-124">Generics</span></span>](#generics)
- [<span data-ttu-id="b0589-125">Делегаты</span><span class="sxs-lookup"><span data-stu-id="b0589-125">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="b0589-126">Классы и объекты</span><span class="sxs-lookup"><span data-stu-id="b0589-126">Classes and objects</span></span>

<span data-ttu-id="b0589-127">Термины *класс* и *объект* часто взаимозаменяемы, но в действительности классы описывают *типы* объектов, а объекты — это используемые *экземпляры* классов.</span><span class="sxs-lookup"><span data-stu-id="b0589-127">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="b0589-128">Поэтому процесс создания объекта называется *созданием экземпляра*.</span><span class="sxs-lookup"><span data-stu-id="b0589-128">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="b0589-129">Если использовать сравнение с чертежом, то класс является чертежом, а объект является зданием, построенным по нему.</span><span class="sxs-lookup"><span data-stu-id="b0589-129">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="b0589-130">Определение класса:</span><span class="sxs-lookup"><span data-stu-id="b0589-130">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="b0589-131">Visual Basic также предоставляет облегченную версию классов, называемых *структурами* , которые полезны, когда необходимо создать большой массив объектов и не требуется потреблять слишком много памяти.</span><span class="sxs-lookup"><span data-stu-id="b0589-131">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="b0589-132">Определение структуры:</span><span class="sxs-lookup"><span data-stu-id="b0589-132">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="b0589-133">Дополнительные сведения можно найти в разделе</span><span class="sxs-lookup"><span data-stu-id="b0589-133">For more information, see:</span></span>

- [<span data-ttu-id="b0589-134">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="b0589-134">Class Statement</span></span>](../../language-reference/statements/class-statement.md)
- [<span data-ttu-id="b0589-135">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="b0589-135">Structure Statement</span></span>](../../language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="b0589-136">Члены класса</span><span class="sxs-lookup"><span data-stu-id="b0589-136">Class members</span></span>

<span data-ttu-id="b0589-137">Каждый класс может состоять из различных *членов класса*, которые содержат свойства, описывающие данные класса, методы, задающие поведение класса, и события, обеспечивающие связь между различными классами и объектами.</span><span class="sxs-lookup"><span data-stu-id="b0589-137">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="b0589-138">Свойства и поля</span><span class="sxs-lookup"><span data-stu-id="b0589-138">Properties and fields</span></span>

<span data-ttu-id="b0589-139">Поля и свойства представляют сведения, содержащиеся в объекте.</span><span class="sxs-lookup"><span data-stu-id="b0589-139">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="b0589-140">Поля подобны переменным в том, что их можно прочитать или изменить напрямую.</span><span class="sxs-lookup"><span data-stu-id="b0589-140">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="b0589-141">Определение поля:</span><span class="sxs-lookup"><span data-stu-id="b0589-141">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="b0589-142">Для работы со свойствами используются процедуры "Get" и "Set", которые расширяют возможности управления способом задания и возврата значений.</span><span class="sxs-lookup"><span data-stu-id="b0589-142">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="b0589-143">Visual Basic позволяет создать частное поле для хранения значения свойства или использовать так называемые автоматически реализуемые свойства, которые создают это поле автоматически в фоновом режиме и предоставляют базовую логику для процедур свойств.</span><span class="sxs-lookup"><span data-stu-id="b0589-143">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="b0589-144">Определение автоматически реализуемого свойства:</span><span class="sxs-lookup"><span data-stu-id="b0589-144">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="b0589-145">Если требуется выполнить дополнительные операции чтения и записи применительно к значению свойства, определите поле для хранения значения свойства и затем реализуйте базовую логику для хранения и извлечения этого значения:</span><span class="sxs-lookup"><span data-stu-id="b0589-145">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

<span data-ttu-id="b0589-146">У большинства свойств есть методы или процедуры для задания и возврата значения свойства.</span><span class="sxs-lookup"><span data-stu-id="b0589-146">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="b0589-147">Однако можно создать свойства, доступные только для чтения или только на запись, чтобы запретить изменение или чтение значений свойств.</span><span class="sxs-lookup"><span data-stu-id="b0589-147">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="b0589-148">Для этого в Visual Basic можно использовать ключевые слова `ReadOnly` и `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="b0589-148">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="b0589-149">Следует отметить, что автоматически реализуемые свойства нельзя сделать доступными только для чтения или только для записи.</span><span class="sxs-lookup"><span data-stu-id="b0589-149">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="b0589-150">Дополнительные сведения см. в разделе:</span><span class="sxs-lookup"><span data-stu-id="b0589-150">For more information, see:</span></span>

- [<span data-ttu-id="b0589-151">Property Statement</span><span class="sxs-lookup"><span data-stu-id="b0589-151">Property Statement</span></span>](../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="b0589-152">Оператор Get</span><span class="sxs-lookup"><span data-stu-id="b0589-152">Get Statement</span></span>](../../language-reference/statements/get-statement.md)
- [<span data-ttu-id="b0589-153">Инструкция SET</span><span class="sxs-lookup"><span data-stu-id="b0589-153">Set Statement</span></span>](../../language-reference/statements/set-statement.md)
- [<span data-ttu-id="b0589-154">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="b0589-154">ReadOnly</span></span>](../../language-reference/modifiers/readonly.md)
- [<span data-ttu-id="b0589-155">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="b0589-155">WriteOnly</span></span>](../../language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="b0589-156">Методы</span><span class="sxs-lookup"><span data-stu-id="b0589-156">Methods</span></span>

 <span data-ttu-id="b0589-157">Действие, которое выполняет объект, называется *методом*.</span><span class="sxs-lookup"><span data-stu-id="b0589-157">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="b0589-158">В Visual Basic существует два способа создания метода: с помощью оператора `Sub` (если метод не возвращает значение) или с помощью оператора `Function` (если метод возвращает значение).</span><span class="sxs-lookup"><span data-stu-id="b0589-158">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="b0589-159">Определение метода класса:</span><span class="sxs-lookup"><span data-stu-id="b0589-159">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="b0589-160">Класс может иметь несколько реализаций или *перегрузок* одного и того же метода, которые отличаются от других числом или типами параметров.</span><span class="sxs-lookup"><span data-stu-id="b0589-160">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="b0589-161">Перегрузка метода:</span><span class="sxs-lookup"><span data-stu-id="b0589-161">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="b0589-162">Как правило, метод объявляется при определении класса.</span><span class="sxs-lookup"><span data-stu-id="b0589-162">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="b0589-163">Однако Visual Basic также поддерживает *методы расширения* , позволяющие добавлять методы в существующий класс за пределами фактического определения класса.</span><span class="sxs-lookup"><span data-stu-id="b0589-163">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="b0589-164">Дополнительные сведения см. в разделе:</span><span class="sxs-lookup"><span data-stu-id="b0589-164">For more information, see:</span></span>

- [<span data-ttu-id="b0589-165">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="b0589-165">Function Statement</span></span>](../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="b0589-166">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="b0589-166">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="b0589-167">Перегрузки</span><span class="sxs-lookup"><span data-stu-id="b0589-167">Overloads</span></span>](../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="b0589-168">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="b0589-168">Extension Methods</span></span>](../language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="b0589-169">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="b0589-169">Constructors</span></span>

<span data-ttu-id="b0589-170">Конструкторы — это методы классов, выполняемые автоматически при создании объекта заданного типа.</span><span class="sxs-lookup"><span data-stu-id="b0589-170">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="b0589-171">Обычно конструкторы выполняют инициализацию членов данных нового объекта.</span><span class="sxs-lookup"><span data-stu-id="b0589-171">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="b0589-172">Конструктор можно запустить только один раз при создании класса.</span><span class="sxs-lookup"><span data-stu-id="b0589-172">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="b0589-173">Кроме того, код конструктора всегда выполняется раньше всех остальных частей кода в классе.</span><span class="sxs-lookup"><span data-stu-id="b0589-173">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="b0589-174">Следует отметить, что так же, как и для других методов, можно создать несколько перегрузок конструктора.</span><span class="sxs-lookup"><span data-stu-id="b0589-174">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="b0589-175">Определение конструктора для класса:</span><span class="sxs-lookup"><span data-stu-id="b0589-175">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="b0589-176">Дополнительные сведения см. в разделе: [время существования объекта: как создаются и уничтожаются объекты](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="b0589-176">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="b0589-177">Деструкторы</span><span class="sxs-lookup"><span data-stu-id="b0589-177">Destructors</span></span>

<span data-ttu-id="b0589-178">Деструкторы используются для уничтожения экземпляров классов.</span><span class="sxs-lookup"><span data-stu-id="b0589-178">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="b0589-179">В платформе .NET Framework сборщик мусора автоматически управляет распределением и освобождением памяти для управляемых объектов приложения.</span><span class="sxs-lookup"><span data-stu-id="b0589-179">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="b0589-180">Однако для очистки неуправляемых ресурсов, создаваемых приложением, могут потребоваться деструкторы.</span><span class="sxs-lookup"><span data-stu-id="b0589-180">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="b0589-181">На один класс допускается только один деструктор.</span><span class="sxs-lookup"><span data-stu-id="b0589-181">There can be only one destructor for a class.</span></span>

<span data-ttu-id="b0589-182">Дополнительные сведения о деструкторах и сборке мусора в .NET Framework см. в разделе [Сборка мусора](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="b0589-182">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="b0589-183">События</span><span class="sxs-lookup"><span data-stu-id="b0589-183">Events</span></span>

<span data-ttu-id="b0589-184">События позволяют классу или объекту уведомлять другие классы или объекты о возникновении каких-либо ситуаций.</span><span class="sxs-lookup"><span data-stu-id="b0589-184">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="b0589-185">Класс, отправляющий (или порождающий) событие, называется *издателем*, а классы, принимающие (или обрабатывающие) событие, называются *подписчиками*.</span><span class="sxs-lookup"><span data-stu-id="b0589-185">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="b0589-186">Дополнительные сведения о том, как порождаются и обрабатываются события, см. в разделе [События](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="b0589-186">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="b0589-187">Для объявления событий используйте [инструкцию Event](../../language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b0589-187">To declare events, use the [Event Statement](../../language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="b0589-188">Для вызова событий используйте [оператор RaiseEvent](../../language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b0589-188">To raise events, use the [RaiseEvent Statement](../../language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="b0589-189">Чтобы задать обработчики событий с помощью декларативного способа, используйте оператор [WithEvents](../../language-reference/modifiers/withevents.md) и предложение [Handles](../../language-reference/statements/handles-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="b0589-189">To specify event handlers using a declarative way, use the [WithEvents](../../language-reference/modifiers/withevents.md) statement and the [Handles](../../language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="b0589-190">Чтобы иметь возможность динамически добавлять, удалять и изменять обработчик событий, связанный с событием, используйте оператор [AddHandler](../../language-reference/statements/addhandler-statement.md) и [оператор RemoveHandler](../../language-reference/statements/removehandler-statement.md) вместе с [оператором AddressOf](../../language-reference/operators/addressof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b0589-190">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="b0589-191">Вложенные классы</span><span class="sxs-lookup"><span data-stu-id="b0589-191">Nested classes</span></span>

<span data-ttu-id="b0589-192">Класс, определенный внутри другого класса, называется *вложенным*.</span><span class="sxs-lookup"><span data-stu-id="b0589-192">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="b0589-193">По умолчанию вложенный класс является частным.</span><span class="sxs-lookup"><span data-stu-id="b0589-193">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="b0589-194">Чтобы создать экземпляр вложенного класса, укажите имя класса контейнера и имя вложенного класса, используя в качестве разделителя точку:</span><span class="sxs-lookup"><span data-stu-id="b0589-194">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="b0589-195">Модификаторы доступа и уровни доступа</span><span class="sxs-lookup"><span data-stu-id="b0589-195">Access modifiers and access levels</span></span>

<span data-ttu-id="b0589-196">С помощью *модификаторов доступа* все классы и члены классов могут указывать уровни доступа, предоставляемые другим классам.</span><span class="sxs-lookup"><span data-stu-id="b0589-196">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="b0589-197">Имеющиеся модификаторы доступа указаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="b0589-197">The following access modifiers are available:</span></span>

|<span data-ttu-id="b0589-198">Модификатор Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0589-198">Visual Basic Modifier</span></span>|<span data-ttu-id="b0589-199">Определение</span><span class="sxs-lookup"><span data-stu-id="b0589-199">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="b0589-200">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="b0589-200">Public</span></span>](../../language-reference/modifiers/public.md)|<span data-ttu-id="b0589-201">Доступ к типу или члену возможен из любого другого кода в той же сборке или другой сборке, ссылающейся на него.</span><span class="sxs-lookup"><span data-stu-id="b0589-201">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="b0589-202">Частная</span><span class="sxs-lookup"><span data-stu-id="b0589-202">Private</span></span>](../../language-reference/modifiers/private.md)|<span data-ttu-id="b0589-203">Доступ к типу или члену можно получить только из кода в том же классе.</span><span class="sxs-lookup"><span data-stu-id="b0589-203">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="b0589-204">От</span><span class="sxs-lookup"><span data-stu-id="b0589-204">Protected</span></span>](../../language-reference/modifiers/protected.md)|<span data-ttu-id="b0589-205">Доступ к типу или члену можно получить только из кода в том же классе или в производном классе.</span><span class="sxs-lookup"><span data-stu-id="b0589-205">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="b0589-206">Friend</span><span class="sxs-lookup"><span data-stu-id="b0589-206">Friend</span></span>](../../language-reference/modifiers/friend.md)|<span data-ttu-id="b0589-207">Доступ к типу или члену возможен из любого кода в той же сборке, но не из другой сборки.</span><span class="sxs-lookup"><span data-stu-id="b0589-207">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="b0589-208">Доступ к типу или члену возможен из любого кода в той же сборке, или из производного класса в другой сборке.</span><span class="sxs-lookup"><span data-stu-id="b0589-208">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="b0589-209">Дополнительные сведения см. [в разделе уровни доступа в Visual Basic](../language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b0589-209">For more information, see [Access levels in Visual Basic](../language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="b0589-210">Создание экземпляров классов</span><span class="sxs-lookup"><span data-stu-id="b0589-210">Instantiating classes</span></span>

<span data-ttu-id="b0589-211">Чтобы создать объект, необходимо создать экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="b0589-211">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="b0589-212">После создания экземпляра класса можно присваивать значения свойствам и полям экземпляра и вызывать методы класса.</span><span class="sxs-lookup"><span data-stu-id="b0589-212">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="b0589-213">Чтобы назначить значения свойствам в процессе создания экземпляра класса, используйте инициализаторы объектов:</span><span class="sxs-lookup"><span data-stu-id="b0589-213">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="b0589-214">Дополнительные сведения можно найти в разделе</span><span class="sxs-lookup"><span data-stu-id="b0589-214">For more information, see:</span></span>

- [<span data-ttu-id="b0589-215">Создание оператора</span><span class="sxs-lookup"><span data-stu-id="b0589-215">New Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="b0589-216">Инициализаторы объектов: именованные и анонимные типы</span><span class="sxs-lookup"><span data-stu-id="b0589-216">Object Initializers: Named and Anonymous Types</span></span>](../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="b0589-217">Общие классы и члены</span><span class="sxs-lookup"><span data-stu-id="b0589-217">Shared classes and members</span></span>

 <span data-ttu-id="b0589-218">Общий член класса является свойством, процедурой или полем, которое совместно используется всеми экземплярами класса.</span><span class="sxs-lookup"><span data-stu-id="b0589-218">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="b0589-219">Определение общего члена:</span><span class="sxs-lookup"><span data-stu-id="b0589-219">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="b0589-220">Чтобы получить доступ к общему члену, используйте имя класса без создания объекта этого класса:</span><span class="sxs-lookup"><span data-stu-id="b0589-220">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="b0589-221">Общие модули в Visual Basic имеют только общие члены и не могут быть созданы.</span><span class="sxs-lookup"><span data-stu-id="b0589-221">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="b0589-222">Общие члены также не могут получать доступ к свойствам, полям или методам, не являющимся общими</span><span class="sxs-lookup"><span data-stu-id="b0589-222">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="b0589-223">Дополнительные сведения см. в разделе:</span><span class="sxs-lookup"><span data-stu-id="b0589-223">For more information, see:</span></span>

- [<span data-ttu-id="b0589-224">Общий</span><span class="sxs-lookup"><span data-stu-id="b0589-224">Shared</span></span>](../../language-reference/modifiers/shared.md)
- [<span data-ttu-id="b0589-225">Оператор Module</span><span class="sxs-lookup"><span data-stu-id="b0589-225">Module Statement</span></span>](../../language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="b0589-226">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="b0589-226">Anonymous types</span></span>

<span data-ttu-id="b0589-227">Анонимные типы позволяют создавать объекты без написания определения класса для типа данных.</span><span class="sxs-lookup"><span data-stu-id="b0589-227">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="b0589-228">Вместо этого компилятор создает класс для вас.</span><span class="sxs-lookup"><span data-stu-id="b0589-228">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="b0589-229">Данный класс не имеет имени и содержит свойства, которые указаны при объявлении объекта.</span><span class="sxs-lookup"><span data-stu-id="b0589-229">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="b0589-230">Создание экземпляра анонимного типа:</span><span class="sxs-lookup"><span data-stu-id="b0589-230">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="b0589-231">Дополнительные сведения можно найти в разделе  [Анонимные типы](../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="b0589-231">For more information, see: [Anonymous Types](../language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="b0589-232">Наследование</span><span class="sxs-lookup"><span data-stu-id="b0589-232">Inheritance</span></span>

<span data-ttu-id="b0589-233">Наследование позволяет создавать новые классы, которые повторно используют, расширяют и изменяют поведение, определенное в другом классе.</span><span class="sxs-lookup"><span data-stu-id="b0589-233">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="b0589-234">Класс, члены которого наследуются, называется *базовым классом*, а класс, который наследует эти члены, называется *производным классом*.</span><span class="sxs-lookup"><span data-stu-id="b0589-234">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="b0589-235">Однако все классы в Visual Basic неявно наследуются от <xref:System.Object> класса, который поддерживает иерархию классов .NET, и предоставляет низкоуровневые службы для всех классов.</span><span class="sxs-lookup"><span data-stu-id="b0589-235">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="b0589-236">Visual Basic не поддерживает множественное наследование.</span><span class="sxs-lookup"><span data-stu-id="b0589-236">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="b0589-237">То есть можно указать только один базовый класс для производного класса.</span><span class="sxs-lookup"><span data-stu-id="b0589-237">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="b0589-238">Наследование от базового класса:</span><span class="sxs-lookup"><span data-stu-id="b0589-238">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="b0589-239">По умолчанию унаследовать класс можно от любого класса.</span><span class="sxs-lookup"><span data-stu-id="b0589-239">By default all classes can be inherited.</span></span> <span data-ttu-id="b0589-240">Однако можно указать, должен ли класс использоваться в качестве базового класса, или создать класс, который может использоваться только в качестве базового.</span><span class="sxs-lookup"><span data-stu-id="b0589-240">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="b0589-241">Указание, что класс не может использоваться в качестве базового класса:</span><span class="sxs-lookup"><span data-stu-id="b0589-241">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="b0589-242">Указание, что класс может использоваться только в качестве базового класса и нельзя создать экземпляр этого класса:</span><span class="sxs-lookup"><span data-stu-id="b0589-242">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="b0589-243">Дополнительные сведения можно найти в разделе</span><span class="sxs-lookup"><span data-stu-id="b0589-243">For more information, see:</span></span>

- [<span data-ttu-id="b0589-244">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="b0589-244">Inherits Statement</span></span>](../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="b0589-245">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="b0589-245">NotInheritable</span></span>](../../language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="b0589-246">MustInherit</span><span class="sxs-lookup"><span data-stu-id="b0589-246">MustInherit</span></span>](../../language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="b0589-247">Переопределение членов</span><span class="sxs-lookup"><span data-stu-id="b0589-247">Overriding members</span></span>

<span data-ttu-id="b0589-248">По умолчанию производный класс наследует все члены от своего базового класса.</span><span class="sxs-lookup"><span data-stu-id="b0589-248">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="b0589-249">Если необходимо изменить поведение унаследованного члена, необходимо переопределить его.</span><span class="sxs-lookup"><span data-stu-id="b0589-249">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="b0589-250">Т. е. в производном классе можно определить новую реализацию метода, свойства или события.</span><span class="sxs-lookup"><span data-stu-id="b0589-250">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="b0589-251">Следующие модификаторы используются для управления переопределением свойств и методов.</span><span class="sxs-lookup"><span data-stu-id="b0589-251">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="b0589-252">Модификатор Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0589-252">Visual Basic Modifier</span></span>|<span data-ttu-id="b0589-253">Определение</span><span class="sxs-lookup"><span data-stu-id="b0589-253">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="b0589-254">Overridable</span><span class="sxs-lookup"><span data-stu-id="b0589-254">Overridable</span></span>](../../language-reference/modifiers/overridable.md)|<span data-ttu-id="b0589-255">Разрешает переопределение члена класса в производном классе.</span><span class="sxs-lookup"><span data-stu-id="b0589-255">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="b0589-256">Переопределения</span><span class="sxs-lookup"><span data-stu-id="b0589-256">Overrides</span></span>](../../language-reference/modifiers/overrides.md)|<span data-ttu-id="b0589-257">Переопределяет виртуальный (переопределяемый) член в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="b0589-257">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="b0589-258">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="b0589-258">NotOverridable</span></span>](../../language-reference/modifiers/notoverridable.md)|<span data-ttu-id="b0589-259">Запрещает переопределение члена в наследующем классе.</span><span class="sxs-lookup"><span data-stu-id="b0589-259">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="b0589-260">MustOverride</span><span class="sxs-lookup"><span data-stu-id="b0589-260">MustOverride</span></span>](../../language-reference/modifiers/mustoverride.md)|<span data-ttu-id="b0589-261">Требует, чтобы член класса был переопределен в производном классе.</span><span class="sxs-lookup"><span data-stu-id="b0589-261">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="b0589-262">Shadows</span><span class="sxs-lookup"><span data-stu-id="b0589-262">Shadows</span></span>](../../language-reference/modifiers/shadows.md)|<span data-ttu-id="b0589-263">Скрывает член, наследуемый от базового класса</span><span class="sxs-lookup"><span data-stu-id="b0589-263">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="b0589-264">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="b0589-264">Interfaces</span></span>

<span data-ttu-id="b0589-265">Интерфейсы, как и классы, определяют набор свойств, методов и событий.</span><span class="sxs-lookup"><span data-stu-id="b0589-265">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="b0589-266">Но, в отличие от классов, интерфейсы не предоставляют реализацию.</span><span class="sxs-lookup"><span data-stu-id="b0589-266">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="b0589-267">Они реализуются классами, но определяются как отдельные от классов сущности.</span><span class="sxs-lookup"><span data-stu-id="b0589-267">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="b0589-268">Интерфейс представляет собой контракт, в котором класс, реализующий интерфейс, должен реализовывать каждый аспект этого интерфейса в точном соответствии с его определением.</span><span class="sxs-lookup"><span data-stu-id="b0589-268">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="b0589-269">Определение интерфейса:</span><span class="sxs-lookup"><span data-stu-id="b0589-269">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="b0589-270">Реализация интерфейса в классе:</span><span class="sxs-lookup"><span data-stu-id="b0589-270">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="b0589-271">Дополнительные сведения см. в разделе:</span><span class="sxs-lookup"><span data-stu-id="b0589-271">For more information, see:</span></span>

- [<span data-ttu-id="b0589-272">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="b0589-272">Interfaces</span></span>](../language-features/interfaces/index.md)
- [<span data-ttu-id="b0589-273">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="b0589-273">Interface Statement</span></span>](../../language-reference/statements/interface-statement.md)
- [<span data-ttu-id="b0589-274">Оператор Implements</span><span class="sxs-lookup"><span data-stu-id="b0589-274">Implements Statement</span></span>](../../language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="b0589-275">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="b0589-275">Generics</span></span>

<span data-ttu-id="b0589-276">Классы, структуры, интерфейсы и методы в .NET могут включать *Параметры типа* , определяющие типы объектов, которые они могут хранить или использовать.</span><span class="sxs-lookup"><span data-stu-id="b0589-276">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="b0589-277">Наиболее распространенным примером универсального шаблона является коллекция, в которой можно указать тип объектов, которые могут в ней храниться.</span><span class="sxs-lookup"><span data-stu-id="b0589-277">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="b0589-278">Определение универсального класса:</span><span class="sxs-lookup"><span data-stu-id="b0589-278">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="b0589-279">Создание экземпляра универсального класса:</span><span class="sxs-lookup"><span data-stu-id="b0589-279">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="b0589-280">Дополнительные сведения можно найти в разделе </span><span class="sxs-lookup"><span data-stu-id="b0589-280">For more information, see:</span></span>

- [<span data-ttu-id="b0589-281">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="b0589-281">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="b0589-282">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0589-282">Generic Types in Visual Basic</span></span>](../language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="b0589-283">Делегаты</span><span class="sxs-lookup"><span data-stu-id="b0589-283">Delegates</span></span>

 <span data-ttu-id="b0589-284">*Делегат* — это тип, который определяет сигнатуру метода и может обеспечивать связь с любым методом с совместимой сигнатурой.</span><span class="sxs-lookup"><span data-stu-id="b0589-284">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="b0589-285">Метод можно запустить (или вызвать) с помощью делегата.</span><span class="sxs-lookup"><span data-stu-id="b0589-285">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="b0589-286">Делегаты используются для передачи методов в качестве аргументов к другим методам.</span><span class="sxs-lookup"><span data-stu-id="b0589-286">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="b0589-287">Обработчики событий — это ничто иное, как методы, вызываемые с помощью делегатов.</span><span class="sxs-lookup"><span data-stu-id="b0589-287">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="b0589-288">Дополнительные сведения об использовании делегатов при обработке событий см. в разделе [События](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="b0589-288">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="b0589-289">Создание делегата:</span><span class="sxs-lookup"><span data-stu-id="b0589-289">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="b0589-290">Создание ссылки на метод, сигнатура которого соответствует сигнатуре, указанной делегатом:</span><span class="sxs-lookup"><span data-stu-id="b0589-290">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

<span data-ttu-id="b0589-291">Дополнительные сведения см. в разделе:</span><span class="sxs-lookup"><span data-stu-id="b0589-291">For more information, see:</span></span>

- [<span data-ttu-id="b0589-292">Делегаты</span><span class="sxs-lookup"><span data-stu-id="b0589-292">Delegates</span></span>](../language-features/delegates/index.md)
- [<span data-ttu-id="b0589-293">Оператор Delegate</span><span class="sxs-lookup"><span data-stu-id="b0589-293">Delegate Statement</span></span>](../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="b0589-294">Оператор AddressOf</span><span class="sxs-lookup"><span data-stu-id="b0589-294">AddressOf Operator</span></span>](../../language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="b0589-295">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b0589-295">See also</span></span>

- [<span data-ttu-id="b0589-296">Руководство по программированию на Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0589-296">Visual Basic Programming Guide</span></span>](../index.md)
