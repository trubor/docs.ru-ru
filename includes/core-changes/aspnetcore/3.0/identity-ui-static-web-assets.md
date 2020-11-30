---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032798"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="a68e8-101">Удостоверение. Пользовательский интерфейс использует функцию статических веб-ресурсов</span><span class="sxs-lookup"><span data-stu-id="a68e8-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="a68e8-102">В ASP.NET Core 3.0 появился статический компонент веб-ресурсов, и он поддерживается пользовательским интерфейсом удостоверений.</span><span class="sxs-lookup"><span data-stu-id="a68e8-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a68e8-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="a68e8-103">Change description</span></span>

<span data-ttu-id="a68e8-104">Внедрение функции статических веб-ресурсов в пользовательский интерфейс удостоверений принесло следующие результаты.</span><span class="sxs-lookup"><span data-stu-id="a68e8-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="a68e8-105">Выбор платформы осуществляется с помощью свойства `IdentityUIFrameworkVersion` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="a68e8-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="a68e8-106">Bootstrap 4 является инфраструктурой пользовательского интерфейса по умолчанию для пользовательского интерфейса удостоверений.</span><span class="sxs-lookup"><span data-stu-id="a68e8-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="a68e8-107">Bootstrap 3 достигла конца жизненного цикла, и мы рекомендуем перейти на поддерживаемую версию.</span><span class="sxs-lookup"><span data-stu-id="a68e8-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a68e8-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="a68e8-108">Version introduced</span></span>

<span data-ttu-id="a68e8-109">3.0</span><span class="sxs-lookup"><span data-stu-id="a68e8-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a68e8-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="a68e8-110">Old behavior</span></span>

<span data-ttu-id="a68e8-111">Инфраструктурой пользовательского интерфейса по умолчанию для пользовательского интерфейса удостоверений была **Bootstrap 3**.</span><span class="sxs-lookup"><span data-stu-id="a68e8-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="a68e8-112">Для платформы пользовательского интерфейса можно настроить параметр вызова метода `AddDefaultUI` в `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="a68e8-112">The UI framework could be configured using a parameter to the `AddDefaultUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a68e8-113">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="a68e8-113">New behavior</span></span>

<span data-ttu-id="a68e8-114">Инфраструктурой пользовательского интерфейса по умолчанию для пользовательского интерфейса удостоверений является **Bootstrap 4**.</span><span class="sxs-lookup"><span data-stu-id="a68e8-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="a68e8-115">Платформа пользовательского интерфейса должна настраиваться в файле проекта, а не в вызове метода `AddDefaultUI`.</span><span class="sxs-lookup"><span data-stu-id="a68e8-115">The UI framework must be configured in your project file, instead of in the `AddDefaultUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a68e8-116">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="a68e8-116">Reason for change</span></span>

<span data-ttu-id="a68e8-117">Внедрение функции статических веб-ресурсов, которое потребовало переноса конфигурация платформы пользовательского интерфейса в MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a68e8-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="a68e8-118">Решение о том, какая платформа будет внедрена, является решением времени сборки, а не среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="a68e8-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a68e8-119">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="a68e8-119">Recommended action</span></span>

<span data-ttu-id="a68e8-120">Проверьте пользовательский интерфейс сайта, чтобы убедиться, что новые компоненты Bootstrap 4 совместимы.</span><span class="sxs-lookup"><span data-stu-id="a68e8-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="a68e8-121">При необходимости используйте свойство MSBuild `IdentityUIFrameworkVersion`, чтобы вернуться к Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="a68e8-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="a68e8-122">Добавьте свойство в элемент `<PropertyGroup>` в файле проекта:</span><span class="sxs-lookup"><span data-stu-id="a68e8-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="a68e8-123">Категория</span><span class="sxs-lookup"><span data-stu-id="a68e8-123">Category</span></span>

<span data-ttu-id="a68e8-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a68e8-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a68e8-125">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a68e8-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
