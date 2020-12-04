---
title: Критическое изменение. Kestrel. Изменены поддерживаемые версии протокола TLS по умолчанию
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Kestrel. Изменены поддерживаемые версии протокола TLS по умолчанию
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: d7018be7cc778560b7b9c65472d42d7e0fbf623d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759593"
---
# <a name="kestrel-default-supported-tls-protocol-versions-changed"></a><span data-ttu-id="7b558-103">Kestrel. Изменены поддерживаемые версии протокола TLS по умолчанию</span><span class="sxs-lookup"><span data-stu-id="7b558-103">Kestrel: Default supported TLS protocol versions changed</span></span>

<span data-ttu-id="7b558-104">В Kestrel теперь используются стандартные версии протокола TLS, а не ограничивается лишь протоколами TLS 1.1 и TLS 1.2, как это было ранее.</span><span class="sxs-lookup"><span data-stu-id="7b558-104">Kestrel now uses the system default TLS protocol versions rather than restricting connections to the TLS 1.1 and TLS 1.2 protocols like it did previously.</span></span>

<span data-ttu-id="7b558-105">Это изменение позволяет:</span><span class="sxs-lookup"><span data-stu-id="7b558-105">This change allows:</span></span>

* <span data-ttu-id="7b558-106">использовать протокол TLS 1.3 по умолчанию в средах, поддерживающих его;</span><span class="sxs-lookup"><span data-stu-id="7b558-106">TLS 1.3 to be used by default in environments that support it.</span></span>
* <span data-ttu-id="7b558-107">использовать TLS 1.0 в некоторых средах (например, в Windows Server 2016 по умолчанию), в которых делать это обычно [нежелательно](/security/engineering/solving-tls1-problem).</span><span class="sxs-lookup"><span data-stu-id="7b558-107">TLS 1.0 to be used in some environments (such as Windows Server 2016 by default), which is usually [not desirable](/security/engineering/solving-tls1-problem).</span></span>

<span data-ttu-id="7b558-108">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span><span class="sxs-lookup"><span data-stu-id="7b558-108">For discussion, see issue [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7b558-109">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="7b558-109">Version introduced</span></span>

<span data-ttu-id="7b558-110">5.0, предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="7b558-110">5.0 Preview 6</span></span>

## <a name="old-behavior"></a><span data-ttu-id="7b558-111">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="7b558-111">Old behavior</span></span>

<span data-ttu-id="7b558-112">Kestrel требовалось, чтобы для подключений по умолчанию использовался TLS 1.1 или TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="7b558-112">Kestrel required that connections use TLS 1.1 or TLS 1.2 by default.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="7b558-113">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="7b558-113">New behavior</span></span>

<span data-ttu-id="7b558-114">Kestrel позволяет операционной системе выбрать наилучший протокол для использования и блокирования небезопасных протоколов.</span><span class="sxs-lookup"><span data-stu-id="7b558-114">Kestrel allows the operating system to choose the best protocol to use and to block insecure protocols.</span></span> <span data-ttu-id="7b558-115"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> теперь по умолчанию использует `SslProtocols.None` вместо `SslProtocols.Tls12 | SslProtocols.Tls11`.</span><span class="sxs-lookup"><span data-stu-id="7b558-115"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> now defaults to `SslProtocols.None` instead of `SslProtocols.Tls12 | SslProtocols.Tls11`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="7b558-116">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="7b558-116">Reason for change</span></span>

<span data-ttu-id="7b558-117">Изменения были внесены для поддержки TLS 1.3 и будущих версий TLS по умолчанию по мере их появления.</span><span class="sxs-lookup"><span data-stu-id="7b558-117">The change was made to support TLS 1.3 and future TLS versions by default as they become available.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7b558-118">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="7b558-118">Recommended action</span></span>

<span data-ttu-id="7b558-119">Если к приложению не предъявляется особых требований, следует использовать новые значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="7b558-119">Unless your app has a specific reason not to, you should use the new defaults.</span></span> <span data-ttu-id="7b558-120">Убедитесь, что ваша система настроена на разрешение только безопасных протоколов.</span><span class="sxs-lookup"><span data-stu-id="7b558-120">Verify your system is configured to allow only secure protocols.</span></span>

<span data-ttu-id="7b558-121">Чтобы отключить старые протоколы, выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="7b558-121">To disable older protocols, take one of the following actions:</span></span>

* <span data-ttu-id="7b558-122">Отключите более старые протоколы, такие как TLS 1.0, на уровне всей системы, руководствуясь [инструкциями для Windows](../../../../framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry).</span><span class="sxs-lookup"><span data-stu-id="7b558-122">Disable older protocols, such as TLS 1.0, system-wide with the [Windows instructions](../../../../framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry).</span></span> <span data-ttu-id="7b558-123">В настоящее время он включен по умолчанию во всех версиях Windows.</span><span class="sxs-lookup"><span data-stu-id="7b558-123">It's currently enabled by default on all Windows versions.</span></span>
* <span data-ttu-id="7b558-124">Вручную выберите протоколы, которые требуется поддерживать в коде, следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7b558-124">Manually select which protocols you want to support in code as follows:</span></span>

    ```csharp
    using System.Security.Authentication;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="7b558-125">К сожалению, нет API для исключения конкретных протоколов.</span><span class="sxs-lookup"><span data-stu-id="7b558-125">Unfortunately, there's no API to exclude specific protocols.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7b558-126">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="7b558-126">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
