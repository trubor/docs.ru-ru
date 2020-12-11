---
title: Как осуществляется версионирование в среде выполнения и пакете SDK для .NET
description: В этой статье описано, как осуществляется версионирование в среде выполнения и пакете SDK для .NET (аналогично семантическому версионированию).
ms.date: 12/07/2020
ms.openlocfilehash: 2fe0b162b52f1e4500ec87f7d5d92054cd569552
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009310"
---
# <a name="overview-of-how-net-is-versioned"></a><span data-ttu-id="884b3-103">Общие сведения о версионировании в .NET</span><span class="sxs-lookup"><span data-stu-id="884b3-103">Overview of how .NET is versioned</span></span>

<span data-ttu-id="884b3-104">Новые функции [в среде выполнения и пакете SDK для .NET](../introduction.md#sdk-and-runtimes) добавляются с различной частотой.</span><span class="sxs-lookup"><span data-stu-id="884b3-104">The [.NET Runtime and the .NET SDK](../introduction.md#sdk-and-runtimes) add new features at different frequencies.</span></span> <span data-ttu-id="884b3-105">Как правило, пакет SDK обновляется чаще, чем среда выполнения.</span><span class="sxs-lookup"><span data-stu-id="884b3-105">In general, the SDK is updated more frequently than the Runtime.</span></span> <span data-ttu-id="884b3-106">В этой статье приводятся сведения о нумерации версий среды выполнения и пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="884b3-106">This article explains the runtime and the SDK version numbers.</span></span>

## <a name="versioning-details"></a><span data-ttu-id="884b3-107">Сведения об управлении версиями</span><span class="sxs-lookup"><span data-stu-id="884b3-107">Versioning details</span></span>

<span data-ttu-id="884b3-108">Для среды выполнения .NET используется формат "основной номер версии/дополнительный номер версии/номер исправления", соответствующий [семантическому версионированию](#semantic-versioning).</span><span class="sxs-lookup"><span data-stu-id="884b3-108">The .NET Runtime has a major/minor/patch approach to versioning that follows [semantic versioning](#semantic-versioning).</span></span>

<span data-ttu-id="884b3-109">Пакет SDK для .NET не соблюдает семантическое версионирование.</span><span class="sxs-lookup"><span data-stu-id="884b3-109">The .NET SDK doesn't follow semantic versioning.</span></span> <span data-ttu-id="884b3-110">Новые версии пакета SDK для .NET выпускаются чаще, а их номера версий должны отражать как версию соответствующей среды выполнения, так и собственный дополнительный номер версии и номер исправления пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="884b3-110">The .NET SDK releases faster and its version numbers must communicate both the aligned runtime and the SDK's own minor and patch releases.</span></span>

<span data-ttu-id="884b3-111">Первые две позиции номера версии пакета SDK для .NET резервируются для среды выполнения .NET, с которой он выпускается.</span><span class="sxs-lookup"><span data-stu-id="884b3-111">The first two positions of the .NET SDK version number are locked to the .NET Runtime it released with.</span></span> <span data-ttu-id="884b3-112">Каждая версия пакета SDK позволяет создавать приложения для этой среды выполнения и любых ее предыдущих версий.</span><span class="sxs-lookup"><span data-stu-id="884b3-112">Each version of the SDK can create applications for this runtime or any lower version.</span></span>

<span data-ttu-id="884b3-113">Третья позиция номера версии пакета SDK сообщает дополнительный номер версии и номер исправления.</span><span class="sxs-lookup"><span data-stu-id="884b3-113">The third position of the SDK version number communicates both the minor and patch number.</span></span> <span data-ttu-id="884b3-114">Дополнительный номер версии умножается на 100.</span><span class="sxs-lookup"><span data-stu-id="884b3-114">The minor version is multiplied by 100.</span></span> <span data-ttu-id="884b3-115">Дополнительный номер версии 1 и номер версии исправления 2 будут представлены как "102".</span><span class="sxs-lookup"><span data-stu-id="884b3-115">Minor version 1, patch version 2 would be represented as 102.</span></span> <span data-ttu-id="884b3-116">Последние две цифры означают номер исправления.</span><span class="sxs-lookup"><span data-stu-id="884b3-116">The final two digits represent the patch number.</span></span> <span data-ttu-id="884b3-117">Например, ниже приведена возможная последовательность номеров версий среды выполнения и пакета SDK:</span><span class="sxs-lookup"><span data-stu-id="884b3-117">For example, here's a possible sequence of runtime and SDK version numbers:</span></span>

| <span data-ttu-id="884b3-118">Change</span><span class="sxs-lookup"><span data-stu-id="884b3-118">Change</span></span>                | <span data-ttu-id="884b3-119">Среда выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="884b3-119">.NET Runtime</span></span>      | <span data-ttu-id="884b3-120">Пакет SDK для .NET (\*)</span><span class="sxs-lookup"><span data-stu-id="884b3-120">.NET SDK (\*)</span></span>     |
|-----------------------|-------------------|-------------------|
| <span data-ttu-id="884b3-121">Начальный выпуск</span><span class="sxs-lookup"><span data-stu-id="884b3-121">Initial release</span></span>       | <span data-ttu-id="884b3-122">2.2.0</span><span class="sxs-lookup"><span data-stu-id="884b3-122">2.2.0</span></span>             | <span data-ttu-id="884b3-123">2.2.100</span><span class="sxs-lookup"><span data-stu-id="884b3-123">2.2.100</span></span>           |
| <span data-ttu-id="884b3-124">Исправление для пакета SDK</span><span class="sxs-lookup"><span data-stu-id="884b3-124">SDK Patch</span></span>             | <span data-ttu-id="884b3-125">2.2.0</span><span class="sxs-lookup"><span data-stu-id="884b3-125">2.2.0</span></span>             | <span data-ttu-id="884b3-126">2.2.101</span><span class="sxs-lookup"><span data-stu-id="884b3-126">2.2.101</span></span>           |
| <span data-ttu-id="884b3-127">Среда выполнения и исправление пакета SDK</span><span class="sxs-lookup"><span data-stu-id="884b3-127">Runtime and SDK Patch</span></span> | <span data-ttu-id="884b3-128">2.2.1</span><span class="sxs-lookup"><span data-stu-id="884b3-128">2.2.1</span></span>             | <span data-ttu-id="884b3-129">2.2.102</span><span class="sxs-lookup"><span data-stu-id="884b3-129">2.2.102</span></span>           |
| <span data-ttu-id="884b3-130">Изменение функций пакета SDK</span><span class="sxs-lookup"><span data-stu-id="884b3-130">SDK Feature change</span></span>    | <span data-ttu-id="884b3-131">2.2.1</span><span class="sxs-lookup"><span data-stu-id="884b3-131">2.2.1</span></span>             | <span data-ttu-id="884b3-132">2.2.200</span><span class="sxs-lookup"><span data-stu-id="884b3-132">2.2.200</span></span>           |

<span data-ttu-id="884b3-133">Примечания:</span><span class="sxs-lookup"><span data-stu-id="884b3-133">NOTES:</span></span>

- <span data-ttu-id="884b3-134">Если перед обновлением компонентов среды выполнения выходит 10 обновлений компонентов пакета SDK, номера версий переходят на числа более 1000. Например, за выпуском 2.2.900 следует версия с номером 2.2.1000.</span><span class="sxs-lookup"><span data-stu-id="884b3-134">If the SDK has 10 feature updates before a runtime feature update, version numbers roll into the 1000 series with numbers like 2.2.1000 as the feature release following 2.2.900.</span></span> <span data-ttu-id="884b3-135">Такая ситуация является маловероятной.</span><span class="sxs-lookup"><span data-stu-id="884b3-135">This situation isn't expected to occur.</span></span>
- <span data-ttu-id="884b3-136">То есть 99 выпусков исправлений без выпуска компонентов не произойдет.</span><span class="sxs-lookup"><span data-stu-id="884b3-136">99 patch releases without a feature release won't occur.</span></span> <span data-ttu-id="884b3-137">Если версия выпуска приближается к такому номеру, неизбежно выходит выпуск компонентов.</span><span class="sxs-lookup"><span data-stu-id="884b3-137">If a release approaches this number, it forces a feature release.</span></span>

<span data-ttu-id="884b3-138">Дополнительные сведения см. в начальном предложении в репозитории [dotnet/designs](https://github.com/dotnet/designs/pull/29).</span><span class="sxs-lookup"><span data-stu-id="884b3-138">You can see more details in the initial proposal at the [dotnet/designs](https://github.com/dotnet/designs/pull/29) repository.</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="884b3-139">Семантическое версионирование</span><span class="sxs-lookup"><span data-stu-id="884b3-139">Semantic versioning</span></span>

<span data-ttu-id="884b3-140">*Среда выполнения* .NET в основном использует [семантическое версионирование (SemVer)](https://semver.org/) с шаблоном номера версии `MAJOR.MINOR.PATCH`, различные части которого служат для описания степени и типа изменений.</span><span class="sxs-lookup"><span data-stu-id="884b3-140">The .NET *Runtime* roughly adheres to [Semantic Versioning (SemVer)](https://semver.org/), adopting the use of `MAJOR.MINOR.PATCH` versioning, using the various parts of the version number to describe the degree and type of change.</span></span>

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

<span data-ttu-id="884b3-141">Необязательные части `PRERELEASE` и `BUILDNUMBER` никогда не используются в поддерживаемых выпусках и применяются только для ночных сборок, локальных сборок, которые создаются из исходных целевых объектов, и неподдерживаемых предварительных выпусков.</span><span class="sxs-lookup"><span data-stu-id="884b3-141">The optional `PRERELEASE` and `BUILDNUMBER` parts are never part of supported releases and only exist on nightly builds, local builds from source targets, and unsupported preview releases.</span></span>

### <a name="understand-runtime-version-number-changes"></a><span data-ttu-id="884b3-142">Общие сведения об изменениях номера версии среды выполнения</span><span class="sxs-lookup"><span data-stu-id="884b3-142">Understand runtime version number changes</span></span>

<span data-ttu-id="884b3-143">`MAJOR` увеличивается в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="884b3-143">`MAJOR` is incremented when:</span></span>

- <span data-ttu-id="884b3-144">Значительные изменения или новое направление развития продукта.</span><span class="sxs-lookup"><span data-stu-id="884b3-144">Significant changes occur to the product, or a new product direction.</span></span>
- <span data-ttu-id="884b3-145">Критические изменения.</span><span class="sxs-lookup"><span data-stu-id="884b3-145">Breaking changes were taken.</span></span> <span data-ttu-id="884b3-146">Для принятия критических изменений действует высокая планка.</span><span class="sxs-lookup"><span data-stu-id="884b3-146">There's a high bar to accepting breaking changes.</span></span>
- <span data-ttu-id="884b3-147">Старая версия больше не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="884b3-147">An old version is no longer supported.</span></span>
- <span data-ttu-id="884b3-148">Присваивается более новая версия `MAJOR` существующей зависимости.</span><span class="sxs-lookup"><span data-stu-id="884b3-148">A newer `MAJOR` version of an existing dependency is adopted.</span></span>

<span data-ttu-id="884b3-149">`MINOR` увеличивается в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="884b3-149">`MINOR` is incremented when:</span></span>

- <span data-ttu-id="884b3-150">Добавляется контактная зона общедоступного API.</span><span class="sxs-lookup"><span data-stu-id="884b3-150">Public API surface area is added.</span></span>
- <span data-ttu-id="884b3-151">Добавляется новое поведение.</span><span class="sxs-lookup"><span data-stu-id="884b3-151">A new behavior is added.</span></span>
- <span data-ttu-id="884b3-152">Присваивается более новая версия `MINOR` существующей зависимости.</span><span class="sxs-lookup"><span data-stu-id="884b3-152">A newer `MINOR` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="884b3-153">Добавляется новая зависимость.</span><span class="sxs-lookup"><span data-stu-id="884b3-153">A new dependency is introduced.</span></span>

<span data-ttu-id="884b3-154">`PATCH` увеличивается в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="884b3-154">`PATCH` is incremented when:</span></span>

- <span data-ttu-id="884b3-155">Вносятся исправления ошибок.</span><span class="sxs-lookup"><span data-stu-id="884b3-155">Bug fixes are made.</span></span>
- <span data-ttu-id="884b3-156">Добавляется поддержка новой платформы.</span><span class="sxs-lookup"><span data-stu-id="884b3-156">Support for a newer platform is added.</span></span>
- <span data-ttu-id="884b3-157">Присваивается более новая версия `PATCH` существующей зависимости.</span><span class="sxs-lookup"><span data-stu-id="884b3-157">A newer `PATCH` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="884b3-158">Вносятся другие изменения, которые не относятся к описанным выше случаям.</span><span class="sxs-lookup"><span data-stu-id="884b3-158">Any other change doesn't fit one of the previous cases.</span></span>

<span data-ttu-id="884b3-159">При наличии нескольких изменений увеличивается самый высокий элемент, затронутый отдельными изменениями, а следующие за ним сбрасываются до нуля.</span><span class="sxs-lookup"><span data-stu-id="884b3-159">When there are multiple changes, the highest element affected by individual changes is incremented, and the following ones are reset to zero.</span></span> <span data-ttu-id="884b3-160">Например, когда `MAJOR` увеличивается, `MINOR` и `PATCH` сбрасываются в нуль.</span><span class="sxs-lookup"><span data-stu-id="884b3-160">For example, when `MAJOR` is incremented, `MINOR` and `PATCH` are reset to zero.</span></span> <span data-ttu-id="884b3-161">Когда `MINOR` увеличивается, `PATCH` сбрасываются в нуль, а `MAJOR` остается без изменений.</span><span class="sxs-lookup"><span data-stu-id="884b3-161">When `MINOR` is incremented, `PATCH` is reset to zero while `MAJOR` is left untouched.</span></span>

## <a name="version-numbers-in-file-names"></a><span data-ttu-id="884b3-162">Номера версий в именах файлов</span><span class="sxs-lookup"><span data-stu-id="884b3-162">Version numbers in file names</span></span>

<span data-ttu-id="884b3-163">Файлы, скачанные для .NET, имеют версию, например: `dotnet-sdk-2.1.300-win10-x64.exe`.</span><span class="sxs-lookup"><span data-stu-id="884b3-163">The files downloaded for .NET carry the version, for example, `dotnet-sdk-2.1.300-win10-x64.exe`.</span></span>

### <a name="preview-versions"></a><span data-ttu-id="884b3-164">Предварительные версии</span><span class="sxs-lookup"><span data-stu-id="884b3-164">Preview versions</span></span>

<span data-ttu-id="884b3-165">Для предварительных версий к номеру версии добавляется `-preview[number]-([build]|"final")`.</span><span class="sxs-lookup"><span data-stu-id="884b3-165">Preview versions have a `-preview[number]-([build]|"final")` appended to the version number.</span></span> <span data-ttu-id="884b3-166">Например, `2.0.0-preview1-final`.</span><span class="sxs-lookup"><span data-stu-id="884b3-166">For example, `2.0.0-preview1-final`.</span></span>

### <a name="servicing-versions"></a><span data-ttu-id="884b3-167">Сервисные версии</span><span class="sxs-lookup"><span data-stu-id="884b3-167">Servicing versions</span></span>

<span data-ttu-id="884b3-168">После выхода выпуска его ветви обычно перестают создавать ежедневные сборки и вместо них начинают формировать сервисные сборки.</span><span class="sxs-lookup"><span data-stu-id="884b3-168">After a release goes out, the release branches generally stop producing daily builds and instead start producing servicing builds.</span></span> <span data-ttu-id="884b3-169">Для сервисных версий к номеру версии добавляется `-servicing-[number]`.</span><span class="sxs-lookup"><span data-stu-id="884b3-169">Servicing versions have a `-servicing-[number]` appended to the version.</span></span> <span data-ttu-id="884b3-170">Например, `2.0.1-servicing-006924`.</span><span class="sxs-lookup"><span data-stu-id="884b3-170">For example, `2.0.1-servicing-006924`.</span></span>

## <a name="relationship-to-net-standard-versions"></a><span data-ttu-id="884b3-171">Связь с версиями .NET Standard</span><span class="sxs-lookup"><span data-stu-id="884b3-171">Relationship to .NET Standard versions</span></span>

<span data-ttu-id="884b3-172">.NET Standard состоит из базовой сборки .NET.</span><span class="sxs-lookup"><span data-stu-id="884b3-172">.NET Standard consists of a .NET reference assembly.</span></span> <span data-ttu-id="884b3-173">Существует множество реализаций, соответствующих конкретным платформам.</span><span class="sxs-lookup"><span data-stu-id="884b3-173">There are multiple implementations specific to each platform.</span></span> <span data-ttu-id="884b3-174">Базовая сборка содержит определение API-интерфейсов .NET, которые являются частью определенной версии .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="884b3-174">The reference assembly contains the definition of .NET APIs which are part of a given .NET Standard version.</span></span> <span data-ttu-id="884b3-175">Каждая реализация выполняет контракт .NET Standard на конкретной платформе.</span><span class="sxs-lookup"><span data-stu-id="884b3-175">Each implementation fulfills the .NET Standard contract on the specific platform.</span></span>

<span data-ttu-id="884b3-176">Базовая сборка .NET Standard использует схему управления версиями `MAJOR.MINOR`.</span><span class="sxs-lookup"><span data-stu-id="884b3-176">The .NET Standard reference assembly uses a `MAJOR.MINOR` versioning scheme.</span></span> <span data-ttu-id="884b3-177">Уровень `PATCH` бесполезен для .NET Standard, так как он предоставляет только спецификацию API (без реализации), а по определению любое изменение в API соответствует изменению набора возможностей и, таким образом, новой версии `MINOR`.</span><span class="sxs-lookup"><span data-stu-id="884b3-177">`PATCH` level isn't useful for .NET Standard because it exposes only an API specification (no implementation) and by definition any change to the API would represent a change in the feature set, and thus a new `MINOR` version.</span></span>

<span data-ttu-id="884b3-178">Реализации на каждой платформе обычно обновляются в составе выпуска под эту платформу и потому незаметны для программистов, использующих на ней .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="884b3-178">The implementations on each platform may be updated, typically as part of the platform release, and thus not evident to the programmers using .NET Standard on that platform.</span></span>

<span data-ttu-id="884b3-179">Дополнительные сведения см. в статье [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="884b3-179">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="884b3-180">См. также</span><span class="sxs-lookup"><span data-stu-id="884b3-180">See also</span></span>

- [<span data-ttu-id="884b3-181">Целевые платформы</span><span class="sxs-lookup"><span data-stu-id="884b3-181">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="884b3-182">Упаковка дистрибутивов .NET</span><span class="sxs-lookup"><span data-stu-id="884b3-182">.NET distribution packaging</span></span>](../distribution-packaging.md)
- [<span data-ttu-id="884b3-183">Справочные материалы по жизненному циклу поддержки .NET</span><span class="sxs-lookup"><span data-stu-id="884b3-183">.NET Support Lifecycle Fact Sheet</span></span>](https://dotnet.microsoft.com/platform/support/policy)
- [<span data-ttu-id="884b3-184">Образы Docker для .NET</span><span class="sxs-lookup"><span data-stu-id="884b3-184">Docker images for .NET</span></span>](https://hub.docker.com/_/microsoft-dotnet/)
