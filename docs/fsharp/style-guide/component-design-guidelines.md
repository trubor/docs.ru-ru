---
title: Рекомендации по проектированию компонентов F#
description: 'Ознакомьтесь с рекомендациями по написанию компонентов F #, предназначенных для использования другими вызывающими объектами.'
ms.date: 05/14/2018
ms.openlocfilehash: 24be2a422c97b9334f749e3d9dfcccd0feec219b
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856111"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="3897c-103">Рекомендации по проектированию компонентов F#</span><span class="sxs-lookup"><span data-stu-id="3897c-103">F# component design guidelines</span></span>

<span data-ttu-id="3897c-104">Этот документ представляет собой набор руководств по проектированию компонентов для программирования на F #, основанный на рекомендациях по проектированию компонентов F #, 14, Microsoft Research и версии, изначально проверенной и поддерживаемой в F # Software Foundation.</span><span class="sxs-lookup"><span data-stu-id="3897c-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and a version that was originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="3897c-105">В этом документе предполагается, что вы знакомы с программированием на F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="3897c-106">Многие благодаря сообществу F # для своих вкладов и полезные отзывы о различных версиях этого руководством.</span><span class="sxs-lookup"><span data-stu-id="3897c-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="3897c-107">Обзор</span><span class="sxs-lookup"><span data-stu-id="3897c-107">Overview</span></span>

<span data-ttu-id="3897c-108">В этом документе рассматриваются некоторые проблемы, связанные с проектированием компонентов и программированием F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="3897c-109">Компонент может иметь одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="3897c-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="3897c-110">Слой в проекте F #, содержащий внешних потребителей в рамках этого проекта.</span><span class="sxs-lookup"><span data-stu-id="3897c-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="3897c-111">Библиотека, предназначенная для использования кодом F # через границы сборки.</span><span class="sxs-lookup"><span data-stu-id="3897c-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="3897c-112">Библиотека, предназначенная для использования любым языком .NET через границы сборки.</span><span class="sxs-lookup"><span data-stu-id="3897c-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="3897c-113">Библиотека, предназначенная для распространения через репозиторий пакетов, например [NuGet](https://nuget.org).</span><span class="sxs-lookup"><span data-stu-id="3897c-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="3897c-114">Методы, описанные в этой статье, соответствуют [пяти принципам хорошего кода F #](index.md#five-principles-of-good-f-code), и поэтому при необходимости используются как функциональное, так и объектное программирование.</span><span class="sxs-lookup"><span data-stu-id="3897c-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="3897c-115">Независимо от методологии конструктор компонента и библиотеки сталкивается с несколькими практичными и просаик проблемами при попытке создания API, который проще использовать для разработчиков.</span><span class="sxs-lookup"><span data-stu-id="3897c-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="3897c-116">КонсЦиентиаус применение рекомендаций по [проектированию библиотеки .NET](../../standard/design-guidelines/index.md) поможет вам создать единообразный набор API-интерфейсов, которые приятный использовать.</span><span class="sxs-lookup"><span data-stu-id="3897c-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="3897c-117">Общие рекомендации</span><span class="sxs-lookup"><span data-stu-id="3897c-117">General guidelines</span></span>

<span data-ttu-id="3897c-118">Существует несколько универсальных рекомендаций, применяемых к библиотекам F #, независимо от предполагаемой аудитории для библиотеки.</span><span class="sxs-lookup"><span data-stu-id="3897c-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="3897c-119">Ознакомьтесь с рекомендациями по проектированию библиотеки .NET</span><span class="sxs-lookup"><span data-stu-id="3897c-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="3897c-120">Независимо от типа кода F # очень важно иметь опыт работы с [рекомендациями по проектированию библиотеки .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="3897c-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="3897c-121">Большинство других программистов F # и .NET будут знакомы с этими рекомендациями и хотят, чтобы код .NET соответствовал им.</span><span class="sxs-lookup"><span data-stu-id="3897c-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="3897c-122">Рекомендации по проектированию библиотек .NET предоставляют общие рекомендации по именованию, проектированию классов и интерфейсов, проектированию элементов (свойствам, методам, событиям и т. д.) и т. д. — это полезная первая ссылка на множество руководств по проектированию.</span><span class="sxs-lookup"><span data-stu-id="3897c-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="3897c-123">Добавление комментариев XML-документации в код</span><span class="sxs-lookup"><span data-stu-id="3897c-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="3897c-124">Документация по XML на общедоступных интерфейсах API гарантирует, что пользователи смогут получить отличные IntelliSense и краткие сведения при использовании этих типов и членов, а также включить создание файлов документации для библиотеки.</span><span class="sxs-lookup"><span data-stu-id="3897c-124">XML documentation on public APIs ensures that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="3897c-125">См. [XML-документацию](../language-reference/xml-documentation.md) по различным XML-тегам, которые можно использовать для дополнительной разметки в комментариях xmlDoc.</span><span class="sxs-lookup"><span data-stu-id="3897c-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

