---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032126"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="51ebb-101">Версии OpenSSL в macOS</span><span class="sxs-lookup"><span data-stu-id="51ebb-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="51ebb-102">В среде выполнения .NET Core 3.0 и более поздних версий в macOS вместо версий OpenSSL 1.0.x для типов <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl> и <xref:System.Security.Cryptography.SafeEvpPKeyHandle> теперь предпочтительно использовать версии OpenSSL 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="51ebb-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="51ebb-103">Среда выполнения .NET Core 2.1 теперь поддерживает версии OpenSSL 1.1.x, однако предпочтительными по-прежнему являются версии OpenSSL 1.0.x.</span><span class="sxs-lookup"><span data-stu-id="51ebb-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="51ebb-104">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="51ebb-104">Change description</span></span>

<span data-ttu-id="51ebb-105">Ранее в среде выполнения .NET Core для типов, которые взаимодействуют с OpenSSL, использовались версии OpenSSL 1.0.x в macOS.</span><span class="sxs-lookup"><span data-stu-id="51ebb-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="51ebb-106">Последняя версия OpenSSL 1.0.x (OpenSSL 1.0.2) теперь не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="51ebb-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="51ebb-107">Для сохранения типов, использующих OpenSSL в поддерживаемых версиях OpenSSL, в средах выполнения .NET Core 3.0 и более поздних версий теперь используются более новые версии OpenSSL в macOS.</span><span class="sxs-lookup"><span data-stu-id="51ebb-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="51ebb-108">В связи с этим изменением поведение сред выполнения .NET Core в macOS теперь реализуется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="51ebb-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="51ebb-109">В средах выполнения .NET Core 3.0 и более поздних версий при условии доступности используется OpenSSL 1.1.x, и только если версия 1.1.x не доступна, осуществляется откат к OpenSSL 1.0.x.</span><span class="sxs-lookup"><span data-stu-id="51ebb-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="51ebb-110">Для вызывающих объектов, использующих типы взаимодействия OpenSSL с пользовательскими методами P/Invoke, необходимо следовать указаниям в примечаниях <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51ebb-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="51ebb-111">Если не проверить значение <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion>, приложение может аварийно завершить работу.</span><span class="sxs-lookup"><span data-stu-id="51ebb-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="51ebb-112">В средах выполнения .NET Core 2.1 при условии доступности используется OpenSSL 1.0.x, а если версия 1.0.x не доступна, осуществляется откат к OpenSSL 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="51ebb-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="51ebb-113">В среде выполнения версии 2.1 предпочтительно использовать более раннюю версию OpenSSL, поскольку в .NET Core 2.1 отсутствует свойство <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType>, в связи с чем во время выполнения невозможно гарантированно определить версию OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="51ebb-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="51ebb-114">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="51ebb-114">Version introduced</span></span>

- <span data-ttu-id="51ebb-115">.NET Core 2.1.16</span><span class="sxs-lookup"><span data-stu-id="51ebb-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="51ebb-116">.NET Core 3.0.3</span><span class="sxs-lookup"><span data-stu-id="51ebb-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="51ebb-117">.NET Core 3.1.2</span><span class="sxs-lookup"><span data-stu-id="51ebb-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="51ebb-118">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="51ebb-118">Recommended action</span></span>

- <span data-ttu-id="51ebb-119">Удалите версию OpenSSL 1.0.2, если она больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="51ebb-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="51ebb-120">Установите версию OpenSSL 1.1.x, если используются типы <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl> или <xref:System.Security.Cryptography.SafeEvpPKeyHandle>.</span><span class="sxs-lookup"><span data-stu-id="51ebb-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="51ebb-121">Если вы используете типы взаимодействия OpenSSL с пользовательскими методами P/Invoke, необходимо следовать указаниям в примечаниях <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51ebb-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="51ebb-122">Категория</span><span class="sxs-lookup"><span data-stu-id="51ebb-122">Category</span></span>

<span data-ttu-id="51ebb-123">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="51ebb-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="51ebb-124">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="51ebb-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
