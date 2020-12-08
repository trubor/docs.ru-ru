---
title: Создание библиотеки классов .NET с помощью Visual Studio
description: Сведения о создании библиотеки классов .NET с помощью Visual Studio.
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperfq1
ms.openlocfilehash: 6a3f61525ca86afc9ee71d56cbc9450862760ba4
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599516"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio"></a><span data-ttu-id="5a073-103">Учебник. Создание библиотеки классов .NET с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5a073-103">Tutorial: Create a .NET class library using Visual Studio</span></span>

<span data-ttu-id="5a073-104">В этом учебнике вы создадите простую библиотеку классов с одним методом для обработки строк.</span><span class="sxs-lookup"><span data-stu-id="5a073-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span>

<span data-ttu-id="5a073-105">*Библиотека классов* определяет типы и методы, которые могут быть вызваны из любого приложения.</span><span class="sxs-lookup"><span data-stu-id="5a073-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="5a073-106">Если библиотека предназначена для .NET Standard 2.0, она может быть вызвана любой реализацией .NET (включая .NET Framework), которая поддерживает .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="5a073-106">If the library targets .NET Standard 2.0, it can be called by any .NET implementation (including .NET Framework) that supports .NET Standard 2.0.</span></span> <span data-ttu-id="5a073-107">Если библиотека предназначена для .NET 5, ее можно вызвать с помощью любого приложения, предназначенного для .NET 5.</span><span class="sxs-lookup"><span data-stu-id="5a073-107">If the library targets .NET 5, it can be called by any application that targets .NET 5.</span></span> <span data-ttu-id="5a073-108">В этом учебнике показано, как ориентироваться на .NET 5.</span><span class="sxs-lookup"><span data-stu-id="5a073-108">This tutorial shows how to target .NET 5.</span></span>

<span data-ttu-id="5a073-109">Когда вы завершите создание библиотеки классов, можете распространить ее как пакет NuGet или включить как компонент в состав приложения, в котором она используется.</span><span class="sxs-lookup"><span data-stu-id="5a073-109">When you create a class library, you can distribute it as a NuGet package or as a component bundled with the application that uses it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5a073-110">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="5a073-110">Prerequisites</span></span>

