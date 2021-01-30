---
title: Пример миграции на .NET 5
description: Показано, как перенести примеры приложений, предназначенных для платформа .NET Framework в .NET 5.
ms.date: 01/19/2021
ms.openlocfilehash: 39ecdfa639f4d68a4a8821da839f014c8de42ab0
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216269"
---
# <a name="example-of-migrating-to-net"></a><span data-ttu-id="413d3-103">Пример перехода на .NET</span><span class="sxs-lookup"><span data-stu-id="413d3-103">Example of migrating to .NET</span></span>

<span data-ttu-id="413d3-104">В этой главе представлены практические рекомендации, которые помогут выполнить миграцию существующего приложения с платформа .NET Framework на .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-104">In this chapter, we present practical guidelines to help you perform a migration of your existing application from .NET Framework to .NET.</span></span>

<span data-ttu-id="413d3-105">Мы представим хорошо структурированный процесс, который вы можете отслеживать, а также наиболее важные моменты, которые следует учитывать на каждом шаге.</span><span class="sxs-lookup"><span data-stu-id="413d3-105">We present a well-structured process you can follow and the most important things to consider on each step.</span></span>

<span data-ttu-id="413d3-106">Затем мы задокументировани пошаговый процесс миграции для примера классического приложения как из версий WinForms, так и для WPF.</span><span class="sxs-lookup"><span data-stu-id="413d3-106">We then document a step-by-step migration process for a sample desktop application, both from WinForms and WPF versions.</span></span>

## <a name="migration-process-overview"></a><span data-ttu-id="413d3-107">Общие сведения о процессе миграции</span><span class="sxs-lookup"><span data-stu-id="413d3-107">Migration process overview</span></span>

<span data-ttu-id="413d3-108">Процесс миграции состоит из четырех последовательных шагов:</span><span class="sxs-lookup"><span data-stu-id="413d3-108">The migration process consists of four sequential steps:</span></span>

1. <span data-ttu-id="413d3-109">**Подготовка**. Изучите зависимости, которые проект должен иметь представление о дальнейших действиях.</span><span class="sxs-lookup"><span data-stu-id="413d3-109">**Preparation**: Understand the dependencies the project has to have an idea of what's ahead.</span></span> <span data-ttu-id="413d3-110">На этом шаге вы переведите текущий проект в состояние, которое упрощает точку запуска для миграции.</span><span class="sxs-lookup"><span data-stu-id="413d3-110">In this step, you take the current project into a state that simplifies the startup point for the migration.</span></span>

2. <span data-ttu-id="413d3-111">**Миграция файла проекта.** в проектах .NET используется новый формат проекта в стиле SDK.</span><span class="sxs-lookup"><span data-stu-id="413d3-111">**Migrate Project File:** .NET projects use the new SDK-style project format.</span></span> <span data-ttu-id="413d3-112">Создайте новый файл проекта с этим форматом или обновите его, чтобы использовать стиль пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="413d3-112">Create a new project file with this format or update the one you have to use the SDK style.</span></span>

3. <span data-ttu-id="413d3-113">**Исправление кода и сборки:** Постройте код в .NET для устранения различий на уровне API между платформа .NET Framework и .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-113">**Fix code and build:** Build the code in .NET addressing API-level differences between .NET Framework and .NET.</span></span> <span data-ttu-id="413d3-114">При необходимости обновите сторонние пакеты до тех, которые поддерживают .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-114">If needed, update third-party packages to the ones that support .NET.</span></span>

4. <span data-ttu-id="413d3-115">**Запуск и тестирование:** Могут возникнуть различия, которые не отображаются до времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="413d3-115">**Run and test:** There might be differences that don't show up until run time.</span></span> <span data-ttu-id="413d3-116">Поэтому не забудьте запустить приложение и проверить, что все работает правильно.</span><span class="sxs-lookup"><span data-stu-id="413d3-116">So, don't forget to run the application and test that everything works as expected.</span></span>

### <a name="preparation"></a><span data-ttu-id="413d3-117">Подготовка</span><span class="sxs-lookup"><span data-stu-id="413d3-117">Preparation</span></span>

#### <a name="migrate-packagesconfig-file"></a><span data-ttu-id="413d3-118">Миграция файла packages.config</span><span class="sxs-lookup"><span data-stu-id="413d3-118">Migrate packages.config file</span></span>

<span data-ttu-id="413d3-119">В платформа .NET Framework приложении все ссылки на внешние пакеты объявляются в файле *packages.config* .</span><span class="sxs-lookup"><span data-stu-id="413d3-119">In a .NET Framework application, all references to external packages are declared in the *packages.config* file.</span></span> <span data-ttu-id="413d3-120">В .NET больше не нужно использовать файл *packages.config* .</span><span class="sxs-lookup"><span data-stu-id="413d3-120">In .NET, there's no longer the need to use the *packages.config* file.</span></span> <span data-ttu-id="413d3-121">Вместо этого используйте свойство [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) в файле проекта, чтобы указать пакеты NuGet для приложения.</span><span class="sxs-lookup"><span data-stu-id="413d3-121">Instead, use the [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) property inside the project file to specify the NuGet packages for your app.</span></span>

