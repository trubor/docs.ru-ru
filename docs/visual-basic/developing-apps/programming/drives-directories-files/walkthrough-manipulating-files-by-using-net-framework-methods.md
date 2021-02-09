---
description: 'Подробнее о следующем: Пошаговое руководство. Управление файлами с помощью методов .NET Framework (Visual Basic)'
title: Управление файлами с помощью методов .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files [Visual Basic], writing to
- reading text files [Visual Basic]
- text, writing to files
- files [Visual Basic], searching
- StreamReader class, walkthroughs
- files [Visual Basic], accessing
- I/O [Visual Basic], writing text to files
- writing to files [Visual Basic], walkthroughs
- StreamWriter class, walkthroughs
- text files [Visual Basic], reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
ms.openlocfilehash: e59dca15660a981c487688234c864a818398af65
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775374"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="adca1-103">Пошаговое руководство. Управление файлами с помощью методов .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adca1-103">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>

<span data-ttu-id="adca1-104">В этом пошаговом руководстве демонстрируются открытие и чтение файла с помощью класса <xref:System.IO.StreamReader>, проверка доступа к файлу, поиск строки в файле, считанном с помощью экземпляра класса <xref:System.IO.StreamReader>, и запись в файл с помощью класса <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="adca1-104">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a><span data-ttu-id="adca1-105">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="adca1-105">Creating the Application</span></span>

<span data-ttu-id="adca1-106">Запустите Visual Studio и начните проект с создания формы, которую пользователь сможет использовать для записи в намеченный файл.</span><span class="sxs-lookup"><span data-stu-id="adca1-106">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="adca1-107">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="adca1-107">To create the project</span></span>

1. <span data-ttu-id="adca1-108">В меню **Файл** выберите пункт **Создать проект**.</span><span class="sxs-lookup"><span data-stu-id="adca1-108">On the **File** menu, select **New Project**.</span></span>

2. <span data-ttu-id="adca1-109">В области **Новый проект** щелкните **Приложения Windows**.</span><span class="sxs-lookup"><span data-stu-id="adca1-109">In the **New Project** pane, click **Windows Application**.</span></span>

3. <span data-ttu-id="adca1-110">В поле **Имя** введите `MyDiary`, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="adca1-110">In the **Name** box type `MyDiary` and click **OK**.</span></span>

     <span data-ttu-id="adca1-111">Visual Studio добавит проект в **обозреватель решений**, после чего откроется **конструктор Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="adca1-111">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>

4. <span data-ttu-id="adca1-112">Добавьте в форму элементы управления из следующей таблицы и установите для их свойств соответствующие значения.</span><span class="sxs-lookup"><span data-stu-id="adca1-112">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="adca1-113">**Объект**</span><span class="sxs-lookup"><span data-stu-id="adca1-113">**Object**</span></span>|<span data-ttu-id="adca1-114">**Свойства**</span><span class="sxs-lookup"><span data-stu-id="adca1-114">**Properties**</span></span>|<span data-ttu-id="adca1-115">**Значение**</span><span class="sxs-lookup"><span data-stu-id="adca1-115">**Value**</span></span>|
|---|---|---|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="adca1-116">**Имя**</span><span class="sxs-lookup"><span data-stu-id="adca1-116">**Name**</span></span><br /><br /> <span data-ttu-id="adca1-117">**Text**</span><span class="sxs-lookup"><span data-stu-id="adca1-117">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="adca1-118">**Сохранить запись**</span><span class="sxs-lookup"><span data-stu-id="adca1-118">**Submit Entry**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="adca1-119">**Имя**</span><span class="sxs-lookup"><span data-stu-id="adca1-119">**Name**</span></span><br /><br /> <span data-ttu-id="adca1-120">**Text**</span><span class="sxs-lookup"><span data-stu-id="adca1-120">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="adca1-121">**Очистить запись**</span><span class="sxs-lookup"><span data-stu-id="adca1-121">**Clear Entry**</span></span>|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="adca1-122">**Имя**</span><span class="sxs-lookup"><span data-stu-id="adca1-122">**Name**</span></span><br /><br /> <span data-ttu-id="adca1-123">**Text**</span><span class="sxs-lookup"><span data-stu-id="adca1-123">**Text**</span></span><br /><br /> <span data-ttu-id="adca1-124">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="adca1-124">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="adca1-125">**Введите произвольный текст.**</span><span class="sxs-lookup"><span data-stu-id="adca1-125">**Please enter something.**</span></span><br /><br /> `False`|

