---
description: 'Подробнее о следующем: Практическое руководство. Чтение текста из файлов с помощью StreamReader (Visual Basic)'
title: Практическое руководство. Чтение текста из файлов с помощью StreamReader
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 9a2eb08209a2a65f7be846c8cb5357978a48ed73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797423"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="3242c-103">Практическое руководство. Чтение текста из файлов с помощью StreamReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3242c-103">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>

<span data-ttu-id="3242c-104">Объект `My.Computer.FileSystem` предоставляет методы для открытия <xref:System.IO.TextReader> и <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="3242c-104">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="3242c-105">Методы `OpenTextFileWriter` и `OpenTextFileReader` являются дополнительными методами и отображаются в IntelliSense, только если выбрана вкладка **Все**.</span><span class="sxs-lookup"><span data-stu-id="3242c-105">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="3242c-106">Чтение строки из файла с помощью средства чтения текста</span><span class="sxs-lookup"><span data-stu-id="3242c-106">To read a line from a file with a text reader</span></span>  
  
- <span data-ttu-id="3242c-107">Используйте `OpenTextFileReader` метод, чтобы открыть <xref:System.IO.TextReader>, указав файл.</span><span class="sxs-lookup"><span data-stu-id="3242c-107">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="3242c-108">В этом примере открывается файл с именем `testfile.txt`, считывается строка из него и отображается в окне сообщения.</span><span class="sxs-lookup"><span data-stu-id="3242c-108">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3242c-109">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="3242c-109">Robust Programming</span></span>  

 <span data-ttu-id="3242c-110">Файл, который считывается, должен быть текстовым файлом.</span><span class="sxs-lookup"><span data-stu-id="3242c-110">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="3242c-111">По имени файла не всегда можно с уверенностью судить о его содержимом.</span><span class="sxs-lookup"><span data-stu-id="3242c-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="3242c-112">Например, файл с именем Form1.vb может вовсе не быть исходным файлом Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3242c-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="3242c-113">Следует проверять все входные данные перед использованием их в приложении.</span><span class="sxs-lookup"><span data-stu-id="3242c-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="3242c-114">Содержимое файла может отличаться от ожидаемого, поэтому может не удаться прочесть файл с помощью методов чтения.</span><span class="sxs-lookup"><span data-stu-id="3242c-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3242c-115">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3242c-115">.NET Framework Security</span></span>  

 <span data-ttu-id="3242c-116">Для чтения из файла сборке требуется уровень привилегий, предоставляемый классом <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="3242c-116">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="3242c-117">Если код выполняется в контексте частичного доверия, исключение может возникнуть из-за недостатка прав доступа.</span><span class="sxs-lookup"><span data-stu-id="3242c-117">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="3242c-118">Дополнительные сведения см. в разделе [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="3242c-118">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span> <span data-ttu-id="3242c-119">Пользователь также должен иметь доступ к файлу.</span><span class="sxs-lookup"><span data-stu-id="3242c-119">The user also needs access to the file.</span></span> <span data-ttu-id="3242c-120">Дополнительные сведения см. в разделе [Общие сведения о технологии ACL](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3242c-120">For more information, see [ACL Technology Overview](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3242c-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3242c-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [<span data-ttu-id="3242c-122">Компонент SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="3242c-122">SaveFileDialog Component</span></span>](/dotnet/desktop/winforms/controls/savefiledialog-component-windows-forms)
- [<span data-ttu-id="3242c-123">Чтение из файлов</span><span class="sxs-lookup"><span data-stu-id="3242c-123">Reading from Files</span></span>](reading-from-files.md)
