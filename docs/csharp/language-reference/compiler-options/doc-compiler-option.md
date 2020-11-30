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
ms.openlocfilehash: b1d7fbbe98aaad16454fdd71c161f2a17a2f4f2e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173260"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="e43bb-103">-doc (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="e43bb-103">-doc (C# Compiler Options)</span></span>

<span data-ttu-id="e43bb-104">Параметр **-doc** позволяет поместить комментарии документации в XML-файл.</span><span class="sxs-lookup"><span data-stu-id="e43bb-104">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e43bb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e43bb-105">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="e43bb-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="e43bb-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="e43bb-107">Выходной XML-файл, который заполняется комментариями из файлов исходного кода, участвующих в компиляции.</span><span class="sxs-lookup"><span data-stu-id="e43bb-107">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e43bb-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="e43bb-108">Remarks</span></span>  

 <span data-ttu-id="e43bb-109">Комментарии документации могут быть обработаны и добавлены в XML-файл, если они предшествуют объектам файлов исходного кода, перечисленным ниже.</span><span class="sxs-lookup"><span data-stu-id="e43bb-109">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="e43bb-110">Такие определяемые пользователем типы, как [класс](../keywords/class.md), [делегат](../builtin-types/reference-types.md#the-delegate-type) или [интерфейс](../keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="e43bb-110">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="e43bb-111">Такие члены, как поле, [событие](../keywords/event.md), [свойство](../../programming-guide/classes-and-structs/using-properties.md) или метод.</span><span class="sxs-lookup"><span data-stu-id="e43bb-111">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="e43bb-112">Файл исходного кода, содержащий метод "Main", первым выводится в XML-файл.</span><span class="sxs-lookup"><span data-stu-id="e43bb-112">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="e43bb-113">Чтобы использовать созданный XML-файл с помощью функции [IntelliSense](/visualstudio/ide/using-intellisense), имя XML-файла должно совпадать с именем сборки, а сам XML-файл должен находиться в одном каталоге со сборкой.</span><span class="sxs-lookup"><span data-stu-id="e43bb-113">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="e43bb-114">Таким образом, если в проект Visual Studio добавляется ссылка на сборку, то XML-файл также будет найден.</span><span class="sxs-lookup"><span data-stu-id="e43bb-114">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="e43bb-115">Дополнительные сведения см. в разделе [Создание XML-примечаний к коду](/visualstudio/ide/reference/generate-xml-documentation-comments).</span><span class="sxs-lookup"><span data-stu-id="e43bb-115">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="e43bb-116">Если при компиляции не используется параметр [-target:module](./target-module-compiler-option.md), `file` будет содержать теги \<assembly>\</assembly>, которые указывают имя файла, содержащего манифест сборки для выходного файла компиляции.</span><span class="sxs-lookup"><span data-stu-id="e43bb-116">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e43bb-117">Параметр -doc применяется ко всем входным файлам или (если он установлен в параметрах проекта) ко всем файлам проекта.</span><span class="sxs-lookup"><span data-stu-id="e43bb-117">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="e43bb-118">Чтобы отключить предупреждения, связанные с комментариями документации для определенного файла или раздела кода, используйте директиву [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="e43bb-118">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="e43bb-119">Способы создания документации из комментариев в коде описаны в разделе [Рекомендуемые теги для комментариев документации](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).</span><span class="sxs-lookup"><span data-stu-id="e43bb-119">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e43bb-120">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e43bb-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="e43bb-121">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="e43bb-121">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="e43bb-122">Перейдите на вкладку **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="e43bb-122">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="e43bb-123">Измените свойство **XML-файл документации**.</span><span class="sxs-lookup"><span data-stu-id="e43bb-123">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="e43bb-124">Сведения об установке этого параметра компилятора программными средствами см. в статье <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="e43bb-124">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e43bb-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e43bb-125">See also</span></span>

- [<span data-ttu-id="e43bb-126">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="e43bb-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e43bb-127">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="e43bb-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
