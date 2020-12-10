---
title: Отладка консольного приложения .NET с помощью Visual Studio для Mac
description: Узнайте, как выполнить отладку консольного приложения .NET с помощью Visual Studio для Mac.
ms.date: 11/30/2020
ms.openlocfilehash: e35bbef5582b6eec00ee48669a0f5d028eb051fb
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599620"
---
# <a name="tutorial-debug-a-net-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="4e485-103">Учебник. Отладка консольного приложения .NET с помощью Visual Studio для Mac</span><span class="sxs-lookup"><span data-stu-id="4e485-103">Tutorial: Debug a .NET console application using Visual Studio for Mac</span></span>

<span data-ttu-id="4e485-104">В этом учебнике представлены средства отладки, доступные в Visual Studio для Mac.</span><span class="sxs-lookup"><span data-stu-id="4e485-104">This tutorial introduces the debugging tools available in Visual Studio for Mac.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4e485-105">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="4e485-105">Prerequisites</span></span>

- <span data-ttu-id="4e485-106">В этом руководстве используется консольное приложение, созданное по инструкциям из статьи [Создание консольного приложения .NET с помощью Visual Studio для Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="4e485-106">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="4e485-107">Использование конфигурации отладочной сборки</span><span class="sxs-lookup"><span data-stu-id="4e485-107">Use Debug build configuration</span></span>

<span data-ttu-id="4e485-108">В Visual Studio используются две встроенные конфигурации сборки — *Отладка* и *Выпуск*.</span><span class="sxs-lookup"><span data-stu-id="4e485-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="4e485-109">Вы воспользуетесь отладочной конфигурацией сборки для отладки и конфигурацией для выпуска для окончательного выпуска программы.</span><span class="sxs-lookup"><span data-stu-id="4e485-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="4e485-110">В отладочной конфигурации программы компилируется с полной символической отладочной информацией и без оптимизации.</span><span class="sxs-lookup"><span data-stu-id="4e485-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="4e485-111">Оптимизация усложняет отладку, поскольку усложняется связь между исходным кодом и сгенерированными инструкциями.</span><span class="sxs-lookup"><span data-stu-id="4e485-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="4e485-112">Конфигурация для выпуска полностью оптимизирована и не содержит символической отладочной информации.</span><span class="sxs-lookup"><span data-stu-id="4e485-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="4e485-113">По умолчанию Visual Studio для Mac использует отладочную конфигурацию сборки, поэтому ее не нужно изменять перед отладкой.</span><span class="sxs-lookup"><span data-stu-id="4e485-113">By default, Visual Studio for Mac uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="4e485-114">Запустите Visual Studio для Mac.</span><span class="sxs-lookup"><span data-stu-id="4e485-114">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="4e485-115">Откройте проект, созданный по инструкциям из статьи [Создание консольного приложения .NET с помощью Visual Studio для Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="4e485-115">Open the project that you created in [Create a .NET console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

   <span data-ttu-id="4e485-116">Используемая конфигурация сборки отображается на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="4e485-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="4e485-117">На следующем изображении панели инструментов показано, что служба Visual Studio настроена для компиляции отладочной версии приложения:</span><span class="sxs-lookup"><span data-stu-id="4e485-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="Панель инструментов Visual Studio с выделенным режимом отладки":::

## <a name="set-a-breakpoint"></a><span data-ttu-id="4e485-119">Установка точки останова</span><span class="sxs-lookup"><span data-stu-id="4e485-119">Set a breakpoint</span></span>

<span data-ttu-id="4e485-120">*Точка останова* приостанавливает выполнение приложения на инструкции, предшествующей той строке, в которой установлена точка останова.</span><span class="sxs-lookup"><span data-stu-id="4e485-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="4e485-121">Установите точку останова в строке, где отображается имя, дата и время.</span><span class="sxs-lookup"><span data-stu-id="4e485-121">Set a breakpoint on the line that displays the name, date, and time.</span></span> <span data-ttu-id="4e485-122">Для этого поместите курсор в строку кода и нажмите клавиши <kbd>⌘</kbd><kbd>\\</kbd> (<kbd>Command</kbd>+<kbd>\\</kbd>).</span><span class="sxs-lookup"><span data-stu-id="4e485-122">To do that, place the cursor in the line of code and press <kbd>⌘</kbd><kbd>\\</kbd> (<kbd>command</kbd>+<kbd>\\</kbd>).</span></span> <span data-ttu-id="4e485-123">Другой способ добавить точку останова — выбрать в меню **Выполнить** > **Перейти к следующей точке останова**.</span><span class="sxs-lookup"><span data-stu-id="4e485-123">Another way to set a breakpoint is by selecting **Run** > **Toggle Breakpoint** from the menu.</span></span>

   <span data-ttu-id="4e485-124">Подсветка текста и красная точка в левом поле обозначает строку с точкой останова Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4e485-124">Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="Окно приложения Visual Studio с установленной точкой останова":::

1. <span data-ttu-id="4e485-126">Чтобы запустить программу в режиме отладки, нажмите клавиши <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd>+<kbd>ВВОД</kbd>).</span><span class="sxs-lookup"><span data-stu-id="4e485-126">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start the program in debugging mode.</span></span> <span data-ttu-id="4e485-127">Еще один способ запуска отладки — выбрать в меню параметры **Запуск** > **Начать отладку**.</span><span class="sxs-lookup"><span data-stu-id="4e485-127">Another way to start debugging is by choosing **Run** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="4e485-128">Когда программа запросит имя, введите любую строку в окне терминала и нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4e485-128">Enter a string in the terminal window when the program prompts for a name, and then press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="4e485-129">Выполнение программы остановится, когда будет достигнута точка останова, то есть перед выполнением метода `Console.WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="4e485-129">Program execution stops when it reaches the breakpoint, before the `Console.WriteLine` method executes.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Снимок экрана с точкой останова в Visual Studio":::