<span data-ttu-id="3897c-126">Можно использовать либо краткие XML-комментарии ( `/// comment` ), либо стандартные комментарии XML ( `///<summary>comment</summary>` ).</span><span class="sxs-lookup"><span data-stu-id="3897c-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="3897c-127">Рассмотрите возможность использования явных файлов сигнатур (. FSI) для стабильных API библиотек и компонентов</span><span class="sxs-lookup"><span data-stu-id="3897c-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="3897c-128">Использование явных файлов сигнатур в библиотеке F # предоставляет краткий обзор общедоступного API, который помогает гарантировать полную открытую область библиотеки и обеспечивает четкое разделение между общедоступной документацией и подробными сведениями о реализации.</span><span class="sxs-lookup"><span data-stu-id="3897c-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which helps to ensure that you know the full public surface of your library, and provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="3897c-129">Файлы сигнатур добавляют трение для изменения общедоступного API, путем внесения изменений в файлы реализации и сигнатуры.</span><span class="sxs-lookup"><span data-stu-id="3897c-129">Signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="3897c-130">В результате файлы сигнатур обычно должны быть введены, только если API стал упрочило и больше не должен меняться.</span><span class="sxs-lookup"><span data-stu-id="3897c-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="3897c-131">Всегда следуйте рекомендациям по использованию строк в .NET</span><span class="sxs-lookup"><span data-stu-id="3897c-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="3897c-132">Следуйте рекомендациям по [использованию строк в](../../standard/base-types/best-practices-strings.md) руководстве по .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="3897c-133">В частности, всегда следует явно задавать *культурное намерение* при преобразовании и сравнении строк (где применимо).</span><span class="sxs-lookup"><span data-stu-id="3897c-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="3897c-134">Рекомендации для библиотек, доступных в F #</span><span class="sxs-lookup"><span data-stu-id="3897c-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="3897c-135">В этом разделе представлены рекомендации по разработке общедоступных библиотек F #. Это значит, что библиотеки предоставляют общедоступные API, предназначенные для использования разработчиками F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="3897c-136">Существуют разнообразные рекомендации по проектированию библиотек, применимые специально для F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="3897c-137">В отсутствие конкретных рекомендаций, описанных ниже, руководства по проектированию библиотек .NET являются резервными.</span><span class="sxs-lookup"><span data-stu-id="3897c-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="3897c-138">Соглашения об именах</span><span class="sxs-lookup"><span data-stu-id="3897c-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="3897c-139">Использовать соглашения об именовании и капитализации .NET</span><span class="sxs-lookup"><span data-stu-id="3897c-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="3897c-140">В следующей таблице приведены соглашения об именовании и капитализации .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="3897c-141">Существуют небольшие дополнения, которые также включают конструкции F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="3897c-142">Конструкция</span><span class="sxs-lookup"><span data-stu-id="3897c-142">Construct</span></span> | <span data-ttu-id="3897c-143">Случай</span><span class="sxs-lookup"><span data-stu-id="3897c-143">Case</span></span> | <span data-ttu-id="3897c-144">Отделение</span><span class="sxs-lookup"><span data-stu-id="3897c-144">Part</span></span> | <span data-ttu-id="3897c-145">Примеры</span><span class="sxs-lookup"><span data-stu-id="3897c-145">Examples</span></span> | <span data-ttu-id="3897c-146">Примечания</span><span class="sxs-lookup"><span data-stu-id="3897c-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="3897c-147">Конкретные типы</span><span class="sxs-lookup"><span data-stu-id="3897c-147">Concrete types</span></span> | <span data-ttu-id="3897c-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="3897c-148">PascalCase</span></span> | <span data-ttu-id="3897c-149">Существительное или прилагательное</span><span class="sxs-lookup"><span data-stu-id="3897c-149">Noun/ adjective</span></span> | <span data-ttu-id="3897c-150">List, Double, Complex</span><span class="sxs-lookup"><span data-stu-id="3897c-150">List, Double, Complex</span></span> | <span data-ttu-id="3897c-151">Конкретные типы — это структуры, классы, перечисления, делегаты, записи и объединения.</span><span class="sxs-lookup"><span data-stu-id="3897c-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="3897c-152">Хотя в OCaml имена типов традиционно строчные, F # использует схему именования .NET для типов.</span><span class="sxs-lookup"><span data-stu-id="3897c-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="3897c-153">библиотеки DLL</span><span class="sxs-lookup"><span data-stu-id="3897c-153">DLLs</span></span>           | <span data-ttu-id="3897c-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="3897c-154">PascalCase</span></span> |                 | <span data-ttu-id="3897c-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="3897c-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="3897c-156">Теги объединения</span><span class="sxs-lookup"><span data-stu-id="3897c-156">Union tags</span></span>     | <span data-ttu-id="3897c-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="3897c-157">PascalCase</span></span> | <span data-ttu-id="3897c-158">Имя существительное</span><span class="sxs-lookup"><span data-stu-id="3897c-158">Noun</span></span> | <span data-ttu-id="3897c-159">Некоторые, добавление, успешное выполнение</span><span class="sxs-lookup"><span data-stu-id="3897c-159">Some, Add, Success</span></span> | <span data-ttu-id="3897c-160">Не используйте префикс в общедоступных API.</span><span class="sxs-lookup"><span data-stu-id="3897c-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="3897c-161">При необходимости используйте префикс при внутренних функциях, например `type Teams = TAlpha | TBeta | TDelta.`</span><span class="sxs-lookup"><span data-stu-id="3897c-161">Optionally use a prefix when internal, such as `type Teams = TAlpha | TBeta | TDelta.`</span></span> |
| <span data-ttu-id="3897c-162">Событие</span><span class="sxs-lookup"><span data-stu-id="3897c-162">Event</span></span>          | <span data-ttu-id="3897c-163">PascalCase</span><span class="sxs-lookup"><span data-stu-id="3897c-163">PascalCase</span></span> | <span data-ttu-id="3897c-164">Команда</span><span class="sxs-lookup"><span data-stu-id="3897c-164">Verb</span></span> | <span data-ttu-id="3897c-165">ValueChanged/Валуечангинг</span><span class="sxs-lookup"><span data-stu-id="3897c-165">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="3897c-166">Исключения</span><span class="sxs-lookup"><span data-stu-id="3897c-166">Exceptions</span></span>     | <span data-ttu-id="3897c-167">PascalCase</span><span class="sxs-lookup"><span data-stu-id="3897c-167">PascalCase</span></span> |      | <span data-ttu-id="3897c-168">WebException</span><span class="sxs-lookup"><span data-stu-id="3897c-168">WebException</span></span> | <span data-ttu-id="3897c-169">Имя должно заканчиваться на "Exception".</span><span class="sxs-lookup"><span data-stu-id="3897c-169">Name should end with "Exception".</span></span> |
| <span data-ttu-id="3897c-170">Поле</span><span class="sxs-lookup"><span data-stu-id="3897c-170">Field</span></span>          | <span data-ttu-id="3897c-171">PascalCase</span><span class="sxs-lookup"><span data-stu-id="3897c-171">PascalCase</span></span> | <span data-ttu-id="3897c-172">Имя существительное</span><span class="sxs-lookup"><span data-stu-id="3897c-172">Noun</span></span> | <span data-ttu-id="3897c-173">куррентнаме</span><span class="sxs-lookup"><span data-stu-id="3897c-173">CurrentName</span></span>  | |
| <span data-ttu-id="3897c-174">Типы интерфейса</span><span class="sxs-lookup"><span data-stu-id="3897c-174">Interface types</span></span> |  <span data-ttu-id="3897c-175">PascalCase</span><span class="sxs-lookup"><span data-stu-id="3897c-175">PascalCase</span></span> | <span data-ttu-id="3897c-176">Существительное или прилагательное</span><span class="sxs-lookup"><span data-stu-id="3897c-176">Noun/ adjective</span></span> | <span data-ttu-id="3897c-177">IDisposable</span><span class="sxs-lookup"><span data-stu-id="3897c-177">IDisposable</span></span> | <span data-ttu-id="3897c-178">Имя должно начинаться с "I".</span><span class="sxs-lookup"><span data-stu-id="3897c-178">Name should start with "I".</span></span> |
| <span data-ttu-id="3897c-179">Метод</span><span class="sxs-lookup"><span data-stu-id="3897c-179">Method</span></span> |  <span data-ttu-id="3897c-180">PascalCase</span><span class="sxs-lookup"><span data-stu-id="3897c-180">PascalCase</span></span> |  <span data-ttu-id="3897c-181">Команда</span><span class="sxs-lookup"><span data-stu-id="3897c-181">Verb</span></span> | <span data-ttu-id="3897c-182">ToString</span><span class="sxs-lookup"><span data-stu-id="3897c-182">ToString</span></span> | |
| <span data-ttu-id="3897c-183">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="3897c-183">Namespace</span></span> | <span data-ttu-id="3897c-184">PascalCase</span><span class="sxs-lookup"><span data-stu-id="3897c-184">PascalCase</span></span> | | <span data-ttu-id="3897c-185">Microsoft.FSharp.Core</span><span class="sxs-lookup"><span data-stu-id="3897c-185">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="3897c-186">В целом `<Organization>.<Technology>[.<Subnamespace>]` , если технология не зависит от Организации, следует удалить организацию.</span><span class="sxs-lookup"><span data-stu-id="3897c-186">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="3897c-187">Параметры</span><span class="sxs-lookup"><span data-stu-id="3897c-187">Parameters</span></span> | <span data-ttu-id="3897c-188">camelCase</span><span class="sxs-lookup"><span data-stu-id="3897c-188">camelCase</span></span> | <span data-ttu-id="3897c-189">Имя существительное</span><span class="sxs-lookup"><span data-stu-id="3897c-189">Noun</span></span> |  <span data-ttu-id="3897c-190">typeName, Transform, Range</span><span class="sxs-lookup"><span data-stu-id="3897c-190">typeName, transform, range</span></span> | |
| <span data-ttu-id="3897c-191">Разрешить значения (внутренние)</span><span class="sxs-lookup"><span data-stu-id="3897c-191">let values (internal)</span></span> | <span data-ttu-id="3897c-192">camelCase или PascalCase</span><span class="sxs-lookup"><span data-stu-id="3897c-192">camelCase or PascalCase</span></span> | <span data-ttu-id="3897c-193">Существительное или глагол</span><span class="sxs-lookup"><span data-stu-id="3897c-193">Noun/ verb</span></span> |  <span data-ttu-id="3897c-194">getValue, myTable</span><span class="sxs-lookup"><span data-stu-id="3897c-194">getValue, myTable</span></span> |
| <span data-ttu-id="3897c-195">Разрешить значения (внешние)</span><span class="sxs-lookup"><span data-stu-id="3897c-195">let values (external)</span></span> | <span data-ttu-id="3897c-196">camelCase или PascalCase</span><span class="sxs-lookup"><span data-stu-id="3897c-196">camelCase or PascalCase</span></span> | <span data-ttu-id="3897c-197">Существительное или глагол</span><span class="sxs-lookup"><span data-stu-id="3897c-197">Noun/verb</span></span>  | <span data-ttu-id="3897c-198">List. Map, dates. Today</span><span class="sxs-lookup"><span data-stu-id="3897c-198">List.map, Dates.Today</span></span> | <span data-ttu-id="3897c-199">значения, связанные с let, часто являются общедоступными при использовании традиционных шаблонов функционального проектирования.</span><span class="sxs-lookup"><span data-stu-id="3897c-199">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="3897c-200">Однако обычно используется PascalCase, если идентификатор можно использовать из других языков .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-200">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="3897c-201">Свойство</span><span class="sxs-lookup"><span data-stu-id="3897c-201">Property</span></span>  | <span data-ttu-id="3897c-202">PascalCase</span><span class="sxs-lookup"><span data-stu-id="3897c-202">PascalCase</span></span>  | <span data-ttu-id="3897c-203">Существительное или прилагательное</span><span class="sxs-lookup"><span data-stu-id="3897c-203">Noun/ adjective</span></span>  | <span data-ttu-id="3897c-204">Исендоффиле, BackColor</span><span class="sxs-lookup"><span data-stu-id="3897c-204">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="3897c-205">Как правило, логические свойства используют, и могут быть голосами подтверждающими, как в Исендоффиле, а не Иснотендоффиле.</span><span class="sxs-lookup"><span data-stu-id="3897c-205">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="3897c-206">Избегайте сокращений</span><span class="sxs-lookup"><span data-stu-id="3897c-206">Avoid abbreviations</span></span>

