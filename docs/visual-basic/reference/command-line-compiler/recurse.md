---
description: 'Дополнительные сведения: -recurse'
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 2c0f1788c3811e24e2d51ff30e4cb2842aa0bd7a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475881"
---
# <a name="-recurse"></a><span data-ttu-id="3a0a0-103">-recurse</span><span class="sxs-lookup"><span data-stu-id="3a0a0-103">-recurse</span></span>

<span data-ttu-id="3a0a0-104">Компилирует файлы исходного кода во всех дочерних каталогах указанного каталога или каталога проекта.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-104">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a0a0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3a0a0-105">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="3a0a0-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="3a0a0-106">Arguments</span></span>  

 `dir`  
 <span data-ttu-id="3a0a0-107">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-107">Optional.</span></span> <span data-ttu-id="3a0a0-108">Каталог, с которого будет начинаться поиск.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-108">The directory in which you want the search to begin.</span></span> <span data-ttu-id="3a0a0-109">Если не указать, поиск начинается в каталоге проекта.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-109">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="3a0a0-110">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-110">Required.</span></span> <span data-ttu-id="3a0a0-111">Файлы для поиска.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-111">The file(s) to search for.</span></span> <span data-ttu-id="3a0a0-112">Поддерживаются подстановочные знаки.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-112">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a0a0-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="3a0a0-113">Remarks</span></span>  

 <span data-ttu-id="3a0a0-114">Чтобы скомпилировать все соответствующие файлы в каталоге проекта, не задавая `-recurse`, можно использовать подстановочные знаки в именах файлов.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-114">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="3a0a0-115">Если имя выходного файла не указано, компилятор выводит имя выходного файла для первого обработанного входного файла.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-115">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="3a0a0-116">Обычно это первый файл в списке файлов, скомпилированных при просмотре в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-116">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="3a0a0-117">По этой причине лучше определять выходной файл с помощью параметра `-out`.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-117">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a0a0-118">Параметр `-recurse` недоступен в среде разработки Visual Studio. Он доступен только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-118">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a0a0-119">Пример</span><span class="sxs-lookup"><span data-stu-id="3a0a0-119">Example</span></span>  

 <span data-ttu-id="3a0a0-120">Следующая команда компилирует все файлы Visual Basic в текущем каталоге.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-120">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="3a0a0-121">Следующая команда компилирует все файлы Visual Basic в каталоге `Test\ABC` и всех вложенных каталогах, а затем создает `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-121">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a0a0-122">См. также</span><span class="sxs-lookup"><span data-stu-id="3a0a0-122">See also</span></span>

- [<span data-ttu-id="3a0a0-123">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="3a0a0-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3a0a0-124">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a0a0-124">-out (Visual Basic)</span></span>](out.md)
- [<span data-ttu-id="3a0a0-125">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="3a0a0-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
