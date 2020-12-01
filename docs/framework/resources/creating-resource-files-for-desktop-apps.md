---
title: Создание файлов ресурсов для приложений .NET
description: Создавайте файлы ресурсов для приложений .NET. Создавайте текстовые файлы со строковыми ресурсами, XML или двоичные файлы программным способом или XML-файлы, содержащие строковые данные, данные изображений или объектов.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resources files
- .resources files
- application resources, creating files
- resource files, creating
ms.assetid: 6c5ad891-66a0-4e7a-adcf-f41863ba6d8d
ms.openlocfilehash: d10af40420c1ab9ab177514c0babeaf5cea96922
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259080"
---
# <a name="create-resource-files-for-net-apps"></a><span data-ttu-id="ed02e-104">Создание файлов ресурсов для приложений .NET</span><span class="sxs-lookup"><span data-stu-id="ed02e-104">Create resource files for .NET apps</span></span>

<span data-ttu-id="ed02e-105">Ресурсы, такие как строки, изображения или данные объектов, можно включать в файлы ресурсов, чтобы сделать их легко доступными для приложения.</span><span class="sxs-lookup"><span data-stu-id="ed02e-105">You can include resources, such as strings, images, or object data, in resources files to make them easily available to your application.</span></span> <span data-ttu-id="ed02e-106">В платформе .NET Framework предлагается пять способов создания файлов ресурсов.</span><span class="sxs-lookup"><span data-stu-id="ed02e-106">The .NET Framework offers five ways to create resources files:</span></span>

