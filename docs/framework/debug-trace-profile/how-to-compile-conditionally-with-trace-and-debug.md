---
title: Практическое руководство. Условная компиляция с использованием атрибутов Trace и Debug
description: Узнайте, как выполнять условную компиляцию с помощью условных атрибутов TRACE и DEBUG при компиляции приложения .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
ms.openlocfilehash: 90c989bcf21e24cf7ccf410c9a18a44cde81233e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478218"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="504d1-103">Практическое руководство. Условная компиляция с использованием атрибутов Trace и Debug</span><span class="sxs-lookup"><span data-stu-id="504d1-103">How to: Compile Conditionally with Trace and Debug</span></span>

<span data-ttu-id="504d1-104">При отладке приложения во время разработки выходные данные трассировки и отладки отображаются в окне «Вывод» Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="504d1-104">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="504d1-105">Однако чтобы включить возможности трассировки в развернутом приложении, необходимо скомпилировать инструментированные приложения с включенной директивой компилятора **TRACE**.</span><span class="sxs-lookup"><span data-stu-id="504d1-105">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="504d1-106">Это позволяет компилировать код трассировки в выпускаемой версии приложения.</span><span class="sxs-lookup"><span data-stu-id="504d1-106">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="504d1-107">Если не включить директиву **TRACE**, весь код трассировки игнорируется во время компиляции и не включается в исполняемый код, который будет развернут.</span><span class="sxs-lookup"><span data-stu-id="504d1-107">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="504d1-108">Методы трассировки и отладки имеют связанные условные атрибуты.</span><span class="sxs-lookup"><span data-stu-id="504d1-108">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="504d1-109">Например, если условный атрибут трассировки имеет значение **true**, все операторы трассировки включаются в сборку (компилированные файлы .exe или .dll); если условный атрибут **Trace** имеет значение **false**, операторы трассировки не включаются.</span><span class="sxs-lookup"><span data-stu-id="504d1-109">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="504d1-110">Для сборки можно включить условный атрибут **Trace** или **Debug**, оба эти атрибута одновременно или ни один из них.</span><span class="sxs-lookup"><span data-stu-id="504d1-110">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="504d1-111">Следовательно, существует четыре типа сборки: **Debug**, **Trace**, обе или ни одной.</span><span class="sxs-lookup"><span data-stu-id="504d1-111">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="504d1-112">Некоторые сборки выпуска для продуктивного развертывания могут не содержать ни одну из них, однако большинство сборок отладки содержат обе.</span><span class="sxs-lookup"><span data-stu-id="504d1-112">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="504d1-113">Можно задать параметры компилятора для вашего приложения несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="504d1-113">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="504d1-114">Страницы свойств</span><span class="sxs-lookup"><span data-stu-id="504d1-114">The property pages</span></span>  
  
- <span data-ttu-id="504d1-115">Командная строка</span><span class="sxs-lookup"><span data-stu-id="504d1-115">The command line</span></span>  
  
