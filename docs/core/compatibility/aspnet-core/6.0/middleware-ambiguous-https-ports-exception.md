---
title: 'Критическое изменение. ПО промежуточного слоя: ПО промежуточного слоя перенаправления HTTPS создает исключение для неоднозначных портов HTTPS'
description: Сведения о критическом изменении в ASP.NET Core 6.0 — ПО промежуточного слоя. ПО промежуточного слоя перенаправления HTTPS создает исключение для неоднозначных портов HTTPS
ms.author: scaddie
ms.date: 02/04/2021
ms.openlocfilehash: e299fc7d2be295d723f5389a2b4cd6896078a752
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255081"
---
# <a name="middleware-https-redirection-middleware-throws-exception-on-ambiguous-https-ports"></a>ПО промежуточного слоя: ПО промежуточного слоя перенаправления HTTPS создает исключение для неоднозначных портов HTTPS

В ASP.NET Core 6.0 [ПО промежуточного слоя перенаправления HTTPS](xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A) вызывает исключение типа <xref:System.InvalidOperationException> при обнаружении нескольких портов HTTPS в конфигурации сервера. Сообщение исключения содержит текст "Не удается определить HTTPS порт от IServerAddressesFeature, найдено несколько значений. Задайте требуемый порт явно в HttpsRedirectionOptions.HttpsPort."

Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#29222](https://github.com/dotnet/aspnetcore/issues/29222).

## <a name="version-introduced"></a>Представленная версия

ASP.NET Core 6.0

## <a name="old-behavior"></a>Старое поведение

Если ПО промежуточного слоя перенаправления HTTPS не настроено явно с помощью порта, во время первого запроса выполняется поиск <xref:Microsoft.AspNetCore.Hosting.Server.Features.IServerAddressesFeature>, чтобы определить HTTPS-порт, на который должно выполняться перенаправление.

Если нет HTTPS-портов или нескольких отдельных портов, то неясно, какой порт следует использовать. ПО промежуточного слоя регистрирует предупреждение и отключается. HTTP-запросы обрабатываются обычным образом.

## <a name="new-behavior"></a>Новое поведение

Если ПО промежуточного слоя перенаправления HTTPS не настроено явно с помощью порта, во время первого запроса выполняется поиск `IServerAddressesFeature`, чтобы определить HTTPS-порт, на который должно выполняться перенаправление.

Если HTTPS-порты отсутствуют, то ПО промежуточного слоя по-прежнему регистрирует предупреждение и отключается. HTTP-запросы обрабатываются обычным образом. Это поведение поддерживает следующее:

* Сценарии разработки без протокола HTTPS.
* Сценарии размещения, в которых работа протокола TLS завершается до достижения сервера.

При наличии нескольких разных портов неясно, какой порт следует использовать. ПО промежуточного слоя создает исключение и обработка HTTP-запроса завершается сбоем.

## <a name="reason-for-change"></a>Причина изменения

Это изменение предотвращает возможность обслуживания потенциально конфиденциальных данных через незашифрованные HTTP-соединения, если известно, что протокол HTTPS доступен.

## <a name="recommended-action"></a>Рекомендованное действие

Чтобы включить перенаправление HTTPS, если на сервере имеется несколько HTTPS-портов, в конфигурации необходимо указать один порт. Дополнительные сведения см. в разделе [Конфигурация портов](/aspnet/core/security/enforcing-ssl?view=aspnetcore-5.0&preserve-view=true#port-configuration).

Если ПО промежуточного слоя перенаправления HTTPS в приложении не требуется, удалите `UseHttpsRedirection` из *Startup.cs*.

Если необходимо динамически выбрать правильный HTTPS-порт, оставьте отзыв в статье на сайте GitHub [dotnet/aspnetcore#21291](https://github.com/dotnet/aspnetcore/issues/21291).

## <a name="affected-apis"></a>Затронутые API

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection`

-->
