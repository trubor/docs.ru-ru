---
description: Построение из командной строки с помощью csc.exe
title: Построение из командной строки с помощью csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 9ffd164602862fce7f5e4f0982d3eda7cb403e60
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "89125934"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="d0028-103">Построение из командной строки с помощью csc.exe</span><span class="sxs-lookup"><span data-stu-id="d0028-103">Command-line build with csc.exe</span></span>

<span data-ttu-id="d0028-104">Чтобы вызвать компилятор C#, следует ввести имя соответствующего исполняемого файла (*csc.exe*) в командной строке.</span><span class="sxs-lookup"><span data-stu-id="d0028-104">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="d0028-105">Если используется окно **Командная строка разработчика для Visual Studio**, все необходимые переменные среды устанавливаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="d0028-105">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="d0028-106">Дополнительные сведения о получении доступа к этому инструменту см. в статье [Командная строка разработчика для Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d0028-106">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span>

<span data-ttu-id="d0028-107">Если используется стандартное окно командной строки, необходимо изменить путь к файлу *csc.exe*, прежде чем вызывать его из любого подкаталога на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d0028-107">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="d0028-108">Чтобы задать соответствующие переменные среды для поддержки построения из командной строки, необходимо запустить пакетный файл *VsDevCmd.bat*.</span><span class="sxs-lookup"><span data-stu-id="d0028-108">You also must run *VsDevCmd.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="d0028-109">Дополнительные сведения о файле *VsDevCmd.bat*, включая инструкции по его поиску и запуску, см. в разделе [Практическое руководство. Настройка переменных среды для командной строки Visual Studio](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="d0028-109">For more information about *VsDevCmd.bat*, including instructions for how to find and run it, see [How to set environment variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="d0028-110">Если на вашем компьютере установлен только пакет средств разработки программного обеспечения для Windows, компилятор C# можно использовать из **командной строки SDK**, которая открывается через пункт меню **Microsoft .NET Framework SDK**.</span><span class="sxs-lookup"><span data-stu-id="d0028-110">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="d0028-111">Для программного построения программ C# можно также использовать средство MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d0028-111">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="d0028-112">Дополнительные сведения см. в разделе [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="d0028-112">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="d0028-113">Обычно исполняемый файл *csc.exe* расположен в папке Microsoft.NET\Framework\\ *\<Version>* в каталоге *Windows*.</span><span class="sxs-lookup"><span data-stu-id="d0028-113">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="d0028-114">Расположение файла может зависеть от конкретной конфигурации компьютера.</span><span class="sxs-lookup"><span data-stu-id="d0028-114">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="d0028-115">Если на компьютере установлено несколько версий .NET Framework, будет несколько версий этого файла.</span><span class="sxs-lookup"><span data-stu-id="d0028-115">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="d0028-116">Дополнительные сведения о подобных вариантах установки см. в разделе [Практическое руководство. Определение установленных версий платформы .NET Framework](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="d0028-116">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
> <span data-ttu-id="d0028-117">При сборке проекта в интегрированной среде разработки Visual Studio можно открыть команду **csc** и связанные с ней параметры компилятора в окне **Вывод**.</span><span class="sxs-lookup"><span data-stu-id="d0028-117">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="d0028-118">Чтобы отобразить эту информацию, следуйте инструкциям в разделе [Практическое руководство. Просмотр, сохранение и настройка файлов журнала сборки](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) для изменения уровня детализации журнала на **Обычный** или **Подробный**.</span><span class="sxs-lookup"><span data-stu-id="d0028-118">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="d0028-119">После сборки проекта выполните поиск по слову **csc** в окне **Вывод**, чтобы найти информацию о запуске компилятора C#.</span><span class="sxs-lookup"><span data-stu-id="d0028-119">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="d0028-120">**Содержание раздела**</span><span class="sxs-lookup"><span data-stu-id="d0028-120">**In this topic**</span></span>

- [<span data-ttu-id="d0028-121">Правила синтаксиса командной строки компоновщика</span><span class="sxs-lookup"><span data-stu-id="d0028-121">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="d0028-122">Примеры командных строк</span><span class="sxs-lookup"><span data-stu-id="d0028-122">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="d0028-123">Различия между выходными данными компилятора C# и компилятора C++</span><span class="sxs-lookup"><span data-stu-id="d0028-123">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="d0028-124">Правила синтаксиса командной строки для компилятора C#</span><span class="sxs-lookup"><span data-stu-id="d0028-124">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="d0028-125">Компилятор C# использует следующие правила при обработке аргументов, вводимых в командной строке операционной системы.</span><span class="sxs-lookup"><span data-stu-id="d0028-125">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="d0028-126">Аргументы разделяются пробелами (пробел или табуляция).</span><span class="sxs-lookup"><span data-stu-id="d0028-126">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="d0028-127">Символ каретки (^) не воспринимается как escape-символ или разделитель.</span><span class="sxs-lookup"><span data-stu-id="d0028-127">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="d0028-128">Этот символ обрабатывается синтаксическим анализатором командной строки в операционной системе, прежде чем передается в массив `argv` программы.</span><span class="sxs-lookup"><span data-stu-id="d0028-128">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="d0028-129">Строка, заключенная в двойные прямые кавычки ("строка"), обрабатывается как один аргумент, независимо от пробельных символов, которые могут в ней присутствовать.</span><span class="sxs-lookup"><span data-stu-id="d0028-129">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="d0028-130">Строку в кавычках можно встроить в аргумент.</span><span class="sxs-lookup"><span data-stu-id="d0028-130">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="d0028-131">Символ двойной кавычки после обратной косой черты (\\") обрабатывается как символ двойной кавычки литерала (").</span><span class="sxs-lookup"><span data-stu-id="d0028-131">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="d0028-132">Символы обратной косой черты обрабатываются буквально, если только им не предшествует двойная кавычка.</span><span class="sxs-lookup"><span data-stu-id="d0028-132">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="d0028-133">Если после четного числа символов обратной косой черты стоит двойная кавычка, в массив `argv` помещается по одному символу обратной косой черты (\) для каждой пары символов обратной косой черты (\\), а двойная кавычка (") обрабатывается как разделитель строки.</span><span class="sxs-lookup"><span data-stu-id="d0028-133">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="d0028-134">Если после нечетного числа символов обратной косой черты стоит двойная кавычка, в массив `argv` помещается по одному символу обратной косой черты (\) для каждой пары символов обратной косой черты (\\), а двойная кавычка (") "изолируется" с помощью оставшихся косых черт.</span><span class="sxs-lookup"><span data-stu-id="d0028-134">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="d0028-135">В результате литеральный символ двойной кавычки (") добавляется в массив `argv`.</span><span class="sxs-lookup"><span data-stu-id="d0028-135">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="d0028-136">Примеры командных строк для компилятора C#</span><span class="sxs-lookup"><span data-stu-id="d0028-136">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="d0028-137">Компиляция *File.cs* и создание *File.exe*:</span><span class="sxs-lookup"><span data-stu-id="d0028-137">Compiles *File.cs* producing *File.exe*:</span></span>

  ```console
  csc File.cs
  ```

- <span data-ttu-id="d0028-138">Компиляция *File.cs* и создание *File.dll*:</span><span class="sxs-lookup"><span data-stu-id="d0028-138">Compiles *File.cs* producing *File.dll*:</span></span>

  ```console
  csc -target:library File.cs
  ```

- <span data-ttu-id="d0028-139">Компиляция *File.cs* и создание *My.exe*:</span><span class="sxs-lookup"><span data-stu-id="d0028-139">Compiles *File.cs* and creates *My.exe*:</span></span>

  ```console
  csc -out:My.exe File.cs
  ```

- <span data-ttu-id="d0028-140">Компиляция всех файлов C# в текущем каталоге с включенными оптимизациями и определение символа DEBUG.</span><span class="sxs-lookup"><span data-stu-id="d0028-140">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="d0028-141">Выводится файл *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="d0028-141">The output is *File2.exe*:</span></span>

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- <span data-ttu-id="d0028-142">Компиляция всех файлов C# в текущем каталоге с созданием отладочной версии *File2.dll*.</span><span class="sxs-lookup"><span data-stu-id="d0028-142">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="d0028-143">Логотипы и предупреждения не отображаются:</span><span class="sxs-lookup"><span data-stu-id="d0028-143">No logo and no warnings are displayed:</span></span>

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- <span data-ttu-id="d0028-144">Компиляция всех файлов C# в текущем каталоге в файл *Something.xyz* (библиотеку DLL):</span><span class="sxs-lookup"><span data-stu-id="d0028-144">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="d0028-145">Различия между выходными данными компилятора C# и компилятора C++</span><span class="sxs-lookup"><span data-stu-id="d0028-145">Differences between C# compiler and C++ compiler output</span></span>

<span data-ttu-id="d0028-146">В результате вызова компилятора C# файлы объектов (*OBJ*-файлы) не создаются; выходные файлы создаются непосредственно.</span><span class="sxs-lookup"><span data-stu-id="d0028-146">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="d0028-147">По этой причине компилятору C# не требуется компоновщик.</span><span class="sxs-lookup"><span data-stu-id="d0028-147">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0028-148">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d0028-148">See also</span></span>

- [<span data-ttu-id="d0028-149">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="d0028-149">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d0028-150">Параметры компилятора C# в алфавитном порядке</span><span class="sxs-lookup"><span data-stu-id="d0028-150">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="d0028-151">Параметры компилятора C#, упорядоченные по категориям</span><span class="sxs-lookup"><span data-stu-id="d0028-151">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="d0028-152">Main() и аргументы командной строки</span><span class="sxs-lookup"><span data-stu-id="d0028-152">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="d0028-153">Аргументы командной строки</span><span class="sxs-lookup"><span data-stu-id="d0028-153">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="d0028-154">Практическое руководство. Отображение аргументов командной строки</span><span class="sxs-lookup"><span data-stu-id="d0028-154">How to display command-line arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="d0028-155">Значения, возвращаемые методом main()</span><span class="sxs-lookup"><span data-stu-id="d0028-155">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