- <span data-ttu-id="504d1-116">Оператор **#CONST** (для Visual Basic) и **#define** (для C#)</span><span class="sxs-lookup"><span data-stu-id="504d1-116">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="504d1-117">Изменить параметры компиляции можно в диалоговом окне «Страницы свойств».</span><span class="sxs-lookup"><span data-stu-id="504d1-117">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="504d1-118">В **обозревателе решений** щелкните узел проекта правой кнопкой.</span><span class="sxs-lookup"><span data-stu-id="504d1-118">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="504d1-119">Выберите в контекстном меню команду **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="504d1-119">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="504d1-120">В Visual Basic щелкните вкладку **Компиляция** в левой области страницы свойств, затем щелкните **Дополнительные параметры компиляции**, чтобы отобразить диалоговое окно **Дополнительные параметры компилятора**.</span><span class="sxs-lookup"><span data-stu-id="504d1-120">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="504d1-121">Установите флажки для параметров компилятора, которые необходимо включить.</span><span class="sxs-lookup"><span data-stu-id="504d1-121">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="504d1-122">Снимите флажки для параметров, которые необходимо отключить.</span><span class="sxs-lookup"><span data-stu-id="504d1-122">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="504d1-123">В C# выберите **Построить** в левой области страницы свойств, а затем установите флажки для параметров компилятора, которые нужно включить.</span><span class="sxs-lookup"><span data-stu-id="504d1-123">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="504d1-124">Снимите флажки для параметров, которые необходимо отключить.</span><span class="sxs-lookup"><span data-stu-id="504d1-124">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="504d1-125">Компиляция инструментированного кода с помощью командной строки</span><span class="sxs-lookup"><span data-stu-id="504d1-125">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="504d1-126">Задайте условный параметр компилятора в командной строке.</span><span class="sxs-lookup"><span data-stu-id="504d1-126">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="504d1-127">Компилятор включит код трассировки или отладки в исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="504d1-127">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="504d1-128">Например, следующая инструкция компилятора, введенная в командной строке, включит код трассировки в компилируемый исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="504d1-128">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="504d1-129">Для Visual Basic: **vbc -r:System.dll-д:траце = true-д:дебуг = false MyApplication. vb**</span><span class="sxs-lookup"><span data-stu-id="504d1-129">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="504d1-130">Для C#: **csc -r:System.dll-д:траце-д:дебуг = FALSE MyApplication.CS**</span><span class="sxs-lookup"><span data-stu-id="504d1-130">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="504d1-131">Чтобы скомпилировать несколько файлов приложений, оставьте пробел между именами файлов, например **MyApplication1.vb MyApplication2.vb MyApplication3.vb** или **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="504d1-131">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="504d1-132">Директивы условной компиляции, используемые в приведенных выше примерах, имеют следующие значения.</span><span class="sxs-lookup"><span data-stu-id="504d1-132">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="504d1-133">Директива</span><span class="sxs-lookup"><span data-stu-id="504d1-133">Directive</span></span>|<span data-ttu-id="504d1-134">Значение</span><span class="sxs-lookup"><span data-stu-id="504d1-134">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="504d1-135">компилятор Visual Basic</span><span class="sxs-lookup"><span data-stu-id="504d1-135">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="504d1-136">Компилятор C#</span><span class="sxs-lookup"><span data-stu-id="504d1-136">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="504d1-137">Ссылка на внешнюю сборку (EXE или DLL)</span><span class="sxs-lookup"><span data-stu-id="504d1-137">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="504d1-138">Определяет символ условной компиляции</span><span class="sxs-lookup"><span data-stu-id="504d1-138">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="504d1-139">Необходимо ввести команды TRACE или DEBUG буквами верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="504d1-139">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="504d1-140">Для получения дополнительных сведений о командах условной компиляции введите `vbc /?` (для Visual Basic) или `csc /?` (для C#) в командной строке.</span><span class="sxs-lookup"><span data-stu-id="504d1-140">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="504d1-141">Дополнительные сведения см. в разделах [Построение из командной строки](../../csharp/language-reference/compiler-options/index.md) (C#) или [Вызов компилятора командной строки](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="504d1-141">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/index.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="504d1-142">Выполнение условной компиляции с помощью #CONST или #define</span><span class="sxs-lookup"><span data-stu-id="504d1-142">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="504d1-143">Введите соответствующую инструкцию для используемого языка программирования в верхней части файла исходного кода.</span><span class="sxs-lookup"><span data-stu-id="504d1-143">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="504d1-144">Язык</span><span class="sxs-lookup"><span data-stu-id="504d1-144">Language</span></span>|<span data-ttu-id="504d1-145">Инструкция</span><span class="sxs-lookup"><span data-stu-id="504d1-145">Statement</span></span>|<span data-ttu-id="504d1-146">Result</span><span class="sxs-lookup"><span data-stu-id="504d1-146">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="504d1-147">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="504d1-147">**Visual Basic**</span></span>|<span data-ttu-id="504d1-148">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="504d1-148">**#CONST TRACE = true**</span></span>|<span data-ttu-id="504d1-149">Включает трассировку</span><span class="sxs-lookup"><span data-stu-id="504d1-149">Enables tracing</span></span>|  
    ||<span data-ttu-id="504d1-150">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="504d1-150">**#CONST TRACE = false**</span></span>|<span data-ttu-id="504d1-151">Отключает трассировку</span><span class="sxs-lookup"><span data-stu-id="504d1-151">Disables tracing</span></span>|  
    ||<span data-ttu-id="504d1-152">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="504d1-152">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="504d1-153">Включает отладку</span><span class="sxs-lookup"><span data-stu-id="504d1-153">Enables debugging</span></span>|  
    ||<span data-ttu-id="504d1-154">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="504d1-154">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="504d1-155">Отключает отладку</span><span class="sxs-lookup"><span data-stu-id="504d1-155">Disables debugging</span></span>|  
    |<span data-ttu-id="504d1-156">**C#**</span><span class="sxs-lookup"><span data-stu-id="504d1-156">**C#**</span></span>|<span data-ttu-id="504d1-157">**#define TRACE**</span><span class="sxs-lookup"><span data-stu-id="504d1-157">**#define TRACE**</span></span>|<span data-ttu-id="504d1-158">Включает трассировку</span><span class="sxs-lookup"><span data-stu-id="504d1-158">Enables tracing</span></span>|  
    ||<span data-ttu-id="504d1-159">**#undef TRACE**</span><span class="sxs-lookup"><span data-stu-id="504d1-159">**#undef TRACE**</span></span>|<span data-ttu-id="504d1-160">Отключает трассировку</span><span class="sxs-lookup"><span data-stu-id="504d1-160">Disables tracing</span></span>|  
    ||<span data-ttu-id="504d1-161">**#define DEBUG**</span><span class="sxs-lookup"><span data-stu-id="504d1-161">**#define DEBUG**</span></span>|<span data-ttu-id="504d1-162">Включает отладку</span><span class="sxs-lookup"><span data-stu-id="504d1-162">Enables debugging</span></span>|  
    ||<span data-ttu-id="504d1-163">**#undef DEBUG**</span><span class="sxs-lookup"><span data-stu-id="504d1-163">**#undef DEBUG**</span></span>|<span data-ttu-id="504d1-164">Отключает отладку</span><span class="sxs-lookup"><span data-stu-id="504d1-164">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="504d1-165">Отключение трассировки или отладки</span><span class="sxs-lookup"><span data-stu-id="504d1-165">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="504d1-166">Удалите директиву компилятора из исходного кода.</span><span class="sxs-lookup"><span data-stu-id="504d1-166">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="504d1-167">\- или -</span><span class="sxs-lookup"><span data-stu-id="504d1-167">\- or -</span></span>  
  
