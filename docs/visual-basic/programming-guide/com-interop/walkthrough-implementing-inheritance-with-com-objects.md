---
description: Дополнительные сведения см. в разделе Пошаговое руководство. Реализация наследования с помощью COM-объектов (Visual Basic)
title: Пошаговое руководство. Реализация наследования с использованием COM-объектов
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: dc16990f25126cba52ef3ea457e8c3157c987c60
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438948"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="a7b95-103">Пошаговое руководство. Реализация наследования с использованием COM-объектов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7b95-103">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>

<span data-ttu-id="a7b95-104">Классы Visual Basic могут быть производными от `Public` классов в COM-объектах, даже тех, которые созданы в более ранних версиях Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a7b95-104">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="a7b95-105">Свойства и методы классов, унаследованных от COM-объектов, могут быть переопределены или перегружены точно так же, как свойства и методы любого другого базового класса могут быть переопределены или перегружены.</span><span class="sxs-lookup"><span data-stu-id="a7b95-105">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="a7b95-106">Наследование от COM-объектов полезно при наличии существующей библиотеки классов, которую не нужно перекомпилировать.</span><span class="sxs-lookup"><span data-stu-id="a7b95-106">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>

<span data-ttu-id="a7b95-107">В следующей процедуре показано, как использовать Visual Basic 6,0 для создания COM-объекта, содержащего класс, а затем использовать его в качестве базового класса.</span><span class="sxs-lookup"><span data-stu-id="a7b95-107">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="a7b95-108">Построение COM-объекта, используемого в этом пошаговом руководстве</span><span class="sxs-lookup"><span data-stu-id="a7b95-108">To build the COM object that is used in this walkthrough</span></span>

1. <span data-ttu-id="a7b95-109">В Visual Basic 6,0 откройте новый проект ActiveX DLL.</span><span class="sxs-lookup"><span data-stu-id="a7b95-109">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="a7b95-110">Будет создан проект с именем `Project1` .</span><span class="sxs-lookup"><span data-stu-id="a7b95-110">A project named `Project1` is created.</span></span> <span data-ttu-id="a7b95-111">Он имеет класс с именем `Class1` .</span><span class="sxs-lookup"><span data-stu-id="a7b95-111">It has a class named `Class1`.</span></span>

2. <span data-ttu-id="a7b95-112">В **обозревателе проектов** щелкните правой кнопкой мыши **проект1** и выберите **Свойства проект1**.</span><span class="sxs-lookup"><span data-stu-id="a7b95-112">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="a7b95-113">Откроется диалоговое окно **Свойства проекта** .</span><span class="sxs-lookup"><span data-stu-id="a7b95-113">The **Project Properties** dialog box is displayed.</span></span>

3. <span data-ttu-id="a7b95-114">На вкладке **Общие** диалогового окна **Свойства проекта** измените имя проекта, введя `ComObject1` в поле **имя проекта** .</span><span class="sxs-lookup"><span data-stu-id="a7b95-114">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>

4. <span data-ttu-id="a7b95-115">В **обозревателе проектов** щелкните правой кнопкой мыши `Class1` и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="a7b95-115">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="a7b95-116">Откроется окно **свойств** класса.</span><span class="sxs-lookup"><span data-stu-id="a7b95-116">The **Properties** window for the class is displayed.</span></span>

5. <span data-ttu-id="a7b95-117">Измените значение `Name` Свойства на `MathFunctions` .</span><span class="sxs-lookup"><span data-stu-id="a7b95-117">Change the `Name` property to `MathFunctions`.</span></span>

6. <span data-ttu-id="a7b95-118">В **обозревателе проектов** щелкните правой кнопкой мыши `MathFunctions` и выберите пункт **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="a7b95-118">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="a7b95-119">Откроется **Редактор кода** .</span><span class="sxs-lookup"><span data-stu-id="a7b95-119">The **Code Editor** is displayed.</span></span>

7. <span data-ttu-id="a7b95-120">Добавьте локальную переменную для хранения значения свойства:</span><span class="sxs-lookup"><span data-stu-id="a7b95-120">Add a local variable to hold the property value:</span></span>

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. <span data-ttu-id="a7b95-121">Добавьте процедуры свойств свойств `Let` и свойств `Get` :</span><span class="sxs-lookup"><span data-stu-id="a7b95-121">Add Property `Let` and Property `Get` property procedures:</span></span>

    ```vb
    Public Property Let Prop1(ByVal vData As Integer)
       'Used when assigning a value to the property.
       mvarProp1 = vData
    End Property
    Public Property Get Prop1() As Integer
       'Used when retrieving a property's value.
       Prop1 = mvarProp1
    End Property
    ```

