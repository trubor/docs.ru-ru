---
title: Руководство по программированию на C#. Получение доступа к объектам взаимодействия
description: Узнайте о возможностях C#, которые упрощают доступ к объектам API Office. Используйте новые возможности для написания кода, который создает и отображает лист Excel.
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: 6c2c49a9fd55c406b69c02586a9b0e4a1d16ccd4
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479924"
---
# <a name="how-to-access-office-interop-objects-c-programming-guide"></a><span data-ttu-id="6abf9-104">Руководство по программированию на C#. Получение доступа к объектам взаимодействия</span><span class="sxs-lookup"><span data-stu-id="6abf9-104">How to access Office interop objects (C# Programming Guide)</span></span>

<span data-ttu-id="6abf9-105">В C# предусмотрены функции, которые упрощают доступ к объектам API Office.</span><span class="sxs-lookup"><span data-stu-id="6abf9-105">C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="6abf9-106">К новым функциям относятся именованные и необязательные аргументы, новый тип `dynamic`, а также возможность передавать аргументы ссылочным параметрам в методах COM, как если бы они были параметрами значений.</span><span class="sxs-lookup"><span data-stu-id="6abf9-106">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>

<span data-ttu-id="6abf9-107">В этом разделе с использованием новых функций будет написан код, который создает и отображает лист Microsoft Office Excel.</span><span class="sxs-lookup"><span data-stu-id="6abf9-107">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="6abf9-108">После этого будет написан код для добавления документа Office Word, который содержит значок, ссылающийся на лист Excel.</span><span class="sxs-lookup"><span data-stu-id="6abf9-108">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>

<span data-ttu-id="6abf9-109">Для выполнения данного пошагового руководства на компьютере должны быть установлены Microsoft Office Excel 2007 и Microsoft Office Word 2007 или более поздние версии продуктов.</span><span class="sxs-lookup"><span data-stu-id="6abf9-109">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="6abf9-110">Создание нового проекта консольного приложения</span><span class="sxs-lookup"><span data-stu-id="6abf9-110">To create a new console application</span></span>

1. <span data-ttu-id="6abf9-111">Запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6abf9-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="6abf9-112">В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-112">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="6abf9-113">Откроется диалоговое окно **Новый проект** .</span><span class="sxs-lookup"><span data-stu-id="6abf9-113">The **New Project** dialog box appears.</span></span>

3. <span data-ttu-id="6abf9-114">В области **Установленные шаблоны** разверните узел **Visual C#** и выберите **Windows**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-114">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="6abf9-115">В верхней части диалогового окна **Новый проект** в качестве целевой платформы необходимо выбрать **.NET Framework 4** (или более позднюю версию).</span><span class="sxs-lookup"><span data-stu-id="6abf9-115">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>

5. <span data-ttu-id="6abf9-116">В области **Шаблоны** щелкните **Консольное приложение**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-116">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="6abf9-117">Введите имя проекта в поле **Имя**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-117">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="6abf9-118">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-118">Click **OK**.</span></span>

     <span data-ttu-id="6abf9-119">В **обозревателе решений** появится новый проект.</span><span class="sxs-lookup"><span data-stu-id="6abf9-119">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-references"></a><span data-ttu-id="6abf9-120">Добавление ссылок</span><span class="sxs-lookup"><span data-stu-id="6abf9-120">To add references</span></span>

1. <span data-ttu-id="6abf9-121">В **обозревателе решений** щелкните имя проекта правой кнопкой мыши и выберите пункт **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-121">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="6abf9-122">Откроется диалоговое окно **Добавление ссылки**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-122">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="6abf9-123">На странице **Сборки** в списке **Имя компонента** выберите **Microsoft.Office.Interop.Word**, а затем, удерживая нажатой клавишу CTRL, выберите **Microsoft.Office.Interop.Excel**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-123">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="6abf9-124">Если сборки отсутствуют, может потребоваться проверить, что они установлены и отображаются.</span><span class="sxs-lookup"><span data-stu-id="6abf9-124">If you do not see the assemblies, you may need to ensure they are installed and displayed.</span></span> <span data-ttu-id="6abf9-125">См. практическое руководство по [ установке основных сборок взаимодействия Microsoft Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span><span class="sxs-lookup"><span data-stu-id="6abf9-125">See [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span></span>