<span data-ttu-id="3897c-207">В рекомендациях .NET не следует использовать аббревиатуры (например, «use», `OnButtonClick` а не `OnBtnClick` «»).</span><span class="sxs-lookup"><span data-stu-id="3897c-207">The .NET guidelines discourage the use of abbreviations (for example, "use `OnButtonClick` rather than `OnBtnClick`").</span></span> <span data-ttu-id="3897c-208">Допустимы стандартные аббревиатуры, например `Async` "асинхронный".</span><span class="sxs-lookup"><span data-stu-id="3897c-208">Common abbreviations, such as `Async` for "Asynchronous", are tolerated.</span></span> <span data-ttu-id="3897c-209">Это правило иногда игнорируется для функционального программирования. Например, `List.iter` использует аббревиатуру для "итерации".</span><span class="sxs-lookup"><span data-stu-id="3897c-209">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for "iterate".</span></span> <span data-ttu-id="3897c-210">По этой причине использование сокращений обычно допускает большую степень в программировании F # в-F #, но ее следует избегать в проектировании общедоступных компонентов.</span><span class="sxs-lookup"><span data-stu-id="3897c-210">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="3897c-211">Избегайте конфликтов имен регистров</span><span class="sxs-lookup"><span data-stu-id="3897c-211">Avoid casing name collisions</span></span>

<span data-ttu-id="3897c-212">В рекомендациях .NET говорится, что регистр не может использоваться для неоднозначности конфликтов имен, так как некоторые клиентские языки (например, Visual Basic) не учитывают регистр.</span><span class="sxs-lookup"><span data-stu-id="3897c-212">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="3897c-213">Используйте акронимы там, где это необходимо</span><span class="sxs-lookup"><span data-stu-id="3897c-213">Use acronyms where appropriate</span></span>

<span data-ttu-id="3897c-214">Акронимы, такие как XML, не являются аббревиатурами и широко используются в библиотеках .NET в формах без заглавных букв (XML).</span><span class="sxs-lookup"><span data-stu-id="3897c-214">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="3897c-215">Следует использовать только хорошо известные, широко распознаваемые акронимы.</span><span class="sxs-lookup"><span data-stu-id="3897c-215">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="3897c-216">Использовать PascalCase для имен универсальных параметров</span><span class="sxs-lookup"><span data-stu-id="3897c-216">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="3897c-217">Используйте PascalCase для универсальных имен параметров в общедоступных API, включая библиотеки для F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-217">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="3897c-218">В частности, используйте такие имена `T` , как,,, `U` `T1` `T2` для произвольных универсальных параметров, и если конкретные имена имеют смысл, то для библиотек, предназначенных для F #, используйте такие имена `Key` , как, `Value` , `Arg` (но не например, `TKey` ).</span><span class="sxs-lookup"><span data-stu-id="3897c-218">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="3897c-219">Использование PascalCase или camelCase для открытых функций и значений в модулях F #</span><span class="sxs-lookup"><span data-stu-id="3897c-219">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="3897c-220">camelCase используется для открытых функций, предназначенных для использования в качестве неквалифицированных (например, `invalidArg` ), и для "стандартных функций сбора" (например, List. Map).</span><span class="sxs-lookup"><span data-stu-id="3897c-220">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the "standard collection functions" (for example, List.map).</span></span> <span data-ttu-id="3897c-221">В обоих этих случаях имена функций действуют примерно так же, как ключевые слова языка.</span><span class="sxs-lookup"><span data-stu-id="3897c-221">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="3897c-222">Разработка объектов, типов и модулей</span><span class="sxs-lookup"><span data-stu-id="3897c-222">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="3897c-223">Использование пространств имен или модулей для хранения типов и модулей</span><span class="sxs-lookup"><span data-stu-id="3897c-223">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="3897c-224">Каждый файл F # в компоненте должен начинаться с объявления пространства имен или объявления модуля.</span><span class="sxs-lookup"><span data-stu-id="3897c-224">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="3897c-225">или</span><span class="sxs-lookup"><span data-stu-id="3897c-225">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="3897c-226">Ниже приведены различия между использованием модулей и пространств имен для организации кода на верхнем уровне.</span><span class="sxs-lookup"><span data-stu-id="3897c-226">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="3897c-227">Пространства имен могут охватывать несколько файлов</span><span class="sxs-lookup"><span data-stu-id="3897c-227">Namespaces can span multiple files</span></span>
* <span data-ttu-id="3897c-228">Пространства имен не могут содержать функции F #, если они не находятся внутри внутреннего модуля</span><span class="sxs-lookup"><span data-stu-id="3897c-228">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="3897c-229">Код для любого конкретного модуля должен содержаться в одном файле</span><span class="sxs-lookup"><span data-stu-id="3897c-229">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="3897c-230">Модули верхнего уровня могут содержать функции F # без необходимости внутреннего модуля.</span><span class="sxs-lookup"><span data-stu-id="3897c-230">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="3897c-231">Выбор между пространством имен верхнего уровня или модулем влияет на скомпилированную форму кода и, таким способом, повлияет на представление из других языков .NET, если ваш API будет использоваться вне кода F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-231">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="3897c-232">Использование методов и свойств для операций, встроенных в типы объектов</span><span class="sxs-lookup"><span data-stu-id="3897c-232">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="3897c-233">При работе с объектами лучше убедиться, что в качестве методов и свойств этого типа реализована потребляемая функциональность.</span><span class="sxs-lookup"><span data-stu-id="3897c-233">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="3897c-234">Основная функциональность для данного элемента не обязательно должна быть реализована в этом члене, но ее можно использовать.</span><span class="sxs-lookup"><span data-stu-id="3897c-234">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="3897c-235">Использование классов для инкапсуляции изменяемого состояния</span><span class="sxs-lookup"><span data-stu-id="3897c-235">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="3897c-236">В F # это необходимо сделать только в том случае, если это состояние еще не инкапсулировано другой конструкцией языка, например закрытием, выражением последовательности или асинхронным вычислением.</span><span class="sxs-lookup"><span data-stu-id="3897c-236">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="3897c-237">Использование интерфейсов для группирования связанных операций</span><span class="sxs-lookup"><span data-stu-id="3897c-237">Use interfaces to group related operations</span></span>

