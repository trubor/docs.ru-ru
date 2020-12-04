---
title: Критическое изменение. Blazor WebAssembly не поддерживает интерфейсы API System.Security.Cryptography
description: Сведения о критическом изменении в .NET 5.0, где интерфейсы API шифрования выдают исключение при запуске в браузере.
ms.date: 09/16/2020
ms.openlocfilehash: ec10fa777e91f641b5582378830536a0cfa8dd72
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759650"
---
# <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a><span data-ttu-id="ce924-103">Blazor WebAssembly не поддерживает интерфейсы API System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="ce924-103">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>

<span data-ttu-id="ce924-104">API <xref:System.Security.Cryptography> выдают исключение <xref:System.PlatformNotSupportedException> при выполнении в браузере.</span><span class="sxs-lookup"><span data-stu-id="ce924-104"><xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> at run time when run on a browser.</span></span>

## <a name="change-description"></a><span data-ttu-id="ce924-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="ce924-105">Change description</span></span>

<span data-ttu-id="ce924-106">В предыдущих версиях .NET большинство API <xref:System.Security.Cryptography> были недоступны приложениям Blazor WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="ce924-106">In previous .NET versions, most of the <xref:System.Security.Cryptography> APIs aren't available to Blazor WebAssembly apps.</span></span> <span data-ttu-id="ce924-107">Начиная с .NET 5.0, приложения Blazor WebAssembly предназначены для использования в полной контактной зоне API .NET 5, но из-за ограничений песочницы браузера поддерживаются не все API .NET 5.</span><span class="sxs-lookup"><span data-stu-id="ce924-107">Starting in .NET 5.0, Blazor WebAssembly apps target the full .NET 5 API surface area, however, not all .NET 5 APIs are supported due to browser sandbox constraints.</span></span> <span data-ttu-id="ce924-108">В .NET 5.0 и более поздних версиях неподдерживаемые API <xref:System.Security.Cryptography> выдают исключение <xref:System.PlatformNotSupportedException> при выполнении в WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="ce924-108">In .NET 5.0 and later versions, the unsupported <xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> when running on WebAssembly.</span></span>

> [!TIP]
> <span data-ttu-id="ce924-109">[Анализатор совместимости платформ](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) помечает все вызовы затронутых API при сборке проекта, который поддерживает платформу браузера.</span><span class="sxs-lookup"><span data-stu-id="ce924-109">The [Platform compatibility analyzer](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) will flag any calls to the affected APIs when you build a project that supports the browser platform.</span></span> <span data-ttu-id="ce924-110">Этот анализатор выполняется по умолчанию в приложениях .NET 5.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="ce924-110">This analyzer runs by default in .NET 5.0 and later apps.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ce924-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="ce924-111">Reason for change</span></span>

<span data-ttu-id="ce924-112">Корпорация Майкрософт не может предоставить OpenSSL как зависимость в конфигурации Blazor WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="ce924-112">Microsoft is unable to ship OpenSSL as a dependency in the Blazor WebAssembly configuration.</span></span> <span data-ttu-id="ce924-113">Мы пытались решить эту проблему, выполнив интеграцию с API `SubtleCrypto` браузера.</span><span class="sxs-lookup"><span data-stu-id="ce924-113">We attempted to work around this by trying to integrate with the browser's `SubtleCrypto` API.</span></span> <span data-ttu-id="ce924-114">К сожалению, это требует кардинального изменения API, что усложняет интеграцию.</span><span class="sxs-lookup"><span data-stu-id="ce924-114">Unfortunately, it required significant API changes that made it too hard to integrate.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ce924-115">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="ce924-115">Version introduced</span></span>

<span data-ttu-id="ce924-116">5.0</span><span class="sxs-lookup"><span data-stu-id="ce924-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ce924-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="ce924-117">Recommended action</span></span>

<span data-ttu-id="ce924-118">В настоящее время мы не можем предложить решение.</span><span class="sxs-lookup"><span data-stu-id="ce924-118">There are no good workarounds to suggest at this time.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ce924-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="ce924-119">Affected APIs</span></span>

<span data-ttu-id="ce924-120">Все API <xref:System.Security.Cryptography?displayProperty=fullName> за исключением следующих:</span><span class="sxs-lookup"><span data-stu-id="ce924-120">All <xref:System.Security.Cryptography?displayProperty=fullName> APIs except the following:</span></span>

- `System.Security.Cryptography.RandomNumberGenerator`
- `System.Security.Cryptography.IncrementalHash`
- `System.Security.Cryptography.SHA1`
- `System.Security.Cryptography.SHA256`
- `System.Security.Cryptography.SHA384`
- `System.Security.Cryptography.SHA512`
- `System.Security.Cryptography.SHA1Managed`
- `System.Security.Cryptography.SHA256Managed`
- `System.Security.Cryptography.SHA384Managed`
- `System.Security.Cryptography.SHA512Managed`

<!--

### Affected APIs

- `T:System.Security.Cryptography`

### Category

- ASP.NET Core
- Cryptography

-->
