---
description: 'Узнайте подробнее о: Запись данных в буфер обмена и чтение их оттуда (Visual Basic)'
title: Запись данных в буфер обмена и чтение их оттуда
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 18cb66f6d8093757ce34ddb20659824787460920
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666346"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="7bf7c-103">Запись данных в буфер обмена и чтение их оттуда (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bf7c-103">Storing data to and reading from the Clipboard (Visual Basic)</span></span>

<span data-ttu-id="7bf7c-104">Буфер обмена можно использовать для хранения данных, таких как текст и изображения.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-104">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="7bf7c-105">Поскольку буфер обмена используется всеми активными процессами, с его помощью можно передавать данные из одного процесса в другой.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-105">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="7bf7c-106">Объект `My.Computer.Clipboard` позволяет легко обращаться к буферу обмена, считывать из него данные и выполнять в него запись.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-106">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="7bf7c-107">Чтение из буфера обмена</span><span class="sxs-lookup"><span data-stu-id="7bf7c-107">Reading from the Clipboard</span></span>  

 <span data-ttu-id="7bf7c-108">Используйте метод <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> для чтения текста из буфера обмена.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-108">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="7bf7c-109">Код в следующем примере считывает текст и отображает его в окне сообщения.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-109">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="7bf7c-110">Для правильной работы этого кода буфер обмена должен содержать какой-либо текст.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-110">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 <span data-ttu-id="7bf7c-111">Этот пример кода также доступен в качестве фрагмента кода IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="7bf7c-112">В средстве выбора фрагмента кода он расположен в разделе **Приложения Windows Forms > Буфер обмена**.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-112">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="7bf7c-113">Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="7bf7c-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="7bf7c-114">Используйте метод <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> для извлечения изображения из буфера обмена.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-114">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="7bf7c-115">Код в этом примере проверяет наличие изображения в буфере обмена, прежде чем извлекать его и назначать `PictureBox1`.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-115">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 <span data-ttu-id="7bf7c-116">Этот пример кода также доступен в качестве фрагмента кода IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="7bf7c-117">В средстве выбора фрагмента кода он расположен в разделе **Приложения Windows Forms > Буфер обмена**. Дополнительные сведения см. в разделе [Фрагменты кода](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="7bf7c-117">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="7bf7c-118">Элементы, добавленные в буфер обмена, сохраняются даже после того, как работа приложения завершается.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-118">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="7bf7c-119">Определение типа файла, хранящегося в буфере обмена</span><span class="sxs-lookup"><span data-stu-id="7bf7c-119">Determining the type of file stored in the Clipboard</span></span>  

 <span data-ttu-id="7bf7c-120">В буфере обмена могут храниться данные в различных форматах, включая тексты, звуковые файлы и изображения.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-120">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="7bf7c-121">Чтобы определить, файл какого типа содержится в буфере обмена, можно использовать такие методы как <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A> и <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-121">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="7bf7c-122">Если вы используете для проверки пользовательский формат файла, можно использовать метод <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A>.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-122">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="7bf7c-123">Функция `ContainsImage` позволяет определить, являются ли данные в буфере обмена изображением.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-123">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="7bf7c-124">Следующий код проверяет, являются ли данные изображением, и выдает соответствующий отчет.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-124">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="7bf7c-125">Очистка буфера обмена</span><span class="sxs-lookup"><span data-stu-id="7bf7c-125">Clearing the Clipboard</span></span>  

 <span data-ttu-id="7bf7c-126">Метод <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> очищает буфер обмена.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-126">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="7bf7c-127">Поскольку буфер обмена используют и другие процессы, очищение буфера может плохо на них повлиять.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-127">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="7bf7c-128">В следующем примере кода демонстрируется применение метода `Clear`.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-128">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="7bf7c-129">Запись в буфер обмена</span><span class="sxs-lookup"><span data-stu-id="7bf7c-129">Writing to the Clipboard</span></span>  

 <span data-ttu-id="7bf7c-130">Используйте метод <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> для записи текста в буфер обмена.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-130">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="7bf7c-131">Следующий код записывает в буфер обмена строку "This is a test string" (Это — тестовая строка).</span><span class="sxs-lookup"><span data-stu-id="7bf7c-131">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 <span data-ttu-id="7bf7c-132">Метод `SetText` может принимать параметр формата, который содержит тип <xref:System.Windows.Forms.TextDataFormat>.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-132">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="7bf7c-133">Следующий код записывает строку "This is a test string" (Это — тестовая строка) в буфер обмена в формате RTF.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-133">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 <span data-ttu-id="7bf7c-134">Используйте метод <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> для записи данных в буфер обмена.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-134">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="7bf7c-135">Код в этом примере записывает `DataObject` `dataChunk` в буфер обмена в пользовательском формате `specialFormat`.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-135">This example writes the `DataObject` `dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 <span data-ttu-id="7bf7c-136">Используйте метод <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> для записи звуковых данных в буфер обмена.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-136">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="7bf7c-137">Код в этом примере создает массив байтов `musicReader`, считывает в него файл `cool.wav` и записывает его в буфер обмена.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-137">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> <span data-ttu-id="7bf7c-138">Поскольку к буферу обмена могут обращаться другие пользователи, не храните в нем конфиденциальные данные, включая пароли.</span><span class="sxs-lookup"><span data-stu-id="7bf7c-138">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf7c-139">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7bf7c-139">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [<span data-ttu-id="7bf7c-140">Практическое руководство. Чтение данных объекта из XML-файла</span><span class="sxs-lookup"><span data-stu-id="7bf7c-140">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="7bf7c-141">Практическое руководство. Запись данных объекта в XML-файл</span><span class="sxs-lookup"><span data-stu-id="7bf7c-141">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