## <a name="writing-to-the-file"></a><span data-ttu-id="adca1-126">Запись в файл</span><span class="sxs-lookup"><span data-stu-id="adca1-126">Writing to the File</span></span>

<span data-ttu-id="adca1-127">Чтобы добавить возможность записи в файл с помощью приложения, воспользуйтесь классом <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="adca1-127">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="adca1-128">Класс <xref:System.IO.StreamWriter> предназначен для вывода символов в определенной кодировке, тогда как класс <xref:System.IO.Stream> предназначен для ввода и вывода двоичных данных.</span><span class="sxs-lookup"><span data-stu-id="adca1-128"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="adca1-129">Класс <xref:System.IO.StreamWriter> следует использовать для записи строк данных в стандартный текстовый файл.</span><span class="sxs-lookup"><span data-stu-id="adca1-129">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="adca1-130">Дополнительные сведения о классе <xref:System.IO.StreamWriter> см. в статье <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="adca1-130">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>

### <a name="to-add-writing-functionality"></a><span data-ttu-id="adca1-131">Добавление возможности записи</span><span class="sxs-lookup"><span data-stu-id="adca1-131">To add writing functionality</span></span>

1. <span data-ttu-id="adca1-132">В меню **Вид** выберите пункт **Код**, чтобы открыть редактор кода.</span><span class="sxs-lookup"><span data-stu-id="adca1-132">From the **View** menu, choose **Code** to open the Code Editor.</span></span>

2. <span data-ttu-id="adca1-133">Поскольку приложение ссылается на пространство имен <xref:System.IO>, следует добавить следующие операторы в самом начале кода перед объявлением класса для формы, которое начинается с `Public Class Form1`.</span><span class="sxs-lookup"><span data-stu-id="adca1-133">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     <span data-ttu-id="adca1-134">Перед записью в файл необходимо создать экземпляр класса <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="adca1-134">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>

3. <span data-ttu-id="adca1-135">В меню **Вид** выберите пункт **Конструктор** для возврата в окно **Конструктор Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="adca1-135">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="adca1-136">Дважды щелкните кнопку `Submit`, чтобы создать для нее обработчик событий <xref:System.Windows.Forms.Control.Click>, а затем добавьте в него следующий код.</span><span class="sxs-lookup"><span data-stu-id="adca1-136">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> <span data-ttu-id="adca1-137">Интегрированная среда разработки (IDE) Visual Studio откроет редактор кода, а курсор будет помещен внутрь обработчика события, в который и следует добавить код.</span><span class="sxs-lookup"><span data-stu-id="adca1-137">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>

1. <span data-ttu-id="adca1-138">Для записи в файл используйте метод <xref:System.IO.StreamWriter.Write%2A> класса <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="adca1-138">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="adca1-139">Добавьте следующий код сразу после `Dim fw As StreamWriter`.</span><span class="sxs-lookup"><span data-stu-id="adca1-139">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="adca1-140">Не стоит беспокоиться о том, что возникнет исключение, если файл не существует, так как в этом случае он будет создан автоматически.</span><span class="sxs-lookup"><span data-stu-id="adca1-140">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. <span data-ttu-id="adca1-141">Чтобы пользователь не смог отправить пустую запись, добавьте следующий код сразу после `Dim ReadString As String`.</span><span class="sxs-lookup"><span data-stu-id="adca1-141">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. <span data-ttu-id="adca1-142">Поскольку речь идет о дневнике, пользователь захочет добавить к каждой записи дату.</span><span class="sxs-lookup"><span data-stu-id="adca1-142">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="adca1-143">Вставьте следующий код после `fw = New StreamWriter("C:\MyDiary.txt", True)`, чтобы присвоить переменной `Today` значение текущей даты.</span><span class="sxs-lookup"><span data-stu-id="adca1-143">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. <span data-ttu-id="adca1-144">Наконец, добавьте код для очистки <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="adca1-144">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="adca1-145">Добавьте следующий код в обработчик события `Clear` для кнопки <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="adca1-145">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="adca1-146">Добавление средств отображения в дневник</span><span class="sxs-lookup"><span data-stu-id="adca1-146">Adding Display Features to the Diary</span></span>