## <a name="use-the-immediate-window"></a><span data-ttu-id="4e485-131">Использование окна "Интерпретация"</span><span class="sxs-lookup"><span data-stu-id="4e485-131">Use the Immediate window</span></span>

<span data-ttu-id="4e485-132">Окно **Интерпретация** позволяет взаимодействовать с приложением, которое вы отлаживаете.</span><span class="sxs-lookup"><span data-stu-id="4e485-132">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="4e485-133">Вы можете интерактивно изменить значения переменных и посмотреть, как это повлияет на работу программы.</span><span class="sxs-lookup"><span data-stu-id="4e485-133">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="4e485-134">Если окно **Интерпретация** не отображается, откройте его, выбрав **Вид** > **Панели отладки** > **Интерпретация**.</span><span class="sxs-lookup"><span data-stu-id="4e485-134">If the **Immediate** window is not visible, display it by choosing **View** > **Debug Pads** > **Immediate**.</span></span>

1. <span data-ttu-id="4e485-135">Введите `name = "Gracie"` в окне **Интерпретация** и нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4e485-135">Enter `name = "Gracie"` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="4e485-136">Введите `date = date.AddDays(1)` в окне **Интерпретация** и нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4e485-136">Enter `date = date.AddDays(1)` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

   <span data-ttu-id="4e485-137">В окне **Интерпретация** отображается новое значение переменной строки и свойства значения <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="4e485-137">The **Immediate** window displays the new value of the string variable and the properties of the <xref:System.DateTime> value.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Окно Интерпретация в Visual Studio":::

   <span data-ttu-id="4e485-139">В окне **Локальные** отображаются значения переменных, которые определены в текущем выполняемом методе.</span><span class="sxs-lookup"><span data-stu-id="4e485-139">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span> <span data-ttu-id="4e485-140">Значения переменных, которые вы только что изменили, обновляются в окне **Локальные**.</span><span class="sxs-lookup"><span data-stu-id="4e485-140">The values of the variables that you just changed are updated in the **Locals** window.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Окно Локальные в Visual Studio":::

1. <span data-ttu-id="4e485-142">Чтобы продолжить отладку, нажмите клавиши <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd>+<kbd>ВВОД</kbd>).</span><span class="sxs-lookup"><span data-stu-id="4e485-142">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

   <span data-ttu-id="4e485-143">Значения, отображаемые в терминале, соответствуют изменениям, произведенным в окне **Интерпретация**.</span><span class="sxs-lookup"><span data-stu-id="4e485-143">The values displayed in the terminal correspond to the changes you made in the **Immediate** window.</span></span>

   <span data-ttu-id="4e485-144">Если окно терминала не отображается, выберите **Terminal - HelloWorld** (Терминал — HelloWorld) в нижней панели навигации.</span><span class="sxs-lookup"><span data-stu-id="4e485-144">If you don't see the Terminal, select **Terminal - HelloWorld** in the bottom navigation bar.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="Terminal - Hello World (Терминал — Hello World) в нижней панели навигации":::