- <span data-ttu-id="5a073-111">[Visual Studio 2019 версии 16.8 или более поздней](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) с установленной рабочей нагрузкой **Кроссплатформенная разработка .NET Core**.</span><span class="sxs-lookup"><span data-stu-id="5a073-111">[Visual Studio 2019 version 16.8 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="5a073-112">Пакет SDK для .NET 5.0 устанавливается автоматически при выборе этой рабочей нагрузки.</span><span class="sxs-lookup"><span data-stu-id="5a073-112">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span> <span data-ttu-id="5a073-113">В этом учебнике предполагается, что вы включили параметр **Показать все шаблоны .NET Core в новом проекте**, как показано в статье [Учебник. Создание консольного приложения .NET в Visual Studio](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="5a073-113">This tutorial assumes you have enabled **Show all .NET Core templates in the New project**, as shown in [Tutorial: Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="5a073-114">Создание решения</span><span class="sxs-lookup"><span data-stu-id="5a073-114">Create a solution</span></span>

<span data-ttu-id="5a073-115">Начните с создания пустого решения для размещения проекта библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="5a073-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="5a073-116">Решение Visual Studio служит контейнером для одного или нескольких проектов.</span><span class="sxs-lookup"><span data-stu-id="5a073-116">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="5a073-117">Вы будете добавлять дополнительные связанные проекты в одно решение.</span><span class="sxs-lookup"><span data-stu-id="5a073-117">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="5a073-118">Чтобы создать пустое решение, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="5a073-118">To create the blank solution:</span></span>

1. <span data-ttu-id="5a073-119">Запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a073-119">Start Visual Studio.</span></span>

2. <span data-ttu-id="5a073-120">На начальном экране выберите **Создать проект**.</span><span class="sxs-lookup"><span data-stu-id="5a073-120">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="5a073-121">В поле поиска на странице **Создание проекта** введите **решение**.</span><span class="sxs-lookup"><span data-stu-id="5a073-121">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="5a073-122">Выберите шаблон **Пустое решение** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="5a073-122">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio/blank-solution.png" alt-text="Шаблон пустого решения в Visual Studio":::

4. <span data-ttu-id="5a073-124">На странице **настройки нового проекта** введите **ClassLibraryProjects** в поле **Имя проекта**.</span><span class="sxs-lookup"><span data-stu-id="5a073-124">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="5a073-125">Затем нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="5a073-125">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="5a073-126">Создание проекта библиотеки классов</span><span class="sxs-lookup"><span data-stu-id="5a073-126">Create a class library project</span></span>

1. <span data-ttu-id="5a073-127">Добавьте в решение новый проект библиотеки классов .NET с именем "StringLibrary".</span><span class="sxs-lookup"><span data-stu-id="5a073-127">Add a new .NET class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="5a073-128">Щелкните решение в **обозревателе решений** правой кнопкой мыши и выберите **Добавить** > **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="5a073-128">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="5a073-129">На странице **добавления нового проекта** введите в поле поиска **библиотека**.</span><span class="sxs-lookup"><span data-stu-id="5a073-129">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="5a073-130">Выберите **C#** или **Visual Basic** из списка языков, а затем — **Все платформы** из списка платформ.</span><span class="sxs-lookup"><span data-stu-id="5a073-130">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="5a073-131">Выберите шаблон **Библиотека классов**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="5a073-131">Choose the **Class Library** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="5a073-132">На странице **настройки нового проекта** введите **StringLibrary** в поле **Имя проекта**, а затем нажмите **Далее**.</span><span class="sxs-lookup"><span data-stu-id="5a073-132">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box, and then choose **Next**.</span></span>

   1. <span data-ttu-id="5a073-133">На странице **Дополнительные сведения** выберите **.NET 5.0 (текущая)** , а затем нажмите **Создать**.</span><span class="sxs-lookup"><span data-stu-id="5a073-133">On the **Additional information** page, select **.NET 5.0 (Current)**, and then choose **Create**.</span></span>

1. <span data-ttu-id="5a073-134">Проверьте, предназначена ли библиотека для правильной версии .NET.</span><span class="sxs-lookup"><span data-stu-id="5a073-134">Check to make sure that the library targets the correct version of .NET.</span></span> <span data-ttu-id="5a073-135">В **обозревателе решений** щелкните проект библиотеки правой кнопкой мыши и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="5a073-135">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="5a073-136">В текстовом поле **Целевая платформа** указано, что целевой платформой проекта является .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="5a073-136">The **Target Framework** text box shows that the project targets .NET 5.0.</span></span>

1. <span data-ttu-id="5a073-137">Если вы используете Visual Basic, удалите текст в поле **Корневое пространство имен**.</span><span class="sxs-lookup"><span data-stu-id="5a073-137">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   :::image type="content" source="./media/library-with-visual-studio/vb/library-project-properties.png" alt-text="Свойства проекта для библиотеки классов":::

   <span data-ttu-id="5a073-139">Для каждого проекта Visual Basic автоматически создает пространство имен, соответствующее имени проекта.</span><span class="sxs-lookup"><span data-stu-id="5a073-139">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="5a073-140">В этом учебнике вы определите пространство имен верхнего уровня с помощью ключевого слова [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) в файле кода.</span><span class="sxs-lookup"><span data-stu-id="5a073-140">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="5a073-141">Замените код, отображаемый в окне кода, для *Class1.cs* или *Class1.vb* следующим текстом, а затем сохраните файл.</span><span class="sxs-lookup"><span data-stu-id="5a073-141">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="5a073-142">Если нужный язык не отображается, измените выбор языка в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="5a073-142">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="5a073-143">Библиотека классов `UtilityLibraries.StringLibrary` содержит метод `StartsWithUpper`,</span><span class="sxs-lookup"><span data-stu-id="5a073-143">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="5a073-144">который возвращает значение <xref:System.Boolean>, указывающее, является ли первым символом текущего экземпляра строки символ верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="5a073-144">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="5a073-145">Символы верхнего регистра определяются по стандарту Юникод.</span><span class="sxs-lookup"><span data-stu-id="5a073-145">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="5a073-146">Метод <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> возвращает `true`, если символ является символом верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="5a073-146">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

   <span data-ttu-id="5a073-147">Метод `StartsWithUpper` реализуется как [метод расширения](../../csharp/programming-guide/classes-and-structs/extension-methods.md), чтобы вызывать его можно было так же, как любой член класса <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5a073-147">`StartsWithUpper` is implemented as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

1. <span data-ttu-id="5a073-148">В строке меню выберите **Сборка** > **Собрать решение** или нажмите клавиши <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>B</kbd>, чтобы убедиться, что проект компилируется без ошибок.</span><span class="sxs-lookup"><span data-stu-id="5a073-148">On the menu bar, select **Build** > **Build Solution** or press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd> to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="5a073-149">Добавление консольного приложения в решение</span><span class="sxs-lookup"><span data-stu-id="5a073-149">Add a console app to the solution</span></span>

<span data-ttu-id="5a073-150">Добавьте консольное приложение, использующее библиотеку классов.</span><span class="sxs-lookup"><span data-stu-id="5a073-150">Add a console application that uses the class library.</span></span> <span data-ttu-id="5a073-151">В приложении пользователю будет предложено ввести строку и сообщить, начинается ли строка с символа верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="5a073-151">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="5a073-152">Добавьте к решению новое консольное приложение .NET под названием "Демонстрация".</span><span class="sxs-lookup"><span data-stu-id="5a073-152">Add a new .NET console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="5a073-153">Щелкните решение в **Обозревателе решений** правой кнопкой мыши и выберите **Добавить** > **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="5a073-153">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="5a073-154">На странице **Добавить новый проект** введите в поле поиска **консоль**.</span><span class="sxs-lookup"><span data-stu-id="5a073-154">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="5a073-155">Выберите **C#** или **Visual Basic** из списка языков, а затем — **Все платформы** из списка платформ.</span><span class="sxs-lookup"><span data-stu-id="5a073-155">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="5a073-156">Выберите шаблон **Консольное приложение** и нажмите **Далее**.</span><span class="sxs-lookup"><span data-stu-id="5a073-156">Choose the **Console Application** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="5a073-157">На странице **Настроить новый проект** введите **Демонстрация** в поле **Имя проекта**.</span><span class="sxs-lookup"><span data-stu-id="5a073-157">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="5a073-158">Нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="5a073-158">Then choose **Next**.</span></span>

   1. <span data-ttu-id="5a073-159">На странице **Дополнительные сведения** выберите **.NET 5.0 (текущая)** в поле **Целевая платформа**.</span><span class="sxs-lookup"><span data-stu-id="5a073-159">On the **Additional information** page, select **.NET 5.0 (Current)** in the **Target Framework** box.</span></span> <span data-ttu-id="5a073-160">Затем нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="5a073-160">Then choose **Create**.</span></span>

1. <span data-ttu-id="5a073-161">В окне кода замените весь код файла *Program.cs* или *Program.vb* следующим текстом.</span><span class="sxs-lookup"><span data-stu-id="5a073-161">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="5a073-162">В этом коде используется переменная `row` для сохранения количества строк данных, записываемых в окно консоли.</span><span class="sxs-lookup"><span data-stu-id="5a073-162">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="5a073-163">Всякий раз, когда оно достигает значения 25 или превышает его, код очищает окно консоли и отображается сообщение для пользователя.</span><span class="sxs-lookup"><span data-stu-id="5a073-163">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="5a073-164">Сама программа предлагает пользователю ввести строку.</span><span class="sxs-lookup"><span data-stu-id="5a073-164">The program prompts the user to enter a string.</span></span> <span data-ttu-id="5a073-165">Она сообщает, начинается ли строка с символа верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="5a073-165">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="5a073-166">Если пользователь нажимает клавишу <kbd>ВВОД</kbd>, не введя никакой строки, приложение завершает свою работу и окно консоли закрывается.</span><span class="sxs-lookup"><span data-stu-id="5a073-166">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="5a073-167">Добавление ссылки на проект</span><span class="sxs-lookup"><span data-stu-id="5a073-167">Add a project reference</span></span>

<span data-ttu-id="5a073-168">Изначально новый проект консольного приложения не имеет доступа к библиотеке классов.</span><span class="sxs-lookup"><span data-stu-id="5a073-168">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="5a073-169">Чтобы позволить приложению вызывать методы из библиотеки классов, создайте в проекте ссылку на проект библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="5a073-169">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="5a073-170">В **обозревателе решений** щелкните правой кнопкой мыши узел **Зависимости** проекта `ShowCase` и выберите команду **Добавить ссылку на проект**.</span><span class="sxs-lookup"><span data-stu-id="5a073-170">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   :::image type="content" source="media/library-with-visual-studio/add-reference-context-menu.png" alt-text="Контекстное меню с пунктом &quot;Добавить ссылку&quot; в Visual Studio":::

1. <span data-ttu-id="5a073-172">В диалоговом окне **Диспетчер ссылок** выберите проект **StringLibrary**, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="5a073-172">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   :::image type="content" source="media/library-with-visual-studio/manage-project-references.png" alt-text="Диалоговое окно &quot;Диспетчер ссылок&quot; с выбранной StringLibrary":::

## <a name="run-the-app"></a><span data-ttu-id="5a073-174">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="5a073-174">Run the app</span></span>

1. <span data-ttu-id="5a073-175">В окне **Обозреватель решений** щелкните правой кнопкой мыши проект **ShowCase** и выберите команду **Назначить запускаемым проектом**.</span><span class="sxs-lookup"><span data-stu-id="5a073-175">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   :::image type="content" source="media/library-with-visual-studio/set-startup-project-context-menu.png" alt-text="Контекстное меню проекта с пунктом &quot;Назначить запускаемым проектом&quot; в Visual Studio":::

1. <span data-ttu-id="5a073-177">Нажмите клавиши <kbd>CTRL</kbd>+<kbd>F5</kbd>, чтобы скомпилировать и запустить программу без отладки.</span><span class="sxs-lookup"><span data-stu-id="5a073-177">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   :::image type="content" source="media/library-with-visual-studio/visual-studio-project-toolbar.png" alt-text="Панель инструментов проекта в Visual Studio c кнопкой отладки":::

1. <span data-ttu-id="5a073-179">Проверьте, как работает программа: вводите строки и нажимайте клавишу <kbd>ВВОД</kbd>. Чтобы выйти, нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="5a073-179">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Окно консоли с запущенным демонстрационным проектом ShowCase":::

## <a name="additional-resources"></a><span data-ttu-id="5a073-181">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="5a073-181">Additional resources</span></span>

* [<span data-ttu-id="5a073-182">Разработка библиотек с помощью .NET CLI</span><span class="sxs-lookup"><span data-stu-id="5a073-182">Develop libraries with the .NET CLI</span></span>](libraries.md)
* <span data-ttu-id="5a073-183">[Список версий .NET Standard и поддерживаемых ими платформ](../../standard/net-standard.md)</span><span class="sxs-lookup"><span data-stu-id="5a073-183">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5a073-184">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="5a073-184">Next steps</span></span>

<span data-ttu-id="5a073-185">В этом руководстве вы создали библиотеку классов.</span><span class="sxs-lookup"><span data-stu-id="5a073-185">In this tutorial, you created a class library.</span></span> <span data-ttu-id="5a073-186">В следующем руководстве вы узнаете, как выполнять модульное тестирование библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="5a073-186">In the next tutorial, you learn how to unit test the class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5a073-187">Модульное тестирование библиотеки классов .NET с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5a073-187">Unit test a .NET class library using Visual Studio</span></span>](testing-library-with-visual-studio.md)

<span data-ttu-id="5a073-188">Вы также можете пропустить автоматическое модульное тестирование и узнать, как можно распространить библиотеку, создав пакет NuGet:</span><span class="sxs-lookup"><span data-stu-id="5a073-188">Or you can skip automated unit testing and learn how to share the library by creating a NuGet package:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5a073-189">Создание и публикация пакета с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5a073-189">Create and publish a package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

<span data-ttu-id="5a073-190">Либо узнайте, как опубликовать консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="5a073-190">Or learn how to publish a console app.</span></span> <span data-ttu-id="5a073-191">При публикации консольного приложения из решения, созданного в этом руководстве, библиотека классов публикуется вместе с ним в виде файла *DLL*.</span><span class="sxs-lookup"><span data-stu-id="5a073-191">If you publish the console app from the solution you created in this tutorial, the class library goes with it as a *.dll* file.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5a073-192">Публикация консольного приложения .NET с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5a073-192">Publish a .NET console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
