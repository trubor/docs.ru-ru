---
description: -doc (параметры компилятора C#)
title: -doc (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: e55b86e5b028fb871f309d80217477cfd164c106
ms.sourcegitcommit: f0eb7eeedf3ceec726499fa678786d03083214ea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/21/2021
ms.locfileid: "98629258"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="78968-103">-doc (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="78968-103">-doc (C# Compiler Options)</span></span>

<span data-ttu-id="78968-104">Параметр **-doc** позволяет поместить комментарии документации в XML-файл.</span><span class="sxs-lookup"><span data-stu-id="78968-104">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78968-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="78968-105">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="78968-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="78968-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="78968-107">Выходной XML-файл, который заполняется комментариями из файлов исходного кода, участвующих в компиляции.</span><span class="sxs-lookup"><span data-stu-id="78968-107">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78968-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="78968-108">Remarks</span></span>  

 <span data-ttu-id="78968-109">Комментарии документации могут быть обработаны и добавлены в XML-файл, если они предшествуют объектам файлов исходного кода, перечисленным ниже.</span><span class="sxs-lookup"><span data-stu-id="78968-109">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="78968-110">Такие определяемые пользователем типы, как [класс](../keywords/class.md), [делегат](../builtin-types/reference-types.md#the-delegate-type) или [интерфейс](../keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="78968-110">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="78968-111">Такие члены, как поле, [событие](../keywords/event.md), [свойство](../../programming-guide/classes-and-structs/using-properties.md) или метод.</span><span class="sxs-lookup"><span data-stu-id="78968-111">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="78968-112">Файл исходного кода, содержащий метод "Main", первым выводится в XML-файл.</span><span class="sxs-lookup"><span data-stu-id="78968-112">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="78968-113">Чтобы использовать созданный XML-файл с помощью функции [IntelliSense](/visualstudio/ide/using-intellisense), имя XML-файла должно совпадать с именем сборки, а сам XML-файл должен находиться в одном каталоге со сборкой.</span><span class="sxs-lookup"><span data-stu-id="78968-113">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="78968-114">Таким образом, если в проект Visual Studio добавляется ссылка на сборку, то XML-файл также будет найден.</span><span class="sxs-lookup"><span data-stu-id="78968-114">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="78968-115">Дополнительные сведения см. в разделе [Создание XML-примечаний к коду](/visualstudio/ide/reference/generate-xml-documentation-comments).</span><span class="sxs-lookup"><span data-stu-id="78968-115">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="78968-116">Если при компиляции не используется параметр [-target:module](./target-module-compiler-option.md), `file` будет содержать теги \<assembly>\</assembly>, которые указывают имя файла, содержащего манифест сборки для выходного файла компиляции.</span><span class="sxs-lookup"><span data-stu-id="78968-116">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78968-117">Параметр -doc применяется ко всем входным файлам или (если он установлен в параметрах проекта) ко всем файлам проекта.</span><span class="sxs-lookup"><span data-stu-id="78968-117">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="78968-118">Чтобы отключить предупреждения, связанные с комментариями документации для определенного файла или раздела кода, используйте директиву [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="78968-118">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="78968-119">Способы создания документации из комментариев в коде описаны в разделе [Рекомендуемые теги для комментариев документации](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).</span><span class="sxs-lookup"><span data-stu-id="78968-119">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-2019-development-environment"></a><span data-ttu-id="78968-120">Установка данного параметра компилятора в среде разработки Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="78968-120">To set this compiler option in the Visual Studio 2019 development environment</span></span>  

1. <span data-ttu-id="78968-121">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="78968-121">Open the project's **Properties** page.</span></span>  
2. <span data-ttu-id="78968-122">Перейдите на вкладку **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="78968-122">Click the **Build** tab.</span></span>
3. <span data-ttu-id="78968-123">Измените свойство **XML-файл документации**.</span><span class="sxs-lookup"><span data-stu-id="78968-123">Modify the **XML documentation file** property.</span></span>
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-for-mac-development-environment"></a><span data-ttu-id="78968-124">Установка данного параметра компилятора в среде разработки Visual Studio для Mac</span><span class="sxs-lookup"><span data-stu-id="78968-124">To set this compiler option in the Visual Studio for Mac development environment</span></span>  
  
1. <span data-ttu-id="78968-125">Откройте страницу проекта **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="78968-125">Open the project's **Options** page.</span></span>
2. <span data-ttu-id="78968-126">Перейдите на вкладку **Компилятор**.</span><span class="sxs-lookup"><span data-stu-id="78968-126">Select the **Compiler** tab.</span></span>
3. <span data-ttu-id="78968-127">Выберите **Создать XML-документацию** и введите имя файла в текстовом поле.</span><span class="sxs-lookup"><span data-stu-id="78968-127">Select **Generate xml documentation** and enter the file name in the text box.</span></span>

<span data-ttu-id="78968-128">Сведения об установке этого параметра компилятора программными средствами см. в статье <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="78968-128">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78968-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="78968-129">See also</span></span>

- [<span data-ttu-id="78968-130">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="78968-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="78968-131">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="78968-131">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
