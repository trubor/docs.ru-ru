---
title: Пример миграции на .NET Core 3.1
description: Показано, как перенести примеры приложений, предназначенных для .NET Framework в .NET Core 3,1.
ms.date: 05/12/2020
ms.openlocfilehash: 6a0311e9aaeb25ac39f3394d3a62e17046fe03d8
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "97866779"
---
# <a name="example-of-migrating-to-net-core-31"></a><span data-ttu-id="dc28c-103">Пример миграции на .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="dc28c-103">Example of migrating to .NET Core 3.1</span></span>

<span data-ttu-id="dc28c-104">В этой главе представлены практические рекомендации, которые помогут выполнить миграцию существующего приложения из .NET Framework в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-104">In this chapter, we present practical guidelines to help you perform a migration of your existing application from .NET Framework to .NET Core.</span></span>

<span data-ttu-id="dc28c-105">Мы представим хорошо структурированный процесс, который вы можете отслеживать, а также наиболее важные моменты, которые следует учитывать на каждом шаге.</span><span class="sxs-lookup"><span data-stu-id="dc28c-105">We present a well-structured process you can follow and the most important things to consider on each step.</span></span>

<span data-ttu-id="dc28c-106">Затем мы задокументировани пошаговый процесс миграции для примера классического приложения как из версий WinForms, так и для WPF.</span><span class="sxs-lookup"><span data-stu-id="dc28c-106">We then document a step-by-step migration process for a sample desktop application, both from WinForms and WPF versions.</span></span>

## <a name="migration-process-overview"></a><span data-ttu-id="dc28c-107">Общие сведения о процессе миграции</span><span class="sxs-lookup"><span data-stu-id="dc28c-107">Migration process overview</span></span>

<span data-ttu-id="dc28c-108">Процесс миграции состоит из четырех последовательных шагов:</span><span class="sxs-lookup"><span data-stu-id="dc28c-108">The migration process consists of four sequential steps:</span></span>

1. <span data-ttu-id="dc28c-109">**Подготовка**. Изучите зависимости, которые проект должен иметь представление о дальнейших действиях.</span><span class="sxs-lookup"><span data-stu-id="dc28c-109">**Preparation**: Understand the dependencies the project has to have an idea of what's ahead.</span></span> <span data-ttu-id="dc28c-110">На этом шаге вы переведите текущий проект в состояние, которое упрощает точку запуска для миграции.</span><span class="sxs-lookup"><span data-stu-id="dc28c-110">In this step, you take the current project into a state that simplifies the startup point for the migration.</span></span>

2. <span data-ttu-id="dc28c-111">**Миграция файла проекта.** в проектах .NET Core используется новый формат проекта в стиле SDK.</span><span class="sxs-lookup"><span data-stu-id="dc28c-111">**Migrate Project File:** .NET Core projects use the new SDK-style project format.</span></span> <span data-ttu-id="dc28c-112">Создайте новый файл проекта с этим форматом или обновите его, чтобы использовать стиль пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="dc28c-112">Create a new project file with this format or update the one you have to use the SDK style.</span></span>

3. <span data-ttu-id="dc28c-113">**Исправление кода и сборки:** Создание кода в .NET Core различие между .NET Framework и .NET Core различается на уровне API.</span><span class="sxs-lookup"><span data-stu-id="dc28c-113">**Fix code and build:** Build the code in .NET Core addressing API-level differences between .NET Framework and .NET Core.</span></span> <span data-ttu-id="dc28c-114">При необходимости обновите сторонние пакеты до тех, которые поддерживают .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-114">If needed, update third-party packages to the ones that support .NET Core.</span></span>

4. <span data-ttu-id="dc28c-115">**Запуск и тестирование:** Могут возникнуть различия, которые не отображаются до времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="dc28c-115">**Run and test:** There might be differences that don't show up until run time.</span></span> <span data-ttu-id="dc28c-116">Поэтому не забудьте запустить приложение и проверить, что все работает правильно.</span><span class="sxs-lookup"><span data-stu-id="dc28c-116">So, don't forget to run the application and test that everything works as expected.</span></span>

### <a name="preparation"></a><span data-ttu-id="dc28c-117">Подготовка</span><span class="sxs-lookup"><span data-stu-id="dc28c-117">Preparation</span></span>

#### <a name="migrate-packagesconfig-file"></a><span data-ttu-id="dc28c-118">Миграция файла packages.config</span><span class="sxs-lookup"><span data-stu-id="dc28c-118">Migrate packages.config file</span></span>

<span data-ttu-id="dc28c-119">В .NET Framework приложении все ссылки на внешние пакеты объявляются в файле *packages.config* .</span><span class="sxs-lookup"><span data-stu-id="dc28c-119">In a .NET Framework application, all references to external packages are declared in the *packages.config* file.</span></span> <span data-ttu-id="dc28c-120">В .NET Core больше не нужно использовать файл *packages.config* .</span><span class="sxs-lookup"><span data-stu-id="dc28c-120">In .NET Core, there's no longer the need to use the *packages.config* file.</span></span> <span data-ttu-id="dc28c-121">Вместо этого используйте свойство [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) в файле проекта, чтобы указать пакеты NuGet для приложения.</span><span class="sxs-lookup"><span data-stu-id="dc28c-121">Instead, use the [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) property inside the project file to specify the NuGet packages for your app.</span></span>

