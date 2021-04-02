---
title: Свойства MSBuild для Microsoft.NET.Sdk
description: Справочник по свойствам и элементам MSBuild, распознаваемым пакетом SDK для .NET.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: effcb704056f553b2986ee4a61f73c0dc58af599
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636770"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a>Справочник по MSBuild для проектов пакета SDK для .NET

Эта страница содержит справочные сведения о свойствах и элементах MSBuild, которые вы можете использовать для настройки проектов .NET.

> [!NOTE]
> Работа над этой страницей еще не завершена, поэтому здесь приведены лишь некоторые полезные свойства MSBuild для пакета SDK для .NET. Список стандартных свойств см. в статье [Общие свойства MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Свойства платформы

В этом разделе описаны следующие свойства MSBuild:

- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

Свойство `TargetFramework` определяет версию целевой платформы для приложения. Список допустимых моникеров целевой платформы см. в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md#supported-target-frameworks).

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

Дополнительные сведения см.в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFrameworks

Используйте свойство `TargetFrameworks`, если приложение должно быть предназначено для нескольких платформ. Список допустимых моникеров целевой платформы см. в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md#supported-target-frameworks).

> [!NOTE]
> Это свойство игнорируется, если указано свойство `TargetFramework` (в единственном числе).

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

Дополнительные сведения см.в статье [Целевые платформы в проектах в стиле SDK](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Это свойство применяется только к проектам, использующим `netstandard1.x`. Он не применяется к проектам, использующим `netstandard2.x`.

Используйте свойство `NetStandardImplicitPackageVersion`, если вам нужно указать версию платформы ниже версии метапакета. Файл проекта, приведенный в следующем примере, предназначен для `netstandard1.3`, но использует `NETStandard.Library` версии 1.6.0.

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="assembly-info-generation-properties"></a>Свойства создания сведений о сборке

- [GenerateAssemblyCompanyAttribute](#generateassemblycompanyattribute)
- [GenerateAssemblyConfigurationAttribute](#generateassemblyconfigurationattribute)
- [GenerateAssemblyCopyrightAttribute](#generateassemblycopyrightattribute)
- [GenerateAssemblyDescriptionAttribute](#generateassemblydescriptionattribute)
- [GenerateAssemblyFileVersionAttribute](#generateassemblyfileversionattribute)
- [GenerateAssemblyInfo](#generateassemblyinfo)
- [GenerateAssemblyInformationalVersionAttribute](#generateassemblyinformationalversionattribute)
- [GenerateAssemblyProductAttribute](#generateassemblyproductattribute)
- [GenerateAssemblyTitleAttribute](#generateassemblytitleattribute)
- [GenerateAssemblyVersionAttribute](#generateassemblyversionattribute)
- [GeneratedAssemblyInfoFile](#generatedassemblyinfofile)
- [GenerateNeutralResourcesLanguageAttribute](#generateneutralresourceslanguageattribute)

### <a name="generateassemblycompanyattribute"></a>GenerateAssemblyCompanyAttribute

Это свойство определяет, создает ли свойство `Company` атрибут <xref:System.Reflection.AssemblyCompanyAttribute> для сборки. Значение по умолчанию — `true`.

```xml
<PropertyGroup>
  <GenerateAssemblyCompanyAttribute>false</GenerateAssemblyCompanyAttribute>
</PropertyGroup>
```

### <a name="generateassemblyconfigurationattribute"></a>GenerateAssemblyConfigurationAttribute

Это свойство определяет, создает ли свойство `Configuration` атрибут <xref:System.Reflection.AssemblyConfigurationAttribute> для сборки. Значение по умолчанию — `true`.

```xml
<PropertyGroup>
  <GenerateAssemblyConfigurationAttribute>false</GenerateAssemblyConfigurationAttribute>
</PropertyGroup>
```

### <a name="generateassemblycopyrightattribute"></a>GenerateAssemblyCopyrightAttribute

Это свойство определяет, создает ли свойство `Copyright` атрибут <xref:System.Reflection.AssemblyCopyrightAttribute> для сборки. Значение по умолчанию — `true`.

```xml
<PropertyGroup>
  <GenerateAssemblyCopyrightAttribute>false</GenerateAssemblyCopyrightAttribute>
</PropertyGroup>
```

### <a name="generateassemblydescriptionattribute"></a>GenerateAssemblyDescriptionAttribute

Это свойство определяет, создает ли свойство `Description` атрибут <xref:System.Reflection.AssemblyDescriptionAttribute> для сборки. Значение по умолчанию — `true`.

```xml
<PropertyGroup>
  <GenerateAssemblyDescriptionAttribute>false</GenerateAssemblyDescriptionAttribute>
</PropertyGroup>
```

### <a name="generateassemblyfileversionattribute"></a>GenerateAssemblyFileVersionAttribute

Это свойство определяет, создает ли свойство `FileVersion` атрибут <xref:System.Reflection.AssemblyFileVersionAttribute> для сборки. Значение по умолчанию — `true`.

```xml
<PropertyGroup>
  <GenerateAssemblyFileVersionAttribute>false</GenerateAssemblyFileVersionAttribute>
</PropertyGroup>
```

### <a name="generateassemblyinfo"></a>GenerateAssemblyInfo

Управляет созданием атрибута `AssemblyInfo` для проекта. Значение по умолчанию — `true`. Используйте `false`, чтобы отключить создание файла:

```xml
<PropertyGroup>
  <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
</PropertyGroup>
```

Параметр [GeneratedAssemblyInfoFile](#generatedassemblyinfofile) определяет имя создаваемого файла.

Если значение `GenerateAssemblyInfo` равно `true`, свойства проекта преобразуются в атрибуты `AssemblyInfo`. В следующей таблице перечислены свойства проекта, которые создают атрибуты, а также свойства, которые могут отключить возможность создания:

| Свойство               | attribute                                                      | Свойство, используемое для отключения                                                                               |
|------------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| `Company`              | <xref:System.Reflection.AssemblyCompanyAttribute>              | [`GenerateAssemblyCompanyAttribute`](#generateassemblycompanyattribute)                           |
| `Configuration`        | <xref:System.Reflection.AssemblyConfigurationAttribute>        | [`GenerateAssemblyConfigurationAttribute`](#generateassemblyconfigurationattribute)               |
| `Copyright`            | <xref:System.Reflection.AssemblyCopyrightAttribute>            | [`GenerateAssemblyCopyrightAttribute`](#generateassemblycopyrightattribute)                       |
| `Description`          | <xref:System.Reflection.AssemblyDescriptionAttribute>          | [`GenerateAssemblyDescriptionAttribute`](#generateassemblydescriptionattribute)                   |
| `FileVersion`          | <xref:System.Reflection.AssemblyFileVersionAttribute>          | [`GenerateAssemblyFileVersionAttribute`](#generateassemblyfileversionattribute)                   |
| `InformationalVersion` | <xref:System.Reflection.AssemblyInformationalVersionAttribute> | [`GenerateAssemblyInformationalVersionAttribute`](#generateassemblyinformationalversionattribute) |
| `Product`              | <xref:System.Reflection.AssemblyProductAttribute>              | [`GenerateAssemblyProductAttribute`](#generateassemblyproductattribute)                           |
| `AssemblyTitle`        | <xref:System.Reflection.AssemblyTitleAttribute>                | [`GenerateAssemblyTitleAttribute`](#generateassemblytitleattribute)                               |
| `AssemblyVersion`      | <xref:System.Reflection.AssemblyVersionAttribute>              | [`GenerateAssemblyVersionAttribute`](#generateassemblyversionattribute)                           |
| `NeutralLanguage`      | <xref:System.Resources.NeutralResourcesLanguageAttribute>      | [`GenerateNeutralResourcesLanguageAttribute`](#generateneutralresourceslanguageattribute)         |

Примечания об этих параметрах:

- `AssemblyVersion` и `FileVersion` по умолчанию имеют значение `$(Version)` без суффикса. Например, если для `$(Version)` нужно указать `1.2.3-beta.4`, то значением будет `1.2.3`.
- По умолчанию для `InformationalVersion` используется значение `$(Version)`.
- Если имеется свойство `$(SourceRevisionId)`, оно добавляется к `InformationalVersion`. Такое поведение можно отключить с помощью `IncludeSourceRevisionInInformationalVersion`.
- Свойства `Copyright` и `Description` также используются для метаданных NuGet.
- Свойство `Configuration`, которое по умолчанию имеет значение `Debug`, является общим для всех целевых объектов MSBuild. Его можно задать с помощью параметра `--configuration` команды `dotnet` (например, [dotnet pack](../tools/dotnet-pack.md)).
- Некоторые свойства используются при создании пакета NuGet. Дополнительные сведения см. в разделе [Свойства пакетов](#package-properties).

#### <a name="migrating-from-net-framework"></a>Миграция из .NET Framework

Шаблоны проектов .NET Framework создают файл кода со следующими заданными атрибутами сведений о сборке. Обычно файл расположен здесь: *.\Properties\AssemblyInfo.cs* или *.\Properties\AssemblyInfo.vb*. Проекты в стиле пакета SDK создают этот файл на основе параметров проекта. **Оба варианта не поддерживаются.** При переносе кода в .NET 5 (и .NET Core 3.1) или более поздней версии выполните одно из следующих действий:

- Отключите возможность создания временного файла кода, который содержит атрибуты сведений о сборке, задав для `GenerateAssemblyInfo` значение `false`. Так вы сохраните свой файл *AssemblyInfo*.
- Перенесите параметры из файла `AssemblyInfo` в файл проекта и удалите файл `AssemblyInfo`.

### <a name="generateassemblyinformationalversionattribute"></a>GenerateAssemblyInformationalVersionAttribute

Это свойство определяет, создает ли свойство `InformationalVersion` атрибут <xref:System.Reflection.AssemblyInformationalVersionAttribute> для сборки. Значение по умолчанию — `true`.

```xml
<PropertyGroup>
  <GenerateAssemblyInformationalVersionAttribute>false</GenerateAssemblyInformationalVersionAttribute>
</PropertyGroup>
```

### <a name="generateassemblyproductattribute"></a>GenerateAssemblyProductAttribute

Это свойство определяет, создает ли свойство `Product` атрибут <xref:System.Reflection.AssemblyProductAttribute> для сборки. Значение по умолчанию — `true`.

```xml
<PropertyGroup>
  <GenerateAssemblyProductAttribute>false</GenerateAssemblyProductAttribute>
</PropertyGroup>
```

### <a name="generateassemblytitleattribute"></a>GenerateAssemblyTitleAttribute

Это свойство определяет, создает ли свойство `AssemblyTitle` атрибут <xref:System.Reflection.AssemblyTitleAttribute> для сборки. Значение по умолчанию — `true`.

```xml
<PropertyGroup>
  <GenerateAssemblyTitleAttribute>false</GenerateAssemblyTitleAttribute>
</PropertyGroup>
```

### <a name="generateassemblyversionattribute"></a>GenerateAssemblyVersionAttribute

Это свойство определяет, создает ли свойство `AssemblyVersion` атрибут <xref:System.Reflection.AssemblyVersionAttribute> для сборки. Значение по умолчанию — `true`.

```xml
<PropertyGroup>
  <GenerateAssemblyVersionAttribute>false</GenerateAssemblyVersionAttribute>
</PropertyGroup>
```

### <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

Это свойство определяет относительный или абсолютный путь к файлу сведений о созданной сборке. По умолчанию используется файл с именем *[имя_проекта].AssemblyInfo.[cs|vb]* в каталоге `$(IntermediateOutputPath)` (обычно это *obj*).

```xml
<PropertyGroup>
  <GeneratedAssemblyInfoFile>assemblyinfo.cs</GeneratedAssemblyInfoFile>
</PropertyGroup>
```

### <a name="generateneutralresourceslanguageattribute"></a>GenerateNeutralResourcesLanguageAttribute

Это свойство определяет, создает ли свойство `NeutralLanguage` атрибут <xref:System.Resources.NeutralResourcesLanguageAttribute> для сборки. Значение по умолчанию — `true`.

```xml
<PropertyGroup>
  <GenerateNeutralResourcesLanguageAttribute>false</GenerateNeutralResourcesLanguageAttribute>
</PropertyGroup>
```

## <a name="package-properties"></a>Свойства пакета

Для описания пакета, созданного из проекта, можно указать такие свойства, как `PackageId`, `PackageVersion`, `PackageIcon`, `Title` и `Description`. Дополнительные сведения об этих и других свойствах см. в разделе [целевой объект пакета](/nuget/reference/msbuild-targets#pack-target).

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-related-properties"></a>Свойства, связанные с публикацией

В этом разделе описаны следующие свойства MSBuild:

- [AppendRuntimeIdentifierToOutputPath](#appendruntimeidentifiertooutputpath)
- [AppendTargetFrameworkToOutputPath](#appendtargetframeworktooutputpath)
- [CopyLocalLockFileAssemblies](#copylocallockfileassemblies)
- [PreserveCompilationContext](#preservecompilationcontext)
- [PreserveCompilationReferences](#preservecompilationreferences)
- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [UseAppHost](#useapphost)

### <a name="appendtargetframeworktooutputpath"></a>AppendTargetFrameworkToOutputPath

Свойство `AppendTargetFrameworkToOutputPath` определяет, добавляется ли [моникер целевой платформы (TFM)](../../standard/frameworks.md) к выходному пути (который определяется свойством [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)). Пакет SDK для .NET автоматически добавляет к выходному пути целевую платформу и идентификатор среды выполнения (если он есть). При установке значения `false` для свойства `AppendTargetFrameworkToOutputPath` TFM не добавляется к выходному пути. Однако при отсутствии TFM в выходном пути несколько артефактов сборки могут перезаписывать друг друга.

Например, при установке следующего параметра выходной путь для приложения .NET 5.0 изменяется с `bin\Debug\net5.0` на `bin\Debug`:

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a>AppendRuntimeIdentifierToOutputPath

Свойство `AppendRuntimeIdentifierToOutputPath` определяет, добавляется ли к выходному пути [идентификатор среды выполнения (RID)](../rid-catalog.md). Пакет SDK для .NET автоматически добавляет к выходному пути целевую платформу и идентификатор среды выполнения (если он есть). При установке значения `false` для свойства `AppendRuntimeIdentifierToOutputPath` RID не добавляется к выходному пути.

Например, при установке следующего параметра выходной путь для приложения .NET 5.0 и идентификатора RID `win10-x64` изменяется с `bin\Debug\net5.0\win10-x64` на `bin\Debug\net5.0`:

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a>CopyLocalLockFileAssemblies

Свойство `CopyLocalLockFileAssemblies` полезно для проектов подключаемых модулей, которые имеют зависимости от других библиотек. Если для этого свойства задано значение `true`, все зависимости пакета NuGet копируются в выходной каталог. Это означает, что вы можете использовать выходные данные `dotnet build` для запуска подключаемого модуля на любом компьютере.

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> Кроме того, можно использовать `dotnet publish` для публикации библиотеки классов. Дополнительные сведения см. в разделе [dotnet publish](../tools/dotnet-publish.md).

### <a name="preservecompilationcontext"></a>PreserveCompilationContext

Свойство `PreserveCompilationContext` позволяет собранному или опубликованному приложению компилировать дополнительный код во время выполнения с теми же параметрами, которые использовались во время сборки. Сборки, ссылки на которые были указаны во время сборки, будут скопированы в подкаталог *ref* выходного каталога. Имена базовых сборок хранятся в файле *.deps.json* приложения вместе с параметрами, передаваемыми компилятору. Эту информацию можно получить с помощью свойств <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> и <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType>.

Эта функциональность в основном используется внутри системы для поддержки компиляции файлов Razor во время выполнения на страницах MVC и Razor ASP.NET Core.

```xml
<PropertyGroup>
  <PreserveCompilationContext>true</PreserveCompilationContext>
</PropertyGroup>
```

### <a name="preservecompilationreferences"></a>PreserveCompilationReferences

Свойство `PreserveCompilationReferences` аналогично свойству [PreserveCompilationContext](#preservecompilationcontext) за исключением того, что при его использовании в каталог публикации копируются только указанные ссылками сборки, но не копируется файл *.deps.json*.

```xml
<PropertyGroup>
  <PreserveCompilationReferences>true</PreserveCompilationReferences>
</PropertyGroup>
```

Дополнительные сведения см. в разделе [Свойства пакета SDK Razor](/aspnet/core/razor-pages/sdk#properties).

### <a name="runtimeidentifier"></a>RuntimeIdentifier

Свойство `RuntimeIdentifier` позволяет указать для проекта один [идентификатор среды выполнения (RID)](../rid-catalog.md). Идентификатор среды выполнения позволяет опубликовать автономное развертывание.

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

Свойство `RuntimeIdentifiers` позволяет указать для проекта список [идентификаторов среды выполнения (RID)](../rid-catalog.md) (в качестве разделителя используется точка с запятой). Используйте это свойство, если вам нужна публикация для нескольких сред. `RuntimeIdentifiers` используется во время восстановления для обеспечения наличия в графе нужных ресурсов.

> [!TIP]
> `RuntimeIdentifier` (в единственном числе) может ускорить создание сборок, когда требуется только одна среда выполнения.

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="useapphost"></a>UseAppHost

Свойство `UseAppHost` контролирует создание собственного исполняемого файла для развертывания. Этот файл требуется для автономных развертываний.

В .NET Core 3.0 и более поздних версиях зависимый от платформы исполняемый файл создается по умолчанию. Задайте свойству `UseAppHost` значение `false`, чтобы отключить создание исполняемого файла.

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

Дополнительные сведения см. в статье о [развертывании приложений .NET](../deploying/index.md).

## <a name="compilation-related-properties"></a>Свойства, связанные с компиляцией

В этом разделе описаны следующие свойства MSBuild:

- [EmbeddedResourceUseDependentUponConvention](#embeddedresourceusedependentuponconvention)
- [LangVersion](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a>EmbeddedResourceUseDependentUponConvention

Свойство `EmbeddedResourceUseDependentUponConvention` определяет, будет ли использоваться информация о типах в исходных файлах, расположенных в одной папке с файлами ресурсов, для создания имен файлов манифеста этих ресурсов. Например, если *Form1.resx* находится в той же папке, что и *Form1.cs*, а `EmbeddedResourceUseDependentUponConvention` имеет значение `true`, то созданному файл *.resources* присваивается имя на основе имени первого типа, определенного в файле *Form1.cs*. Например, если первым типом в файле *Form1.cs* является `MyNamespace.Form1`, созданному файлу присваивается имя *MyNamespace.Form1.resources*.

> [!NOTE]
> Если для `EmbeddedResource` элемента заданы метаданные `LogicalName`, `ManifestResourceName` или `DependentUpon`, то имя файла манифеста для этого файла ресурсов будет создаваться на основе таких метаданных.

По умолчанию для нового проекта .NET этому свойству задается значение `true`. Если задано значение `false` и для элемента `EmbeddedResource` в файле проекта не указаны метаданные `LogicalName`, `ManifestResourceName` или `DependentUpon`, то имя файла манифеста для этого ресурса будет основано на имени корневого пространства имен проекта и относительном пути к файлу *.resx*. Дополнительные сведения об определение имени файла манифеста см. [здесь](../resources/manifest-file-names.md).

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a>LangVersion

Свойство `LangVersion` позволяет указать конкретную версию языка программирования. Например, если требуется доступ к предварительным версиям функций C#, задайте параметру `LangVersion` значение `preview`.

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Дополнительные сведения см. в статье [Управление версиями языка C#](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="default-item-inclusion-properties"></a>Свойства включения элементов по умолчанию

В этом разделе описаны следующие свойства MSBuild:

- [DefaultExcludesInProjectFolder](#defaultexcludesinprojectfolder)
- [DefaultItemExcludes](#defaultitemexcludes)
- [EnableDefaultCompileItems](#enabledefaultcompileitems)
- [EnableDefaultEmbeddedResourceItems](#enabledefaultembeddedresourceitems)
- [EnableDefaultItems](#enabledefaultitems)
- [EnableDefaultNoneItems](#enabledefaultnoneitems)

Дополнительные сведения см. в разделе [Включения и исключения по умолчанию](overview.md#default-includes-and-excludes).

### <a name="defaultitemexcludes"></a>DefaultItemExcludes

Используйте свойство `DefaultItemExcludes`, чтобы определить стандартные маски для файлов и папок, которые должны быть исключены из стандартных масок включения, исключения и удаления. По умолчанию папки *./bin* и *./obj* исключаются из стандартных масок.

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a>DefaultExcludesInProjectFolder

Используйте свойство `DefaultExcludesInProjectFolder`, чтобы определить стандартные маски для файлов и папок в папке проекта, которые должны быть исключены из стандартных масок включения, исключения и удаления. По умолчанию папки, начинающиеся с точки (`.`), такие как *.git* и *.vs*, исключаются из стандартных масок.

Это свойство очень похоже на свойство `DefaultItemExcludes`, за исключением того, что оно учитывает только файлы и папки в папке проекта. Если стандартная маска будет случайно соответствовать элементам за пределами папки проекта с относительным путем, используйте свойство `DefaultExcludesInProjectFolder` вместо свойства `DefaultItemExcludes`.

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a>EnableDefaultItems

Свойство `EnableDefaultItems` определяет, включаются ли в проект неявным образом элементы компиляции, элементы внедренных ресурсов и элементы `None`. Значение по умолчанию — `true`. Задайте значение `false` для свойства `EnableDefaultItems`, чтобы отключить все неявные включения файлов.

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a>EnableDefaultCompileItems

Свойство `EnableDefaultCompileItems` определяет, включаются ли в проект неявным образом элементы компиляции. Значение по умолчанию — `true`. Задайте значение `false` для свойства `EnableDefaultCompileItems`, чтобы отключить неявное включение файлов *.cs и других файлов расширения языка.

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a>EnableDefaultEmbeddedResourceItems

Свойство `EnableDefaultEmbeddedResourceItems` определяет, включаются ли в проект неявным образом элементы внедренных ресурсов. Значение по умолчанию — `true`. Задайте значение `false` для свойства `EnableDefaultEmbeddedResourceItems`, чтобы отключить неявное включение файлов внедренных ресурсов.

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a>EnableDefaultNoneItems

Свойство `EnableDefaultNoneItems` определяет, включаются ли в проект неявным образом элементы `None` (файлы, которые не играют никакой роли в процессе сборки). Значение по умолчанию — `true`. Задайте значение `false` для свойства `EnableDefaultNoneItems`, чтобы отключить неявное включение элементов `None`.

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a>Свойства анализа кода

В этом разделе описаны следующие свойства MSBuild:

- [AnalysisLevel](#analysislevel)
- [AnalysisMode](#analysismode)
- [CodeAnalysisTreatWarningsAsErrors](#codeanalysistreatwarningsaserrors)
- [EnableNETAnalyzers](#enablenetanalyzers)
- [EnforceCodeStyleInBuild](#enforcecodestyleinbuild)

### <a name="analysislevel"></a>AnalysisLevel

Свойство `AnalysisLevel` позволяет указать уровень анализа кода. Например, если требуется доступ к анализаторам кода предварительной версии, задайте для параметра `AnalysisLevel` значение `preview`.

Значение по умолчанию:

- Если проект предназначен для .NET 5.0 или более поздней версии или если вы добавили свойство [AnalysisMode](#analysismode), значением по умолчанию будет `latest`.
- В противном случае это свойство не будет учитываться, если оно явно не добавлено в файл проекта.

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

В следующей таблице приведены доступные параметры.

| Значение | Значение |
|-|-|
| `latest` | Используются новейшие анализаторы кода, которые были выпущены. Это значение по умолчанию. |
| `preview` | Используются новейшие анализаторы кода, даже если они находятся на этапе предварительной версии. |
| `5.0` | Используется набор правил, включенных для выпуска .NET 5.0, даже если доступны новые правила. |
| `5` | Используется набор правил, включенных для выпуска .NET 5.0, даже если доступны новые правила. |

> [!NOTE]
> Это свойство не влияет на анализ кода в проектах, которые не ссылаются на [пакет SDK проекта](overview.md), например, проекты на устаревших платформах .NET Framework, которые ссылаются на пакет NuGet Microsoft.CodeAnalysis.NetAnalyzers.

### <a name="analysismode"></a>AnalysisMode

Начиная с .NET 5.0 пакет SDK для .NET поставляется со всеми [правилами качества кода "CA"](../../fundamentals/code-analysis/quality-rules/index.md). По умолчанию в качестве предупреждений сборки включены только [некоторые правила](../../fundamentals/code-analysis/overview.md#enabled-rules). Свойство `AnalysisMode` позволяет настроить набор правил, включенных по умолчанию. Можно либо переключиться на более агрессивный (неявный) режим анализа, либо более консервативный (явный) режим анализа. Например, если вы хотите включить все правила по умолчанию как предупреждения сборки, установите значение `AllEnabledByDefault`.

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

В следующей таблице приведены доступные параметры.

| Значение | Значение |
|-|-|
| `Default` | Режим по умолчанию, при котором определенные правила включаются в виде предупреждений сборки, некоторые правила включаются в качестве предложений интегрированной среды разработки Visual Studio, а остальные отключаются. |
| `AllEnabledByDefault` | Агрессивный или неявный режим означает, что все правила по умолчанию включены как предупреждения сборки. Вы можете выборочно [отказаться](../../fundamentals/code-analysis/configuration-options.md) от отдельных правил, чтобы отключить их. |
| `AllDisabledByDefault` | Консервативный или явный режим означает, что все правила по умолчанию отключены. Можно выборочно [принять](../../fundamentals/code-analysis/configuration-options.md) отдельные правила, чтобы включить их. |

> [!NOTE]
> Это свойство не влияет на анализ кода в проектах, которые не ссылаются на [пакет SDK проекта](overview.md), например, проекты на устаревших платформах .NET Framework, которые ссылаются на пакет NuGet Microsoft.CodeAnalysis.NetAnalyzers.

### <a name="codeanalysistreatwarningsaserrors"></a>CodeAnalysisTreatWarningsAsErrors

Свойство `CodeAnalysisTreatWarningsAsErrors` позволяет настроить, следует ли обрабатывать предупреждения анализа качества кода (CAxxxx) как предупреждения и прекращать сборку. Если при построении проектов используется флаг `-warnaserror`, предупреждения [анализа качества кода .NET](../../fundamentals/code-analysis/overview.md#code-quality-analysis) также обрабатываются как ошибки. Если вы не хотите, чтобы предупреждения качества кода обрабатывались как ошибки, можно задать для свойства MSBuild `CodeAnalysisTreatWarningsAsErrors` значение `false` в файле проекта.

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a>EnableNETAnalyzers

Для проектов, предназначенных для .NET 5.0 или более поздней версии, по умолчанию включен [анализ качества кода .NET](../../fundamentals/code-analysis/overview.md#code-quality-analysis). Вы можете включить анализ кода .NET для проектов в стиле пакета SDK, предназначенных для более ранних версий .NET, установив для свойства `EnableNETAnalyzers` значение `true`. Чтобы отключить анализ кода в любом проекте, присвойте этому свойству значение `false`.

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!NOTE]
> Это свойство применяется к встроенным анализаторам в пакете SDK для .NET 5+. Его не следует использовать при установке пакета NuGet для анализа кода.

### <a name="enforcecodestyleinbuild"></a>EnforceCodeStyleInBuild

> [!NOTE]
> Эта функция в настоящее время является экспериментальной и может измениться в .NET 6 по сравнению с реализацией в .NET 5.

[Анализ стиля кода .NET](../../fundamentals/code-analysis/overview.md#code-style-analysis) по умолчанию отключен при сборке для всех проектов .NET. Можно включить анализ стиля кода для проектов .NET, задав для свойства `EnforceCodeStyleInBuild` значение `true`.

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

Все правила стиля кода, которые [настроены](../../fundamentals/code-analysis/overview.md#code-style-analysis) как предупреждения или ошибки, будут выполняться при нарушениях сборки и отчета.

## <a name="run-time-configuration-properties"></a>Свойства конфигурации среды выполнения

Вы можете настроить некоторые варианты поведения среды выполнения, указав свойства MSBuild в файле проекта приложения. Сведения о других способах настройки поведения среды выполнения см. в статье о [параметрах конфигурации среды выполнения](../run-time-config/index.md).

- [ConcurrentGarbageCollection](#concurrentgarbagecollection)
- [InvariantGlobalization](#invariantglobalization)
- [RetainVMGarbageCollection](#retainvmgarbagecollection)
- [ServerGarbageCollection](#servergarbagecollection)
- [ThreadPoolMaxThreads](#threadpoolmaxthreads)
- [ThreadPoolMinThreads](#threadpoolminthreads)
- [TieredCompilation](#tieredcompilation)
- [TieredCompilationQuickJit](#tieredcompilationquickjit)
- [TieredCompilationQuickJitForLoops](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a>ConcurrentGarbageCollection

Свойство `ConcurrentGarbageCollection` указывает, включена ли [фоновая (параллельная) сборка мусора](../../standard/garbage-collection/background-gc.md). Задайте значение `false`, чтобы отключить фоновую сборку мусора. Дополнительные сведения см. в разделе [Сборка мусора в фоновом режиме](../run-time-config/garbage-collector.md#background-gc).

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a>InvariantGlobalization

Свойство `InvariantGlobalization` определяет, выполняется ли приложение в *инвариантном режиме глобализации*, что означает, что у него нет доступа к данным, относящимся к языку и региональным параметрам. Установите значение `true` для запуска в инвариантном режиме глобализации. Дополнительные сведения см. в разделе [Инвариантный режим](../run-time-config/globalization.md#invariant-mode).

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a>RetainVMGarbageCollection

Свойство `RetainVMGarbageCollection` настраивает сборщик мусора для помещения удаленных сегментов памяти в список ожидания для будущего использования или освобождения. Значение `true` указывает сборщику мусора разместить сегменты в списке ожидания. Дополнительные сведения см. в разделе [Сохранение виртуальной машины](../run-time-config/garbage-collector.md#retain-vm).

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a>ServerGarbageCollection

Свойство `ServerGarbageCollection` указывает, использует ли приложение [сборку мусора рабочей станции или сборку мусора сервера](../../standard/garbage-collection/workstation-server-gc.md). Задайте значение `true`, чтобы использовать сборку мусора сервера. Дополнительные сведения см. в разделе [Рабочая станция и сервер](../run-time-config/garbage-collector.md#workstation-vs-server).

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a>ThreadPoolMaxThreads

Свойство `ThreadPoolMaxThreads` указывает максимальное число потоков для пула рабочих потоков. Дополнительные сведения см. в разделе [Максимальное число потоков](../run-time-config/threading.md#maximum-threads).

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a>ThreadPoolMinThreads

Свойство `ThreadPoolMinThreads` указывает минимальное число потоков для пула рабочих потоков. Дополнительные сведения см. в разделе [Минимальное число потоков](../run-time-config/threading.md#minimum-threads).

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a>TieredCompilation

Свойство `TieredCompilation` указывает, использует ли JIT-компилятор [многоуровневую компиляцию](../whats-new/dotnet-core-3-0.md#tiered-compilation). Задайте значение `false`, чтобы отключить многоуровневую компиляцию. Дополнительные сведения см. в разделе [Многоуровневая компиляция](../run-time-config/compilation.md#tiered-compilation).

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a>TieredCompilationQuickJit

Свойство `TieredCompilationQuickJit` указывает, использует ли JIT-компилятор быструю JIT-компиляцию. Задайте значение `false`, чтобы отключить быструю JIT-компиляцию. Дополнительные сведения см. в разделе [Быстрая JIT-компиляция](../run-time-config/compilation.md#quick-jit).

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a>TieredCompilationQuickJitForLoops

Свойство `TieredCompilationQuickJitForLoops` указывает, использует ли JIT-компилятор быструю JIT-компиляцию для методов, содержащих циклы. Задайте значение `true`, чтобы включить быструю JIT-компиляцию для методов, содержащих циклы. Дополнительные сведения см. в разделе [Быстрая JIT-компиляция для циклов](../run-time-config/compilation.md#quick-jit-for-loops).

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a>Свойства ссылки

В этом разделе описаны следующие свойства MSBuild:

- [AssetTargetFallback](#assettargetfallback)
- [DisableImplicitFrameworkReferences](#disableimplicitframeworkreferences)
- [Свойства, связанные с восстановлением](#restore-related-properties)

### <a name="assettargetfallback"></a>AssetTargetFallback

Свойство `AssetTargetFallback` позволяет указать дополнительные совместимые версии платформы для ссылок на проекты и пакетов NuGet. Например, если вы указали зависимость пакета с помощью `PackageReference`, но в этом пакете нет ресурсов, совместимых с `TargetFramework` вашего проекта, тогда пригодится свойство `AssetTargetFallback`. Совместимость пакета, на который указывает ссылка, повторно проверяется с помощью каждой целевой платформы, указанной в свойстве `AssetTargetFallback`. Это свойство заменяет устаревшее свойство `PackageTargetFallback`.

В качестве значения свойства `AssetTargetFallback` можно задать одну [версию целевой платформы](../../standard/frameworks.md#supported-target-frameworks) или несколько.

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a>DisableImplicitFrameworkReferences

Свойство `DisableImplicitFrameworkReferences` управляет неявными элементами `FrameworkReference` при разработке для .NET Core 3.0 и более поздних версий. При использовании .NET Core 2.1 или .NET Standard 2.0 и более ранних версий оно управляет неявными элементами [PackageReference](#packagereference) в пакетах в метапакете. (Метапакет — это пакет на основе платформы, который состоит только из зависимостей от других пакетов.) Это свойство также управляет неявными ссылками, такими как `System` и `System.Core`, при разработке для .NET Framework.

Присвойте этому свойству значение `true`, чтобы отключить неявные элементы `FrameworkReference` или [PackageReference](#packagereference). Если этому свойству присвоено значение `true`, можно добавить явные ссылки на только необходимые платформы или пакеты.

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="restore-related-properties"></a>Свойства, связанные с восстановлением

При восстановлении пакета, на который указывает ссылка, устанавливаются все его прямые зависимости и все зависимости этих зависимостей. Можно настроить восстановление пакетов, указав такие свойства, как `RestorePackagesPath` и `RestoreIgnoreFailedSources`. Дополнительные сведения об этих и других свойствах см. в разделе [целевой объект восстановления](/nuget/reference/msbuild-targets#restore-target).

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-related-properties"></a>Свойства, связанные с запуском

Следующие свойства используются для запуска приложения с помощью команды [`dotnet run`](../tools/dotnet-run.md):

- [RunArguments](#runarguments)
- [RunWorkingDirectory](#runworkingdirectory)

### <a name="runarguments"></a>RunArguments

Свойство `RunArguments` определяет аргументы, которые передаются в приложение при его запуске.

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> Можно указать дополнительные аргументы для передачи в приложение с помощью параметра [`--` для `dotnet run`](../tools/dotnet-run.md#options).

### <a name="runworkingdirectory"></a>RunWorkingDirectory

Свойство `RunWorkingDirectory` определяет рабочий каталог для запуска процесса приложения. Это может быть абсолютный путь или путь относительно каталога проекта. Если каталог не указан, в качестве рабочего каталога используется `OutDir`.

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-related-properties"></a>Свойства, связанные с размещением

В этом разделе описаны следующие свойства MSBuild:

- [EnableComHosting](#enablecomhosting)
- [EnableDynamicLoading](#enabledynamicloading)

### <a name="enablecomhosting"></a>EnableComHosting

Свойство `EnableComHosting` указывает, что сборка предоставляет сервер COM. Установка `EnableComHosting` в `true` также подразумевает, что [EnableDynamicLoading](#enabledynamicloading) — `true`.

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

Дополнительные сведения см. в разделе [Предоставление компонентов .NET для COM](../native-interop/expose-components-to-com.md).

### <a name="enabledynamicloading"></a>EnableDynamicLoading

Свойство `EnableDynamicLoading` указывает, что сборка является динамически загружаемым компонентом. Компонентом может быть [библиотека COM](/windows/win32/com/the-component-object-model) или библиотека, не относящаяся к COM, которую можно [использовать из собственного узла](../tutorials/netcore-hosting.md). Если присвоить этому свойству значения `true`:

- Создается файл *runtimeconfig.json*.
- [Накат](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) получает значение `LatestMinor`.
- Ссылки NuGet копируются локально.

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="items"></a>Элементы

[Элементы MSBuild](/visualstudio/msbuild/msbuild-items) — это входные данные для системы сборки. Элементы указываются в соответствии с их типом, который является именем элемента. Например, `Compile` и `Reference` — [два распространенных типа элементов](/visualstudio/msbuild/common-msbuild-project-items). Пакет SDK для .NET предоставляет следующие дополнительные типы элементов:

- [PackageReference](#packagereference)
- [TrimmerRootAssembly](#trimmerrootassembly)

Для этих элементов можно использовать любой из стандартных [атрибутов элемента](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), например `Include` и `Update`. Чтобы добавить новый элемент, используйте `Include`. Для изменения существующего элемента используйте `Update`. Например, `Update` часто используется для изменения элемента, который неявно был добавлен пакетом SDK для .NET.

### <a name="packagereference"></a>PackageReference

Элемент `PackageReference` определяет ссылку на пакет NuGet.

Атрибут `Include` указывает идентификатор пакета. Атрибут `Version` указывает версию или диапазон версий. Сведения о том, как указать минимальную версию, максимальную версию, диапазон или точное соответствие, см. в разделе [Диапазоны версий](/nuget/concepts/package-versioning#version-ranges).

Фрагмент файла проекта в следующем примере ссылается на пакет [System.Runtime](https://www.nuget.org/packages/System.Runtime/).

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

Также можно [управлять ресурсами зависимостей](/nuget/consume-packages/package-references-in-project-files#controlling-dependency-assets) с помощью таких метаданных, как `PrivateAssets`.

```xml
<ItemGroup>
  <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0">
    <PrivateAssets>all</PrivateAssets>
  </PackageReference>
</ItemGroup>
```

Дополнительные сведения см. в статье [Ссылки на пакеты в файлах проекта](/nuget/consume-packages/package-references-in-project-files).

### <a name="trimmerrootassembly"></a>TrimmerRootAssembly

Элемент `TrimmerRootAssembly` позволяет исключить сборку из [*обрезки*](../deploying/trim-self-contained.md). Обрезка — это процесс удаления неиспользуемых частей среды выполнения из упакованного приложения. В некоторых случаях при обрезке могут неправильно удаляться необходимые ссылки.

Следующий код XML исключает сборку `System.Security` из обрезки.

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="item-metadata"></a>Метаданные элементов

Помимо стандартных [атрибутов элемента MSBuild](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), в пакете SDK для .NET доступны следующие теги метаданных элементов:

- [CopyToPublishDirectory](#copytopublishdirectory)
- [LinkBase](#linkbase)

### <a name="copytopublishdirectory"></a>CopyToPublishDirectory

Метаданные `CopyToPublishDirectory` в элементах управления MSBuild, когда элемент копируется в каталог публикации. Допустимые значения: `PreserveNewest`, при котором копируется только элемент, если он был изменен, `Always`, при котором всегда копируется элемент, и `Never`, при котором элемент никогда не копируется. С точки зрения производительности `PreserveNewest` предпочтительнее, поскольку включает инкрементную сборку.

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a>LinkBase

Для элемента, находящегося за пределами каталога проекта и его подкаталогов, целевой объект публикации использует [метаданные Link](/visualstudio/msbuild/common-msbuild-item-metadata) элемента, чтобы определить, куда копировать элемент. `Link` также определяет, как элементы за пределами дерева проекта отображаются в окне обозревателя решений Visual Studio.

Если для элемента, находящегося за пределами проекта, `Link` не указан, по умолчанию используется `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`. `LinkBase` позволяет указать допустимую базовую папку для элементов за пределами проекта. Иерархия папок в базовой папке обеспечивается с помощью `RecursiveDir`. Если параметр `LinkBase` не указан, он опускается в пути `Link`.

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

На следующем рисунке показано, как файл, который включен с помощью стандартной маски предыдущего элемента `Include`, отображается в обозревателе решений.

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="Обозреватель решений: элемент с метаданными LinkBase.":::

## <a name="see-also"></a>См. также

- [Справочник по схеме MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Общие свойства MSBuild](/visualstudio/msbuild/common-msbuild-project-properties)
- [Свойства MSBuild для целевого объекта pack NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Свойства MSBuild для целевого объекта restore NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Настройка сборки](/visualstudio/msbuild/customize-your-build)
