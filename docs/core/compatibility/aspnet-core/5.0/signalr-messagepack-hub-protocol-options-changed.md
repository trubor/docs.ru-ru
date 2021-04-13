---
title: Критическое изменение. SignalR. Тип параметров протокола концентратора MessagePack изменился
description: Сведения о критическом изменении в ASP.NET Core 5.0 — SignalR. Тип параметров протокола концентратора MessagePack изменился
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 5a1a3728e4f842074c80f5063dcfe47ad8858674
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497922"
---
# <a name="signalr-messagepack-hub-protocol-options-type-changed"></a>SignalR. Тип параметров протокола концентратора MessagePack изменился

Тип параметров протокола концентратора MessagePack ASP.NET Core SignalR изменился с `IList<MessagePack.IFormatterResolver>` на тип `MessagePackSerializerOptions` библиотеки [MessagePack](https://www.nuget.org/packages/MessagePack).

Обсуждение этого изменения см. на странице [dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506).

## <a name="version-introduced"></a>Представленная версия

5.0, предварительная версия 4

## <a name="old-behavior"></a>Старое поведение

Можно добавить параметры, как показано в следующем примере:

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

И заменить параметры следующим образом:

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

## <a name="new-behavior"></a>Новое поведение

Можно добавить параметры, как показано в следующем примере:

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

И заменить параметры следующим образом:

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

## <a name="reason-for-change"></a>Причина изменения

Это изменение является частью перехода к MessagePack v2.x, который был объявлен на странице [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404). В библиотеку v2.x добавлен API параметров, который проще в использовании и предоставляет больше возможностей, чем список `MessagePack.IFormatterResolver`, представленный ранее.

## <a name="recommended-action"></a>Рекомендованное действие

Это критическое изменение затрагивает всех, кто настраивает значения на <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>. Если вы используете протокол концентратора MessagePack ASP.NET Core SignalR и изменяете параметры, внесите изменения, чтобы использовать новый API параметров, как показано выше.

## <a name="affected-apis"></a>Затронутые API

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
