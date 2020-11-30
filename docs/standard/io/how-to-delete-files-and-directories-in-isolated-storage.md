---
title: Практическое руководство. Удаление файлов и каталогов из изолированного хранилища
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET], isolated storage
- files [.NET], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
ms.openlocfilehash: ea1d7a460a8867f069aa4b4d915e03d6948e23b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688514"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="5fba6-102">Практическое руководство. Удаление файлов и каталогов из изолированного хранилища</span><span class="sxs-lookup"><span data-stu-id="5fba6-102">How to: Delete Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="5fba6-103">Вы можете удалять файлы и папки из файла изолированного хранилища.</span><span class="sxs-lookup"><span data-stu-id="5fba6-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="5fba6-104">В хранилище имена файлов и каталогов зависят от используемой операционной системы, а путь к ним указывается относительно корня виртуальной файловой системы.</span><span class="sxs-lookup"><span data-stu-id="5fba6-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="5fba6-105">В операционных системах Windows регистр в именах файлов не учитывается.</span><span class="sxs-lookup"><span data-stu-id="5fba6-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="5fba6-106">Класс <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> предоставляет два метода для удаления каталогов и файлов: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> и <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="5fba6-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="5fba6-107">При попытке удалить несуществующий файл или каталог создается исключение <xref:System.IO.IsolatedStorage.IsolatedStorageException>.</span><span class="sxs-lookup"><span data-stu-id="5fba6-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="5fba6-108">Если в имени будет указан подстановочный знак, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> создает исключение <xref:System.IO.IsolatedStorage.IsolatedStorageException>, а <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> создает исключение <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="5fba6-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="5fba6-109">Метод <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> завершается ошибкой, если удаляемый каталог содержит файлы или подкаталоги.</span><span class="sxs-lookup"><span data-stu-id="5fba6-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="5fba6-110">Вы можете использовать методы <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> и <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>, чтобы получить существующие файлы и каталоги.</span><span class="sxs-lookup"><span data-stu-id="5fba6-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="5fba6-111">Дополнительные сведения о поиске в виртуальной файловой системе хранилища см. в статье [Практическое руководство. Поиск существующих файлов и каталоги в изолированном хранилище](how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="5fba6-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fba6-112">Пример</span><span class="sxs-lookup"><span data-stu-id="5fba6-112">Example</span></span>  

 <span data-ttu-id="5fba6-113">Следующий пример кода создает несколько каталогов и файлов, а затем удаляет их.</span><span class="sxs-lookup"><span data-stu-id="5fba6-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5fba6-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5fba6-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="5fba6-115">Изолированное хранилище</span><span class="sxs-lookup"><span data-stu-id="5fba6-115">Isolated Storage</span></span>](isolated-storage.md)
