---
description: 'Дополнительные сведения: -resource (Visual Basic)'
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 830d89ab4f4063aa12d12a5206b76e49c5355708
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474113"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="387fb-103">-resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="387fb-103">-resource (Visual Basic)</span></span>

<span data-ttu-id="387fb-104">Внедряет управляемый ресурс в сборку.</span><span class="sxs-lookup"><span data-stu-id="387fb-104">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="387fb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="387fb-105">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="387fb-106">or</span><span class="sxs-lookup"><span data-stu-id="387fb-106">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="387fb-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="387fb-107">Arguments</span></span>  
  
|<span data-ttu-id="387fb-108">Термин</span><span class="sxs-lookup"><span data-stu-id="387fb-108">Term</span></span>|<span data-ttu-id="387fb-109">Определение</span><span class="sxs-lookup"><span data-stu-id="387fb-109">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="387fb-110">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="387fb-110">Required.</span></span> <span data-ttu-id="387fb-111">Имя файла ресурсов, который вам нужно внедрить в выходной файл.</span><span class="sxs-lookup"><span data-stu-id="387fb-111">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="387fb-112">По умолчанию `filename` в сборке является общедоступным.</span><span class="sxs-lookup"><span data-stu-id="387fb-112">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="387fb-113">Если имя файла содержит пробел, заключите это имя в кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="387fb-113">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="387fb-114">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="387fb-114">Optional.</span></span> <span data-ttu-id="387fb-115">Логическое имя ресурса, которое используется для его загрузки.</span><span class="sxs-lookup"><span data-stu-id="387fb-115">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="387fb-116">По умолчанию используется имя файла.</span><span class="sxs-lookup"><span data-stu-id="387fb-116">The default is the name of the file.</span></span> <span data-ttu-id="387fb-117">При необходимости в манифесте сборки можно указать, является ли ресурс общедоступным или частным, например так: `-res:filename.res, myname.res, public`.</span><span class="sxs-lookup"><span data-stu-id="387fb-117">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="387fb-118">Примечания</span><span class="sxs-lookup"><span data-stu-id="387fb-118">Remarks</span></span>  

 <span data-ttu-id="387fb-119">Используйте `-linkresource`, чтобы связать ресурс со сборкой без размещения файла ресурсов в выходном файле.</span><span class="sxs-lookup"><span data-stu-id="387fb-119">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="387fb-120">Если `filename` — файл ресурса .NET Framework, созданный генератором файлов ресурсов ([Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md)) или в среде разработки, то к нему можно обращаться с помощью элементов пространства имен <xref:System.Resources> (дополнительные сведения см. в статье о классе <xref:System.Resources.ResourceManager>).</span><span class="sxs-lookup"><span data-stu-id="387fb-120">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="387fb-121">Для доступа ко всем остальным ресурсам во время выполнения используйте следующие методы: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> и <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="387fb-121">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="387fb-122">Краткой формой `-resource` является `-res`.</span><span class="sxs-lookup"><span data-stu-id="387fb-122">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="387fb-123">Дополнительные сведения о настройке `-resource` в интегрированной среде разработки Visual Studio см. в статье [об управлении ресурсами приложения в .NET](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="387fb-123">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="387fb-124">Пример</span><span class="sxs-lookup"><span data-stu-id="387fb-124">Example</span></span>  

 <span data-ttu-id="387fb-125">Следующий код компилирует `In.vb` и присоединяет файл ресурсов `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="387fb-125">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="387fb-126">См. также</span><span class="sxs-lookup"><span data-stu-id="387fb-126">See also</span></span>

- [<span data-ttu-id="387fb-127">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="387fb-127">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="387fb-128">-win32resource</span><span class="sxs-lookup"><span data-stu-id="387fb-128">-win32resource</span></span>](win32resource.md)
- [<span data-ttu-id="387fb-129">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="387fb-129">-linkresource (Visual Basic)</span></span>](linkresource.md)
- [<span data-ttu-id="387fb-130">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="387fb-130">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="387fb-131">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="387fb-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