1. <span data-ttu-id="4e485-146">Нажмите любую клавишу для выхода из программы.</span><span class="sxs-lookup"><span data-stu-id="4e485-146">Press any key to exit the program.</span></span>

1. <span data-ttu-id="4e485-147">Закройте окно терминала.</span><span class="sxs-lookup"><span data-stu-id="4e485-147">Close the terminal window.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="4e485-148">Установка условной точки останова</span><span class="sxs-lookup"><span data-stu-id="4e485-148">Set a conditional breakpoint</span></span>

<span data-ttu-id="4e485-149">Программа отображает строку, которую вводит пользователь.</span><span class="sxs-lookup"><span data-stu-id="4e485-149">The program displays a string that the user enters.</span></span> <span data-ttu-id="4e485-150">Что произойдет, если пользователь ничего не введет?</span><span class="sxs-lookup"><span data-stu-id="4e485-150">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="4e485-151">Это можно проверить с помощью полезной функции отладки, которая называется *условной точкой останова*.</span><span class="sxs-lookup"><span data-stu-id="4e485-151">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="4e485-152">Удерживая нажатой клавишу <kbd>CTRL</kbd>, щелкните красную точку, представляющую точку останова.</span><span class="sxs-lookup"><span data-stu-id="4e485-152"><kbd>ctrl</kbd>-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="4e485-153">В контекстном меню выберите **Изменить точку останова**.</span><span class="sxs-lookup"><span data-stu-id="4e485-153">In the context menu, select **Edit Breakpoint**.</span></span>

1. <span data-ttu-id="4e485-154">В диалоговом окне **Изменить точку останова** введите код в поле, следующее за полем **И выполняется следующее условие** и выберите **Применить**.</span><span class="sxs-lookup"><span data-stu-id="4e485-154">In the **Edit Breakpoint** dialog, enter the following code in the field that follows **And the following condition is true**, and select **Apply**.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="Редактор параметров точки останова":::

   <span data-ttu-id="4e485-156">При каждом достижении точки останова отладчик вызывает метод `String.IsNullOrEmpty(name)` и останавливается на этой строке только в том случае, если вызов метода возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="4e485-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="4e485-157">Вместо условного выражения можно указать *количество обращений* (выполнение программы будет прервано, пока инструкция не будет выполнена указанное количество раз).</span><span class="sxs-lookup"><span data-stu-id="4e485-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span>

1. <span data-ttu-id="4e485-158">Чтобы начать отладку, нажмите клавиши <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd>+<kbd>ВВОД</kbd>).</span><span class="sxs-lookup"><span data-stu-id="4e485-158">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

1. <span data-ttu-id="4e485-159">Когда в окне терминала появится предложение ввести имя, нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4e485-159">In the terminal window, press <kbd>enter</kbd> when prompted to enter your name.</span></span>

   <span data-ttu-id="4e485-160">Так как указанное вами условие соблюдается (`name` имеет значение `null` или <xref:System.String.Empty?displayProperty=nameWithType>), выполнение программы будет остановлено при достижении точки останова.</span><span class="sxs-lookup"><span data-stu-id="4e485-160">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint.</span></span>

1. <span data-ttu-id="4e485-161">Выберите окно **Локальные**, в котором отображаются значения локальных переменных для текущего выполняемого метода.</span><span class="sxs-lookup"><span data-stu-id="4e485-161">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="4e485-162">В нашем примере этим методом является `Main`.</span><span class="sxs-lookup"><span data-stu-id="4e485-162">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="4e485-163">Обратите внимание, что переменная `name` имеет значение `""`, то есть <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e485-163">Observe that the value of the `name` variable is `""`, that is, <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="4e485-164">Можно также увидеть, что переменная содержит пустую строку, введя имя переменной `name` в окне **Интерпретация** и нажав клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4e485-164">You can also see that the value is an empty string by entering the `name` variable name in the **Immediate** window and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="Окно интерпретации, отображающее имя, которое является пустой строкой":::

1. <span data-ttu-id="4e485-166">Чтобы продолжить отладку, нажмите клавиши <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd>+<kbd>ВВОД</kbd>).</span><span class="sxs-lookup"><span data-stu-id="4e485-166">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

1. <span data-ttu-id="4e485-167">В окне терминала нажмите любую клавишу, чтобы выйти из программы.</span><span class="sxs-lookup"><span data-stu-id="4e485-167">In the terminal window, press any key to exit the program.</span></span>

