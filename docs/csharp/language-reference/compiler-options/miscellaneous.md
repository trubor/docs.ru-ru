---
description: Прочие параметры компилятора C#. Это общие параметры для компилятора.
title: Параметры компилятора C#, которые не относятся к другим категориям
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- ResponseFiles compiler option [C#]
- NoLogo compiler option [C#]
- NoConfig compiler option [C#]
ms.openlocfilehash: ec7d9c3685c9acb5ca3cda28aca55abb26b836cf
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103482478"
---
# <a name="miscellaneous-c-compiler-options"></a><span data-ttu-id="ea71e-104">Прочие параметры компилятора C#</span><span class="sxs-lookup"><span data-stu-id="ea71e-104">Miscellaneous C# Compiler Options</span></span>

<span data-ttu-id="ea71e-105">Следующие параметры управляют прочей функциональностью компилятора.</span><span class="sxs-lookup"><span data-stu-id="ea71e-105">The following options control miscellaneous compiler behavior.</span></span> <span data-ttu-id="ea71e-106">Новый синтаксис MSBuild выделен **полужирным шрифтом**.</span><span class="sxs-lookup"><span data-stu-id="ea71e-106">The new MSBuild syntax is shown in **Bold**.</span></span> <span data-ttu-id="ea71e-107">Для старого синтаксиса *csc.exe* используется формат `code style`.</span><span class="sxs-lookup"><span data-stu-id="ea71e-107">The older *csc.exe* syntax is shown in `code style`.</span></span>

- <span data-ttu-id="ea71e-108">**ResponseFiles** / `-@`: считывание файла ответов с дополнительными параметрами.</span><span class="sxs-lookup"><span data-stu-id="ea71e-108">**ResponseFiles** / `-@`: Read response file for more options.</span></span>
- <span data-ttu-id="ea71e-109">**NoLogo** / `-nologo`: запрещает отображение сообщения компилятора об авторских правах.</span><span class="sxs-lookup"><span data-stu-id="ea71e-109">**NoLogo** / `-nologo` : Suppress compiler copyright message.</span></span>
- <span data-ttu-id="ea71e-110">**NoConfig** / `-noconfig`: запрещает автоматическое включение файла *CSC.RSP*.</span><span class="sxs-lookup"><span data-stu-id="ea71e-110">**NoConfig** / `-noconfig`: Don't auto include *CSC.RSP* file.</span></span>

## <a name="responsefiles"></a><span data-ttu-id="ea71e-111">ResponseFiles</span><span class="sxs-lookup"><span data-stu-id="ea71e-111">ResponseFiles</span></span>

<span data-ttu-id="ea71e-112">С помощью параметра **ResponseFiles** можно указать файл, содержащий параметры компилятора и список файлов исходного кода, которые требуется компилировать.</span><span class="sxs-lookup"><span data-stu-id="ea71e-112">The **ResponseFiles** option lets you specify a file that contains compiler options and source code files to compile.</span></span>

```xml
<ResponseFiles>response_file</ResponseFiles>
```

<span data-ttu-id="ea71e-113">`response_file` указывает файл, содержащий список параметров компилятора и файлов исходного кода, которые требуется компилировать.</span><span class="sxs-lookup"><span data-stu-id="ea71e-113">The `response_file` specifies the file that lists compiler options or source code files to compile.</span></span> <span data-ttu-id="ea71e-114">Параметры компилятора и файлы исходного кода будут обрабатываться компилятором таким образом, как если бы они были указаны в командной строке.</span><span class="sxs-lookup"><span data-stu-id="ea71e-114">The compiler options and source code files will be processed by the compiler as if they had been specified on the command line.</span></span> <span data-ttu-id="ea71e-115">Чтобы задать несколько файлов ответов для компиляции, используйте соответствующее число параметров файла ответов.</span><span class="sxs-lookup"><span data-stu-id="ea71e-115">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="ea71e-116">В одной строке файла ответов может содержаться несколько параметров компилятора и файлов исходного кода.</span><span class="sxs-lookup"><span data-stu-id="ea71e-116">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="ea71e-117">Спецификация отдельного параметра компилятора должна размещаться на одной строке и не может разбиваться на несколько строк.</span><span class="sxs-lookup"><span data-stu-id="ea71e-117">A single compiler option specification must appear on one line (can't span multiple lines).</span></span> <span data-ttu-id="ea71e-118">В файл ответов можно добавлять комментарии, которые должны начинаться с символа #.</span><span class="sxs-lookup"><span data-stu-id="ea71e-118">Response files can have comments that begin with the # symbol.</span></span> <span data-ttu-id="ea71e-119">Указание параметров компилятора в файле ответов аналогично выполнению соответствующих команд из командной строки.</span><span class="sxs-lookup"><span data-stu-id="ea71e-119">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="ea71e-120">Компилятор обрабатывает параметры команд в том порядке, в котором они считываются.</span><span class="sxs-lookup"><span data-stu-id="ea71e-120">The compiler processes the command options as they're read.</span></span> <span data-ttu-id="ea71e-121">Аргументы командной строки могут переопределять параметры, заданные ранее в файле ответов.</span><span class="sxs-lookup"><span data-stu-id="ea71e-121">Command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="ea71e-122">Аналогичным образом, параметры в файле ответов будут переопределять параметры, ранее заданные в командной строке или в других файлах ответов.</span><span class="sxs-lookup"><span data-stu-id="ea71e-122">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span> <span data-ttu-id="ea71e-123">В C# представлен файл csc.rsp, который находится в одном каталоге с файлом csc.exe.</span><span class="sxs-lookup"><span data-stu-id="ea71e-123">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="ea71e-124">Дополнительные сведения о формате файла ответов см. в разделе о параметре [**NoConfig**](#noconfig).</span><span class="sxs-lookup"><span data-stu-id="ea71e-124">For more information about the response file format, see [**NoConfig**](#noconfig).</span></span> <span data-ttu-id="ea71e-125">Этот параметр компилятора нельзя задать в среде разработки Visual Studio или изменить программными средствами.</span><span class="sxs-lookup"><span data-stu-id="ea71e-125">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span> <span data-ttu-id="ea71e-126">Ниже приведено несколько строк из образца файла ответов:</span><span class="sxs-lookup"><span data-stu-id="ea71e-126">The following are a few lines from a sample response file:</span></span>

```console
# build the first output file
-target:exe -out:MyExe.exe source1.cs source2.cs
```

## <a name="nologo"></a><span data-ttu-id="ea71e-127">NoLogo</span><span class="sxs-lookup"><span data-stu-id="ea71e-127">NoLogo</span></span>

<span data-ttu-id="ea71e-128">Параметр **NoLogo** отключает отображение приветствия при запуске компилятора и информационных сообщений во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="ea71e-128">The **NoLogo** option suppresses display of the sign-on banner when the compiler starts up and display of informational messages during compiling.</span></span>

```xml
<NoLogo>true</NoLogo>
```

## <a name="noconfig"></a><span data-ttu-id="ea71e-129">NoConfig</span><span class="sxs-lookup"><span data-stu-id="ea71e-129">NoConfig</span></span>

<span data-ttu-id="ea71e-130">Параметр **NoConfig** указывает компилятору не использовать файл *csc.rsp* при компиляции.</span><span class="sxs-lookup"><span data-stu-id="ea71e-130">The **NoConfig** option tells the compiler not to compile with the *csc.rsp* file.</span></span>

```xml
<NoConfig>true</NoConfig>
```

<span data-ttu-id="ea71e-131">Файл *csc.rsp* содержит ссылки на все сборки, поставляемые вместе с .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ea71e-131">The *csc.rsp* file references all the assemblies shipped with .NET Framework.</span></span> <span data-ttu-id="ea71e-132">Фактические ссылки, которые включает среда разработки Visual Studio .NET, зависят от типа проекта.</span><span class="sxs-lookup"><span data-stu-id="ea71e-132">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span> <span data-ttu-id="ea71e-133">Вы можете изменить файл *csc.rsp* и указать дополнительные параметры компилятора, которые нужно включать при каждой компиляции.</span><span class="sxs-lookup"><span data-stu-id="ea71e-133">You can modify the *csc.rsp* file and specify additional compiler options that should be included in every compilation.</span></span> <span data-ttu-id="ea71e-134">Если не требуется, чтобы компилятор искал и использовал параметры в файле *csc.rsp*, укажите параметр **NoConfig**.</span><span class="sxs-lookup"><span data-stu-id="ea71e-134">If you don't want the compiler to look for and use the settings in the *csc.rsp* file, specify **NoConfig**.</span></span> <span data-ttu-id="ea71e-135">Этот параметр компилятора недоступен в Visual Studio и не может быть изменен программным способом.</span><span class="sxs-lookup"><span data-stu-id="ea71e-135">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>
