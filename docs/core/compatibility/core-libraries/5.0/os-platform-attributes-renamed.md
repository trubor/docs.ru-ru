---
title: Критическое изменение. Атрибуты OSPlatform переименованы или удалены
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где атрибуты платформы ОС, появившиеся в предварительной версии, были удалены или переименованы.
ms.date: 11/01/2020
ms.openlocfilehash: 118c5360eb02c1b4d57fccbd3b2cfdeff0b9fe12
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257262"
---
# <a name="osplatform-attributes-renamed-or-removed"></a><span data-ttu-id="ae6ee-103">Атрибуты OSPlatform переименованы или удалены</span><span class="sxs-lookup"><span data-stu-id="ae6ee-103">OSPlatform attributes renamed or removed</span></span>

<span data-ttu-id="ae6ee-104">Следующие атрибуты, появившиеся в предварительной версии 8 .NET 5, были удалены или переименованы: `MinimumOSPlatformAttribute`, `RemovedInOSPlatformAttribute` и `ObsoletedInOSPlatformAttribute`.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-104">The following attributes that were introduced in .NET 5 Preview 8 have been removed or renamed: `MinimumOSPlatformAttribute`, `RemovedInOSPlatformAttribute`, and `ObsoletedInOSPlatformAttribute`.</span></span>

## <a name="change-description"></a><span data-ttu-id="ae6ee-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="ae6ee-105">Change description</span></span>

<span data-ttu-id="ae6ee-106">В предварительной версии 8 .NET 5 в пространстве имен <xref:System.Runtime.Versioning> появились следующие атрибуты:</span><span class="sxs-lookup"><span data-stu-id="ae6ee-106">.NET 5 Preview 8 introduced the following attributes in the <xref:System.Runtime.Versioning> namespace:</span></span>

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

<span data-ttu-id="ae6ee-107">Если в предварительной версии 8 .NET 5 проект предназначен для использования в конкретной ОС .NET 5 с помощью [моникера целевой платформы](../../../../standard/frameworks.md), например `net5.0-windows`, сборка добавляет атрибут `System.Runtime.Versioning.MinimumOSPlatformAttribute` уровня сборки.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-107">In .NET 5 Preview 8, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level `System.Runtime.Versioning.MinimumOSPlatformAttribute` attribute.</span></span>

<span data-ttu-id="ae6ee-108">В .NET 5 RC1 атрибут `ObsoletedInOSPlatformAttribute` был удален, а атрибуты `MinimumOSPlatformAttribute` и `RemovedInOSPlatformAttribute` переименованы следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-108">In .NET 5 RC1, the `ObsoletedInOSPlatformAttribute` has been removed, and `MinimumOSPlatformAttribute` and `RemovedInOSPlatformAttribute` have been renamed as follows:</span></span>

| <span data-ttu-id="ae6ee-109">Имя предварительной версии 8</span><span class="sxs-lookup"><span data-stu-id="ae6ee-109">Preview 8 name</span></span> | <span data-ttu-id="ae6ee-110">Имя RC1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="ae6ee-110">RC1 and later name</span></span> |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

<span data-ttu-id="ae6ee-111">Если в .NET 5 RC1 и более поздних версиях проект предназначен для использования в конкретной ОС .NET 5 с помощью [моникера целевой платформы](../../../../standard/frameworks.md), например `net5.0-windows`, сборка добавляет атрибут <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> уровня сборки.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-111">In .NET 5 RC1 and later, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> attribute.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ae6ee-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="ae6ee-112">Reason for change</span></span>

<span data-ttu-id="ae6ee-113">В предварительной версии 8 .NET 5 в <xref:System.Runtime.Versioning> появились атрибуты для указания поддерживаемых платформ для API-интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-113">.NET 5 Preview 8 introduced attributes in <xref:System.Runtime.Versioning> to specify supported platforms for APIs.</span></span> <span data-ttu-id="ae6ee-114">[Анализатор совместимости платформ](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) использует эти атрибуты для создания предупреждений сборки, когда интерфейсы API, зависящие от платформы, работают на платформах, их не поддерживающих.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-114">The attributes are consumed by the [Platform compatibility analyzer](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) to produce build warnings when platform-specific APIs are consumed on platforms that don't support those APIs.</span></span>