<span data-ttu-id="dc28c-122">Поэтому необходимо перейти от одного формата к другому.</span><span class="sxs-lookup"><span data-stu-id="dc28c-122">So, you need to transition from one format to another.</span></span> <span data-ttu-id="dc28c-123">Обновление можно выполнить вручную, используя зависимости, содержащиеся в файле *packages.config* , и перенести их в файл проекта в `PackageReference` формате.</span><span class="sxs-lookup"><span data-stu-id="dc28c-123">You can do the update manually, taking the dependencies contained in the *packages.config* file and migrating them to the project file with the `PackageReference` format.</span></span> <span data-ttu-id="dc28c-124">Вы также можете позволить Visual Studio выполнить свою работу: щелкните правой кнопкой мыши файл *packages.config* и выберите пункт **перенести packages.config в PackageReference** .</span><span class="sxs-lookup"><span data-stu-id="dc28c-124">Or, you can let Visual Studio do the work for you: right-click on the *packages.config* file and select the **Migrate packages.config to PackageReference** option.</span></span>

#### <a name="verify-every-dependency-compatibility-in-net-core"></a><span data-ttu-id="dc28c-125">Проверка каждой совместимости зависимостей в .NET Core</span><span class="sxs-lookup"><span data-stu-id="dc28c-125">Verify every dependency compatibility in .NET Core</span></span>

