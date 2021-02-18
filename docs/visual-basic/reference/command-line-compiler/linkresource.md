---
description: 'Дополнительные сведения: -linkresource (Visual Basic)'
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 21fc47ecff44230bda0f445bc695706b5ae91eff
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463706"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="47c38-103">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47c38-103">-linkresource (Visual Basic)</span></span>

<span data-ttu-id="47c38-104">Создает ссылку на управляемый ресурс.</span><span class="sxs-lookup"><span data-stu-id="47c38-104">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47c38-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="47c38-105">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="47c38-106">or</span><span class="sxs-lookup"><span data-stu-id="47c38-106">or</span></span>  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="47c38-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="47c38-107">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="47c38-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="47c38-108">Required.</span></span> <span data-ttu-id="47c38-109">Файл ресурсов, связываемый со сборкой.</span><span class="sxs-lookup"><span data-stu-id="47c38-109">The resource file to link to the assembly.</span></span> <span data-ttu-id="47c38-110">Если имя файла содержит пробел, заключите его в кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="47c38-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="47c38-111">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="47c38-111">Optional.</span></span> <span data-ttu-id="47c38-112">Логическое имя ресурса.</span><span class="sxs-lookup"><span data-stu-id="47c38-112">The logical name for the resource.</span></span> <span data-ttu-id="47c38-113">Имя, которое используется для загрузки ресурса.</span><span class="sxs-lookup"><span data-stu-id="47c38-113">The name that is used to load the resource.</span></span> <span data-ttu-id="47c38-114">По умолчанию используется имя файла.</span><span class="sxs-lookup"><span data-stu-id="47c38-114">The default is the name of the file.</span></span> <span data-ttu-id="47c38-115">При необходимости в манифесте сборки можно указать, является ли файл общедоступным или частным, например: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="47c38-115">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="47c38-116">По умолчанию `filename` в сборке является общедоступным.</span><span class="sxs-lookup"><span data-stu-id="47c38-116">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47c38-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="47c38-117">Remarks</span></span>  

 <span data-ttu-id="47c38-118">Параметр `-linkresource` не подразумевает внедрение файла ресурсов в выходной файл; для этого используйте параметр `-resource`.</span><span class="sxs-lookup"><span data-stu-id="47c38-118">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="47c38-119">Для параметра `-linkresource` требуется один из параметров `-target`, кроме `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="47c38-119">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="47c38-120">Если `filename` является файлом ресурсов .NET Framework, созданным, например, генератором файлов ресурсов ([Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md)) или в среде разработки, то к нему можно обращаться с помощью элементов пространства имен <xref:System.Resources>.</span><span class="sxs-lookup"><span data-stu-id="47c38-120">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="47c38-121">(Дополнительные сведения см. в разделе <xref:System.Resources.ResourceManager>.) Для доступа ко всем остальным ресурсам во время выполнения используйте методы, начинающиеся с `GetManifestResource`, из класса <xref:System.Reflection.Assembly>.</span><span class="sxs-lookup"><span data-stu-id="47c38-121">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="47c38-122">Имя файла может быть в любом формате файла.</span><span class="sxs-lookup"><span data-stu-id="47c38-122">The file name can be any file format.</span></span> <span data-ttu-id="47c38-123">Например, может потребоваться сделать имеющуюся на компьютере библиотеку DLL частью сборки, поэтому ее можно разместить в глобальном кэше сборок и обеспечить к ней доступ из управляемого кода сборки.</span><span class="sxs-lookup"><span data-stu-id="47c38-123">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="47c38-124">Краткой формой `-linkresource` является `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="47c38-124">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47c38-125">Параметр `-linkresource` недоступен в среде разработки Visual Studio. Его можно использовать только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="47c38-125">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47c38-126">Пример</span><span class="sxs-lookup"><span data-stu-id="47c38-126">Example</span></span>  

 <span data-ttu-id="47c38-127">Следующий код компилирует `in.vb` и обращается к файлу ресурсов `rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="47c38-127">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="47c38-128">См. также</span><span class="sxs-lookup"><span data-stu-id="47c38-128">See also</span></span>

- [<span data-ttu-id="47c38-129">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="47c38-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="47c38-130">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47c38-130">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="47c38-131">-resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47c38-131">-resource (Visual Basic)</span></span>](resource.md)
- [<span data-ttu-id="47c38-132">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="47c38-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