- <span data-ttu-id="ed02e-107">Создайте текстовый файл, содержащий строковые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="ed02e-107">Create a text file that contains string resources.</span></span> <span data-ttu-id="ed02e-108">Для преобразования текстового файла в двоичный файл ресурсов (RESOURCES-файл) можно использовать [генератор файлов ресурсов (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md).</span><span class="sxs-lookup"><span data-stu-id="ed02e-108">You can use [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to convert the text file into a binary resource (.resources) file.</span></span> <span data-ttu-id="ed02e-109">Затем можно внедрить двоичный файл ресурсов в исполняемый файл приложения или библиотеку приложения с помощью компилятора языка или во вспомогательную сборку с помощью [компоновщика сборок (Al.exe)](../tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="ed02e-109">You can then embed the binary resource file  in an application executable or an application library by using a language compiler, or you can embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="ed02e-110">Дополнительные сведения см. в разделе [Ресурсы в текстовых файлах](creating-resource-files-for-desktop-apps.md#TextFiles).</span><span class="sxs-lookup"><span data-stu-id="ed02e-110">For more information, see the [Resources in Text Files](creating-resource-files-for-desktop-apps.md#TextFiles) section.</span></span>

- <span data-ttu-id="ed02e-111">Создайте XML-файл ресурсов (RESX-файл), который содержит строки, изображения или данные объектов.</span><span class="sxs-lookup"><span data-stu-id="ed02e-111">Create an XML resource (.resx) file that contains string, image, or object data.</span></span> <span data-ttu-id="ed02e-112">Для преобразования RESX-файла в двоичный файл ресурсов (RESOURCES-файл) можно использовать [генератор файлов ресурсов (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md).</span><span class="sxs-lookup"><span data-stu-id="ed02e-112">You can use [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to convert the .resx file into a binary resource (.resources) file.</span></span> <span data-ttu-id="ed02e-113">Затем двоичный файл ресурсов можно внедрить в исполняемый файл приложения или библиотеку приложения с помощью компилятора языка или во вспомогательную сборку с помощью [компоновщика сборок (Al.exe)](../tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="ed02e-113">You can then embed the binary resource file in an application executable or an application library by using a language compiler, or you can embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="ed02e-114">Дополнительные сведения см. в разделе [Ресурсы в RESX-файлах](creating-resource-files-for-desktop-apps.md#ResxFiles).</span><span class="sxs-lookup"><span data-stu-id="ed02e-114">For more information, see the [Resources in .resx Files](creating-resource-files-for-desktop-apps.md#ResxFiles) section.</span></span>

- <span data-ttu-id="ed02e-115">Создайте XML-файл ресурсов (RESX-файл) программным способом с помощью типов в пространстве имен <xref:System.Resources>.</span><span class="sxs-lookup"><span data-stu-id="ed02e-115">Create an XML resource (.resx) file programmatically by using types in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="ed02e-116">Можно создать RESX-файл, перечислить его ресурсы и извлечь конкретные ресурсы по имени.</span><span class="sxs-lookup"><span data-stu-id="ed02e-116">You can create a .resx file, enumerate its resources, and retrieve specific resources by name.</span></span> <span data-ttu-id="ed02e-117">Дополнительные сведения см. в разделе [Работа с RESX-файлами программным способом](working-with-resx-files-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="ed02e-117">For more information, see [Working with .resx Files Programmatically](working-with-resx-files-programmatically.md).</span></span>

- <span data-ttu-id="ed02e-118">Создайте двоичный файл ресурсов (RESOURCES-файл) программным способом.</span><span class="sxs-lookup"><span data-stu-id="ed02e-118">Create a binary resource (.resources) file programmatically.</span></span> <span data-ttu-id="ed02e-119">Затем этот файл можно внедрить в исполняемый файл приложения или библиотеку приложения с помощью компилятора языка или во вспомогательную сборку с помощью [компоновщика сборок (Al.exe)](../tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="ed02e-119">You can then embed the file in an application executable or an application library by using a language compiler, or you can embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="ed02e-120">Дополнительные сведения см. в разделе [Ресурсы в RESOURCES-файлах](creating-resource-files-for-desktop-apps.md#ResourcesFiles).</span><span class="sxs-lookup"><span data-stu-id="ed02e-120">For more information, see the [Resources in .resources Files](creating-resource-files-for-desktop-apps.md#ResourcesFiles) section.</span></span>

- <span data-ttu-id="ed02e-121">Создайте файл ресурсов в [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) и включите этот файл в проект.</span><span class="sxs-lookup"><span data-stu-id="ed02e-121">Use [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) to create a resource file and include it in your project.</span></span> <span data-ttu-id="ed02e-122">В Visual Studio есть редактор ресурсов,с помощью которого можно добавлять, удалять и изменять ресурсы.</span><span class="sxs-lookup"><span data-stu-id="ed02e-122">Visual Studio provides a resource editor that lets you add, delete, and modify resources.</span></span> <span data-ttu-id="ed02e-123">Во время компиляции файл ресурсов автоматически преобразуется в двоичный RESOURCES-файл и внедряется в сборку приложения или вспомогательную сборку.</span><span class="sxs-lookup"><span data-stu-id="ed02e-123">At compile time, the resource file is automatically converted to a binary .resources file and embedded in an application assembly or satellite assembly.</span></span> <span data-ttu-id="ed02e-124">Дополнительные сведения см. в разделе [Файлы ресурсов в Visual Studio](creating-resource-files-for-desktop-apps.md#VSResFiles).</span><span class="sxs-lookup"><span data-stu-id="ed02e-124">For more information, see the [Resource Files in Visual Studio](creating-resource-files-for-desktop-apps.md#VSResFiles) section.</span></span>

<a name="TextFiles"></a>

## <a name="resources-in-text-files"></a><span data-ttu-id="ed02e-125">Ресурсы в формате текстовых файлов</span><span class="sxs-lookup"><span data-stu-id="ed02e-125">Resources in text files</span></span>

<span data-ttu-id="ed02e-126">В текстовых файлах (TXT или RESTEXT) можно сохранять только строковые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="ed02e-126">You can use text (.txt or .restext) files to store string resources only.</span></span> <span data-ttu-id="ed02e-127">Для нестроковых ресурсов используйте RESX-файлы или создавайте их программными средствами.</span><span class="sxs-lookup"><span data-stu-id="ed02e-127">For non-string resources, use .resx files or create them programmatically.</span></span> <span data-ttu-id="ed02e-128">Текстовые файлы, содержащие строковые ресурсы, имеют следующий формат.</span><span class="sxs-lookup"><span data-stu-id="ed02e-128">Text files that contain string resources have the following format:</span></span>

```text
# This is an optional comment.
name = value

; This is another optional comment.
name = value

; The following supports conditional compilation if X is defined.
#ifdef X
name1=value1
name2=value2
#endif

# The following supports conditional compilation if Y is undefined.
#if !Y
name1=value1
name2=value2
#endif
```

 <span data-ttu-id="ed02e-129">Форматы TXT- и RESTEXT-файлов ресурсов идентичны.</span><span class="sxs-lookup"><span data-stu-id="ed02e-129">The resource file format of .txt and .restext files is identical.</span></span> <span data-ttu-id="ed02e-130">Расширение файла RESTEX служит для того, чтобы текстовые файлы сразу опознавались как файлы ресурсов на основе текста.</span><span class="sxs-lookup"><span data-stu-id="ed02e-130">The .restext file extension merely serves to make text files immediately identifiable as text-based resource files.</span></span>

 <span data-ttu-id="ed02e-131">Строковые ресурсы представляются в виде пар *имя/значение*, где *имя* — строка, определяющая ресурс, а *значение* — строка ресурса, которая возвращается при передаче *имени* методу извлечения ресурсов, например, <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ed02e-131">String resources appear as *name/value* pairs, where *name* is a string that identifies the resource, and *value* is the resource string that is returned when you pass *name* to a resource retrieval method such as <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ed02e-132">*Имя* и *значение* должны быть разделены знаком равенства (=).</span><span class="sxs-lookup"><span data-stu-id="ed02e-132">*name* and *value* must be separated by an equal sign (=).</span></span> <span data-ttu-id="ed02e-133">Пример:</span><span class="sxs-lookup"><span data-stu-id="ed02e-133">For example:</span></span>

```text
FileMenuName=File
EditMenuName=Edit
ViewMenuName=View
HelpMenuName=Help
```

> [!CAUTION]
> <span data-ttu-id="ed02e-134">Не следует использовать файлы ресурсов для хранения паролей, конфиденциальной информации или личных данных.</span><span class="sxs-lookup"><span data-stu-id="ed02e-134">Do not use resource files to store passwords, security-sensitive information, or private data.</span></span>

 <span data-ttu-id="ed02e-135">В текстовых файлах допускаются пустые строки (то есть, ресурсы, значение которых равно <xref:System.String.Empty?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="ed02e-135">Empty strings (that is, a resource whose value is <xref:System.String.Empty?displayProperty=nameWithType>) are permitted in text files.</span></span> <span data-ttu-id="ed02e-136">Пример:</span><span class="sxs-lookup"><span data-stu-id="ed02e-136">For example:</span></span>

```text
EmptyString=
```

 <span data-ttu-id="ed02e-137">Начиная с .NET Framework 4.5 и во всех версиях .NET Core текстовые файлы поддерживают условную компиляцию с конструкциями `#ifdef`*символ*... `#endif` и `#if !`*символ*... `#endif`.</span><span class="sxs-lookup"><span data-stu-id="ed02e-137">Starting with .NET Framework 4.5 and in all versions of .NET Core, text files support conditional compilation with the `#ifdef`*symbol*... `#endif` and `#if !`*symbol*... `#endif` constructs.</span></span> <span data-ttu-id="ed02e-138">Для определения символов можно использовать [генератор файлов ресурсов (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) с параметром `/define`.</span><span class="sxs-lookup"><span data-stu-id="ed02e-138">You can then use the `/define` switch with [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to define symbols.</span></span> <span data-ttu-id="ed02e-139">Каждый ресурс должен иметь собственную конструкцию `#ifdef`*символ*... `#endif` или `#if !`*символ*... `#endif`.</span><span class="sxs-lookup"><span data-stu-id="ed02e-139">Each resource requires its own `#ifdef`*symbol*... `#endif` or `#if !`*symbol*... `#endif` construct.</span></span> <span data-ttu-id="ed02e-140">Если при использовании оператора `#ifdef` указан *символ*, связанный ресурс добавляется в RESOURCES-файл; в противном случае он не добавляется.</span><span class="sxs-lookup"><span data-stu-id="ed02e-140">If you use an `#ifdef` statement and *symbol* is defined, the associated resource is included in the .resources file; otherwise, it is not included.</span></span> <span data-ttu-id="ed02e-141">Если при использовании оператора `#if !`*символ* не указан, связанный ресурс добавляется в RESOURCES-файл; в противном случае он не добавляется.</span><span class="sxs-lookup"><span data-stu-id="ed02e-141">If you use an `#if !` statement and *symbol* is not defined, the associated resource is included in the .resources file; otherwise, it is not included.</span></span>

 <span data-ttu-id="ed02e-142">Комментарии в текстовых файлах необязательны и начинаются с точки с запятой (;) или знака решетки (#) в начале строки.</span><span class="sxs-lookup"><span data-stu-id="ed02e-142">Comments are optional in text files and are preceded either by a semicolon (;) or by a pound sign (#) at the beginning of a line.</span></span> <span data-ttu-id="ed02e-143">Строки с комментариями могут находиться в любом месте файла.</span><span class="sxs-lookup"><span data-stu-id="ed02e-143">Lines that contain comments can be placed anywhere in the file.</span></span> <span data-ttu-id="ed02e-144">Комментарии не включаются в скомпилированный RESOURCES-файл, созданный с помощью [генератора файлов ресурсов (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md).</span><span class="sxs-lookup"><span data-stu-id="ed02e-144">Comments are not included in a compiled .resources file that is created by using [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md).</span></span>

 <span data-ttu-id="ed02e-145">Любые пустые строки в текстовых файлах считаются содержащими пробелы и игнорируются.</span><span class="sxs-lookup"><span data-stu-id="ed02e-145">Any blank lines in the text files are considered to be white space and are ignored.</span></span>

 <span data-ttu-id="ed02e-146">В следующем примере определяются два строковых ресурса с именами `OKButton` и `CancelButton`.</span><span class="sxs-lookup"><span data-stu-id="ed02e-146">The following example defines two string resources named `OKButton` and `CancelButton`.</span></span>

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 <span data-ttu-id="ed02e-147">Если в текстовом файле содержатся дубликаты *имен*, [генератор файлов ресурсов (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) отображает предупреждение и игнорирует второе имя.</span><span class="sxs-lookup"><span data-stu-id="ed02e-147">If the text file contains duplicate occurrences of *name*, [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) displays a warning and ignores the second name.</span></span>

 <span data-ttu-id="ed02e-148">*Значение* не может содержать символы новой строки. Но с помощью escape-символов языка С можно указать символы новой строки (`\n`) и табуляции (`\t`). Также можно включить символ обратной косой черты, предварив его escape-символом (например, "\\\\").</span><span class="sxs-lookup"><span data-stu-id="ed02e-148">*value* cannot contain new line characters, but you can use C language-style escape characters such as `\n` to represent a new line and `\t` to represent a tab. You can also include a backslash character if it is escaped (for example, "\\\\").</span></span> <span data-ttu-id="ed02e-149">Также допускаются пустые строки.</span><span class="sxs-lookup"><span data-stu-id="ed02e-149">In addition, an empty string is permitted.</span></span>

 <span data-ttu-id="ed02e-150">Сохраняйте ресурсы в формате текстового файла с кодировкой UTF-8 или UTF-16 с прямым или обратным порядком байтов.</span><span class="sxs-lookup"><span data-stu-id="ed02e-150">Save resources in text file format by using UTF-8 encoding or UTF-16 encoding in either little-endian or big-endian byte order.</span></span> <span data-ttu-id="ed02e-151">Но [генератор файлов ресурсов (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md), преобразующий TXT-файл в RESOURCES-файл, по умолчанию обрабатывает файлы в кодировке UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ed02e-151">However, [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md), which converts a .txt file to a .resources file, treats files as UTF-8 by default.</span></span> <span data-ttu-id="ed02e-152">Если вы хотите, чтобы программа Resgen.exe могла работать с файлом в кодировке UTF-16, необходимо указать метку порядка байтов Юникода (U+FEFF) в начале файла.</span><span class="sxs-lookup"><span data-stu-id="ed02e-152">If you want Resgen.exe to recognize a file that was encoded using UTF-16, you must include a Unicode byte order mark (U+FEFF) at the beginning of the file.</span></span>

 <span data-ttu-id="ed02e-153">Чтобы внедрить файл ресурсов в текстовом формате в сборку .NET, необходимо преобразовать текстовый файл в двоичный файл ресурсов (RESOURCES) с помощью [генератора файлов ресурсов (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md).</span><span class="sxs-lookup"><span data-stu-id="ed02e-153">To embed a resource file in text format into a .NET assembly, you must convert the file to a binary resource (.resources) file by using [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md).</span></span> <span data-ttu-id="ed02e-154">Затем можно внедрить RESOURCES-файл в сборку .NET с помощью компилятора языка или во вспомогательную сборку с помощью [компоновщика сборок (Al.exe)](../tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="ed02e-154">You can then embed the .resources file in a .NET assembly by using a language compiler or embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span>

 <span data-ttu-id="ed02e-155">В следующем примере используется файл ресурсов в текстовом формате GreetingResources.txt для простого консольного приложения "Hello World".</span><span class="sxs-lookup"><span data-stu-id="ed02e-155">The following example uses a resource file in text format named GreetingResources.txt for a simple "Hello World" console application.</span></span> <span data-ttu-id="ed02e-156">В этом текстовом файле определены две строки — `prompt` и `greeting`, которые предлагают пользователю ввести свое имя и отображают приветствие.</span><span class="sxs-lookup"><span data-stu-id="ed02e-156">The text file defines two strings, `prompt` and `greeting`, that prompt the user to enter their name and display a greeting.</span></span>

```text
# GreetingResources.txt
# A resource file in text format for a "Hello World" application.
#
# Initial prompt to the user.
prompt=Enter your name:
# Format string to display the result.
greeting=Hello, {0}!
```

<span data-ttu-id="ed02e-157">Текстовый файл преобразуется в RESOURCES-файл с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="ed02e-157">The text file is converted to a .resources file by using the following command:</span></span>

```console
resgen GreetingResources.txt
```

 <span data-ttu-id="ed02e-158">В следующем примере показан исходный код для консольного приложения, которое получает сообщения из RESOURCES-файла и выводит их на экран.</span><span class="sxs-lookup"><span data-stu-id="ed02e-158">The following example shows the source code for a console application that uses the .resources file to display messages to the user.</span></span>

 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]

 <span data-ttu-id="ed02e-159">Если вы используете Visual Basic и файл с исходным кодом называется Greeting.vb, используйте следующую команду для создания исполняемого файла, содержащего внедренный RESOURCES-файл:</span><span class="sxs-lookup"><span data-stu-id="ed02e-159">If you are using Visual Basic, and the source code file is named Greeting.vb, the following command creates an executable file that includes the embedded .resources file:</span></span>

```console
vbc greeting.vb -resource:GreetingResources.resources
```

 <span data-ttu-id="ed02e-160">Если вы используете C# и файл исходного кода называется Greeting.cs, исполняемый файл, содержащий внедренный RESOURCES-файл, создается с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="ed02e-160">If you are using C#, and the source code file is named Greeting.cs, the following command creates an executable file that includes the embedded .resources file:</span></span>

```console
csc greeting.cs -resource:GreetingResources.resources
```

<a name="ResxFiles"></a>

## <a name="resources-in-resx-files"></a><span data-ttu-id="ed02e-161">Ресурсы в RESX-файлах</span><span class="sxs-lookup"><span data-stu-id="ed02e-161">Resources in .resx files</span></span>

 <span data-ttu-id="ed02e-162">В отличие от текстовых файлов, в которых могут храниться только строковые ресурсы, в XML-файлах ресурсов (RESX) могут храниться строки, двоичные данные (такие как изображения, значки и аудиоклипы) и программные объекты.</span><span class="sxs-lookup"><span data-stu-id="ed02e-162">Unlike text files, which can only store string resources, XML resource (.resx) files can store strings, binary data such as images, icons, and audio clips, and programmatic objects.</span></span> <span data-ttu-id="ed02e-163">RESX-файл содержит стандартный заголовок, который описывает формат записей ресурсов и включает сведения о версии XML, которые используются для анализа данных.</span><span class="sxs-lookup"><span data-stu-id="ed02e-163">A .resx file contains a standard header, which describes the format of the resource entries and specifies the versioning information for the XML that is used to parse the data.</span></span> <span data-ttu-id="ed02e-164">За заголовком XML следуют данные в файле ресурсов.</span><span class="sxs-lookup"><span data-stu-id="ed02e-164">The resource file data follows the XML header.</span></span> <span data-ttu-id="ed02e-165">Каждый элемент данных состоит из пары "имя-значение", заключенной в тег `data`.</span><span class="sxs-lookup"><span data-stu-id="ed02e-165">Each data item consists of a name/value pair that is contained in a `data` tag.</span></span> <span data-ttu-id="ed02e-166">Атрибут `name` этого тега определяет имя ресурса, а вложенный тег `value` содержит значение ресурса.</span><span class="sxs-lookup"><span data-stu-id="ed02e-166">Its `name` attribute defines the resource name, and the nested `value` tag contains the resource value.</span></span> <span data-ttu-id="ed02e-167">Для строковых данных тег `value` содержит строку.</span><span class="sxs-lookup"><span data-stu-id="ed02e-167">For string data, the `value` tag contains the string.</span></span>

 <span data-ttu-id="ed02e-168">Например, следующий тег `data` определяет строковый ресурс с именем `prompt` и значением "Enter your name:".</span><span class="sxs-lookup"><span data-stu-id="ed02e-168">For example, the following `data` tag defines a string resource named `prompt` whose value is "Enter your name:".</span></span>

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> <span data-ttu-id="ed02e-169">Не следует использовать файлы ресурсов для хранения паролей, конфиденциальной информации или личных данных.</span><span class="sxs-lookup"><span data-stu-id="ed02e-169">Do not use resource files to store passwords, security-sensitive information, or private data.</span></span>

 <span data-ttu-id="ed02e-170">Для объектов ресурсов тег **data** содержит атрибут `type`, указывающий тип данных ресурса.</span><span class="sxs-lookup"><span data-stu-id="ed02e-170">For resource objects, the **data** tag includes a `type` attribute that indicates the data type of the resource.</span></span> <span data-ttu-id="ed02e-171">Для объектов, состоящих из двоичных данных, тег `data` также включает атрибут `mimetype`, который указывает тип `base64` двоичных данных.</span><span class="sxs-lookup"><span data-stu-id="ed02e-171">For objects that consist of binary data, the `data` tag also includes a `mimetype` attribute, which indicates the `base64` type of the binary data.</span></span>

> [!NOTE]
> <span data-ttu-id="ed02e-172">Во всех RESX-файлах для создания и анализа двоичных данных заданного типа используется форматтер двоичной сериализации.</span><span class="sxs-lookup"><span data-stu-id="ed02e-172">All .resx files use a binary serialization formatter to generate and parse the binary data for a specified type.</span></span> <span data-ttu-id="ed02e-173">В результате, если формат двоичной сериализации для объекта изменится недопустимым образом, RESX-файл может стать недействительным.</span><span class="sxs-lookup"><span data-stu-id="ed02e-173">As a result, a .resx file can become invalid if the binary serialization format for an object changes in an incompatible way.</span></span>

 <span data-ttu-id="ed02e-174">В следующем примере показана часть RESX-файла, в которой содержится ресурс <xref:System.Int32> и растровое изображение.</span><span class="sxs-lookup"><span data-stu-id="ed02e-174">The following example shows a portion of a .resx file that includes an <xref:System.Int32> resource and a bitmap image.</span></span>

```xml
<data name="i1" type="System.Int32, mscorlib">
  <value>20</value>
</data>

<data name="flag" type="System.Drawing.Bitmap, System.Drawing,
    Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
    mimetype="application/x-microsoft.net.object.bytearray.base64">
  <value>
    AAEAAAD/////AQAAAAAAAAAMAgAAADtTeX…
  </value>
</data>
```

> [!IMPORTANT]
> <span data-ttu-id="ed02e-175">Так как RESX-файлы должны представлять собой XML-код с правильным, заранее определенным форматом, с ними не рекомендуется работать вручную, особенно если они содержат нестроковые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="ed02e-175">Because .resx files must consist of well-formed XML in a predefined format, we do not recommend working with .resx files manually, particularly when the .resx files contain resources other than strings.</span></span> <span data-ttu-id="ed02e-176">Вместо этого в [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) предусмотрен прозрачный интерфейс для создания RESX-файлов и управления ими.</span><span class="sxs-lookup"><span data-stu-id="ed02e-176">Instead, [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) provides a transparent interface for creating and manipulating .resx files.</span></span> <span data-ttu-id="ed02e-177">Дополнительные сведения см. в разделе [Файлы ресурсов в Visual Studio](creating-resource-files-for-desktop-apps.md#VSResFiles).</span><span class="sxs-lookup"><span data-stu-id="ed02e-177">For more information, see the [Resource Files in Visual Studio](creating-resource-files-for-desktop-apps.md#VSResFiles) section.</span></span> <span data-ttu-id="ed02e-178">Создавать RESX-файлы и управлять ими можно также программно.</span><span class="sxs-lookup"><span data-stu-id="ed02e-178">You can also create and manipulate .resx files programmatically.</span></span> <span data-ttu-id="ed02e-179">Дополнительные сведения см. в разделе [Работа с RESX-файлами программным способом](working-with-resx-files-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="ed02e-179">For more information, see [Working with .resx Files Programmatically](working-with-resx-files-programmatically.md).</span></span>

<a name="ResourcesFiles"></a>

## <a name="resources-in-resources-files"></a><span data-ttu-id="ed02e-180">Ресурсы в RESOURCES-файлах</span><span class="sxs-lookup"><span data-stu-id="ed02e-180">Resources in .resources files</span></span>

<span data-ttu-id="ed02e-181">Для программного создания двоичного файла ресурсов (RESOURCES-файла) непосредственно из кода можно использовать класс <xref:System.Resources.ResourceWriter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ed02e-181">You can use the <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> class to programmatically create a binary resource (.resources) file directly from code.</span></span> <span data-ttu-id="ed02e-182">Для создания RESOURCES-файла из текстового файла или RESX-файла можно также использовать [генератор файлов ресурсов (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md).</span><span class="sxs-lookup"><span data-stu-id="ed02e-182">You can also use [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to create a .resources file from a text file or a .resx file.</span></span> <span data-ttu-id="ed02e-183">Помимо строковых данных, RESOURCES-файл может содержать двоичные данные (массивы байтов) и данные объектов.</span><span class="sxs-lookup"><span data-stu-id="ed02e-183">The .resources file can contain binary data (byte arrays) and object data in addition to string data.</span></span> <span data-ttu-id="ed02e-184">Для программного создания RESOURCES-файла необходимо выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="ed02e-184">Programmatically creating a .resources file requires the following steps:</span></span>

1. <span data-ttu-id="ed02e-185">Создайте объект <xref:System.Resources.ResourceWriter> с уникальным именем файла.</span><span class="sxs-lookup"><span data-stu-id="ed02e-185">Create a <xref:System.Resources.ResourceWriter> object with a unique file name.</span></span> <span data-ttu-id="ed02e-186">Это можно сделать, указав имя файла или файловый поток для конструктора класса <xref:System.Resources.ResourceWriter>.</span><span class="sxs-lookup"><span data-stu-id="ed02e-186">You can do this by specifying either a file name or a file stream to a <xref:System.Resources.ResourceWriter> class constructor.</span></span>

2. <span data-ttu-id="ed02e-187">Вызовите одну из перегрузок метода <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> для каждого именованного ресурса, который требуется добавить в файл.</span><span class="sxs-lookup"><span data-stu-id="ed02e-187">Call one of the overloads of the <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> method for each named resource to add to the file.</span></span> <span data-ttu-id="ed02e-188">Ресурсом может быть строка, объект или коллекция двоичных данных (массив байтов).</span><span class="sxs-lookup"><span data-stu-id="ed02e-188">The resource can be a string, an object, or a collection of binary data (a byte array).</span></span>

3. <span data-ttu-id="ed02e-189">Вызовете метод <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType>, чтобы записать ресурсы в файл и закрыть объект <xref:System.Resources.ResourceWriter>.</span><span class="sxs-lookup"><span data-stu-id="ed02e-189">Call the <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> method to write the resources to the file and to close the <xref:System.Resources.ResourceWriter> object.</span></span>

> [!NOTE]
> <span data-ttu-id="ed02e-190">Не следует использовать файлы ресурсов для хранения паролей, конфиденциальной информации или личных данных.</span><span class="sxs-lookup"><span data-stu-id="ed02e-190">Do not use resource files to store passwords, security-sensitive information, or private data.</span></span>

 <span data-ttu-id="ed02e-191">В следующем примере программным способом создается RESOURCES-файл с именем CarResources.resources, в котором хранятся шесть строк, значок и два объекта, определяемые приложением (два объекта `Automobile`).</span><span class="sxs-lookup"><span data-stu-id="ed02e-191">The following example programmatically creates a .resources file named CarResources.resources that stores six strings, an icon, and two application-defined objects (two `Automobile` objects).</span></span> <span data-ttu-id="ed02e-192">Класс `Automobile`, определенный и созданный в этом примере, отмечен атрибутом <xref:System.SerializableAttribute>, который позволяет ему сохраняться модулем форматирования при двоичной сериализации.</span><span class="sxs-lookup"><span data-stu-id="ed02e-192">The `Automobile` class, which is defined and instantiated in the example, is tagged with the <xref:System.SerializableAttribute> attribute, which allows it to be persisted by the binary serialization formatter.</span></span>

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 <span data-ttu-id="ed02e-193">После создания RESOURCES-файла его можно внедрить в исполняемый файл среды выполнения или библиотеку, используя параметр `/resource` компилятора языка, или во вспомогательную сборку с помощью [компоновщик сборок (Al.exe)](../tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="ed02e-193">After you create the .resources file, you can embed it in a run-time executable or library by including the language compiler's `/resource` switch, or embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span>

<a name="VSResFiles"></a>

## <a name="resource-files-in-visual-studio"></a><span data-ttu-id="ed02e-194">Файлы ресурсов в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ed02e-194">Resource files in Visual Studio</span></span>

<span data-ttu-id="ed02e-195">При добавлении файла ресурсов в проект [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) среда Visual Studio создает RESX-файл в каталоге проекта.</span><span class="sxs-lookup"><span data-stu-id="ed02e-195">When you add a resource file to your [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) project, Visual Studio creates a .resx file in the project directory.</span></span> <span data-ttu-id="ed02e-196">В Visual Studio имеются редакторы ресурсов, позволяющие добавлять строки, изображения и двоичные объекты.</span><span class="sxs-lookup"><span data-stu-id="ed02e-196">Visual Studio provides resource editors that enable you to add strings, images, and binary objects.</span></span> <span data-ttu-id="ed02e-197">Так как редакторы предназначены для обработки только статических данных, их нельзя использовать для хранения программных объектов; данные объектов необходимо записывать в RESX- или RESOURCES-файл программным способом.</span><span class="sxs-lookup"><span data-stu-id="ed02e-197">Because the editors are designed to handle static data only, they cannot be used to store programmatic objects; you must write object data to either a .resx file or to a .resources file programmatically.</span></span> <span data-ttu-id="ed02e-198">Дополнительные сведения см. в статье [Работа с RESX-файлами программным способом](working-with-resx-files-programmatically.md) и разделе [Ресурсы в RESOURCES-файлах](creating-resource-files-for-desktop-apps.md#ResourcesFiles).</span><span class="sxs-lookup"><span data-stu-id="ed02e-198">For more information, see [Working with .resx Files Programmatically](working-with-resx-files-programmatically.md) and the [Resources in .resources Files](creating-resource-files-for-desktop-apps.md#ResourcesFiles) section.</span></span>

<span data-ttu-id="ed02e-199">При добавлении локализованных ресурсов указывайте для них то же имя корневого файла, что и для основного файла ресурсов.</span><span class="sxs-lookup"><span data-stu-id="ed02e-199">If you're adding localized resources, give them the same root file name as the main resource file.</span></span> <span data-ttu-id="ed02e-200">Также в имени файла необходимо указать язык и региональные параметры.</span><span class="sxs-lookup"><span data-stu-id="ed02e-200">You should also designate their culture in the file name.</span></span> <span data-ttu-id="ed02e-201">Например, при добавлении файла ресурсов с именем Resources.resx можно также создать файлы ресурсов с именами Resources.en-US.resx и Resources.fr-FR.resx, чтобы сохранить локализованные ресурсы для английского (США) и французского (Франция) языков и региональных параметров соответственно.</span><span class="sxs-lookup"><span data-stu-id="ed02e-201">For example, if you add a resource file named Resources.resx, you might also create resource files named Resources.en-US.resx and Resources.fr-FR.resx to hold localized resources for the English (United States) and French (France) cultures, respectively.</span></span> <span data-ttu-id="ed02e-202">Следует также указать язык и региональные параметры по умолчанию для приложения.</span><span class="sxs-lookup"><span data-stu-id="ed02e-202">You should also designate your application's default culture.</span></span> <span data-ttu-id="ed02e-203">Это язык и региональные параметры, ресурсы которых используются в том случае, если для конкретного языка и региональных параметров никаких локализованных ресурсов обнаружить не удается.</span><span class="sxs-lookup"><span data-stu-id="ed02e-203">This is the culture whose resources are used if no localized resources for a particular culture can be found.</span></span> <span data-ttu-id="ed02e-204">Чтобы задать язык и региональные параметры по умолчанию, в обозревателе решений Visual Studio щелкните правой кнопкой мыши имя проекта, выберите "Приложение", щелкните **Сведения о сборке** и в списке **Нейтральный язык** выберите соответствующий язык и региональные параметры.</span><span class="sxs-lookup"><span data-stu-id="ed02e-204">To specify the default culture, in Solution Explorer in Visual Studio, right-click the project name, point to Application, click **Assembly Information**, and select the appropriate language/culture in the **Neutral language** list.</span></span>

<span data-ttu-id="ed02e-205">Во время компиляции среда Visual Studio сначала преобразует RESX-файлы проекта в двоичные файлы ресурсов (RESOURCES) и сохраняет их в подкаталоге каталога *obj* проекта.</span><span class="sxs-lookup"><span data-stu-id="ed02e-205">At compile time, Visual Studio first converts the .resx files in a project to binary resource (.resources) files and stores them in a subdirectory of the project's *obj* directory.</span></span> <span data-ttu-id="ed02e-206">Visual Studio внедряет любые файлы ресурсов, не содержащие локализованные ресурсы, в основную сборку, созданную проектом.</span><span class="sxs-lookup"><span data-stu-id="ed02e-206">Visual Studio embeds any resource files that do not contain localized resources in the main assembly that is generated by the project.</span></span> <span data-ttu-id="ed02e-207">Если в каких-либо файлах ресурсов есть локализованные ресурсы, Visual Studio внедряет их в отдельные вспомогательные сборки для каждого локализованного языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="ed02e-207">If any resource files contain localized resources, Visual Studio embeds them in separate satellite assemblies for each localized culture.</span></span> <span data-ttu-id="ed02e-208">Затем Visual Studio сохраняет каждую вспомогательную сборку в каталоге, имя которого соответствует локализованному языку и региональным параметрам.</span><span class="sxs-lookup"><span data-stu-id="ed02e-208">It then stores each satellite assembly in a directory whose name corresponds to the localized culture.</span></span> <span data-ttu-id="ed02e-209">Например, локализованные ресурсы английского языка (США) сохраняются во вспомогательной сборке в подкаталоге en-US.</span><span class="sxs-lookup"><span data-stu-id="ed02e-209">For example, localized English (United States) resources are stored in a satellite assembly in the en-US subdirectory.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed02e-210">См. также</span><span class="sxs-lookup"><span data-stu-id="ed02e-210">See also</span></span>

- <xref:System.Resources>
- [<span data-ttu-id="ed02e-211">Ресурсы в приложениях .NET</span><span class="sxs-lookup"><span data-stu-id="ed02e-211">Resources in .NET Apps</span></span>](index.md)
- [<span data-ttu-id="ed02e-212">Упаковка и развертывание ресурсов</span><span class="sxs-lookup"><span data-stu-id="ed02e-212">Packaging and Deploying Resources</span></span>](packaging-and-deploying-resources-in-desktop-apps.md)
