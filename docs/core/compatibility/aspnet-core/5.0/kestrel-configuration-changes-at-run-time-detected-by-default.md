---
title: Критическое изменение. Kestrel. Обнаружение изменений конфигурации во время выполнения включено по умолчанию
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Kestrel. Обнаружение изменений конфигурации во время выполнения включено по умолчанию
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 35b733cd872b9d6d944896349921c54f672b31b0
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498104"
---
# <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a><span data-ttu-id="5e36b-103">Kestrel. Обнаружение изменений конфигурации во время выполнения включено по умолчанию</span><span class="sxs-lookup"><span data-stu-id="5e36b-103">Kestrel: Configuration changes at run time detected by default</span></span>

<span data-ttu-id="5e36b-104">Kestrel теперь реагирует на изменения, внесенные в раздел `Kestrel` экземпляра `IConfiguration` проекта (например, *appsettings.json*) во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="5e36b-104">Kestrel now reacts to changes made to the `Kestrel` section of the project's `IConfiguration` instance (for example, *appsettings.json*) at run time.</span></span> <span data-ttu-id="5e36b-105">Дополнительные сведения о настройке Kestrel с помощью *appsettings.json* см. в примере *appsettings.json* в [конфигурации конечной точки](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span><span class="sxs-lookup"><span data-stu-id="5e36b-105">To learn more about how to configure Kestrel using *appsettings.json*, see the *appsettings.json* example in [Endpoint configuration](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span></span>

<span data-ttu-id="5e36b-106">Kestrel привязывает, отменяет привязку и повторно привязывает конечные точки при необходимости для реагирования на соответствующие изменения в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5e36b-106">Kestrel will bind, unbind, and rebind endpoints as necessary to react to these configuration changes.</span></span>

<span data-ttu-id="5e36b-107">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#22807](https://github.com/dotnet/aspnetcore/issues/22807).</span><span class="sxs-lookup"><span data-stu-id="5e36b-107">For discussion, see issue [dotnet/aspnetcore#22807](https://github.com/dotnet/aspnetcore/issues/22807).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="5e36b-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="5e36b-108">Version introduced</span></span>

<span data-ttu-id="5e36b-109">5.0 (предварительная версия 7)</span><span class="sxs-lookup"><span data-stu-id="5e36b-109">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="5e36b-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="5e36b-110">Old behavior</span></span>

<span data-ttu-id="5e36b-111">До ASP.NET Core 5.0 (предварительная версия 6) Kestrel не поддерживал изменение конфигурации во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="5e36b-111">Before ASP.NET Core 5.0 Preview 6, Kestrel didn't support changing configuration at run time.</span></span>

<span data-ttu-id="5e36b-112">В ASP.NET Core 5.0 (предварительная версия 6) можно было выбрать поведение по умолчанию для действий, выполняемых в настоящее время, для реагирования на изменения в конфигурации во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="5e36b-112">In ASP.NET Core 5.0 Preview 6, you could opt into the now-default behavior of reacting to configuration changes at run time.</span></span> <span data-ttu-id="5e36b-113">Включение в конфигурацию требуемой привязки Kestrel вручную:</span><span class="sxs-lookup"><span data-stu-id="5e36b-113">Opting in required binding Kestrel's configuration manually:</span></span>

```csharp
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
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

## <a name="new-behavior"></a><span data-ttu-id="5e36b-114">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="5e36b-114">New behavior</span></span>

<span data-ttu-id="5e36b-115">По умолчанию Kestrel реагирует на изменения конфигурации во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="5e36b-115">Kestrel reacts to configuration changes at run time by default.</span></span> <span data-ttu-id="5e36b-116">Для поддержки этого изменения <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> по умолчанию вызывает `KestrelServerOptions.Configure(IConfiguration, bool)` с `reloadOnChange: true`.</span><span class="sxs-lookup"><span data-stu-id="5e36b-116">To support that change, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> calls `KestrelServerOptions.Configure(IConfiguration, bool)` with `reloadOnChange: true` by default.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="5e36b-117">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="5e36b-117">Reason for change</span></span>

<span data-ttu-id="5e36b-118">Было внесено изменение для поддержки перенастройки конечной точки во время выполнения без полного перезапуска сервера.</span><span class="sxs-lookup"><span data-stu-id="5e36b-118">The change was made to support endpoint reconfiguration at run time without completely restarting the server.</span></span> <span data-ttu-id="5e36b-119">В отличие от полного перезапуска сервера, привязка неизмененных конечных точек не отменяется даже временно.</span><span class="sxs-lookup"><span data-stu-id="5e36b-119">Unlike with a full server restart, unchanged endpoints aren't unbound even temporarily.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5e36b-120">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="5e36b-120">Recommended action</span></span>

* <span data-ttu-id="5e36b-121">В большинстве сценариев, в которых раздел конфигурации Kestrel по умолчанию не изменяется во время выполнения, это изменение не оказывает влияния и никаких действий не требуется.</span><span class="sxs-lookup"><span data-stu-id="5e36b-121">For most scenarios in which Kestrel's default configuration section doesn't change at run time, this change has no impact and no action is needed.</span></span>
* <span data-ttu-id="5e36b-122">Для сценариев, в которых раздел конфигурации Kestrel по умолчанию изменяется во время выполнения и Kestrel должен реагировать на него, это поведение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5e36b-122">For scenarios in which Kestrel's default configuration section does change at run time and Kestrel should react to it, this is now the default behavior.</span></span>
* <span data-ttu-id="5e36b-123">Для сценариев, в которых раздел конфигурации Kestrel по умолчанию изменяется во время выполнения и Kestrel не должен реагировать на него, можно отказаться от приведенных ниже действий.</span><span class="sxs-lookup"><span data-stu-id="5e36b-123">For scenarios in which Kestrel's default configuration section changes at run time and Kestrel shouldn't react to it, you can opt out as follows:</span></span>

    ```csharp
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
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="5e36b-124">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="5e36b-124">**Notes:**</span></span>

<span data-ttu-id="5e36b-125">Это изменение не изменяет поведение перегрузки `KestrelServerOptions.Configure(IConfiguration)`, которое по умолчанию по-прежнему `reloadOnChange: false`.</span><span class="sxs-lookup"><span data-stu-id="5e36b-125">This change doesn't modify the behavior of the `KestrelServerOptions.Configure(IConfiguration)` overload, which still defaults to the `reloadOnChange: false` behavior.</span></span>

<span data-ttu-id="5e36b-126">Также важно убедиться, что источник конфигурации поддерживает перезагрузку.</span><span class="sxs-lookup"><span data-stu-id="5e36b-126">It's also important to make sure the configuration source supports reloading.</span></span> <span data-ttu-id="5e36b-127">Для источников JSON перезагрузка настраивается путем вызова `AddJsonFile(path, reloadOnChange: true)`.</span><span class="sxs-lookup"><span data-stu-id="5e36b-127">For JSON sources, reloading is configured by calling `AddJsonFile(path, reloadOnChange: true)`.</span></span> <span data-ttu-id="5e36b-128">Для *appsettings.json* и *appsettings.{Environment}.json* повторная загрузка уже настроена по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5e36b-128">Reloading is already configured by default for *appsettings.json* and *appsettings.{Environment}.json*.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5e36b-129">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="5e36b-129">Affected APIs</span></span>

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
