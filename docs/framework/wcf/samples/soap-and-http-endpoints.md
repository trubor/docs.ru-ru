---
description: 'Дополнительные сведения: конечные точки SOAP и HTTP'
title: Конечные точки SOAP и HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: e07f2d33656b6f697d25a684e49e60d748badc2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703540"
---
# <a name="soap-and-http-endpoints"></a><span data-ttu-id="2b35b-103">Конечные точки SOAP и HTTP</span><span class="sxs-lookup"><span data-stu-id="2b35b-103">SOAP and HTTP Endpoints</span></span>

<span data-ttu-id="2b35b-104">В этом образце показано, как реализовать службу на основе RPC и предоставить ее в формате SOAP и формате "Plain Old XML" (POX) с помощью модели веб-программирования WCF.</span><span class="sxs-lookup"><span data-stu-id="2b35b-104">This sample demonstrates how to implement an RPC-based service and expose it in the SOAP format and the "Plain Old XML" (POX) format using the WCF Web Programming model.</span></span> <span data-ttu-id="2b35b-105">Дополнительные сведения о привязке HTTP для службы см. в разделе образец [основной службы HTTP](basic-http-service.md) .</span><span class="sxs-lookup"><span data-stu-id="2b35b-105">See the [Basic HTTP Service](basic-http-service.md) sample for more details about the HTTP binding for the service.</span></span> <span data-ttu-id="2b35b-106">В данном образце акцент сделан на особенностях предоставления одной и той же службы через протокол SOAP и HTTP с использованием разных привязок.</span><span class="sxs-lookup"><span data-stu-id="2b35b-106">This sample focuses on the details that pertain to exposing the same service over SOAP and HTTP using different bindings.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="2b35b-107">Что демонстрирует</span><span class="sxs-lookup"><span data-stu-id="2b35b-107">Demonstrates</span></span>  

 <span data-ttu-id="2b35b-108">Предоставление доступа к службе RPC по протоколу SOAP и HTTP с помощью WCF.</span><span class="sxs-lookup"><span data-stu-id="2b35b-108">Exposing an RPC service over SOAP and HTTP using WCF.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="2b35b-109">Разговор</span><span class="sxs-lookup"><span data-stu-id="2b35b-109">Discussion</span></span>  

 <span data-ttu-id="2b35b-110">Этот пример состоит из двух компонентов: проекта веб-приложения (службы), который содержит службу WCF, и консольного приложения (клиента), которое вызывает операции службы с помощью привязок SOAP и HTTP.</span><span class="sxs-lookup"><span data-stu-id="2b35b-110">This sample consists of two components: a Web Application project (Service) that contains a WCF service and a console application (Client) that invokes service operations using SOAP and HTTP bindings.</span></span>  
  
 <span data-ttu-id="2b35b-111">Служба WCF предоставляет 2 операции — `GetData` и `PutData` — это строка, передаваемая в качестве входных данных.</span><span class="sxs-lookup"><span data-stu-id="2b35b-111">The WCF service exposes 2 operations –`GetData` and `PutData` – that echo the string that was passed as input.</span></span> <span data-ttu-id="2b35b-112">Операции службы помечены атрибутами <xref:System.ServiceModel.Web.WebGetAttribute> и <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2b35b-112">The service operations are annotated with <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="2b35b-113">Эти атрибуты управляют HTTP-проекцией операций.</span><span class="sxs-lookup"><span data-stu-id="2b35b-113">These attributes control the HTTP projection of these operations.</span></span> <span data-ttu-id="2b35b-114">Кроме того, они помечены атрибутом <xref:System.ServiceModel.OperationContractAttribute>, который позволяет предоставлять их через привязки протокола SOAP.</span><span class="sxs-lookup"><span data-stu-id="2b35b-114">In addition, they are annotated with <xref:System.ServiceModel.OperationContractAttribute>, which enables them to be exposed over SOAP bindings.</span></span> <span data-ttu-id="2b35b-115">Метод службы `PutData` вызывает исключение <xref:System.ServiceModel.Web.WebFaultException>, которое отправляется обратно через HTTP с использованием кода состояния HTTP, а через SOAP как ошибка SOAP.</span><span class="sxs-lookup"><span data-stu-id="2b35b-115">The service’s `PutData` method throws a <xref:System.ServiceModel.Web.WebFaultException>, which gets sent back over HTTP using the HTTP status code and gets sent back over SOAP as a SOAP fault.</span></span>  
  
 <span data-ttu-id="2b35b-116">Файл Web.config настраивает службу WCF с 3 конечными точками:</span><span class="sxs-lookup"><span data-stu-id="2b35b-116">The Web.config file configures the WCF service with 3 endpoints:</span></span>  
  
- <span data-ttu-id="2b35b-117">Конечная точка ~/service.svc/mex предоставляет доступ к метаданным службы клиентам на основе SOAP.</span><span class="sxs-lookup"><span data-stu-id="2b35b-117">The ~/service.svc/mex endpoint that exposes the service metadata for access by SOAP-based clients.</span></span>  
  
- <span data-ttu-id="2b35b-118">Конечная точка ~/service.svc/http позволяет клиентам получать доступ к службе с использованием привязки HTTP.</span><span class="sxs-lookup"><span data-stu-id="2b35b-118">The ~/service.svc/http endpoint that enables clients to access the service using the HTTP binding.</span></span>  
  
