---
description: 'Узнайте подробнее о: Построение из командной строки (Visual Basic)'
title: Построение из командной строки
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: 5f0f8dd61bd5b79987cc1e59dcf4bfd8071a925e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468269"
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="e7ef8-103">Построение из командной строки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7ef8-103">Building from the Command Line (Visual Basic)</span></span>

<span data-ttu-id="e7ef8-104">Проект Visual Basic состоит из одного или нескольких отдельных исходных файлов.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-104">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="e7ef8-105">В ходе процесса, который называется компиляцией, эти файлы объединяются в один пакет — единый исполняемый файл, который можно запускать как приложение.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-105">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>

<span data-ttu-id="e7ef8-106">Visual Basic предоставляет компилятор командной строки, который можно использовать вместо компиляции программ в интегрированной среде разработки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-106">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="e7ef8-107">Компилятор командной строки предназначен для ситуаций, в которых вам не требуется полный набор функций интегрированной среды разработки, — например, когда вы используете компьютеры с ограниченным объемом системной памяти или дискового пространства или пишете код для таких компьютеров.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-107">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>

<span data-ttu-id="e7ef8-108">Чтобы скомпилировать исходные файлы в интегрированной среде разработки Visual Studio, выберите команду **Выполнить сборку** в меню **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-108">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>

> [!TIP]
> <span data-ttu-id="e7ef8-109">При сборке файлов проекта в интегрированной среде разработки Visual Studio можно вывести сведения о соответствующей команде **vbc** и ее параметрах в окне вывода.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-109">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="e7ef8-110">Чтобы отобразить эти сведения, откройте [диалоговое окно "Параметры", последовательно выберите пункты "Проекты и решения", "Сборка и запуск"](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), а затем установите для параметра **Уровень детализации выходных данных сборки проекта MSBuild** значение **Обычный** или выберите более высокий уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-110">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="e7ef8-111">Дополнительные сведения см. в разделе [Практическое руководство. Просмотр, сохранение и настройка файлов журнала сборки](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span><span class="sxs-lookup"><span data-stu-id="e7ef8-111">For more information, see [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span></span>

<span data-ttu-id="e7ef8-112">Файлы проекта (с расширением VBPROJ) можно компилировать в командной строке с помощью MSBuild.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-112">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="e7ef8-113">Дополнительные сведения см. в [справочнике по командной строке](/visualstudio/msbuild/msbuild-command-line-reference) и [пошаговом руководстве в Visual Studio](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="e7ef8-113">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e7ef8-114">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="e7ef8-114">In This Section</span></span>

<span data-ttu-id="e7ef8-115">[Практическое руководство. Вызов компилятора командной строки](how-to-invoke-the-command-line-compiler.md) </span><span class="sxs-lookup"><span data-stu-id="e7ef8-115">[How to: Invoke the Command-Line Compiler](how-to-invoke-the-command-line-compiler.md) </span></span>\
<span data-ttu-id="e7ef8-116">Описание вызова компилятора командной строки в командной строке MS-DOS или из определенного подкаталога.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-116">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>

<span data-ttu-id="e7ef8-117">[Примеры командных строк компиляции](sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="e7ef8-117">[Sample Compilation Command Lines](sample-compilation-command-lines.md) </span></span>\
<span data-ttu-id="e7ef8-118">Список примеров командных строк, которые можно изменять для использования в своих целях.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-118">Provides a list of sample command lines that you can modify for your own use.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e7ef8-119">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="e7ef8-119">Related Sections</span></span>

<span data-ttu-id="e7ef8-120">[Компилятор Visual Basic с интерфейсом командной строки](index.md) </span><span class="sxs-lookup"><span data-stu-id="e7ef8-120">[Visual Basic Command-Line Compiler](index.md) </span></span>\
<span data-ttu-id="e7ef8-121">Списки параметров компилятора, упорядоченных в алфавитном порядке или по назначению.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-121">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>

<span data-ttu-id="e7ef8-122">[Условная компиляция](../../programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="e7ef8-122">[Conditional Compilation](../../programming-guide/program-structure/conditional-compilation.md) </span></span>\
<span data-ttu-id="e7ef8-123">Описание компиляции отдельных разделов кода.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-123">Describes how to compile particular sections of code.</span></span>

<span data-ttu-id="e7ef8-124">[Building and Cleaning Projects and Solutions in Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) \ (Построение и очистка проектов и решений в Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="e7ef8-124">[Building and Cleaning Projects and Solutions in Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) \</span></span>
<span data-ttu-id="e7ef8-125">Описание, как можно упорядочивать то, что будет включено в различные сборки, выбирать свойства проекта и проверять правильность порядка сборки проектов.</span><span class="sxs-lookup"><span data-stu-id="e7ef8-125">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