<span data-ttu-id="3897c-238">Используйте типы интерфейсов для представления набора операций.</span><span class="sxs-lookup"><span data-stu-id="3897c-238">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="3897c-239">Это предпочтительно для других параметров, таких как кортежи функций или записей функций.</span><span class="sxs-lookup"><span data-stu-id="3897c-239">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="3897c-240">В качестве предпочтения к:</span><span class="sxs-lookup"><span data-stu-id="3897c-240">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

<span data-ttu-id="3897c-241">Интерфейсы — это основные понятия .NET, которые можно использовать для достижения того, что операторов в обычном режиме.</span><span class="sxs-lookup"><span data-stu-id="3897c-241">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="3897c-242">Кроме того, они могут использоваться для кодирования типов существующий в программу, а записи функций — нет.</span><span class="sxs-lookup"><span data-stu-id="3897c-242">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a><span data-ttu-id="3897c-243">Использование модуля для группирования функций, действующих в коллекциях</span><span class="sxs-lookup"><span data-stu-id="3897c-243">Use a module to group functions that act on collections</span></span>

<span data-ttu-id="3897c-244">При определении типа коллекции рассмотрите возможность предоставления стандартного набора операций, таких как `CollectionType.map` и `CollectionType.iter` ), для новых типов коллекций.</span><span class="sxs-lookup"><span data-stu-id="3897c-244">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="3897c-245">Если вы включили такой модуль, следуйте стандартным соглашениям об именовании для функций, найденных в FSharp. Core.</span><span class="sxs-lookup"><span data-stu-id="3897c-245">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="3897c-246">Используйте модуль для группировки функций для распространенных, канонических функций, особенно в математических и ДОМЕНных библиотеках.</span><span class="sxs-lookup"><span data-stu-id="3897c-246">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="3897c-247">Например, `Microsoft.FSharp.Core.Operators` — это автоматически открываемая коллекция функций верхнего уровня (например `abs` , и `sin` ), предоставляемых FSharp.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="3897c-247">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="3897c-248">Аналогичным образом библиотека статистики может включать модуль с функциями `erf` и `erfc` , где этот модуль предназначен для явного или автоматического открытия.</span><span class="sxs-lookup"><span data-stu-id="3897c-248">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="3897c-249">Рассмотрите возможность использования Рекуирекуалифиедакцесс и тщательного применения атрибутов Автооткрытия</span><span class="sxs-lookup"><span data-stu-id="3897c-249">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="3897c-250">Добавление `[<RequireQualifiedAccess>]` атрибута в модуль указывает на то, что модуль не может быть открыт, а ссылки на элементы модуля необходимы для явного полного доступа.</span><span class="sxs-lookup"><span data-stu-id="3897c-250">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="3897c-251">Например, у `Microsoft.FSharp.Collections.List` модуля есть этот атрибут.</span><span class="sxs-lookup"><span data-stu-id="3897c-251">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="3897c-252">Это полезно, когда функции и значения в модуле имеют имена, которые, скорее всего, конфликтуют с именами в других модулях.</span><span class="sxs-lookup"><span data-stu-id="3897c-252">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="3897c-253">Обязательное получение полного доступа может значительно увеличить долгосрочное обслуживание и развитию библиотеки.</span><span class="sxs-lookup"><span data-stu-id="3897c-253">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="3897c-254">Добавление `[<AutoOpen>]` атрибута в модуль означает, что модуль будет открыт при открытии содержащего его пространства имен.</span><span class="sxs-lookup"><span data-stu-id="3897c-254">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="3897c-255">`[<AutoOpen>]`Атрибут может также применяться к сборке для указания модуля, который автоматически открывается при ссылке на сборку.</span><span class="sxs-lookup"><span data-stu-id="3897c-255">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="3897c-256">Например, Библиотека статистики **масшеавен. Statistics** может содержать `module MathsHeaven.Statistics.Operators` содержащиеся в ней функции `erf` и `erfc` .</span><span class="sxs-lookup"><span data-stu-id="3897c-256">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="3897c-257">Разумно пометить этот модуль как `[<AutoOpen>]` .</span><span class="sxs-lookup"><span data-stu-id="3897c-257">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="3897c-258">Это означает `open MathsHeaven.Statistics` , что также откроет этот модуль и поместит имена `erf` и `erfc` в область.</span><span class="sxs-lookup"><span data-stu-id="3897c-258">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="3897c-259">Еще один хороший `[<AutoOpen>]` способ использования — для модулей, содержащих методы расширения.</span><span class="sxs-lookup"><span data-stu-id="3897c-259">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="3897c-260">Чрезмерное число `[<AutoOpen>]` интересов в пространствах имен искажены, и атрибут следует использовать с осторожностью.</span><span class="sxs-lookup"><span data-stu-id="3897c-260">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="3897c-261">Для конкретных библиотек в конкретных доменах разумное использование `[<AutoOpen>]` может привести к повышению удобства использования.</span><span class="sxs-lookup"><span data-stu-id="3897c-261">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="3897c-262">Рассмотрите возможность определения членов оператора в классах, где используются хорошо известные операторы</span><span class="sxs-lookup"><span data-stu-id="3897c-262">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="3897c-263">Иногда классы используются для моделирования математических конструкций, таких как векторы.</span><span class="sxs-lookup"><span data-stu-id="3897c-263">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="3897c-264">Если в домене, на который моделируется, есть хорошо известные операторы, это полезно, определяя их как члены, встроенные в класс.</span><span class="sxs-lookup"><span data-stu-id="3897c-264">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="3897c-265">Это руководство соответствует общим рекомендациям .NET для этих типов.</span><span class="sxs-lookup"><span data-stu-id="3897c-265">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="3897c-266">Однако он может быть дополнительно важен в коде F #, так как это позволяет использовать эти типы в сочетании с функциями и методами F # с ограничениями элементов, такими как List. sumBy.</span><span class="sxs-lookup"><span data-stu-id="3897c-266">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="3897c-267">Рассмотрите возможность использования CompiledName для предоставления. NET-понятное имя для других потребителей языков .NET</span><span class="sxs-lookup"><span data-stu-id="3897c-267">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="3897c-268">Иногда может потребоваться присвоить что-либо в одном стиле для потребителей F # (например, статический элемент в нижнем регистре, чтобы он выводился как функция, привязанная к модулю), но иметь другой стиль имени при компиляции в сборку.</span><span class="sxs-lookup"><span data-stu-id="3897c-268">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="3897c-269">Атрибут можно использовать `[<CompiledName>]` для предоставления другого стиля для кода, не использующего F #, который использует сборку.</span><span class="sxs-lookup"><span data-stu-id="3897c-269">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="3897c-270">С помощью `[<CompiledName>]` можно использовать соглашения об именовании .NET для потребителей сборки, не относящихся к F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-270">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="3897c-271">Используйте перегрузку метода для функций-членов, если это делает API более простым</span><span class="sxs-lookup"><span data-stu-id="3897c-271">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="3897c-272">Перегрузка методов — это мощный инструмент для упрощения API, который может потребовать выполнения аналогичных функций, но с различными параметрами или аргументами.</span><span class="sxs-lookup"><span data-stu-id="3897c-272">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="3897c-273">В F # более распространена перегрузка для количества аргументов, а не типов аргументов.</span><span class="sxs-lookup"><span data-stu-id="3897c-273">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="3897c-274">Скрытие представлений типов записи и объединения, если структура этих типов, вероятно, будет развиваться</span><span class="sxs-lookup"><span data-stu-id="3897c-274">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="3897c-275">Старайтесь не раскрывать конкретные представления объектов.</span><span class="sxs-lookup"><span data-stu-id="3897c-275">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="3897c-276">Например, конкретное представление <xref:System.DateTime> значений не раскрывается внешним общедоступным API-интерфейсом структуры библиотеки .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-276">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="3897c-277">Во время выполнения среда CLR знает о зафиксированной реализации, которая будет использоваться в процессе выполнения.</span><span class="sxs-lookup"><span data-stu-id="3897c-277">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="3897c-278">Однако скомпилированный код сам по себе не берет зависимости от конкретного представления.</span><span class="sxs-lookup"><span data-stu-id="3897c-278">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="3897c-279">Избегайте использования наследования реализации для расширяемости</span><span class="sxs-lookup"><span data-stu-id="3897c-279">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="3897c-280">В F # наследование реализации используется редко.</span><span class="sxs-lookup"><span data-stu-id="3897c-280">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="3897c-281">Кроме того, иерархии наследования часто сложны и изменяются при прибытии новых требований.</span><span class="sxs-lookup"><span data-stu-id="3897c-281">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="3897c-282">Реализация наследования по-прежнему существует в F # для обеспечения совместимости и редких случаев, когда это лучшее решение проблемы, но при проектировании для полиморфизма в программах F # следует использовать альтернативные методы, такие как реализация интерфейса.</span><span class="sxs-lookup"><span data-stu-id="3897c-282">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="3897c-283">Сигнатуры функций и членов</span><span class="sxs-lookup"><span data-stu-id="3897c-283">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="3897c-284">Использование кортежей для возвращаемых значений при возврате небольшого числа нескольких несвязанных значений</span><span class="sxs-lookup"><span data-stu-id="3897c-284">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="3897c-285">Ниже приведен хороший пример использования кортежа в типе возвращаемого значения:</span><span class="sxs-lookup"><span data-stu-id="3897c-285">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="3897c-286">Для возвращаемых типов, содержащих множество компонентов или компонентов, связанных с одной идентифицируемой сущностью, рекомендуется использовать именованный тип вместо кортежа.</span><span class="sxs-lookup"><span data-stu-id="3897c-286">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="3897c-287">Использовать `Async<T>` для асинхронного программирования на границах API F #</span><span class="sxs-lookup"><span data-stu-id="3897c-287">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="3897c-288">Если имеется соответствующая синхронная операция с именем, `Operation` которая возвращает `T` , то асинхронной операции следует присвоить имя, `AsyncOperation` если она возвращает значение, `Async<T>` или `OperationAsync` возвращает `Task<T>` .</span><span class="sxs-lookup"><span data-stu-id="3897c-288">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="3897c-289">Для часто используемых типов .NET, предоставляющих методы Begin и End, рекомендуется использовать `Async.FromBeginEnd` для записи методов расширения в качестве фасадной, чтобы обеспечить модель асинхронного программирования F # для этих API-интерфейсов .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-289">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="3897c-290">Исключения</span><span class="sxs-lookup"><span data-stu-id="3897c-290">Exceptions</span></span>

