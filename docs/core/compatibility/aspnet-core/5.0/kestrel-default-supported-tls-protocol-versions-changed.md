---
title: Критическое изменение. Kestrel. Изменены поддерживаемые версии протокола TLS по умолчанию
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Kestrel. Изменены поддерживаемые версии протокола TLS по умолчанию
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 1e3ebd700e5bb603f95a8b20ebdbd61379f1e508
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497649"
---
# <a name="kestrel-default-supported-tls-protocol-versions-changed"></a>Kestrel. Изменены поддерживаемые версии протокола TLS по умолчанию

В Kestrel теперь используются стандартные версии протокола TLS, а не ограничивается лишь протоколами TLS 1.1 и TLS 1.2, как это было ранее.

Это изменение позволяет:

* использовать протокол TLS 1.3 по умолчанию в средах, поддерживающих его;
* использовать TLS 1.0 в некоторых средах (например, в Windows Server 2016 по умолчанию), в которых делать это обычно [нежелательно](/security/engineering/solving-tls1-problem).

Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).

## <a name="version-introduced"></a>Представленная версия

5.0, предварительная версия 6

## <a name="old-behavior"></a>Старое поведение

Kestrel требовалось, чтобы для подключений по умолчанию использовался TLS 1.1 или TLS 1.2.

## <a name="new-behavior"></a>Новое поведение

Kestrel позволяет операционной системе выбрать наилучший протокол для использования и блокирования небезопасных протоколов. <xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> теперь по умолчанию использует `SslProtocols.None` вместо `SslProtocols.Tls12 | SslProtocols.Tls11`.

## <a name="reason-for-change"></a>Причина изменения

Изменения были внесены для поддержки TLS 1.3 и будущих версий TLS по умолчанию по мере их появления.

## <a name="recommended-action"></a>Рекомендованное действие

Если к приложению не предъявляется особых требований, следует использовать новые значения по умолчанию. Убедитесь, что ваша система настроена на разрешение только безопасных протоколов.

Чтобы отключить старые протоколы, выполните одно из следующих действий.

* Отключите более старые протоколы, такие как TLS 1.0, на уровне всей системы, руководствуясь [инструкциями для Windows](../../../../framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry). В настоящее время он включен по умолчанию во всех версиях Windows.
* Вручную выберите протоколы, которые требуется поддерживать в коде, следующим образом:

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

К сожалению, нет API для исключения конкретных протоколов.

## <a name="affected-apis"></a>Затронутые API

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
