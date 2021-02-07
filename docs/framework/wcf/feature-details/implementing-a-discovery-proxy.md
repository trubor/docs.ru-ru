---
description: Дополнительные сведения см. в статье Реализация прокси-сервера обнаружения.
title: Реализация прокси-сервера обнаружения
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: cfd897e114c99bcacb24e9981ee4a3e99e06636c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734039"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="b459c-103">Реализация прокси-сервера обнаружения</span><span class="sxs-lookup"><span data-stu-id="b459c-103">Implementing a Discovery Proxy</span></span>

<span data-ttu-id="b459c-104">В данном разделе приводятся инструкции по реализации прокси-сервера обнаружения.</span><span class="sxs-lookup"><span data-stu-id="b459c-104">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="b459c-105">Прокси-сервер обнаружения - это автономная служба, содержащая репозиторий служб.</span><span class="sxs-lookup"><span data-stu-id="b459c-105">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="b459c-106">Клиенты могут выполнять запросы к прокси-серверу обнаружения, чтобы найти обнаружимые службы, доступные серверу.</span><span class="sxs-lookup"><span data-stu-id="b459c-106">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="b459c-107">Метод заполнения прокси-сервера службами определяется разработчиком.</span><span class="sxs-lookup"><span data-stu-id="b459c-107">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="b459c-108">Например, прокси-сервер обнаружения может подключаться к существующему репозиторию служб и сделать эту информацию обнаружимой, администратор может при помощи API управления добавить обнаружимые службы к прокси-серверу, а прокси-сервер обнаружения может при помощи функции объявлений обновить свой внутренний кэш.</span><span class="sxs-lookup"><span data-stu-id="b459c-108">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="b459c-109">Реализация WCF обеспечивает базовые классы, которые позволят легко создавать прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="b459c-109">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="b459c-110">Эти API-интерфейсы можно использовать для создания прокси-сервера обнаружения поверх существующего репозитория.</span><span class="sxs-lookup"><span data-stu-id="b459c-110">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="b459c-111">Используемый здесь прокси-сервер обнаружения похож на любую другую службу WCF в том, что можно сделать прокси-сервер обнаруживаемым и позволить клиентам находить его конечные точки.</span><span class="sxs-lookup"><span data-stu-id="b459c-111">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b459c-112">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="b459c-112">In This Section</span></span>  

 [<span data-ttu-id="b459c-113">Практическое руководство. Как реализовать прокси-сервер обнаружения</span><span class="sxs-lookup"><span data-stu-id="b459c-113">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="b459c-114">Реализация прокси-сервера обнаружения.</span><span class="sxs-lookup"><span data-stu-id="b459c-114">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="b459c-115">Практическое руководство. Как реализовать обнаружимую службу, которая регистрируется в прокси-сервере обнаружения</span><span class="sxs-lookup"><span data-stu-id="b459c-115">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="b459c-116">Описывает, как реализовать обнаруживаемую службу WCF, которая регистрируется в прокси-сервере обнаружения.</span><span class="sxs-lookup"><span data-stu-id="b459c-116">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="b459c-117">Практическое руководство. Как реализовать клиентское приложение, которое для поиска служб использует прокси-сервер обнаружения</span><span class="sxs-lookup"><span data-stu-id="b459c-117">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="b459c-118">Описание реализации клиентского приложения WCF, использующего прокси-сервер обнаружения для поиска службы.</span><span class="sxs-lookup"><span data-stu-id="b459c-118">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="b459c-119">Практическое руководство. Как проверить прокси-сервер обнаружения</span><span class="sxs-lookup"><span data-stu-id="b459c-119">How to: Test the Discovery Proxy</span></span>](how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="b459c-120">Описывает, как проверить код, приведенный в предыдущих трех разделах.</span><span class="sxs-lookup"><span data-stu-id="b459c-120">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b459c-121">См. также</span><span class="sxs-lookup"><span data-stu-id="b459c-121">See also</span></span>

- [<span data-ttu-id="b459c-122">Обнаружение WCF</span><span class="sxs-lookup"><span data-stu-id="b459c-122">WCF Discovery</span></span>](wcf-discovery.md)
- [<span data-ttu-id="b459c-123">Практическое руководство. Как программно добавить возможность обнаружения к службе и клиенту WCF</span><span class="sxs-lookup"><span data-stu-id="b459c-123">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
