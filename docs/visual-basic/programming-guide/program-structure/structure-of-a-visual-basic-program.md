---
description: Дополнительные сведения о структуре Visual Basicной программы
title: Структура программы Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: e5941b1cbdfdc460e3e860a5449e8ccae0673612
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468204"
---
# <a name="structure-of-a-visual-basic-program"></a><span data-ttu-id="3d976-103">Структура программы Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3d976-103">Structure of a Visual Basic Program</span></span>

<span data-ttu-id="3d976-104">Visual Basicная программа строится на основе стандартных блоков.</span><span class="sxs-lookup"><span data-stu-id="3d976-104">A Visual Basic program is built up from standard building blocks.</span></span> <span data-ttu-id="3d976-105">*Решение* состоит из одного или нескольких проектов.</span><span class="sxs-lookup"><span data-stu-id="3d976-105">A *solution* comprises one or more projects.</span></span> <span data-ttu-id="3d976-106">*Проект* , в свою очередь, может содержать одну или несколько сборок.</span><span class="sxs-lookup"><span data-stu-id="3d976-106">A *project* in turn can contain one or more assemblies.</span></span> <span data-ttu-id="3d976-107">Каждая *Сборка* компилируется из одного или нескольких исходных файлов.</span><span class="sxs-lookup"><span data-stu-id="3d976-107">Each *assembly* is compiled from one or more source files.</span></span> <span data-ttu-id="3d976-108">*Исходный файл* предоставляет определение и реализацию классов, структур, модулей и интерфейсов, которые в конечном итоге содержат весь код.</span><span class="sxs-lookup"><span data-stu-id="3d976-108">A *source file* provides the definition and implementation of classes, structures, modules, and interfaces, which ultimately contain all your code.</span></span>  
  
 <span data-ttu-id="3d976-109">Дополнительные сведения об этих стандартных блоках Visual Basic программы см. в разделе [решения и проекты](/visualstudio/ide/solutions-and-projects-in-visual-studio) и [сборки в .NET](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="3d976-109">For more information about these building blocks of a Visual Basic program, see [Solutions and Projects](/visualstudio/ide/solutions-and-projects-in-visual-studio) and [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
## <a name="file-level-programming-elements"></a><span data-ttu-id="3d976-110">File-Level программных элементов</span><span class="sxs-lookup"><span data-stu-id="3d976-110">File-Level Programming Elements</span></span>  

 <span data-ttu-id="3d976-111">При запуске проекта или файла и открытии редактора кода вы увидите, что какой-то код уже существует и в правильном порядке.</span><span class="sxs-lookup"><span data-stu-id="3d976-111">When you start a project or file and open the code editor, you see some code already in place and in the correct order.</span></span> <span data-ttu-id="3d976-112">Любой код, который вы пишете, должен соответствовать следующей последовательности:</span><span class="sxs-lookup"><span data-stu-id="3d976-112">Any code that you write should follow the following sequence:</span></span>  
  
1. <span data-ttu-id="3d976-113">`Option` инструкции</span><span class="sxs-lookup"><span data-stu-id="3d976-113">`Option` statements</span></span>  
  
2. <span data-ttu-id="3d976-114">`Imports` инструкции</span><span class="sxs-lookup"><span data-stu-id="3d976-114">`Imports` statements</span></span>  
  
3. <span data-ttu-id="3d976-115">`Namespace` операторы и элементы уровня пространства имен</span><span class="sxs-lookup"><span data-stu-id="3d976-115">`Namespace` statements and namespace-level elements</span></span>  
  
 <span data-ttu-id="3d976-116">При вводе инструкций в другом порядке могут возникнуть ошибки компиляции.</span><span class="sxs-lookup"><span data-stu-id="3d976-116">If you enter statements in a different order, compilation errors can result.</span></span>  
  
 <span data-ttu-id="3d976-117">Программа также может содержать инструкции условной компиляции.</span><span class="sxs-lookup"><span data-stu-id="3d976-117">A program can also contain conditional compilation statements.</span></span> <span data-ttu-id="3d976-118">Их можно отключать в исходном файле между инструкциями предыдущей последовательности.</span><span class="sxs-lookup"><span data-stu-id="3d976-118">You can intersperse these in the source file among the statements of the preceding sequence.</span></span>  
  
### <a name="option-statements"></a><span data-ttu-id="3d976-119">Операторы Option</span><span class="sxs-lookup"><span data-stu-id="3d976-119">Option Statements</span></span>  

 <span data-ttu-id="3d976-120">`Option` инструкции устанавливают правила заземления для последующего кода, помогая предотвратить синтаксические и логические ошибки.</span><span class="sxs-lookup"><span data-stu-id="3d976-120">`Option` statements establish ground rules for subsequent code, helping prevent syntax and logic errors.</span></span> <span data-ttu-id="3d976-121">[Оператор Option Explicit](../../language-reference/statements/option-explicit-statement.md) гарантирует, что все переменные объявляются и написаны правильно, что сокращает время отладки.</span><span class="sxs-lookup"><span data-stu-id="3d976-121">The [Option Explicit Statement](../../language-reference/statements/option-explicit-statement.md) ensures that all variables are declared and spelled correctly, which reduces debugging time.</span></span> <span data-ttu-id="3d976-122">[Оператор Option-Statement](../../language-reference/statements/option-strict-statement.md) позволяет снизить количество логических ошибок и потери данных, которые могут возникать при работе между переменными различных типов данных.</span><span class="sxs-lookup"><span data-stu-id="3d976-122">The [Option Strict Statement](../../language-reference/statements/option-strict-statement.md) helps to minimize logic errors and data loss that can occur when you work between variables of different data types.</span></span> <span data-ttu-id="3d976-123">[Оператор Option Compare](../../language-reference/statements/option-compare-statement.md) указывает, каким образом строки сравниваются друг с другом на основе их `Binary` `Text` значений или.</span><span class="sxs-lookup"><span data-stu-id="3d976-123">The [Option Compare Statement](../../language-reference/statements/option-compare-statement.md) specifies the way strings are compared to each other, based on either their `Binary` or `Text` values.</span></span>  
  
### <a name="imports-statements"></a><span data-ttu-id="3d976-124">Операторы Imports</span><span class="sxs-lookup"><span data-stu-id="3d976-124">Imports Statements</span></span>  

 <span data-ttu-id="3d976-125">Можно включить [оператор Imports (пространство имен .NET и тип)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) для импорта имен, определенных за пределами проекта.</span><span class="sxs-lookup"><span data-stu-id="3d976-125">You can include an [Imports Statement (.NET Namespace and Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) to import names defined outside your project.</span></span> <span data-ttu-id="3d976-126">`Imports`Оператор позволяет коду ссылаться на классы и другие типы, определенные в импортированном пространстве имен, без необходимости уточнять их.</span><span class="sxs-lookup"><span data-stu-id="3d976-126">An `Imports` statement allows your code to refer to classes and other types defined within the imported namespace, without having to qualify them.</span></span> <span data-ttu-id="3d976-127">Можно использовать столько `Imports` инструкций, сколько необходимо.</span><span class="sxs-lookup"><span data-stu-id="3d976-127">You can use as many `Imports` statements as appropriate.</span></span> <span data-ttu-id="3d976-128">Дополнительные сведения см. [в разделе ссылки и оператор Imports](references-and-the-imports-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d976-128">For more information, see [References and the Imports Statement](references-and-the-imports-statement.md).</span></span>  
  
### <a name="namespace-statements"></a><span data-ttu-id="3d976-129">Операторы пространства имен</span><span class="sxs-lookup"><span data-stu-id="3d976-129">Namespace Statements</span></span>  

 <span data-ttu-id="3d976-130">Пространства имен помогают организовывать и классифицировать программные элементы для простоты группирования и доступа.</span><span class="sxs-lookup"><span data-stu-id="3d976-130">Namespaces help you organize and classify your programming elements for ease of grouping and accessing.</span></span> <span data-ttu-id="3d976-131">[Оператор Namespace](../../language-reference/statements/namespace-statement.md) используется для классификации следующих операторов в определенном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="3d976-131">You use the [Namespace Statement](../../language-reference/statements/namespace-statement.md) to classify the following statements within a particular namespace.</span></span> <span data-ttu-id="3d976-132">Дополнительные сведения см. в разделе [Пространства имен в Visual Basic](namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="3d976-132">For more information, see [Namespaces in Visual Basic](namespaces.md).</span></span>  
  
### <a name="conditional-compilation-statements"></a><span data-ttu-id="3d976-133">Операторы условной компиляции</span><span class="sxs-lookup"><span data-stu-id="3d976-133">Conditional Compilation Statements</span></span>  

 <span data-ttu-id="3d976-134">Операторы условной компиляции могут находиться практически в любом месте исходного файла.</span><span class="sxs-lookup"><span data-stu-id="3d976-134">Conditional compilation statements can appear almost anywhere in your source file.</span></span> <span data-ttu-id="3d976-135">Они приводят к включению или исключению частей кода во время компиляции в зависимости от определенных условий.</span><span class="sxs-lookup"><span data-stu-id="3d976-135">They cause parts of your code to be included or excluded at compile time depending on certain conditions.</span></span> <span data-ttu-id="3d976-136">Их также можно использовать для отладки приложения, так как условный код выполняется только в режиме отладки.</span><span class="sxs-lookup"><span data-stu-id="3d976-136">You can also use them for debugging your application, because conditional code runs in debugging mode only.</span></span> <span data-ttu-id="3d976-137">Дополнительные сведения см. в разделе [условная компиляция](conditional-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="3d976-137">For more information, see [Conditional Compilation](conditional-compilation.md).</span></span>  
  
## <a name="namespace-level-programming-elements"></a><span data-ttu-id="3d976-138">Namespace-Level программных элементов</span><span class="sxs-lookup"><span data-stu-id="3d976-138">Namespace-Level Programming Elements</span></span>  

 <span data-ttu-id="3d976-139">Классы, структуры и модули содержат весь код в исходном файле.</span><span class="sxs-lookup"><span data-stu-id="3d976-139">Classes, structures, and modules contain all the code in your source file.</span></span> <span data-ttu-id="3d976-140">Они представляют собой элементы *уровня пространства имен* , которые могут использоваться в пространстве имен или на уровне исходного файла.</span><span class="sxs-lookup"><span data-stu-id="3d976-140">They are *namespace-level* elements, which can appear within a namespace or at the source file level.</span></span> <span data-ttu-id="3d976-141">Они содержат объявления всех других программных элементов.</span><span class="sxs-lookup"><span data-stu-id="3d976-141">They hold the declarations of all other programming elements.</span></span> <span data-ttu-id="3d976-142">Интерфейсы, которые определяют подписи элементов, но не предоставляют реализации, также отображаются на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="3d976-142">Interfaces, which define element signatures but provide no implementation, also appear at module level.</span></span> <span data-ttu-id="3d976-143">Дополнительные сведения об элементах уровня модуля см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="3d976-143">For more information on the module-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="3d976-144">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="3d976-144">Class Statement</span></span>](../../language-reference/statements/class-statement.md)  
  
- [<span data-ttu-id="3d976-145">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="3d976-145">Structure Statement</span></span>](../../language-reference/statements/structure-statement.md)  
  
- [<span data-ttu-id="3d976-146">Оператор Module</span><span class="sxs-lookup"><span data-stu-id="3d976-146">Module Statement</span></span>](../../language-reference/statements/module-statement.md)  
  
- [<span data-ttu-id="3d976-147">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="3d976-147">Interface Statement</span></span>](../../language-reference/statements/interface-statement.md)  
  
 <span data-ttu-id="3d976-148">Элементы данных на уровне пространства имен являются перечислениями и делегатами.</span><span class="sxs-lookup"><span data-stu-id="3d976-148">Data elements at namespace level are enumerations and delegates.</span></span>  
  
## <a name="module-level-programming-elements"></a><span data-ttu-id="3d976-149">Module-Level программных элементов</span><span class="sxs-lookup"><span data-stu-id="3d976-149">Module-Level Programming Elements</span></span>  

 <span data-ttu-id="3d976-150">Процедуры, операторы, свойства и события — это единственные элементы программирования, которые могут содержать исполняемый код (операторы, выполняющие действия во время выполнения).</span><span class="sxs-lookup"><span data-stu-id="3d976-150">Procedures, operators, properties, and events are the only programming elements that can hold executable code (statements that perform actions at run time).</span></span> <span data-ttu-id="3d976-151">Они являются элементами *уровня модуля* программы.</span><span class="sxs-lookup"><span data-stu-id="3d976-151">They are the *module-level* elements of your program.</span></span> <span data-ttu-id="3d976-152">Дополнительные сведения об элементах уровня процедуры см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="3d976-152">For more information on the procedure-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="3d976-153">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="3d976-153">Function Statement</span></span>](../../language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="3d976-154">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="3d976-154">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)  
  
- [<span data-ttu-id="3d976-155">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="3d976-155">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)  
  
- [<span data-ttu-id="3d976-156">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="3d976-156">Operator Statement</span></span>](../../language-reference/statements/operator-statement.md)  
  
- [<span data-ttu-id="3d976-157">Property Statement</span><span class="sxs-lookup"><span data-stu-id="3d976-157">Property Statement</span></span>](../../language-reference/statements/property-statement.md)  
  
- [<span data-ttu-id="3d976-158">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="3d976-158">Event Statement</span></span>](../../language-reference/statements/event-statement.md)  
  
 <span data-ttu-id="3d976-159">Элементы данных на уровне модуля — это переменные, константы, перечисления и делегаты.</span><span class="sxs-lookup"><span data-stu-id="3d976-159">Data elements at module level are variables, constants, enumerations, and delegates.</span></span>  
  
## <a name="procedure-level-programming-elements"></a><span data-ttu-id="3d976-160">Procedure-Level программных элементов</span><span class="sxs-lookup"><span data-stu-id="3d976-160">Procedure-Level Programming Elements</span></span>  

 <span data-ttu-id="3d976-161">Большая часть содержимого элементов *уровня процедуры* — это исполняемые операторы, которые составляют код времени выполнения программы.</span><span class="sxs-lookup"><span data-stu-id="3d976-161">Most of the contents of *procedure-level* elements are executable statements, which constitute the run-time code of your program.</span></span> <span data-ttu-id="3d976-162">Весь исполняемый код должен быть в некоторой процедуре ( `Function` ,,,,,, `Sub` `Operator` `Get` `Set` `AddHandler` `RemoveHandler` , `RaiseEvent` ).</span><span class="sxs-lookup"><span data-stu-id="3d976-162">All executable code must be in some procedure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span></span> <span data-ttu-id="3d976-163">Дополнительные сведения см. в разделе [Инструкции](../language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="3d976-163">For more information, see [Statements](../language-features/statements.md).</span></span>  
  
 <span data-ttu-id="3d976-164">Элементы данных на уровне процедуры ограничены локальными переменными и константами.</span><span class="sxs-lookup"><span data-stu-id="3d976-164">Data elements at procedure level are limited to local variables and constants.</span></span>  
  
## <a name="the-main-procedure"></a><span data-ttu-id="3d976-165">Основная процедура</span><span class="sxs-lookup"><span data-stu-id="3d976-165">The Main Procedure</span></span>  

 <span data-ttu-id="3d976-166">`Main`Процедура является первым кодом, который выполняется при загрузке приложения.</span><span class="sxs-lookup"><span data-stu-id="3d976-166">The `Main` procedure is the first code to run when your application has been loaded.</span></span> <span data-ttu-id="3d976-167">`Main` служит в качестве начальной точки и общего управления для приложения.</span><span class="sxs-lookup"><span data-stu-id="3d976-167">`Main` serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="3d976-168">Существует четыре вида `Main` :</span><span class="sxs-lookup"><span data-stu-id="3d976-168">There are four varieties of `Main`:</span></span>  
  
- `Sub Main()`  
  
- `Sub Main(ByVal cmdArgs() As String)`  
  
- `Function Main() As Integer`  
  
- `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 <span data-ttu-id="3d976-169">Наиболее распространенная часть этой процедуры — `Sub Main()` .</span><span class="sxs-lookup"><span data-stu-id="3d976-169">The most common variety of this procedure is `Sub Main()`.</span></span> <span data-ttu-id="3d976-170">Дополнительные сведения см. [в разделе Главная процедура в Visual Basic](main-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="3d976-170">For more information, see [Main Procedure in Visual Basic](main-procedure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d976-171">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3d976-171">See also</span></span>

- [<span data-ttu-id="3d976-172">Процедура Main в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3d976-172">Main Procedure in Visual Basic</span></span>](main-procedure.md)
- [<span data-ttu-id="3d976-173">Соглашения об именах Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3d976-173">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="3d976-174">Ограничения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3d976-174">Visual Basic Limitations</span></span>](limitations.md)
