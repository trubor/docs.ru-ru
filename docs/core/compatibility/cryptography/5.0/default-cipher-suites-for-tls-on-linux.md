---
title: Критическое изменение. Комплекты шифров TLS по умолчанию для .NET в Linux
description: Ознакомьтесь с критическим изменением в .NET 5.0, где .NET в Linux теперь учитывает конфигурацию OpenSSL для наборов шифров по умолчанию при выполнении шифрования TLS/SSL.
ms.date: 10/16/2020
ms.openlocfilehash: f1c23517161ac213a9cd7cf6e7da8eebeb91583b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759573"
---
# <a name="default-tls-cipher-suites-for-net-on-linux"></a><span data-ttu-id="4d1ee-103">Комплекты шифров TLS по умолчанию для .NET в Linux</span><span class="sxs-lookup"><span data-stu-id="4d1ee-103">Default TLS cipher suites for .NET on Linux</span></span>

<span data-ttu-id="4d1ee-104">Теперь .NET для Linux учитывает конфигурацию OpenSSL для наборов шифров по умолчанию при выполнении шифрования TLS/SSL с помощью класса <xref:System.Net.Security.SslStream> или операций более высокого уровня, таких как HTTPS с помощью класса <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-104">.NET, on Linux, now respects the OpenSSL configuration for default cipher suites when doing TLS/SSL via the <xref:System.Net.Security.SslStream> class or higher-level operations, such as HTTPS via the <xref:System.Net.Http.HttpClient> class.</span></span> <span data-ttu-id="4d1ee-105">Если комплекты шифров по умолчанию не настроены явно, .NET для Linux использует строго ограниченный список разрешенных комплектов шифров.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-105">When default cipher suites aren't explicitly configured, .NET on Linux uses a tightly restricted list of permitted cipher suites.</span></span>

## <a name="change-description"></a><span data-ttu-id="4d1ee-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="4d1ee-106">Change description</span></span>

<span data-ttu-id="4d1ee-107">В предыдущих версиях .NET не учитывается конфигурация системы для комплектов шифров по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-107">In previous .NET versions, .NET does not respect system configuration for default cipher suites.</span></span> <span data-ttu-id="4d1ee-108">Список комплектов шифров по умолчанию для .NET в Linux является нестрогим.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-108">The default cipher suite list for .NET on Linux is very permissive.</span></span>

<span data-ttu-id="4d1ee-109">Начиная с .NET 5.0 .NET для Linux учитывает конфигурацию OpenSSL для комплектов шифров по умолчанию, если она указана в файле *openssl.cnf*.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-109">Starting in .NET 5.0, .NET on Linux respects the OpenSSL configuration for default cipher suites when it's specified in *openssl.cnf*.</span></span> <span data-ttu-id="4d1ee-110">Если комплекты шифров не настроены явно, единственными разрешенными комплектами шифров являются следующие:</span><span class="sxs-lookup"><span data-stu-id="4d1ee-110">When cipher suites aren't explicitly configured, the only permitted cipher suites are as follows:</span></span>

- <span data-ttu-id="4d1ee-111">Комплекты шифров TLS 1.3</span><span class="sxs-lookup"><span data-stu-id="4d1ee-111">TLS 1.3 cipher suites</span></span>
- <span data-ttu-id="4d1ee-112">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="4d1ee-112">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="4d1ee-113">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="4d1ee-113">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="4d1ee-114">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="4d1ee-114">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="4d1ee-115">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="4d1ee-115">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="4d1ee-116">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="4d1ee-116">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="4d1ee-117">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="4d1ee-117">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span></span>
- <span data-ttu-id="4d1ee-118">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="4d1ee-118">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="4d1ee-119">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="4d1ee-119">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span></span>

