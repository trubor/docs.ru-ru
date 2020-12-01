---
title: Создание и компиляция исходного кода из графа CodeDOM
description: Создавайте и компилируйте исходный код из графа CodeDOM в .NET. Используйте поставщик кода CodeDOM для создания исходного кода и компиляции сборок.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- CodeDOM, generating source code
- Code Document Object Model, graphs
- templated code generation
- source code, generating
- dynamically representing source code
- generating CodeDOM graphs
- Code Document Object Model, generating source code
- translating language to language
- compiling assemblies
- generating source code in multiple languages
- graphing with CodeDOM
- dynamic compilation
- assemblies [.NET Framework], CodeDOM
- source code generation
- outputting source code by CodeDOM
- code generators
- compiling source code, multiple languages
- CodeDOM, graphs
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
ms.openlocfilehash: aec7d6b44e63558ae70bc0eb41f94e55c8a6c325
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266341"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="046fe-104">Создание и компиляция исходного кода из графа CodeDOM</span><span class="sxs-lookup"><span data-stu-id="046fe-104">Generating and Compiling Source Code from a CodeDOM Graph</span></span>

<span data-ttu-id="046fe-105">Пространство имен <xref:System.CodeDom.Compiler> предоставляет интерфейсы для создания исходного кода из графов объекта CodeDOM и для управления компиляцией в поддерживаемых компиляторах.</span><span class="sxs-lookup"><span data-stu-id="046fe-105">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="046fe-106">Поставщик кода может создавать исходный код на конкретном языке программирования, используя граф CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="046fe-106">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="046fe-107">Класс, производный от <xref:System.CodeDom.Compiler.CodeDomProvider>, обычно может предоставлять методы для создания и компиляции кода для языка, поддерживаемого поставщиком.</span><span class="sxs-lookup"><span data-stu-id="046fe-107">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="046fe-108">Использование поставщика кода CodeDOM для создания исходного кода</span><span class="sxs-lookup"><span data-stu-id="046fe-108">Using a CodeDOM code provider to generate source code</span></span>  

 <span data-ttu-id="046fe-109">Чтобы создать исходный код на конкретном языке, необходим граф CodeDOM, представляющий структуру создаваемого исходного кода.</span><span class="sxs-lookup"><span data-stu-id="046fe-109">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="046fe-110">В следующем примере демонстрируется создание экземпляра <xref:Microsoft.CSharp.CSharpCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="046fe-110">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="046fe-111">Граф для создания кода, как правило, содержится в <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="046fe-111">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="046fe-112">Чтобы создать код для **CodeCompileUnit**, содержащего граф CodeDOM, вызовите метод <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> поставщика кода.</span><span class="sxs-lookup"><span data-stu-id="046fe-112">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="046fe-113">Этот метод имеет параметр для указания объекта <xref:System.IO.TextWriter>, используемого для создания исходного кода, поэтому иногда сначала необходимо создавать **TextWriter**, в который и будет осуществляться запись.</span><span class="sxs-lookup"><span data-stu-id="046fe-113">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="046fe-114">В следующем примере демонстрируется генерация кода из **CodeCompileUnit** и запись созданного исходного кода в файл с именем HelloWorld.cs.</span><span class="sxs-lookup"><span data-stu-id="046fe-114">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="046fe-115">Использование поставщика кода CodeDOM для компиляции сборок</span><span class="sxs-lookup"><span data-stu-id="046fe-115">Using a CodeDOM code provider to compile assemblies</span></span>  

 <span data-ttu-id="046fe-116">**Вызов процесса компиляции**</span><span class="sxs-lookup"><span data-stu-id="046fe-116">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="046fe-117">Чтобы скомпилировать сборку, используя поставщик CodeDom, необходимо иметь либо исходный код для компиляции на языке, для которого есть компилятор, либо граф CodeDOM, из которого может быть создан исходный код для компиляции.</span><span class="sxs-lookup"><span data-stu-id="046fe-117">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="046fe-118">При компиляции из графа CodeDOM передайте объект <xref:System.CodeDom.CodeCompileUnit>, содержащий граф, в метод <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> поставщика кода.</span><span class="sxs-lookup"><span data-stu-id="046fe-118">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="046fe-119">Если имеется файл исходного кода на языке, который понимает компилятор, передайте имя файла, содержащего исходный код, в метод <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> поставщика CodeDom.</span><span class="sxs-lookup"><span data-stu-id="046fe-119">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="046fe-120">Также можно передать строку, содержащую исходный код на языке, воспринимаемом компилятором, в метод <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> поставщика CodeDom.</span><span class="sxs-lookup"><span data-stu-id="046fe-120">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="046fe-121">**Настройка параметров компиляции**</span><span class="sxs-lookup"><span data-stu-id="046fe-121">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="046fe-122">Все стандартные методы вызова компиляции поставщика CodeDom имеют параметр типа <xref:System.CodeDom.Compiler.CompilerParameters>, который указывает параметры, используемые для компиляции.</span><span class="sxs-lookup"><span data-stu-id="046fe-122">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="046fe-123">Можно указать имя файла для выходной сборки в свойстве <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> объекта **CompilerParameters**.</span><span class="sxs-lookup"><span data-stu-id="046fe-123">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="046fe-124">В противном случае будет использоваться имя выходного файла по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="046fe-124">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="046fe-125">По умолчанию инициализируется новый объект **CompilerParameters** со свойством <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A>, равным **false**.</span><span class="sxs-lookup"><span data-stu-id="046fe-125">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="046fe-126">При компиляции исполняемой программы необходимо установить значение свойства **GenerateExecutable** равным **true**.</span><span class="sxs-lookup"><span data-stu-id="046fe-126">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="046fe-127">Если **GenerateExecutable** имеет значение **false**, компилятор создаст библиотеку классов.</span><span class="sxs-lookup"><span data-stu-id="046fe-127">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="046fe-128">При компиляции исполняемой программы из графа CodeDOM следует определить в графе объект <xref:System.CodeDom.CodeEntryPointMethod>.</span><span class="sxs-lookup"><span data-stu-id="046fe-128">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="046fe-129">Если в коде имеется несколько точек входа, может понадобиться задать свойство <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> объекта **CompilerParameters** равным имени класса, в котором определяется используемая точка входа.</span><span class="sxs-lookup"><span data-stu-id="046fe-129">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="046fe-130">Чтобы включить сведения об отладке в создаваемый исполняемый файл, присвойте свойству <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> значение **true**.</span><span class="sxs-lookup"><span data-stu-id="046fe-130">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="046fe-131">Если проект ссылается на какие-либо сборки, необходимо указать имена этих сборок, как элементы в коллекции <xref:System.Collections.Specialized.StringCollection>, так же, как свойство <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> объекта **CompilerParameters** используется при вызове компиляции.</span><span class="sxs-lookup"><span data-stu-id="046fe-131">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="046fe-132">Для того чтобы скомпилированная сборка записывалась в память, а не на диск, задайте для свойства <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> значение **true**.</span><span class="sxs-lookup"><span data-stu-id="046fe-132">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="046fe-133">При создании сборки в памяти код может получить ссылку на создаваемую сборку из свойства <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> объекта <xref:System.CodeDom.Compiler.CompilerResults>.</span><span class="sxs-lookup"><span data-stu-id="046fe-133">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="046fe-134">При записи сборки на диск можно получить путь к созданной сборке из свойства <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> объекта **CompilerResults**.</span><span class="sxs-lookup"><span data-stu-id="046fe-134">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="046fe-135">Чтобы указать пользовательскую строку аргументов командной строки, которую следует использовать при вызове процесса компиляции, задайте строку в свойстве <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A>.</span><span class="sxs-lookup"><span data-stu-id="046fe-135">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="046fe-136">Если для вызова процесса компилятора требуется маркер безопасности Win32, задайте этот маркер в свойстве <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A>.</span><span class="sxs-lookup"><span data-stu-id="046fe-136">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="046fe-137">Чтобы сделать ссылку на исходный файл Win32 в скомпилированной сборке, укажите имя исходного файла Win32 в свойстве <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A>.</span><span class="sxs-lookup"><span data-stu-id="046fe-137">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="046fe-138">Чтобы указать уровень предупреждения, на котором следует прекратить компиляцию, задайте свойство <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> как целое число, представляющее уровень предупреждения для прекращения компиляции.</span><span class="sxs-lookup"><span data-stu-id="046fe-138">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="046fe-139">Можно также настроить компилятор для прекращения компиляции при обнаружении предупреждений, задав свойству <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> значение **true**.</span><span class="sxs-lookup"><span data-stu-id="046fe-139">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="046fe-140">В следующем примере кода демонстрируется компиляция исходного файла с помощью поставщика CodeDom, производного от класса <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="046fe-140">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="046fe-141">Встроенная поддержка языков</span><span class="sxs-lookup"><span data-stu-id="046fe-141">Languages with Initial Support</span></span>  

 <span data-ttu-id="046fe-142">.NET Framework предоставляет компиляторы и генераторы кода для следующих языков: C#, Visual Basic, C++ и JScript.</span><span class="sxs-lookup"><span data-stu-id="046fe-142">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="046fe-143">Поддержка CodeDOM может быть расширена на другие языки путем реализации генераторов и компиляторов кода для определенных языков.</span><span class="sxs-lookup"><span data-stu-id="046fe-143">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="046fe-144">См. также</span><span class="sxs-lookup"><span data-stu-id="046fe-144">See also</span></span>

- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- [<span data-ttu-id="046fe-145">Динамическое создание и компиляция исходного кода</span><span class="sxs-lookup"><span data-stu-id="046fe-145">Dynamic Source Code Generation and Compilation</span></span>](dynamic-source-code-generation-and-compilation.md)
- <span data-ttu-id="046fe-146">[Краткий справочник по CodeDOM](/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="046fe-146">[CodeDOM Quick Reference](/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>
