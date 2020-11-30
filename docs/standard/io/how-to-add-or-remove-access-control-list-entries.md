---
title: Практическое руководство. добавление или удаление записей списка управления доступом (только для .NET Framework)
ms.date: 01/14/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
ms.openlocfilehash: 53daa88b761f46dab26b1c12c73741e880512d8d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682696"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="987ae-102">Практическое руководство. добавление или удаление записей списка управления доступом (только для .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="987ae-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>

<span data-ttu-id="987ae-103">Для добавления или удаления записей списка управления доступом (ACL) из файла или каталога получите объект <xref:System.Security.AccessControl.FileSecurity> или <xref:System.Security.AccessControl.DirectorySecurity> из файла или каталога.</span><span class="sxs-lookup"><span data-stu-id="987ae-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="987ae-104">Измените объект, а затем примените его к файлу или каталогу.</span><span class="sxs-lookup"><span data-stu-id="987ae-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="987ae-105">Добавление или удаление элемента списка ACL из файла</span><span class="sxs-lookup"><span data-stu-id="987ae-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="987ae-106">Вызовите метод <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> для получения объекта <xref:System.Security.AccessControl.FileSecurity>, содержащего текущие элементы списка ACL файла.</span><span class="sxs-lookup"><span data-stu-id="987ae-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="987ae-107">Добавьте и удалите элементы списка ACL из объекта <xref:System.Security.AccessControl.FileSecurity>, возвращенного в шаге 1.</span><span class="sxs-lookup"><span data-stu-id="987ae-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="987ae-108">Чтобы применить изменения, передайте объект <xref:System.Security.AccessControl.FileSecurity> в метод <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="987ae-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="987ae-109">Добавление или удаление элемента списка ACL из каталога</span><span class="sxs-lookup"><span data-stu-id="987ae-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="987ae-110">Вызовите метод <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> для получения объекта <xref:System.Security.AccessControl.DirectorySecurity>, содержащего текущие элементы списка ACL каталога.</span><span class="sxs-lookup"><span data-stu-id="987ae-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="987ae-111">Добавьте и удалите элементы списка ACL из объекта <xref:System.Security.AccessControl.DirectorySecurity>, возвращенного в шаге 1.</span><span class="sxs-lookup"><span data-stu-id="987ae-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="987ae-112">Чтобы применить изменения, передайте объект <xref:System.Security.AccessControl.DirectorySecurity> в метод <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="987ae-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="987ae-113">Пример</span><span class="sxs-lookup"><span data-stu-id="987ae-113">Example</span></span>  

 <span data-ttu-id="987ae-114">Для выполнения этого примера необходимо указать допустимую учетную запись пользователя или группы.</span><span class="sxs-lookup"><span data-stu-id="987ae-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="987ae-115">В этом примере используется объект <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="987ae-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="987ae-116">Используйте ту же процедуру для классов <xref:System.IO.FileInfo>, <xref:System.IO.Directory> и <xref:System.IO.DirectoryInfo>.</span><span class="sxs-lookup"><span data-stu-id="987ae-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