<span data-ttu-id="4d1ee-120">Поскольку это резервное значение по умолчанию не включает комплекты шифров, которые совместимы с TLS 1.0 или TLS 1.1, эти старые версии протоколов по умолчанию отключаются.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-120">Since this fallback default doesn't include any cipher suites that are compatible with TLS 1.0 or TLS 1.1, these older protocol versions are effectively disabled by default.</span></span>

<span data-ttu-id="4d1ee-121">Если указано значение CipherSuitePolicy для SslStream для конкретного сеанса, по-прежнему будет заменяться содержимое файла конфигурации и (или) резервное значение по умолчанию .NET.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-121">Supplying a CipherSuitePolicy value to SslStream for a specific session will still replace the configuration file content and/or .NET fallback default.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="4d1ee-122">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="4d1ee-122">Reason for change</span></span>

<span data-ttu-id="4d1ee-123">Пользователи, работающие с .NET для Linux, запрашивают изменение конфигурации по умолчанию для <xref:System.Net.Security.SslStream> на ту, которая обеспечивает высокую степень безопасности согласно результатам сторонних средств оценки.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-123">Users running .NET on Linux requested that the default configuration for <xref:System.Net.Security.SslStream> be changed to one that provided a high security rating from third-party assessment tools.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="4d1ee-124">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="4d1ee-124">Version introduced</span></span>

<span data-ttu-id="4d1ee-125">5.0</span><span class="sxs-lookup"><span data-stu-id="4d1ee-125">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4d1ee-126">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="4d1ee-126">Recommended action</span></span>

<span data-ttu-id="4d1ee-127">Новые значения по умолчанию, скорее всего, будут работать при взаимодействии с современными клиентами или серверами.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-127">The new defaults are likely to work when communicating with modern clients or servers.</span></span> <span data-ttu-id="4d1ee-128">Если необходимо расширить список комплектов шифров по умолчанию для работы с устаревшими клиентами (или для взаимодействия с устаревшими серверами), укажите значение `CipherSuitePolicy` или измените файл конфигурации OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-128">If you need to expand the default cipher suite list to accept legacy clients (or to contact legacy servers), either specify a `CipherSuitePolicy` value or change the OpenSSL configuration file.</span></span> <span data-ttu-id="4d1ee-129">Во многих дистрибутивах Linux файл конфигурации OpenSSL находится по пути */etc/ssl/openssl.cnf*.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-129">On many Linux distributions, the OpenSSL configuration file is at */etc/ssl/openssl.cnf*.</span></span>

<span data-ttu-id="4d1ee-130">В этом примере файл *openssl.cnf* определяет минимальный набор правил, эквивалентный заданной по умолчанию политике комплектов шифров для .NET 5.0 и более поздних версий для Linux.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-130">This sample *openssl.cnf* file is a minimal file that's equivalent to the default cipher suites policy for .NET 5.0 and later on Linux.</span></span> <span data-ttu-id="4d1ee-131">Вместо замены системного файла объедините эти понятия с файлом, который присутствует в вашей системе.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-131">Instead of replacing the system file, merge these concepts with the file that's present on your system.</span></span>

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

<span data-ttu-id="4d1ee-132">В дистрибутивах Red Hat Enterprise Linux, CentOS и Fedora в приложениях .NET по умолчанию используются комплекты шифров, разрешенные политиками шифрования на уровне системы.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-132">On the Red Hat Enterprise Linux, CentOS, and Fedora distributions, .NET applications default to the cipher suites permitted by the system-wide cryptographic policies.</span></span> <span data-ttu-id="4d1ee-133">В этих дистрибутивах следует использовать конфигурацию политик шифрования вместо *openssl.cnf*.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-133">On these distributions, use the crypto-policies configuration instead of *openssl.cnf*.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="4d1ee-134">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="4d1ee-134">Affected APIs</span></span>

<span data-ttu-id="4d1ee-135">Невозможно обнаружить с помощью анализа API.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-135">Not detectible via API analysis.</span></span>

<!--

### Affected APIs

- Not detectible via API analysis.

### Category

- Cryptography
- Security

-->
