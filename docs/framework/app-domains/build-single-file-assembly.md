---
title: Практическое руководство. Создание однофайловой сборки .NET Framework
description: Сведения о построении однофайловой сборки в .NET. Однофайловая сборка может представлять собой ориентированную на .NET библиотеку (DLL) или исполняемый файл (EXE).
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: bdffa9417a7d52e9c825ca6455997b9bfa7408e4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271529"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="07e4a-104">Практическое руководство. Создание однофайловой сборки .NET Framework</span><span class="sxs-lookup"><span data-stu-id="07e4a-104">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="07e4a-105">Однофайловая сборка, являясь простейшим типом сборки, содержит данные о типе и реализации, а также [манифест сборки](../../standard/assembly/manifest.md).</span><span class="sxs-lookup"><span data-stu-id="07e4a-105">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="07e4a-106">Для создания однофайловой сборки, ориентированной на .NET Framework, можно использовать компиляторы командной строки или Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07e4a-106">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="07e4a-107">По умолчанию компилятор создает файл сборки с расширением *EXE*.</span><span class="sxs-lookup"><span data-stu-id="07e4a-107">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="07e4a-108">Visual Studio для C# и Visual Basic можно использовать только для создания однофайловых сборок.</span><span class="sxs-lookup"><span data-stu-id="07e4a-108">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="07e4a-109">Чтобы создать многофайловую сборку, необходимо использовать компиляторы командной строки или Visual C++.</span><span class="sxs-lookup"><span data-stu-id="07e4a-109">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="07e4a-110">В следующих процедурах показано создани6 однофайловых сборок с помощью компиляторов, работающих в режиме командной строки.</span><span class="sxs-lookup"><span data-stu-id="07e4a-110">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="07e4a-111">Создание сборки с расширением EXE</span><span class="sxs-lookup"><span data-stu-id="07e4a-111">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="07e4a-112">В командной строке введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="07e4a-112">At the command prompt, type the following command:</span></span>

<span data-ttu-id="07e4a-113">\<*compiler command*> \<*module name*></span><span class="sxs-lookup"><span data-stu-id="07e4a-113">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="07e4a-114">В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, а *имя модуля* — имя компилируемого в сборку модуля кода.</span><span class="sxs-lookup"><span data-stu-id="07e4a-114">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="07e4a-115">В следующем примере создается сборка с именем *myCode.exe* из модуля кода с именем `myCode`.</span><span class="sxs-lookup"><span data-stu-id="07e4a-115">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="07e4a-116">Создание сборки с расширением EXE и указание имени выходного файла</span><span class="sxs-lookup"><span data-stu-id="07e4a-116">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="07e4a-117">В командной строке введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="07e4a-117">At the command prompt, type the following command:</span></span>

<span data-ttu-id="07e4a-118">\<*compiler command*> **/out:** \<*file name*> \<*module name*></span><span class="sxs-lookup"><span data-stu-id="07e4a-118">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="07e4a-119">В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, *имя файла* — имя выходного файла, а *имя модуля* — имя компилируемого в сборку модуля кода.</span><span class="sxs-lookup"><span data-stu-id="07e4a-119">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="07e4a-120">В следующем примере создается сборка с именем *myAssembly.exe* из модуля кода с именем `myCode`.</span><span class="sxs-lookup"><span data-stu-id="07e4a-120">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="07e4a-121">Создание библиотечных сборок</span><span class="sxs-lookup"><span data-stu-id="07e4a-121">Create library assemblies</span></span>

 <span data-ttu-id="07e4a-122">Библиотечная сборка аналогична библиотеке классов.</span><span class="sxs-lookup"><span data-stu-id="07e4a-122">A library assembly is similar to a class library.</span></span> <span data-ttu-id="07e4a-123">Библиотечная сборка аналогична библиотеке классов. Она содержит типы, на которые имеются ссылки в других сборках, но не имеет точки входа, с которой начинается выполнение.</span><span class="sxs-lookup"><span data-stu-id="07e4a-123">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="07e4a-124">Чтобы создать библиотечную сборку, в командной строке введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="07e4a-124">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="07e4a-125">\<*compiler command*> **-t:library** \<*module name*></span><span class="sxs-lookup"><span data-stu-id="07e4a-125">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="07e4a-126">В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, а *имя модуля* — имя компилируемого в сборку модуля кода.</span><span class="sxs-lookup"><span data-stu-id="07e4a-126">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="07e4a-127">Можно также использовать другие параметры компилятора, такие как **-out:** .</span><span class="sxs-lookup"><span data-stu-id="07e4a-127">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="07e4a-128">В следующем примере создается библиотечная сборка с именем *myCodeAssembly.dll* из модуля кода с именем `myCode`.</span><span class="sxs-lookup"><span data-stu-id="07e4a-128">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="07e4a-129">См. также</span><span class="sxs-lookup"><span data-stu-id="07e4a-129">See also</span></span>

- [<span data-ttu-id="07e4a-130">Создание сборок</span><span class="sxs-lookup"><span data-stu-id="07e4a-130">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="07e4a-131">Многофайловые сборки</span><span class="sxs-lookup"><span data-stu-id="07e4a-131">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="07e4a-132">Практическое руководство. Создание многофайловой сборки</span><span class="sxs-lookup"><span data-stu-id="07e4a-132">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="07e4a-133">Программирование с использованием сборок</span><span class="sxs-lookup"><span data-stu-id="07e4a-133">Program with assemblies</span></span>](../../standard/assembly/index.md)
