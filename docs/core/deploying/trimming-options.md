---
title: Параметры обрезки
description: Узнайте, как управлять обрезкой автономных приложений.
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: 93fee991cf218a52ad1d9a2597b1c9b2d442110a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874255"
---
# <a name="trimming-options"></a><span data-ttu-id="3f26f-103">Параметры обрезки</span><span class="sxs-lookup"><span data-stu-id="3f26f-103">Trimming options</span></span>

<span data-ttu-id="3f26f-104">Следующие свойства и элементы MSBuild влияют на поведение [обрезанных автономных развертываний](trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="3f26f-104">The following MSBuild properties and items influence the behavior of [trimmed self-contained deployments](trim-self-contained.md).</span></span> <span data-ttu-id="3f26f-105">Некоторые параметры упоминают `ILLink`, то есть имя базового инструмента, реализующего обрезку.</span><span class="sxs-lookup"><span data-stu-id="3f26f-105">Some of the options mention `ILLink`, which is the name of the underlying tool that implements trimming.</span></span> <span data-ttu-id="3f26f-106">Дополнительные сведения о базовом средстве можно найти в [документации по компоновщику](https://github.com/mono/linker/tree/master/docs).</span><span class="sxs-lookup"><span data-stu-id="3f26f-106">More information about the underlying tool can be found at the [Linker documentation](https://github.com/mono/linker/tree/master/docs).</span></span>

## <a name="enable-trimming"></a><span data-ttu-id="3f26f-107">Включение обрезки</span><span class="sxs-lookup"><span data-stu-id="3f26f-107">Enable trimming</span></span>

- `<PublishTrimmed>true</PublishTrimmed>`

   <span data-ttu-id="3f26f-108">Включите обрезку во время публикации с параметрами по умолчанию, определенными пакетом SDK.</span><span class="sxs-lookup"><span data-stu-id="3f26f-108">Enable trimming during publish, with the default settings defined by the SDK.</span></span>

<span data-ttu-id="3f26f-109">При использовании `Microsoft.NET.Sdk` выполняется обрезка сборок платформы из пакета среды выполнения netcoreapp на уровне сборки.</span><span class="sxs-lookup"><span data-stu-id="3f26f-109">When using `Microsoft.NET.Sdk`, this will perform assembly-level trimming of the framework assemblies from the netcoreapp runtime pack.</span></span> <span data-ttu-id="3f26f-110">Код приложения и библиотеки, отличные от платформы, не обрезаются.</span><span class="sxs-lookup"><span data-stu-id="3f26f-110">Application code and non-framework libraries are not trimmed.</span></span> <span data-ttu-id="3f26f-111">Другие пакеты SDK могут определять разные значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3f26f-111">Other SDKs may define different defaults.</span></span>

## <a name="trimming-granularity"></a><span data-ttu-id="3f26f-112">Степень детализации обрезки</span><span class="sxs-lookup"><span data-stu-id="3f26f-112">Trimming granularity</span></span>

<span data-ttu-id="3f26f-113">Следующие параметры степени детализации управляют тем, насколько агрессивно отбрасываются неиспользуемые IL.</span><span class="sxs-lookup"><span data-stu-id="3f26f-113">The following granularity settings control how aggressively unused IL is discarded.</span></span> <span data-ttu-id="3f26f-114">Это можно задать как свойство или как метаданные в [отдельной сборке](#trimmed-assemblies).</span><span class="sxs-lookup"><span data-stu-id="3f26f-114">This can be set as a property, or as metadata on an [individual assembly](#trimmed-assemblies).</span></span>

- `<TrimMode>copyused</TrimMode>`

   <span data-ttu-id="3f26f-115">Включите функцию обрезки на уровне сборки, которая сохранит всю сборку, если какая-либо ее часть используется (статически понятным образом).</span><span class="sxs-lookup"><span data-stu-id="3f26f-115">Enable assembly-level trimming, which will keep an entire assembly if any part of it is used (in a statically understood way).</span></span>

- `<TrimMode>link</TrimMode>`

    <span data-ttu-id="3f26f-116">Включите функцию обрезки на уровне элементов, которая удаляет неиспользуемые элементы из типов.</span><span class="sxs-lookup"><span data-stu-id="3f26f-116">Enable member-level trimming, which removes unused members from types.</span></span>

<span data-ttu-id="3f26f-117">Сборки с метаданными `<IsTrimmable>true</IsTrimmable>`, но без явного `TrimMode` будут использовать глобальную `TrimMode`.</span><span class="sxs-lookup"><span data-stu-id="3f26f-117">Assemblies with `<IsTrimmable>true</IsTrimmable>` metadata but no explicit `TrimMode` will use the global `TrimMode`.</span></span> <span data-ttu-id="3f26f-118">`TrimMode` по умолчанию для `Microsoft.NET.Sdk` — `copyused`.</span><span class="sxs-lookup"><span data-stu-id="3f26f-118">The default `TrimMode` for `Microsoft.NET.Sdk` is `copyused`.</span></span>

## <a name="trimmed-assemblies"></a><span data-ttu-id="3f26f-119">Обрезанные сборки</span><span class="sxs-lookup"><span data-stu-id="3f26f-119">Trimmed assemblies</span></span>

<span data-ttu-id="3f26f-120">При публикации обрезанного приложения пакет SDK выдает `ItemGroup` с именем `ManagedAssemblyToLink`, который представляет набор файлов для обработки обрезки.</span><span class="sxs-lookup"><span data-stu-id="3f26f-120">When publishing a trimmed app, the SDK computes an `ItemGroup` called `ManagedAssemblyToLink` that represents the set of files to be processed for trimming.</span></span> <span data-ttu-id="3f26f-121">`ManagedAssemblyToLink` может иметь метаданные, управляющие поведением обрезки для каждой сборки.</span><span class="sxs-lookup"><span data-stu-id="3f26f-121">`ManagedAssemblyToLink` may have metadata that controls the trimming behavior per assembly.</span></span> <span data-ttu-id="3f26f-122">Чтобы задать эти метаданные, создайте целевой объект, выполняемый перед встроенным целевым объектом `PrepareForILLink`.</span><span class="sxs-lookup"><span data-stu-id="3f26f-122">To set this metadata, create a target that runs before the built-in `PrepareForILLink` target.</span></span> <span data-ttu-id="3f26f-123">В следующем примере показано, как включить обрезку `MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="3f26f-123">The following example shows how to enable trimming of `MyAssembly`.</span></span>

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

<span data-ttu-id="3f26f-124">Не добавляйте и не удаляйте элементы в `ManagedAssemblyToLink`, так как пакет SDK рассчитывает этот набор во время публикации и полагает, что он не изменяется.</span><span class="sxs-lookup"><span data-stu-id="3f26f-124">Do not add or remove items to/from `ManagedAssemblyToLink`, because the SDK computes this set during publish and expects it not to change.</span></span> <span data-ttu-id="3f26f-125">Поддерживаются следующие метаданные.</span><span class="sxs-lookup"><span data-stu-id="3f26f-125">The supported metadata is:</span></span>

- `<IsTrimmable>true</IsTrimmable>`

  <span data-ttu-id="3f26f-126">Управление тем, обрезана ли данная сборка.</span><span class="sxs-lookup"><span data-stu-id="3f26f-126">Control whether the given assembly is trimmed.</span></span>

- <span data-ttu-id="3f26f-127">`<TrimMode>copyused</TrimMode>` или `<TrimMode>link</TrimMode>`</span><span class="sxs-lookup"><span data-stu-id="3f26f-127">`<TrimMode>copyused</TrimMode>` or `<TrimMode>link</TrimMode>`</span></span>

  <span data-ttu-id="3f26f-128">Управление [степенью детализации](#trimming-granularity) этой сборки.</span><span class="sxs-lookup"><span data-stu-id="3f26f-128">Control the [trimming granularity](#trimming-granularity) of this assembly.</span></span> <span data-ttu-id="3f26f-129">Имеет приоритет над глобальным `TrimMode`.</span><span class="sxs-lookup"><span data-stu-id="3f26f-129">This takes precedence over the global `TrimMode`.</span></span> <span data-ttu-id="3f26f-130">Установка `TrimMode` для сборки подразумевает `<IsTrimmable>true</IsTrimmable>`.</span><span class="sxs-lookup"><span data-stu-id="3f26f-130">Setting `TrimMode` on an assembly implies `<IsTrimmable>true</IsTrimmable>`.</span></span>

## <a name="root-assemblies"></a><span data-ttu-id="3f26f-131">Корневые сборки</span><span class="sxs-lookup"><span data-stu-id="3f26f-131">Root assemblies</span></span>

<span data-ttu-id="3f26f-132">Все сборки без `<IsTrimmable>true</IsTrimmable>` считаются корневыми для анализа. Это означает, что они будут сохранены со всеми своими статически понятными зависимостями.</span><span class="sxs-lookup"><span data-stu-id="3f26f-132">All assemblies that do not have `<IsTrimmable>true</IsTrimmable>` are considered roots for the analysis, which means that they and all of their statically understood dependencies will be kept.</span></span> <span data-ttu-id="3f26f-133">Дополнительные сборки могут быть корневыми по имени (без расширения `.dll`).</span><span class="sxs-lookup"><span data-stu-id="3f26f-133">Additional assemblies may be "rooted" by name (without the `.dll` extension):</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a><span data-ttu-id="3f26f-134">Корневые дескрипторы</span><span class="sxs-lookup"><span data-stu-id="3f26f-134">Root descriptors</span></span>

<span data-ttu-id="3f26f-135">Другой способ указания корней для анализа — использование XML-файла, в котором используется компоновщик [формата дескриптора](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format).</span><span class="sxs-lookup"><span data-stu-id="3f26f-135">Another way to specify roots for analysis is using an XML file that uses the linker [descriptor format](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format).</span></span> <span data-ttu-id="3f26f-136">Это позволяет использовать корневые члены вместо целой сборки.</span><span class="sxs-lookup"><span data-stu-id="3f26f-136">This lets you root specific members instead of a whole assembly.</span></span>

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

<span data-ttu-id="3f26f-137">Например, `MyRoots.xml` может быть корневым для конкретного метода, к которому приложение обращается динамически.</span><span class="sxs-lookup"><span data-stu-id="3f26f-137">For example, `MyRoots.xml` might root a specific method that is dynamically accessed by the application:</span></span>

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a><span data-ttu-id="3f26f-138">Предупреждения при анализе</span><span class="sxs-lookup"><span data-stu-id="3f26f-138">Analysis warnings</span></span>

<span data-ttu-id="3f26f-139">Обрезка приведет к удалению IL, который не является статически достижимым.</span><span class="sxs-lookup"><span data-stu-id="3f26f-139">Trimming will remove IL that is not statically reachable.</span></span> <span data-ttu-id="3f26f-140">Приложения, использующие отражение или другие шаблоны, которые создают динамические зависимости, могут быть разорваны путем обрезки.</span><span class="sxs-lookup"><span data-stu-id="3f26f-140">Apps that use reflection or other patterns that create dynamic dependencies may be broken by trimming.</span></span> <span data-ttu-id="3f26f-141">Чтобы получать предупреждения об этих шаблонах, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="3f26f-141">To warn about such patterns:</span></span>

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    <span data-ttu-id="3f26f-142">Включите предупреждения при анализе обрезки.</span><span class="sxs-lookup"><span data-stu-id="3f26f-142">Enable trim analysis warnings.</span></span>

<span data-ttu-id="3f26f-143">Сюда будут включены предупреждения обо всем приложении, включая собственный код, код библиотеки и код платформы.</span><span class="sxs-lookup"><span data-stu-id="3f26f-143">This will include warnings about the entire app, including your own code, library code, and framework code.</span></span>

## <a name="warning-versions"></a><span data-ttu-id="3f26f-144">Версии предупреждений</span><span class="sxs-lookup"><span data-stu-id="3f26f-144">Warning versions</span></span>

<span data-ttu-id="3f26f-145">При анализе обрезки учитывается свойство [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel), которое управляет версией предупреждений при анализе для пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="3f26f-145">Trim analysis respects the [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) property that controls the version of analysis warnings across the SDK.</span></span> <span data-ttu-id="3f26f-146">Существует еще одно свойство, которое управляет версией предупреждений при анализе обрезки независимо (аналогично `WarningLevel` для компилятора).</span><span class="sxs-lookup"><span data-stu-id="3f26f-146">There is another property that controls the version of trim analysis warnings independently (similar to `WarningLevel` for the compiler):</span></span>

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    <span data-ttu-id="3f26f-147">Настройте отображение только предупреждений заданного или нижнего уровня.</span><span class="sxs-lookup"><span data-stu-id="3f26f-147">Emit only warnings of the given level or lower.</span></span> <span data-ttu-id="3f26f-148">Это может быть `9999` для включения всех версий предупреждений.</span><span class="sxs-lookup"><span data-stu-id="3f26f-148">This can be `9999` to include all warning versions.</span></span>

## <a name="suppressing-warnings"></a><span data-ttu-id="3f26f-149">Подавление предупреждений</span><span class="sxs-lookup"><span data-stu-id="3f26f-149">Suppressing warnings</span></span>

<span data-ttu-id="3f26f-150">Отдельные [коды предупреждений](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) можно подавлять с помощью стандартных свойств MSBuild, которые учитываются цепочкой инструментов, включая `NoWarn`, `WarningsAsErrors`, `WarningsNotAsErrors` и `TreatWarningsAsErrors`.</span><span class="sxs-lookup"><span data-stu-id="3f26f-150">Individual [warning codes](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) can be suppressed using the usual MSBuild properties respected by the toolchain, including `NoWarn`, `WarningsAsErrors`, `WarningsNotAsErrors`, and `TreatWarningsAsErrors`.</span></span> <span data-ttu-id="3f26f-151">Существует дополнительный параметр, который управляет поведением предупреждения как ошибки ILLink отдельно.</span><span class="sxs-lookup"><span data-stu-id="3f26f-151">There is an additional option that controls the ILLink warn-as-error behavior independently:</span></span>

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    <span data-ttu-id="3f26f-152">Не обрабатывайте предупреждения ILLink как ошибки.</span><span class="sxs-lookup"><span data-stu-id="3f26f-152">Don't treat ILLink warnings as errors.</span></span> <span data-ttu-id="3f26f-153">Это может быть полезно, чтобы не включать предупреждения при анализе обрезки в ошибки при обработке предупреждений компилятора как ошибок в глобальном масштабе.</span><span class="sxs-lookup"><span data-stu-id="3f26f-153">This may be useful to avoid turning trim analysis warnings into errors when treating compiler warnings as errors globally.</span></span>

## <a name="removing-symbols"></a><span data-ttu-id="3f26f-154">Удаление символов</span><span class="sxs-lookup"><span data-stu-id="3f26f-154">Removing symbols</span></span>

<span data-ttu-id="3f26f-155">Символы, как правило, усекаются, чтобы соответствовать обрезанным сборкам.</span><span class="sxs-lookup"><span data-stu-id="3f26f-155">Symbols will normally be trimmed to match the trimmed assemblies.</span></span> <span data-ttu-id="3f26f-156">Можно также удалить все символы.</span><span class="sxs-lookup"><span data-stu-id="3f26f-156">You can also remove all symbols:</span></span>

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    <span data-ttu-id="3f26f-157">Удалите символы из обрезанного приложения, включая внедренные PDB-файлы и отдельные PDB.</span><span class="sxs-lookup"><span data-stu-id="3f26f-157">Remove symbols from the trimmed application, including embedded PDBs and separate PDB files.</span></span> <span data-ttu-id="3f26f-158">Это относится как к коду приложения, так и к любым зависимостям, которые входят в состав символов.</span><span class="sxs-lookup"><span data-stu-id="3f26f-158">This applies to both the application code and any dependencies that come with symbols.</span></span>

<span data-ttu-id="3f26f-159">Пакет SDK также позволяет отключить поддержку отладчика, используя свойство `DebuggerSupport`.</span><span class="sxs-lookup"><span data-stu-id="3f26f-159">The SDK also makes it possible to disable debugger support using the property `DebuggerSupport`.</span></span> <span data-ttu-id="3f26f-160">Если поддержка отладчика отключена, то при обрезке символы автоматически удаляются (`TrimmerRemoveSymbols` по умолчанию принимает значение true).</span><span class="sxs-lookup"><span data-stu-id="3f26f-160">When debugger support is disabled, trimming will remove symbols automatically (`TrimmerRemoveSymbols` will default to true).</span></span>

## <a name="trimming-framework-library-features"></a><span data-ttu-id="3f26f-161">Усечение функций библиотеки инфраструктуры</span><span class="sxs-lookup"><span data-stu-id="3f26f-161">Trimming framework library features</span></span>

<span data-ttu-id="3f26f-162">Несколько функциональных возможностей библиотек платформы поставляются с директивами компоновщика, которые позволяют удалить код для отключенных функций.</span><span class="sxs-lookup"><span data-stu-id="3f26f-162">Several feature areas of the framework libraries come with linker directives that make it possible to remove the code for disabled features.</span></span>

- `<DebuggerSupport>false</DebuggerSupport>`

    <span data-ttu-id="3f26f-163">Удалите код, обеспечивающий лучшую отладку.</span><span class="sxs-lookup"><span data-stu-id="3f26f-163">Remove code that enables better debugging experiences.</span></span> <span data-ttu-id="3f26f-164">Это также приведет к [удалению символов](#removing-symbols).</span><span class="sxs-lookup"><span data-stu-id="3f26f-164">This will also [remove symbols](#removing-symbols).</span></span>

- `<EnableUnsafeBinaryFormatterSerialization>false</EnableUnsafeBinaryFormatterSerialization>`

    <span data-ttu-id="3f26f-165">Удалите поддержку сериализации BinaryFormatter.</span><span class="sxs-lookup"><span data-stu-id="3f26f-165">Remove BinaryFormatter serialization support.</span></span> <span data-ttu-id="3f26f-166">Дополнительные сведения см. в разделе [Методы сериализации BinaryFormatter устарели](../compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete.md).</span><span class="sxs-lookup"><span data-stu-id="3f26f-166">For more information, see [BinaryFormatter serialization methods are obsolete](../compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete.md).</span></span>

- `<EnableUnsafeUTF7Encoding>false</EnableUnsafeUTF7Encoding>`

    <span data-ttu-id="3f26f-167">Удалите небезопасный код кодировки UTF-7.</span><span class="sxs-lookup"><span data-stu-id="3f26f-167">Remove insecure UTF-7 encoding code.</span></span> <span data-ttu-id="3f26f-168">Дополнительные сведения см. в разделе [Пути к коду в кодировке UTF-7 устарели](../compatibility/core-libraries/5.0/utf-7-code-paths-obsolete.md).</span><span class="sxs-lookup"><span data-stu-id="3f26f-168">For more information, see [UTF-7 code paths are obsolete](../compatibility/core-libraries/5.0/utf-7-code-paths-obsolete.md).</span></span>

- `<EventSourceSupport>false</EventSourceSupport>`

    <span data-ttu-id="3f26f-169">Удалите код или логику, связанную с EventSource.</span><span class="sxs-lookup"><span data-stu-id="3f26f-169">Remove EventSource related code or logic.</span></span>

- `<HttpActivityPropagationSupport>false</HttpActivityPropagationSupport>`

    <span data-ttu-id="3f26f-170">Удалите код, связанный с поддержкой диагностики для System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="3f26f-170">Remove code related to diagnostics support for System.Net.Http.</span></span>

- `<InvariantGlobalization>true</InvariantGlobalization>`

    <span data-ttu-id="3f26f-171">Удалите код и данные, связанные с глобализацией.</span><span class="sxs-lookup"><span data-stu-id="3f26f-171">Remove globalization specific code and data.</span></span> <span data-ttu-id="3f26f-172">Дополнительные сведения см. в разделе [Инвариантный режим](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="3f26f-172">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

- `<UseSystemResourceKeys>true</UseSystemResourceKeys>`

    <span data-ttu-id="3f26f-173">Удалите сообщения об исключениях для сборок `System.*`.</span><span class="sxs-lookup"><span data-stu-id="3f26f-173">Strip exception messages for `System.*` assemblies.</span></span> <span data-ttu-id="3f26f-174">При возникновении исключения из сборки `System.*` сообщение будет содержать упрощенный идентификатор ресурса вместо полного сообщения.</span><span class="sxs-lookup"><span data-stu-id="3f26f-174">When an exception is thrown from a `System.*` assembly, the message will be a simplified resource ID instead of the full message.</span></span>

 <span data-ttu-id="3f26f-175">Эти свойства приведут к усечению связанного кода, а также к отключению функций через файл [runtimeconfig](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f26f-175">These properties will cause the related code to be trimmed and will also disable features via the [runtimeconfig](../run-time-config/index.md) file.</span></span> <span data-ttu-id="3f26f-176">Дополнительные сведения об этих свойствах, включая соответствующие параметры runtimeconfig, см. в разделе, посвященном [переключению функций](https://github.com/dotnet/runtime/blob/main/docs/workflow/trimming/feature-switches.md).</span><span class="sxs-lookup"><span data-stu-id="3f26f-176">For more information about these properties, including the corresponding runtimeconfig options, see [feature switches](https://github.com/dotnet/runtime/blob/main/docs/workflow/trimming/feature-switches.md).</span></span> <span data-ttu-id="3f26f-177">Некоторые пакеты SDK могут иметь значения по умолчанию для этих свойств.</span><span class="sxs-lookup"><span data-stu-id="3f26f-177">Some SDKs may have default values for these properties.</span></span>
