---
title: Практическое руководство. Поиск существующих файлов и каталоги в изолированном хранилище
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
ms.openlocfilehash: 43685a6ecb92510ad8d80c472a1c774d46cbb5f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734638"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="3e902-102">Практическое руководство. Поиск существующих файлов и каталоги в изолированном хранилище</span><span class="sxs-lookup"><span data-stu-id="3e902-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="3e902-103">Чтобы выполнить поиск по каталогу в изолированном хранилище, используйте метод <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3e902-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3e902-104">Этот метод принимает строку, которая представляет шаблон для поиска.</span><span class="sxs-lookup"><span data-stu-id="3e902-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="3e902-105">В шаблоне поиска вы можете использовать как одиночные (?), так и многосимвольные (\*) подстановочные знаки, но они должны находиться только в последней части имени.</span><span class="sxs-lookup"><span data-stu-id="3e902-105">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="3e902-106">Например, допустимой строкой для поиска является `directory1/*ect*`, но не `*ect*/directory2`.</span><span class="sxs-lookup"><span data-stu-id="3e902-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="3e902-107">Чтобы выполнить поиск файла, используйте метод <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3e902-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3e902-108">Ограничение на использование подстановочных знаков в строках для поиска, которое задано для <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>, применяется и к <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e902-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="3e902-109">Ни один из этих методов не является рекурсивным. Класс <xref:System.IO.IsolatedStorage.IsolatedStorageFile> не предоставляет никаких методов для перечисления всех каталогов или файлов в хранилище.</span><span class="sxs-lookup"><span data-stu-id="3e902-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="3e902-110">Но в примере кода ниже мы предлагаем вам несколько рекурсивных методов.</span><span class="sxs-lookup"><span data-stu-id="3e902-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e902-111">Пример</span><span class="sxs-lookup"><span data-stu-id="3e902-111">Example</span></span>  

 <span data-ttu-id="3e902-112">В примере кода ниже показано, как создавать файлы и каталоги в изолированном хранилище.</span><span class="sxs-lookup"><span data-stu-id="3e902-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="3e902-113">Сначала код получает данные о хранилище, изолированном по пользователю, домену и сборке, и помещает его в переменную `isoStore`.</span><span class="sxs-lookup"><span data-stu-id="3e902-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="3e902-114">С помощью метода <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> создаются несколько разных каталогов, а конструктор <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> создает в них файлы.</span><span class="sxs-lookup"><span data-stu-id="3e902-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="3e902-115">Затем код в цикле обрабатывает результаты выполнения метода `GetAllDirectories`.</span><span class="sxs-lookup"><span data-stu-id="3e902-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="3e902-116">Этот метод использует <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> для поиска всех имен каталогов в текущем каталоге.</span><span class="sxs-lookup"><span data-stu-id="3e902-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="3e902-117">Эти имена сохраняются в массиве, а затем `GetAllDirectories` вызывает сам себя и передает в качестве параметра каждый найденный каталог.</span><span class="sxs-lookup"><span data-stu-id="3e902-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="3e902-118">В конечном счете возвращается массив с именами всех каталогов.</span><span class="sxs-lookup"><span data-stu-id="3e902-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="3e902-119">Затем этот код вызывает метод `GetAllFiles`.</span><span class="sxs-lookup"><span data-stu-id="3e902-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="3e902-120">Он, в свою очередь, вызывает `GetAllDirectories` для поиска всех имен каталогов и ищет файлы в каждом из каталогов с помощью метода <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e902-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="3e902-121">Результат возвращается в виде массива для отображения.</span><span class="sxs-lookup"><span data-stu-id="3e902-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="3e902-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3e902-122">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="3e902-123">Изолированное хранилище</span><span class="sxs-lookup"><span data-stu-id="3e902-123">Isolated Storage</span></span>](isolated-storage.md)
