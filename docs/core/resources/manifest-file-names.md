---
title: Как MSBuild генерирует имена файлов манифеста
description: В статье описываются факторы, влияющие на имя файла манифеста ресурса, создаваемого MSBuild во время компиляции.
ms.date: 05/08/2020
ms.topic: conceptual
ms.openlocfilehash: 383bf6a077b0631e70ddaa4721b20e992127a73c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "97866393"
---
# <a name="how-resource-manifest-files-are-named"></a><span data-ttu-id="164a3-103">Имена файлов манифестов ресурсов</span><span class="sxs-lookup"><span data-stu-id="164a3-103">How resource manifest files are named</span></span>

<span data-ttu-id="164a3-104">Когда MSBuild компилирует проект .NET Core, файлы ресурсов XML, имеющие расширение файла *RESX*, преобразуются в двоичные файлы *RESOURCES*.</span><span class="sxs-lookup"><span data-stu-id="164a3-104">When MSBuild compiles a .NET Core project, XML resource files, which have the *.resx* file extension, are converted into binary *.resources* files.</span></span> <span data-ttu-id="164a3-105">Двоичные файлы внедряются в выходные данные компилятора и могут быть считаны <xref:System.Resources.ResourceManager>.</span><span class="sxs-lookup"><span data-stu-id="164a3-105">The binary files are embedded into the output of the compiler and can be read by the <xref:System.Resources.ResourceManager>.</span></span> <span data-ttu-id="164a3-106">В этой статье описывается, как MSBuild выбирает имя для каждого файла *RESOURCES*.</span><span class="sxs-lookup"><span data-stu-id="164a3-106">This article describes how MSBuild chooses a name for each *.resources* file.</span></span>