<span data-ttu-id="3897c-291">Сведения о правильном использовании исключений, результатов и параметров см. в разделе [Управление ошибками](conventions.md#error-management) .</span><span class="sxs-lookup"><span data-stu-id="3897c-291">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="3897c-292">Члены расширений</span><span class="sxs-lookup"><span data-stu-id="3897c-292">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="3897c-293">Аккуратное применение членов расширения F # в компонентах F # в-F #</span><span class="sxs-lookup"><span data-stu-id="3897c-293">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="3897c-294">Члены расширений F # обычно должны использоваться только для операций, которые находятся в замыкании внутренних операций, связанных с типом, в большинстве режимов использования.</span><span class="sxs-lookup"><span data-stu-id="3897c-294">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="3897c-295">Одним из распространенных способов является предоставление API-интерфейсов, которые более идиоматическим в F # для различных типов .NET:</span><span class="sxs-lookup"><span data-stu-id="3897c-295">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="3897c-296">Типы объединений</span><span class="sxs-lookup"><span data-stu-id="3897c-296">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="3897c-297">Использование размеченных объединений вместо иерархий классов для структурированных данных дерева</span><span class="sxs-lookup"><span data-stu-id="3897c-297">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="3897c-298">Структуры, схожие с деревом, определяются рекурсивно.</span><span class="sxs-lookup"><span data-stu-id="3897c-298">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="3897c-299">Это не имеет отношения к наследованию, но элегантно с помощью размеченных объединений.</span><span class="sxs-lookup"><span data-stu-id="3897c-299">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="3897c-300">Представление данных в виде дерева с помощью размеченных объединений также позволяет использовать преимущества ексхаустивенесс в сопоставлении шаблонов.</span><span class="sxs-lookup"><span data-stu-id="3897c-300">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="3897c-301">Используйте `[<RequireQualifiedAccess>]` для типов объединения, имена вариантов которых недостаточно уникальны</span><span class="sxs-lookup"><span data-stu-id="3897c-301">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="3897c-302">Вы можете найти себя в домене, где одно и то же имя является лучшим именем для различных вещей, таких как случаи размеченного объединения.</span><span class="sxs-lookup"><span data-stu-id="3897c-302">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="3897c-303">Можно использовать `[<RequireQualifiedAccess>]` для устранения неоднозначности имен регистров во избежание вызова непонятных ошибок из-за того, что тень зависит от порядка `open` инструкций.</span><span class="sxs-lookup"><span data-stu-id="3897c-303">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="3897c-304">Скрытие представлений размеченных объединений для API, совместимых с двоичными данными, если структура этих типов, скорее всего, будет развиваться</span><span class="sxs-lookup"><span data-stu-id="3897c-304">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="3897c-305">Типы объединений основываются на формах, соответствующих шаблону F #, для краткой модели программирования.</span><span class="sxs-lookup"><span data-stu-id="3897c-305">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="3897c-306">Как упоминалось ранее, не следует раскрывать конкретные представления данных, если проект этих типов, вероятно, будет развиваться.</span><span class="sxs-lookup"><span data-stu-id="3897c-306">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="3897c-307">Например, представление размеченного объединения может быть скрыто с помощью частного или внутреннего объявления или с помощью файла сигнатуры.</span><span class="sxs-lookup"><span data-stu-id="3897c-307">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="3897c-308">Если вы раскрываете размеченные объединения неограниченно, то, возможно, вам не придется выполнять версию библиотеки без нарушения пользовательского кода.</span><span class="sxs-lookup"><span data-stu-id="3897c-308">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="3897c-309">Вместо этого рассмотрите возможность раскрытия одного или нескольких активных шаблонов, чтобы обеспечить сопоставление шаблонов для значений типа.</span><span class="sxs-lookup"><span data-stu-id="3897c-309">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="3897c-310">Активные шаблоны обеспечивают альтернативный способ предоставления потребителей F # с сопоставлением шаблонов, не позволяя напрямую предоставлять типы объединения F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-310">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="3897c-311">Встроенные функции и ограничения элементов</span><span class="sxs-lookup"><span data-stu-id="3897c-311">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="3897c-312">Определение универсальных числовых алгоритмов с помощью встроенных функций с неявными ограничениями элементов и статически разрешенными универсальными типами</span><span class="sxs-lookup"><span data-stu-id="3897c-312">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="3897c-313">Ограничения арифметического элемента и ограничения на сравнение F # являются стандартом для программирования на F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-313">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="3897c-314">Рассмотрим следующий пример кода:</span><span class="sxs-lookup"><span data-stu-id="3897c-314">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="3897c-315">Эта функция имеет следующий тип:</span><span class="sxs-lookup"><span data-stu-id="3897c-315">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="3897c-316">Это подходящая функция для открытого API в математической библиотеке.</span><span class="sxs-lookup"><span data-stu-id="3897c-316">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="3897c-317">Избегайте использования ограничений членов для имитации классов типов и ввода утка</span><span class="sxs-lookup"><span data-stu-id="3897c-317">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="3897c-318">Можно имитировать «утка типизацию» с помощью ограничений для членов F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-318">It is possible to simulate "duck typing" using F# member constraints.</span></span> <span data-ttu-id="3897c-319">Тем не менее члены, которые используют эту возможность, не должны использоваться в структурах библиотеки F # в-F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-319">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="3897c-320">Это обусловлено тем, что структуры библиотек на основе незнакомых или нестандартных неявных ограничений обычно приводят к тому, что пользовательский код становится негибким и привязан к одному конкретному шаблону платформы.</span><span class="sxs-lookup"><span data-stu-id="3897c-320">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="3897c-321">Кроме того, существует хороший шанс, что использование ограничений на элементы таким образом может привести к очень длительному времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="3897c-321">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="3897c-322">Определения операторов</span><span class="sxs-lookup"><span data-stu-id="3897c-322">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="3897c-323">Избегайте определения пользовательских символьных операторов</span><span class="sxs-lookup"><span data-stu-id="3897c-323">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="3897c-324">Пользовательские операторы являются важными в некоторых ситуациях и представляют собой очень полезные устройства нотаций в большом тексте кода реализации.</span><span class="sxs-lookup"><span data-stu-id="3897c-324">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="3897c-325">Для новых пользователей библиотеки именованные функции часто проще в использовании.</span><span class="sxs-lookup"><span data-stu-id="3897c-325">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="3897c-326">Кроме того, пользовательские символьные операторы могут быть сложными для документирования, и пользователям больше сложно найти справку по операторам в связи с существующими ограничениями в интегрированной среде разработки и механизмах поиска.</span><span class="sxs-lookup"><span data-stu-id="3897c-326">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="3897c-327">В результате лучше опубликовать функциональные возможности как именованные функции и члены, а также предоставить операторам для этой функции только в том случае, если преимущества в нотации перевешивают документацию и издержки на их использование.</span><span class="sxs-lookup"><span data-stu-id="3897c-327">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="3897c-328">Единицы измерения</span><span class="sxs-lookup"><span data-stu-id="3897c-328">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="3897c-329">Тщательно используйте единицы измерения для повышения безопасности типов в коде F #</span><span class="sxs-lookup"><span data-stu-id="3897c-329">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="3897c-330">Дополнительные сведения о вводе для единиц измерения удаляются при просмотре другими языками .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-330">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="3897c-331">Имейте в виду, что компоненты, средства и отражение будут видеть типы-San-единицы.</span><span class="sxs-lookup"><span data-stu-id="3897c-331">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="3897c-332">Например, пользователи C# увидят, `float` а не `float<kg>` .</span><span class="sxs-lookup"><span data-stu-id="3897c-332">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="3897c-333">Сокращенные обозначения типов</span><span class="sxs-lookup"><span data-stu-id="3897c-333">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="3897c-334">Аккуратно используйте сокращения типов для упрощения кода на F #</span><span class="sxs-lookup"><span data-stu-id="3897c-334">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="3897c-335">Компоненты, средства и отражение .NET не увидят сокращенные имена типов.</span><span class="sxs-lookup"><span data-stu-id="3897c-335">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="3897c-336">Значительное использование сокращений типов также может привести к более сложному домену, чем на самом деле, что может напутать потребителей.</span><span class="sxs-lookup"><span data-stu-id="3897c-336">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="3897c-337">Избегайте сокращений типов для открытых типов, члены и свойства которых должны различаться в соответствии с тем, которые доступны в сокращенном типе.</span><span class="sxs-lookup"><span data-stu-id="3897c-337">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="3897c-338">В этом случае тип, который сокращается, выдает слишком много сведений о представлении фактического типа.</span><span class="sxs-lookup"><span data-stu-id="3897c-338">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="3897c-339">Вместо этого рекомендуется заключить сокращение в оболочку типа класса или размеченного объединения одиночного случая (или, если требуется производительность, рассмотрите возможность использования типа структуры для заключения аббревиатуры).</span><span class="sxs-lookup"><span data-stu-id="3897c-339">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="3897c-340">Например, можно определить несколько карт как особый случай для схемы F #, например:</span><span class="sxs-lookup"><span data-stu-id="3897c-340">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="3897c-341">Однако операции с нотацией логических точек для этого типа не совпадают с операциями на карте. Например, разумно, чтобы оператор уточняющего запроса был сопоставлен. [key] возвращает пустой список, если ключ отсутствует в словаре, а не вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="3897c-341">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="3897c-342">Рекомендации по использованию библиотек для других языков .NET</span><span class="sxs-lookup"><span data-stu-id="3897c-342">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="3897c-343">При проектировании библиотек для использования из других языков .NET важно соблюдать [рекомендации по проектированию библиотеки .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="3897c-343">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="3897c-344">В этом документе эти библиотеки помечены как библиотеки обычный .NET, а не библиотеки F #, использующие конструкции F # без ограничений.</span><span class="sxs-lookup"><span data-stu-id="3897c-344">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="3897c-345">Разработка библиотек обычный .NET означает предоставление привычных и идиоматическим интерфейсов API, совместимых с остальными .NET Framework за счет минимизации использования конструкций, характерных для F #, в общедоступном API.</span><span class="sxs-lookup"><span data-stu-id="3897c-345">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="3897c-346">Правила описаны в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="3897c-346">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="3897c-347">Разработка пространства имен и типа (для библиотек, используемых на других языках .NET)</span><span class="sxs-lookup"><span data-stu-id="3897c-347">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="3897c-348">Примените соглашения об именовании .NET к общедоступному API компонентов.</span><span class="sxs-lookup"><span data-stu-id="3897c-348">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="3897c-349">Обратите особое внимание на использование сокращенных имен и рекомендации по капитализации .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-349">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="3897c-350">Использование пространств имен, типов и членов в качестве основной организационной структуры для компонентов</span><span class="sxs-lookup"><span data-stu-id="3897c-350">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="3897c-351">Все файлы, содержащие открытые функции, должны начинаться с `namespace` объявления, а единственные открытые сущности в пространствах имен должны быть типами.</span><span class="sxs-lookup"><span data-stu-id="3897c-351">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="3897c-352">Не используйте модули F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-352">Do not use F# modules.</span></span>

<span data-ttu-id="3897c-353">Используйте неоткрытые модули для хранения кода реализации, типов служебных программ и служебных функций.</span><span class="sxs-lookup"><span data-stu-id="3897c-353">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="3897c-354">Статические типы должны быть предпочтительнее модулей, так как они обеспечивают будущее развитие API для использования перегрузки и других концепций проектирования API .NET, которые не могут использоваться в модулях F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-354">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="3897c-355">Например, вместо следующего общедоступного API:</span><span class="sxs-lookup"><span data-stu-id="3897c-355">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="3897c-356">Вместо этого следует рассмотреть следующее:</span><span class="sxs-lookup"><span data-stu-id="3897c-356">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="3897c-357">Используйте типы записей F # в API обычный .NET, если структура типов не будет развиваться</span><span class="sxs-lookup"><span data-stu-id="3897c-357">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="3897c-358">Типы записей F # компилируются в простой класс .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-358">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="3897c-359">Они подходят для некоторых простых, стабильных типов в API.</span><span class="sxs-lookup"><span data-stu-id="3897c-359">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="3897c-360">Рассмотрите возможность `[<NoEquality>]` использования `[<NoComparison>]` атрибутов и для подавления автоматического создания интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="3897c-360">Consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="3897c-361">Кроме того, не используйте изменяемые поля записей в API обычный .NET, так как они предоставляют открытое поле.</span><span class="sxs-lookup"><span data-stu-id="3897c-361">Also avoid using mutable record fields in vanilla .NET APIs as these expose a public field.</span></span> <span data-ttu-id="3897c-362">Всегда продумайте, будет ли класс предоставлять более гибкий вариант для будущего развития API.</span><span class="sxs-lookup"><span data-stu-id="3897c-362">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="3897c-363">Например, следующий код F # предоставляет открытый API для потребителя C#:</span><span class="sxs-lookup"><span data-stu-id="3897c-363">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="3897c-364">F#:</span><span class="sxs-lookup"><span data-stu-id="3897c-364">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

<span data-ttu-id="3897c-365">C#:</span><span class="sxs-lookup"><span data-stu-id="3897c-365">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="3897c-366">Скрытие представления типов объединения F # в API-интерфейсах обычный .NET</span><span class="sxs-lookup"><span data-stu-id="3897c-366">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="3897c-367">Типы объединения f # обычно не используются в границах компонентов, даже для кодирования F # в-F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-367">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="3897c-368">Они являются отличным устройством реализации при внутреннем использовании в компонентах и библиотеках.</span><span class="sxs-lookup"><span data-stu-id="3897c-368">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="3897c-369">При проектировании обычный API .NET рассмотрите возможность скрытия представления типа объединения с помощью частного объявления или файла сигнатуры.</span><span class="sxs-lookup"><span data-stu-id="3897c-369">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="3897c-370">Кроме того, можно дополнить типы, использующие представление UNION внутри с элементами для предоставления требуемого значения. Интерфейс API с выходом на .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-370">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="3897c-371">Разработка графического пользовательского интерфейса и других компонентов с использованием шаблонов разработки платформы</span><span class="sxs-lookup"><span data-stu-id="3897c-371">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="3897c-372">В .NET доступны различные платформы, такие как WinForms, WPF и ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-372">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="3897c-373">Соглашения об именовании и проектировании для каждого из них следует использовать при проектировании компонентов для использования в этих платформах.</span><span class="sxs-lookup"><span data-stu-id="3897c-373">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="3897c-374">Например, для программирования WPF следует внедрять шаблоны разработки WPF для разрабатываемых классов.</span><span class="sxs-lookup"><span data-stu-id="3897c-374">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="3897c-375">Для моделей в программировании пользовательского интерфейса используйте шаблоны разработки, такие как события и коллекции на основе уведомлений, например, которые находятся в <xref:System.Collections.ObjectModel> .</span><span class="sxs-lookup"><span data-stu-id="3897c-375">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="3897c-376">Разработка объектов и элементов (для библиотек, используемых на других языках .NET)</span><span class="sxs-lookup"><span data-stu-id="3897c-376">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="3897c-377">Использование атрибута CLIEvent для предоставления событий .NET</span><span class="sxs-lookup"><span data-stu-id="3897c-377">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="3897c-378">Создайте `DelegateEvent` с помощью определенного типа делегата .NET, который принимает объект и `EventArgs` (вместо `Event` , который просто использует `FSharpHandler` тип по умолчанию), чтобы события публиковались в привычном виде для других языков .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-378">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a><span data-ttu-id="3897c-379">Предоставление асинхронных операций в качестве методов, возвращающих задачи .NET</span><span class="sxs-lookup"><span data-stu-id="3897c-379">Expose asynchronous operations as methods that return .NET tasks</span></span>

<span data-ttu-id="3897c-380">Задачи используются в .NET для представления активных асинхронных вычислений.</span><span class="sxs-lookup"><span data-stu-id="3897c-380">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="3897c-381">Задачи в целом меньше, чем объекты F # `Async<T>` , так как они представляют "уже выполняющиеся" задачи и не могут составляться одновременно с выполнением параллельной компоновки или скрывать распространение сигналов отмены и других контекстных параметров.</span><span class="sxs-lookup"><span data-stu-id="3897c-381">Tasks are in general less compositional than F# `Async<T>` objects, since they represent "already executing" tasks and can't be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="3897c-382">Однако, несмотря на это, методы, возвращающие задачи, являются стандартным представлением асинхронного программирования на .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-382">However, despite this, methods that return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="3897c-383">Кроме того, вы часто хотите принять явный токен отмены:</span><span class="sxs-lookup"><span data-stu-id="3897c-383">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="3897c-384">Использование типов делегатов .NET вместо типов функций F #</span><span class="sxs-lookup"><span data-stu-id="3897c-384">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="3897c-385">Здесь "типы функций F #" означают тип "стрелка" `int -> int` , например.</span><span class="sxs-lookup"><span data-stu-id="3897c-385">Here "F# function types" mean "arrow" types like `int -> int`.</span></span>

<span data-ttu-id="3897c-386">Вместо этого:</span><span class="sxs-lookup"><span data-stu-id="3897c-386">Instead of this:</span></span>

```fsharp
member this.Transform(f: int->int) =
    ...
```

<span data-ttu-id="3897c-387">Процедура</span><span class="sxs-lookup"><span data-stu-id="3897c-387">Do this:</span></span>

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

<span data-ttu-id="3897c-388">Тип функции F # выглядит так же `class FSharpFunc<T,U>` , как и другие языки .NET, и менее подходит для языковых функций и средств, которые понимают типы делегатов.</span><span class="sxs-lookup"><span data-stu-id="3897c-388">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understands delegate types.</span></span> <span data-ttu-id="3897c-389">При создании метода более высокого порядка, предназначенного для .NET Framework 3,5 или более поздней версии, `System.Func` `System.Action` делегаты и являются верными API-интерфейсами для публикации, чтобы позволить разработчикам .NET использовать эти API с низким уровнем трения.</span><span class="sxs-lookup"><span data-stu-id="3897c-389">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="3897c-390">(При нацеливании на .NET Framework 2,0, определяемые системой типы делегатов более ограничены; рассмотрите возможность использования предопределенных типов делегатов, например, `System.Converter<T,U>` или определения конкретного типа делегата.)</span><span class="sxs-lookup"><span data-stu-id="3897c-390">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="3897c-391">На стороне перелистывания делегаты .NET не являются естественными для библиотек, предназначенных для F # (см. следующий раздел о библиотеках, доступных в F #).</span><span class="sxs-lookup"><span data-stu-id="3897c-391">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="3897c-392">В результате распространенной стратегией реализации при разработке методов более высокого порядка для библиотек обычный .NET является создание всех реализаций с помощью типов функций F #, а затем создание общедоступного API с помощью делегатов в качестве тонкой фасаднойной реализации на самом деле реализация F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-392">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="3897c-393">Используйте шаблон TryGetValue вместо возврата значений параметров F # и предпочитать перегрузку метода для получения значений параметров F # в качестве аргументов.</span><span class="sxs-lookup"><span data-stu-id="3897c-393">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="3897c-394">Распространенные шаблоны использования для типа параметра F # в интерфейсах API более эффективны в API-интерфейсах обычный .NET с использованием стандартных методов проектирования .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-394">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="3897c-395">Вместо того чтобы возвращать значение параметра F #, рекомендуется использовать тип возвращаемого значения bool плюс параметр out, как в шаблоне "TryGetValue".</span><span class="sxs-lookup"><span data-stu-id="3897c-395">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="3897c-396">Вместо того, чтобы использовать в качестве параметров значения параметров F #, рассмотрите возможность использования перегрузки метода или необязательных аргументов.</span><span class="sxs-lookup"><span data-stu-id="3897c-396">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="3897c-397">Использование типов интерфейсов коллекций .NET IEnumerable \<T\> и IDictionary \<Key,Value\> для параметров и возвращаемых значений</span><span class="sxs-lookup"><span data-stu-id="3897c-397">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="3897c-398">Избегайте использования конкретных типов коллекций, таких как массивы .NET `T[]` , типы F # `list<T>` , `Map<Key,Value>` и `Set<T>` , а также конкретных типов коллекций .NET, таких как `Dictionary<Key,Value>` .</span><span class="sxs-lookup"><span data-stu-id="3897c-398">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="3897c-399">Рекомендации по проектированию библиотеки .NET содержат советы и рекомендации относительно использования различных типов коллекций, таких как `IEnumerable<T>` .</span><span class="sxs-lookup"><span data-stu-id="3897c-399">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="3897c-400">Использование массивов ( `T[]` ) является приемлемым в некоторых обстоятельствах, по причинам производительности.</span><span class="sxs-lookup"><span data-stu-id="3897c-400">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="3897c-401">Обратите внимание, особенно, что `seq<T>` является просто псевдонимом F # для `IEnumerable<T>` , и, таким образом, seq часто является подходящим типом для обычный .NET API.</span><span class="sxs-lookup"><span data-stu-id="3897c-401">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="3897c-402">Вместо списков F #:</span><span class="sxs-lookup"><span data-stu-id="3897c-402">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names: string list) =
    ...
```

<span data-ttu-id="3897c-403">Использовать последовательности F #:</span><span class="sxs-lookup"><span data-stu-id="3897c-403">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="3897c-404">Используйте тип Unit в качестве единственного входного типа метода для определения метода с нулевым аргументом или как единственный возвращаемый тип для определения метода, возвращающего значение void.</span><span class="sxs-lookup"><span data-stu-id="3897c-404">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="3897c-405">Избегайте других применений типа единиц измерения.</span><span class="sxs-lookup"><span data-stu-id="3897c-405">Avoid other uses of the unit type.</span></span> <span data-ttu-id="3897c-406">Это хорошо:</span><span class="sxs-lookup"><span data-stu-id="3897c-406">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

<span data-ttu-id="3897c-407">Это неплохо:</span><span class="sxs-lookup"><span data-stu-id="3897c-407">This is bad:</span></span>

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="3897c-408">Проверять наличие значений NULL на границах API обычный .NET</span><span class="sxs-lookup"><span data-stu-id="3897c-408">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="3897c-409">Код реализации F #, как правило, имеет меньше значений NULL из-за неизменяемых шаблонов проектирования и ограничений на использование литералов NULL для типов F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-409">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="3897c-410">Другие языки .NET часто используют значение NULL в качестве значения гораздо чаще.</span><span class="sxs-lookup"><span data-stu-id="3897c-410">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="3897c-411">По этой причине код F #, который предоставляет обычный API .NET, должен проверять параметры для значения NULL в границах API и предотвращать более глубокое перетекание этих значений в код реализации F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-411">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="3897c-412">`isNull`Можно использовать функцию или сопоставление шаблонов в `null` шаблоне.</span><span class="sxs-lookup"><span data-stu-id="3897c-412">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="3897c-413">Избегайте использования кортежей в качестве возвращаемых значений</span><span class="sxs-lookup"><span data-stu-id="3897c-413">Avoid using tuples as return values</span></span>

<span data-ttu-id="3897c-414">Вместо этого предпочтительнее возвращать именованный тип, содержащий статистические данные, или использовать выходные параметры для возвращения нескольких значений.</span><span class="sxs-lookup"><span data-stu-id="3897c-414">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="3897c-415">Хотя в .NET существуют кортежи и кортежи структур (включая поддержку языка C# для кортежей структуры), они чаще всего не предоставляют идеальный и ожидаемый API для разработчиков .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-415">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="3897c-416">Избегайте использования параметров карринг</span><span class="sxs-lookup"><span data-stu-id="3897c-416">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="3897c-417">Вместо этого используйте соглашения о вызовах .NET `Method(arg1,arg2,…,argN)` .</span><span class="sxs-lookup"><span data-stu-id="3897c-417">Instead, use .NET calling conventions `Method(arg1,arg2,…,argN)`.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="3897c-418">Совет. Если вы разрабатываете библиотеки для использования на любом языке .NET, нет никакой замены на фактическое выполнение экспериментального программирования на C# и Visual Basic, чтобы гарантировать правильное использование библиотек на этих языках.</span><span class="sxs-lookup"><span data-stu-id="3897c-418">Tip: If you're designing libraries for use from any .NET language, then there's no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="3897c-419">Вы также можете использовать такие средства, как .NET Reflector и обозреватель объектов Visual Studio, чтобы гарантировать, что библиотеки и их документация должным образом отображались для разработчиков.</span><span class="sxs-lookup"><span data-stu-id="3897c-419">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="3897c-420">Приложение</span><span class="sxs-lookup"><span data-stu-id="3897c-420">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="3897c-421">Полный пример разработки кода на F # для использования другими языками .NET</span><span class="sxs-lookup"><span data-stu-id="3897c-421">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="3897c-422">Рассмотрим следующий класс:</span><span class="sxs-lookup"><span data-stu-id="3897c-422">Consider the following class:</span></span>

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

<span data-ttu-id="3897c-423">Выводимый тип F # этого класса выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3897c-423">The inferred F# type of this class is as follows:</span></span>

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

<span data-ttu-id="3897c-424">Давайте посмотрим, как этот тип F # появился программисту, используя другой язык .NET.</span><span class="sxs-lookup"><span data-stu-id="3897c-424">Let's take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="3897c-425">Например, приблизительная сигнатура C# выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3897c-425">For example, the approximate C# "signature" is as follows:</span></span>

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="3897c-426">Есть несколько важных моментов, на которые следует обратить внимание о том, как F # представляет здесь конструкции.</span><span class="sxs-lookup"><span data-stu-id="3897c-426">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="3897c-427">Пример:</span><span class="sxs-lookup"><span data-stu-id="3897c-427">For example:</span></span>

* <span data-ttu-id="3897c-428">Метаданные, такие как имена аргументов, сохранены.</span><span class="sxs-lookup"><span data-stu-id="3897c-428">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="3897c-429">Методы F #, которые принимают два аргумента, становятся методами C#, принимающими два аргумента.</span><span class="sxs-lookup"><span data-stu-id="3897c-429">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="3897c-430">Функции и списки становятся ссылками на соответствующие типы в библиотеке F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-430">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="3897c-431">В следующем коде показано, как настроить этот код, чтобы учесть эти вещи.</span><span class="sxs-lookup"><span data-stu-id="3897c-431">The following code shows how to adjust this code to take these things into account.</span></span>

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

<span data-ttu-id="3897c-432">Выводимый тип F # кода выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3897c-432">The inferred F# type of the code is as follows:</span></span>

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

<span data-ttu-id="3897c-433">Сигнатура C# теперь выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3897c-433">The C# signature is now as follows:</span></span>

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="3897c-434">Исправления, внесенные в подготовку этого типа для использования в составе библиотеки обычный .NET, приведены ниже.</span><span class="sxs-lookup"><span data-stu-id="3897c-434">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="3897c-435">Изменено несколько имен: `Point1` , `n` , `l` , и `f` перестали `RadialPoint` , `count` , `factor` и `transform` соответственно.</span><span class="sxs-lookup"><span data-stu-id="3897c-435">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="3897c-436">Используется тип возвращаемого значения, `seq<RadialPoint>` а не `RadialPoint list` путем изменения построения списка с помощью `[ ... ]` в конструкции последовательности с помощью `IEnumerable<RadialPoint>` .</span><span class="sxs-lookup"><span data-stu-id="3897c-436">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="3897c-437">Используется тип делегата .NET `System.Func` вместо типа функции F #.</span><span class="sxs-lookup"><span data-stu-id="3897c-437">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="3897c-438">Это позволяет лучше использовать код C#.</span><span class="sxs-lookup"><span data-stu-id="3897c-438">This makes it far nicer to consume in C# code.</span></span>
