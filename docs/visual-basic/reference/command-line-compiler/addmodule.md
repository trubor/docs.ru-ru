---
description: 'Дополнительные сведения: -addmodule'
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: ca08aa599003897e680240af21c4a0eb568e31d8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468295"
---
# <a name="-addmodule"></a><span data-ttu-id="45f4b-103">-addmodule</span><span class="sxs-lookup"><span data-stu-id="45f4b-103">-addmodule</span></span>

<span data-ttu-id="45f4b-104">Дает компилятору указание сделать всю информацию о типах из указанных файлов доступной компилируемому проекту.</span><span class="sxs-lookup"><span data-stu-id="45f4b-104">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45f4b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="45f4b-105">Syntax</span></span>  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="45f4b-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="45f4b-106">Arguments</span></span>  

 `fileList`  
 <span data-ttu-id="45f4b-107">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="45f4b-107">Required.</span></span> <span data-ttu-id="45f4b-108">Разделенный запятыми список файлов, содержащих метаданные, но не содержащих манифесты сборки.</span><span class="sxs-lookup"><span data-stu-id="45f4b-108">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="45f4b-109">Имена файлов, содержащие пробелы, должны быть заключены в кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="45f4b-109">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45f4b-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="45f4b-110">Remarks</span></span>  

 <span data-ttu-id="45f4b-111">Файлы, перечисленные в параметре `fileList`, должны быть созданы с использованием параметра `-target:module` или параметра, эквивалентного `-target:module`, в другом компиляторе.</span><span class="sxs-lookup"><span data-stu-id="45f4b-111">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="45f4b-112">Все модули, добавленные с помощью `-addmodule`, во время выполнения должны находиться в том же каталоге, что и выходной файл.</span><span class="sxs-lookup"><span data-stu-id="45f4b-112">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="45f4b-113">То есть во время компиляции можно указать модуль в любом каталоге, но во время выполнения он должен находиться в каталоге приложения.</span><span class="sxs-lookup"><span data-stu-id="45f4b-113">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="45f4b-114">В противном случае возникает ошибка <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="45f4b-114">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="45f4b-115">При указании (неявно или явно) любого параметра [-target (Visual Basic)](target.md), кроме `-target:module` с `-addmodule`, файлы, передаваемые в `-addmodule`, становятся частью сборки проекта.</span><span class="sxs-lookup"><span data-stu-id="45f4b-115">If you specify (implicitly or explicitly) any[-target (Visual Basic)](target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="45f4b-116">Сборка необходима для запуска выходного файла, который содержит один или несколько файлов, добавленных с помощью `-addmodule`.</span><span class="sxs-lookup"><span data-stu-id="45f4b-116">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="45f4b-117">Используйте параметр [-reference (Visual Basic)](reference.md) для импорта метаданных из файла, содержащего сборку.</span><span class="sxs-lookup"><span data-stu-id="45f4b-117">Use [-reference (Visual Basic)](reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45f4b-118">Параметр `-addmodule` недоступен в среде разработки Visual Studio. Его можно использовать только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="45f4b-118">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45f4b-119">Пример</span><span class="sxs-lookup"><span data-stu-id="45f4b-119">Example</span></span>  

 <span data-ttu-id="45f4b-120">Следующий код создает модуль.</span><span class="sxs-lookup"><span data-stu-id="45f4b-120">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="45f4b-121">Следующий код импортирует типы модуля.</span><span class="sxs-lookup"><span data-stu-id="45f4b-121">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="45f4b-122">При запуске `t1` он выводит `802`.</span><span class="sxs-lookup"><span data-stu-id="45f4b-122">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f4b-123">См. также</span><span class="sxs-lookup"><span data-stu-id="45f4b-123">See also</span></span>

- [<span data-ttu-id="45f4b-124">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="45f4b-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="45f4b-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45f4b-125">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="45f4b-126">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45f4b-126">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="45f4b-127">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="45f4b-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
