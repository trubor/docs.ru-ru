---
title: Критическое изменение. Аутентификация. API-интерфейсы и пакеты AzureAD.UI и AzureADB2C.UI помечены как устаревшие
description: Сведения о критическом изменении в ASP.NET Core 5.0 — аутентификация. API-интерфейсы и пакеты AzureAD.UI и AzureADB2C.UI помечены как устаревшие
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 179b0b248131a7c02c5f79fbba4562be0ad49d77
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498273"
---
# <a name="authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete"></a><span data-ttu-id="67d0b-103">Аутентификация. API-интерфейсы и пакеты AzureAD.UI и AzureADB2C.UI помечены как устаревшие</span><span class="sxs-lookup"><span data-stu-id="67d0b-103">Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete</span></span>

<span data-ttu-id="67d0b-104">В ASP.NET Core 2.1 интеграцию с проверкой подлинности Azure Active Directory (Azure AD) и Azure Active Directory B2C (Azure AD B2C) обеспечивают пакеты [Microsoft.AspNetCore.Authentication.AzureAD.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) и [Microsoft.AspNetCore.Authentication.AzureADB2C.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI).</span><span class="sxs-lookup"><span data-stu-id="67d0b-104">In ASP.NET Core 2.1, integration with Azure Active Directory (Azure AD) and Azure Active Directory B2C (Azure AD B2C) authentication is provided by the [Microsoft.AspNetCore.Authentication.AzureAD.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) and [Microsoft.AspNetCore.Authentication.AzureADB2C.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) packages.</span></span> <span data-ttu-id="67d0b-105">Функциональные возможности, предоставляемые этими пакетами, основаны на конечной точке Azure AD версии 1.0.</span><span class="sxs-lookup"><span data-stu-id="67d0b-105">The functionality provided by these packages is based on the Azure AD v1.0 endpoint.</span></span>

<span data-ttu-id="67d0b-106">В ASP.NET Core 5.0 и более поздних версиях интеграцию с проверкой подлинности Azure AD и Azure AD B2C обеспечивает пакет [Microsoft.Identity.Web](https://www.nuget.org/packages/Microsoft.Identity.Web).</span><span class="sxs-lookup"><span data-stu-id="67d0b-106">In ASP.NET Core 5.0 and later, integration with Azure AD and Azure AD B2C authentication is provided by the [Microsoft.Identity.Web](https://www.nuget.org/packages/Microsoft.Identity.Web) package.</span></span> <span data-ttu-id="67d0b-107">Этот пакет основан на платформе Microsoft Identity, которая ранее называлась конечной точкой Azure AD версии 2.0.</span><span class="sxs-lookup"><span data-stu-id="67d0b-107">This package is based on the Microsoft Identity Platform, which is formerly known as the Azure AD v2.0 endpoint.</span></span> <span data-ttu-id="67d0b-108">Следовательно, использовать старые API-интерфейсы в пакетах `Microsoft.AspNetCore.Authentication.AzureAD.UI` и `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="67d0b-108">Consequently, the old APIs in the `Microsoft.AspNetCore.Authentication.AzureAD.UI` and `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` packages were deprecated.</span></span>

<span data-ttu-id="67d0b-109">Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#25807](https://github.com/dotnet/aspnetcore/issues/25807).</span><span class="sxs-lookup"><span data-stu-id="67d0b-109">For discussion, see GitHub issue [dotnet/aspnetcore#25807](https://github.com/dotnet/aspnetcore/issues/25807).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="67d0b-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="67d0b-110">Version introduced</span></span>

<span data-ttu-id="67d0b-111">5.0, предварительная версия 8</span><span class="sxs-lookup"><span data-stu-id="67d0b-111">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="67d0b-112">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="67d0b-112">Old behavior</span></span>

<span data-ttu-id="67d0b-113">API-интерфейсы не помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="67d0b-113">The APIs weren't marked as obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="67d0b-114">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="67d0b-114">New behavior</span></span>

<span data-ttu-id="67d0b-115">API-интерфейсы помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="67d0b-115">The APIs are marked as obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="67d0b-116">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="67d0b-116">Reason for change</span></span>

<span data-ttu-id="67d0b-117">Возможности проверки подлинности Azure AD и Azure AD B2C были перенесены в API-интерфейсы Библиотеки проверки подлинности Майкрософт (MSAL), предоставляемые `Microsoft.Identity.Web`.</span><span class="sxs-lookup"><span data-stu-id="67d0b-117">The Azure AD and Azure AD B2C authentication functionality was migrated to Microsoft Authentication Library (MSAL) APIs that are provided by `Microsoft.Identity.Web`.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="67d0b-118">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="67d0b-118">Recommended action</span></span>

<span data-ttu-id="67d0b-119">Следуйте указаниям по API `Microsoft.Identity.Web` для [веб-приложений](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) и [веб-API](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).</span><span class="sxs-lookup"><span data-stu-id="67d0b-119">Follow the `Microsoft.Identity.Web` API guidance for [web apps](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) and [web APIs](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="67d0b-120">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="67d0b-120">Affected APIs</span></span>

* [<span data-ttu-id="67d0b-121">Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="67d0b-121">Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="67d0b-122">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults</span><span class="sxs-lookup"><span data-stu-id="67d0b-122">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureaddefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="67d0b-123">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions</span><span class="sxs-lookup"><span data-stu-id="67d0b-123">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureadoptions?view=aspnetcore-3.0)
* [<span data-ttu-id="67d0b-124">Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="67d0b-124">Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2cauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="67d0b-125">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults</span><span class="sxs-lookup"><span data-stu-id="67d0b-125">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2cdefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="67d0b-126">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions</span><span class="sxs-lookup"><span data-stu-id="67d0b-126">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2coptions?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions`

-->
