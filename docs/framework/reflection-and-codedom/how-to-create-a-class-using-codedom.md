---
title: Практическое руководство. Создание класса с помощью CodeDOM
description: Изучите подробный пример, в котором объясняется, как создать класс с помощью Code Document Object Model (CodeDOM).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code Document Object Model, graphs
- Code Document Object Model, creating classes
- graphing with CodeDOM
- CodeDOM, creating classes
- CodeDOM, graphs
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
ms.openlocfilehash: 7c2cda2bb7cbdb93c27aef91c08f7c7227da7eed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235705"
---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="bfe21-103">Практическое руководство. Создание класса с помощью CodeDOM</span><span class="sxs-lookup"><span data-stu-id="bfe21-103">How to: Create a Class Using CodeDOM</span></span>

<span data-ttu-id="bfe21-104">В следующих процедурах демонстрируется создание и компиляция графа CodeDOM, который создает класс, содержащий два поля, три свойства, метод, конструктор и точку входа.</span><span class="sxs-lookup"><span data-stu-id="bfe21-104">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1. <span data-ttu-id="bfe21-105">Создайте приложение консоли, которое будет использовать код CodeDOM для создания исходного кода класса.</span><span class="sxs-lookup"><span data-stu-id="bfe21-105">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="bfe21-106">В этом примере создающий класс называется `Sample`, а созданный код — это класс `CodeDOMCreatedClass` в файле с именем SampleCode.</span><span class="sxs-lookup"><span data-stu-id="bfe21-106">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2. <span data-ttu-id="bfe21-107">В создающем классе инициализируйте граф CodeDOM и используйте методы CodeDOM для определения элементов, конструктора и точки входа (метод `Main`) созданного класса.</span><span class="sxs-lookup"><span data-stu-id="bfe21-107">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="bfe21-108">В этом примере созданный класс имеет два поля, три свойства, конструктор, метод и метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="bfe21-108">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3. <span data-ttu-id="bfe21-109">В создающем классе создайте поставщик кода определенного языка и вызовите его метод <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> для создания кода из графа.</span><span class="sxs-lookup"><span data-stu-id="bfe21-109">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4. <span data-ttu-id="bfe21-110">Скомпилируйте и выполните приложение для создания кода.</span><span class="sxs-lookup"><span data-stu-id="bfe21-110">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="bfe21-111">В этом примере созданный код находится в файле с именем SampleCode.</span><span class="sxs-lookup"><span data-stu-id="bfe21-111">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="bfe21-112">Скомпилируйте и выполните этот код для просмотра выходных данных примера.</span><span class="sxs-lookup"><span data-stu-id="bfe21-112">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="bfe21-113">Создание приложения, которое будет выполнять код CodeDOM</span><span class="sxs-lookup"><span data-stu-id="bfe21-113">To create the application that will execute the CodeDOM code</span></span>  
  
- <span data-ttu-id="bfe21-114">Создайте класс приложения консоли для включения кода CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="bfe21-114">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="bfe21-115">Определите глобальные поля, которые должны использоваться в классе для ссылки на сборку (<xref:System.CodeDom.CodeCompileUnit>) и класс (<xref:System.CodeDom.CodeTypeDeclaration>), укажите имя созданного исходного файла и объявите метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="bfe21-115">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="bfe21-116">Инициализация графа CodeDOM</span><span class="sxs-lookup"><span data-stu-id="bfe21-116">To initialize the CodeDOM graph</span></span>  
  
- <span data-ttu-id="bfe21-117">В конструкторе для класса приложения консоли инициализируйте сборку и класс, затем добавьте соответствующие объявления в граф CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="bfe21-117">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="bfe21-118">Добавление элементов в граф CodeDOM</span><span class="sxs-lookup"><span data-stu-id="bfe21-118">To add members to the CodeDOM graph</span></span>  
  
- <span data-ttu-id="bfe21-119">Добавьте поля в граф CodeDOM, добавив объекты <xref:System.CodeDom.CodeMemberField> в свойство <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> класса.</span><span class="sxs-lookup"><span data-stu-id="bfe21-119">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- <span data-ttu-id="bfe21-120">Добавьте свойства в граф CodeDOM, добавив объекты <xref:System.CodeDom.CodeMemberProperty> в свойство <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> класса.</span><span class="sxs-lookup"><span data-stu-id="bfe21-120">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- <span data-ttu-id="bfe21-121">Добавьте метод в граф CodeDOM, добавив объект <xref:System.CodeDom.CodeMemberMethod> в свойство <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> класса.</span><span class="sxs-lookup"><span data-stu-id="bfe21-121">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- <span data-ttu-id="bfe21-122">Добавьте конструктор в граф CodeDOM, добавив объект <xref:System.CodeDom.CodeConstructor> в свойство <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> класса.</span><span class="sxs-lookup"><span data-stu-id="bfe21-122">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- <span data-ttu-id="bfe21-123">Добавьте точку входа вграф CodeDOM, добавив объект <xref:System.CodeDom.CodeEntryPointMethod> в свойство <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> класса.</span><span class="sxs-lookup"><span data-stu-id="bfe21-123">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="bfe21-124">Создание кода из графа CodeDOM</span><span class="sxs-lookup"><span data-stu-id="bfe21-124">To generate the code from the CodeDOM graph</span></span>  
  
- <span data-ttu-id="bfe21-125">Создайте исходный код из графа CodeDOM, вызвав метод <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A>.</span><span class="sxs-lookup"><span data-stu-id="bfe21-125">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="bfe21-126">Создание графа и генерация кода</span><span class="sxs-lookup"><span data-stu-id="bfe21-126">To create the graph and generate the code</span></span>  
  
1. <span data-ttu-id="bfe21-127">Добавьте методы, созданные на предыдущих этапах, в метод `Main`, определенный на первом этапе.</span><span class="sxs-lookup"><span data-stu-id="bfe21-127">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. <span data-ttu-id="bfe21-128">Скомпилируйте и выполните создающий класс.</span><span class="sxs-lookup"><span data-stu-id="bfe21-128">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfe21-129">Пример</span><span class="sxs-lookup"><span data-stu-id="bfe21-129">Example</span></span>  

 <span data-ttu-id="bfe21-130">В следующем примере кода представлен код, созданный на предыдущих этапах.</span><span class="sxs-lookup"><span data-stu-id="bfe21-130">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="bfe21-131">При компиляции и выполнении предыдущего примера, происходит создание следующего исходного кода.</span><span class="sxs-lookup"><span data-stu-id="bfe21-131">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="bfe21-132">Созданный исходный код формирует следующие выходные данные при компиляции и выполнении.</span><span class="sxs-lookup"><span data-stu-id="bfe21-132">The generated source code produces the following output when compiled and executed.</span></span>  
  
```output
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bfe21-133">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="bfe21-133">Compiling the Code</span></span>  
  
- <span data-ttu-id="bfe21-134">Для выполнения этого кода должно быть установлено разрешение `FullTrust`.</span><span class="sxs-lookup"><span data-stu-id="bfe21-134">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfe21-135">См. также</span><span class="sxs-lookup"><span data-stu-id="bfe21-135">See also</span></span>

- [<span data-ttu-id="bfe21-136">Использование CodeDOM</span><span class="sxs-lookup"><span data-stu-id="bfe21-136">Using the CodeDOM</span></span>](using-the-codedom.md)
- [<span data-ttu-id="bfe21-137">Создание и компиляция исходного кода из графа CodeDOM</span><span class="sxs-lookup"><span data-stu-id="bfe21-137">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)
