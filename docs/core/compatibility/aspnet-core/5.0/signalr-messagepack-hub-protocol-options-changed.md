---
title: Критическое изменение. SignalR. Тип параметров протокола концентратора MessagePack изменился
description: Сведения о критическом изменении в ASP.NET Core 5.0 — SignalR. Тип параметров протокола концентратора MessagePack изменился
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b75dbec834699472f18b3058052274476bd9751d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760027"
---
# <a name="signalr-messagepack-hub-protocol-options-type-changed"></a><span data-ttu-id="1faee-103">SignalR. Тип параметров протокола концентратора MessagePack изменился</span><span class="sxs-lookup"><span data-stu-id="1faee-103">SignalR: MessagePack Hub Protocol options type changed</span></span>

<span data-ttu-id="1faee-104">Тип параметров протокола концентратора MessagePack ASP.NET Core SignalR изменился с `IList<MessagePack.IFormatterResolver>` на тип `MessagePackSerializerOptions` библиотеки [MessagePack](https://www.nuget.org/packages/MessagePack).</span><span class="sxs-lookup"><span data-stu-id="1faee-104">The ASP.NET Core SignalR MessagePack Hub Protocol options type has changed from `IList<MessagePack.IFormatterResolver>` to the [MessagePack](https://www.nuget.org/packages/MessagePack) library's `MessagePackSerializerOptions` type.</span></span>

<span data-ttu-id="1faee-105">Обсуждение этого изменения см. на странице [dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506).</span><span class="sxs-lookup"><span data-stu-id="1faee-105">For discussion on this change, see [dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1faee-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1faee-106">Version introduced</span></span>

<span data-ttu-id="1faee-107">5.0, предварительная версия 4</span><span class="sxs-lookup"><span data-stu-id="1faee-107">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="1faee-108">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="1faee-108">Old behavior</span></span>

<span data-ttu-id="1faee-109">Можно добавить параметры, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="1faee-109">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="1faee-110">И заменить параметры следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1faee-110">And replace the options as follows:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers = new List<MessagePack.IFormatterResolver>()
        {
            MessagePack.Resolvers.StandardResolver.Instance
        };
    });
```

## <a name="new-behavior"></a><span data-ttu-id="1faee-111">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="1faee-111">New behavior</span></span>

<span data-ttu-id="1faee-112">Можно добавить параметры, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="1faee-112">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="1faee-113">И заменить параметры следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1faee-113">And replace the options as follows:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions = MessagePackSerializerOptions
                .Standard
                .WithResolver(MessagePack.Resolvers.StandardResolver.Instance)
                .WithSecurity(MessagePackSecurity.UntrustedData);
    });
```

## <a name="reason-for-change"></a><span data-ttu-id="1faee-114">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="1faee-114">Reason for change</span></span>

<span data-ttu-id="1faee-115">Это изменение является частью перехода к MessagePack v2.x, который был объявлен на странице [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404).</span><span class="sxs-lookup"><span data-stu-id="1faee-115">This change is part of moving to MessagePack v2.x, which was announced in [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404).</span></span> <span data-ttu-id="1faee-116">В библиотеку v2.x добавлен API параметров, который проще в использовании и предоставляет больше возможностей, чем список `MessagePack.IFormatterResolver`, представленный ранее.</span><span class="sxs-lookup"><span data-stu-id="1faee-116">The v2.x library has added an options API that's easier to use and provides more features than the list of `MessagePack.IFormatterResolver` that was exposed before.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1faee-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="1faee-117">Recommended action</span></span>

<span data-ttu-id="1faee-118">Это критическое изменение затрагивает всех, кто настраивает значения на <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span><span class="sxs-lookup"><span data-stu-id="1faee-118">This breaking change affects anyone who is configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span> <span data-ttu-id="1faee-119">Если вы используете протокол концентратора MessagePack ASP.NET Core SignalR и изменяете параметры, внесите изменения, чтобы использовать новый API параметров, как показано выше.</span><span class="sxs-lookup"><span data-stu-id="1faee-119">If you're using the ASP.NET Core SignalR MessagePack Hub Protocol and modifying the options, update your usage to use the new options API as shown above.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1faee-120">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="1faee-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
