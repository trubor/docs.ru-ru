---
description: 'Подробнее о следующем: Практическое руководство. Создание файла в Visual Basic'
title: Практическое руководство. Создание файла
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: b46786035c14021ceb27cce5b34eff5c8397fc9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797592"
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="ed756-103">Практическое руководство. Создание файла в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed756-103">How to: Create a File in Visual Basic</span></span>

<span data-ttu-id="ed756-104">В этом примере создается пустой текстовый файл по указанному пути с использованием метода <xref:System.IO.File.Create%2A> класса <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="ed756-104">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed756-105">Пример</span><span class="sxs-lookup"><span data-stu-id="ed756-105">Example</span></span>  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ed756-106">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="ed756-106">Compiling the Code</span></span>  

 <span data-ttu-id="ed756-107">Для записи в файл используется переменная `file`.</span><span class="sxs-lookup"><span data-stu-id="ed756-107">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ed756-108">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="ed756-108">Robust Programming</span></span>  

 <span data-ttu-id="ed756-109">Если файл уже существует, он заменяется.</span><span class="sxs-lookup"><span data-stu-id="ed756-109">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="ed756-110">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="ed756-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ed756-111">Недопустимое имя пути</span><span class="sxs-lookup"><span data-stu-id="ed756-111">The path name is malformed.</span></span> <span data-ttu-id="ed756-112">Например, оно содержит недопустимые символы или состоит из одних пробелов (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="ed756-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="ed756-113">Путь доступен только для чтения (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ed756-113">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="ed756-114">Имя пути — `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="ed756-114">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="ed756-115">Имя пути слишком длинное (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="ed756-115">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="ed756-116">Указан недопустимый путь (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="ed756-116">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="ed756-117">Путь состоит только из двоеточия (":") (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="ed756-117">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ed756-118">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ed756-118">.NET Framework Security</span></span>  

 <span data-ttu-id="ed756-119">Исключение <xref:System.Security.SecurityException> может быть создано в средах с частичным доверием.</span><span class="sxs-lookup"><span data-stu-id="ed756-119">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="ed756-120">Вызов метода <xref:System.IO.File.Create%2A> требует <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="ed756-120">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="ed756-121">Исключение <xref:System.UnauthorizedAccessException> возникает, если пользователь не имеет разрешения на создание файла.</span><span class="sxs-lookup"><span data-stu-id="ed756-121">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed756-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ed756-122">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [<span data-ttu-id="ed756-123">Использование библиотек из не вполне надежного кода</span><span class="sxs-lookup"><span data-stu-id="ed756-123">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [<span data-ttu-id="ed756-124">Основы управления доступом для кода</span><span class="sxs-lookup"><span data-stu-id="ed756-124">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
