---
description: 'Подробнее о следующем: Практическое руководство. Создание каталога в Visual Basic'
title: Практическое руководство. Создание каталога
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 39a0f1b2f482b27b6f207f0ca8a498db198e9d59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797605"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="5fa31-103">Практическое руководство. Создание каталога в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fa31-103">How to: Create a Directory in Visual Basic</span></span>

<span data-ttu-id="5fa31-104">Для создания каталога используйте метод `CreateDirectory` объекта `My.Computer.FileSystem`.</span><span class="sxs-lookup"><span data-stu-id="5fa31-104">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="5fa31-105">Если каталог уже существует, исключение не возникает.</span><span class="sxs-lookup"><span data-stu-id="5fa31-105">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="5fa31-106">Создание каталога</span><span class="sxs-lookup"><span data-stu-id="5fa31-106">To create a directory</span></span>  
  
- <span data-ttu-id="5fa31-107">Используйте метод `CreateDirectory`, указав полный путь к папке, где следует создать каталог.</span><span class="sxs-lookup"><span data-stu-id="5fa31-107">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="5fa31-108">В этом примере создается каталог `NewDirectory` в `C:\Documents and Settings\All Users\Documents`.</span><span class="sxs-lookup"><span data-stu-id="5fa31-108">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5fa31-109">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="5fa31-109">Robust Programming</span></span>  

 <span data-ttu-id="5fa31-110">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="5fa31-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5fa31-111">Неверное имя каталога.</span><span class="sxs-lookup"><span data-stu-id="5fa31-111">The directory name is malformed.</span></span> <span data-ttu-id="5fa31-112">Например, оно содержит недопустимые символы или состоит из одних пробелов (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="5fa31-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="5fa31-113">Родительский каталог создаваемого каталога доступен только для чтения (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5fa31-113">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="5fa31-114">Именем каталога является `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="5fa31-114">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="5fa31-115">Слишком длинное имя каталога (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="5fa31-115">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="5fa31-116">Имя каталога состоит из двоеточия ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="5fa31-116">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="5fa31-117">У пользователя нет разрешения на создание каталога (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="5fa31-117">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="5fa31-118">У пользователя нет разрешений в ситуации частичного доверия (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="5fa31-118">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa31-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5fa31-119">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [<span data-ttu-id="5fa31-120">Создание, удаление и перемещение файлов и каталогов</span><span class="sxs-lookup"><span data-stu-id="5fa31-120">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)
