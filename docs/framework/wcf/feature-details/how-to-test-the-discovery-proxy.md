---
description: Дополнительные сведения см. в статье тестирование прокси-сервера обнаружения.
title: Практическое руководство. Как проверить прокси-сервер обнаружения
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 32360fd1f3724f2a557182ce2e11d346ba5c959d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643115"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="a521e-103">Практическое руководство. Как проверить прокси-сервер обнаружения</span><span class="sxs-lookup"><span data-stu-id="a521e-103">How to: Test the Discovery Proxy</span></span>

<span data-ttu-id="a521e-104">Это последний из четырех разделов, в которых демонстрируется реализация прокси-сервера обнаружения.</span><span class="sxs-lookup"><span data-stu-id="a521e-104">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="a521e-105">В предыдущем разделе [как реализовать клиентское приложение, использующее прокси-сервер обнаружения для поиска службы](client-app-discovery-proxy-to-find-a-service.md), вы реализовали клиентское приложение WCF, которое использует прокси-сервер обнаружения для поиска службы и затем вызывает службу.</span><span class="sxs-lookup"><span data-stu-id="a521e-105">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="a521e-106">В данном разделе показано, как проверить работу прокси-сервера обнаружения, службы и клиентского приложения.</span><span class="sxs-lookup"><span data-stu-id="a521e-106">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="a521e-107">Запуск прокси-сервера обнаружения</span><span class="sxs-lookup"><span data-stu-id="a521e-107">Run the Discovery Proxy</span></span>  
  
1. <span data-ttu-id="a521e-108">Откройте командную строку от имени учетной записи администратора.</span><span class="sxs-lookup"><span data-stu-id="a521e-108">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="a521e-109">Может появиться диалоговое окно с сообщением «Брандмауэр Windows заблокировал некоторые из функций этой программы».</span><span class="sxs-lookup"><span data-stu-id="a521e-109">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="a521e-110">Если вы видите это сообщение, нажмите кнопку **разблокировать** .</span><span class="sxs-lookup"><span data-stu-id="a521e-110">If you see this message, click the **Unblock** button.</span></span>  
  
3. <span data-ttu-id="a521e-111">Запустите из командной строки прокси-сервер обнаружения DiscoveryProxy.exe.</span><span class="sxs-lookup"><span data-stu-id="a521e-111">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4. <span data-ttu-id="a521e-112">Приложение должно вывести на экран сообщение: `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="a521e-112">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="a521e-113">Запуск обнаруживаемой службы</span><span class="sxs-lookup"><span data-stu-id="a521e-113">Run the Discoverable Service</span></span>  
  
1. <span data-ttu-id="a521e-114">Откройте командную строку от имени учетной записи администратора.</span><span class="sxs-lookup"><span data-stu-id="a521e-114">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="a521e-115">Из командной строки запустите обнаруживаемую службу Service.exe.</span><span class="sxs-lookup"><span data-stu-id="a521e-115">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3. <span data-ttu-id="a521e-116">В DiscoveryProxy.exe должен отображаться следующий текст: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="a521e-116">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="a521e-117">Запуск клиентского приложения</span><span class="sxs-lookup"><span data-stu-id="a521e-117">Run the Client Application</span></span>  
  
1. <span data-ttu-id="a521e-118">Откройте командную строку.</span><span class="sxs-lookup"><span data-stu-id="a521e-118">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="a521e-119">Из командной строки запустите приложение client.exe.</span><span class="sxs-lookup"><span data-stu-id="a521e-119">Within the command prompt, run the client.exe application.</span></span>  
  
3. <span data-ttu-id="a521e-120">Через несколько секунд клиентское приложение выведет на экран сообщение: «Connecting to [Service-Endpoint]».</span><span class="sxs-lookup"><span data-stu-id="a521e-120">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4. <span data-ttu-id="a521e-121">Программа service.exe должна затем вывести на экран сообщение: «Greeting request received, I will respond».</span><span class="sxs-lookup"><span data-stu-id="a521e-121">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5. <span data-ttu-id="a521e-122">Приложение client.exe должно затем вывести на экран сообщение: «Hello Client!»</span><span class="sxs-lookup"><span data-stu-id="a521e-122">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="a521e-123">Завершение работы приложений</span><span class="sxs-lookup"><span data-stu-id="a521e-123">Shut Down the Applications</span></span>  
  
1. <span data-ttu-id="a521e-124">Закройте клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="a521e-124">Shut down the client application.</span></span>  
  
2. <span data-ttu-id="a521e-125">Завершите работу службы.</span><span class="sxs-lookup"><span data-stu-id="a521e-125">Shut down the service.</span></span> <span data-ttu-id="a521e-126">Прокси-сервер обнаружения выведет на экран сообщение: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="a521e-126">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3. <span data-ttu-id="a521e-127">Завершите работу прокси-сервера обнаружения.</span><span class="sxs-lookup"><span data-stu-id="a521e-127">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a521e-128">См. также</span><span class="sxs-lookup"><span data-stu-id="a521e-128">See also</span></span>

- [<span data-ttu-id="a521e-129">Общие сведения об обнаружении WCF</span><span class="sxs-lookup"><span data-stu-id="a521e-129">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="a521e-130">Практическое руководство. Как реализовать прокси-сервер обнаружения</span><span class="sxs-lookup"><span data-stu-id="a521e-130">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="a521e-131">Практическое руководство. Как реализовать обнаружимую службу, которая регистрируется в прокси-сервере обнаружения</span><span class="sxs-lookup"><span data-stu-id="a521e-131">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="a521e-132">Практическое руководство. Как реализовать клиентское приложение, которое для поиска служб использует прокси-сервер обнаружения</span><span class="sxs-lookup"><span data-stu-id="a521e-132">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
