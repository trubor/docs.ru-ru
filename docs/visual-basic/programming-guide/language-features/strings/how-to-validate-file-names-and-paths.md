---
description: Дополнительные сведения см. в статье Проверка имен файлов и путей в Visual Basic
title: Практическое руководство. Проверка имен файлов и путей
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: 02a48ea7cbf3291cb2fe1c64c4e636a273842546
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429744"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="d9882-103">Практическое руководство. Проверка имен файлов и путей в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9882-103">How to: Validate File Names and Paths in Visual Basic</span></span>

<span data-ttu-id="d9882-104">В этом примере возвращается `Boolean` значение, указывающее, представляет ли строка имя файла или путь.</span><span class="sxs-lookup"><span data-stu-id="d9882-104">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="d9882-105">Проверка проверяет, содержит ли имя символы, недопустимые в файловой системе.</span><span class="sxs-lookup"><span data-stu-id="d9882-105">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9882-106">Пример</span><span class="sxs-lookup"><span data-stu-id="d9882-106">Example</span></span>  

 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="d9882-107">В этом примере не проверяется, неправильно ли в имени размещены двоеточия или каталоги без имени, или значение, если длина имени превышает максимальную длину, определенную системой.</span><span class="sxs-lookup"><span data-stu-id="d9882-107">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="d9882-108">Он также не проверяет, имеет ли приложение разрешение на доступ к ресурсу файловой системы с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="d9882-108">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9882-109">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d9882-109">See also</span></span>

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="d9882-110">Проверка строк в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9882-110">Validating Strings in Visual Basic</span></span>](validating-strings.md)
