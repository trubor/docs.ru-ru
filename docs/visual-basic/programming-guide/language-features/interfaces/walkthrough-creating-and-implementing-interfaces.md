---
description: Дополнительные сведения см. в разделе Пошаговое руководство. Создание и реализация интерфейсов (Visual Basic)
title: Создание и реализация интерфейсов
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 058011d311fdecba626a59228816f9bced319c97
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468425"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="690f2-103">Пошаговое руководство. Создание и реализация интерфейсов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="690f2-103">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="690f2-104">Интерфейсы описывают характеристики свойств, методов и событий, но не содержат сведений о реализации до структур или классов.</span><span class="sxs-lookup"><span data-stu-id="690f2-104">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="690f2-105">В этом пошаговом руководстве показано, как объявить и реализовать интерфейс.</span><span class="sxs-lookup"><span data-stu-id="690f2-105">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="690f2-106">В этом пошаговом руководстве не содержатся сведения о создании пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="690f2-106">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="690f2-107">Определение интерфейса</span><span class="sxs-lookup"><span data-stu-id="690f2-107">To define an interface</span></span>
  
1. <span data-ttu-id="690f2-108">Откройте новый проект приложения Windows на Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="690f2-108">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="690f2-109">Добавьте в проект новый модуль, выбрав в меню **проект** пункт **Добавить модуль** .</span><span class="sxs-lookup"><span data-stu-id="690f2-109">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3. <span data-ttu-id="690f2-110">Присвойте новому модулю имя `Module1.vb` и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="690f2-110">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="690f2-111">Отобразится код для нового модуля.</span><span class="sxs-lookup"><span data-stu-id="690f2-111">The code for the new module is displayed.</span></span>  
  
4. <span data-ttu-id="690f2-112">Определите интерфейс с именем `TestInterface` в `Module1` , введя `Interface TestInterface` между `Module` `End Module` операторами и, а затем нажав клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="690f2-112">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="690f2-113">**Редактор кода** смещает `Interface` ключевое слово и добавляет `End Interface` оператор для формирования блока кода.</span><span class="sxs-lookup"><span data-stu-id="690f2-113">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5. <span data-ttu-id="690f2-114">Определите свойство, метод и событие для интерфейса, поместив следующий код между `Interface` `End Interface` операторами и:</span><span class="sxs-lookup"><span data-stu-id="690f2-114">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="690f2-115">Реализация</span><span class="sxs-lookup"><span data-stu-id="690f2-115">Implementation</span></span>

 <span data-ttu-id="690f2-116">Вы можете заметить, что синтаксис, используемый для объявления членов интерфейса, отличается от синтаксиса, используемого для объявления членов класса.</span><span class="sxs-lookup"><span data-stu-id="690f2-116">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="690f2-117">Это различие отражает тот факт, что интерфейсы не могут содержать код реализации.</span><span class="sxs-lookup"><span data-stu-id="690f2-117">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="690f2-118">Реализация интерфейса</span><span class="sxs-lookup"><span data-stu-id="690f2-118">To implement the interface</span></span>
  
1. <span data-ttu-id="690f2-119">Добавьте класс с именем, `ImplementationClass` добавив следующий оператор в `Module1` , после `End Interface` оператора, но перед `End Module` оператором, а затем нажав клавишу ВВОД:</span><span class="sxs-lookup"><span data-stu-id="690f2-119">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="690f2-120">При работе в интегрированной среде разработки **Редактор кода** предоставляет соответствующий `End Class` оператор при нажатии клавиши ВВОД.</span><span class="sxs-lookup"><span data-stu-id="690f2-120">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2. <span data-ttu-id="690f2-121">Добавьте следующий `Implements` оператор в `ImplementationClass` , который именует интерфейс, реализуемый классом:</span><span class="sxs-lookup"><span data-stu-id="690f2-121">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="690f2-122">При указании отдельно от других элементов в верхней части класса или структуры `Implements` оператор указывает, что класс или структура реализуют интерфейс.</span><span class="sxs-lookup"><span data-stu-id="690f2-122">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="690f2-123">При работе в интегрированной среде разработки **Редактор кода** реализует члены класса, необходимые `TestInterface` при нажатии клавиши ВВОД, и вы можете пропустить следующий шаг.</span><span class="sxs-lookup"><span data-stu-id="690f2-123">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3. <span data-ttu-id="690f2-124">Если вы не работаете в интегрированной среде разработки, необходимо реализовать все члены интерфейса `MyInterface` .</span><span class="sxs-lookup"><span data-stu-id="690f2-124">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="690f2-125">Добавьте следующий код в `ImplementationClass` для реализации `Event1` , `Method1` и `Prop1` :</span><span class="sxs-lookup"><span data-stu-id="690f2-125">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="690f2-126">`Implements`Оператор именует интерфейс и член интерфейса, который реализуется.</span><span class="sxs-lookup"><span data-stu-id="690f2-126">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4. <span data-ttu-id="690f2-127">Завершите определение `Prop1` , добавив закрытое поле в класс, который сохранил значение свойства:</span><span class="sxs-lookup"><span data-stu-id="690f2-127">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="690f2-128">Возврат значения `pval` из метода доступа get свойства.</span><span class="sxs-lookup"><span data-stu-id="690f2-128">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="690f2-129">Задайте значение `pval` в методе доступа к набору свойств.</span><span class="sxs-lookup"><span data-stu-id="690f2-129">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. <span data-ttu-id="690f2-130">Завершите определение `Method1` , добавив следующий код.</span><span class="sxs-lookup"><span data-stu-id="690f2-130">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="690f2-131">Тестирование реализации интерфейса</span><span class="sxs-lookup"><span data-stu-id="690f2-131">To test the implementation of the interface</span></span>
  