<span data-ttu-id="adca1-147">В этом разделе вы добавите средство для отображения последней записи в элементе управления `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="adca1-147">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="adca1-148">Вы также можете добавить элемент <xref:System.Windows.Forms.ComboBox>, который отображает разные записи и позволяет пользователю выбрать запись для отображения в `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="adca1-148">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="adca1-149">Экземпляр класса <xref:System.IO.StreamReader> считывает информацию из `MyDiary.txt`.</span><span class="sxs-lookup"><span data-stu-id="adca1-149">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="adca1-150">Как и класс <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader> предназначен для использования с текстовыми файлами.</span><span class="sxs-lookup"><span data-stu-id="adca1-150">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>

<span data-ttu-id="adca1-151">Для реализации следующей части пошагового руководства необходимо добавить в форму элементы управления из следующей таблицы и присвоить соответствующие значения их свойствам.</span><span class="sxs-lookup"><span data-stu-id="adca1-151">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="adca1-152">Control</span><span class="sxs-lookup"><span data-stu-id="adca1-152">Control</span></span>|<span data-ttu-id="adca1-153">Свойства</span><span class="sxs-lookup"><span data-stu-id="adca1-153">Properties</span></span>|<span data-ttu-id="adca1-154">Значения</span><span class="sxs-lookup"><span data-stu-id="adca1-154">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="adca1-155">**имя**;</span><span class="sxs-lookup"><span data-stu-id="adca1-155">**Name**</span></span><br /><br /> <span data-ttu-id="adca1-156">**Visible**</span><span class="sxs-lookup"><span data-stu-id="adca1-156">**Visible**</span></span><br /><br /> <span data-ttu-id="adca1-157">**Size**</span><span class="sxs-lookup"><span data-stu-id="adca1-157">**Size**</span></span><br /><br /> <span data-ttu-id="adca1-158">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="adca1-158">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="adca1-159">**Имя**</span><span class="sxs-lookup"><span data-stu-id="adca1-159">**Name**</span></span><br /><br /> <span data-ttu-id="adca1-160">**Text**</span><span class="sxs-lookup"><span data-stu-id="adca1-160">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="adca1-161">**Дисплей**</span><span class="sxs-lookup"><span data-stu-id="adca1-161">**Display**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="adca1-162">**Имя**</span><span class="sxs-lookup"><span data-stu-id="adca1-162">**Name**</span></span><br /><br /> <span data-ttu-id="adca1-163">**Text**</span><span class="sxs-lookup"><span data-stu-id="adca1-163">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="adca1-164">**Получение записей**</span><span class="sxs-lookup"><span data-stu-id="adca1-164">**Get Entries**</span></span>|
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="adca1-165">**Имя**</span><span class="sxs-lookup"><span data-stu-id="adca1-165">**Name**</span></span><br /><br /> <span data-ttu-id="adca1-166">**Text**</span><span class="sxs-lookup"><span data-stu-id="adca1-166">**Text**</span></span><br /><br /> <span data-ttu-id="adca1-167">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="adca1-167">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="adca1-168">**Выбор записи**</span><span class="sxs-lookup"><span data-stu-id="adca1-168">**Select an Entry**</span></span><br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a><span data-ttu-id="adca1-169">Заполнение элемента управления ComboBox</span><span class="sxs-lookup"><span data-stu-id="adca1-169">To populate the combo box</span></span>