<span data-ttu-id="413d3-122">Поэтому необходимо перейти от одного формата к другому.</span><span class="sxs-lookup"><span data-stu-id="413d3-122">So, you need to transition from one format to another.</span></span> <span data-ttu-id="413d3-123">Обновление можно выполнить вручную, используя зависимости, содержащиеся в файле *packages.config* , и перенести их в файл проекта в `PackageReference` формате.</span><span class="sxs-lookup"><span data-stu-id="413d3-123">You can do the update manually, taking the dependencies contained in the *packages.config* file and migrating them to the project file with the `PackageReference` format.</span></span> <span data-ttu-id="413d3-124">Вы также можете позволить Visual Studio выполнить свою работу: щелкните правой кнопкой мыши файл *packages.config* и выберите пункт **перенести packages.config в PackageReference** .</span><span class="sxs-lookup"><span data-stu-id="413d3-124">Or, you can let Visual Studio do the work for you: right-click on the *packages.config* file and select the **Migrate packages.config to PackageReference** option.</span></span>

#### <a name="verify-every-dependency-compatibility-in-net"></a><span data-ttu-id="413d3-125">Проверка каждой совместимости зависимостей в .NET</span><span class="sxs-lookup"><span data-stu-id="413d3-125">Verify every dependency compatibility in .NET</span></span>