<span data-ttu-id="ae6ee-115">В .NET 5 RC1 в анализатор совместимости платформ была добавлена дополнительная возможность исключения платформы.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-115">For .NET 5 RC1, an additional feature was added to the platform compatibility analyzer for platform exclusion.</span></span> <span data-ttu-id="ae6ee-116">Эта функция позволяет помечать API-интерфейсы как полностью не поддерживаемые на платформах ОС.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-116">The feature allows APIs to be marked as entirely unsupported on OS platforms.</span></span> <span data-ttu-id="ae6ee-117">Она предлагает изменить атрибуты или использовать более подходящие имена.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-117">That feature prompted changes to the attributes, including using more suitable names.</span></span> <span data-ttu-id="ae6ee-118">`ObsoletedInOSPlatformAttribute` был удален, так как он больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-118">The `ObsoletedInOSPlatformAttribute` was removed because it was no longer needed.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ae6ee-119">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="ae6ee-119">Version introduced</span></span>

<span data-ttu-id="ae6ee-120">5.0 (RC1)</span><span class="sxs-lookup"><span data-stu-id="ae6ee-120">5.0 RC1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ae6ee-121">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="ae6ee-121">Recommended action</span></span>

<span data-ttu-id="ae6ee-122">При изменении целевой платформы проекта с предварительной версии 8 .NET 5 на .NET 5 RC1 могут возникать ошибки сборки или времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-122">When you retarget your project from .NET 5 Preview 8 to .NET 5 RC1, you might encounter build or run-time errors due to these changes.</span></span> <span data-ttu-id="ae6ee-123">Например, переименование `MinimumOSPlatformAttribute`, скорее всего, приведет к появлению ошибок, поскольку атрибут применяется к сборкам для конкретных платформ во время сборки, а старые артефакты сборки по-прежнему ссылаются на старое имя API.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-123">For example, the renaming of `MinimumOSPlatformAttribute` is likely to produce errors, because the attribute is applied to platform-specific assemblies at build time, and old build artifacts will still reference the old API name.</span></span>

<span data-ttu-id="ae6ee-124">Примеры ошибок во время сборки:</span><span class="sxs-lookup"><span data-stu-id="ae6ee-124">Example build-time errors:</span></span>

- <span data-ttu-id="ae6ee-125">**Ошибка CS0246. Не удалось найти тип или имя пространства имен "MinimumOSPlatformAttribute" (возможно, отсутствует директива using или ссылка на сборку).**</span><span class="sxs-lookup"><span data-stu-id="ae6ee-125">**error CS0246: The type or namespace name 'MinimumOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="ae6ee-126">**Ошибка CS0246. Не удалось найти тип или имя пространства имен "RemovedInOSPlatformAttribute" (возможно, отсутствует директива using или ссылка на сборку).**</span><span class="sxs-lookup"><span data-stu-id="ae6ee-126">**error CS0246: The type or namespace name 'RemovedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="ae6ee-127">**Ошибка CS0246. Не удалось найти тип или имя пространства имен "ObsoletedInOSPlatformAttribute" (возможно, отсутствует директива using или ссылка на сборку).**</span><span class="sxs-lookup"><span data-stu-id="ae6ee-127">**error CS0246: The type or namespace name 'ObsoletedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>

<span data-ttu-id="ae6ee-128">Пример ошибки во время выполнения:</span><span class="sxs-lookup"><span data-stu-id="ae6ee-128">Example run-time error:</span></span>

<span data-ttu-id="ae6ee-129">**Необработанное исключение. System.TypeLoadException: Не удалось загрузить тип "System.Runtime.Versioning.MinimumOSPlatformAttribute"из сборки "System.Runtime, Version=5.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a".**</span><span class="sxs-lookup"><span data-stu-id="ae6ee-129">**Unhandled exception. System.TypeLoadException: Could not load type 'System.Runtime.Versioning.MinimumOSPlatformAttribute' from assembly 'System.Runtime, Version=5.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'.**</span></span>

<span data-ttu-id="ae6ee-130">Чтобы устранить эти ошибки, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-130">To resolve these errors:</span></span>

- <span data-ttu-id="ae6ee-131">Обновите все ссылки `MinimumOSPlatformAttribute` до <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-131">Update any references of `MinimumOSPlatformAttribute` to <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="ae6ee-132">Обновите все ссылки `RemovedInOSPlatformAttribute` до <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-132">Update any references of `RemovedInOSPlatformAttribute` to <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="ae6ee-133">Удалите все ссылки на `ObsoletedInOSPlatformAttribute`.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-133">Remove any references to `ObsoletedInOSPlatformAttribute`.</span></span>
- <span data-ttu-id="ae6ee-134">Перестройте проект (или выполните очистку и сборку), чтобы удалить старые артефакты сборки.</span><span class="sxs-lookup"><span data-stu-id="ae6ee-134">Rebuild your project (or perform clean + build) to delete old build artifacts.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ae6ee-135">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="ae6ee-135">Affected APIs</span></span>

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->
