---
title: Доступ к службе из веб-браузера (краткое руководство по службе данных WCF)
description: Узнайте, как запустить службы данных WCF в Visual Studio и отключить чтение веб-канала в браузере. Получите документ определения службы и ресурсы службы данных Access.
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: 27b599b6bf28b2ee0810564a3fb73b14274467ff
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805549"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="80632-104">Доступ к службе из веб-браузера (краткое руководство по службе данных WCF)</span><span class="sxs-lookup"><span data-stu-id="80632-104">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="80632-105">Это вторая задача краткого руководства по службы данных WCF.</span><span class="sxs-lookup"><span data-stu-id="80632-105">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="80632-106">В этой задаче вы запускаете службы данных WCF из Visual Studio и при необходимости отключаете чтение веб-канала в браузере.</span><span class="sxs-lookup"><span data-stu-id="80632-106">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="80632-107">Затем вы получаете документ определения службы и доступ к ресурсам службы данных, отправляя запросы HTTP GET через веб-браузер к предоставленным ресурсам.</span><span class="sxs-lookup"><span data-stu-id="80632-107">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="80632-108">По умолчанию Visual Studio автоматически приписывает для URI на компьютере номер порта `localhost`.</span><span class="sxs-lookup"><span data-stu-id="80632-108">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="80632-109">В данной задаче в примерах URI используется порт номер `12345`.</span><span class="sxs-lookup"><span data-stu-id="80632-109">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="80632-110">Дополнительные сведения о том, как задать конкретный номер порта в проекте Visual Studio, см. в разделе [Создание службы данных](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="80632-110">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="80632-111">Запрос сервисного документа по умолчанию с помощью Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="80632-111">To request the default service document by using Internet Explorer</span></span>

1. <span data-ttu-id="80632-112">В Internet Explorer в меню **Сервис** выберите **Свойства обозревателя**, перейдите на вкладку **содержимое** , щелкните **Параметры** и снимите флажок **включить просмотр веб-канала**.</span><span class="sxs-lookup"><span data-stu-id="80632-112">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="80632-113">При этом чтение каналов будет отключено.</span><span class="sxs-lookup"><span data-stu-id="80632-113">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="80632-114">Если не выключить эту функцию, то веб-браузер будет рассматривать документ в формате AtomPub в качестве канала XML, а не отображать необработанные данные XML.</span><span class="sxs-lookup"><span data-stu-id="80632-114">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="80632-115">Если браузер не может отобразить канал в виде необработанных XML-данных, его все равно можно просмотреть в виде исходного кода страницы.</span><span class="sxs-lookup"><span data-stu-id="80632-115">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2. <span data-ttu-id="80632-116">В Visual Studio нажмите клавишу **F5** , чтобы начать отладку приложения.</span><span class="sxs-lookup"><span data-stu-id="80632-116">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3. <span data-ttu-id="80632-117">Откройте веб-браузер на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="80632-117">Open a Web browser on the local computer.</span></span> <span data-ttu-id="80632-118">В адресной строке введите следующий URI:</span><span class="sxs-lookup"><span data-stu-id="80632-118">In the address bar, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="80632-119">При этом будет возвращен сервисный документ по умолчанию, в котором содержится список наборов сущностей, предоставляемых службой данных.</span><span class="sxs-lookup"><span data-stu-id="80632-119">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="80632-120">Доступ к ресурсам набора сущностей из веб-браузера</span><span class="sxs-lookup"><span data-stu-id="80632-120">To access entity set resources from a Web browser</span></span>

1. <span data-ttu-id="80632-121">В адресной строке веб-браузера введите следующий URI:</span><span class="sxs-lookup"><span data-stu-id="80632-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="80632-122">При этом будет возвращен набор всех клиентов из образца базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="80632-122">This returns a set of all customers in the Northwind sample database.</span></span>

2. <span data-ttu-id="80632-123">В адресной строке веб-браузера введите следующий URI:</span><span class="sxs-lookup"><span data-stu-id="80632-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="80632-124">При этом возвращается экземпляр сущности для конкретного клиента `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="80632-124">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3. <span data-ttu-id="80632-125">В адресной строке веб-браузера введите следующий URI:</span><span class="sxs-lookup"><span data-stu-id="80632-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="80632-126">При этом произойдет переход по связи между клиентами и заказами для возвращения набора всех заказов для конкретного клиента `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="80632-126">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4. <span data-ttu-id="80632-127">В адресной строке веб-браузера введите следующий URI:</span><span class="sxs-lookup"><span data-stu-id="80632-127">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="80632-128">При этом будут отфильтрованы заказы, принадлежащие конкретному клиенту `ALFKI`, в результате чего будет возвращен только конкретный заказ на основе переданного значения `OrderID`.</span><span class="sxs-lookup"><span data-stu-id="80632-128">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="80632-129">Next Steps</span><span class="sxs-lookup"><span data-stu-id="80632-129">Next Steps</span></span>

<span data-ttu-id="80632-130">Вы успешно получили доступ к службы данных WCF из веб-браузера, где браузер выдает HTTP-запросы GET к указанным ресурсам.</span><span class="sxs-lookup"><span data-stu-id="80632-130">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="80632-131">Веб-браузер предоставляет простой способ проведения экспериментов с синтаксисом адресации запросов и просмотра результатов.</span><span class="sxs-lookup"><span data-stu-id="80632-131">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="80632-132">Однако к производственной службе данных таким способом обычно не обращаются.</span><span class="sxs-lookup"><span data-stu-id="80632-132">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="80632-133">Как правило, взаимодействие приложений со службой данных осуществляется через программный код или языки сценариев.</span><span class="sxs-lookup"><span data-stu-id="80632-133">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="80632-134">Далее мы создадим клиентское приложение, которое использует клиентские библиотеки для обращения к ресурсам службы данных, как если бы они являлись объектами CLR.</span><span class="sxs-lookup"><span data-stu-id="80632-134">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="80632-135">Создание клиентского приложения .NET Framework</span><span class="sxs-lookup"><span data-stu-id="80632-135">Creating the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="80632-136">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="80632-136">See also</span></span>

- [<span data-ttu-id="80632-137">Доступ к ресурсам служб данных</span><span class="sxs-lookup"><span data-stu-id="80632-137">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