<span data-ttu-id="413d3-126">После переноса ссылок на пакеты необходимо проверить каждую ссылку на совместимость.</span><span class="sxs-lookup"><span data-stu-id="413d3-126">Once you've migrated the package references, you must check each reference for compatibility.</span></span> <span data-ttu-id="413d3-127">Вы можете исследовать зависимости каждого пакета NuGet, используемого приложением в [NuGet.org](https://www.nuget.org/). Если пакет имеет .NET Standard зависимости, он будет работать на .NET 5,0, так как .NET [поддерживает](../../standard/net-standard.md#net-implementation-support) все версии .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="413d3-127">You can explore the dependencies of each NuGet package your application is using on [nuget.org](https://www.nuget.org/). If the package has .NET Standard dependencies, then it's going to work on .NET 5.0 because .NET [supports](../../standard/net-standard.md#net-implementation-support) all versions of .NET Standard.</span></span> <span data-ttu-id="413d3-128">На следующем рисунке показаны зависимости для `Castle.Windsor` пакета.</span><span class="sxs-lookup"><span data-stu-id="413d3-128">The following image shows the dependencies for the `Castle.Windsor` package:</span></span>

![Снимок экрана зависимостей NuGet для пакета Castle. Windsor](./media/example-migration-core/nuget-dependencies.png)

<span data-ttu-id="413d3-130">Чтобы проверить совместимость пакета, можно использовать средство <https://fuget.org> , предлагающее более подробные сведения о версиях и зависимостях.</span><span class="sxs-lookup"><span data-stu-id="413d3-130">To check the package compatibility, you can use the tool <https://fuget.org> that offers a more detailed information about versions and dependencies.</span></span>

<span data-ttu-id="413d3-131">Возможно, проект ссылается на старые версии пакетов, которые не поддерживают .NET, но вы можете найти более новые версии, поддерживающие ее.</span><span class="sxs-lookup"><span data-stu-id="413d3-131">Maybe the project is referencing older package versions that don't support .NET, but you might find newer versions that do support it.</span></span> <span data-ttu-id="413d3-132">Поэтому обновление пакетов до более новых версий обычно является хорошей рекомендацией.</span><span class="sxs-lookup"><span data-stu-id="413d3-132">So, updating packages to newer versions is generally a good recommendation.</span></span> <span data-ttu-id="413d3-133">Однако следует учитывать, что обновление версии пакета может привести к внесению некоторых критических изменений, которые приведут к необходимости обновления кода.</span><span class="sxs-lookup"><span data-stu-id="413d3-133">However, you should consider that updating the package version can introduce some breaking changes that would force you to update your code.</span></span>

<span data-ttu-id="413d3-134">Что произойдет, если вы не нашли совместимую версию?</span><span class="sxs-lookup"><span data-stu-id="413d3-134">What happens if you don't find a compatible version?</span></span> <span data-ttu-id="413d3-135">Что делать, если не нужно обновлять версию пакета из-за этих критических изменений?</span><span class="sxs-lookup"><span data-stu-id="413d3-135">What if you just don't want to update the version of a package because of these breaking changes?</span></span> <span data-ttu-id="413d3-136">Не беспокойтесь, так как можно зависеть от пакетов платформа .NET Framework из приложения .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-136">Don't worry because it's possible to depend on .NET Framework packages from a .NET application.</span></span> <span data-ttu-id="413d3-137">Не забудьте серьезно протестировать ее, так как она может вызвать ошибки времени выполнения, если внешний пакет вызывает API, недоступный в .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-137">Don't forget to test it extensively because it can cause run-time errors if the external package calls an API that isn't available on .NET.</span></span> <span data-ttu-id="413d3-138">Это очень удобно, если вы используете старый пакет, который не будет обновляться, и вы можете просто перенацелить работу на .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-138">This is great for when you're using an old package that isn't going to be updated and you can just retarget to work on the .NET.</span></span>

#### <a name="check-for-api-compatibility"></a><span data-ttu-id="413d3-139">Проверка совместимости API</span><span class="sxs-lookup"><span data-stu-id="413d3-139">Check for API compatibility</span></span>

<span data-ttu-id="413d3-140">Так как поверхность API в платформа .NET Framework и .NET аналогична, но не идентична, необходимо проверить, какие интерфейсы API доступны в .NET, а какие нет.</span><span class="sxs-lookup"><span data-stu-id="413d3-140">Since the API surface in .NET Framework and .NET is similar but not identical, you must check which APIs are available on .NET and which aren't.</span></span> <span data-ttu-id="413d3-141">Средство анализатора переносимости .NET можно использовать для использования API-интерфейсов, отсутствующих в .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-141">You can use the .NET Portability Analyzer tool to surface APIs used that aren't present on .NET.</span></span> <span data-ttu-id="413d3-142">Он рассматривает двоичный уровень приложения, извлекает все вызываемые API, а затем перечисляет, какие интерфейсы API недоступны в вашей целевой платформе (в данном случае это .NET 5,0).</span><span class="sxs-lookup"><span data-stu-id="413d3-142">It looks at the binary level of your app, extracts all the APIs that are called, and then lists which APIs aren't available on your target framework (.NET 5.0 in this case).</span></span>

<span data-ttu-id="413d3-143">Дополнительные сведения об этом средстве можно найти по адресу:</span><span class="sxs-lookup"><span data-stu-id="413d3-143">You can find more information about this tool at:</span></span>

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

<span data-ttu-id="413d3-144">Интересным аспектом этого средства является то, что он охватывает только отличия от собственного кода, а не код из внешних пакетов, которые нельзя изменить.</span><span class="sxs-lookup"><span data-stu-id="413d3-144">An interesting aspect of this tool is that it only surfaces the differences from your own code and not code from external packages, which you can't change.</span></span> <span data-ttu-id="413d3-145">Помните, что большинство этих пакетов следует обновить, чтобы они работали с .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-145">Remember you should have updated most of these packages to make them work with .NET.</span></span>

### <a name="migrate-with-try-convert-tool"></a><span data-ttu-id="413d3-146">Миграция с помощью инструмента "повторить преобразование"</span><span class="sxs-lookup"><span data-stu-id="413d3-146">Migrate with Try Convert tool</span></span>

<span data-ttu-id="413d3-147">Средство " [попробовать преобразовать](https://github.com/dotnet/try-convert/releases) " — отличный способ миграции проекта.</span><span class="sxs-lookup"><span data-stu-id="413d3-147">The [Try Convert](https://github.com/dotnet/try-convert/releases) tool is a great way to migrate a project.</span></span> <span data-ttu-id="413d3-148">Это глобальное средство, которое пытается обновить файл проекта по старому стилю до нового стиля пакета SDK и перенацелить применимые проекты на .NET 5.</span><span class="sxs-lookup"><span data-stu-id="413d3-148">It's a global tool that attempts to upgrade your project file from the old style to the new SDK style, and retargets applicable projects to .NET 5.</span></span> <span data-ttu-id="413d3-149">После установки можно выполнить следующие команды:</span><span class="sxs-lookup"><span data-stu-id="413d3-149">Once installed, you can run the following commands:</span></span>

```dotnetcli
try-convert -p "<path to your project file>"
```

<span data-ttu-id="413d3-150">Или сделайте так:</span><span class="sxs-lookup"><span data-stu-id="413d3-150">Or:</span></span>

```dotnetcli
try-convert -w "<path to your solution>"
```

<span data-ttu-id="413d3-151">После того как средство предпримет попытку преобразования, перезагрузите файлы в Visual Studio для выполнения и тестирования.</span><span class="sxs-lookup"><span data-stu-id="413d3-151">After the tool attempts the conversion, reload your files in Visual Studio to run and test.</span></span> <span data-ttu-id="413d3-152">Существует вероятность, что попытка преобразования не сможет выполнить преобразование из-за особенностей проекта.</span><span class="sxs-lookup"><span data-stu-id="413d3-152">There's a possibility that Try Convert won't be able to perform the conversion due to the specifics of your project.</span></span> <span data-ttu-id="413d3-153">В этом случае вы можете ознакомиться с приведенными ниже шагами.</span><span class="sxs-lookup"><span data-stu-id="413d3-153">In that case, you can refer the below steps.</span></span>

#### <a name="migrate-manually"></a><span data-ttu-id="413d3-154">Миграция вручную</span><span class="sxs-lookup"><span data-stu-id="413d3-154">Migrate manually</span></span>

1. <span data-ttu-id="413d3-155">Создание нового проекта .NET</span><span class="sxs-lookup"><span data-stu-id="413d3-155">Create the new .NET project</span></span>

<span data-ttu-id="413d3-156">В большинстве случаев необходимо обновить существующий проект до нового формата .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-156">In most cases, you'll want to update your existing project to the new .NET format.</span></span> <span data-ttu-id="413d3-157">Однако можно также создать новый проект, сохранив старый.</span><span class="sxs-lookup"><span data-stu-id="413d3-157">However, you can also create a new project while maintaining the old one.</span></span> <span data-ttu-id="413d3-158">Основной недостаток обновления старого проекта заключается в том, что вы потеряли поддержку конструктора, которая может быть важной для вас и вашей команды разработчиков.</span><span class="sxs-lookup"><span data-stu-id="413d3-158">The main drawback from updating the old project is that you lose designer support, which may be important to you and your development team.</span></span> <span data-ttu-id="413d3-159">Если вы хотите продолжить работу с конструктором, необходимо создать новый проект .NET параллельно с старым и поделиться ресурсами.</span><span class="sxs-lookup"><span data-stu-id="413d3-159">If you want to keep using the designer, you must create a new .NET project in parallel with the old one and share assets.</span></span> <span data-ttu-id="413d3-160">Если необходимо изменить элементы пользовательского интерфейса в конструкторе, можно переключиться на старый проект, чтобы сделать это.</span><span class="sxs-lookup"><span data-stu-id="413d3-160">If you need to modify UI elements in the designer, you can switch to the old project to do that.</span></span> <span data-ttu-id="413d3-161">А так как ресурсы связаны, они также будут обновлены в проекте .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-161">And since assets are linked, they'll be updated in the .NET project as well.</span></span>

<span data-ttu-id="413d3-162">[Проект в стиле пакета SDK](../../core/project-sdk/msbuild-props.md) для .NET гораздо проще, чем формат проекта платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="413d3-162">The [SDK-style project](../../core/project-sdk/msbuild-props.md) for .NET is a lot simpler than .NET Framework's project format.</span></span> <span data-ttu-id="413d3-163">Помимо упомянутых выше `PackageReference` записей вам больше не нужно делать.</span><span class="sxs-lookup"><span data-stu-id="413d3-163">Apart from the previously mentioned `PackageReference` entries, you won't need to do much more.</span></span> <span data-ttu-id="413d3-164">Новый формат проекта [включает файлы с определенными расширениями по умолчанию](../../core/project-sdk/overview.md#default-includes-and-excludes), `.cs` например `.xaml` файлы и, без необходимости явно включать их в файл проекта.</span><span class="sxs-lookup"><span data-stu-id="413d3-164">The new project format [includes files with certain extensions by default](../../core/project-sdk/overview.md#default-includes-and-excludes), such as `.cs` and `.xaml` files, without the need to explicitly include them in the project file.</span></span>

#### <a name="assemblyinfo-considerations"></a><span data-ttu-id="413d3-165">Рекомендации по AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="413d3-165">AssemblyInfo considerations</span></span>

<span data-ttu-id="413d3-166">Атрибуты формируются автоматически в проектах .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-166">Attributes are autogenerated on .NET projects.</span></span> <span data-ttu-id="413d3-167">Если проект содержит файл *AssemblyInfo.CS* , то определения будут дублироваться, что приведет к конфликтам компиляции.</span><span class="sxs-lookup"><span data-stu-id="413d3-167">If the project contains an *AssemblyInfo.cs* file, the definitions will be duplicated, which will cause compilation conflicts.</span></span> <span data-ttu-id="413d3-168">Вы можете удалить старый файл *AssemblyInfo.CS* или отключить автоматическое создание, добавив следующую запись в файл проекта .NET:</span><span class="sxs-lookup"><span data-stu-id="413d3-168">You can delete the older *AssemblyInfo.cs* file or disable autogeneration by adding the following entry to the .NET project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a><span data-ttu-id="413d3-169">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="413d3-169">Resources</span></span>

<span data-ttu-id="413d3-170">Внедренные ресурсы включаются автоматически, но ресурсы — нет, поэтому необходимо перенести ресурсы в новый файл проекта.</span><span class="sxs-lookup"><span data-stu-id="413d3-170">Embedded resources are included automatically but resources aren't, so you need to migrate the resources to the new project file.</span></span>

#### <a name="package-references"></a><span data-ttu-id="413d3-171">Ссылки на пакеты</span><span class="sxs-lookup"><span data-stu-id="413d3-171">Package references</span></span>

<span data-ttu-id="413d3-172">С помощью параметра **Migrate packages.config to PackageReference** можно легко переместить ссылки на внешние пакеты в новый формат, как упоминалось ранее.</span><span class="sxs-lookup"><span data-stu-id="413d3-172">With the **Migrate packages.config to PackageReference** option, you can easily move your external package references to the new format as previously mentioned.</span></span>

#### <a name="update-package-references"></a><span data-ttu-id="413d3-173">Обновление ссылок на пакеты</span><span class="sxs-lookup"><span data-stu-id="413d3-173">Update package references</span></span>

<span data-ttu-id="413d3-174">Обновите версии пакетов, которые были бы совместимыми, как показано в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="413d3-174">Update the versions of the packages you've found to be compatible, as shown in the previous section.</span></span>

### <a name="fix-the-code-and-build"></a><span data-ttu-id="413d3-175">Исправление кода и сборка</span><span class="sxs-lookup"><span data-stu-id="413d3-175">Fix the code and build</span></span>

#### <a name="microsoftwindowscompatibility"></a><span data-ttu-id="413d3-176">Microsoft. Windows. Compatibility</span><span class="sxs-lookup"><span data-stu-id="413d3-176">Microsoft.Windows.Compatibility</span></span>

<span data-ttu-id="413d3-177">Если приложение зависит от интерфейсов API, которые недоступны в .NET, таких как реестр, списки ACL или WCF, необходимо включить ссылку на `Microsoft.Windows.Compatibility` пакет, чтобы добавить эти интерфейсы API для Windows.</span><span class="sxs-lookup"><span data-stu-id="413d3-177">If your application depends on APIs that aren't available on .NET, such as Registry, ACLs, or WCF, you have to include a reference to the `Microsoft.Windows.Compatibility` package to add these Windows-specific APIs.</span></span> <span data-ttu-id="413d3-178">Они работают на платформе .NET, но не включены, так как они не являются кросс-платформенными.</span><span class="sxs-lookup"><span data-stu-id="413d3-178">They work on .NET but aren't included as they aren't cross-platform.</span></span>

<span data-ttu-id="413d3-179">Это средство, именуемое анализатором API ( <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> ), помогающее определить интерфейсы API, которые не совместимы с кодом.</span><span class="sxs-lookup"><span data-stu-id="413d3-179">There's a tool called API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) that helps you identify APIs that aren't compatible with your code.</span></span>

#### <a name="use-if-directives"></a><span data-ttu-id="413d3-180">Использовать \# директивы if</span><span class="sxs-lookup"><span data-stu-id="413d3-180">Use \#if directives</span></span>

<span data-ttu-id="413d3-181">Если требуются разные пути выполнения при нацеливании на платформа .NET Framework и .NET, следует использовать константы компиляции.</span><span class="sxs-lookup"><span data-stu-id="413d3-181">If you need different execution paths when targeting .NET Framework and .NET, you should use compilation constants.</span></span> <span data-ttu-id="413d3-182">Добавьте в \# код несколько директив if, чтобы иметь одинаковую базу кода для обеих целей.</span><span class="sxs-lookup"><span data-stu-id="413d3-182">Add some \#if directives to your code to keep the same code base for both targets.</span></span>

#### <a name="technologies-not-available-on-net"></a><span data-ttu-id="413d3-183">Технологии, недоступные в .NET</span><span class="sxs-lookup"><span data-stu-id="413d3-183">Technologies not available on .NET</span></span>

<span data-ttu-id="413d3-184">Некоторые технологии недоступны в .NET, например:</span><span class="sxs-lookup"><span data-stu-id="413d3-184">Some technologies aren't available on .NET, such as:</span></span>

* <span data-ttu-id="413d3-185">Домены приложений</span><span class="sxs-lookup"><span data-stu-id="413d3-185">AppDomains</span></span>
* <span data-ttu-id="413d3-186">Удаленное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="413d3-186">Remoting</span></span>
* <span data-ttu-id="413d3-187">Управление доступом для кода</span><span class="sxs-lookup"><span data-stu-id="413d3-187">Code Access Security</span></span>
* <span data-ttu-id="413d3-188">Сервер WCF</span><span class="sxs-lookup"><span data-stu-id="413d3-188">WCF Server</span></span>
* <span data-ttu-id="413d3-189">Рабочий процесс Windows</span><span class="sxs-lookup"><span data-stu-id="413d3-189">Windows Workflow</span></span>

<span data-ttu-id="413d3-190">Именно поэтому необходимо найти замену этих технологий, если вы используете их в своем приложении.</span><span class="sxs-lookup"><span data-stu-id="413d3-190">That's why you need to find a replacement for these technologies if you're using them in your application.</span></span> <span data-ttu-id="413d3-191">Дополнительные сведения см. в статье [платформа .NET Framework технологии, недоступные в .NET Core и .NET 5 +](../../core/porting/net-framework-tech-unavailable.md) .</span><span class="sxs-lookup"><span data-stu-id="413d3-191">For more information, see the [.NET Framework technologies unavailable on .NET Core and .NET 5+](../../core/porting/net-framework-tech-unavailable.md) article.</span></span>

#### <a name="regenerate-autogenerated-clients"></a><span data-ttu-id="413d3-192">Повторное создание автоматически сформированных клиентов</span><span class="sxs-lookup"><span data-stu-id="413d3-192">Regenerate autogenerated clients</span></span>

<span data-ttu-id="413d3-193">Если приложение использует автоматически сформированный код, например клиент WCF, может потребоваться повторно создать этот код для .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-193">If your application uses autogenerated code, such as a WCF client, you may need to regenerate this code to target .NET.</span></span> <span data-ttu-id="413d3-194">Иногда можно найти некоторые отсутствующие ссылки, так как они могут не быть включены в набор сборок .NET по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="413d3-194">Sometimes, you can find some missing references since they may not be included as part of the default .NET assemblies set.</span></span> <span data-ttu-id="413d3-195">С помощью такого средства <https://apisof.net/> , как, можно легко найти сборку, в которой находится отсутствующая ссылка, и добавить ее из NuGet.</span><span class="sxs-lookup"><span data-stu-id="413d3-195">Using a tool like <https://apisof.net/>, you can easily locate the assembly the missing reference lives in and add it from NuGet.</span></span>

#### <a name="rolling-back-package-versions"></a><span data-ttu-id="413d3-196">Откат версий пакета</span><span class="sxs-lookup"><span data-stu-id="413d3-196">Rolling back package versions</span></span>

<span data-ttu-id="413d3-197">Как правило, мы уже упоминали, что вы лучше обновляете каждую версию одного пакета, чтобы обеспечить совместимость с .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-197">As a general rule, we've previously stated that you better update every single package version to be compatible with .NET.</span></span> <span data-ttu-id="413d3-198">Однако вы можете найти, что для обновленной и совместимой версий сборки просто не взимается.</span><span class="sxs-lookup"><span data-stu-id="413d3-198">However, you can find that targeting an updated and compatible version of an assembly just doesn't pay off.</span></span> <span data-ttu-id="413d3-199">Если стоимость изменения не является приемлемой, можно рассмотреть возможность отката версий пакета, сохраняя те, которые используются в платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="413d3-199">If the cost of change isn't acceptable, you can consider rolling back package versions keeping the ones you use on .NET Framework.</span></span> <span data-ttu-id="413d3-200">Хотя они и не предназначены для .NET, они должны работать, если они не вызывают некоторые неподдерживаемые API.</span><span class="sxs-lookup"><span data-stu-id="413d3-200">Although they may not be targeting .NET, they should work well unless they call some unsupported APIs.</span></span>

### <a name="run-and-test"></a><span data-ttu-id="413d3-201">Запуск и тестирование</span><span class="sxs-lookup"><span data-stu-id="413d3-201">Run and test</span></span>

<span data-ttu-id="413d3-202">После создания приложения без ошибок можно запустить последний шаг миграции, проверив все функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="413d3-202">Once you have your application building with no errors, you can start the last step of the migration by testing every functionality.</span></span>

<span data-ttu-id="413d3-203">На этом заключительном этапе можно найти несколько различных проблем в зависимости от сложности приложения и используемых зависимостей и интерфейсов API.</span><span class="sxs-lookup"><span data-stu-id="413d3-203">In this final step, you can find several different issues depending on the complexity of your application and the dependencies and APIs you're using.</span></span>

<span data-ttu-id="413d3-204">Например, при использовании файлов конфигурации (*app.config*) могут возникнуть ошибки во время выполнения, такие как разделы конфигурации, которые отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="413d3-204">For example, if you use configuration files (*app.config*), you may find some errors at run time like Configuration Sections not present.</span></span> <span data-ttu-id="413d3-205">Использование `Microsoft.Extensions.Configuration` пакета NuGet должно исправить эту ошибку.</span><span class="sxs-lookup"><span data-stu-id="413d3-205">Using the `Microsoft.Extensions.Configuration` NuGet package should fix that error.</span></span>

<span data-ttu-id="413d3-206">Другой причиной ошибок является использование `BeginInvoke` методов и, `EndInvoke` поскольку они не поддерживаются в .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-206">Another reason for errors is the use of the `BeginInvoke` and `EndInvoke` methods because they aren't supported on .NET.</span></span> <span data-ttu-id="413d3-207">Они не поддерживаются в .NET, так как они имеют зависимость от удаленного взаимодействия, которое не существует в .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-207">They aren't supported on .NET because they have a dependency on Remoting, which doesn't exist on .NET.</span></span> <span data-ttu-id="413d3-208">Чтобы решить эту проблему, попробуйте использовать `await` ключевое слово (если доступно) или <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="413d3-208">To solve this issue, try to use the `await` keyword (when available) or the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="413d3-209">Анализаторы совместимости можно использовать для выявления интерфейсов API и шаблонов кода в коде, которые могут вызывать проблемы во время выполнения с помощью .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-209">You can use compatibility analyzers to let you identify APIs and code patterns in your code that can potentially cause problems at run time with .NET.</span></span> <span data-ttu-id="413d3-210">Перейдите на страницу <https://github.com/dotnet/platform-compat> и используйте анализатор .NET API для своего проекта.</span><span class="sxs-lookup"><span data-stu-id="413d3-210">Go to <https://github.com/dotnet/platform-compat> and use the .NET API analyzer on your project.</span></span>

## <a name="migrating-a-windows-forms-application"></a><span data-ttu-id="413d3-211">Перенос приложения Windows Forms</span><span class="sxs-lookup"><span data-stu-id="413d3-211">Migrating a Windows Forms application</span></span>

<span data-ttu-id="413d3-212">Чтобы продемонстрировать полный процесс миграции Windows Forms приложения, мы решили перенести пример приложения Ешоп, доступного по адресу <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="413d3-212">To showcase a complete migration process of a Windows Forms application, we've chosen to migrate the eShop sample application available at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms>.</span></span> <span data-ttu-id="413d3-213">Полный результат миграции можно найти по адресу <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="413d3-213">You can find the complete result of the migration at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms>.</span></span>

<span data-ttu-id="413d3-214">Это приложение показывает Каталог продуктов и позволяет пользователю перемещаться по продуктам, фильтровать их и выполнять поиск.</span><span class="sxs-lookup"><span data-stu-id="413d3-214">This application shows a product catalog and allows the user to navigate, filter, and search for products.</span></span> <span data-ttu-id="413d3-215">С точки зрения архитектуры, приложение использует внешнюю службу WCF, которая служит фасадной для серверной базы данных.</span><span class="sxs-lookup"><span data-stu-id="413d3-215">From an architecture point of view, the app relies on an external WCF service that serves as a façade to a back-end database.</span></span>

<span data-ttu-id="413d3-216">Основное окно приложения можно увидеть на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="413d3-216">You can see the main application window in the following picture:</span></span>

![Главное окно приложения](./media/example-migration-core/main-application-window.png)

<span data-ttu-id="413d3-218">Если открыть *CSPROJ* -файл проекта, можно увидеть примерно следующее:</span><span class="sxs-lookup"><span data-stu-id="413d3-218">If you open the *.csproj* project file, you can see something like this:</span></span>

![Снимок экрана с содержимым файла CSPROJ](./media/example-migration-core/csproj-file.png)

<span data-ttu-id="413d3-220">Как упоминалось ранее, проект .NET имеет более компактный стиль, поэтому необходимо перенести структуру проекта в новый стиль пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-220">As previously mentioned, .NET project has a more compact style and you need to migrate the project structure to the new .NET SDK style.</span></span>

<span data-ttu-id="413d3-221">В Обозреватель решений щелкните правой кнопкой мыши проект Windows Forms и выберите команду **Выгрузить проект**  >  **изменить**.</span><span class="sxs-lookup"><span data-stu-id="413d3-221">In the Solution Explorer, right click on the Windows Forms project and select **Unload Project** > **Edit**.</span></span>

<span data-ttu-id="413d3-222">Теперь можно обновить CSPROJ файл.</span><span class="sxs-lookup"><span data-stu-id="413d3-222">Now you can update the .csproj file.</span></span> <span data-ttu-id="413d3-223">Вы удалите все содержимое и замените его следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="413d3-223">You'll delete the entire content and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="413d3-224">Сохраните и перезагрузите проект.</span><span class="sxs-lookup"><span data-stu-id="413d3-224">Save and reload the project.</span></span> <span data-ttu-id="413d3-225">Теперь обновление файла проекта завершено, и проект предназначен для .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-225">You're now done updating the project file and the project is targeting the .NET.</span></span>

<span data-ttu-id="413d3-226">Если скомпилировать проект на этом этапе, вы найдете некоторые ошибки, связанные со ссылкой на клиент WCF.</span><span class="sxs-lookup"><span data-stu-id="413d3-226">If you compile the project at this point, you'll find some errors related to the WCF client reference.</span></span> <span data-ttu-id="413d3-227">Поскольку этот код создается автоматически, его необходимо создать заново для .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-227">Since this code is autogenerated, you must regenerate it to target .NET.</span></span>

![Снимок экрана с ошибками компиляции в Visual Studio](./media/example-migration-core/winforms-compilation-errors.png)

<span data-ttu-id="413d3-229">Удалите файл *Reference.CS* и создайте новый клиент службы.</span><span class="sxs-lookup"><span data-stu-id="413d3-229">Delete the *Reference.cs* file and generate a new Service Client.</span></span>

<span data-ttu-id="413d3-230">Щелкните правой кнопкой мыши **подключенные службы** и выберите пункт **Добавить подключенную службу** .</span><span class="sxs-lookup"><span data-stu-id="413d3-230">Right-click on **Connected Services** and select the **Add Connected Service** option.</span></span>

![Снимок экрана: меню "Подключенные службы" с выбранным параметром "добавить подключенную службу"](./media/example-migration-core/add-connected-service.png)

<span data-ttu-id="413d3-232">Откроется окно Подключенные службы.</span><span class="sxs-lookup"><span data-stu-id="413d3-232">The Connected Services window opens.</span></span> <span data-ttu-id="413d3-233">Выберите параметр **веб-служба Microsoft WCF** .</span><span class="sxs-lookup"><span data-stu-id="413d3-233">Select the **Microsoft WCF Web Service** option.</span></span>

![Снимок экрана окна Подключенные службы](./media/example-migration-core/connected-services-window.png)

<span data-ttu-id="413d3-235">Если у вас есть служба WCF в том же решении, что и в этом примере, вместо указания URL-адреса службы можно выбрать параметр **Discover** .</span><span class="sxs-lookup"><span data-stu-id="413d3-235">If you have the WCF Service in the same solution as we have in this example, you can select the **Discover** option instead of specifying a service URL.</span></span>

![Снимок экрана: окно "Настройка ссылки на веб-службу WCF"](./media/example-migration-core/configure-wcf-reference.png)

<span data-ttu-id="413d3-237">После обнаружения службы средство отражает контракт API, реализованный службой.</span><span class="sxs-lookup"><span data-stu-id="413d3-237">Once the service is located, the tool reflects the API contract implemented by the service.</span></span> <span data-ttu-id="413d3-238">Измените имя пространства имен, `eShopServiceReference` как показано на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="413d3-238">Change the name of the namespace to be `eShopServiceReference` as shown in the following image:</span></span>

![Снимок экрана: контракт API и пространство имен изменены](./media/example-migration-core/api-contract-namespace.png)

<span data-ttu-id="413d3-240">Нажмите кнопку **Готово** .</span><span class="sxs-lookup"><span data-stu-id="413d3-240">Select the **Finish** button.</span></span> <span data-ttu-id="413d3-241">Через некоторое время вы увидите созданный код.</span><span class="sxs-lookup"><span data-stu-id="413d3-241">After a while, you'll see the generated code.</span></span>

<span data-ttu-id="413d3-242">Вы должны увидеть три автоматически создаваемых файла:</span><span class="sxs-lookup"><span data-stu-id="413d3-242">You should see three autogenerated files:</span></span>

1. <span data-ttu-id="413d3-243">*Начало работы*: ссылка на GitHub, чтобы предоставить некоторую информацию о WCF.</span><span class="sxs-lookup"><span data-stu-id="413d3-243">*Getting Started*: a link to GitHub to provide some information on WCF.</span></span>
2. <span data-ttu-id="413d3-244">*ConnectedService.json*: параметры конфигурации для подключения к службе.</span><span class="sxs-lookup"><span data-stu-id="413d3-244">*ConnectedService.json*: configuration parameters to connect to the service.</span></span>
3. <span data-ttu-id="413d3-245">*Reference.CS*: фактический код клиента WCF.</span><span class="sxs-lookup"><span data-stu-id="413d3-245">*Reference.cs*: the actual WCF client code.</span></span>

![Снимок экрана обозреватель решений окна с тремя автоматически созданными файлами](./media/example-migration-core/autogenerated-files.png)

<span data-ttu-id="413d3-247">При повторной компиляции вы увидите много ошибок, поступающих из файлов *CS* в папку *Helper* .</span><span class="sxs-lookup"><span data-stu-id="413d3-247">If you compile again, you'll see many errors coming from *.cs* files inside the *Helper* folder.</span></span> <span data-ttu-id="413d3-248">Эта папка присутствовала в платформа .NET Framework версии, но не включена в Old *. csproj*.</span><span class="sxs-lookup"><span data-stu-id="413d3-248">This folder was present in the .NET Framework version but not included in the old *.csproj*.</span></span> <span data-ttu-id="413d3-249">Но при использовании нового проекта в стиле SDK каждый файл кода, который находится под расположением файла проекта, включается по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="413d3-249">But with the new SDK-style project, every code file present underneath the project file location is included by default.</span></span> <span data-ttu-id="413d3-250">То есть новый проект .NET Core пытается скомпилировать файлы в папке *Helper* .</span><span class="sxs-lookup"><span data-stu-id="413d3-250">That is, the new .NET Core project tries to compile the files inside the *Helper* folder.</span></span> <span data-ttu-id="413d3-251">Так как эта папка не требуется, ее можно безопасно удалить.</span><span class="sxs-lookup"><span data-stu-id="413d3-251">Since that folder isn't needed, you can safely delete it.</span></span>

<span data-ttu-id="413d3-252">Если скомпилировать проект еще раз и выполнить его, вы не увидите образы продукта.</span><span class="sxs-lookup"><span data-stu-id="413d3-252">If you compile the project again and execute it, you won't see the product images.</span></span> <span data-ttu-id="413d3-253">Проблема заключается в том, что теперь путь к файлам немного изменился.</span><span class="sxs-lookup"><span data-stu-id="413d3-253">The problem is that now the path to the files has slightly changed.</span></span> <span data-ttu-id="413d3-254">Чтобы устранить эту проблему, необходимо добавить в путь другой уровень глубины, обновив в файле `CatalogView.cs` строку:</span><span class="sxs-lookup"><span data-stu-id="413d3-254">To fix this issue, you need to add another level of depth in the path, updating in the file `CatalogView.cs` the line:</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="413d3-255">значение</span><span class="sxs-lookup"><span data-stu-id="413d3-255">to</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="413d3-256">После этого изменения можно убедиться, что приложение запускается и работает должным образом в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="413d3-256">After this change, you can check that the application launches and runs as expected on .NET Core.</span></span>

## <a name="migrating-a-wpf-application"></a><span data-ttu-id="413d3-257">Миграция приложения WPF</span><span class="sxs-lookup"><span data-stu-id="413d3-257">Migrating a WPF application</span></span>

<span data-ttu-id="413d3-258">Мы будем использовать `Shop.ClassicWPF` пример приложения для выполнения миграции.</span><span class="sxs-lookup"><span data-stu-id="413d3-258">We'll use the `Shop.ClassicWPF` sample application to perform the migration.</span></span> <span data-ttu-id="413d3-259">На следующем рисунке показан снимок экрана приложения перед миграцией:</span><span class="sxs-lookup"><span data-stu-id="413d3-259">The following image shows a screenshot of the app before migration:</span></span>

![Пример приложения перед миграцией](./media/example-migration-core/app-before-migration.png)

<span data-ttu-id="413d3-261">Это приложение использует локальную базу данных SQL Server Express для хранения сведений о каталоге продуктов.</span><span class="sxs-lookup"><span data-stu-id="413d3-261">This application uses a local SQL Server Express database to hold the product catalog information.</span></span> <span data-ttu-id="413d3-262">Доступ к этой базе данных осуществляется непосредственно из приложения WPF.</span><span class="sxs-lookup"><span data-stu-id="413d3-262">This database is accessed directly from the WPF application.</span></span>

<span data-ttu-id="413d3-263">Сначала необходимо обновить файл *CSPROJ* до нового стиля SDK, используемого приложениями .NET Core.</span><span class="sxs-lookup"><span data-stu-id="413d3-263">First, you must update the *.csproj* file to the new SDK style used by .NET Core applications.</span></span> <span data-ttu-id="413d3-264">Вы выполните те же действия, которые описаны в Windows Forms миграции: вы выгружаете проект, открываете файл *. csproj* , обновляете его содержимое и перезагружаете проект.</span><span class="sxs-lookup"><span data-stu-id="413d3-264">You'll follow the same steps described in the Windows Forms migration: you'll unload the project, open the *.csproj* file, update its contents, and reload the project.</span></span>

<span data-ttu-id="413d3-265">В этом случае удалите все содержимое файла *CSPROJ* и замените его следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="413d3-265">In this case, delete all the content of the *.csproj* file and replace it with the following code:</span></span>

```xml
 <Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWpf>true</UseWpf>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="413d3-266">Если перезагрузить проект и скомпилировать его, вы получите следующую ошибку:</span><span class="sxs-lookup"><span data-stu-id="413d3-266">If you reload the project and compile it, you'll get the following error:</span></span>

![Снимок экрана с ошибками компиляции в Visual Studio](./media/example-migration-core/wpf-compilation-error.png)

<span data-ttu-id="413d3-268">Так как вы удалили все содержимое *CSPROJ* , вы потеряли спецификацию ссылок проекта, присутствующую в старом проекте.</span><span class="sxs-lookup"><span data-stu-id="413d3-268">Since you've deleted all the *.csproj* contents, you've lost a project reference specification present in the old project.</span></span> <span data-ttu-id="413d3-269">Необходимо просто добавить эту строку в *CSPROJ* файл, чтобы включить ссылку на проект.</span><span class="sxs-lookup"><span data-stu-id="413d3-269">You just need to add this line to the *.csproj* file to include the project reference back:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

<span data-ttu-id="413d3-270">Можно также разрешить Visual Studio, щелкнув правой кнопкой мыши узел **зависимости** и выбрав пункт **Добавить ссылку на проект**.</span><span class="sxs-lookup"><span data-stu-id="413d3-270">You can also let Visual Studio help you by right-clicking on the **Dependencies** node and selecting **Add Project Reference**.</span></span> <span data-ttu-id="413d3-271">Выберите проект из решения и нажмите кнопку " **ОК**":</span><span class="sxs-lookup"><span data-stu-id="413d3-271">Select the project from the solution and click **OK**:</span></span>

![Снимок экрана: диалоговое окно диспетчера ссылок с выбранным проектом Ешоп. дескриптора SqlProvider](./media/example-migration-core/reference-manager.png)

<span data-ttu-id="413d3-273">После добавления ссылки на отсутствующий проект приложение компилируется и выполняется должным образом в .NET.</span><span class="sxs-lookup"><span data-stu-id="413d3-273">Once you add the missing project reference, the application compiles and runs as expected on .NET.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="413d3-274">[Назад](windows-migration.md)
>[Вперед](deploy-modern-applications.md)</span><span class="sxs-lookup"><span data-stu-id="413d3-274">[Previous](windows-migration.md)
[Next](deploy-modern-applications.md)</span></span>
