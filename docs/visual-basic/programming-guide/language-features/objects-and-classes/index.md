---
description: 'Дополнительные сведения: объекты и классы в Visual Basic'
title: Объекты и классы
ms.date: 05/26/2020
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 9cefcc117c9dd4ac42940f342dbf75d8ddb4f41d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462728"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="4f7b7-103">Объекты и классы Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4f7b7-103">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="4f7b7-104">*Объект* представляет собой сочетание кода и данных, которое рассматривается как единое целое.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-104">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="4f7b7-105">Объект может быть частью приложения, как, например, элемент управления или форма.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-105">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="4f7b7-106">Также объектом может являться само приложение в целом.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-106">An entire application can also be an object.</span></span>

<span data-ttu-id="4f7b7-107">При создании приложения в Visual Basic вы постоянно работаете с объектами.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-107">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="4f7b7-108">Можно использовать объекты, предоставляемые Visual Basic, такие как элементы управления, формы и объекты доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-108">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="4f7b7-109">Кроме того, в приложении Visual Basic можно использовать объекты других приложений.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-109">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="4f7b7-110">Вы даже можете создать собственные объекты и определить для них дополнительные свойства и методы.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-110">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="4f7b7-111">Объекты выполняют функцию готовых блоков для создания программ — вы можете один раз написать фрагмент кода и использовать его многократно.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-111">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="4f7b7-112">В этой статье мы подробно расскажем вам про объекты.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-112">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="4f7b7-113">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="4f7b7-113">Objects and classes</span></span>

<span data-ttu-id="4f7b7-114">Каждый объект в Visual Basic определяется *классом*.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-114">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="4f7b7-115">Класс описывает переменные, свойства, процедуры и события объекта.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-115">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="4f7b7-116">Объекты являются экземплярами классов. Определив класс, вы можете создать из него любое количество объектов.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-116">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="4f7b7-117">Взаимосвязь между объектом и его классом можно проиллюстрировать на примере печенья и формочки для печенья.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-117">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="4f7b7-118">Форма для печенья — это класс.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-118">The cookie cutter is the class.</span></span> <span data-ttu-id="4f7b7-119">Она определяет характеристики каждого печенья, то есть размер и форму.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-119">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="4f7b7-120">Класс используется для создания объектов.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-120">The class is used to create objects.</span></span> <span data-ttu-id="4f7b7-121">Отдельные печенья — это и есть объекты.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-121">The objects are the cookies.</span></span>

<span data-ttu-id="4f7b7-122">Необходимо создать объект, чтобы получить доступ к его членам, за исключением [`Shared`](../../../language-reference/modifiers/shared.md) элементов, к которым можно получить доступ без объекта класса.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-122">You must create an object before you can access its members, except for [`Shared`](../../../language-reference/modifiers/shared.md) members which can be accessed without an object of the class.</span></span>

### <a name="create-an-object-from-a-class"></a><span data-ttu-id="4f7b7-123">Создание объекта из класса</span><span class="sxs-lookup"><span data-stu-id="4f7b7-123">Create an object from a class</span></span>

1. <span data-ttu-id="4f7b7-124">Определите, из какого класса нужно создать объект, или определите собственный класс.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-124">Determine from which class you want to create an object, or define your own class.</span></span> <span data-ttu-id="4f7b7-125">Пример:</span><span class="sxs-lookup"><span data-stu-id="4f7b7-125">For example:</span></span>

   ```vb
   Public Class Customer
       Public Property AccountNumber As Integer
   End Class
   ```

2. <span data-ttu-id="4f7b7-126">Напишите [оператор Dim](../../../language-reference/statements/dim-statement.md) для создания переменной, значением которой будет новый экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-126">Write a [Dim Statement](../../../language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="4f7b7-127">Переменная должна иметь тип, соответствующий нужному классу.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-127">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As Customer
   ```

3. <span data-ttu-id="4f7b7-128">Добавьте ключевое слово [New Operator](../../../language-reference/operators/new-operator.md), сохранить новый экземпляр класса в переменную.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-128">Add the [New Operator](../../../language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New Customer
   ```

