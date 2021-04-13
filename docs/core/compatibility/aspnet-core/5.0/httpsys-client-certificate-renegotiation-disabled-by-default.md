---
title: 'Критическое изменение. HttpSys: Повторное согласование сертификата клиента по умолчанию отключено'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — HttpSys. Повторное согласование сертификата клиента по умолчанию отключено
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 41c421417125061fa9879f14a1307aa1463ca033
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498130"
---
# <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a><span data-ttu-id="b2dd5-103">HttpSys: Повторное согласование сертификата клиента по умолчанию отключено</span><span class="sxs-lookup"><span data-stu-id="b2dd5-103">HttpSys: Client certificate renegotiation disabled by default</span></span>

<span data-ttu-id="b2dd5-104">Возможность повторного согласования подключения и запроса сертификата клиента по умолчанию отключена.</span><span class="sxs-lookup"><span data-stu-id="b2dd5-104">The option to renegotiate a connection and request a client certificate has been disabled by default.</span></span> <span data-ttu-id="b2dd5-105">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#23181](https://github.com/dotnet/aspnetcore/issues/23181).</span><span class="sxs-lookup"><span data-stu-id="b2dd5-105">For discussion, see issue [dotnet/aspnetcore#23181](https://github.com/dotnet/aspnetcore/issues/23181).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b2dd5-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="b2dd5-106">Version introduced</span></span>

<span data-ttu-id="b2dd5-107">ASP.NET Core 5.0</span><span class="sxs-lookup"><span data-stu-id="b2dd5-107">ASP.NET Core 5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="b2dd5-108">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="b2dd5-108">Old behavior</span></span>

<span data-ttu-id="b2dd5-109">Подключение можно повторно согласовать, чтобы запросить сертификат клиента.</span><span class="sxs-lookup"><span data-stu-id="b2dd5-109">The connection can be renegotiated to request a client certificate.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="b2dd5-110">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="b2dd5-110">New behavior</span></span>

<span data-ttu-id="b2dd5-111">Сертификаты клиентов можно запросить только во время первоначального подтверждения соединения.</span><span class="sxs-lookup"><span data-stu-id="b2dd5-111">Client certificates can only be requested during the initial connection handshake.</span></span> <span data-ttu-id="b2dd5-112">Подробную информацию см. в описании запроса на внесение изменений [dotnet/aspnetcore#23162](https://github.com/dotnet/aspnetcore/pull/23162).</span><span class="sxs-lookup"><span data-stu-id="b2dd5-112">For more information, see pull request [dotnet/aspnetcore#23162](https://github.com/dotnet/aspnetcore/pull/23162).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b2dd5-113">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="b2dd5-113">Reason for change</span></span>

<span data-ttu-id="b2dd5-114">Повторное согласование привело к ряду проблем с производительностью и взаимоблокировкой.</span><span class="sxs-lookup"><span data-stu-id="b2dd5-114">Renegotiation caused a number of performance and deadlock issues.</span></span> <span data-ttu-id="b2dd5-115">Оно также не поддерживается в HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="b2dd5-115">It's also not supported in HTTP/2.</span></span> <span data-ttu-id="b2dd5-116">Расширенный контекст с момента реализации этого параметра для управления таким поведением в ASP.NET Core 3.1 см. на странице [dotnet/aspnetcore#14806](https://github.com/dotnet/aspnetcore/issues/14806).</span><span class="sxs-lookup"><span data-stu-id="b2dd5-116">For additional context from when the option to control this behavior was introduced in ASP.NET Core 3.1, see issue [dotnet/aspnetcore#14806](https://github.com/dotnet/aspnetcore/issues/14806).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b2dd5-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="b2dd5-117">Recommended action</span></span>

<span data-ttu-id="b2dd5-118">Приложения, для которых требуются сертификаты клиентов, должны использовать *netsh.exe* для присвоения параметру `clientcertnegotiation` значения `enabled`.</span><span class="sxs-lookup"><span data-stu-id="b2dd5-118">Apps that require client certificates should use *netsh.exe* to set the `clientcertnegotiation` option to `enabled`.</span></span> <span data-ttu-id="b2dd5-119">Дополнительные сведения см. в разделе [Команды netsh http](/windows-server/networking/technologies/netsh/netsh-http).</span><span class="sxs-lookup"><span data-stu-id="b2dd5-119">For more information, see [netsh http commands](/windows-server/networking/technologies/netsh/netsh-http).</span></span>

<span data-ttu-id="b2dd5-120">Если необходимо включить сертификаты клиентов только для некоторых частей приложения, см. инструкции в разделе [Дополнительные сертификаты клиента](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span><span class="sxs-lookup"><span data-stu-id="b2dd5-120">If you want client certificates enabled for only some parts of your app, see the guidance at [Optional client certificates](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span></span>

<span data-ttu-id="b2dd5-121">Если необходимо вернуть предыдущее поведение при повторном согласовании, задайте для `HttpSysOptions.ClientCertificateMethod` старое значение `ClientCertificateMethod.AllowRenegotiate`.</span><span class="sxs-lookup"><span data-stu-id="b2dd5-121">If you need the old renegotiate behavior, set `HttpSysOptions.ClientCertificateMethod` to the old value `ClientCertificateMethod.AllowRenegotiate`.</span></span> <span data-ttu-id="b2dd5-122">Этот способ не рекомендуется по причинам, описанным выше и в соответствующем руководстве.</span><span class="sxs-lookup"><span data-stu-id="b2dd5-122">This isn't recommended for the reasons outlined above and in the linked guidance.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b2dd5-123">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="b2dd5-123">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->
