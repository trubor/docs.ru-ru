---
description: -linkresource (параметры компилятора C#)
title: -linkresource (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: 4efa0cbf286b40ad971bad66a7acce15e553eb39
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194106"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="d394d-103">-linkresource (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="d394d-103">-linkresource (C# Compiler Options)</span></span>

<span data-ttu-id="d394d-104">Создает в выходном файле ссылку на ресурс .NET.</span><span class="sxs-lookup"><span data-stu-id="d394d-104">Creates a link to a .NET resource in the output file.</span></span> <span data-ttu-id="d394d-105">Файл ресурсов не добавляется в выходной файл.</span><span class="sxs-lookup"><span data-stu-id="d394d-105">The resource file is not added to the output file.</span></span> <span data-ttu-id="d394d-106">Этот параметр отличается от параметра [-resource](./resource-compiler-option.md), который внедряет файл ресурсов в выходной файл.</span><span class="sxs-lookup"><span data-stu-id="d394d-106">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d394d-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d394d-107">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d394d-108">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d394d-108">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="d394d-109">Файл ресурсов .NET, ссылку на который необходимо создать из сборки.</span><span class="sxs-lookup"><span data-stu-id="d394d-109">The .NET resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="d394d-110">Среда `identifier` (необязательно)</span><span class="sxs-lookup"><span data-stu-id="d394d-110">`identifier` (optional)</span></span>  
 <span data-ttu-id="d394d-111">Логическое имя ресурса, используемое для его загрузки.</span><span class="sxs-lookup"><span data-stu-id="d394d-111">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="d394d-112">По умолчанию используется имя файла.</span><span class="sxs-lookup"><span data-stu-id="d394d-112">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="d394d-113">Среда `accessibility-modifier` (необязательно)</span><span class="sxs-lookup"><span data-stu-id="d394d-113">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="d394d-114">Доступность ресурса: "public" (открытый) или "private" (закрытый).</span><span class="sxs-lookup"><span data-stu-id="d394d-114">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="d394d-115">Значение по умолчанию: public.</span><span class="sxs-lookup"><span data-stu-id="d394d-115">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d394d-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="d394d-116">Remarks</span></span>  

 <span data-ttu-id="d394d-117">По умолчанию связанные ресурсы в сборке открыты, если они создавались с помощью компилятора C#.</span><span class="sxs-lookup"><span data-stu-id="d394d-117">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="d394d-118">Чтобы сделать ресурс закрытым, укажите параметр `private` в качестве модификатора доступа.</span><span class="sxs-lookup"><span data-stu-id="d394d-118">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="d394d-119">Модификаторы, отличные от `public` или `private`, не допускаются.</span><span class="sxs-lookup"><span data-stu-id="d394d-119">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="d394d-120">Параметр **-linkresource** требует один из параметров [-target](./target-compiler-option.md), отличный от **-target:module**.</span><span class="sxs-lookup"><span data-stu-id="d394d-120">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="d394d-121">Если `filename` является файлом ресурсов .NET, созданным, например, с помощью [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) или в среде разработки, то к нему можно обращаться с помощью элементов в пространстве имен <xref:System.Resources>.</span><span class="sxs-lookup"><span data-stu-id="d394d-121">If `filename` is a .NET resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="d394d-122">Для получения дополнительной информации см. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d394d-122">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d394d-123">Чтобы получить доступ ко всем остальным ресурсам во время выполнения, используйте методы `GetManifestResource` в классе <xref:System.Reflection.Assembly>.</span><span class="sxs-lookup"><span data-stu-id="d394d-123">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="d394d-124">Файл, указанный в параметре `filename`, может иметь любой формат.</span><span class="sxs-lookup"><span data-stu-id="d394d-124">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="d394d-125">Например, может потребоваться сделать имеющуюся на компьютере библиотеку DLL частью сборки, поэтому ее можно разместить в глобальном кэше сборок и обеспечить к ней доступ из управляемого кода сборки.</span><span class="sxs-lookup"><span data-stu-id="d394d-125">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="d394d-126">Во втором из следующих примеров показывается, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="d394d-126">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="d394d-127">Это действие можно также выполнить в компоновщике сборок.</span><span class="sxs-lookup"><span data-stu-id="d394d-127">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="d394d-128">В третьем из следующих примеров показывается, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="d394d-128">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="d394d-129">Дополнительные сведения см. в разделах [Al.exe (компоновщик сборок)](../../../framework/tools/al-exe-assembly-linker.md) и [Работа со сборками и глобальным кэшем сборок](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="d394d-129">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="d394d-130">**-linkres** является краткой формой **-linkresource**.</span><span class="sxs-lookup"><span data-stu-id="d394d-130">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="d394d-131">Этот параметр компилятора недоступен в Visual Studio и не может быть изменен программным способом.</span><span class="sxs-lookup"><span data-stu-id="d394d-131">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d394d-132">Пример</span><span class="sxs-lookup"><span data-stu-id="d394d-132">Example</span></span>  

 <span data-ttu-id="d394d-133">Компиляция `in.cs` и создание ссылки на файл ресурсов `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="d394d-133">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="d394d-134">Пример</span><span class="sxs-lookup"><span data-stu-id="d394d-134">Example</span></span>  

 <span data-ttu-id="d394d-135">Скомпилируйте `A.cs` в библиотеку DLL, создайте ссылку на машинную библиотеку N.dll и поместите выходные данные в глобальный кэш сборок (GAC).</span><span class="sxs-lookup"><span data-stu-id="d394d-135">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="d394d-136">В этом примере оба файла A.dll и N.dll будут расположены в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="d394d-136">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="d394d-137">Пример</span><span class="sxs-lookup"><span data-stu-id="d394d-137">Example</span></span>  

 <span data-ttu-id="d394d-138">В этом примере выполняются те же действия, что и в предыдущем примере, но с использованием параметров компоновщика сборок.</span><span class="sxs-lookup"><span data-stu-id="d394d-138">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="d394d-139">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d394d-139">See also</span></span>

- [<span data-ttu-id="d394d-140">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="d394d-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d394d-141">Al.exe (компоновщик сборок)</span><span class="sxs-lookup"><span data-stu-id="d394d-141">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="d394d-142">Работа со сборками и глобальным кэшем сборок</span><span class="sxs-lookup"><span data-stu-id="d394d-142">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="d394d-143">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="d394d-143">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
