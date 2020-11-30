---
title: Рекомендации по использованию классов System.Net
description: Следуйте этим рекомендациям по использованию классов, содержащихся в System.Net, при программировании в .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
ms.openlocfilehash: 170e8cfe0a7d7c911122dafe18b8a5081ceb3d2d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250779"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="476d0-103">Рекомендации по использованию классов System.Net</span><span class="sxs-lookup"><span data-stu-id="476d0-103">Best Practices for System.Net Classes</span></span>

<span data-ttu-id="476d0-104">В этом разделе приводятся рекомендации по наиболее эффективному использованию классов, содержащихся в <xref:System.Net>:</span><span class="sxs-lookup"><span data-stu-id="476d0-104">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
- <span data-ttu-id="476d0-105">Рекомендации по протоколу TLS см. в разделе [Рекомендации по использованию протокола TLS с .NET Framework](tls.md).</span><span class="sxs-lookup"><span data-stu-id="476d0-105">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

- <span data-ttu-id="476d0-106">По возможности рекомендуется всегда использовать <xref:System.Net.WebRequest> и <xref:System.Net.WebResponse> вместо приведения типов к классам потомков.</span><span class="sxs-lookup"><span data-stu-id="476d0-106">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="476d0-107">Приложения, использующие **WebRequest** и **WebResponse**, могут использовать преимущества новых протоколов Интернета, не требуя при этом серьезного изменения кода.</span><span class="sxs-lookup"><span data-stu-id="476d0-107">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
- <span data-ttu-id="476d0-108">При написании приложений ASP.NET, которые выполняются на сервере с использованием классов **System.Net**, с точки зрения производительности зачастую лучше использовать асинхронные методы для <xref:System.Net.WebRequest.GetResponse%2A> и <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="476d0-108">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
- <span data-ttu-id="476d0-109">Число открытых подключений к интернет-ресурсам может заметно влиять на производительность и пропускную способность сети.</span><span class="sxs-lookup"><span data-stu-id="476d0-109">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="476d0-110">В **System.Net** по умолчанию используется два подключения для каждого приложения на один ведущий узел.</span><span class="sxs-lookup"><span data-stu-id="476d0-110">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="476d0-111">С помощью свойства <xref:System.Net.ServicePoint.ConnectionLimit%2A> в <xref:System.Net.ServicePoint> приложения можно увеличить число его подключений для конкретного узла.</span><span class="sxs-lookup"><span data-stu-id="476d0-111">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="476d0-112">Свойство <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> позволяет увеличить это значение по умолчанию для всех узлов.</span><span class="sxs-lookup"><span data-stu-id="476d0-112">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
- <span data-ttu-id="476d0-113">При написании протоколов уровня сокета по возможности используйте <xref:System.Net.Sockets.TcpClient> или <xref:System.Net.Sockets.UdpClient> вместо прямого использования <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="476d0-113">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="476d0-114">Эти два клиентских класса инкапсулируют создание сокетов TCP и UDP, не требуя от вас обработки сведений о подключении.</span><span class="sxs-lookup"><span data-stu-id="476d0-114">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
- <span data-ttu-id="476d0-115">При доступе к узлам, требующим ввода учетных данных, используйте класс <xref:System.Net.CredentialCache> для создания кэша учетных данных вместо того, чтобы предоставлять их с каждым запросом.</span><span class="sxs-lookup"><span data-stu-id="476d0-115">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="476d0-116">Класс **CredentialCache** выполняет поиск соответствующих запросу учетных данных в кэше, освобождая вас от необходимости создавать и предоставлять учетные данные на основе URL.</span><span class="sxs-lookup"><span data-stu-id="476d0-116">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="476d0-117">См. также</span><span class="sxs-lookup"><span data-stu-id="476d0-117">See also</span></span>

- [<span data-ttu-id="476d0-118">Сетевое программирование в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="476d0-118">Network Programming in the .NET Framework</span></span>](index.md)
