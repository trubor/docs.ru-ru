---
title: Критическое изменение. Класс WinHttpHandler удален из среды выполнения .NET
description: Сведения о критическом изменении в .NET 5,0, где класс WinHttpHandler был удален из среды выполнения .NET.
ms.date: 10/18/2020
ms.openlocfilehash: f8b9910ade8d459133791a23704d624a91cc5dff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759686"
---
# <a name="winhttphandler-removed-from-net-runtime"></a><span data-ttu-id="81f91-103">Класс WinHttpHandler удален из среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="81f91-103">WinHttpHandler removed from .NET runtime</span></span>

<span data-ttu-id="81f91-104">Класс `WinHttpHandler` был удален из сборки *System.Net.Http.dll*.</span><span class="sxs-lookup"><span data-stu-id="81f91-104">The `WinHttpHandler` class was removed from the *System.Net.Http.dll* assembly.</span></span> <span data-ttu-id="81f91-105">Теперь он доступен только как внештатный (OOB) [пакет NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span><span class="sxs-lookup"><span data-stu-id="81f91-105">It's now available only as an out-of-band (OOB) [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="81f91-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="81f91-106">Version introduced</span></span>

<span data-ttu-id="81f91-107">5.0</span><span class="sxs-lookup"><span data-stu-id="81f91-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="81f91-108">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="81f91-108">Change description</span></span>

<span data-ttu-id="81f91-109">В предыдущих версиях .NET класс <xref:System.Net.Http.WinHttpHandler> доступен как часть основных библиотек .NET.</span><span class="sxs-lookup"><span data-stu-id="81f91-109">In previous .NET versions, the <xref:System.Net.Http.WinHttpHandler> class is available as part of the core .NET libraries.</span></span> <span data-ttu-id="81f91-110">Начиная с .NET 5.0 класс <xref:System.Net.Http.WinHttpHandler> доступен только как отдельно устанавливаемый [пакет NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span><span class="sxs-lookup"><span data-stu-id="81f91-110">Starting in .NET 5.0, the <xref:System.Net.Http.WinHttpHandler> class is only available as a separately installed [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="81f91-111">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="81f91-111">Recommended action</span></span>

<span data-ttu-id="81f91-112">Установите пакет NuGet [System.Net.Http.WinHttpHandler](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span><span class="sxs-lookup"><span data-stu-id="81f91-112">Install the [System.Net.Http.WinHttpHandler NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span> <span data-ttu-id="81f91-113">Или, если не требуются специфические для WinHTTP функции, используйте вместо этого <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="81f91-113">Or, if you don't require WinHTTP-specific features, use <xref:System.Net.Http.SocketsHttpHandler> instead.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="81f91-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="81f91-114">Affected APIs</span></span>

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

### Category

Networking

-->