<span data-ttu-id="504d1-168">Удалите комментарий к директиве компилятора.</span><span class="sxs-lookup"><span data-stu-id="504d1-168">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="504d1-169">Когда все готово для компиляции, можно выбрать команду **Построить** из меню **Сборка** или использовать метод командной строки (но без ввода **d:**), чтобы определить символы условной компиляции.</span><span class="sxs-lookup"><span data-stu-id="504d1-169">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="504d1-170">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="504d1-170">See also</span></span>

- [<span data-ttu-id="504d1-171">Трассировка и инструментирование приложений</span><span class="sxs-lookup"><span data-stu-id="504d1-171">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="504d1-172">Практическое руководство. Создание, инициализация и настройка переключателей трассировки</span><span class="sxs-lookup"><span data-stu-id="504d1-172">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="504d1-173">Переключатели трассировки</span><span class="sxs-lookup"><span data-stu-id="504d1-173">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="504d1-174">Прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="504d1-174">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="504d1-175">Практическое руководство. Добавление операторов трассировки в код приложения</span><span class="sxs-lookup"><span data-stu-id="504d1-175">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="504d1-176">Практическое руководство. Настройка переменных среды для командной строки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="504d1-176">How to set environment variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="504d1-177">Практическое руководство. Вызов компилятора командной строки</span><span class="sxs-lookup"><span data-stu-id="504d1-177">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