1. <span data-ttu-id="4e485-168">Закройте окно терминала.</span><span class="sxs-lookup"><span data-stu-id="4e485-168">Close the terminal window.</span></span>

1. <span data-ttu-id="4e485-169">Очистите точку останова. Для этого щелкните красную точку в левом поле окна с кодом.</span><span class="sxs-lookup"><span data-stu-id="4e485-169">Clear the breakpoint by clicking on the red dot in the left margin of the code window.</span></span> <span data-ttu-id="4e485-170">Или выберите **Выполнить > Перейти к следующей точке останова** при выбранной строке кода.</span><span class="sxs-lookup"><span data-stu-id="4e485-170">Another way to clear a breakpoint is by choosing **Run > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="4e485-171">Пошаговое выполнение программы</span><span class="sxs-lookup"><span data-stu-id="4e485-171">Step through a program</span></span>

<span data-ttu-id="4e485-172">Visual Studio позволяет выполнять программу пошагово, отслеживая результат ее выполнения.</span><span class="sxs-lookup"><span data-stu-id="4e485-172">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="4e485-173">Для этого обычно задают точку останова и запускают программу в небольшой части ее кода.</span><span class="sxs-lookup"><span data-stu-id="4e485-173">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="4e485-174">Поскольку наша программа невелика, давайте выполним ее пошагово.</span><span class="sxs-lookup"><span data-stu-id="4e485-174">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="4e485-175">Установите точку останова на фигурной скобке, обозначающей начало метода `Main` (нажмите клавишу <kbd>Command</kbd>+<kbd>\\</kbd>).</span><span class="sxs-lookup"><span data-stu-id="4e485-175">Set a breakpoint on the curly brace that marks the start of the `Main` method (press <kbd>command</kbd>+<kbd>\\</kbd>).</span></span>

1. <span data-ttu-id="4e485-176">Чтобы начать отладку, нажмите клавиши <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd>+<kbd>ВВОД</kbd>).</span><span class="sxs-lookup"><span data-stu-id="4e485-176">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

   <span data-ttu-id="4e485-177">Visual Studio останавливается в строке с точкой останова.</span><span class="sxs-lookup"><span data-stu-id="4e485-177">Visual Studio stops on the line with the breakpoint.</span></span>

1. <span data-ttu-id="4e485-178">Нажмите клавиши <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>SHIFT</kbd>+<kbd>Command</kbd>+<kbd>I</kbd>) или выберите **Выполнить** > **Шаг с заходом**, чтобы перейти на следующую строку.</span><span class="sxs-lookup"><span data-stu-id="4e485-178">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>) or select **Run** > **Step Into** to advance one line.</span></span>

   <span data-ttu-id="4e485-179">Следующая выполняемая строка будет выделена, и рядом с ней появится стрелка.</span><span class="sxs-lookup"><span data-stu-id="4e485-179">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Метод выполнения по шагам в Visual Studio":::

   <span data-ttu-id="4e485-181">На этом этапе в окне **Локальные** показано, что массив `args` пуст, а `name` и `date` имеют значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4e485-181">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="4e485-182">Кроме того, в Visual Studio открылся пустой терминал.</span><span class="sxs-lookup"><span data-stu-id="4e485-182">In addition, Visual Studio has opened a blank terminal.</span></span>

1. <span data-ttu-id="4e485-183">Нажмите клавиши <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>SHIFT</kbd>+<kbd>Command</kbd>+<kbd>I</kbd>).</span><span class="sxs-lookup"><span data-stu-id="4e485-183">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="4e485-184">Visual Studio подсвечивает инструкцию, которая содержит присваивание значения переменной `name`.</span><span class="sxs-lookup"><span data-stu-id="4e485-184">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="4e485-185">В окне **Локальные** отображается, что `name` имеет значение `null`, а в терминале появилась строка "What is your name?" (Введите имя:).</span><span class="sxs-lookup"><span data-stu-id="4e485-185">The **Locals** window shows that `name` is `null`, and the terminal displays the string "What is your name?".</span></span>

