---
title: HTTP
description: Узнайте о полной поддержке HTTP, которая доступна в .NET Framework посредством классов HttpWebRequest и HttpWebResponse.
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
ms.openlocfilehash: 62c4ddb7e4b904be501ed2938692bce405c7e5f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253405"
---
# <a name="http"></a><span data-ttu-id="b2048-103">HTTP</span><span class="sxs-lookup"><span data-stu-id="b2048-103">HTTP</span></span>

<span data-ttu-id="b2048-104">Платформа .NET предоставляет полную поддержку протокола HTTP, на который приходит большая часть интернет-трафика, с помощью классов <xref:System.Net.HttpWebRequest> и <xref:System.Net.HttpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="b2048-104">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="b2048-105">Эти классы, производные от <xref:System.Net.WebRequest> и <xref:System.Net.WebResponse>, возвращаются по умолчанию всякий раз, когда статический метод <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> обнаруживает URI, начинающийся с "http" или "https".</span><span class="sxs-lookup"><span data-stu-id="b2048-105">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="b2048-106">В большинстве случаев классы **WebRequest** и **WebResponse** предоставляют все необходимое для выполнения запроса, но если вам необходим доступ к возможностям HTTP-протокола, представленным в виде свойств, можно выполнить приведение этих классов к **HttpWebRequest** или **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="b2048-106">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="b2048-107">Классы **HttpWebRequest** и **HttpWebResponse** инкапсулируют стандартную транзакцию "запрос-ответ" HTTP и предоставляют доступ к основным заголовкам HTTP.</span><span class="sxs-lookup"><span data-stu-id="b2048-107">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="b2048-108">Эти классы также поддерживают большинство функций HTTP 1.1, включая конвейеризацию, отправку и получение данных в блоках, проверку подлинности, предварительную проверку подлинности, шифрование, поддержку прокси-сервера, проверку сертификата сервера и управление соединениями.</span><span class="sxs-lookup"><span data-stu-id="b2048-108">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="b2048-109">Пользовательские заголовки и заголовки, доступ к которым через свойства не предоставляется, можно получить в разделе **Заголовки**.</span><span class="sxs-lookup"><span data-stu-id="b2048-109">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="b2048-110">Класс **HttpWebRequest** — класс по умолчанию, который используется классом **WebRequest**. Этот класс не требуется регистрировать перед тем, как передавать URI в метод **WebRequest.Create**.</span><span class="sxs-lookup"><span data-stu-id="b2048-110">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="b2048-111">Чтобы приложение автоматически перенаправляло запросы HTTP, можно установить свойство <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> в значение **true** (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="b2048-111">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="b2048-112">Приложение будет перенаправлять запросы, а свойство <xref:System.Net.HttpWebResponse.ResponseUri%2A> объекта **HttpWebResponse** будет содержать веб-ресурс, который ответил на запрос.</span><span class="sxs-lookup"><span data-stu-id="b2048-112">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="b2048-113">Если установить свойство **AllowAutoRedirect** в значение **false**, приложение сможет обрабатывать перенаправления как ошибки протокола HTTP.</span><span class="sxs-lookup"><span data-stu-id="b2048-113">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="b2048-114">Приложения получают ошибки протокола HTTP, перехватывая <xref:System.Net.WebException> со свойством <xref:System.Net.WebException.Status%2A>, установленным в значение <xref:System.Net.WebExceptionStatus>.</span><span class="sxs-lookup"><span data-stu-id="b2048-114">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="b2048-115">Свойство <xref:System.Net.WebException.Response%2A> означает фактическую обнаруженную ошибку HTTP и содержит объект **WebResponse**, отправленный сервером.</span><span class="sxs-lookup"><span data-stu-id="b2048-115">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2048-116">См. также</span><span class="sxs-lookup"><span data-stu-id="b2048-116">See also</span></span>

- [<span data-ttu-id="b2048-117">Доступ к Интернету через прокси-сервер</span><span class="sxs-lookup"><span data-stu-id="b2048-117">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="b2048-118">Использование протоколов приложений</span><span class="sxs-lookup"><span data-stu-id="b2048-118">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="b2048-119">Практическое руководство. Доступ к свойствам, относящимся к HTTP</span><span class="sxs-lookup"><span data-stu-id="b2048-119">How to: Access HTTP-Specific Properties</span></span>](how-to-access-http-specific-properties.md)