> [!TIP]
> <span data-ttu-id="164a3-107">Если в файл проекта явно добавлен элемент ресурса, который также [включен в глобальные элементы по умолчанию для .NET Core](../project-sdk/overview.md#default-compilation-includes), возникнет ошибка сборки.</span><span class="sxs-lookup"><span data-stu-id="164a3-107">If you explicitly add a resource item to your project file, and it's also [included with the default include globs for .NET Core](../project-sdk/overview.md#default-compilation-includes), you will get a build error.</span></span> <span data-ttu-id="164a3-108">Чтобы вручную включить файлы ресурсов в качестве элементов `EmbeddedResource`, установите для свойства `EnableDefaultEmbeddedResourceItems` значение false.</span><span class="sxs-lookup"><span data-stu-id="164a3-108">To manually include resource files as `EmbeddedResource` items, set the `EnableDefaultEmbeddedResourceItems` property to false.</span></span>

## <a name="default-name"></a><span data-ttu-id="164a3-109">Имя по умолчанию</span><span class="sxs-lookup"><span data-stu-id="164a3-109">Default name</span></span>

<span data-ttu-id="164a3-110">В .NET Core 3.0 и более поздних версиях при соблюдении обоих следующих условий манифесту ресурса присваивается имя по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="164a3-110">In .NET Core 3.0 and later, the default name for a resource manifest is used when both of the following conditions are met:</span></span>

- <span data-ttu-id="164a3-111">Файл ресурсов не включен явным образом в файл проекта как элемент `EmbeddedResource` с метаданными `LogicalName`, `ManifestResourceName` или `DependentUpon`.</span><span class="sxs-lookup"><span data-stu-id="164a3-111">The resource file is not explicitly included in the project file as an `EmbeddedResource` item with `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata.</span></span>
- <span data-ttu-id="164a3-112">В файле проекта для свойства `EmbeddedResourceUseDependentUponConvention` не задано значение `false`.</span><span class="sxs-lookup"><span data-stu-id="164a3-112">The `EmbeddedResourceUseDependentUponConvention` property is not set to `false` in the project file.</span></span> <span data-ttu-id="164a3-113">По умолчанию для свойства задано значение `true`.</span><span class="sxs-lookup"><span data-stu-id="164a3-113">By default, this property is set to `true`.</span></span> <span data-ttu-id="164a3-114">Дополнительные сведения см. в разделе [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span><span class="sxs-lookup"><span data-stu-id="164a3-114">For more information, see [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span></span>

<span data-ttu-id="164a3-115">Если файл ресурсов совместно расположен с исходным файлом (*CS* или *VB*) с тем же именем корневого файла, то для имени файла манифеста используется полное имя первого типа, определенного в исходном файле.</span><span class="sxs-lookup"><span data-stu-id="164a3-115">If the resource file is colocated with a source file (*.cs* or *.vb*) of the same root file name, the full name of the first type that's defined in the source file is used for the manifest file name.</span></span> <span data-ttu-id="164a3-116">Например, если `MyNamespace.Form1` является первым типом, определенным в *Form1.cs*, а *Form1.cs* хранится вместе с *Form1.resx*, то сгенерированным именем манифеста для этого файла ресурсов будет *MyNamespace.Form1.resources*.</span><span class="sxs-lookup"><span data-stu-id="164a3-116">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, and *Form1.cs* is colocated with *Form1.resx*, the generated manifest name for that resource file is *MyNamespace.Form1.resources*.</span></span>

## <a name="logicalname-metadata"></a><span data-ttu-id="164a3-117">Метаданные LogicalName</span><span class="sxs-lookup"><span data-stu-id="164a3-117">LogicalName metadata</span></span>

<span data-ttu-id="164a3-118">Если файл ресурсов явно включен в файл проекта в качестве элемента `EmbeddedResource` с метаданными `LogicalName`, в качестве имени манифеста используется значение `LogicalName`.</span><span class="sxs-lookup"><span data-stu-id="164a3-118">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `LogicalName` metadata, the `LogicalName` value is used as the manifest name.</span></span> <span data-ttu-id="164a3-119">`LogicalName` имеет приоритет над любым другим метаданным или параметром.</span><span class="sxs-lookup"><span data-stu-id="164a3-119">`LogicalName` takes precedence over any other metadata or setting.</span></span>

<span data-ttu-id="164a3-120">Например, имя манифеста для файла ресурсов, определенного в следующем фрагменте файла проекта, — *SomeName.resources*.</span><span class="sxs-lookup"><span data-stu-id="164a3-120">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

<span data-ttu-id="164a3-121">-или-</span><span class="sxs-lookup"><span data-stu-id="164a3-121">-or-</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a><span data-ttu-id="164a3-122">Метаданные ManifestResourceName</span><span class="sxs-lookup"><span data-stu-id="164a3-122">ManifestResourceName metadata</span></span>

<span data-ttu-id="164a3-123">Если файл ресурсов явно включен в файл проекта как элемент `EmbeddedResource` с метаданными `ManifestResourceName` (и `LogicalName` отсутствует), в качестве имени файла манифеста используется значение `ManifestResourceName` в сочетании с расширением файла *RESOURCES*.</span><span class="sxs-lookup"><span data-stu-id="164a3-123">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `ManifestResourceName` metadata (and `LogicalName` is absent), the `ManifestResourceName` value, combined with the file extension *.resources*, is used as the manifest file name.</span></span>

<span data-ttu-id="164a3-124">Например, имя манифеста для файла ресурсов, определенного в следующем фрагменте файла проекта, — *SomeName.resources*.</span><span class="sxs-lookup"><span data-stu-id="164a3-124">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

<span data-ttu-id="164a3-125">Имя манифеста для файла ресурсов, определенного в следующем фрагменте файла проекта, — *SomeName.fr-FR.resources*.</span><span class="sxs-lookup"><span data-stu-id="164a3-125">The manifest name for the resource file that's defined in the following project file snippet is *SomeName.fr-FR.resources*.</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a><span data-ttu-id="164a3-126">Метаданные DependentUpon</span><span class="sxs-lookup"><span data-stu-id="164a3-126">DependentUpon metadata</span></span>

<span data-ttu-id="164a3-127">Если файл ресурсов явно включен в файл проекта как элемент `EmbeddedResource` с метаданными `DependentUpon` (а `LogicalName` и `ManifestResourceName` отсутствуют), то сведения из исходного файла, определенного `DependentUpon`, используются для имени файла манифеста ресурса.</span><span class="sxs-lookup"><span data-stu-id="164a3-127">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `DependentUpon` metadata (and `LogicalName` and `ManifestResourceName` are absent), information from the source file defined by `DependentUpon` is used for the resource manifest file name.</span></span> <span data-ttu-id="164a3-128">В частности, имя первого типа, определенное в исходном файле, используется в имени манифеста следующим образом: *Namespace.Classname\[.Culture].resources*.</span><span class="sxs-lookup"><span data-stu-id="164a3-128">Specifically, the name of the first type that's defined in the source file is used in the manifest name as follows: *Namespace.Classname\[.Culture].resources*.</span></span>

<span data-ttu-id="164a3-129">Например, имя манифеста для файла ресурсов, определенного в следующем фрагменте файла проекта, — *Namespace.Classname.resources* (где `Namespace.Classname` является первым классом, который определен в *MyTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="164a3-129">For example, the manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

<span data-ttu-id="164a3-130">Имя манифеста для файла ресурсов, определенного в следующем фрагменте файла проекта, — *Namespace.Classname.fr-FR.resources* (где `Namespace.Classname` является первым классом, который определен в *MyTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="164a3-130">The manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a><span data-ttu-id="164a3-131">Свойство EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="164a3-131">EmbeddedResourceUseDependentUponConvention property</span></span>

<span data-ttu-id="164a3-132">Если в файле проекта `EmbeddedResourceUseDependentUponConvention` имеет значение `false`, каждое имя файла манифеста ресурса будет основано на имени корневого пространства имен проекта и относительном пути к файлу *RESX* из корневого каталога проекта.</span><span class="sxs-lookup"><span data-stu-id="164a3-132">If `EmbeddedResourceUseDependentUponConvention` is set to `false` in the project file, each resource manifest file name is based off the root namespace for the project and the relative path from the project root to the *.resx* file.</span></span> <span data-ttu-id="164a3-133">В частности, именем сгенерированного файла манифеста ресурса будет *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span><span class="sxs-lookup"><span data-stu-id="164a3-133">More specifically, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="164a3-134">Такая же логика применяется при генерировании имен манифестов в версиях .NET Core, предшествующих версии 3.0.</span><span class="sxs-lookup"><span data-stu-id="164a3-134">This is also the logic used to generate manifest names in .NET Core versions prior to 3.0.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="164a3-135">Если параметр `RootNamespace` не определен, по умолчанию используется имя проекта.</span><span class="sxs-lookup"><span data-stu-id="164a3-135">If `RootNamespace` is not defined, it defaults to the project name.</span></span>
> - <span data-ttu-id="164a3-136">Если для элемента `EmbeddedResource` в файле проекта заданы метаданные `LogicalName`, `ManifestResourceName` или `DependentUpon`, это правило именования не применяется к этому файлу ресурсов.</span><span class="sxs-lookup"><span data-stu-id="164a3-136">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item in the project file, this naming rule does not apply to that resource file.</span></span>

## <a name="see-also"></a><span data-ttu-id="164a3-137">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="164a3-137">See also</span></span>

- [<span data-ttu-id="164a3-138">Как работает именование ресурсов манифеста</span><span class="sxs-lookup"><span data-stu-id="164a3-138">How Manifest Resource Naming Works</span></span>](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [<span data-ttu-id="164a3-139">Свойства MSBuild для проектов пакета SDK для .NET Core</span><span class="sxs-lookup"><span data-stu-id="164a3-139">MSBuild properties for .NET Core SDK projects</span></span>](../project-sdk/msbuild-props.md)
- [<span data-ttu-id="164a3-140">Критические изменения MSBuild</span><span class="sxs-lookup"><span data-stu-id="164a3-140">MSBuild breaking changes</span></span>](../compatibility/msbuild.md)