1. <span data-ttu-id="690f2-132">Щелкните правой кнопкой мыши форму запуска проекта в **Обозреватель решений** и выберите пункт **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="690f2-132">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="690f2-133">Редактор отображает класс для начальной формы.</span><span class="sxs-lookup"><span data-stu-id="690f2-133">The editor displays the class for your startup form.</span></span> <span data-ttu-id="690f2-134">По умолчанию вызывается форма запуска `Form1` .</span><span class="sxs-lookup"><span data-stu-id="690f2-134">By default, the startup form is called `Form1`.</span></span>  
  
2. <span data-ttu-id="690f2-135">Добавьте в `testInstance` класс следующее поле `Form1` :</span><span class="sxs-lookup"><span data-stu-id="690f2-135">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="690f2-136">Если объявить `testInstance` как `WithEvents` , `Form1` класс может управлять его событиями.</span><span class="sxs-lookup"><span data-stu-id="690f2-136">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3. <span data-ttu-id="690f2-137">Добавьте следующий обработчик событий в `Form1` класс для обработки событий, вызванных `testInstance` :</span><span class="sxs-lookup"><span data-stu-id="690f2-137">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. <span data-ttu-id="690f2-138">Добавьте подпрограммы с именем `Test` в `Form1` класс для проверки класса реализации:</span><span class="sxs-lookup"><span data-stu-id="690f2-138">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="690f2-139">`Test`Процедура создает экземпляр класса, реализующего `MyInterface` , присваивает этот экземпляр `testInstance` полю, устанавливает свойство и запускает метод через интерфейс.</span><span class="sxs-lookup"><span data-stu-id="690f2-139">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5. <span data-ttu-id="690f2-140">Добавьте код для вызова `Test` процедуры из `Form1 Load` процедуры формы запуска:</span><span class="sxs-lookup"><span data-stu-id="690f2-140">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. <span data-ttu-id="690f2-141">Выполните `Test` процедуру, нажав клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="690f2-141">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="690f2-142">Отображается сообщение «Prop1 имело значение 9».</span><span class="sxs-lookup"><span data-stu-id="690f2-142">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="690f2-143">После нажатия кнопки ОК отображается сообщение "параметр X для Method1 равен 5".</span><span class="sxs-lookup"><span data-stu-id="690f2-143">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="690f2-144">Нажмите кнопку ОК, после чего появится сообщение "обработчик событий захватил событие".</span><span class="sxs-lookup"><span data-stu-id="690f2-144">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="690f2-145">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="690f2-145">See also</span></span>

- [<span data-ttu-id="690f2-146">Оператор Implements</span><span class="sxs-lookup"><span data-stu-id="690f2-146">Implements Statement</span></span>](../../../language-reference/statements/implements-statement.md)
- [<span data-ttu-id="690f2-147">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="690f2-147">Interfaces</span></span>](index.md)
- [<span data-ttu-id="690f2-148">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="690f2-148">Interface Statement</span></span>](../../../language-reference/statements/interface-statement.md)
- [<span data-ttu-id="690f2-149">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="690f2-149">Event Statement</span></span>](../../../language-reference/statements/event-statement.md)