- <span data-ttu-id="2b35b-119">Конечная точка ~/service.svc/soap позволяет клиентам получать доступ к службе с использованием привязки протокола SOAP.</span><span class="sxs-lookup"><span data-stu-id="2b35b-119">The ~/service.svc/soap endpoint that allows the clients to access the service using the SOAP over HTTP binding.</span></span>  
  
 <span data-ttu-id="2b35b-120">Конечная точка HTTP настроена с помощью <`webHttp`> стандартной конечной точки, `helpEnabled` для которой задано значение `true` .</span><span class="sxs-lookup"><span data-stu-id="2b35b-120">The HTTP endpoint is configured with a <`webHttp`> standard endpoint which has `helpEnabled` set to `true`.</span></span> <span data-ttu-id="2b35b-121">В результате этого служба предоставляет справочную страницу на основе XHTML по адресу ~/service.svc/http/help, которую клиенты на основе HTTP могут использовать для доступа к службе.</span><span class="sxs-lookup"><span data-stu-id="2b35b-121">As a result, the service exposes an XHTML based help page at ~/service.svc/http/help that HTTP-based clients can use to access the service.</span></span>  
  
 <span data-ttu-id="2b35b-122">Клиентский проект демонстрирует доступ к службе с помощью прокси-сервера SOAP (созданного с помощью **Добавление ссылки на службу**) и доступа к службе с помощью <xref:System.Net.WebClient> .</span><span class="sxs-lookup"><span data-stu-id="2b35b-122">The client project demonstrates accessing the service using a SOAP proxy (generated through **Add Service Reference**) and accessing the service using <xref:System.Net.WebClient>.</span></span>  
  
 <span data-ttu-id="2b35b-123">Образец состоит из службы, размещенной на веб-сервере, и консольного приложения.</span><span class="sxs-lookup"><span data-stu-id="2b35b-123">The sample consists of a Web-hosted service and a console application.</span></span> <span data-ttu-id="2b35b-124">Во время выполнения консольного приложения клиент совершает запросы к службе и выводит в окно консоли нужные сведения из ответов.</span><span class="sxs-lookup"><span data-stu-id="2b35b-124">As the console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="2b35b-125">Выполнение образца</span><span class="sxs-lookup"><span data-stu-id="2b35b-125">To run the sample</span></span>  
  
1. <span data-ttu-id="2b35b-126">Откройте решение для образца «SOAP and HTTP Endpoints».</span><span class="sxs-lookup"><span data-stu-id="2b35b-126">Open the solution for the SOAP and HTTP Endpoints Sample.</span></span>  
  
2. <span data-ttu-id="2b35b-127">Чтобы построить решение, нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="2b35b-127">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3. <span data-ttu-id="2b35b-128">Если он еще не открыт, нажмите клавиши CTRL + W, S, чтобы открыть окно **Обозреватель решений** .</span><span class="sxs-lookup"><span data-stu-id="2b35b-128">If it is not already open, press CTRL+W, S to open the **Solution Explorer** window.</span></span>  
  
4. <span data-ttu-id="2b35b-129">В окне **Обозреватель решений** щелкните правой кнопкой мыши проект **службы** и наведите курсор на пункт контекстного меню **Отладка** , чтобы появился контекстное меню **Запуск нового экземпляра** .</span><span class="sxs-lookup"><span data-stu-id="2b35b-129">From the **Solution Explorer** window, right-click the **Service** project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="2b35b-130">Нажмите кнопку **запустить новый экземпляр**.</span><span class="sxs-lookup"><span data-stu-id="2b35b-130">Click **Start New Instance**.</span></span> <span data-ttu-id="2b35b-131">Запускается сервер разработки ASP.NET, на котором размещается служба.</span><span class="sxs-lookup"><span data-stu-id="2b35b-131">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5. <span data-ttu-id="2b35b-132">В обозреватель решенийных окнах щелкните правой кнопкой мыши проект клиента и наведите курсор на пункт контекстного меню **Отладка** , чтобы появился контекстное меню **запустить новый экземпляр** .</span><span class="sxs-lookup"><span data-stu-id="2b35b-132">From the Solution Explorer windows, right-click the Client project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="2b35b-133">Нажмите кнопку **запустить новый экземпляр**.</span><span class="sxs-lookup"><span data-stu-id="2b35b-133">Click **Start New Instance**.</span></span>  
  
6. <span data-ttu-id="2b35b-134">На клиенте открывается окно консоли с URI запущенной службы и URI HTML-страницы справки для запущенной службы.</span><span class="sxs-lookup"><span data-stu-id="2b35b-134">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="2b35b-135">HTML-страницу справки можно просмотреть в любой момент времени, введя URI этой страницы в браузере.</span><span class="sxs-lookup"><span data-stu-id="2b35b-135">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7. <span data-ttu-id="2b35b-136">Во время работы образца клиент записывает состояние текущего действия.</span><span class="sxs-lookup"><span data-stu-id="2b35b-136">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8. <span data-ttu-id="2b35b-137">Чтобы завершить клиентское консольное приложение, нажмите любую клавишу.</span><span class="sxs-lookup"><span data-stu-id="2b35b-137">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="2b35b-138">Чтобы прекратить отладку службы, нажмите клавиши SHIFT+F5.</span><span class="sxs-lookup"><span data-stu-id="2b35b-138">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="2b35b-139">В области уведомлений Windows щелкните правой кнопкой мыши значок сервера ASP.NET Development Server и выберите в контекстном меню пункт " **Закрыть** ".</span><span class="sxs-lookup"><span data-stu-id="2b35b-139">In the Windows Notification Area, right-click the ASP.NET development server icon and select **Stop** from the context menu.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2b35b-140">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="2b35b-140">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2b35b-141">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="2b35b-141">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2b35b-142">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="2b35b-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2b35b-143">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="2b35b-143">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