9. <span data-ttu-id="a7b95-122">Добавьте функцию:</span><span class="sxs-lookup"><span data-stu-id="a7b95-122">Add a function:</span></span>

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. <span data-ttu-id="a7b95-123">Создайте и зарегистрируйте COM-объект, выбрав команду **сделать ComObject1.dll** в меню **файл** .</span><span class="sxs-lookup"><span data-stu-id="a7b95-123">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a7b95-124">Хотя можно также предоставить класс, созданный с помощью Visual Basic, в качестве COM-объекта, он не является настоящим COM-объектом и не может использоваться в этом пошаговом руководстве.</span><span class="sxs-lookup"><span data-stu-id="a7b95-124">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="a7b95-125">Дополнительные сведения см. [в разделе COM-взаимодействие в приложениях платформа .NET Framework](com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="a7b95-125">For details, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>

## <a name="interop-assemblies"></a><span data-ttu-id="a7b95-126">Сборки взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a7b95-126">Interop Assemblies</span></span>

<span data-ttu-id="a7b95-127">В следующей процедуре будет создана сборка взаимодействия, которая выступает в качестве моста между неуправляемым кодом (например, COM-объектом) и управляемым кодом, используемым Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a7b95-127">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="a7b95-128">Сборка взаимодействия, которую Visual Basic создает, обрабатывает множество деталей работы с COM-объектами, например *Маршалинг взаимодействия*, процесс упаковки параметров и возвращаемые значения в эквивалентные типы данных при их перемещении в COM-объекты и из них.</span><span class="sxs-lookup"><span data-stu-id="a7b95-128">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="a7b95-129">Ссылка в приложении Visual Basic указывает на сборку взаимодействия, а не на фактический COM-объект.</span><span class="sxs-lookup"><span data-stu-id="a7b95-129">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="a7b95-130">Использование COM-объекта с Visual Basic 2005 и более поздними версиями</span><span class="sxs-lookup"><span data-stu-id="a7b95-130">To use a COM object with Visual Basic 2005 and later versions</span></span>

1. <span data-ttu-id="a7b95-131">Откройте новый проект приложения Windows на Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a7b95-131">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="a7b95-132">В меню **Проект** выберите пункт **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="a7b95-132">On the **Project** menu, click **Add Reference**.</span></span>

     <span data-ttu-id="a7b95-133">Появится диалоговое окно **Добавление ссылки**.</span><span class="sxs-lookup"><span data-stu-id="a7b95-133">The **Add Reference** dialog box is displayed.</span></span>

3. <span data-ttu-id="a7b95-134">На вкладке **com** дважды щелкните `ComObject1` список **имя компонента** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="a7b95-134">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>

4. <span data-ttu-id="a7b95-135">В меню **Проект** выберите **Добавить новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="a7b95-135">On the **Project** menu, click **Add New Item**.</span></span>

     <span data-ttu-id="a7b95-136">Откроется диалоговое окно **Добавление нового элемента**.</span><span class="sxs-lookup"><span data-stu-id="a7b95-136">The **Add New Item** dialog box is displayed.</span></span>

5. <span data-ttu-id="a7b95-137">В области **шаблоны** щелкните **класс**.</span><span class="sxs-lookup"><span data-stu-id="a7b95-137">In the **Templates** pane, click **Class**.</span></span>

     <span data-ttu-id="a7b95-138">Имя файла по умолчанию `Class1.vb` отображается в поле **имя** .</span><span class="sxs-lookup"><span data-stu-id="a7b95-138">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="a7b95-139">Измените это поле на MathClass. vb и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="a7b95-139">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="a7b95-140">При этом создается класс с именем `MathClass` и отображается его код.</span><span class="sxs-lookup"><span data-stu-id="a7b95-140">This creates a class named `MathClass`, and displays its code.</span></span>

6. <span data-ttu-id="a7b95-141">Добавьте следующий код в начало, `MathClass` чтобы унаследовать от класса COM.</span><span class="sxs-lookup"><span data-stu-id="a7b95-141">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. <span data-ttu-id="a7b95-142">Перегрузите открытый метод базового класса, добавив следующий код в `MathClass` :</span><span class="sxs-lookup"><span data-stu-id="a7b95-142">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. <span data-ttu-id="a7b95-143">Расширьте унаследованный класс, добавив следующий код в `MathClass` :</span><span class="sxs-lookup"><span data-stu-id="a7b95-143">Extend the inherited class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

<span data-ttu-id="a7b95-144">Новый класс наследует свойства базового класса в COM-объекте, перегружает метод и определяет новый метод для расширения класса.</span><span class="sxs-lookup"><span data-stu-id="a7b95-144">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>