1. <span data-ttu-id="4e485-186">Ответьте на этот запрос, введя строку в окно консоли и нажав клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4e485-186">Respond to the prompt by entering a string in the console window and pressing <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="4e485-187">Нажмите клавиши <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>SHIFT</kbd>+<kbd>Command</kbd>+<kbd>I</kbd>).</span><span class="sxs-lookup"><span data-stu-id="4e485-187">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="4e485-188">Visual Studio подсвечивает инструкцию, которая содержит присваивание значения переменной `date`.</span><span class="sxs-lookup"><span data-stu-id="4e485-188">Visual Studio highlights the statement that includes the `date` variable assignment.</span></span> <span data-ttu-id="4e485-189">В окне **Локальные** отображается значение, полученное в результате вызова метода <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e485-189">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4e485-190">В терминале также отображается строка, указанная в командной строке.</span><span class="sxs-lookup"><span data-stu-id="4e485-190">The terminal displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="4e485-191">Нажмите клавиши <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>SHIFT</kbd>+<kbd>Command</kbd>+<kbd>I</kbd>).</span><span class="sxs-lookup"><span data-stu-id="4e485-191">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="4e485-192">В окне **Локальные** отображается значение переменной `date`, которому было присвоено свойство <xref:System.DateTime.Now?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e485-192">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="4e485-193">Терминал остается без изменений.</span><span class="sxs-lookup"><span data-stu-id="4e485-193">The terminal is unchanged.</span></span>

1. <span data-ttu-id="4e485-194">Нажмите клавиши <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>SHIFT</kbd>+<kbd>Command</kbd>+<kbd>I</kbd>).</span><span class="sxs-lookup"><span data-stu-id="4e485-194">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="4e485-195">Visual Studio вызывает метод <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e485-195">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4e485-196">В терминале отображается форматированная строка.</span><span class="sxs-lookup"><span data-stu-id="4e485-196">The terminal displays the formatted string.</span></span>

1. <span data-ttu-id="4e485-197">Нажмите клавиши <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>SHIFT</kbd>+<kbd>Command</kbd>+<kbd>U</kbd>) или выберите **Выполнить** > **Шаг с выходом**.</span><span class="sxs-lookup"><span data-stu-id="4e485-197">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>U</kbd>) or select **Run** > **Step Out**.</span></span>

   <span data-ttu-id="4e485-198">В терминале отображается сообщение с предложением нажать любую клавишу для выхода.</span><span class="sxs-lookup"><span data-stu-id="4e485-198">The terminal displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="4e485-199">Нажмите любую клавишу для выхода из программы.</span><span class="sxs-lookup"><span data-stu-id="4e485-199">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="4e485-200">Использование конфигурации сборки для выпуска</span><span class="sxs-lookup"><span data-stu-id="4e485-200">Use Release build configuration</span></span>

<span data-ttu-id="4e485-201">После тестирования отладочной версии приложения следует скомпилировать и протестировать версию в режиме выпуска.</span><span class="sxs-lookup"><span data-stu-id="4e485-201">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="4e485-202">При сборке в режиме выпуска компилятор использует методы оптимизации, которые могут негативно повлиять на поведение приложения.</span><span class="sxs-lookup"><span data-stu-id="4e485-202">The Release version incorporates compiler optimizations that can negatively affect the behavior of an application.</span></span> <span data-ttu-id="4e485-203">Например, оптимизации компилятора для повышения производительности могут привести к состоянию конкуренции в многопоточных приложениях.</span><span class="sxs-lookup"><span data-stu-id="4e485-203">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="4e485-204">Чтобы создать и протестировать окончательную версию консольного приложения, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="4e485-204">To build and test the Release version of the console application, do the following steps:</span></span>

1. <span data-ttu-id="4e485-205">Измените конфигурацию сборки на панели инструментов, указав конфигурацию **Выпуск** вместо конфигурации **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="4e485-205">Change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="Панель инструментов Visual Studio по умолчанию с выделенным режимом отладки":::

1. <span data-ttu-id="4e485-207">Чтобы запустить без отладки, нажмите клавиши <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Option</kbd>+<kbd>Command</kbd>+<kbd>ВВОД</kbd>).</span><span class="sxs-lookup"><span data-stu-id="4e485-207">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run without debugging.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4e485-208">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="4e485-208">Next steps</span></span>

<span data-ttu-id="4e485-209">В этом руководстве вы использовали средства отладки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4e485-209">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="4e485-210">В следующем руководстве вы опубликуете развертываемую версию приложения.</span><span class="sxs-lookup"><span data-stu-id="4e485-210">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4e485-211">Публикация консольного приложения .NET с помощью Visual Studio для Mac</span><span class="sxs-lookup"><span data-stu-id="4e485-211">Publish a .NET console application using Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
