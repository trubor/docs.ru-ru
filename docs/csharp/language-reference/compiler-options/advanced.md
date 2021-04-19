---
description: Расширенные параметры компилятора C#. Эти параметры используются в сложных сценариях.
title: Параметры компилятора C# — сложные сценарии
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- BaseAddress compiler option [C#]
- ChecksumAlgorithm compiler option [C#]
- CodePage compiler option [C#]
- Utf8Output compiler option [C#]
- MainEntryPoint compiler option [C#]
- GenerateFullPaths compiler option [C#]
- FileAlignment compiler option [C#]
- PathMap compiler option [C#]
- PdbFile compiler option [C#]
- ErrorEndLocation compiler option [C#]
- NoStandardLib compiler option [C#]
- PreferredUILang compiler option [C#]
- SubsystemVersion compiler option [C#]
- AdditionalLibPaths compiler option [C#]
- ApplicationConfiguration compiler option [C#]
- ModuleAssemblyName compiler option [C#]
ms.openlocfilehash: 50108fa18127c55bd791d70520c8dfd90331f86f
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494100"
---
# <a name="advanced-c-compiler-options"></a><span data-ttu-id="efbc8-104">Расширенные параметры компилятора C#</span><span class="sxs-lookup"><span data-stu-id="efbc8-104">Advanced C# compiler options</span></span>

<span data-ttu-id="efbc8-105">Следующие параметры поддерживают сложные сценарии.</span><span class="sxs-lookup"><span data-stu-id="efbc8-105">The following options support advanced scenarios.</span></span> <span data-ttu-id="efbc8-106">Новый синтаксис MSBuild выделен **полужирным шрифтом**.</span><span class="sxs-lookup"><span data-stu-id="efbc8-106">The new MSBuild syntax is shown in **Bold**.</span></span> <span data-ttu-id="efbc8-107">Для старого синтаксиса `csc.exe` используется `code style`.</span><span class="sxs-lookup"><span data-stu-id="efbc8-107">The older `csc.exe` syntax is shown in `code style`.</span></span>

- <span data-ttu-id="efbc8-108">**MainEntryPoint**, **StartupObject** / `-main`: указание типа, который содержит точку входа.</span><span class="sxs-lookup"><span data-stu-id="efbc8-108">**MainEntryPoint**, **StartupObject** / `-main`: Specify the type that contains the entry point.</span></span>
- <span data-ttu-id="efbc8-109">**PdbFile** / `-pdb`: указание имени файла с данными отладки.</span><span class="sxs-lookup"><span data-stu-id="efbc8-109">**PdbFile** / `-pdb`: Specify debug information file name.</span></span>
- <span data-ttu-id="efbc8-110">**PathMap** / `-pathmap`: указание сопоставления для вывода компилятором имен исходных путей.</span><span class="sxs-lookup"><span data-stu-id="efbc8-110">**PathMap** / `-pathmap`: Specify a mapping for source path names output by the compiler.</span></span>
- <span data-ttu-id="efbc8-111">**ApplicationConfiguration** / `-appconfig`: указание файла конфигурации приложения, который содержит параметры привязки сборки.</span><span class="sxs-lookup"><span data-stu-id="efbc8-111">**ApplicationConfiguration** / `-appconfig`: Specify an application configuration file containing assembly binding settings.</span></span>
- <span data-ttu-id="efbc8-112">**AdditionalLibPaths** / `-lib`: указание дополнительных каталогов для поиска ссылок.</span><span class="sxs-lookup"><span data-stu-id="efbc8-112">**AdditionalLibPaths** / `-lib`: Specify additional directories to search in for references.</span></span>
- <span data-ttu-id="efbc8-113">**GenerateFullPaths** / `-fullpath`: компилятор будет создавать абсолютные пути.</span><span class="sxs-lookup"><span data-stu-id="efbc8-113">**GenerateFullPaths** / `-fullpath`: Compiler generates fully qualified paths.</span></span>
- <span data-ttu-id="efbc8-114">**PreferredUILang** / `-preferreduilang`: указание имени предпочтительного языка для вывода данных.</span><span class="sxs-lookup"><span data-stu-id="efbc8-114">**PreferredUILang** / `-preferreduilang`: Specify the preferred output language name.</span></span>
- <span data-ttu-id="efbc8-115">**BaseAddress** / `-baseaddress`: указание базового адреса библиотеки для сборки.</span><span class="sxs-lookup"><span data-stu-id="efbc8-115">**BaseAddress** / `-baseaddress`: Specify the base address for the library to be built.</span></span>
- <span data-ttu-id="efbc8-116">**ChecksumAlgorithm** / `-checksumalgorithm`: указание алгоритма для расчета контрольной суммы файла источника, хранящегося в PDB.</span><span class="sxs-lookup"><span data-stu-id="efbc8-116">**ChecksumAlgorithm** / `-checksumalgorithm` : Specify algorithm for calculating source file checksum stored in PDB.</span></span>
- <span data-ttu-id="efbc8-117">**CodePage** / `-codepage`: указание кодовой страницы, используемой при открытии исходных файлов.</span><span class="sxs-lookup"><span data-stu-id="efbc8-117">**CodePage** / `-codepage`: Specify the codepage to use when opening source files.</span></span>
- <span data-ttu-id="efbc8-118">**Utf8Output** / `-utf8output`: сообщения компилятора будут выводиться в кодировке UTF-8.</span><span class="sxs-lookup"><span data-stu-id="efbc8-118">**Utf8Output** / `-utf8output`: Output compiler messages in UTF-8 encoding.</span></span>
- <span data-ttu-id="efbc8-119">**FileAlignment** / `-filealign`: указание выравнивания для разделов выходного файла.</span><span class="sxs-lookup"><span data-stu-id="efbc8-119">**FileAlignment** / `-filealign`: Specify the alignment used for output file sections.</span></span>
- <span data-ttu-id="efbc8-120">**ErrorEndLocation** / `-errorendlocation`: выходные строка и столбец конечного расположения каждой ошибки.</span><span class="sxs-lookup"><span data-stu-id="efbc8-120">**ErrorEndLocation** / `-errorendlocation`: Output line and column of the end location of each error.</span></span>
- <span data-ttu-id="efbc8-121">**NoStandardLib** / `-nostdlib`: не указывать ссылку на стандартную библиотеку *mscorlib.dll*.</span><span class="sxs-lookup"><span data-stu-id="efbc8-121">**NoStandardLib** / `-nostdlib`: Don't reference standard library *mscorlib.dll*.</span></span>
- <span data-ttu-id="efbc8-122">**SubsystemVersion** / `-subsystemversion`: указание версии подсистемы для этой сборки.</span><span class="sxs-lookup"><span data-stu-id="efbc8-122">**SubsystemVersion** / `-subsystemversion`: Specify subsystem version of this assembly.</span></span>
- <span data-ttu-id="efbc8-123">**ModuleAssemblyName** / `-moduleassemblyname`: имя сборки, частью которой будет этот модуль.</span><span class="sxs-lookup"><span data-stu-id="efbc8-123">**ModuleAssemblyName** / `-moduleassemblyname`: Name of the assembly that this module will be a part of.</span></span>

## <a name="mainentrypoint-or-startupobject"></a><span data-ttu-id="efbc8-124">MainEntryPoint или StartupObject</span><span class="sxs-lookup"><span data-stu-id="efbc8-124">MainEntryPoint or StartupObject</span></span>

<span data-ttu-id="efbc8-125">Этот параметр определяет класс, который содержит точку входа в программу, если метод `Main` содержит сразу несколько классов.</span><span class="sxs-lookup"><span data-stu-id="efbc8-125">This option specifies the class that contains the entry point to the program, if more than one class contains a `Main` method.</span></span>

```xml
<StartupObject>MyNamespace.Program</StartupObject>
```

<span data-ttu-id="efbc8-126">или</span><span class="sxs-lookup"><span data-stu-id="efbc8-126">or</span></span>

```xml
<MainEntryPoint>MyNamespace.Program</MainEntryPoint>
```

<span data-ttu-id="efbc8-127">Где `Program` — это тип, содержащий метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="efbc8-127">Where `Program` is the type that contains the `Main` method.</span></span> <span data-ttu-id="efbc8-128">Указанное имя класса должно быть полным; оно должно включать полное пространство имен, содержащее ключевое слово class, за которым следует имя класса.</span><span class="sxs-lookup"><span data-stu-id="efbc8-128">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="efbc8-129">Например, если метод `Main` находится в классе `Program` в пространстве имен `MyApplication.Core`, необходимо указать параметр компилятора `-main:MyApplication.Core.Program`.</span><span class="sxs-lookup"><span data-stu-id="efbc8-129">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span> <span data-ttu-id="efbc8-130">Если ваша компиляция включает более одного типа с методом [`Main`](../../programming-guide/main-and-command-args/index.md), вы можете указать, какой тип содержит метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="efbc8-130">If your compilation includes more than one type with a [`Main`](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the `Main` method.</span></span>

> [!NOTE]
> <span data-ttu-id="efbc8-131">Этот параметр нельзя использовать для проекта, который включает [инструкции верхнего уровня](../../programming-guide/main-and-command-args/top-level-statements.md), даже если этот проект содержит один или несколько методов `Main`.</span><span class="sxs-lookup"><span data-stu-id="efbc8-131">This option can't be used for a project that includes [top-level statements](../../programming-guide/main-and-command-args/top-level-statements.md), even if that project contains one or more `Main` methods.</span></span>

## <a name="pdbfile"></a><span data-ttu-id="efbc8-132">PdbFile</span><span class="sxs-lookup"><span data-stu-id="efbc8-132">PdbFile</span></span>

<span data-ttu-id="efbc8-133">Параметр компилятора **PdbFile** задает имя и расположение файла отладочных символов.</span><span class="sxs-lookup"><span data-stu-id="efbc8-133">The **PdbFile** compiler option specifies the name and location of the debug symbols file.</span></span>  <span data-ttu-id="efbc8-134">Значение `filename` указывает на имя и расположение файла отладочных символов.</span><span class="sxs-lookup"><span data-stu-id="efbc8-134">The `filename` value specifies the name and location of the debug symbols file.</span></span>  

```xml
<PdbFile>filename</PdbFile>
```

<span data-ttu-id="efbc8-135">Если указан [**DebugType**](code-generation.md#debugtype), компилятор создаст *PDB*-файл в том же каталоге, в котором он создаст выходной файл (EXE или DLL).</span><span class="sxs-lookup"><span data-stu-id="efbc8-135">When you specify [**DebugType**](code-generation.md#debugtype), the compiler will create a *.pdb* file in the same directory where the compiler will create the output file (.exe or .dll).</span></span> <span data-ttu-id="efbc8-136">*PDB*-файл имеет такое же базовое имя файла, что и выходной файл.</span><span class="sxs-lookup"><span data-stu-id="efbc8-136">The *.pdb* file has the same base file name as the name of the output file.</span></span> <span data-ttu-id="efbc8-137">С помощью параметра **PdbFile** можно задать имя и расположение PDB-файла, отличающееся от используемых по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="efbc8-137">**PdbFile** allows you to specify a non-default file name and location for the .pdb file.</span></span> <span data-ttu-id="efbc8-138">Этот параметр компилятора нельзя задать в среде разработки Visual Studio или изменить программными средствами.</span><span class="sxs-lookup"><span data-stu-id="efbc8-138">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  

## <a name="pathmap"></a><span data-ttu-id="efbc8-139">PathMap</span><span class="sxs-lookup"><span data-stu-id="efbc8-139">PathMap</span></span>

<span data-ttu-id="efbc8-140">Параметр компилятора **PathMap** определяет способ сопоставления компилятором физических путей и выходных имен исходных путей.</span><span class="sxs-lookup"><span data-stu-id="efbc8-140">The **PathMap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span> <span data-ttu-id="efbc8-141">Этот параметр сопоставляет каждый физический путь на компьютере, где выполняется компилятор, с соответствующим путем, который должен быть записан в выходные файлы.</span><span class="sxs-lookup"><span data-stu-id="efbc8-141">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span> <span data-ttu-id="efbc8-142">В следующем примере `path1` — это полный путь к исходным файлам в текущей среде, а `sourcePath1` — исходный путь, подставляемый вместо `path1` во всех выходных файлах.</span><span class="sxs-lookup"><span data-stu-id="efbc8-142">In the following example, `path1` is the full path to the source files in the current environment, and `sourcePath1` is the source path substituted for `path1` in any output files.</span></span> <span data-ttu-id="efbc8-143">Чтобы указать несколько сопоставленных исходных путей, разделите их точкой с запятой.</span><span class="sxs-lookup"><span data-stu-id="efbc8-143">To specify multiple mapped source paths, separate each with a semicolon.</span></span>

```xml
<PathMap>path1=sourcePath1;path2=sourcePath2</PathMap>
```

<span data-ttu-id="efbc8-144">Компилятор записывает исходный путь в выходные данные по следующим причинам:</span><span class="sxs-lookup"><span data-stu-id="efbc8-144">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="efbc8-145">Исходный путь подставляется вместо аргумента, когда <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> применяется как необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="efbc8-145">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="efbc8-146">Исходный путь внедряется как PDB-файл.</span><span class="sxs-lookup"><span data-stu-id="efbc8-146">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="efbc8-147">Путь к PDB-файлу внедряется в PE-файл (переносимый исполняемый файл).</span><span class="sxs-lookup"><span data-stu-id="efbc8-147">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

## <a name="applicationconfiguration"></a><span data-ttu-id="efbc8-148">ApplicationConfiguration</span><span class="sxs-lookup"><span data-stu-id="efbc8-148">ApplicationConfiguration</span></span>

<span data-ttu-id="efbc8-149">Параметр компилятора **ApplicationConfiguration** позволяет приложению C# задать расположение файла конфигурации приложения сборки (app.config) в среде CLR во время привязки сборки.</span><span class="sxs-lookup"><span data-stu-id="efbc8-149">The **ApplicationConfiguration** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>

```xml
<ApplicationConfiguration>file</ApplicationConfiguration>
```

<span data-ttu-id="efbc8-150">Где `file` — это файл конфигурации приложения, содержащий параметры привязки сборки.</span><span class="sxs-lookup"><span data-stu-id="efbc8-150">Where `file` is the application configuration file that contains assembly binding settings.</span></span> <span data-ttu-id="efbc8-151">Один из случаев использования параметра **ApplicationConfiguration** — сложные сценарии, когда в сборке одновременно используются ссылки на версию .NET Framework и на версию .NET Framework для Silverlight определенной базовой сборки.</span><span class="sxs-lookup"><span data-stu-id="efbc8-151">One use of **ApplicationConfiguration** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="efbc8-152">Например, для конструктора XAML, написанного в Windows Presentation Foundation (WPF), может потребоваться ссылаться на оба рабочих стола WPF, для пользовательского интерфейса конструктора и для подмножества WPF, поставляемого с Silverlight.</span><span class="sxs-lookup"><span data-stu-id="efbc8-152">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="efbc8-153">Одна и та же сборка конструктора имеет доступ к обеим сборкам.</span><span class="sxs-lookup"><span data-stu-id="efbc8-153">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="efbc8-154">По умолчанию отдельные ссылки вызывают ошибку компиляции, так как привязка сборки видит две эквивалентные сборки.</span><span class="sxs-lookup"><span data-stu-id="efbc8-154">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="efbc8-155">Параметр компилятора **ApplicationConfiguration** позволяет указать расположение файла app.config, который отключает поведение по умолчанию с помощью тега `<supportPortability>`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="efbc8-155">The **ApplicationConfiguration** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>

```xml
<supportPortability PKT="7cec85d7bea7798e" enable="false"/>
```

<span data-ttu-id="efbc8-156">Компилятор передает расположение файла в логику с привязкой сборки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="efbc8-156">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>

> [!NOTE]
> <span data-ttu-id="efbc8-157">Чтобы использовать файл app.config, уже заданный в проекте, добавьте тег свойства `<UseAppConfigForCompiler>` в *CSPROJ*-файл и задайте для него значение `true`.</span><span class="sxs-lookup"><span data-stu-id="efbc8-157">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the *.csproj* file and set its value to `true`.</span></span> <span data-ttu-id="efbc8-158">Чтобы указать другой файл app.config, добавьте тег свойства `<AppConfigForCompiler>` и задайте в качестве его значения расположение требуемого файла.</span><span class="sxs-lookup"><span data-stu-id="efbc8-158">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>

<span data-ttu-id="efbc8-159">В следующем примере показан файл app.config, позволяющий приложению иметь ссылки на реализации .NET Framework и .NET Framework для реализации Silverlight любой сборки .NET Framework, существующей в обеих реализациях.</span><span class="sxs-lookup"><span data-stu-id="efbc8-159">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="efbc8-160">Параметр компилятора **ApplicationConfiguration** позволяет указать расположение этого файла app.config.</span><span class="sxs-lookup"><span data-stu-id="efbc8-160">The **ApplicationConfiguration** compiler option specifies the location of this app.config file.</span></span>

```xml
<configuration>
  <runtime>
    <assemblyBinding>
      <supportPortability PKT="7cec85d7bea7798e" enable="false"/>
      <supportPortability PKT="31bf3856ad364e35" enable="false"/>
    </assemblyBinding>
  </runtime>
</configuration>
```

## <a name="additionallibpaths"></a><span data-ttu-id="efbc8-161">AdditionalLibPaths</span><span class="sxs-lookup"><span data-stu-id="efbc8-161">AdditionalLibPaths</span></span>

<span data-ttu-id="efbc8-162">Параметр **AdditionalLibPaths** позволяет задать расположение сборок, указанных с помощью параметра [**References**](inputs.md#references).</span><span class="sxs-lookup"><span data-stu-id="efbc8-162">The **AdditionalLibPaths** option specifies the location of assemblies referenced with the [**References**](inputs.md#references) option.</span></span>

```xml
<AdditionalLibPaths>dir1[,dir2]</AdditionalLibPaths>
```

<span data-ttu-id="efbc8-163">Где `dir1` — это каталог, в котором компилятор должен искать базовую сборку, если она отсутствует в текущем рабочем каталоге (из которого был вызван компилятор) и системном каталоге среды CLR.</span><span class="sxs-lookup"><span data-stu-id="efbc8-163">Where `dir1` is a directory for the compiler to look in if a referenced assembly isn't found in the current working directory (the directory from which you're invoking the compiler) or in the common language runtime's system directory.</span></span> <span data-ttu-id="efbc8-164">`dir2` — это один или несколько дополнительных каталогов для поиска связанных сборок.</span><span class="sxs-lookup"><span data-stu-id="efbc8-164">`dir2` is one or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="efbc8-165">Имена каталогов разделяются запятыми без пробелов.</span><span class="sxs-lookup"><span data-stu-id="efbc8-165">Separate directory names with a comma, and without white space between them.</span></span> <span data-ttu-id="efbc8-166">Компилятор выполняет поиск ссылок на сборки, для которых не указано полное имя, в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="efbc8-166">The compiler searches for assembly references that aren't fully qualified in the following order:</span></span>  

1. <span data-ttu-id="efbc8-167">Текущая рабочая папка.</span><span class="sxs-lookup"><span data-stu-id="efbc8-167">Current working directory.</span></span>
1. <span data-ttu-id="efbc8-168">Системный каталог среды CLR.</span><span class="sxs-lookup"><span data-stu-id="efbc8-168">The common language runtime system directory.</span></span>
1. <span data-ttu-id="efbc8-169">Каталоги, указанные с помощью параметра **AdditionalLibPaths**.</span><span class="sxs-lookup"><span data-stu-id="efbc8-169">Directories specified by **AdditionalLibPaths**.</span></span>
1. <span data-ttu-id="efbc8-170">Каталоги, указанные переменной среды LIB.</span><span class="sxs-lookup"><span data-stu-id="efbc8-170">Directories specified by the LIB environment variable.</span></span>

<span data-ttu-id="efbc8-171">Для указания ссылки на сборку используется параметр **Reference**.</span><span class="sxs-lookup"><span data-stu-id="efbc8-171">Use **Reference** to specify an assembly reference.</span></span> <span data-ttu-id="efbc8-172">**AdditionalLibPaths** является аддитивным,</span><span class="sxs-lookup"><span data-stu-id="efbc8-172">**AdditionalLibPaths** is additive.</span></span> <span data-ttu-id="efbc8-173">то есть каждое следующее указание этого параметра присоединяется к предыдущим значениям.</span><span class="sxs-lookup"><span data-stu-id="efbc8-173">Specifying it more than once appends to any prior values.</span></span> <span data-ttu-id="efbc8-174">Так как путь к зависимой сборке не указывается в манифесте сборки, приложение найдет используемую сборку в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="efbc8-174">Since the path to the dependent assembly isn't specified in the assembly manifest, the application will find and use the assembly in the global assembly cache.</span></span> <span data-ttu-id="efbc8-175">Компилятор, ссылающийся на сборку, не подразумевает, что среда CLR может найти и загрузить сборку во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="efbc8-175">The compiler referencing the assembly doesn't imply the common language runtime can find and load the assembly at runtime.</span></span> <span data-ttu-id="efbc8-176">Сведения о том, как среда выполнения выполняет поиск связанных сборок, см. в разделе [Обнаружение сборок в среде выполнения](../../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="efbc8-176">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  

## <a name="generatefullpaths"></a><span data-ttu-id="efbc8-177">GenerateFullPaths</span><span class="sxs-lookup"><span data-stu-id="efbc8-177">GenerateFullPaths</span></span>

<span data-ttu-id="efbc8-178">Параметр **GenerateFullPaths** указывает компилятору на необходимость задавать полный путь к файлу при выводе списка ошибок и предупреждений компиляции.</span><span class="sxs-lookup"><span data-stu-id="efbc8-178">The **GenerateFullPaths** option causes the compiler to specify the full path to the file when listing compilation errors and warnings.</span></span>
  
```Xml
<GenerateFullPaths>true</GenerateFullPaths>
```

<span data-ttu-id="efbc8-179">По умолчанию для ошибок и предупреждений, возникающих в ходе компиляции, указывается имя файла, в котором они были обнаружены.</span><span class="sxs-lookup"><span data-stu-id="efbc8-179">By default, errors and warnings that result from compilation specify the name of the file in which an error was found.</span></span> <span data-ttu-id="efbc8-180">Параметр **GenerateFullPaths** указывает компилятору на необходимость задать полный путь к файлу.</span><span class="sxs-lookup"><span data-stu-id="efbc8-180">The **GenerateFullPaths** option causes the compiler to specify the full path to the file.</span></span> <span data-ttu-id="efbc8-181">Этот параметр компилятора недоступен в Visual Studio и не может быть изменен программным способом.</span><span class="sxs-lookup"><span data-stu-id="efbc8-181">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>

## <a name="preferreduilang"></a><span data-ttu-id="efbc8-182">PreferredUILang</span><span class="sxs-lookup"><span data-stu-id="efbc8-182">PreferredUILang</span></span>

<span data-ttu-id="efbc8-183">С помощью параметра компилятора **PreferredUILang** можно указать язык, на котором компилятор C# отображает выходные данные, например сообщения об ошибках.</span><span class="sxs-lookup"><span data-stu-id="efbc8-183">By using the **PreferredUILang** compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>

```xml
<PreferredUILang>language</PreferredUILang>
```

<span data-ttu-id="efbc8-184">Где `language` — это [название языка](/windows/desktop/Intl/language-names), который будет использоваться для вывода компилятора.</span><span class="sxs-lookup"><span data-stu-id="efbc8-184">Where `language` is the [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span> <span data-ttu-id="efbc8-185">Параметр компилятора **PreferredUILang** можно использовать, чтобы указать язык, который компилятор C# должен использовать для сообщений об ошибках и других данных вывода командной строки.</span><span class="sxs-lookup"><span data-stu-id="efbc8-185">You can use the **PreferredUILang** compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="efbc8-186">Если необходимый языковой пакет не установлен, вместо него используются языковые настройки операционной системы.</span><span class="sxs-lookup"><span data-stu-id="efbc8-186">If the language pack for the language isn't installed, the language setting of the operating system is used instead.</span></span>

## <a name="baseaddress"></a><span data-ttu-id="efbc8-187">BaseAddress</span><span class="sxs-lookup"><span data-stu-id="efbc8-187">BaseAddress</span></span>

<span data-ttu-id="efbc8-188">Параметр **BaseAddress** позволяет указать предпочтительный базовый адрес для загрузки библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="efbc8-188">The **BaseAddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="efbc8-189">Дополнительные сведения о случаях использования этого параметра см. в [блоге Ларри Остермана (Larry Osterman)](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span><span class="sxs-lookup"><span data-stu-id="efbc8-189">For more information about when and why to use this option, see [Larry Osterman's WebLog](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span></span>

```xml
<BaseAddress>address</BaseAddress>
```

<span data-ttu-id="efbc8-190">Где `address` — это базовый адрес для библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="efbc8-190">Where `address` is the base address for the DLL.</span></span> <span data-ttu-id="efbc8-191">Этот адрес можно задать в десятичном, шестнадцатеричном или восьмеричном формате.</span><span class="sxs-lookup"><span data-stu-id="efbc8-191">This address can be specified as a decimal, hexadecimal, or octal number.</span></span> <span data-ttu-id="efbc8-192">Базовый адрес по умолчанию для библиотеки DLL задается в среде выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="efbc8-192">The default base address for a DLL is set by the .NET common language runtime.</span></span> <span data-ttu-id="efbc8-193">Младшее слово этого адреса будет округляться,</span><span class="sxs-lookup"><span data-stu-id="efbc8-193">The lower-order word in this address will be rounded.</span></span> <span data-ttu-id="efbc8-194">например значение `0x11110001` округляется до `0x11110000`.</span><span class="sxs-lookup"><span data-stu-id="efbc8-194">For example, if you specify `0x11110001`, it will be rounded to `0x11110000`.</span></span> <span data-ttu-id="efbc8-195">Чтобы завершить процесс подписи для библиотеки DLL, используйте файл SN. EXE с параметром -R.</span><span class="sxs-lookup"><span data-stu-id="efbc8-195">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>

## <a name="checksumalgorithm"></a><span data-ttu-id="efbc8-196">ChecksumAlgorithm</span><span class="sxs-lookup"><span data-stu-id="efbc8-196">ChecksumAlgorithm</span></span>

<span data-ttu-id="efbc8-197">Этот параметр управляет алгоритмом контрольной суммы, который используется для кодирования исходных файлов в формат PDB.</span><span class="sxs-lookup"><span data-stu-id="efbc8-197">This option controls the checksum algorithm we use to encode source files in the PDB.</span></span>

```xml
<ChecksumAlgorithm>algorithm</ChecksumAlgorithm>
```

<span data-ttu-id="efbc8-198">Параметр `algorithm` должен иметь значение `SHA1` (по умолчанию) или `SHA256`.</span><span class="sxs-lookup"><span data-stu-id="efbc8-198">The `algorithm` must be either `SHA1` (default) or `SHA256`.</span></span>

## <a name="codepage"></a><span data-ttu-id="efbc8-199">CodePage</span><span class="sxs-lookup"><span data-stu-id="efbc8-199">CodePage</span></span>

<span data-ttu-id="efbc8-200">Этот параметр позволяет указать кодовую страницу, используемую во время компиляции, если требуемая страница не является текущей кодовой страницей системы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="efbc8-200">This option specifies which codepage to use during compilation if the required page isn't the current default codepage for the system.</span></span>
  
```xml
<CodePage>id</CodePage>
```

<span data-ttu-id="efbc8-201">Где `id` — это идентификатор кодовой страницы, используемой для всех файлов исходного кода при компиляции.</span><span class="sxs-lookup"><span data-stu-id="efbc8-201">Where `id` is the id of the code page to use for all source code files in the compilation.</span></span> <span data-ttu-id="efbc8-202">Во-первых, компилятор будет пытаться интерпретировать все исходные файлы в кодировке UTF-8.</span><span class="sxs-lookup"><span data-stu-id="efbc8-202">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="efbc8-203">Если кодировка файлов исходного кода отличается от UTF-8 и использует символы, отличные от 7-разрядных символов ASCII, используйте параметр **CodePage**, чтобы указать нужную кодовую страницу.</span><span class="sxs-lookup"><span data-stu-id="efbc8-203">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **CodePage** option to specify which code page should be used.</span></span> <span data-ttu-id="efbc8-204">Параметр **CodePage** применяется ко всем файлам исходного кода, включенным в компиляцию.</span><span class="sxs-lookup"><span data-stu-id="efbc8-204">**CodePage** applies to all source code files in your compilation.</span></span> <span data-ttu-id="efbc8-205">Сведения о том, как найти кодовые страницы, которые поддерживаются в системе, см. на странице, посвященной функции [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo).</span><span class="sxs-lookup"><span data-stu-id="efbc8-205">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>

## <a name="utf8output"></a><span data-ttu-id="efbc8-206">Utf8Output</span><span class="sxs-lookup"><span data-stu-id="efbc8-206">Utf8Output</span></span>

<span data-ttu-id="efbc8-207">Параметр **Utf8Output** отображает выходные данные компилятора в кодировке UTF-8.</span><span class="sxs-lookup"><span data-stu-id="efbc8-207">The **Utf8Output** option displays compiler output using UTF-8 encoding.</span></span>

```xml
<Utf8Output>true</Utf8Output>
```

<span data-ttu-id="efbc8-208">В некоторых конфигурациях для различных языков выходные данные компилятора некорректно отображаются в консоли.</span><span class="sxs-lookup"><span data-stu-id="efbc8-208">In some international configurations, compiler output cannot correctly be displayed in the console.</span></span> <span data-ttu-id="efbc8-209">Используйте **Utf8Output** и перенаправьте выходные данные компилятора в файл.</span><span class="sxs-lookup"><span data-stu-id="efbc8-209">Use **Utf8Output** and redirect compiler output to a file.</span></span>

## <a name="filealignment"></a><span data-ttu-id="efbc8-210">FileAlignment</span><span class="sxs-lookup"><span data-stu-id="efbc8-210">FileAlignment</span></span>

<span data-ttu-id="efbc8-211">Параметр **FileAlignment** позволяет указать размер разделов в выходном файле.</span><span class="sxs-lookup"><span data-stu-id="efbc8-211">The **FileAlignment** option lets you specify the size of sections in your output file.</span></span> <span data-ttu-id="efbc8-212">Допустимые значения: 512, 1024, 2048, 4096 и 8192.</span><span class="sxs-lookup"><span data-stu-id="efbc8-212">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="efbc8-213">Эти значения указаны в байтах.</span><span class="sxs-lookup"><span data-stu-id="efbc8-213">These values are in bytes.</span></span>

```xml
<FileAlignment>number</FileAlignment>
```

<span data-ttu-id="efbc8-214">Параметр **FileAlignment** задается на странице **Дополнительно** в свойствах **сборки** проекта в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="efbc8-214">You set the **FileAlignment** option from the **Advanced** page of the **Build** properties for your project in Visual Studio.</span></span> <span data-ttu-id="efbc8-215">Каждый раздел выравнивается по границе, кратной значению **FileAlignment**.</span><span class="sxs-lookup"><span data-stu-id="efbc8-215">Each section will be aligned on a boundary that is a multiple of the **FileAlignment** value.</span></span> <span data-ttu-id="efbc8-216">Фиксированный размер по умолчанию не предусмотрен.</span><span class="sxs-lookup"><span data-stu-id="efbc8-216">There's no fixed default.</span></span> <span data-ttu-id="efbc8-217">Если значение **FileAlignment** не указано, среда CLR выбирает значение по умолчанию во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="efbc8-217">If **FileAlignment** isn't specified, the common language runtime picks a default at compile time.</span></span> <span data-ttu-id="efbc8-218">Указанный размер раздела влияет на размер выходного файла.</span><span class="sxs-lookup"><span data-stu-id="efbc8-218">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="efbc8-219">Изменение размера раздела может применяться для программ, выполняющихся на небольших устройствах.</span><span class="sxs-lookup"><span data-stu-id="efbc8-219">Modifying section size may be useful for programs that will run on smaller devices.</span></span> <span data-ttu-id="efbc8-220">Используйте [DUMPBIN](/cpp/build/reference/dumpbin-options) для просмотра информации о разделах выходного файла.</span><span class="sxs-lookup"><span data-stu-id="efbc8-220">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>

## <a name="errorendlocation"></a><span data-ttu-id="efbc8-221">ErrorEndLocation</span><span class="sxs-lookup"><span data-stu-id="efbc8-221">ErrorEndLocation</span></span>

<span data-ttu-id="efbc8-222">Указывает компилятору выводить строку и столбец конечного расположения каждой ошибки.</span><span class="sxs-lookup"><span data-stu-id="efbc8-222">Instructs the compiler to output line and column of the end location of each error.</span></span>

```xml
<ErrorEndLocation>filename</ErrorEndLocation>
```

<span data-ttu-id="efbc8-223">По умолчанию компилятор записывает начальное расположение в исходном коде для всех ошибок и предупреждений.</span><span class="sxs-lookup"><span data-stu-id="efbc8-223">By default, the compiler writes the starting location in source for all errors and warnings.</span></span> <span data-ttu-id="efbc8-224">Если этот параметр имеет значение True, компилятор записывает как начальное, так и конечное расположения для каждой ошибки и предупреждения.</span><span class="sxs-lookup"><span data-stu-id="efbc8-224">When this option is set to true, the compiler writes both the starting and end location for each error and warning.</span></span>

## <a name="nostandardlib"></a><span data-ttu-id="efbc8-225">NoStandardLib</span><span class="sxs-lookup"><span data-stu-id="efbc8-225">NoStandardLib</span></span>

<span data-ttu-id="efbc8-226">Параметр **NoStandardLib** запрещает импорт библиотеки mscorlib.dll, которая определяет все пространство имен System.</span><span class="sxs-lookup"><span data-stu-id="efbc8-226">**NoStandardLib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

```xml
<NoStandardLib>true</NoStandardLib>
```

<span data-ttu-id="efbc8-227">Используйте этот параметр, если вы хотите определить или создать собственное пространство имен System и объекты.</span><span class="sxs-lookup"><span data-stu-id="efbc8-227">Use this option if you want to define or create your own System namespace and objects.</span></span> <span data-ttu-id="efbc8-228">Если вы не укажете параметр **NoStandardLib**, библиотека mscorlib.dll будет импортирована в вашу программу (как и при указании `<NoStandardLib>false</NoStandardLib>`).</span><span class="sxs-lookup"><span data-stu-id="efbc8-228">If you don't specify **NoStandardLib**, mscorlib.dll is imported into your program (same as specifying `<NoStandardLib>false</NoStandardLib>`).</span></span>

## <a name="subsystemversion"></a><span data-ttu-id="efbc8-229">SubsystemVersion</span><span class="sxs-lookup"><span data-stu-id="efbc8-229">SubsystemVersion</span></span>

<span data-ttu-id="efbc8-230">Задает минимальную версию подсистемы, в которой может выполняться исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="efbc8-230">Specifies the minimum version of the subsystem on which the executable file runs.</span></span> <span data-ttu-id="efbc8-231">Чаще всего этот параметр предоставляет исполняемому файлу возможность использовать функции безопасности, недоступные в прежних версиях Windows.</span><span class="sxs-lookup"><span data-stu-id="efbc8-231">Most commonly, this option ensures that the executable file can use security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="efbc8-232">Чтобы указать саму подсистему, используйте параметр компилятора [**TargetType**](./output.md#targettype).</span><span class="sxs-lookup"><span data-stu-id="efbc8-232">To specify the subsystem itself, use the [**TargetType**](./output.md#targettype) compiler option.</span></span>

```xml
<SubsystemVersion>major.minor</SubsystemVersion>
```

<span data-ttu-id="efbc8-233">`major.minor` задает минимальную требуемую версию подсистемы (через точку записываются основная и дополнительная версии).</span><span class="sxs-lookup"><span data-stu-id="efbc8-233">The `major.minor` specify the minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="efbc8-234">Например, можно указать, что приложение не может работать в операционной системе старше Windows 7.</span><span class="sxs-lookup"><span data-stu-id="efbc8-234">For example, you can specify that an application can't run on an operating system that's older than Windows 7.</span></span> <span data-ttu-id="efbc8-235">Установите для этого параметра значение 6.01, как описано в таблице ниже в этой статье.</span><span class="sxs-lookup"><span data-stu-id="efbc8-235">Set the value of this option to 6.01, as the table later in this article describes.</span></span> <span data-ttu-id="efbc8-236">Укажите значения для параметров `major` и `minor` в виде целых чисел.</span><span class="sxs-lookup"><span data-stu-id="efbc8-236">You specify the values for `major` and `minor` as integers.</span></span> <span data-ttu-id="efbc8-237">Нули в начале версии `minor` не изменяют версию, нули в конце — изменяют.</span><span class="sxs-lookup"><span data-stu-id="efbc8-237">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="efbc8-238">Например, 6.1 и 6.01 — одна версия, а 6.10 — другая.</span><span class="sxs-lookup"><span data-stu-id="efbc8-238">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="efbc8-239">Рекомендуется указывать дополнительный номер версии двумя цифрами, чтобы избежать путаницы.</span><span class="sxs-lookup"><span data-stu-id="efbc8-239">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

<span data-ttu-id="efbc8-240">В следующей таблице перечислены распространенные версии подсистем Windows.</span><span class="sxs-lookup"><span data-stu-id="efbc8-240">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="efbc8-241">Версия Windows</span><span class="sxs-lookup"><span data-stu-id="efbc8-241">Windows version</span></span>|<span data-ttu-id="efbc8-242">Версия подсистемы</span><span class="sxs-lookup"><span data-stu-id="efbc8-242">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="efbc8-243">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="efbc8-243">Windows Server 2003</span></span>|<span data-ttu-id="efbc8-244">5.02</span><span class="sxs-lookup"><span data-stu-id="efbc8-244">5.02</span></span>|
|<span data-ttu-id="efbc8-245">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="efbc8-245">Windows Vista</span></span>|<span data-ttu-id="efbc8-246">6.00</span><span class="sxs-lookup"><span data-stu-id="efbc8-246">6.00</span></span>|
|<span data-ttu-id="efbc8-247">Windows 7</span><span class="sxs-lookup"><span data-stu-id="efbc8-247">Windows 7</span></span>|<span data-ttu-id="efbc8-248">6.01</span><span class="sxs-lookup"><span data-stu-id="efbc8-248">6.01</span></span>|
|<span data-ttu-id="efbc8-249">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="efbc8-249">Windows Server 2008</span></span>|<span data-ttu-id="efbc8-250">6.01</span><span class="sxs-lookup"><span data-stu-id="efbc8-250">6.01</span></span>|
|<span data-ttu-id="efbc8-251">Windows 8</span><span class="sxs-lookup"><span data-stu-id="efbc8-251">Windows 8</span></span>|<span data-ttu-id="efbc8-252">6.02</span><span class="sxs-lookup"><span data-stu-id="efbc8-252">6.02</span></span>|

<span data-ttu-id="efbc8-253">Значение по умолчанию параметра компилятора **SubsystemVersion** зависит от условий в следующем списке:</span><span class="sxs-lookup"><span data-stu-id="efbc8-253">The default value of the **SubsystemVersion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="efbc8-254">Значение по умолчанию — 6.02, если задан любой параметр компилятора из следующего списка.</span><span class="sxs-lookup"><span data-stu-id="efbc8-254">The default value is 6.02 if any compiler option in the following list is set:</span></span>
  - [<span data-ttu-id="efbc8-255">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="efbc8-255">-target:appcontainerexe</span></span>](output.md)
  - [<span data-ttu-id="efbc8-256">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="efbc8-256">-target:winmdobj</span></span>](output.md)
  - [<span data-ttu-id="efbc8-257">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="efbc8-257">-platform:arm</span></span>](output.md)
- <span data-ttu-id="efbc8-258">Значение по умолчанию — 6.00, если используется средство MSBuild, приложение предназначено для .NET Framework 4.5 и не установлены параметры компилятора, определенные ранее в этом списке.</span><span class="sxs-lookup"><span data-stu-id="efbc8-258">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>
- <span data-ttu-id="efbc8-259">Если ни одно из предыдущих условий не верно, значение по умолчанию — 4.00.</span><span class="sxs-lookup"><span data-stu-id="efbc8-259">The default value is 4.00 if none of the previous conditions are true.</span></span>

## <a name="moduleassemblyname"></a><span data-ttu-id="efbc8-260">ModuleAssemblyName</span><span class="sxs-lookup"><span data-stu-id="efbc8-260">ModuleAssemblyName</span></span>

<span data-ttu-id="efbc8-261">Указывает имя сборки, к отдельным типам которой может обращаться *.netmodule*.</span><span class="sxs-lookup"><span data-stu-id="efbc8-261">Specifies the name of an assembly whose non-public types a *.netmodule* can access.</span></span>

```xml
<ModuleAssemblyName>assembly_name</ModuleAssemblyName>
```

<span data-ttu-id="efbc8-262">Параметр **ModuleAssemblyName** нужно использовать при сборке *.netmodule* и выполнении следующих условий:</span><span class="sxs-lookup"><span data-stu-id="efbc8-262">**ModuleAssemblyName** should be used when building a *.netmodule*, and where the following conditions are true:</span></span>

- <span data-ttu-id="efbc8-263">Для *.netmodule* требуется доступ к неоткрытым типам в существующей сборке.</span><span class="sxs-lookup"><span data-stu-id="efbc8-263">The *.netmodule* needs access to non-public types in an existing assembly.</span></span>
- <span data-ttu-id="efbc8-264">Известно имя сборки, в которой будет создан .netmodule.</span><span class="sxs-lookup"><span data-stu-id="efbc8-264">You know the name of the assembly into which the .netmodule will be built.</span></span>
- <span data-ttu-id="efbc8-265">Существующая сборка предоставила дружественной сборке доступ к сборке, в которую будет встроен *.netmodule*.</span><span class="sxs-lookup"><span data-stu-id="efbc8-265">The existing assembly has granted friend assembly access to the assembly into which the .*netmodule* will be built.</span></span>

<span data-ttu-id="efbc8-266">Дополнительные сведения о сборке .netmodule см. в разделе о параметре [**TargetType**](output.md#targettype) и его значении **module**.</span><span class="sxs-lookup"><span data-stu-id="efbc8-266">For more information on building a .netmodule, see [**TargetType**](output.md#targettype) option of **module**.</span></span> <span data-ttu-id="efbc8-267">Дополнительные сведения см. в разделе [Дружественные сборки](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="efbc8-267">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>