3. <span data-ttu-id="6abf9-126">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-126">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="6abf9-127">Добавление необходимых директив using</span><span class="sxs-lookup"><span data-stu-id="6abf9-127">To add necessary using directives</span></span>

1. <span data-ttu-id="6abf9-128">В **обозревателе решений** щелкните правой кнопкой мыши файл *Program.cs* и выберите пункт **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-128">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="6abf9-129">В начало файла кода добавьте следующие директивы `using`:</span><span class="sxs-lookup"><span data-stu-id="6abf9-129">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="6abf9-130">Создание списка банковских счетов</span><span class="sxs-lookup"><span data-stu-id="6abf9-130">To create a list of bank accounts</span></span>

1. <span data-ttu-id="6abf9-131">Вставьте следующее определение класса в файл **Program.cs** в класс `Program`.</span><span class="sxs-lookup"><span data-stu-id="6abf9-131">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. <span data-ttu-id="6abf9-132">Чтобы создать список `bankAccounts`, содержащий два счета, добавьте в метод `Main` следующий код.</span><span class="sxs-lookup"><span data-stu-id="6abf9-132">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="6abf9-133">Объявление метода, экспортирующего сведения о счетах в Excel</span><span class="sxs-lookup"><span data-stu-id="6abf9-133">To declare a method that exports account information to Excel</span></span>

1. <span data-ttu-id="6abf9-134">Чтобы настроить лист Excel, добавьте в класс `Program` следующий метод.</span><span class="sxs-lookup"><span data-stu-id="6abf9-134">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>

     <span data-ttu-id="6abf9-135">У метода <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> есть необязательный параметр для указания конкретного шаблона.</span><span class="sxs-lookup"><span data-stu-id="6abf9-135">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="6abf9-136">Для необязательных параметров, впервые появившихся в C# 4, можно опускать аргумент, если нужно использовать значение параметра по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6abf9-136">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="6abf9-137">Поскольку в следующем коде никакой аргумент не передается, в методе `Add` используется шаблон по умолчанию и создается новая книга.</span><span class="sxs-lookup"><span data-stu-id="6abf9-137">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="6abf9-138">В эквивалентном операторе в более ранних версиях C# необходимо было использовать аргумент-местозаполнитель `ExcelApp.Workbooks.Add(Type.Missing)`.</span><span class="sxs-lookup"><span data-stu-id="6abf9-138">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. <span data-ttu-id="6abf9-139">Добавьте в конец метода `DisplayInExcel` следующий код.</span><span class="sxs-lookup"><span data-stu-id="6abf9-139">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="6abf9-140">Этот код вставляет значения в первые два столбца первой строки листа.</span><span class="sxs-lookup"><span data-stu-id="6abf9-140">The code inserts values into the first two columns of the first row of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. <span data-ttu-id="6abf9-141">Добавьте в конец метода `DisplayInExcel` следующий код.</span><span class="sxs-lookup"><span data-stu-id="6abf9-141">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="6abf9-142">Цикл `foreach` помещает сведения из списка счетов в первые два столбца последовательных строк листа.</span><span class="sxs-lookup"><span data-stu-id="6abf9-142">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. <span data-ttu-id="6abf9-143">Добавьте в конец метода `DisplayInExcel` следующий код, чтобы ширина столбца изменялась в соответствии с содержимым.</span><span class="sxs-lookup"><span data-stu-id="6abf9-143">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     <span data-ttu-id="6abf9-144">В более ранних версиях C# требовалось явное приведение типов для этих операций, поскольку `ExcelApp.Columns[1]` возвращает тип `Object`, а метод `AutoFit` является методом Excel <xref:Microsoft.Office.Interop.Excel.Range>.</span><span class="sxs-lookup"><span data-stu-id="6abf9-144">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="6abf9-145">Приведение показано в следующих строках.</span><span class="sxs-lookup"><span data-stu-id="6abf9-145">The following lines show the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     <span data-ttu-id="6abf9-146">C# 4 и более поздних версий преобразует возвращаемое значение `Object` в `dynamic` автоматически, если ссылка на сборку задана с помощью параметра компилятора [**EmbedInteropTypes**](../../language-reference/compiler-options/inputs.md#embedinteroptypes) или, что эквивалентно, если свойство Excel **Внедрить типы взаимодействия** имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="6abf9-146">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [**EmbedInteropTypes**](../../language-reference/compiler-options/inputs.md#embedinteroptypes) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="6abf9-147">True является значением по умолчанию для этого свойства.</span><span class="sxs-lookup"><span data-stu-id="6abf9-147">True is the default value for this property.</span></span>

