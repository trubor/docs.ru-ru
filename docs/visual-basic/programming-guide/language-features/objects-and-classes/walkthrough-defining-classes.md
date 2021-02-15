---
description: Дополнительные сведения см. в разделе Пошаговое руководство. Определение классов (Visual Basic)
title: Определение классов
ms.date: 07/20/2015
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
ms.openlocfilehash: a97e04b92db3387966afa410d5697a05b482ae09
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438792"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="ea17f-103">Пошаговое руководство. Определение классов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea17f-103">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="ea17f-104">В этом пошаговом руководстве показано, как определить классы, которые затем можно использовать для создания объектов.</span><span class="sxs-lookup"><span data-stu-id="ea17f-104">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="ea17f-105">В нем также показано, как добавить свойства и методы в новый класс, и демонстрируется инициализация объекта.</span><span class="sxs-lookup"><span data-stu-id="ea17f-105">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="ea17f-106">Определение класса</span><span class="sxs-lookup"><span data-stu-id="ea17f-106">To define a class</span></span>
  
1. <span data-ttu-id="ea17f-107">Создайте проект, щелкнув **создать проект** в меню **файл** .</span><span class="sxs-lookup"><span data-stu-id="ea17f-107">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="ea17f-108">Откроется диалоговое окно **Новый проект** .</span><span class="sxs-lookup"><span data-stu-id="ea17f-108">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="ea17f-109">Выберите приложение Windows в списке шаблонов проектов Visual Basic, чтобы отобразить новый проект.</span><span class="sxs-lookup"><span data-stu-id="ea17f-109">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3. <span data-ttu-id="ea17f-110">Добавьте в проект новый класс, щелкнув **Добавить класс** в меню **проект** .</span><span class="sxs-lookup"><span data-stu-id="ea17f-110">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="ea17f-111">Откроется диалоговое окно **Добавление нового элемента**.</span><span class="sxs-lookup"><span data-stu-id="ea17f-111">The **Add New Item** dialog box appears.</span></span>  
  
4. <span data-ttu-id="ea17f-112">Выберите шаблон **класса** .</span><span class="sxs-lookup"><span data-stu-id="ea17f-112">Select the **Class** template.</span></span>  
  
5. <span data-ttu-id="ea17f-113">Присвойте новому классу имя `UserNameInfo.vb` , а затем нажмите кнопку **Добавить** , чтобы отобразить код для нового класса.</span><span class="sxs-lookup"><span data-stu-id="ea17f-113">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > <span data-ttu-id="ea17f-114">Можно использовать **Редактор кода** Visual Basic, чтобы добавить класс в форму запуска, введя `Class` ключевое слово, за которым следует имя нового класса.</span><span class="sxs-lookup"><span data-stu-id="ea17f-114">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="ea17f-115">**Редактор кода** предоставляет соответствующий `End Class` оператор.</span><span class="sxs-lookup"><span data-stu-id="ea17f-115">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6. <span data-ttu-id="ea17f-116">Определите частное поле для класса, добавив следующий код между `Class` `End Class` операторами и:</span><span class="sxs-lookup"><span data-stu-id="ea17f-116">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="ea17f-117">Объявление поля как означает, `Private` что его можно использовать только в пределах класса.</span><span class="sxs-lookup"><span data-stu-id="ea17f-117">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="ea17f-118">Можно сделать поля доступными извне класса, используя модификаторы доступа, такие как `Public` , которые обеспечивают дополнительный доступ.</span><span class="sxs-lookup"><span data-stu-id="ea17f-118">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="ea17f-119">Дополнительные сведения см. [в разделе уровни доступа в Visual Basic](../declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ea17f-119">For more information, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
7. <span data-ttu-id="ea17f-120">Определите свойство для класса, добавив следующий код:</span><span class="sxs-lookup"><span data-stu-id="ea17f-120">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. <span data-ttu-id="ea17f-121">Определите метод для класса, добавив следующий код:</span><span class="sxs-lookup"><span data-stu-id="ea17f-121">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="ea17f-122">Определите параметризованный конструктор для нового класса, добавив процедуру с именем `Sub New` :</span><span class="sxs-lookup"><span data-stu-id="ea17f-122">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="ea17f-123">`Sub New`Конструктор вызывается автоматически при создании объекта на основе этого класса.</span><span class="sxs-lookup"><span data-stu-id="ea17f-123">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="ea17f-124">Этот конструктор задает значение поля, в котором содержится имя пользователя.</span><span class="sxs-lookup"><span data-stu-id="ea17f-124">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="ea17f-125">Создание кнопки для проверки класса</span><span class="sxs-lookup"><span data-stu-id="ea17f-125">To create a button to test the class</span></span>
  
1. <span data-ttu-id="ea17f-126">Измените форму запуска на режим конструктора, щелкнув правой кнопкой мыши ее имя в **Обозреватель решений** а затем выбрав пункт **Конструктор представлений**.</span><span class="sxs-lookup"><span data-stu-id="ea17f-126">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="ea17f-127">По умолчанию форма запуска для проектов приложений Windows называется Form1. vb.</span><span class="sxs-lookup"><span data-stu-id="ea17f-127">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="ea17f-128">Откроется Главная форма.</span><span class="sxs-lookup"><span data-stu-id="ea17f-128">The main form will then appear.</span></span>  
  
2. <span data-ttu-id="ea17f-129">Добавьте кнопку в главную форму и дважды щелкните ее, чтобы отобразить код для `Button1_Click` обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="ea17f-129">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="ea17f-130">Добавьте следующий код для вызова тестовой процедуры:</span><span class="sxs-lookup"><span data-stu-id="ea17f-130">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="ea17f-131">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="ea17f-131">To run your application</span></span>
  
1. <span data-ttu-id="ea17f-132">Запустите приложение, нажав клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="ea17f-132">Run your application by pressing F5.</span></span> <span data-ttu-id="ea17f-133">Нажмите кнопку в форме, чтобы вызвать процедуру тестирования.</span><span class="sxs-lookup"><span data-stu-id="ea17f-133">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="ea17f-134">В нем отображается сообщение о том, что исходное значение `UserName` — «перебобби», поскольку процедура вызвала `Capitalize` метод объекта.</span><span class="sxs-lookup"><span data-stu-id="ea17f-134">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2. <span data-ttu-id="ea17f-135">Нажмите кнопку **ОК**, чтобы закрыть окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="ea17f-135">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="ea17f-136">`Button1 Click`Процедура изменяет значение `UserName` Свойства и отображает сообщение о том, что новое значение `UserName` равно "Ворден, Джо".</span><span class="sxs-lookup"><span data-stu-id="ea17f-136">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea17f-137">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ea17f-137">See also</span></span>

- <span data-ttu-id="ea17f-138">[Object-Oriented Programming (Visual Basic)](../../concepts/object-oriented-programming.md) (Объектно-ориентированное программирование на языке Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea17f-138">[Object-Oriented Programming (Visual Basic)](../../concepts/object-oriented-programming.md)</span></span>
- [<span data-ttu-id="ea17f-139">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="ea17f-139">Objects and Classes</span></span>](index.md)