1. <span data-ttu-id="adca1-170">В элементе управления `PickEntries`<xref:System.Windows.Forms.ComboBox> отображается дата создания каждой из записей, чтобы пользователь мог выбрать запись за определенную дату.</span><span class="sxs-lookup"><span data-stu-id="adca1-170">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="adca1-171">Создайте обработчик события <xref:System.Windows.Forms.Control.Click> для кнопки `GetEntries` и добавьте в него следующий код.</span><span class="sxs-lookup"><span data-stu-id="adca1-171">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. <span data-ttu-id="adca1-172">Чтобы протестировать код, нажмите клавишу F5 для компиляции, а затем нажмите кнопку **Показать записи**.</span><span class="sxs-lookup"><span data-stu-id="adca1-172">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="adca1-173">Щелкните стрелку раскрывающегося списка в <xref:System.Windows.Forms.ComboBox>, чтобы отобразить даты записей.</span><span class="sxs-lookup"><span data-stu-id="adca1-173">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>

### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="adca1-174">Выбор и просмотр отдельных записей</span><span class="sxs-lookup"><span data-stu-id="adca1-174">To choose and display individual entries</span></span>

1. <span data-ttu-id="adca1-175">Создайте обработчик события <xref:System.Windows.Forms.Control.Click> для кнопки `Display` и добавьте в него следующий код.</span><span class="sxs-lookup"><span data-stu-id="adca1-175">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. <span data-ttu-id="adca1-176">Чтобы протестировать код, нажмите клавишу F5 для компиляции, а затем введите запись.</span><span class="sxs-lookup"><span data-stu-id="adca1-176">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="adca1-177">Щелкните **Показать записи**, выберите запись из списка <xref:System.Windows.Forms.ComboBox> и нажмите кнопку **Отображение**.</span><span class="sxs-lookup"><span data-stu-id="adca1-177">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="adca1-178">Содержимое выбранной записи появится в элементе `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="adca1-178">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="adca1-179">Предоставление пользователям возможности удалять и изменять записи</span><span class="sxs-lookup"><span data-stu-id="adca1-179">Enabling Users to Delete or Modify Entries</span></span>

<span data-ttu-id="adca1-180">В заключение можно включить в приложение дополнительные функции, позволяющие пользователям удалять и изменять записи с помощью кнопок `DeleteEntry` и `EditEntry`.</span><span class="sxs-lookup"><span data-stu-id="adca1-180">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="adca1-181">Обе кнопки неактивны, пока не выбрана ни одна запись.</span><span class="sxs-lookup"><span data-stu-id="adca1-181">Both buttons remain disabled unless an entry is displayed.</span></span>

<span data-ttu-id="adca1-182">Добавьте в форму элементы управления из следующей таблицы и установите для их свойств соответствующие значения.</span><span class="sxs-lookup"><span data-stu-id="adca1-182">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="adca1-183">Control</span><span class="sxs-lookup"><span data-stu-id="adca1-183">Control</span></span>|<span data-ttu-id="adca1-184">Свойства</span><span class="sxs-lookup"><span data-stu-id="adca1-184">Properties</span></span>|<span data-ttu-id="adca1-185">Значения</span><span class="sxs-lookup"><span data-stu-id="adca1-185">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="adca1-186">**имя**;</span><span class="sxs-lookup"><span data-stu-id="adca1-186">**Name**</span></span><br /><br /> <span data-ttu-id="adca1-187">**Text**</span><span class="sxs-lookup"><span data-stu-id="adca1-187">**Text**</span></span><br /><br /> <span data-ttu-id="adca1-188">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="adca1-188">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="adca1-189">**Удаление записи**</span><span class="sxs-lookup"><span data-stu-id="adca1-189">**Delete Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="adca1-190">**Имя**</span><span class="sxs-lookup"><span data-stu-id="adca1-190">**Name**</span></span><br /><br /> <span data-ttu-id="adca1-191">**Text**</span><span class="sxs-lookup"><span data-stu-id="adca1-191">**Text**</span></span><br /><br /> <span data-ttu-id="adca1-192">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="adca1-192">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="adca1-193">**Изменить запись**</span><span class="sxs-lookup"><span data-stu-id="adca1-193">**Edit Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="adca1-194">**Имя**</span><span class="sxs-lookup"><span data-stu-id="adca1-194">**Name**</span></span><br /><br /> <span data-ttu-id="adca1-195">**Text**</span><span class="sxs-lookup"><span data-stu-id="adca1-195">**Text**</span></span><br /><br /> <span data-ttu-id="adca1-196">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="adca1-196">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="adca1-197">**Отправка изменений**</span><span class="sxs-lookup"><span data-stu-id="adca1-197">**Submit Edit**</span></span><br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="adca1-198">Включение возможности удаления и изменения записей</span><span class="sxs-lookup"><span data-stu-id="adca1-198">To enable deletion and modification of entries</span></span>

1. <span data-ttu-id="adca1-199">Добавьте следующий код в обработчик события `Display` для кнопки <xref:System.Windows.Forms.Control.Click> после элемента `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="adca1-199">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <span data-ttu-id="adca1-200">Создайте обработчик события <xref:System.Windows.Forms.Control.Click> для кнопки `DeleteEntry` и добавьте в него следующий код.</span><span class="sxs-lookup"><span data-stu-id="adca1-200">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. <span data-ttu-id="adca1-201">Когда пользователь отображает запись, кнопка `EditEntry` становится доступной.</span><span class="sxs-lookup"><span data-stu-id="adca1-201">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="adca1-202">Добавьте следующий код в обработчик событий <xref:System.Windows.Forms.Control.Click> для кнопки `Display` после элемента `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="adca1-202">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <span data-ttu-id="adca1-203">Создайте обработчик события <xref:System.Windows.Forms.Control.Click> для кнопки `EditEntry` и добавьте в него следующий код.</span><span class="sxs-lookup"><span data-stu-id="adca1-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <span data-ttu-id="adca1-204">Создайте обработчик события <xref:System.Windows.Forms.Control.Click> для кнопки `SubmitEdit` и добавьте в него следующий код.</span><span class="sxs-lookup"><span data-stu-id="adca1-204">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

<span data-ttu-id="adca1-205">Чтобы протестировать код, нажмите клавишу F5 для компиляции приложения.</span><span class="sxs-lookup"><span data-stu-id="adca1-205">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="adca1-206">Щелкните **Показать записи**, выберите запись и нажмите кнопку **Посмотреть**.</span><span class="sxs-lookup"><span data-stu-id="adca1-206">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="adca1-207">Выбранная запись появится в элементе `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="adca1-207">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="adca1-208">Нажмите кнопку **Изменить запись**.</span><span class="sxs-lookup"><span data-stu-id="adca1-208">Click **Edit Entry**.</span></span> <span data-ttu-id="adca1-209">Выбранная запись появится в элементе `Entry`<xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="adca1-209">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="adca1-210">Измените запись в `Entry`<xref:System.Windows.Forms.TextBox> и щелкните действие **Сохранить изменения**.</span><span class="sxs-lookup"><span data-stu-id="adca1-210">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="adca1-211">Откройте `MyDiary.txt` файл, чтобы убедиться, что изменения внесены.</span><span class="sxs-lookup"><span data-stu-id="adca1-211">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="adca1-212">Теперь выберите запись и нажмите кнопку **Удалить запись**.</span><span class="sxs-lookup"><span data-stu-id="adca1-212">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="adca1-213">Когда <xref:System.Windows.Forms.MessageBox> запросит подтверждение, нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="adca1-213">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="adca1-214">Закройте приложение и откройте файл `MyDiary.txt` для подтверждения удаления.</span><span class="sxs-lookup"><span data-stu-id="adca1-214">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>

## <a name="see-also"></a><span data-ttu-id="adca1-215">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="adca1-215">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="adca1-216">Пошаговые руководства</span><span class="sxs-lookup"><span data-stu-id="adca1-216">Walkthroughs</span></span>](../../../walkthroughs.md)
