---
title: 'Критическое изменение: из общей платформы Microsoft.AspNetCore.App удалены сборки'
description: Сведения о критических изменениях в ASP.NET Core 6.0, где некоторые сборки были удалены из общей платформы Microsoft.AspNetCore.App.
ms.date: 04/02/2021
ms.openlocfilehash: e6a0aa97dd97eae2cdc5aa8ae64e277840d6a083
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255263"
---
# <a name="assemblies-removed-from-microsoftaspnetcoreapp-shared-framework"></a><span data-ttu-id="79e4c-103">Сборки, удаленные из общей платформы Microsoft.AspNetCore.App</span><span class="sxs-lookup"><span data-stu-id="79e4c-103">Assemblies removed from Microsoft.AspNetCore.App shared framework</span></span>

<span data-ttu-id="79e4c-104">Из целевого пакета ASP.NET Core были удалены следующие две сборки:</span><span class="sxs-lookup"><span data-stu-id="79e4c-104">The following two assemblies were removed from the ASP.NET Core targeting pack:</span></span>

- <span data-ttu-id="79e4c-105">System.Security.Permissions</span><span class="sxs-lookup"><span data-stu-id="79e4c-105">System.Security.Permissions</span></span>
- <span data-ttu-id="79e4c-106">System.Windows.Extensions</span><span class="sxs-lookup"><span data-stu-id="79e4c-106">System.Windows.Extensions</span></span>

<span data-ttu-id="79e4c-107">Кроме того, следующие сборки были удалены из пакета среды выполнения ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="79e4c-107">In addition, the following assemblies were removed from the ASP.NET Core runtime pack:</span></span>

- <span data-ttu-id="79e4c-108">Microsoft.Win32.SystemEvents</span><span class="sxs-lookup"><span data-stu-id="79e4c-108">Microsoft.Win32.SystemEvents</span></span>
- <span data-ttu-id="79e4c-109">System.Drawing.Common</span><span class="sxs-lookup"><span data-stu-id="79e4c-109">System.Drawing.Common</span></span>
- <span data-ttu-id="79e4c-110">System.Security.Permissions</span><span class="sxs-lookup"><span data-stu-id="79e4c-110">System.Security.Permissions</span></span>
- <span data-ttu-id="79e4c-111">System.Windows.Extensions</span><span class="sxs-lookup"><span data-stu-id="79e4c-111">System.Windows.Extensions</span></span>

## <a name="version-introduced"></a><span data-ttu-id="79e4c-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="79e4c-112">Version introduced</span></span>

<span data-ttu-id="79e4c-113">ASP.NET Core 6.0</span><span class="sxs-lookup"><span data-stu-id="79e4c-113">ASP.NET Core 6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="79e4c-114">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="79e4c-114">Old behavior</span></span>

<span data-ttu-id="79e4c-115">Приложения могут использовать API из этих библиотек, путем обращения к общей платформе [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app).</span><span class="sxs-lookup"><span data-stu-id="79e4c-115">Applications could use APIs provided by these libraries by referencing the [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) shared framework.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="79e4c-116">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="79e4c-116">New behavior</span></span>

<span data-ttu-id="79e4c-117">Если вы используете API из затронутых сборок без наличия [PackageReference](../../../project-sdk/msbuild-props.md#packagereference) в файле проекта, то могут возникать ошибки во время выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="79e4c-117">If you use APIs from the affected assemblies without having a [PackageReference](../../../project-sdk/msbuild-props.md#packagereference) in your project file, you might see run-time errors.</span></span> <span data-ttu-id="79e4c-118">Например, в приложении, использующем отражение для доступа к API из одной из этих сборок без добавления явной ссылки на пакет, будут возникать ошибки во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="79e4c-118">For example, an application that uses reflection to access APIs from one of these assemblies without adding an explicit reference to the package will have run-time errors.</span></span> <span data-ttu-id="79e4c-119">Компонент `PackageReference` обеспечивает наличие сборок в выходных данных приложения.</span><span class="sxs-lookup"><span data-stu-id="79e4c-119">The `PackageReference` ensures that the assemblies are present as part of the application output.</span></span>

<span data-ttu-id="79e4c-120">Обсуждение этого вопроса см. на странице <https://github.com/dotnet/aspnetcore/issues/31007>.</span><span class="sxs-lookup"><span data-stu-id="79e4c-120">For discussion, see <https://github.com/dotnet/aspnetcore/issues/31007>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="79e4c-121">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="79e4c-121">Reason for change</span></span>

<span data-ttu-id="79e4c-122">Это изменение было введено для уменьшения размера общей платформы ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="79e4c-122">This change was introduced to reduce the size of the ASP.NET Core shared framework.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="79e4c-123">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="79e4c-123">Recommended action</span></span>

<span data-ttu-id="79e4c-124">Чтобы продолжить использование этих API-интерфейсов в проекте, добавьте в него [PackageReference](../../../project-sdk/msbuild-props.md#packagereference).</span><span class="sxs-lookup"><span data-stu-id="79e4c-124">To continue using these APIs in your project, add a [PackageReference](../../../project-sdk/msbuild-props.md#packagereference).</span></span> <span data-ttu-id="79e4c-125">Пример:</span><span class="sxs-lookup"><span data-stu-id="79e4c-125">For example:</span></span>

```xml
<PackageReference Include="System.Security.Permissions" Version="6.0.0" />
```

## <a name="affected-apis"></a><span data-ttu-id="79e4c-126">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="79e4c-126">Affected APIs</span></span>

- <xref:System.Security.Permissions?displayProperty=fullName>
- <xref:System.Media?displayProperty=fullName>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate2UI?displayProperty=fullName>
- <xref:System.Xaml.Permissions.XamlAccessLevel?displayProperty=fullName>

<!--

## Category

ASP.NET Core

## Affected APIs

- `N:System.Security.Permissions`
- `N:System.Media`
- `N:System.Security.Cryptography.X509Certificates.X509Certificate2UI`
- `N:System.Xaml.Permissions.XamlAccessLevel`

-->