## <a name="to-run-the-project"></a><span data-ttu-id="6abf9-148">Запуск проекта</span><span class="sxs-lookup"><span data-stu-id="6abf9-148">To run the project</span></span>

1. <span data-ttu-id="6abf9-149">Добавьте в конец метода `Main` следующую строку.</span><span class="sxs-lookup"><span data-stu-id="6abf9-149">Add the following line at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. <span data-ttu-id="6abf9-150">Нажмите клавиши CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="6abf9-150">Press CTRL+F5.</span></span>

     <span data-ttu-id="6abf9-151">Появится книга Excel, содержащая данные о двух счетах.</span><span class="sxs-lookup"><span data-stu-id="6abf9-151">An Excel worksheet appears that contains the data from the two accounts.</span></span>

## <a name="to-add-a-word-document"></a><span data-ttu-id="6abf9-152">Добавление документа Word</span><span class="sxs-lookup"><span data-stu-id="6abf9-152">To add a Word document</span></span>

1. <span data-ttu-id="6abf9-153">Чтобы продемонстрировать дополнительные способы, совершенствующие программирование для Office в C# 4 и более поздних версиях, следующий код открывает приложение Word и создает значок со ссылкой на лист Excel.</span><span class="sxs-lookup"><span data-stu-id="6abf9-153">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>

     <span data-ttu-id="6abf9-154">Вставьте метод `CreateIconInWordDoc`, указанный далее в этом шаге, в класс `Program`.</span><span class="sxs-lookup"><span data-stu-id="6abf9-154">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="6abf9-155">`CreateIconInWordDoc` использует именованные и необязательные аргументы, чтобы упростить вызовы методов <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> и <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span><span class="sxs-lookup"><span data-stu-id="6abf9-155">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="6abf9-156">В этих вызовах используются две новые возможности, появившиеся в C# 4, которые упрощают вызовы к методам COM, имеющим ссылочные параметры.</span><span class="sxs-lookup"><span data-stu-id="6abf9-156">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="6abf9-157">Во-первых, аргументы можно передать в ссылочные параметры, как если бы они были параметрами значений.</span><span class="sxs-lookup"><span data-stu-id="6abf9-157">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="6abf9-158">Это значит, что значения можно передавать напрямую без создания переменной для каждого ссылочного параметра.</span><span class="sxs-lookup"><span data-stu-id="6abf9-158">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="6abf9-159">Компилятор создает временные переменные для хранения значений аргументов и уничтожает эти переменные после завершения вызываемого метода.</span><span class="sxs-lookup"><span data-stu-id="6abf9-159">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="6abf9-160">Во-вторых, ключевое слово `ref` в списке аргументов можно опустить.</span><span class="sxs-lookup"><span data-stu-id="6abf9-160">Second, you can omit the `ref` keyword in the argument list.</span></span>

     <span data-ttu-id="6abf9-161">У метода `Add` имеется четыре ссылочных параметра, все из которых являются необязательными.</span><span class="sxs-lookup"><span data-stu-id="6abf9-161">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="6abf9-162">В C# 4.0 или более поздних версиях вы можете опустить аргументы для любого или для всех параметров, если требуется использовать значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6abf9-162">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="6abf9-163">В C# 3.0 и более ранних версиях необходимо было указывать аргумент для каждого из параметров, и этот аргумент должен был быть переменной, поскольку параметры являются ссылочными.</span><span class="sxs-lookup"><span data-stu-id="6abf9-163">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>

     <span data-ttu-id="6abf9-164">Метод `PasteSpecial` вставляет содержимое буфера обмена.</span><span class="sxs-lookup"><span data-stu-id="6abf9-164">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="6abf9-165">У метода имеется семь ссылочных параметров, все из которых являются необязательными.</span><span class="sxs-lookup"><span data-stu-id="6abf9-165">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="6abf9-166">Следующий код задает аргументы для двух из них: `Link` для создания ссылки на исходное содержимое буфера и `DisplayAsIcon` для отображения ссылки в виде значка.</span><span class="sxs-lookup"><span data-stu-id="6abf9-166">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="6abf9-167">В C# 4.0 и более поздних версиях можно использовать именованные аргументы для этих двух параметров и опустить остальные аргументы.</span><span class="sxs-lookup"><span data-stu-id="6abf9-167">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="6abf9-168">Хотя эти параметры являются ссылочными, использовать ключевое слово `ref` или создавать переменные для передачи аргументов не требуется.</span><span class="sxs-lookup"><span data-stu-id="6abf9-168">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="6abf9-169">Значения можно передать напрямую.</span><span class="sxs-lookup"><span data-stu-id="6abf9-169">You can send the values directly.</span></span> <span data-ttu-id="6abf9-170">В C# 3.0 и более ранних версиях необходимо было передавать аргумент в виде переменной для каждого ссылочного параметра.</span><span class="sxs-lookup"><span data-stu-id="6abf9-170">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     <span data-ttu-id="6abf9-171">В C# 3.0 и более ранних версиях приходилось использовать следующий более сложный синтаксис.</span><span class="sxs-lookup"><span data-stu-id="6abf9-171">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. <span data-ttu-id="6abf9-172">Добавьте в конец метода `Main` следующую инструкцию.</span><span class="sxs-lookup"><span data-stu-id="6abf9-172">Add the following statement at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. <span data-ttu-id="6abf9-173">Добавьте в конец метода `DisplayInExcel` следующую инструкцию.</span><span class="sxs-lookup"><span data-stu-id="6abf9-173">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="6abf9-174">Метод `Copy` добавляет лист в буфер обмена.</span><span class="sxs-lookup"><span data-stu-id="6abf9-174">The `Copy` method adds the worksheet to the Clipboard.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. <span data-ttu-id="6abf9-175">Нажмите клавиши CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="6abf9-175">Press CTRL+F5.</span></span>

     <span data-ttu-id="6abf9-176">Появится документ Word, содержащий значок.</span><span class="sxs-lookup"><span data-stu-id="6abf9-176">A Word document appears that contains an icon.</span></span> <span data-ttu-id="6abf9-177">Дважды щелкните значок, чтобы отобразить лист на переднем плане.</span><span class="sxs-lookup"><span data-stu-id="6abf9-177">Double-click the icon to bring the worksheet to the foreground.</span></span>

## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="6abf9-178">Задание свойства "Внедрить типы взаимодействия"</span><span class="sxs-lookup"><span data-stu-id="6abf9-178">To set the Embed Interop Types property</span></span>

1. <span data-ttu-id="6abf9-179">При вызове типа COM, который не требует во время выполнения основной сборки взаимодействия (PIA), можно использовать дополнительные усовершенствования.</span><span class="sxs-lookup"><span data-stu-id="6abf9-179">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="6abf9-180">Избавление от зависимостей от PIA приводит к независимости версий и делает развертывание более простым.</span><span class="sxs-lookup"><span data-stu-id="6abf9-180">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="6abf9-181">Дополнительные сведения о преимуществах программирования без основных сборок взаимодействия см. в руководстве по [ внедрению типов из управляемых сборок](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="6abf9-181">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>

     <span data-ttu-id="6abf9-182">Кроме того, писать программы стало проще, поскольку типы, принимаемые и возвращаемые методами COM, можно представить с помощью типа `dynamic` вместо типа `Object`.</span><span class="sxs-lookup"><span data-stu-id="6abf9-182">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="6abf9-183">Переменные типа `dynamic` не вычисляются до времени выполнения, что позволяет обходиться без явного приведения.</span><span class="sxs-lookup"><span data-stu-id="6abf9-183">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="6abf9-184">Дополнительные сведения см. в разделе [Использование типа dynamic](../types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="6abf9-184">For more information, see [Using Type dynamic](../types/using-type-dynamic.md).</span></span>

     <span data-ttu-id="6abf9-185">В C# 4 внедрение сведений о типах вместо использования сборок PIA является поведением по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6abf9-185">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="6abf9-186">За счет этого несколько приведенных выше примеров становятся проще, поскольку явное приведение не требуется.</span><span class="sxs-lookup"><span data-stu-id="6abf9-186">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="6abf9-187">Например, объявление `worksheet` в методе `DisplayInExcel` записывается как `Excel._Worksheet workSheet = excelApp.ActiveSheet`, а не как `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span><span class="sxs-lookup"><span data-stu-id="6abf9-187">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="6abf9-188">Для вызовов `AutoFit` в рамках одного метода также требовалось бы явное приведение без поведения по умолчанию, поскольку `ExcelApp.Columns[1]` возвращает тип `Object`, а `AutoFit` является методом Excel.</span><span class="sxs-lookup"><span data-stu-id="6abf9-188">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="6abf9-189">Приведение показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6abf9-189">The following code shows the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. <span data-ttu-id="6abf9-190">Чтобы изменить поведение по умолчанию и использовать сборки PIA вместо внедрения сведений о типе, разверните узел **Ссылки** в **обозревателе решений** и выберите **Microsoft.Office.Interop.Excel** или **Microsoft.Office.Interop.Word**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-190">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>

3. <span data-ttu-id="6abf9-191">Если окно **Свойства** не отображается, нажмите клавишу **F4**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-191">If you cannot see the **Properties** window, press **F4**.</span></span>

4. <span data-ttu-id="6abf9-192">В списке свойств найдите свойство **Внедрить типы взаимодействия** и измените его значение на **False**.</span><span class="sxs-lookup"><span data-stu-id="6abf9-192">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="6abf9-193">Также можно выполнить компиляцию с помощью командной строки с использованием параметра компилятора [**References**](../../language-reference/compiler-options/inputs.md#references) вместо [**EmbedInteropTypes**](../../language-reference/compiler-options/inputs.md#embedinteroptypes).</span><span class="sxs-lookup"><span data-stu-id="6abf9-193">Equivalently, you can compile by using the [**References**](../../language-reference/compiler-options/inputs.md#references) compiler option instead of [**EmbedInteropTypes**](../../language-reference/compiler-options/inputs.md#embedinteroptypes) at a command prompt.</span></span>

## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="6abf9-194">Дополнительное форматирование таблицы</span><span class="sxs-lookup"><span data-stu-id="6abf9-194">To add additional formatting to the table</span></span>

1. <span data-ttu-id="6abf9-195">Замените два вызова `AutoFit` в методе `DisplayInExcel` следующей инструкцией.</span><span class="sxs-lookup"><span data-stu-id="6abf9-195">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <span data-ttu-id="6abf9-196">У метода <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> имеется семь параметров значений, и все они являются необязательными.</span><span class="sxs-lookup"><span data-stu-id="6abf9-196">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="6abf9-197">Именованные и необязательные аргументы позволяют задать аргументы для всех параметров, их части или ни для одного параметра.</span><span class="sxs-lookup"><span data-stu-id="6abf9-197">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="6abf9-198">В приведенной выше инструкции аргумент задается только для одного из параметров, `Format`.</span><span class="sxs-lookup"><span data-stu-id="6abf9-198">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="6abf9-199">Поскольку `Format` является первым параметром в списке, имя параметра указывать не требуется.</span><span class="sxs-lookup"><span data-stu-id="6abf9-199">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="6abf9-200">Однако инструкция может быть проще для понимания, если указать имя параметра, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="6abf9-200">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. <span data-ttu-id="6abf9-201">Нажмите сочетание клавиш CTRL + F5, чтобы увидеть результат.</span><span class="sxs-lookup"><span data-stu-id="6abf9-201">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="6abf9-202">Другие форматы представлены в перечислении <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat>.</span><span class="sxs-lookup"><span data-stu-id="6abf9-202">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>

3. <span data-ttu-id="6abf9-203">Сравните инструкцию в шаге 1 со следующим кодом, в котором показаны аргументы, необходимые в C# 3.0 или более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="6abf9-203">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a><span data-ttu-id="6abf9-204">Пример</span><span class="sxs-lookup"><span data-stu-id="6abf9-204">Example</span></span>

<span data-ttu-id="6abf9-205">Ниже приведен полный пример кода.</span><span class="sxs-lookup"><span data-stu-id="6abf9-205">The following code shows the complete example.</span></span>

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a><span data-ttu-id="6abf9-206">См. также</span><span class="sxs-lookup"><span data-stu-id="6abf9-206">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="6abf9-207">dynamic</span><span class="sxs-lookup"><span data-stu-id="6abf9-207">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="6abf9-208">Использование типа dynamic</span><span class="sxs-lookup"><span data-stu-id="6abf9-208">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="6abf9-209">Именованные и необязательные аргументы</span><span class="sxs-lookup"><span data-stu-id="6abf9-209">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="6abf9-210">Использование именованных и необязательных аргументов в программировании приложений Office</span><span class="sxs-lookup"><span data-stu-id="6abf9-210">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