4. <span data-ttu-id="4f7b7-129">Теперь члены класса будут доступны через переменную объекта.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-129">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.AccountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="4f7b7-130">Всегда, если это возможно, следует объявлять переменную с типом того класса, который будет в ней храниться.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-130">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="4f7b7-131">Этот принцип называется *раннее связывание*.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-131">This is called *early binding*.</span></span> <span data-ttu-id="4f7b7-132">Если во время компиляции тип класса не известен, можно использовать *позднее связывание*, объявив переменную с [типом данных объекта](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="4f7b7-132">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="4f7b7-133">Но помните, что позднее связывание может снижать производительность и ограничивать доступ к членам объекта во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-133">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="4f7b7-134">Дополнительные сведения см. в статье [Object Variable Declaration](../variables/object-variable-declaration.md) (Объявление объектной переменной).</span><span class="sxs-lookup"><span data-stu-id="4f7b7-134">For more information, see [Object Variable Declaration](../variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="4f7b7-135">Несколько экземпляров</span><span class="sxs-lookup"><span data-stu-id="4f7b7-135">Multiple instances</span></span>

<span data-ttu-id="4f7b7-136">Обычно все только что созданные из класса объекты идентичны друг другу.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-136">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="4f7b7-137">Но с того момента, когда они возникают как отдельные объекты, их переменные и свойства изменяются независимо от других экземпляров объекта.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-137">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="4f7b7-138">Например, если вы добавляете в форму три флажка, каждый из объектов флажков является экземпляром класса <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-138">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="4f7b7-139">Отдельные объекты <xref:System.Windows.Forms.CheckBox> имеют одинаковый набор характеристик и возможностей (свойства, переменные, процедуры и события), которые определены в этом классе.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-139">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="4f7b7-140">Но каждый из объектов имеет собственное имя, каждый можно отдельно включать и отключать, а также перемещать в другое место на форме.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-140">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="4f7b7-141">Члены объекта</span><span class="sxs-lookup"><span data-stu-id="4f7b7-141">Object members</span></span>

<span data-ttu-id="4f7b7-142">Объект является элементом приложения и представляет собой *экземпляр* некоторого класса.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-142">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="4f7b7-143">Поля, свойства, методы и события являются составными частями объекта, и совокупно именуются *членами* объекта.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-143">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="4f7b7-144">Доступ к членам</span><span class="sxs-lookup"><span data-stu-id="4f7b7-144">Member Access</span></span>

<span data-ttu-id="4f7b7-145">Чтобы обратиться к члену объекта, нужно указать имя соответствующей переменной объекта и имя нужного члена, отделив его точкой (`.`).</span><span class="sxs-lookup"><span data-stu-id="4f7b7-145">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="4f7b7-146">В следующем примере задается свойство <xref:System.Windows.Forms.Control.Text%2A> объекта <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-146">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="4f7b7-147">Список членов IntelliSense</span><span class="sxs-lookup"><span data-stu-id="4f7b7-147">IntelliSense listing of members</span></span>

<span data-ttu-id="4f7b7-148">Технология IntelliSense перечисляет члены класса, когда вы обращаетесь к функции списка членов, например вводите точку (`.`) в контексте доступа к члену.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-148">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="4f7b7-149">Если точка ставится после имени переменной, объявленной как экземпляр некоторого класса, IntelliSense перечисляет все члены экземпляра, но опускает общие члены.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-149">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="4f7b7-150">Если точка ставится после имени класса, то IntelliSense перечисляет все общие члены, но опускает члены экземпляра.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-150">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="4f7b7-151">Дополнительные сведения см. в разделе [Using IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="4f7b7-151">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="4f7b7-152">Поля и свойства</span><span class="sxs-lookup"><span data-stu-id="4f7b7-152">Fields and properties</span></span>

<span data-ttu-id="4f7b7-153">*Поля* и *свойства* представляют сведения, содержащиеся в объекте.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-153">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="4f7b7-154">Их значения можно задавать и получать с помощью инструкций присваивания, так же как для локальных переменных в процедуре.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-154">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="4f7b7-155">В следующем примере мы получаем значение свойства <xref:System.Windows.Forms.Control.Width%2A> и устанавливаем значение свойства <xref:System.Windows.Forms.Control.ForeColor%2A> для объекта <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-155">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="4f7b7-156">Поле можно также называть *переменная-член*.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-156">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="4f7b7-157">Процедуры свойств удобно использовать в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-157">Use property procedures when:</span></span>

- <span data-ttu-id="4f7b7-158">Вы хотите контролировать, когда и как значения будут задаваться и извлекаться.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-158">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="4f7b7-159">Свойство имеет строго определенный набор значений, которые требуется проверять.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-159">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="4f7b7-160">Изменение значения приводит к существенному изменению состояния объекта (как, например, значение свойства `IsVisible`).</span><span class="sxs-lookup"><span data-stu-id="4f7b7-160">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="4f7b7-161">Изменение значения свойства изменяет другие внутренние переменные или значения других свойств.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-161">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="4f7b7-162">Перед установкой или получением свойства необходимо выполнить определенный набор действий.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-162">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="4f7b7-163">Если выполняются следующие условия, можно использовать поля.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-163">Use fields when:</span></span>

- <span data-ttu-id="4f7b7-164">Значение имеет тип, для которого существует встроенная проверка.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-164">The value is of a self-validating type.</span></span> <span data-ttu-id="4f7b7-165">Например, если присвоить переменной типа `Boolean` любое значение, кроме `True` или `False`, создается ошибка или выполняется автоматическое преобразование данных.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-165">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="4f7b7-166">Допустимым является любое значение из диапазона, поддерживаемого для этого типа данных.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-166">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="4f7b7-167">Это справедливо для многих свойств с типами `Single` или `Double`.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-167">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="4f7b7-168">Свойство имеет тип данных `String` и не имеет ограничений на размер или значение строки.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-168">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="4f7b7-169">Дополнительные сведения см. в статье [Property Procedures (Visual Basic)](../procedures/property-procedures.md) (Процедуры свойств в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4f7b7-169">For more information, see [Property Procedures](../procedures/property-procedures.md).</span></span>

> [!TIP]
> <span data-ttu-id="4f7b7-170">Всегда оставляйте неконстантные поля частными.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-170">Always keep the non-constant fields private.</span></span> <span data-ttu-id="4f7b7-171">Если вы хотите сделать его общедоступным, используйте вместо него свойство.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-171">When you want to make it public, use a property instead.</span></span>

### <a name="methods"></a><span data-ttu-id="4f7b7-172">Методы</span><span class="sxs-lookup"><span data-stu-id="4f7b7-172">Methods</span></span>

<span data-ttu-id="4f7b7-173">Действие, которое выполняет объект, называется *методом*.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-173">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="4f7b7-174">Например, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> — это метод объекта <xref:System.Windows.Forms.ComboBox>, который добавляет новую запись в поле со списком.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-174">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="4f7b7-175">В следующем примере иллюстрируется использование метода <xref:System.Windows.Forms.Timer.Start%2A> объекта <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-175">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="4f7b7-176">По сути метод — это просто *процедура*, предоставляемая объектом.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-176">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="4f7b7-177">Дополнительные сведения см. в разделе [Procedures in Visual Basic](../procedures/index.md) (Процедуры в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4f7b7-177">For more information, see [Procedures](../procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="4f7b7-178">События</span><span class="sxs-lookup"><span data-stu-id="4f7b7-178">Events</span></span>

<span data-ttu-id="4f7b7-179">Событие — это действие, распознаваемое объектом, например, щелчок мышью или нажатие клавиши. Вы можете написать код для реагирования на эти события.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-179">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="4f7b7-180">События могут происходить в результате действий пользователя, выполнения программного кода или изменения состояния системы.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-180">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="4f7b7-181">Принято говорить, что код, который объявляет о наступлении события, *создает* это событие, а код, который реагирует на него, *обрабатывает* событие.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-181">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="4f7b7-182">Вы можете разработать собственные события, которые будут создаваться и обрабатываться созданными вами объектами.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-182">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="4f7b7-183">Дополнительные сведения см. в статье [Events (Visual Basic)](../events/index.md) (События в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4f7b7-183">For more information, see [Events](../events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="4f7b7-184">Члены экземпляров и общие члены</span><span class="sxs-lookup"><span data-stu-id="4f7b7-184">Instance members and shared members</span></span>

<span data-ttu-id="4f7b7-185">Когда вы создаете объект на основе класса, вы получаете экземпляр этого класса.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-185">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="4f7b7-186">Члены, которые объявлены без ключевого слова [Shared](../../../language-reference/modifiers/shared.md), являются *членами экземпляра*, то есть принадлежат исключительно одному определенному экземпляру.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-186">Members that are not declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="4f7b7-187">Член экземпляра в одном экземпляре никак не зависит от такого же члена в другом экземпляре того же класса.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-187">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="4f7b7-188">Например, переменная-член экземпляра может иметь разные значения в разных экземплярах.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-188">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="4f7b7-189">Члены, объявленные с ключевым словом `Shared`, являются *общими членами*, то есть относятся к классу в целом, а не к отдельному экземпляру.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-189">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="4f7b7-190">Существует только одна копия каждого общего члена, независимо от количества созданных экземпляров. Общий член определен даже в том случае, если не создано ни одного экземпляра.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-190">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="4f7b7-191">Например, общая переменная-член имеет только одно значение, которое можно получить из любого фрагмента кода, имеющего доступ к соответствующему классу.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-191">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-non-shared-members"></a><span data-ttu-id="4f7b7-192">Доступ к членам, не являющимся общими</span><span class="sxs-lookup"><span data-stu-id="4f7b7-192">Accessing non-shared members</span></span>

1. <span data-ttu-id="4f7b7-193">Убедитесь, что объект уже создан на основе нужного класса и сохранен в объектной переменной.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-193">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="4f7b7-194">В инструкции, которая обращается к члену, укажите имя объектной переменной с помощью *оператора доступа к члену* ( `.` ), а затем имя члена.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-194">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="4f7b7-195">Доступ к общим членам</span><span class="sxs-lookup"><span data-stu-id="4f7b7-195">Accessing shared members</span></span>

- <span data-ttu-id="4f7b7-196">Укажите имя класса с помощью *оператора доступа к члену* ( `.` ), а затем имя члена.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-196">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="4f7b7-197">К члену объекта, объявленному с ключевым словом `Shared`, нужно всегда обращаться напрямую через имя класса.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-197">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   Console.WriteLine("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="4f7b7-198">Если вы уже создали из этого класса объект, вы можете обращаться к члену, объявленному с ключевым словом `Shared`, и через переменную этого объекта.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-198">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="4f7b7-199">Различия между классами и модулями</span><span class="sxs-lookup"><span data-stu-id="4f7b7-199">Differences between classes and modules</span></span>

<span data-ttu-id="4f7b7-200">Основное различие между классами и модулями заключается в том, что для классов можно создавать экземпляры в качестве объектов. Модули таким свойством не обладают.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-200">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="4f7b7-201">Поскольку все данные стандартного модуля существуют только в одной копии, любые изменения общей переменной стандартного модуля, выполненные в любой части программы, будут влиять на все остальные обращения к значению этой переменной.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-201">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="4f7b7-202">Данные объекта, наоборот, существуют отдельно для каждого созданного экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-202">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="4f7b7-203">Еще одно важное различие состоит в том, что классы могут реализовывать интерфейсы, а модули — нет.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-203">Another difference is that unlike standard modules, classes can implement interfaces.</span></span> <span data-ttu-id="4f7b7-204">Если класс помечен модификатором [MustInherit](../../../language-reference/modifiers/mustinherit.md) , он не может быть создан напрямую.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-204">If a class is marked with the [MustInherit](../../../language-reference/modifiers/mustinherit.md) modifier, it can't be instantiated directly.</span></span> <span data-ttu-id="4f7b7-205">Однако он по-прежнему отличается от модуля, так как он может быть унаследован, пока модули не могут быть унаследованы.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-205">However, it's still different from a module as it can be inherited while modules can't be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="4f7b7-206">Если к члену класса применяется модификатор `Shared`, он устанавливается для класса в целом, а не для конкретного экземпляра класса.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-206">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="4f7b7-207">Прямой доступ к члену осуществляется через имя класса, так же как и к членам модуля.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-207">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="4f7b7-208">Также классы и модули используют разные области действия для своих членов.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-208">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="4f7b7-209">Члены, определенные внутри класса, относятся к определенному экземпляру класса и существуют только в то время, когда существует этот объект.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-209">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="4f7b7-210">Для обращения к членам класса из кода за пределами этого класса следует использовать полные имена в формате *Объект*.*Член*.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-210">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="4f7b7-211">С другой стороны, все объявленные в модуле члены по умолчанию свободно используются из любого места в коде, откуда есть доступ к этому модулю.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-211">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="4f7b7-212">Это означает, что переменные стандартного модуля являются фактически глобальными переменными. Они видимы из любой точки проекта и существуют в течение всего времени жизни программы.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-212">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="4f7b7-213">Повторное использование классов и объектов</span><span class="sxs-lookup"><span data-stu-id="4f7b7-213">Reusing classes and objects</span></span>

<span data-ttu-id="4f7b7-214">Объекты позволяют один раз объявить переменную или процедуру, а затем использовать ее везде, где потребуется.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-214">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="4f7b7-215">Например, если в приложении вам нужно средство проверки орфографии, то для него потребуется определить все необходимые переменные и служебные функции.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-215">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="4f7b7-216">Создав специальный класс для средства проверки орфографии, вы сможете использовать его снова в других приложениях, просто добавив ссылку на скомпилированную сборку.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-216">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="4f7b7-217">Более того, вы можете сэкономить время и силы, взяв готовый класс проверки орфографии, созданный ранее кем-то другим.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-217">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="4f7b7-218">.NET предоставляет множество примеров компонентов, доступных для использования.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-218">.NET provides many examples of components that are available for use.</span></span> <span data-ttu-id="4f7b7-219">В следующем примере используется класс <xref:System.TimeZone> в пространстве имен <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-219">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="4f7b7-220">Члены класса <xref:System.TimeZone> позволяют получить сведения о часовом поясе, выбранном на компьютере.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-220"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub ExamineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    Console.WriteLine(s)
End Sub
```

<span data-ttu-id="4f7b7-221">В предыдущем примере первый [оператор Dim](../../../language-reference/statements/dim-statement.md) объявляет переменную объекта типа <xref:System.TimeZone> и присваивает ей объект <xref:System.TimeZone>, который возвращается свойством <xref:System.TimeZone.CurrentTimeZone%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-221">In the preceding example, the first [Dim Statement](../../../language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="4f7b7-222">Отношения между объектами</span><span class="sxs-lookup"><span data-stu-id="4f7b7-222">Relationships among objects</span></span>

<span data-ttu-id="4f7b7-223">Между объектами могут существовать связи нескольких видов.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-223">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="4f7b7-224">В первую очередь эти связи подразделяются на *иерархию* и *вложенность*.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-224">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="4f7b7-225">Иерархические связи</span><span class="sxs-lookup"><span data-stu-id="4f7b7-225">Hierarchical relationship</span></span>

<span data-ttu-id="4f7b7-226">Если классы являются производным от других, более фундаментальных классов, такие отношения именуются *иерархической связью*.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-226">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="4f7b7-227">Иерархии классов удобны при описании объектов, являющихся подтипами более общих классов.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-227">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="4f7b7-228">Для следующего примера предположим, что нам нужен особый вид объекта <xref:System.Windows.Forms.Button>, который действует как обычная кнопка <xref:System.Windows.Forms.Button>, но в дополнение имеет метод, меняющий местами цвет фона и цвет переднего плана.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-228">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="define-a-class-that-is-derived-from-an-already-existing-class"></a><span data-ttu-id="4f7b7-229">Определить класс, производный от уже существующего класса</span><span class="sxs-lookup"><span data-stu-id="4f7b7-229">Define a class that is derived from an already existing class</span></span>

1. <span data-ttu-id="4f7b7-230">С помощью [инструкции Class](../../../language-reference/statements/class-statement.md) определите класс, из которого вы будете создавать нужный объект.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-230">Use a [Class Statement](../../../language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class ReversibleButton
   ```

   <span data-ttu-id="4f7b7-231">Код определения класса должен завершаться строкой `End Class`.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-231">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="4f7b7-232">По умолчанию интегрированная среда разработки (IDE) автоматически создает `End Class` при вводе инструкции `Class`.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-232">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="4f7b7-233">Сразу за инструкцией `Class` создайте [инструкцию Inherits](../../../language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4f7b7-233">Follow the `Class` statement immediately with an [Inherits Statement](../../../language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="4f7b7-234">Укажите класс, производным от которого будет этот новый класс.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-234">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="4f7b7-235">Новый класс наследует все члены, определенные в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-235">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="4f7b7-236">Добавьте код для дополнительных элементов, которые будет предоставлять производный класс.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-236">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="4f7b7-237">Например, вы можете добавить метод `ReverseColors`, тогда определение производного класса будет выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="4f7b7-237">For example, you might add a `ReverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class ReversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub ReverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="4f7b7-238">При создании объекта из `ReversibleButton` класса он может получить доступ ко всем членам <xref:System.Windows.Forms.Button> класса, а также к `ReverseColors` методу и другим новым элементам, определенным в `ReversibleButton` .</span><span class="sxs-lookup"><span data-stu-id="4f7b7-238">If you create an object from the `ReversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `ReverseColors` method and any other new members you define in `ReversibleButton`.</span></span>

<span data-ttu-id="4f7b7-239">Производные классы наследуют члены класса, на котором они основаны, что позволяет постепенно повышать сложность при продвижении по иерархии классов.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-239">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="4f7b7-240">Дополнительные сведения см. в статье [Inheritance Basics (Visual Basic)](inheritance-basics.md) (Основная информация о наследовании в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4f7b7-240">For more information, see [Inheritance Basics](inheritance-basics.md).</span></span>

### <a name="compile-the-code"></a><span data-ttu-id="4f7b7-241">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="4f7b7-241">Compile the code</span></span>

<span data-ttu-id="4f7b7-242">Убедитесь, что компилятор сможет получить доступ к классу, на основе которого вы намерены создать новый класс.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-242">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="4f7b7-243">Возможно, для этого придется указать его полное имя, как в предыдущем примере, или определить его пространства имен в [операторе Imports](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="4f7b7-243">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="4f7b7-244">Если класс находится в другом проекте, может потребоваться ссылка на этот проект.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-244">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="4f7b7-245">Дополнительные сведения см. в статье [Управление ссылками в проекте](/visualstudio/ide/managing-references-in-a-project).</span><span class="sxs-lookup"><span data-stu-id="4f7b7-245">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="4f7b7-246">Отношение вложения</span><span class="sxs-lookup"><span data-stu-id="4f7b7-246">Containment relationship</span></span>

<span data-ttu-id="4f7b7-247">Также объекты могут быть связаны *отношением вложения*.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-247">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="4f7b7-248">Объекты-контейнеры на логическом уровне содержат в себе другие объекты.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-248">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="4f7b7-249">Например, объект <xref:System.OperatingSystem> логически содержит объект <xref:System.Version>, который он возвращает с помощью свойства <xref:System.OperatingSystem.Version%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-249">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="4f7b7-250">Важно понимать, что физически объект-контейнер не содержит в себе других объектов.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-250">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="4f7b7-251">Коллекции</span><span class="sxs-lookup"><span data-stu-id="4f7b7-251">Collections</span></span>

<span data-ttu-id="4f7b7-252">В качестве примера объектов-контейнеров можно привести *коллекции*.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-252">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="4f7b7-253">Коллекции представляют собой группы однотипных перечисляемых объектов.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-253">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="4f7b7-254">Visual Basic поддерживает конкретный синтаксис в области [For Each... Оператор Next](../../../language-reference/statements/for-each-next-statement.md) , позволяющий выполнять итерацию по элементам коллекции.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-254">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="4f7b7-255">Кроме того, коллекции часто позволяют использовать свойство <xref:Microsoft.VisualBasic.Collection.Item%2A> для обращения к элементам по индексу или по уникальной строке.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-255">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="4f7b7-256">Коллекции иногда проще в использовании, чем массивы, поскольку они позволяют добавлять или удалять элементы без использования индексов.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-256">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="4f7b7-257">Благодаря простоте использования коллекции часто применяются для хранения форм и элементов управления.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-257">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="4f7b7-258">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="4f7b7-258">Related topics</span></span>

<span data-ttu-id="4f7b7-259">[Пошаговое руководство. Определение классов](walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="4f7b7-259">[Walkthrough: Defining Classes](walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="4f7b7-260">Пошаговые инструкции по созданию класса.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-260">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="4f7b7-261">[Перегруженные свойства и методы](overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="4f7b7-261">[Overloaded Properties and Methods](overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="4f7b7-262">Перегруженные свойства и методы</span><span class="sxs-lookup"><span data-stu-id="4f7b7-262">Overloaded Properties and Methods</span></span>

<span data-ttu-id="4f7b7-263">[Основы наследования](inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="4f7b7-263">[Inheritance Basics](inheritance-basics.md)</span></span>\
<span data-ttu-id="4f7b7-264">Описание модификаторов наследования, переопределения методов и свойств, MyClass и MyBase.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-264">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="4f7b7-265">[Время существования объекта: как создаются и уничтожаются объекты](object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="4f7b7-265">[Object Lifetime: How Objects Are Created and Destroyed](object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="4f7b7-266">Вопросы создания и уничтожения экземпляров классов.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-266">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="4f7b7-267">[Анонимные типы](anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="4f7b7-267">[Anonymous Types](anonymous-types.md)</span></span>\
<span data-ttu-id="4f7b7-268">Описание создания и использования анонимных типов, которые позволяют создавать объекты без определения класса для типа данных.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-268">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="4f7b7-269">[Инициализаторы объектов: именованные и анонимные типы](object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="4f7b7-269">[Object Initializers: Named and Anonymous Types](object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="4f7b7-270">Описание инициализаторов объектов, которые позволяют создавать экземпляры именованных и анонимных типов с помощью одного выражения.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-270">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="4f7b7-271">[Как вывести имена и типы свойств в объявлениях анонимного типа](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="4f7b7-271">[How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="4f7b7-272">Обсуждение имен свойств и типов в контексте объявлений анонимных типов.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-272">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="4f7b7-273">Содержит примеры успешного и неуспешного вывода.</span><span class="sxs-lookup"><span data-stu-id="4f7b7-273">Provides examples of successful and unsuccessful inference.</span></span>