### <a name="to-test-the-inherited-class"></a><span data-ttu-id="a7b95-145">Тестирование наследуемого класса</span><span class="sxs-lookup"><span data-stu-id="a7b95-145">To test the inherited class</span></span>

1. <span data-ttu-id="a7b95-146">Добавьте кнопку в форму запуска, а затем дважды щелкните ее, чтобы просмотреть ее код.</span><span class="sxs-lookup"><span data-stu-id="a7b95-146">Add a button to your startup form, and then double-click it to view its code.</span></span>

2. <span data-ttu-id="a7b95-147">В `Click` процедуре обработчика событий кнопки добавьте следующий код, чтобы создать экземпляр `MathClass` и вызвать перегруженные методы:</span><span class="sxs-lookup"><span data-stu-id="a7b95-147">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. <span data-ttu-id="a7b95-148">Запустите проект, нажав клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="a7b95-148">Run the project by pressing F5.</span></span>

<span data-ttu-id="a7b95-149">При нажатии кнопки в форме `AddNumbers` метод сначала вызывается с `Short` номерами типов данных, а Visual Basic выбирает соответствующий метод из базового класса.</span><span class="sxs-lookup"><span data-stu-id="a7b95-149">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="a7b95-150">Второй вызов `AddNumbers` метода направляется в метод перегрузки из `MathClass` .</span><span class="sxs-lookup"><span data-stu-id="a7b95-150">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="a7b95-151">Третий вызов вызывает `SubtractNumbers` метод, который расширяет класс.</span><span class="sxs-lookup"><span data-stu-id="a7b95-151">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="a7b95-152">Свойство в базовом классе задается, и отображается значение.</span><span class="sxs-lookup"><span data-stu-id="a7b95-152">The property in the base class is set, and the value is displayed.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a7b95-153">Next Steps</span><span class="sxs-lookup"><span data-stu-id="a7b95-153">Next Steps</span></span>

<span data-ttu-id="a7b95-154">Возможно, вы заметили, что перегруженная `AddNumbers` функция имеет тот же тип данных, что и метод, унаследованный от базового класса COM-объекта.</span><span class="sxs-lookup"><span data-stu-id="a7b95-154">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="a7b95-155">Это обусловлено тем, что аргументы и параметры метода базового класса определяются как 16-разрядные целые числа в Visual Basic 6,0, но они предоставляются как 16-разрядные целые числа типа `Short` в более поздних версиях Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a7b95-155">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="a7b95-156">Новая функция принимает 32-разрядные целые числа и перегружает функцию базового класса.</span><span class="sxs-lookup"><span data-stu-id="a7b95-156">The new function accepts 32-bit integers, and overloads the base class function.</span></span>

<span data-ttu-id="a7b95-157">При работе с COM-объектами убедитесь, что вы проверите размер и типы данных параметров.</span><span class="sxs-lookup"><span data-stu-id="a7b95-157">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="a7b95-158">Например, при использовании объекта COM, который принимает объект коллекции Visual Basic 6,0 в качестве аргумента, вы не можете предоставить коллекцию из более поздней версии Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a7b95-158">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>

<span data-ttu-id="a7b95-159">Свойства и методы, унаследованные от классов COM, можно переопределить, то есть можно объявить локальное свойство или метод, который заменяет свойство или метод, наследуемые от базового класса COM.</span><span class="sxs-lookup"><span data-stu-id="a7b95-159">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="a7b95-160">Правила переопределения унаследованных COM-свойств похожи на правила переопределения других свойств и методов, за исключением следующих.</span><span class="sxs-lookup"><span data-stu-id="a7b95-160">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>

- <span data-ttu-id="a7b95-161">При переопределении любого свойства или метода, унаследованного от класса COM, необходимо переопределить все остальные унаследованные свойства и методы.</span><span class="sxs-lookup"><span data-stu-id="a7b95-161">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>

- <span data-ttu-id="a7b95-162">Свойства, использующие `ByRef` Параметры, не могут быть переопределены.</span><span class="sxs-lookup"><span data-stu-id="a7b95-162">Properties that use `ByRef` parameters cannot be overridden.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7b95-163">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a7b95-163">See also</span></span>

- [<span data-ttu-id="a7b95-164">COM-взаимодействие в приложениях .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a7b95-164">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="a7b95-165">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="a7b95-165">Inherits Statement</span></span>](../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="a7b95-166">Тип данных Short</span><span class="sxs-lookup"><span data-stu-id="a7b95-166">Short Data Type</span></span>](../../language-reference/data-types/short-data-type.md)
