---
description: 'Узнайте подробнее о: Примеры командных строк компиляции (Visual Basic)'
title: Примеры командных строк компиляции
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: fbd35b7f12b3bee9690698a24dcb70d850081f95
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474009"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="ebd72-103">Примеры командных строк компиляции (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebd72-103">Sample compilation command lines (Visual Basic)</span></span>

<span data-ttu-id="ebd72-104">В качестве альтернативы компиляции Visual Basic программ из Visual Studio можно выполнить компиляцию из командной строки, чтобы создать исполняемые файлы (EXE) или файлы библиотеки динамической компоновки (DLL).</span><span class="sxs-lookup"><span data-stu-id="ebd72-104">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>

<span data-ttu-id="ebd72-105">Компилятор командной строки Visual Basic поддерживает полный набор параметров, управляющих входными и выходными файлами, сборками, а также параметрами отладки и препроцессора.</span><span class="sxs-lookup"><span data-stu-id="ebd72-105">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="ebd72-106">Каждый параметр доступен в двух взаимозаменяемых формах: `-option` и `/option`.</span><span class="sxs-lookup"><span data-stu-id="ebd72-106">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="ebd72-107">В этой документации приводится только форма `-option`.</span><span class="sxs-lookup"><span data-stu-id="ebd72-107">This documentation shows only the `-option` form.</span></span>

<span data-ttu-id="ebd72-108">В следующей таблице приведены некоторые примеры командных строк, которые можно изменять для использования в своих целях.</span><span class="sxs-lookup"><span data-stu-id="ebd72-108">The following table lists some sample command lines you can modify for your own use.</span></span>

|<span data-ttu-id="ebd72-109">Кому</span><span class="sxs-lookup"><span data-stu-id="ebd72-109">To</span></span>|<span data-ttu-id="ebd72-110">Использовать</span><span class="sxs-lookup"><span data-stu-id="ebd72-110">Use</span></span>|
|--------|---------|
|<span data-ttu-id="ebd72-111">Компиляция файла File.vb и создание файла File.exe</span><span class="sxs-lookup"><span data-stu-id="ebd72-111">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|<span data-ttu-id="ebd72-112">Компиляция файла File.vb и создание файла File.dll</span><span class="sxs-lookup"><span data-stu-id="ebd72-112">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|
|<span data-ttu-id="ebd72-113">Компиляция файла File.vb и создание файла My.exe</span><span class="sxs-lookup"><span data-stu-id="ebd72-113">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|
|<span data-ttu-id="ebd72-114">Компиляция файла File.vb и создание библиотеки и базовой сборки с именем File.dll</span><span class="sxs-lookup"><span data-stu-id="ebd72-114">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="ebd72-115">Компиляция всех файлов Visual Basic в текущем каталоге с включенными оптимизациями и заданным символом `DEBUG`, ведущая к созданию файла File2.exe</span><span class="sxs-lookup"><span data-stu-id="ebd72-115">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|<span data-ttu-id="ebd72-116">Компиляция всех файлов Visual Basic в текущем каталоге, ведущая к созданию отладочной версии библиотеки File2.dll без отображения логотипа или предупреждений</span><span class="sxs-lookup"><span data-stu-id="ebd72-116">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|<span data-ttu-id="ebd72-117">Компиляция всех файлов Visual Basic в текущем каталоге в файл Something.dll</span><span class="sxs-lookup"><span data-stu-id="ebd72-117">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> <span data-ttu-id="ebd72-118">При сборке проекта в интегрированной среде разработки Visual Studio можно вывести сведения о соответствующей команде **vbc** и ее параметрах компилятора в окне вывода.</span><span class="sxs-lookup"><span data-stu-id="ebd72-118">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="ebd72-119">Чтобы отобразить эти сведения, откройте [диалоговое окно "Параметры", последовательно выберите пункты "Проекты и решения", "Сборка и запуск"](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), а затем установите для параметра **Уровень детализации выходных данных сборки проекта MSBuild** значение **Обычный** или выберите более высокий уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="ebd72-119">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebd72-120">См. также</span><span class="sxs-lookup"><span data-stu-id="ebd72-120">See also</span></span>

- [<span data-ttu-id="ebd72-121">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="ebd72-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ebd72-122">Условная компиляция</span><span class="sxs-lookup"><span data-stu-id="ebd72-122">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
