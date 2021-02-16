---
description: 'Подробнее о следующем: Практическое руководство. Вызов компилятора командной строки (Visual Basic)'
title: Практическое руководство. Вызов компилятора командной строки
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: aca8fe70e252ae9e7fb06f740ce5b7f3c8ca3d5d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470217"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="7937b-103">Практическое руководство. Вызов компилятора командной строки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7937b-103">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>

<span data-ttu-id="7937b-104">Вы можете вызвать компилятор командной строки, указав имя исполняемого файла в командной строке, которая также называется командной строкой MS-DOS.</span><span class="sxs-lookup"><span data-stu-id="7937b-104">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="7937b-105">При компиляции из командной строки Windows по умолчанию необходимо ввести полный путь к исполняемому файлу.</span><span class="sxs-lookup"><span data-stu-id="7937b-105">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="7937b-106">Чтобы переопределить это поведение по умолчанию, можно либо использовать командную строку разработчика для Visual Studio, либо изменить переменную среды PATH.</span><span class="sxs-lookup"><span data-stu-id="7937b-106">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="7937b-107">Оба варианта позволяют выполнять сборку из любого каталога при вводе имени компилятора.</span><span class="sxs-lookup"><span data-stu-id="7937b-107">Both allow you to compile from any directory by simply typing the compiler name.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="7937b-108">Вызов компилятора с помощью командной строки разработчика для Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7937b-108">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>

1. <span data-ttu-id="7937b-109">Откройте папку "Инструменты Visual Studio" в группе программы Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7937b-109">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>

2. <span data-ttu-id="7937b-110">Если на вашем компьютере установлена среда Visual Studio, вы можете использовать командную строку разработчика для Visual Studio, чтобы получить доступ к компилятору из любого каталога на компьютере.</span><span class="sxs-lookup"><span data-stu-id="7937b-110">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>

3. <span data-ttu-id="7937b-111">Запустите командную строку разработчика для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7937b-111">Invoke the Developer Command Prompt for Visual Studio.</span></span>

4. <span data-ttu-id="7937b-112">В командной строке введите `vbc.exe` *имя исходного файла* и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="7937b-112">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>

    <span data-ttu-id="7937b-113">Например, если вы сохранили исходный код в каталоге с именем `SourceFiles`, откройте командную строку и введите `cd SourceFiles`, чтобы перейти в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="7937b-113">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="7937b-114">Если каталог содержит исходный файл с именем `Source.vb`, его можно скомпилировать, выполнив команду `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="7937b-114">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="7937b-115">Установка переменной среды PATH компилятора для командной строки Windows</span><span class="sxs-lookup"><span data-stu-id="7937b-115">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>

1. <span data-ttu-id="7937b-116">С помощью функции "Поиск" Windows найдите файл Vbc.exe на локальном диске.</span><span class="sxs-lookup"><span data-stu-id="7937b-116">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>

    <span data-ttu-id="7937b-117">Точное имя каталога, в котором находится компилятор, зависит от расположения каталога Windows и версии установленной платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7937b-117">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="7937b-118">Если установлено несколько версий платформы .NET Framework, необходимо определить, какую версию следует использовать (как правило, это последняя версия).</span><span class="sxs-lookup"><span data-stu-id="7937b-118">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>

2. <span data-ttu-id="7937b-119">В меню **Пуск** щелкните правой кнопкой мыши **Мой компьютер**, а затем в контекстном меню выберите **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="7937b-119">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>

3. <span data-ttu-id="7937b-120">Перейдите на вкладку **Дополнительно**, затем выберите **Переменные среды**.</span><span class="sxs-lookup"><span data-stu-id="7937b-120">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>

4. <span data-ttu-id="7937b-121">В области **Системные переменные** выберите **Путь** из списка и щелкните **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="7937b-121">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>

5. <span data-ttu-id="7937b-122">В диалоговом окне **Изменение системной переменной** переместите курсор в конец строки в поле **Значение переменной** и введите точку с запятой (;) и полное имя каталога, полученное на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="7937b-122">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>

6. <span data-ttu-id="7937b-123">Нажмите кнопку **ОК** для подтверждения изменений и закрытия диалоговых окон.</span><span class="sxs-lookup"><span data-stu-id="7937b-123">Click **OK** to confirm your edits and close the dialog boxes.</span></span>

     <span data-ttu-id="7937b-124">После изменения переменной среды PATH можно запустить компилятор Visual Basic в командной строке Windows из любого каталога на компьютере.</span><span class="sxs-lookup"><span data-stu-id="7937b-124">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="7937b-125">Вызов компилятора с помощью командной строки Windows</span><span class="sxs-lookup"><span data-stu-id="7937b-125">To invoke the compiler using the Windows Command Prompt</span></span>

1. <span data-ttu-id="7937b-126">В меню **Пуск** выберите папку **Стандартные**, а затем откройте **командную строку Windows**.</span><span class="sxs-lookup"><span data-stu-id="7937b-126">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>

2. <span data-ttu-id="7937b-127">В командной строке введите `vbc.exe`*имя исходного файла* и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="7937b-127">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>

     <span data-ttu-id="7937b-128">Например, если вы сохранили исходный код в каталоге с именем `SourceFiles`, откройте командную строку и введите `cd SourceFiles`, чтобы перейти в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="7937b-128">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="7937b-129">Если каталог содержит исходный файл с именем `Source.vb`, его можно скомпилировать, выполнив команду `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="7937b-129">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="see-also"></a><span data-ttu-id="7937b-130">См. также</span><span class="sxs-lookup"><span data-stu-id="7937b-130">See also</span></span>

- [<span data-ttu-id="7937b-131">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="7937b-131">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="7937b-132">Условная компиляция</span><span class="sxs-lookup"><span data-stu-id="7937b-132">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
