---
description: 'Подробнее о следующем: Практическое руководство. Анализ путей к файлам в Visual Basic'
title: Практическое руководство. Анализ путей к файлам
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: dff423679324974d64c613a292c253d99d668c7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797501"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="39c13-103">Практическое руководство. Анализ путей к файлам в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39c13-103">How to: Parse File Paths in Visual Basic</span></span>

<span data-ttu-id="39c13-104">Объект <xref:Microsoft.VisualBasic.FileIO.FileSystem> предоставляет ряд полезных методов при анализе путей к файлам.</span><span class="sxs-lookup"><span data-stu-id="39c13-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
- <span data-ttu-id="39c13-105">Метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> получает два пути и возвращает комбинированный путь в правильном формате.</span><span class="sxs-lookup"><span data-stu-id="39c13-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
- <span data-ttu-id="39c13-106">Метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> возвращает абсолютный путь к родительскому элементу указанного пути.</span><span class="sxs-lookup"><span data-stu-id="39c13-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
- <span data-ttu-id="39c13-107">Метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> возвращает объект <xref:System.IO.FileInfo> , к которому можно выполнить запрос, чтобы определить свойства файла, например имя и путь.</span><span class="sxs-lookup"><span data-stu-id="39c13-107">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="39c13-108">По расширению файла не всегда можно с уверенностью судить о его содержимом.</span><span class="sxs-lookup"><span data-stu-id="39c13-108">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="39c13-109">Например, файл с именем Form1.vb может вовсе не быть исходным файлом Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="39c13-109">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="39c13-110">Определение имени и пути для файла</span><span class="sxs-lookup"><span data-stu-id="39c13-110">To determine a file's name and path</span></span>  
  
- <span data-ttu-id="39c13-111">Используйте свойства <xref:System.IO.FileInfo.DirectoryName%2A> и <xref:System.IO.FileInfo.Name%2A> объекта <xref:System.IO.FileInfo> , чтобы определить для файла имя и путь.</span><span class="sxs-lookup"><span data-stu-id="39c13-111">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="39c13-112">В этом примере определяются и отображаются имя и путь.</span><span class="sxs-lookup"><span data-stu-id="39c13-112">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="39c13-113">Объединение имени и каталога файла для создания полного пути</span><span class="sxs-lookup"><span data-stu-id="39c13-113">To combine a file's name and directory to create the full path</span></span>  
  
- <span data-ttu-id="39c13-114">Используйте метод `CombinePath` , указав каталог и имя.</span><span class="sxs-lookup"><span data-stu-id="39c13-114">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="39c13-115">В этом примере объединяются строки `folderPath` и `fileName` , созданные в предыдущем примере, и отображается результат.</span><span class="sxs-lookup"><span data-stu-id="39c13-115">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="39c13-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="39c13-116">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="39c13-117">Практическое руководство. Получение коллекции содержащихся в каталоге файлов</span><span class="sxs-lookup"><span data-stu-id="39c13-117">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
