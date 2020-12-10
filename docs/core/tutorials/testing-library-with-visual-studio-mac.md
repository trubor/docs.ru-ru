---
title: Тестирование библиотеки классов .NET с помощью Visual Studio для Mac
description: Создайте проект модульного теста для библиотеки классов .NET. Проверьте правильность работы библиотеки классов .NET с помощью модульных тестов.
ms.date: 11/18/2020
ms.openlocfilehash: 02d5aa74258ec15c5447b23246a3c7e9c61a6760
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599530"
---
# <a name="test-a-net-class-library-using-visual-studio"></a><span data-ttu-id="074af-104">Тестирование библиотеки классов .NET с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="074af-104">Test a .NET class library using Visual Studio</span></span>

<span data-ttu-id="074af-105">В этом руководстве показано, как автоматизировать модульное тестирование путем добавления тестового проекта в решение.</span><span class="sxs-lookup"><span data-stu-id="074af-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="074af-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="074af-106">Prerequisites</span></span>

- <span data-ttu-id="074af-107">В этом руководстве используется решение, созданное при работе со статьей [Создание библиотеки классов .NET с помощью Visual Studio для Mac](library-with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="074af-107">This tutorial works with the solution that you create in [Create a .NET class library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="074af-108">Создание проекта модульного теста</span><span class="sxs-lookup"><span data-stu-id="074af-108">Create a unit test project</span></span>

<span data-ttu-id="074af-109">Модульные тесты обеспечивают автоматическое тестирование программного обеспечения во время разработки и публикации.</span><span class="sxs-lookup"><span data-stu-id="074af-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="074af-110">[MSTest](https://github.com/Microsoft/testfx-docs) — это одна из трех доступных для выбора платформ тестирования.</span><span class="sxs-lookup"><span data-stu-id="074af-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="074af-111">Другими являются [xUnit](https://xunit.net/) и [nUnit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="074af-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="074af-112">Запустите Visual Studio для Mac.</span><span class="sxs-lookup"><span data-stu-id="074af-112">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="074af-113">Откройте решение`ClassLibraryProjects`, созданное при работе со статьей [Создание библиотеки классов .NET с помощью Visual Studio для Mac](library-with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="074af-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET class library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="074af-114">На панели **Решение** щелкните решение `ClassLibraryProjects` при нажатой клавише <kbd>CTRL</kbd> и выберите пункт **Добавить** > **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="074af-114">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="074af-115">В узле **Web and Console** (Интернет и консоль) диалогового окна **Создание проекта** выберите **Тесты**.</span><span class="sxs-lookup"><span data-stu-id="074af-115">In the **New Project** dialog, select **Tests** from the **Web and Console** node.</span></span> <span data-ttu-id="074af-116">Выберите **Проект MSTest** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="074af-116">Select the **MSTest Project** followed by **Next**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="Создание тестового проекта в диалоговом окне Создание проекта Visual Studio для Mac":::

1. <span data-ttu-id="074af-118">Выберите **.NET 5.0** в качестве **целевой платформы**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="074af-118">Select **.NET 5.0** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="074af-119">Назовите новый проект StringLibraryTest и выберите **Создать**.</span><span class="sxs-lookup"><span data-stu-id="074af-119">Name the new project "StringLibraryTest" and select **Create**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-new-project-name.png" alt-text="Диалоговое окно Создание проекта Visual Studio для Mac с именем проекта":::

   <span data-ttu-id="074af-121">Visual Studio создает файл класса, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="074af-121">Visual Studio creates a class file with the following code:</span></span>

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   <span data-ttu-id="074af-122">Исходный код, созданный шаблоном модульного теста, выполняет следующие действия.</span><span class="sxs-lookup"><span data-stu-id="074af-122">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="074af-123">Он импортирует пространство имен <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, которое содержит типы, используемые для модульного тестирования.</span><span class="sxs-lookup"><span data-stu-id="074af-123">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="074af-124">Он применяет атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> к классу `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="074af-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="074af-125">Он применяет атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> для `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="074af-125">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to `TestMethod1`.</span></span>

   <span data-ttu-id="074af-126">При запуске модульного теста автоматически выполняются все методы теста, помеченные атрибутом [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), в тестовом классе, помеченном атрибутом [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute).</span><span class="sxs-lookup"><span data-stu-id="074af-126">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="074af-127">Добавление ссылки на проект</span><span class="sxs-lookup"><span data-stu-id="074af-127">Add a project reference</span></span>

<span data-ttu-id="074af-128">Чтобы тестовый проект работал с классом `StringLibrary`, добавьте ссылку на проект `StringLibrary`.</span><span class="sxs-lookup"><span data-stu-id="074af-128">For the test project to work with the `StringLibrary` class, add a reference to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="074af-129">На панели **Решение** щелкните элемент **Зависимости** при нажатой клавише <kbd>CTRL</kbd> в области **StringLibraryTest**.</span><span class="sxs-lookup"><span data-stu-id="074af-129">In the **Solution** pad, <kbd>ctrl</kbd>-click **Dependencies** under **StringLibraryTest**.</span></span> <span data-ttu-id="074af-130">Выберите пункт **Добавить ссылку** в контекстном меню.</span><span class="sxs-lookup"><span data-stu-id="074af-130">Select **Add Reference** from the context menu.</span></span>

1. <span data-ttu-id="074af-131">В диалоговом окне **Ссылки** выберите проект **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="074af-131">In the **References** dialog, select the **StringLibrary** project.</span></span> <span data-ttu-id="074af-132">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="074af-132">Select **OK**.</span></span>

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Диалоговое окно Изменение ссылок Visual Studio для Mac":::

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="074af-134">Добавление и выполнение методов модульного теста</span><span class="sxs-lookup"><span data-stu-id="074af-134">Add and run unit test methods</span></span>

<span data-ttu-id="074af-135">При запуске модульного теста Visual Studio выполняет каждый метод, помеченный атрибутом <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>, в классе, помеченном атрибутом <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>.</span><span class="sxs-lookup"><span data-stu-id="074af-135">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="074af-136">Метод теста завершается, когда происходит первый сбой или когда все тесты, содержащиеся в методе, будут успешно выполнены.</span><span class="sxs-lookup"><span data-stu-id="074af-136">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="074af-137">В самых распространенных тестах вызываются члены класса <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="074af-137">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="074af-138">Многие методы утверждения (Assert) принимают по крайней мере два параметра, из которых один представляет ожидаемый результат теста, а второй — фактический результат теста.</span><span class="sxs-lookup"><span data-stu-id="074af-138">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="074af-139">Наиболее популярные из этих методов класса `Assert` перечислены в следующей таблице:</span><span class="sxs-lookup"><span data-stu-id="074af-139">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="074af-140">Методы утверждения</span><span class="sxs-lookup"><span data-stu-id="074af-140">Assert methods</span></span>     | <span data-ttu-id="074af-141">Функция</span><span class="sxs-lookup"><span data-stu-id="074af-141">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="074af-142">Проверяет равенство двух значений или объектов.</span><span class="sxs-lookup"><span data-stu-id="074af-142">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="074af-143">Утверждение не выполняется, если значения или объекты не равны.</span><span class="sxs-lookup"><span data-stu-id="074af-143">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="074af-144">Проверяет, что две объектные переменные ссылаются на один и тот же объект.</span><span class="sxs-lookup"><span data-stu-id="074af-144">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="074af-145">Утверждение не выполняется, если переменные ссылаются на разные объекты.</span><span class="sxs-lookup"><span data-stu-id="074af-145">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="074af-146">Проверяет, что условие имеет значение `false`.</span><span class="sxs-lookup"><span data-stu-id="074af-146">Verifies that a condition is `false`.</span></span> <span data-ttu-id="074af-147">Утверждение не выполняется, если условие имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="074af-147">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="074af-148">Проверяет, что объект не имеет значение `null`.</span><span class="sxs-lookup"><span data-stu-id="074af-148">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="074af-149">Утверждение не выполняется, если объект является `null`.</span><span class="sxs-lookup"><span data-stu-id="074af-149">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="074af-150">Вы можете также использовать метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> в методе теста, чтобы указать тип исключения, которое он должен создавать.</span><span class="sxs-lookup"><span data-stu-id="074af-150">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="074af-151">Такой тест считается не выполненным, если заявленное исключение не было создано.</span><span class="sxs-lookup"><span data-stu-id="074af-151">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="074af-152">Для тестирования метода `StringLibrary.StartsWithUpper` необходимо предоставить несколько строк, которые начинаются с символов верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="074af-152">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="074af-153">Предполагается, что в этих случаях метод возвратит `true`, поэтому можно вызвать метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="074af-153">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="074af-154">Представьте также несколько строк, которые не начинаются с символов верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="074af-154">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="074af-155">Предполагается, что в этих случаях метод возвратит `false`, поэтому можно вызвать метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="074af-155">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="074af-156">Так как ваш метод библиотеки обрабатывает строки, нам нужно проверить правильность обработки [пустых строк (`String.Empty`)](xref:System.String.Empty) (так называется допустимая строка, которая не содержит символов и для которой свойство <xref:System.String.Length> имеет значение 0) и строки `null`, которая не была инициализирована.</span><span class="sxs-lookup"><span data-stu-id="074af-156">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="074af-157">Метод `StartsWithUpper` можно вызвать напрямую как статический метод и передать ему один аргумент типа <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="074af-157">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="074af-158">Или метод `StartsWithUpper` можно вызвать как метод расширения для переменной `string`, которой назначено значение `null`.</span><span class="sxs-lookup"><span data-stu-id="074af-158">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="074af-159">Вы определите три метода, каждый из которых вызывает метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> для каждого элемента в массиве строк.</span><span class="sxs-lookup"><span data-stu-id="074af-159">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="074af-160">Вы вызовете перегруженную версию метода, которая позволяет указать сообщение об ошибке, отображаемое в случае сбоя теста.</span><span class="sxs-lookup"><span data-stu-id="074af-160">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="074af-161">В этом сообщении определяется строка, вызвавшая сбой.</span><span class="sxs-lookup"><span data-stu-id="074af-161">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="074af-162">Создание методов теста:</span><span class="sxs-lookup"><span data-stu-id="074af-162">To create the test methods:</span></span>

1. <span data-ttu-id="074af-163">Откройте файл *UnitTest1.cs* и замените его содержимое на следующий код:</span><span class="sxs-lookup"><span data-stu-id="074af-163">Open the *UnitTest1.cs* file and replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="074af-164">Тест на символы верхнего регистра в методе `TestStartsWithUpper` включает заглавную греческую букву "альфа" (U+0391) и заглавную кириллическую букву "М" (U+041C).</span><span class="sxs-lookup"><span data-stu-id="074af-164">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="074af-165">Тест на символы нижнего регистра в методе `TestDoesNotStartWithUpper` включает строчную греческую букву "альфа" (U+03B1) и строчную кириллическую букву "г" (U+0433).</span><span class="sxs-lookup"><span data-stu-id="074af-165">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="074af-166">В строке меню выберите **Файл** > **Сохранить как**.</span><span class="sxs-lookup"><span data-stu-id="074af-166">On the menu bar, select **File** > **Save As**.</span></span> <span data-ttu-id="074af-167">В диалоговом окне проверьте, что поле **Кодировка** имеет значение **Юникод (UTF-8)** .</span><span class="sxs-lookup"><span data-stu-id="074af-167">In the dialog, make sure that **Encoding** is set to **Unicode (UTF-8)**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Диалоговое окно Сохранить файл как в Visual Studio":::

1. <span data-ttu-id="074af-169">Когда вам предложат заменить существующий файл, выберите **Заменить**.</span><span class="sxs-lookup"><span data-stu-id="074af-169">When you're asked if you want to replace the existing file, select **Replace**.</span></span>

   <span data-ttu-id="074af-170">Если вы не сохраните исходный код в кодировке UTF8, Visual Studio может сохранить его как файл ASCII.</span><span class="sxs-lookup"><span data-stu-id="074af-170">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="074af-171">В этом случае среде выполнения не удастся правильно раскодировать символы UTF8 за пределами стандартного диапазона ASCII, и результаты теста будут неправильными.</span><span class="sxs-lookup"><span data-stu-id="074af-171">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="074af-172">Откройте панель **Модульные тесты** в правой части экрана.</span><span class="sxs-lookup"><span data-stu-id="074af-172">Open the **Unit Tests** panel on the right side of the screen.</span></span> <span data-ttu-id="074af-173">В меню выберите **Просмотр** > **Тесты**.</span><span class="sxs-lookup"><span data-stu-id="074af-173">Select **View** > **Tests** from the menu.</span></span>

1. <span data-ttu-id="074af-174">Щелкните значок **Закрепить**, чтобы панель не закрывалась.</span><span class="sxs-lookup"><span data-stu-id="074af-174">Click the **Dock** icon to keep the panel open.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Значок закрепления на панели Модульные тесты в Visual Studio для Mac":::

1. <span data-ttu-id="074af-176">Нажмите кнопку **Запустить все**.</span><span class="sxs-lookup"><span data-stu-id="074af-176">Click the **Run All** button.</span></span>

   <span data-ttu-id="074af-177">Все тесты пройдены.</span><span class="sxs-lookup"><span data-stu-id="074af-177">All tests pass.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Ожидаемое прохождение теста в Visual Studio для Mac":::

## <a name="handle-test-failures"></a><span data-ttu-id="074af-179">Обработка сбоев теста</span><span class="sxs-lookup"><span data-stu-id="074af-179">Handle test failures</span></span>

<span data-ttu-id="074af-180">Выполняя разработку на основе тестирования (TDD), вы сначала пишете тесты, и они завершаются сбоем при первом запуске.</span><span class="sxs-lookup"><span data-stu-id="074af-180">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="074af-181">Затем вы добавляете код в приложение, и тест успешно выполняется.</span><span class="sxs-lookup"><span data-stu-id="074af-181">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="074af-182">В рамках этого учебника вы создали тест после написания кода приложения для его проверки, поэтому тест был пройден.</span><span class="sxs-lookup"><span data-stu-id="074af-182">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="074af-183">Чтобы проверить, завершается ли тест ошибкой, как и ожидается, добавьте недопустимое значение во входные данные теста.</span><span class="sxs-lookup"><span data-stu-id="074af-183">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="074af-184">Измените массив `words` в методе `TestDoesNotStartWithUpper`, включив в него строку "Error".</span><span class="sxs-lookup"><span data-stu-id="074af-184">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="074af-185">Сохранять файл не требуется, поскольку при сборке решения для выполнения тестов Visual Studio автоматически сохраняет открытые файлы.</span><span class="sxs-lookup"><span data-stu-id="074af-185">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="074af-186">Повторно запустите тесты.</span><span class="sxs-lookup"><span data-stu-id="074af-186">Run the tests again.</span></span>

   <span data-ttu-id="074af-187">В этот раз в окне **Обозреватель тестов** будет указано, что два теста выполнены успешно, а третий завершился ошибкой.</span><span class="sxs-lookup"><span data-stu-id="074af-187">This time, the **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="Окно Обозреватель тестов с тестами, которые завершились ошибкой":::

1. <span data-ttu-id="074af-189">Щелкните непройденный тест `TestDoesNotStartWithUpper` при нажатой клавише <kbd>CTRL</kbd> и в контекстном меню выберите **Показать панель результатов**.</span><span class="sxs-lookup"><span data-stu-id="074af-189"><kbd>ctrl</kbd>-click the failed test, `TestDoesNotStartWithUpper`, and select **Show Results Pad** from the context menu.</span></span>

   <span data-ttu-id="074af-190">На панели **Результаты** появится сообщение, созданное методом утверждения: "Assert.IsFalse failed.</span><span class="sxs-lookup"><span data-stu-id="074af-190">The **Results** pad displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="074af-191">Expected for 'Error': false; actual: True".</span><span class="sxs-lookup"><span data-stu-id="074af-191">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="074af-192">Из-за этого сбоя строки в массиве, расположенные после слова "Error", не проверялись.</span><span class="sxs-lookup"><span data-stu-id="074af-192">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="Окно Обозреватель тестов с сообщением о том, что утверждение IsFalse ошибочно":::

1. <span data-ttu-id="074af-194">Удалите строку "Error", которую вы добавили на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="074af-194">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="074af-195">Еще раз запустите тест. Теперь тесты будут пройдены.</span><span class="sxs-lookup"><span data-stu-id="074af-195">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="074af-196">Тестирование версии выпуска для библиотеки</span><span class="sxs-lookup"><span data-stu-id="074af-196">Test the Release version of the library</span></span>

<span data-ttu-id="074af-197">Теперь, когда все тесты пройдены при выполнении сборки в режиме отладки, следует запустить все тесты еще раз, теперь уже для сборки библиотеки в режиме выпуска.</span><span class="sxs-lookup"><span data-stu-id="074af-197">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="074af-198">Некоторые факторы, например оптимизации компилятора, иногда могут вызывать разное поведение сборки в режимах отладки и выпуска.</span><span class="sxs-lookup"><span data-stu-id="074af-198">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="074af-199">Протестируйте сборку выпуска следующим образом.</span><span class="sxs-lookup"><span data-stu-id="074af-199">To test the Release build:</span></span>

1. <span data-ttu-id="074af-200">В панели инструментов Visual Studio измените конфигурацию сборки с режима **Отладка** на **Выпуск**.</span><span class="sxs-lookup"><span data-stu-id="074af-200">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="Панель инструментов Visual Studio с выделенной сборкой выпуска":::

1. <span data-ttu-id="074af-202">На панели **Решение** щелкните проект **StringLibrary** при нажатой клавише <kbd>CTRL</kbd> и выберите в контекстном меню пункт **Сборка**, чтобы выполнить повторную компиляцию библиотеки.</span><span class="sxs-lookup"><span data-stu-id="074af-202">In the **Solution** pad, <kbd>ctrl</kbd>-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="Контекстное меню проекта StringLibrary с командой сборки":::

1. <span data-ttu-id="074af-204">Повторно запустите модульные тесты.</span><span class="sxs-lookup"><span data-stu-id="074af-204">Run the unit tests again.</span></span>

   <span data-ttu-id="074af-205">Все тесты будут пройдены.</span><span class="sxs-lookup"><span data-stu-id="074af-205">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="074af-206">Отладка тестов</span><span class="sxs-lookup"><span data-stu-id="074af-206">Debug tests</span></span>

<span data-ttu-id="074af-207">Если в качестве IDE вы используете Visual Studio для Mac, то можете следовать инструкциям из статьи [Учебник. Отладка консольного приложения .NET с помощью Visual Studio для Mac](debugging-with-visual-studio-mac.md), чтобы выполнить отладку кода с помощью проекта модульного теста.</span><span class="sxs-lookup"><span data-stu-id="074af-207">If you're using Visual Studio for Mac as your IDE, you can use the same process shown in [Tutorial: Debug a .NET console application using Visual Studio for Mac](debugging-with-visual-studio-mac.md) to debug code using your unit test project.</span></span> <span data-ttu-id="074af-208">Вместо запуска проекта приложения *ShowCase* щелкните проект **StringLibraryTests**, удерживая клавишу <kbd>CTRL</kbd> и выберите элемент **Начать отладку проекта** в контекстном меню.</span><span class="sxs-lookup"><span data-stu-id="074af-208">Instead of starting the *ShowCase* app project, <kbd>ctrl</kbd>-click the **StringLibraryTests** project, and select **Start Debugging Project** from the context menu.</span></span>

<span data-ttu-id="074af-209">Visual Studio запускает тестовый проект с присоединенным отладчиком.</span><span class="sxs-lookup"><span data-stu-id="074af-209">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="074af-210">Выполнение будет прервано в любой точке останова, добавленной в тестовый проект или базовый код библиотеки.</span><span class="sxs-lookup"><span data-stu-id="074af-210">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="074af-211">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="074af-211">Additional resources</span></span>

* [<span data-ttu-id="074af-212">Модульное тестирование в .NET</span><span class="sxs-lookup"><span data-stu-id="074af-212">Unit testing in .NET</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="074af-213">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="074af-213">Next steps</span></span>

<span data-ttu-id="074af-214">В этом руководстве вы выполнили модульное тестирование библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="074af-214">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="074af-215">Чтобы сделать библиотеку доступной другим пользователям, опубликуйте ее в [NuGet](https://nuget.org) в качестве пакета.</span><span class="sxs-lookup"><span data-stu-id="074af-215">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="074af-216">Чтобы узнать, как это делать, следуйте указаниям в руководстве по NuGet:</span><span class="sxs-lookup"><span data-stu-id="074af-216">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="074af-217">Создание и публикация пакета (dotnet CLI)</span><span class="sxs-lookup"><span data-stu-id="074af-217">Create and publish a package (dotnet CLI)</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="074af-218">Если библиотека опубликована как пакет NuGet, ее могут устанавливать и использовать другие пользователи.</span><span class="sxs-lookup"><span data-stu-id="074af-218">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="074af-219">Чтобы узнать, как это делать, следуйте указаниям в руководстве по NuGet:</span><span class="sxs-lookup"><span data-stu-id="074af-219">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="074af-220">Установка и использование пакета Visual Studio для Mac</span><span class="sxs-lookup"><span data-stu-id="074af-220">Install and use a package in Visual Studio for Mac</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

<span data-ttu-id="074af-221">Библиотеку не нужно распространять как пакет.</span><span class="sxs-lookup"><span data-stu-id="074af-221">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="074af-222">Ее можно объединить с консольным приложением, где она используется.</span><span class="sxs-lookup"><span data-stu-id="074af-222">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="074af-223">Чтобы узнать, как опубликовать консольное приложение, ознакомьтесь с предыдущим руководством в этой серии:</span><span class="sxs-lookup"><span data-stu-id="074af-223">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="074af-224">Публикация консольного приложения .NET с помощью Visual Studio для Mac</span><span class="sxs-lookup"><span data-stu-id="074af-224">Publish a .NET console application using Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