<span data-ttu-id="dc28c-126">После переноса ссылок на пакеты необходимо проверить каждую ссылку на совместимость.</span><span class="sxs-lookup"><span data-stu-id="dc28c-126">Once you've migrated the package references, you must check each reference for compatibility.</span></span> <span data-ttu-id="dc28c-127">Вы можете исследовать зависимости каждого пакета NuGet, используемого приложением в [NuGet.org](https://www.nuget.org/). Если пакет имеет .NET Standard зависимости, он будет работать в .NET Core, так как .NET Core 3,1 [поддерживает](../../standard/net-standard.md#net-implementation-support) все версии .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="dc28c-127">You can explore the dependencies of each NuGet package your application is using on [nuget.org](https://www.nuget.org/). If the package has .NET Standard dependencies, then it's going to work on .NET Core because .NET Core 3.1 [supports](../../standard/net-standard.md#net-implementation-support) all versions of .NET Standard.</span></span> <span data-ttu-id="dc28c-128">На следующем рисунке показаны зависимости для `Castle.Windsor` пакета.</span><span class="sxs-lookup"><span data-stu-id="dc28c-128">The following image shows the dependencies for the `Castle.Windsor` package:</span></span>

![Снимок экрана зависимостей NuGet для пакета Castle. Windsor](./media/example-migration-core/nuget-dependencies.png)

<span data-ttu-id="dc28c-130">Чтобы проверить совместимость пакета, можно использовать средство <https://fuget.org> , предлагающее более подробные сведения о версиях и зависимостях.</span><span class="sxs-lookup"><span data-stu-id="dc28c-130">To check the package compatibility, you can use the tool <https://fuget.org> that offers a more detailed information about versions and dependencies.</span></span>

<span data-ttu-id="dc28c-131">Возможно, проект ссылается на старые версии пакетов, не поддерживающие .NET Core, но вы можете найти более новые версии, поддерживающие ее.</span><span class="sxs-lookup"><span data-stu-id="dc28c-131">Maybe the project is referencing older package versions that don't support .NET Core, but you might find newer versions that do support it.</span></span> <span data-ttu-id="dc28c-132">Поэтому обновление пакетов до более новых версий обычно является хорошей рекомендацией.</span><span class="sxs-lookup"><span data-stu-id="dc28c-132">So, updating packages to newer versions is generally a good recommendation.</span></span> <span data-ttu-id="dc28c-133">Однако следует учитывать, что обновление версии пакета может привести к внесению некоторых критических изменений, которые приведут к необходимости обновления кода.</span><span class="sxs-lookup"><span data-stu-id="dc28c-133">However, you should consider that updating the package version can introduce some breaking changes that would force you to update your code.</span></span>

<span data-ttu-id="dc28c-134">Что произойдет, если вы не нашли совместимую версию?</span><span class="sxs-lookup"><span data-stu-id="dc28c-134">What happens if you don't find a compatible version?</span></span> <span data-ttu-id="dc28c-135">Что делать, если не нужно обновлять версию пакета из-за этих критических изменений?</span><span class="sxs-lookup"><span data-stu-id="dc28c-135">What if you just don't want to update the version of a package because of these breaking changes?</span></span> <span data-ttu-id="dc28c-136">Не беспокойтесь, так как можно зависеть от пакетов .NET Framework из приложения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-136">Don't worry because it's possible to depend on .NET Framework packages from a .NET Core application.</span></span> <span data-ttu-id="dc28c-137">Не забудьте серьезно протестировать ее, так как она может вызвать ошибки времени выполнения, если внешний пакет вызывает API, недоступный в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-137">Don't forget to test it extensively because it can cause run-time errors if the external package calls an API that isn't available on .NET Core.</span></span> <span data-ttu-id="dc28c-138">Это очень удобно, если вы используете старый пакет, который не будет обновляться, и вы можете просто перенацелить работу на .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-138">This is great for when you're using an old package that isn't going to be updated and you can just retarget to work on the .NET Core.</span></span>

#### <a name="check-for-api-compatibility"></a><span data-ttu-id="dc28c-139">Проверка совместимости API</span><span class="sxs-lookup"><span data-stu-id="dc28c-139">Check for API compatibility</span></span>

<span data-ttu-id="dc28c-140">Поскольку поверхность API в .NET Framework и .NET Core аналогична, но не идентична, необходимо проверить, какие интерфейсы API доступны в .NET Core, а какие нет.</span><span class="sxs-lookup"><span data-stu-id="dc28c-140">Since the API surface in .NET Framework and .NET Core is similar but not identical, you must check which APIs are available on .NET Core and which aren't.</span></span> <span data-ttu-id="dc28c-141">Средство анализатора переносимости .NET можно использовать для использования интерфейсов API, которые отсутствуют в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-141">You can use the .NET Portability Analyzer tool to surface APIs used that aren't present on .NET Core.</span></span> <span data-ttu-id="dc28c-142">Он рассматривает двоичный уровень приложения, извлекает все вызываемые API, а затем перечисляет, какие интерфейсы API недоступны в вашей целевой платформе (в данном случае это .NET Core 3,1).</span><span class="sxs-lookup"><span data-stu-id="dc28c-142">It looks at the binary level of your app, extracts all the APIs that are called, and then lists which APIs aren't available on your target framework (.NET Core 3.1 in this case).</span></span>

<span data-ttu-id="dc28c-143">Дополнительные сведения об этом средстве можно найти по адресу:</span><span class="sxs-lookup"><span data-stu-id="dc28c-143">You can find more information about this tool at:</span></span>

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

<span data-ttu-id="dc28c-144">Интересным аспектом этого средства является то, что он охватывает только отличия от собственного кода, а не код из внешних пакетов, которые нельзя изменить.</span><span class="sxs-lookup"><span data-stu-id="dc28c-144">An interesting aspect of this tool is that it only surfaces the differences from your own code and not code from external packages, which you can't change.</span></span> <span data-ttu-id="dc28c-145">Помните, что большинство этих пакетов следует обновить, чтобы они работали с .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-145">Remember you should have updated most of these packages to make them work with .NET Core.</span></span>

### <a name="migrate-project-file"></a><span data-ttu-id="dc28c-146">Перенос файла проекта</span><span class="sxs-lookup"><span data-stu-id="dc28c-146">Migrate project file</span></span>

#### <a name="create-the-new-net-core-project"></a><span data-ttu-id="dc28c-147">Создание нового проекта .NET Core</span><span class="sxs-lookup"><span data-stu-id="dc28c-147">Create the new .NET Core project</span></span>

<span data-ttu-id="dc28c-148">В большинстве случаев необходимо обновить существующий проект до нового формата .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-148">In most of the cases, you'll want to update your existing project to the new .NET Core format.</span></span> <span data-ttu-id="dc28c-149">Однако можно также создать новый проект, сохранив старый.</span><span class="sxs-lookup"><span data-stu-id="dc28c-149">However, you can also create a new project while maintaining the old one.</span></span> <span data-ttu-id="dc28c-150">Основным недостатком обновления старого проекта является то, что вы потеряли поддержку конструктора, что может быть важным для вас.</span><span class="sxs-lookup"><span data-stu-id="dc28c-150">The main drawback from updating the old project is that you lose designer support, which may be important for you.</span></span> <span data-ttu-id="dc28c-151">Если вы хотите продолжить работу с конструктором, необходимо создать новый проект .NET Core параллельно с прежним и общим ресурсам.</span><span class="sxs-lookup"><span data-stu-id="dc28c-151">If you want to keep using the designer, you must create a new .NET Core project in parallel with the old one and share assets.</span></span> <span data-ttu-id="dc28c-152">Если необходимо изменить элементы пользовательского интерфейса в конструкторе, можно переключиться на старый проект, чтобы сделать это.</span><span class="sxs-lookup"><span data-stu-id="dc28c-152">If you need to modify UI elements in the designer, you can switch to the old project to do that.</span></span> <span data-ttu-id="dc28c-153">А так как ресурсы связаны, они также будут обновлены в проекте .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-153">And since assets are linked, they'll be updated in the .NET Core project as well.</span></span>

<span data-ttu-id="dc28c-154">[Проект в стиле пакета SDK](../../core/project-sdk/msbuild-props.md) для .NET Core гораздо проще, чем формат проекта .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc28c-154">The [SDK-style project](../../core/project-sdk/msbuild-props.md) for .NET Core is a lot simpler than .NET Framework's project format.</span></span> <span data-ttu-id="dc28c-155">За исключением упомянутых ранее `PackageReference` записей, вам больше не потребуется делать это.</span><span class="sxs-lookup"><span data-stu-id="dc28c-155">And apart from the previously mentioned `PackageReference` entries, you won't need to do much more.</span></span> <span data-ttu-id="dc28c-156">Новый формат проекта включает определенные расширения файлов по [умолчанию](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects), например `.cs` файлы и `.xaml` , без необходимости явно включать их в файл проекта.</span><span class="sxs-lookup"><span data-stu-id="dc28c-156">The new project format includes certain file extensions [by default](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects), such as `.cs` and `.xaml` files, without the need to explicitly include them in the project file.</span></span>

#### <a name="assemblyinfo-considerations"></a><span data-ttu-id="dc28c-157">Рекомендации по Assembly.info</span><span class="sxs-lookup"><span data-stu-id="dc28c-157">Assembly.info considerations</span></span>

<span data-ttu-id="dc28c-158">Атрибуты формируются автоматически в проектах .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-158">Attributes are autogenerated on .NET Core projects.</span></span> <span data-ttu-id="dc28c-159">Если проект содержит файл *AssemblyInfo.CS* , то определения будут дублироваться, что приведет к конфликтам компиляции.</span><span class="sxs-lookup"><span data-stu-id="dc28c-159">If the project contains an *AssemblyInfo.cs* file, the definitions will be duplicated, which will cause compilation conflicts.</span></span> <span data-ttu-id="dc28c-160">Вы можете удалить старый файл *AssemblyInfo.CS* или отключить автоматическое создание, добавив следующую запись в файл проекта .NET Core:</span><span class="sxs-lookup"><span data-stu-id="dc28c-160">You can delete the older *AssemblyInfo.cs* file or disable autogeneration by adding the following entry to the .NET Core project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a><span data-ttu-id="dc28c-161">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="dc28c-161">Resources</span></span>

<span data-ttu-id="dc28c-162">Внедренные ресурсы включаются автоматически, но ресурсы — нет, поэтому необходимо перенести ресурсы в новый файл проекта.</span><span class="sxs-lookup"><span data-stu-id="dc28c-162">Embedded resources are included automatically but resources aren't, so you need to migrate the resources to the new project file.</span></span>

#### <a name="package-references"></a><span data-ttu-id="dc28c-163">Ссылки на пакеты</span><span class="sxs-lookup"><span data-stu-id="dc28c-163">Package references</span></span>

<span data-ttu-id="dc28c-164">С помощью параметра **Migrate packages.config to PackageReference** можно легко переместить ссылки на внешние пакеты в новый формат, как упоминалось ранее.</span><span class="sxs-lookup"><span data-stu-id="dc28c-164">With the **Migrate packages.config to PackageReference** option, you can easily move your external package references to the new format as previously mentioned.</span></span>

#### <a name="update-package-references"></a><span data-ttu-id="dc28c-165">Обновление ссылок на пакеты</span><span class="sxs-lookup"><span data-stu-id="dc28c-165">Update package references</span></span>

<span data-ttu-id="dc28c-166">Обновите версии пакетов, которые были бы совместимыми, как показано в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="dc28c-166">Update the versions of the packages you've found to be compatible, as shown in the previous section.</span></span>

### <a name="fix-the-code-and-build"></a><span data-ttu-id="dc28c-167">Исправление кода и сборка</span><span class="sxs-lookup"><span data-stu-id="dc28c-167">Fix the code and build</span></span>

#### <a name="microsoftwindowscompatibility"></a><span data-ttu-id="dc28c-168">Microsoft. Windows. Compatibility</span><span class="sxs-lookup"><span data-stu-id="dc28c-168">Microsoft.Windows.Compatibility</span></span>

<span data-ttu-id="dc28c-169">Если приложение зависит от интерфейсов API, которые недоступны в .NET Core, таких как реестр, списки ACL или WCF, необходимо включить ссылку на `Microsoft.Windows.Compatibility` пакет, чтобы добавить эти API для Windows.</span><span class="sxs-lookup"><span data-stu-id="dc28c-169">If your application depends on APIs that aren't available on .NET Core, such as Registry, ACLs, or WCF, you have to include a reference to the `Microsoft.Windows.Compatibility` package to add these Windows-specific APIs.</span></span> <span data-ttu-id="dc28c-170">Они работают с .NET Core, но не включены, так как они не являются кросс-платформенными.</span><span class="sxs-lookup"><span data-stu-id="dc28c-170">They work on .NET Core but aren't included as they aren't cross-platform.</span></span>

<span data-ttu-id="dc28c-171">Это средство, именуемое анализатором API ( <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> ), помогающее определить интерфейсы API, которые не совместимы с кодом.</span><span class="sxs-lookup"><span data-stu-id="dc28c-171">There's a tool called API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) that helps you identify APIs that aren't compatible with your code.</span></span>

#### <a name="use-if-directives"></a><span data-ttu-id="dc28c-172">Использовать \# директивы if</span><span class="sxs-lookup"><span data-stu-id="dc28c-172">Use \#if directives</span></span>

<span data-ttu-id="dc28c-173">Если требуются разные пути выполнения при нацеливании на .NET Framework и .NET Core, следует использовать константы компиляции.</span><span class="sxs-lookup"><span data-stu-id="dc28c-173">If you need different execution paths when targeting .NET Framework and .NET Core, you should use compilation constants.</span></span> <span data-ttu-id="dc28c-174">Добавьте в \# код несколько директив if, чтобы иметь одинаковую базу кода для обеих целей.</span><span class="sxs-lookup"><span data-stu-id="dc28c-174">Add some \#if directives to your code to keep the same code base for both targets.</span></span>

#### <a name="technologies-not-available-on-net-core"></a><span data-ttu-id="dc28c-175">Технологии, недоступные в .NET Core</span><span class="sxs-lookup"><span data-stu-id="dc28c-175">Technologies not available on .NET Core</span></span>

<span data-ttu-id="dc28c-176">Некоторые технологии недоступны в .NET Core, например:</span><span class="sxs-lookup"><span data-stu-id="dc28c-176">Some technologies aren't available on .NET Core, such as:</span></span>

* <span data-ttu-id="dc28c-177">Домены приложений</span><span class="sxs-lookup"><span data-stu-id="dc28c-177">AppDomains</span></span>
* <span data-ttu-id="dc28c-178">Удаленное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="dc28c-178">Remoting</span></span>
* <span data-ttu-id="dc28c-179">Управление доступом для кода</span><span class="sxs-lookup"><span data-stu-id="dc28c-179">Code Access Security</span></span>
* <span data-ttu-id="dc28c-180">Сервер WCF</span><span class="sxs-lookup"><span data-stu-id="dc28c-180">WCF Server</span></span>
* <span data-ttu-id="dc28c-181">Рабочий процесс Windows</span><span class="sxs-lookup"><span data-stu-id="dc28c-181">Windows Workflow</span></span>

<span data-ttu-id="dc28c-182">Именно поэтому необходимо найти замену этих технологий, если вы используете их в своем приложении.</span><span class="sxs-lookup"><span data-stu-id="dc28c-182">That's why you need to find a replacement for these technologies if you're using them in your application.</span></span> <span data-ttu-id="dc28c-183">Дополнительные сведения см. в статье [.NET Framework технологии, недоступные в .NET Core](../../core/porting/net-framework-tech-unavailable.md) .</span><span class="sxs-lookup"><span data-stu-id="dc28c-183">For more information, see the [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md) article.</span></span>

#### <a name="regenerate-autogenerated-clients"></a><span data-ttu-id="dc28c-184">Повторное создание автоматически сформированных клиентов</span><span class="sxs-lookup"><span data-stu-id="dc28c-184">Regenerate autogenerated clients</span></span>

<span data-ttu-id="dc28c-185">Если приложение использует автоматически сформированный код, например клиент WCF, может потребоваться повторно создать этот код для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-185">If your application uses autogenerated code, such as a WCF client, you may need to regenerate this code to target .NET Core.</span></span> <span data-ttu-id="dc28c-186">Иногда можно найти некоторые отсутствующие ссылки, так как они могут не быть включены в набор сборок .NET Core по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="dc28c-186">Sometimes, you can find some missing references since they may not be included as part of the default .NET Core assemblies set.</span></span> <span data-ttu-id="dc28c-187">С помощью такого средства <https://apisof.net/> , как, можно легко найти сборку, в которой находится отсутствующая ссылка, и добавить ее из NuGet.</span><span class="sxs-lookup"><span data-stu-id="dc28c-187">Using a tool like <https://apisof.net/>, you can easily locate the assembly the missing reference lives in and add it from NuGet.</span></span>

#### <a name="rolling-back-package-versions"></a><span data-ttu-id="dc28c-188">Откат версий пакета</span><span class="sxs-lookup"><span data-stu-id="dc28c-188">Rolling back package versions</span></span>

<span data-ttu-id="dc28c-189">Как правило, мы уже упоминали, что вы лучше обновляете каждую версию одного пакета, чтобы обеспечить совместимость с .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-189">As a general rule, we've previously stated that you better update every single package version to be compatible with .NET Core.</span></span> <span data-ttu-id="dc28c-190">Однако вы можете найти, что для обновленной и совместимой версий сборки просто не взимается.</span><span class="sxs-lookup"><span data-stu-id="dc28c-190">However, you can find that targeting an updated and compatible version of an assembly just doesn't pay off.</span></span> <span data-ttu-id="dc28c-191">Если стоимость изменения не является приемлемой, можно рассмотреть возможность отката версий пакета, сохраняя те, которые используются в .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc28c-191">If the cost of change isn't acceptable, you can consider rolling back package versions keeping the ones you use on .NET Framework.</span></span> <span data-ttu-id="dc28c-192">Несмотря на то, что они не предназначены для .NET Core, они должны работать правильно, если они не вызывают некоторые неподдерживаемые API.</span><span class="sxs-lookup"><span data-stu-id="dc28c-192">Although they may not be targeting .NET Core, they should work well unless they call some unsupported APIs.</span></span>

### <a name="run-and-test"></a><span data-ttu-id="dc28c-193">Запуск и тестирование</span><span class="sxs-lookup"><span data-stu-id="dc28c-193">Run and test</span></span>

<span data-ttu-id="dc28c-194">После создания приложения без ошибок можно запустить последний шаг миграции, проверив все функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="dc28c-194">Once you have your application building with no errors, you can start the last step of the migration by testing every functionality.</span></span>

<span data-ttu-id="dc28c-195">На этом заключительном этапе можно найти несколько различных проблем в зависимости от сложности приложения и используемых зависимостей и интерфейсов API.</span><span class="sxs-lookup"><span data-stu-id="dc28c-195">In this final step, you can find several different issues depending on the complexity of your application and the dependencies and APIs you're using.</span></span>

<span data-ttu-id="dc28c-196">Например, при использовании файлов конфигурации (*app.config*) могут возникнуть ошибки во время выполнения, такие как разделы конфигурации, которые отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="dc28c-196">For example, if you use configuration files (*app.config*), you may find some errors at run time like Configuration Sections not present.</span></span> <span data-ttu-id="dc28c-197">Использование `Microsoft.Extensions.Configuration` пакета NuGet должно исправить эту ошибку.</span><span class="sxs-lookup"><span data-stu-id="dc28c-197">Using the `Microsoft.Extensions.Configuration` NuGet package should fix that error.</span></span>

<span data-ttu-id="dc28c-198">Другой причиной ошибок является использование `BeginInvoke` методов и, `EndInvoke` поскольку они не поддерживаются в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-198">Another reason for errors is the use of the `BeginInvoke` and `EndInvoke` methods because they aren't supported on .NET Core.</span></span> <span data-ttu-id="dc28c-199">Они не поддерживаются в .NET Core, так как они имеют зависимость от удаленного взаимодействия, которое не существует в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-199">They aren't supported on .NET Core because they have a dependency on Remoting, which doesn't exist on .NET Core.</span></span> <span data-ttu-id="dc28c-200">Чтобы решить эту проблему, попробуйте использовать `await` ключевое слово (если доступно) или <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="dc28c-200">To solve this issue, try to use the `await` keyword (when available) or the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="dc28c-201">Анализаторы совместимости можно использовать для выявления интерфейсов API и шаблонов кода в коде, которые могут вызывать проблемы во время выполнения с помощью .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-201">You can use compatibility analyzers to let you identify APIs and code patterns in your code that can potentially cause problems at run time with .NET Core.</span></span> <span data-ttu-id="dc28c-202">Перейдите на страницу <https://github.com/dotnet/platform-compat> и используйте анализатор .NET API для своего проекта.</span><span class="sxs-lookup"><span data-stu-id="dc28c-202">Go to <https://github.com/dotnet/platform-compat> and use the .NET API analyzer on your project.</span></span>

## <a name="migrating-a-windows-forms-application"></a><span data-ttu-id="dc28c-203">Перенос приложения Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dc28c-203">Migrating a Windows Forms application</span></span>

<span data-ttu-id="dc28c-204">Чтобы продемонстрировать полный процесс миграции Windows Forms приложения, мы решили перенести пример приложения Ешоп, доступного по адресу <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="dc28c-204">To showcase a complete migration process of a Windows Forms application, we've chosen to migrate the eShop sample application available at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms>.</span></span> <span data-ttu-id="dc28c-205">Полный результат миграции можно найти по адресу <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="dc28c-205">You can find the complete result of the migration at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms>.</span></span>

<span data-ttu-id="dc28c-206">Это приложение показывает Каталог продуктов и позволяет пользователю перемещаться по продуктам, фильтровать их и выполнять поиск.</span><span class="sxs-lookup"><span data-stu-id="dc28c-206">This application shows a product catalog and allows the user to navigate, filter, and search for products.</span></span> <span data-ttu-id="dc28c-207">С точки зрения архитектуры, приложение использует внешнюю службу WCF, которая служит фасадной для серверной базы данных.</span><span class="sxs-lookup"><span data-stu-id="dc28c-207">From an architecture point of view, the app relies on an external WCF service that serves as a façade to a back-end database.</span></span>

<span data-ttu-id="dc28c-208">Основное окно приложения можно увидеть на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="dc28c-208">You can see the main application window in the following picture:</span></span>

![Главное окно приложения](./media/example-migration-core/main-application-window.png)

<span data-ttu-id="dc28c-210">Если открыть *CSPROJ* -файл проекта, можно увидеть примерно следующее:</span><span class="sxs-lookup"><span data-stu-id="dc28c-210">If you open the *.csproj* project file, you can see something like this:</span></span>

![Снимок экрана с содержимым файла CSPROJ](./media/example-migration-core/csproj-file.png)

<span data-ttu-id="dc28c-212">Как упоминалось ранее, проект .NET Core имеет более компактный стиль, поэтому необходимо перенести структуру проекта в новый стиль пакет SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-212">As previously mentioned, .NET Core project has a more compact style and you need to migrate the project structure to the new .NET Core SDK style.</span></span>

<span data-ttu-id="dc28c-213">В Обозреватель решений щелкните правой кнопкой мыши проект Windows Forms и выберите команду **Выгрузить проект**  >  **изменить**.</span><span class="sxs-lookup"><span data-stu-id="dc28c-213">In the Solution Explorer, right click on the Windows Forms project and select **Unload Project** > **Edit**.</span></span>

<span data-ttu-id="dc28c-214">Теперь можно обновить CSPROJ файл.</span><span class="sxs-lookup"><span data-stu-id="dc28c-214">Now you can update the .csproj file.</span></span> <span data-ttu-id="dc28c-215">Вы удалите все содержимое и замените его следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="dc28c-215">You'll delete the entire content and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWindowsForms>true</UseWindowsForms>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="dc28c-216">Сохраните и перезагрузите проект.</span><span class="sxs-lookup"><span data-stu-id="dc28c-216">Save and reload the project.</span></span> <span data-ttu-id="dc28c-217">Теперь обновление файла проекта завершено, и проект предназначен для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-217">You're now done updating the project file and the project is targeting the .NET Core.</span></span>

<span data-ttu-id="dc28c-218">Если скомпилировать проект на этом этапе, вы найдете некоторые ошибки, связанные со ссылкой на клиент WCF.</span><span class="sxs-lookup"><span data-stu-id="dc28c-218">If you compile the project at this point, you'll find some errors related to the WCF client reference.</span></span> <span data-ttu-id="dc28c-219">Так как этот код создается автоматически, необходимо создать его повторно, чтобы он нацелиться на .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-219">Since this code is autogenerated, you must regenerate it to target .NET Core.</span></span>

![Снимок экрана с ошибками компиляции в Visual Studio](./media/example-migration-core/winforms-compilation-errors.png)

<span data-ttu-id="dc28c-221">Удалите файл *Reference.CS* и создайте новый клиент службы.</span><span class="sxs-lookup"><span data-stu-id="dc28c-221">Delete the *Reference.cs* file and generate a new Service Client.</span></span>

<span data-ttu-id="dc28c-222">Щелкните правой кнопкой мыши **подключенные службы** и выберите пункт **Добавить подключенную службу** .</span><span class="sxs-lookup"><span data-stu-id="dc28c-222">Right-click on **Connected Services** and select the **Add Connected Service** option.</span></span>

![Снимок экрана: меню "Подключенные службы" с выбранным параметром "добавить подключенную службу"](./media/example-migration-core/add-connected-service.png)

<span data-ttu-id="dc28c-224">Откроется окно Подключенные службы.</span><span class="sxs-lookup"><span data-stu-id="dc28c-224">The Connected Services window opens.</span></span> <span data-ttu-id="dc28c-225">Выберите параметр **веб-служба Microsoft WCF** .</span><span class="sxs-lookup"><span data-stu-id="dc28c-225">Select the **Microsoft WCF Web Service** option.</span></span>

![Снимок экрана окна Подключенные службы](./media/example-migration-core/connected-services-window.png)

<span data-ttu-id="dc28c-227">Если у вас есть служба WCF в том же решении, что и в этом примере, вместо указания URL-адреса службы можно выбрать параметр **Discover** .</span><span class="sxs-lookup"><span data-stu-id="dc28c-227">If you have the WCF Service in the same solution as we have in this example, you can select the **Discover** option instead of specifying a service URL.</span></span>

![Снимок экрана: окно "Настройка ссылки на веб-службу WCF"](./media/example-migration-core/configure-wcf-reference.png)

<span data-ttu-id="dc28c-229">После обнаружения службы средство отражает контракт API, реализованный службой.</span><span class="sxs-lookup"><span data-stu-id="dc28c-229">Once the service is located, the tool reflects the API contract implemented by the service.</span></span> <span data-ttu-id="dc28c-230">Измените имя пространства имен, `eShopServiceReference` как показано на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="dc28c-230">Change the name of the namespace to be `eShopServiceReference` as shown in the following image:</span></span>

![Снимок экрана: контракт API и пространство имен изменены](./media/example-migration-core/api-contract-namespace.png)

<span data-ttu-id="dc28c-232">Нажмите кнопку **Готово** .</span><span class="sxs-lookup"><span data-stu-id="dc28c-232">Select the **Finish** button.</span></span> <span data-ttu-id="dc28c-233">Через некоторое время вы увидите созданный код.</span><span class="sxs-lookup"><span data-stu-id="dc28c-233">After a while, you'll see the generated code.</span></span>

<span data-ttu-id="dc28c-234">Вы должны увидеть три автоматически создаваемых файла:</span><span class="sxs-lookup"><span data-stu-id="dc28c-234">You should see three autogenerated files:</span></span>

1. <span data-ttu-id="dc28c-235">*Начало работы*: ссылка на GitHub, чтобы предоставить некоторую информацию о WCF.</span><span class="sxs-lookup"><span data-stu-id="dc28c-235">*Getting Started*: a link to GitHub to provide some information on WCF.</span></span>
2. <span data-ttu-id="dc28c-236">*ConnectedService.json*: параметры конфигурации для подключения к службе.</span><span class="sxs-lookup"><span data-stu-id="dc28c-236">*ConnectedService.json*: configuration parameters to connect to the service.</span></span>
3. <span data-ttu-id="dc28c-237">*Reference.CS*: фактический код клиента WCF.</span><span class="sxs-lookup"><span data-stu-id="dc28c-237">*Reference.cs*: the actual WCF client code.</span></span>

![Снимок экрана обозреватель решений окна с тремя автоматически созданными файлами](./media/example-migration-core/autogenerated-files.png)

<span data-ttu-id="dc28c-239">При повторной компиляции вы увидите много ошибок, поступающих из файлов *CS* в папку *Helper* .</span><span class="sxs-lookup"><span data-stu-id="dc28c-239">If you compile again, you'll see many errors coming from *.cs* files inside the *Helper* folder.</span></span> <span data-ttu-id="dc28c-240">Эта папка присутствовала в .NET Framework версии, но не включена в Old *. csproj*.</span><span class="sxs-lookup"><span data-stu-id="dc28c-240">This folder was present in the .NET Framework version but not included in the old *.csproj*.</span></span> <span data-ttu-id="dc28c-241">Но при использовании нового проекта в стиле SDK каждый файл кода, который находится под расположением файла проекта, включается по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="dc28c-241">But with the new SDK-style project, every code file present underneath the project file location is included by default.</span></span> <span data-ttu-id="dc28c-242">То есть новый проект .NET Core пытается скомпилировать файлы в папке *Helper* .</span><span class="sxs-lookup"><span data-stu-id="dc28c-242">That is, the new .NET Core project tries to compile the files inside the *Helper* folder.</span></span> <span data-ttu-id="dc28c-243">Так как эта папка не требуется, ее можно безопасно удалить.</span><span class="sxs-lookup"><span data-stu-id="dc28c-243">Since that folder isn't needed, you can safely delete it.</span></span>

<span data-ttu-id="dc28c-244">Если скомпилировать проект еще раз и выполнить его, вы не увидите образы продукта.</span><span class="sxs-lookup"><span data-stu-id="dc28c-244">If you compile the project again and execute it, you won't see the product images.</span></span> <span data-ttu-id="dc28c-245">Проблема заключается в том, что теперь путь к файлам немного изменился.</span><span class="sxs-lookup"><span data-stu-id="dc28c-245">The problem is that now the path to the files has slightly changed.</span></span> <span data-ttu-id="dc28c-246">Чтобы устранить эту проблему, необходимо добавить в путь другой уровень глубины, обновив в файле `CatalogView.cs` строку:</span><span class="sxs-lookup"><span data-stu-id="dc28c-246">To fix this issue, you need to add another level of depth in the path, updating in the file `CatalogView.cs` the line:</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="dc28c-247">в</span><span class="sxs-lookup"><span data-stu-id="dc28c-247">to</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="dc28c-248">После этого изменения можно убедиться, что приложение запускается и работает должным образом в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-248">After this change, you can check that the application launches and runs as expected on .NET Core.</span></span>

## <a name="migrating-a-wpf-application"></a><span data-ttu-id="dc28c-249">Миграция приложения WPF</span><span class="sxs-lookup"><span data-stu-id="dc28c-249">Migrating a WPF application</span></span>

<span data-ttu-id="dc28c-250">Мы будем использовать `Shop.ClassicWPF` пример приложения для выполнения миграции.</span><span class="sxs-lookup"><span data-stu-id="dc28c-250">We'll use the `Shop.ClassicWPF` sample application to perform the migration.</span></span> <span data-ttu-id="dc28c-251">На следующем рисунке показан снимок экрана приложения перед миграцией:</span><span class="sxs-lookup"><span data-stu-id="dc28c-251">The following image shows a screenshot of the app before migration:</span></span>

![Пример приложения перед миграцией](./media/example-migration-core/app-before-migration.png)

<span data-ttu-id="dc28c-253">Это приложение использует локальную базу данных SQL Server Express для хранения сведений о каталоге продуктов.</span><span class="sxs-lookup"><span data-stu-id="dc28c-253">This application uses a local SQL Server Express database to hold the product catalog information.</span></span> <span data-ttu-id="dc28c-254">Доступ к этой базе данных осуществляется непосредственно из приложения WPF.</span><span class="sxs-lookup"><span data-stu-id="dc28c-254">This database is accessed directly from the WPF application.</span></span>

<span data-ttu-id="dc28c-255">Сначала необходимо обновить файл *CSPROJ* до нового стиля SDK, используемого приложениями .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-255">First, you must update the *.csproj* file to the new SDK style used by .NET Core applications.</span></span> <span data-ttu-id="dc28c-256">Вы выполните те же действия, которые описаны в Windows Forms миграции: вы выгружаете проект, открываете файл *. csproj* , обновляете его содержимое и перезагружаете проект.</span><span class="sxs-lookup"><span data-stu-id="dc28c-256">You'll follow the same steps described in the Windows Forms migration: you'll unload the project, open the *.csproj* file, update its contents, and reload the project.</span></span>

<span data-ttu-id="dc28c-257">В этом случае удалите все содержимое файла *CSPROJ* и замените его следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="dc28c-257">In this case, delete all the content of the *.csproj* file and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWpf>true</UseWpf>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="dc28c-258">Если перезагрузить проект и скомпилировать его, вы получите следующую ошибку:</span><span class="sxs-lookup"><span data-stu-id="dc28c-258">If you reload the project and compile it, you'll get the following error:</span></span>

![Снимок экрана с ошибками компиляции в Visual Studio](./media/example-migration-core/wpf-compilation-error.png)

<span data-ttu-id="dc28c-260">Так как вы удалили все содержимое *CSPROJ* , вы потеряли спецификацию ссылок проекта, присутствующую в старом проекте.</span><span class="sxs-lookup"><span data-stu-id="dc28c-260">Since you've deleted all the *.csproj* contents, you've lost a project reference specification present in the old project.</span></span> <span data-ttu-id="dc28c-261">Необходимо просто добавить эту строку в *CSPROJ* файл, чтобы включить ссылку на проект.</span><span class="sxs-lookup"><span data-stu-id="dc28c-261">You just need to add this line to the *.csproj* file to include the project reference back:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

<span data-ttu-id="dc28c-262">Можно также разрешить Visual Studio, щелкнув правой кнопкой мыши узел **зависимости** и выбрав пункт **Добавить ссылку на проект**.</span><span class="sxs-lookup"><span data-stu-id="dc28c-262">You can also let Visual Studio help you by right-clicking on the **Dependencies** node and selecting **Add Project Reference**.</span></span> <span data-ttu-id="dc28c-263">Выберите проект из решения и нажмите кнопку " **ОК**":</span><span class="sxs-lookup"><span data-stu-id="dc28c-263">Select the project from the solution and click **OK**:</span></span>

![Снимок экрана: диалоговое окно диспетчера ссылок с выбранным проектом Ешоп. дескриптора SqlProvider](./media/example-migration-core/reference-manager.png)

<span data-ttu-id="dc28c-265">После добавления ссылки на отсутствующий проект приложение компилируется и выполняется должным образом в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc28c-265">Once you add the missing project reference, the application compiles and runs as expected on .NET Core.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="dc28c-266">[Назад](windows-migration.md)
>[Вперед](deploy-modern-applications.md)</span><span class="sxs-lookup"><span data-stu-id="dc28c-266">[Previous](windows-migration.md)
[Next](deploy-modern-applications.md)</span></span>
