---
title: Критическое изменение. Изменены заметки ссылочного типа, допускающего значение NULL
description: Узнайте о критическом изменении в ASP.NET Core 6.0, связанном с заметками ссылочного типа, допускающего значения NULL
author: scottaddie
ms.author: scaddie
ms.date: 02/16/2021
ms.openlocfilehash: 6277b57e0340d099d11ddf2e955ab1fc969e3270
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2021
ms.locfileid: "100643588"
---
# <a name="nullable-reference-type-annotations-changed"></a><span data-ttu-id="0d63e-103">Изменения в аннотациях ссылочного типа, допускающего значения NULL</span><span class="sxs-lookup"><span data-stu-id="0d63e-103">Nullable reference type annotations changed</span></span>

<span data-ttu-id="0d63e-104">_**Работа над этой проблемой еще ведется. Все критические изменения, связанные с заметками о допустимости значений NULL, будут включены в это решение проблемы в ходе исправления ошибок в ASP.NET Core 6.0.**_</span><span class="sxs-lookup"><span data-stu-id="0d63e-104">_**This issue represents a work-in-progress. All breaking changes to nullability annotations will be aggregated into this issue throughout the course of ASP.NET Core 6.0.**_</span></span>

<span data-ttu-id="0d63e-105">Начиная с версии ASP.NET Core 5.0, заметки о допустимости значений NULL применялись к частям кода.</span><span class="sxs-lookup"><span data-stu-id="0d63e-105">Starting in ASP.NET Core 5.0, nullability annotations have been applied to parts of the code.</span></span> <span data-ttu-id="0d63e-106">С самого начала работы над этой возможностью [ожидались проблемы](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/api-guidelines/nullability.md#breaking-change-guidance) с заметками, которые требовали исправлений.</span><span class="sxs-lookup"><span data-stu-id="0d63e-106">From the outset of this effort, [mistakes were expected](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/api-guidelines/nullability.md#breaking-change-guidance) in these annotations and fixes would need to be made.</span></span> <span data-ttu-id="0d63e-107">Мы работаем над обновлением некоторых заметок, ранее примененных в ASP.NET Core 6.0.</span><span class="sxs-lookup"><span data-stu-id="0d63e-107">In ASP.NET Core 6.0, some previously applied annotations are being updated.</span></span> <span data-ttu-id="0d63e-108">Некоторые из этих изменений представляют собой критические изменения исходного кода.</span><span class="sxs-lookup"><span data-stu-id="0d63e-108">Some of these changes are considered source breaking changes.</span></span> <span data-ttu-id="0d63e-109">Такие изменения приводят к несовместимости или большему ограничению API.</span><span class="sxs-lookup"><span data-stu-id="0d63e-109">The changes lead to the APIs being incompatible or more restrictive.</span></span> <span data-ttu-id="0d63e-110">Использование обновленных API может привести к появлению предупреждений во время сборки при использовании в проектах, в которых включены ссылочные типы, допускающие значения NULL.</span><span class="sxs-lookup"><span data-stu-id="0d63e-110">The updated APIs may result in build-time warnings when used in projects that have nullable reference types enabled.</span></span>

<span data-ttu-id="0d63e-111">Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#27564](https://github.com/dotnet/aspnetcore/issues/27564).</span><span class="sxs-lookup"><span data-stu-id="0d63e-111">For discussion, see GitHub issue [dotnet/aspnetcore#27564](https://github.com/dotnet/aspnetcore/issues/27564).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0d63e-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="0d63e-112">Version introduced</span></span>

<span data-ttu-id="0d63e-113">6,0</span><span class="sxs-lookup"><span data-stu-id="0d63e-113">6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="0d63e-114">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="0d63e-114">Old behavior</span></span>

<span data-ttu-id="0d63e-115">В затронутых API применялись неправильные заметки ссылочного типа, допускающего значения NULL.</span><span class="sxs-lookup"><span data-stu-id="0d63e-115">The affected APIs have incorrect nullable reference type annotations.</span></span> <span data-ttu-id="0d63e-116">Предупреждения при сборке не отображались или отображались неправильно.</span><span class="sxs-lookup"><span data-stu-id="0d63e-116">Build warnings are either absent or incorrect.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="0d63e-117">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="0d63e-117">New behavior</span></span>

<span data-ttu-id="0d63e-118">Создаются новые предупреждения при сборке.</span><span class="sxs-lookup"><span data-stu-id="0d63e-118">New build warnings are produced.</span></span> <span data-ttu-id="0d63e-119">Для затронутых API больше не отображаются неправильные предупреждения при сборке.</span><span class="sxs-lookup"><span data-stu-id="0d63e-119">Incorrect build warnings are no longer produced for the affected APIs.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="0d63e-120">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="0d63e-120">Reason for change</span></span>

<span data-ttu-id="0d63e-121">Благодаря отзывам и дальнейшему тестированию заметки, допускающие значение NULL для затрагиваемых API, были определены как неточные.</span><span class="sxs-lookup"><span data-stu-id="0d63e-121">Through feedback and further testing, the nullable annotations for the affected APIs were determined to be inaccurate.</span></span> <span data-ttu-id="0d63e-122">В обновленных заметках правильно представлены контракты допустимости значений NULL для API.</span><span class="sxs-lookup"><span data-stu-id="0d63e-122">The updated annotations now correctly represent the nullability contracts for the APIs.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="0d63e-123">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="0d63e-123">Recommended action</span></span>

<span data-ttu-id="0d63e-124">Обновите код вызова этих API для отражения изменений в контрактах, допускающих значения NULL.</span><span class="sxs-lookup"><span data-stu-id="0d63e-124">Update code calling these APIs to reflect the revised nullability contracts.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="0d63e-125">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="0d63e-125">Affected APIs</span></span>

* <xref:Microsoft.AspNetCore.Components.ParameterView.FromDictionary%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Components.RenderTree.Renderer.DispatchEventAsync%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeEdit.RemovedAttributeName?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Authentication.AuthenticationSchemeOptions.ForwardDefaultSelector%2A?displayProperty=nameWithType>
* <xref:Microsoft.Net.Http.Headers.RangeConditionHeaderValue.%23ctor%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Connections.IConnectionListener.AcceptAsync%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.Infrastructure.IApplicationDiscriminator.Discriminator%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.DataProtectionOptions.ApplicationDiscriminator%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.AuthenticatedEncryptorFactory.CreateEncryptorInstance%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngCbcAuthenticatedEncryptorFactory.CreateEncryptorInstance%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngGcmAuthenticatedEncryptorFactory.CreateEncryptorInstance%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.IAuthenticatedEncryptorFactory.CreateEncryptorInstance%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.ManagedAuthenticatedEncryptorFactory.CreateEncryptorInstance%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.IKey.CreateEncryptor%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.AuthenticatedEncryptorConfiguration%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlEncryptor%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlRepository%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.XmlEncryption.ICertificateResolver.ResolveCertificate%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.DataProtectionUtilityExtensions.GetApplicationUniqueIdentifier%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.Repositories.FileSystemXmlRepository.DefaultKeyStorageDirectory%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.Repositories.RegistryXmlRepository.DefaultRegistryKey%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.XmlEncryption.CertificateResolver.ResolveCertificate%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Endpoint.%23ctor%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Endpoint.RequestDelegate%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Routing.RouteValueDictionary.TryAdd%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Routing.LinkGenerator.GetUriByAddress%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Set%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Features.FeatureCollection.Set%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Get%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Authentication.Cookies.ITicketStore.RetrieveAsync%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Get%60%601?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Set%60%601(%60%600)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Features.FeatureCollection.Set%60%601(%60%600)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Mvc.ModelBinding.ModelStateDictionary.SetModelValue(System.String,System.Object,System.String)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Mvc.ModelBinding.ModelStateDictionary.Item(System.String)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ClientValidatorItem.%23ctor%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ClientValidatorItem.Validator%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Endpoint.%23ctor%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Routing.RouteValueDictionary.TryAdd(System.String,System.Object)?displayProperty=nameWithType>>
* <xref:Microsoft.AspNetCore.Routing.LinkGenerator.GetUriByAddress%60%601(%60%600,Microsoft.AspNetCore.Routing.RouteValueDictionary,System.String,Microsoft.AspNetCore.Http.HostString,Microsoft.AspNetCore.Http.PathString,Microsoft.AspNetCore.Http.FragmentString,Microsoft.AspNetCore.Routing.LinkOptions)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.Infrastructure.IApplicationDiscriminator.Discriminator?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.DataProtectionOptions.ApplicationDiscriminator?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.AuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngCbcAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngGcmAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.IAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.ManagedAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.IKey.CreateEncryptor?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.AuthenticatedEncryptorConfiguration?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlEncryptor?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlRepository?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.XmlEncryption.ICertificateResolver.ResolveCertificate(System.String)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.DataProtectionUtilityExtensions.GetApplicationUniqueIdentifier(System.IServiceProvider)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.Repositories.FileSystemXmlRepository.DefaultKeyStorageDirectory?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.Repositories.RegistryXmlRepository.DefaultRegistryKey?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.XmlEncryption.CertificateResolver.ResolveCertificate(System.String)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Connections.IConnectionListener.AcceptAsync(System.Threading.CancellationToken)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Authentication.AuthenticationSchemeOptions.ForwardDefaultSelector?displayProperty=nameWithType>
* <xref:Microsoft.Net.Http.Headers.RangeConditionHeaderValue.%23ctor(Microsoft.Net.Http.Headers.EntityTagHeaderValue)?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

- `Overload:Microsoft.AspNetCore.Components.ParameterView.FromDictionary`
- `Overload:Microsoft.AspNetCore.Components.RenderTree.Renderer.DispatchEventAsync`
- `F:Microsoft.AspNetCore.Components.RenderTree.RenderTreeEdit.RemovedAttributeName`
- `Overload:Microsoft.AspNetCore.Authentication.AuthenticationSchemeOptions.ForwardDefaultSelector`
- `Overload:Microsoft.Net.Http.Headers.RangeConditionHeaderValue.#ctor`
- `Overload:Microsoft.AspNetCore.Connections.IConnectionListener.AcceptAsync`
- `Overload:Microsoft.AspNetCore.DataProtection.Infrastructure.IApplicationDiscriminator.Discriminator`
- `Overload:Microsoft.AspNetCore.DataProtection.DataProtectionOptions.ApplicationDiscriminator`
- `Overload:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.AuthenticatedEncryptorFactory.CreateEncryptorInstance`
- `Overload:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngCbcAuthenticatedEncryptorFactory.CreateEncryptorInstance`
- `Overload:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngGcmAuthenticatedEncryptorFactory.CreateEncryptorInstance`
- `Overload:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.IAuthenticatedEncryptorFactory.CreateEncryptorInstance`
- `Overload:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.ManagedAuthenticatedEncryptorFactory.CreateEncryptorInstance`
- `Overload:Microsoft.AspNetCore.DataProtection.KeyManagement.IKey.CreateEncryptor`
- `Overload:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.AuthenticatedEncryptorConfiguration`
- `Overload:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlEncryptor`
- `Overload:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlRepository`
- `Overload:Microsoft.AspNetCore.DataProtection.XmlEncryption.ICertificateResolver.ResolveCertificate`
- `Overload:Microsoft.AspNetCore.DataProtection.DataProtectionUtilityExtensions.GetApplicationUniqueIdentifier`
- `Overload:Microsoft.AspNetCore.DataProtection.Repositories.FileSystemXmlRepository.DefaultKeyStorageDirectory`
- `Overload:Microsoft.AspNetCore.DataProtection.Repositories.RegistryXmlRepository.DefaultRegistryKey`
- `Overload:Microsoft.AspNetCore.DataProtection.XmlEncryption.CertificateResolver.ResolveCertificate`
- `Overload:Microsoft.AspNetCore.Http.Endpoint.#ctor`
- `Overload:Microsoft.AspNetCore.Http.Endpoint.RequestDelegate`
- `Overload:Microsoft.AspNetCore.Routing.RouteValueDictionary.TryAdd`
- `Overload:Microsoft.AspNetCore.Routing.LinkGenerator.GetUriByAddress`
- `Overload:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Set`
- `Overload:Microsoft.AspNetCore.Http.Features.FeatureCollection.Set`
- `Overload:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Get`
- `Overload:Microsoft.AspNetCore.Authentication.Cookies.ITicketStore.RetrieveAsync`
- `M:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Get%60%601`
- `M:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Set%60%601(%60%600)`
- `M:Microsoft.AspNetCore.Http.Features.FeatureCollection.Set%60%601(%60%600)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ModelStateDictionary.SetModelValue(System.String,System.Object,System.String)`
- `P:Microsoft.AspNetCore.Mvc.ModelBinding.ModelStateDictionary.Item(System.String)`
- `Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ClientValidatorItem.#ctor`
- `Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ClientValidatorItem.Validator`
- `Overload:Microsoft.AspNetCore.Http.Endpoint.#ctor`
- `M:Microsoft.AspNetCore.Routing.RouteValueDictionary.TryAdd(System.String,System.Object)`
- `M:Microsoft.AspNetCore.Routing.LinkGenerator.GetUriByAddress%60%601(%60%600,Microsoft.AspNetCore.Routing.RouteValueDictionary,System.String,Microsoft.AspNetCore.Http.HostString,Microsoft.AspNetCore.Http.PathString,Microsoft.AspNetCore.Http.FragmentString,Microsoft.AspNetCore.Routing.LinkOptions)`
- `P:Microsoft.AspNetCore.DataProtection.Infrastructure.IApplicationDiscriminator.Discriminator`
- `P:Microsoft.AspNetCore.DataProtection.DataProtectionOptions.ApplicationDiscriminator`
- `M:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.AuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)`
- `M:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngCbcAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)`
- `M:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngGcmAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)`
- `M:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.IAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)`
- `M:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.ManagedAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)`
- `M:Microsoft.AspNetCore.DataProtection.KeyManagement.IKey.CreateEncryptor`
- `P:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.AuthenticatedEncryptorConfiguration`
- `P:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlEncryptor`
- `P:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlRepository`
- `M:Microsoft.AspNetCore.DataProtection.XmlEncryption.ICertificateResolver.ResolveCertificate(System.String)`
- `M:Microsoft.AspNetCore.DataProtection.DataProtectionUtilityExtensions.GetApplicationUniqueIdentifier(System.IServiceProvider)`
- `P:Microsoft.AspNetCore.DataProtection.Repositories.FileSystemXmlRepository.DefaultKeyStorageDirectory`
- `P:Microsoft.AspNetCore.DataProtection.Repositories.RegistryXmlRepository.DefaultRegistryKey`
- `M:Microsoft.AspNetCore.DataProtection.XmlEncryption.CertificateResolver.ResolveCertificate(System.String)`
- `M:Microsoft.AspNetCore.Connections.IConnectionListener.AcceptAsync(System.Threading.CancellationToken)`
- `P:Microsoft.AspNetCore.Authentication.AuthenticationSchemeOptions.ForwardDefaultSelector`
- `M:Microsoft.Net.Http.Headers.RangeConditionHeaderValue.#ctor(Microsoft.Net.Http.Headers.EntityTagHeaderValue)`

-->