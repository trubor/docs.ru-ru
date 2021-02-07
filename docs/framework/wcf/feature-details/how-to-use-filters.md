---
description: Дополнительные сведения см. в статье как использовать фильтры.
title: 'Как выполнить: Использование фильтров'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 0218685cae6fe8dc4c1e36e51075d58b041ae7fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734325"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="c9b09-103">Как выполнить: Использование фильтров</span><span class="sxs-lookup"><span data-stu-id="c9b09-103">How To: Use Filters</span></span>

<span data-ttu-id="c9b09-104">В этом разделе описаны основные шаги по созданию конфигурации маршрутизации с несколькими фильтрами.</span><span class="sxs-lookup"><span data-stu-id="c9b09-104">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="c9b09-105">В этом примере сообщения направляются в две реализации службы калькулятора: regularCalc и roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="c9b09-105">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="c9b09-106">Обе реализации поддерживают одинаковые операции, однако одна служба, прежде чем вернуть результаты вычислений, округляет их до ближайшего целого числа.</span><span class="sxs-lookup"><span data-stu-id="c9b09-106">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="c9b09-107">Клиентское приложение должно иметь возможность указывать, нужно ли использовать версию службы, выполняющую округление. Если предпочитаемая служба не указана, сообщения равномерно распределяются между двумя службами.</span><span class="sxs-lookup"><span data-stu-id="c9b09-107">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="c9b09-108">Операции, предоставляемые обеими службами:</span><span class="sxs-lookup"><span data-stu-id="c9b09-108">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="c9b09-109">Add</span><span class="sxs-lookup"><span data-stu-id="c9b09-109">Add</span></span>  
  
- <span data-ttu-id="c9b09-110">Subtract</span><span class="sxs-lookup"><span data-stu-id="c9b09-110">Subtract</span></span>  
  
- <span data-ttu-id="c9b09-111">Multiply</span><span class="sxs-lookup"><span data-stu-id="c9b09-111">Multiply</span></span>  
  
- <span data-ttu-id="c9b09-112">Divide</span><span class="sxs-lookup"><span data-stu-id="c9b09-112">Divide</span></span>  
  
 <span data-ttu-id="c9b09-113">Поскольку в обеих службах применяются одни и те же операции, нельзя использовать фильтр действий, так как указанное в сообщении действие не будет уникальным.</span><span class="sxs-lookup"><span data-stu-id="c9b09-113">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="c9b09-114">Вместо этого придется проделать дополнительную работу, чтобы гарантированно направлять сообщения в соответствующую конечную точку.</span><span class="sxs-lookup"><span data-stu-id="c9b09-114">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="c9b09-115">Определение уникальных данных</span><span class="sxs-lookup"><span data-stu-id="c9b09-115">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="c9b09-116">Поскольку обе реализации служб обрабатывают одни и те же операции и, в сущности, отличаются только возвращаемыми данных, базовые данные, содержащиеся в сообщениях, отправленных клиентскими приложениями, не являются достаточно уникальными, чтобы можно было определить способ маршрутизации запроса.</span><span class="sxs-lookup"><span data-stu-id="c9b09-116">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="c9b09-117">Но если клиентское приложение добавляет в сообщение уникальное значение заголовка, можно использовать это значение для маршрутизации сообщения.</span><span class="sxs-lookup"><span data-stu-id="c9b09-117">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="c9b09-118">Например, если клиентскому приложению нужно, чтобы сообщение обрабатывалось калькулятором с округлением, в него необходимо добавить пользовательский заголовок с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="c9b09-118">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="c9b09-119">Теперь можно применить фильтр XPath, чтобы выявлять сообщения с этим заголовком и направлять их в службу roundCalc.</span><span class="sxs-lookup"><span data-stu-id="c9b09-119">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="c9b09-120">Кроме того, в службе маршрутизации имеются две виртуальные конечные точки службы, которые могут использоваться с фильтрами EndpointName, EndpointAddress или PrefixEndpointAddress для уникальной маршрутизации входящих сообщений в определенную реализацию калькулятора, в зависимости от того, к какой конечной точке клиентское приложение направляет запрос.</span><span class="sxs-lookup"><span data-stu-id="c9b09-120">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="c9b09-121">Определение конечных точек</span><span class="sxs-lookup"><span data-stu-id="c9b09-121">Define Endpoints</span></span>  
  
1. <span data-ttu-id="c9b09-122">При определении конечных точек, используемых службой маршрутизации, необходимо сначала определить форму канала, используемого клиентами и службами.</span><span class="sxs-lookup"><span data-stu-id="c9b09-122">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="c9b09-123">В этом сценарии обе целевые службы используют шаблон «запрос-ответ», поэтому применяется <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span><span class="sxs-lookup"><span data-stu-id="c9b09-123">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="c9b09-124">В следующем примере определяются конечные точки службы, предоставляемые службой маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="c9b09-124">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     <span data-ttu-id="c9b09-125">В этой конфигурации службы маршрутизации предоставляют три отдельные конечные точки.</span><span class="sxs-lookup"><span data-stu-id="c9b09-125">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="c9b09-126">В зависимости от выборов, сделанных в процессе работы, клиентское приложение отправляет сообщения по одному из этих адресов.</span><span class="sxs-lookup"><span data-stu-id="c9b09-126">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="c9b09-127">Сообщения, поступающие на одну из виртуальных конечных точек службы ("округление/калькулятор" или "обычный/калькулятор"), перенаправляются в соответствующую реализацию калькулятора.</span><span class="sxs-lookup"><span data-stu-id="c9b09-127">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="c9b09-128">Если клиентское приложение не направляет запрос в определенную конечную точку, сообщение отправляется в общую конечную точку.</span><span class="sxs-lookup"><span data-stu-id="c9b09-128">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="c9b09-129">Независимо от того, какая конечная точка выбрана, клиентское приложение может также включить пользовательский заголовок, указывающий, что сообщение должно быть перенаправлено в реализацию калькулятора с округлением.</span><span class="sxs-lookup"><span data-stu-id="c9b09-129">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="c9b09-130">В следующем примере определяются клиентские (целевые) конечные точки, в которые направляет сообщения служба маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="c9b09-130">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     <span data-ttu-id="c9b09-131">Эти конечные точки используются в таблице фильтров для указания целевой конечной точки, в которую отправляется сообщение, если оно соответствует критериям определенного фильтра.</span><span class="sxs-lookup"><span data-stu-id="c9b09-131">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="c9b09-132">Определение фильтров</span><span class="sxs-lookup"><span data-stu-id="c9b09-132">Define Filters</span></span>  
  
1. <span data-ttu-id="c9b09-133">Чтобы направить сообщения на основе пользовательского заголовка "Раундингкалкулатор", который клиентское приложение добавляет в сообщение, определите фильтр, использующий запрос XPath для проверки наличия этого заголовка.</span><span class="sxs-lookup"><span data-stu-id="c9b09-133">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="c9b09-134">Поскольку этот заголовок определяется с помощью пользовательского пространства имен, также добавьте запись пространства имен, определяющую префикс пользовательского пространства имен "Custom", который используется в запросе XPath.</span><span class="sxs-lookup"><span data-stu-id="c9b09-134">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="c9b09-135">В следующем примере определяются необходимый раздел маршрутизации, таблица пространства имен и фильтр XPath.</span><span class="sxs-lookup"><span data-stu-id="c9b09-135">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     <span data-ttu-id="c9b09-136">Этот **MessageFilter** ищет в сообщении заголовок раундингкалкулатор, который содержит значение "Round".</span><span class="sxs-lookup"><span data-stu-id="c9b09-136">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="c9b09-137">Этот заголовок задается клиентом и указывает, что сообщение должно быть направлено в службу roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="c9b09-137">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c9b09-138">Префикс пространства имен s12 определяется по умолчанию в таблице пространства имен и представляет пространство имен `http://www.w3.org/2003/05/soap-envelope` .</span><span class="sxs-lookup"><span data-stu-id="c9b09-138">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="c9b09-139">Также необходимо определить фильтры для поиска сообщений, полученных в двух виртуальных конечных точках.</span><span class="sxs-lookup"><span data-stu-id="c9b09-139">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="c9b09-140">Первая виртуальная конечная точка — это конечная точка обычного или калькулятора.</span><span class="sxs-lookup"><span data-stu-id="c9b09-140">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="c9b09-141">Клиент может направлять запросы в эту конечную точку, чтобы указать, что сообщение должно быть направлено в службу regularCalc.</span><span class="sxs-lookup"><span data-stu-id="c9b09-141">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="c9b09-142">В следующей конфигурации определен фильтр, использующий <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> для определения, было ли сообщение получено через конечную точку с именем, указанным в параметре filterData.</span><span class="sxs-lookup"><span data-stu-id="c9b09-142">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="c9b09-143">При получении сообщения конечной точкой службы с именем "Калкулаторендпоинт" Этот фильтр принимает значение `true` .</span><span class="sxs-lookup"><span data-stu-id="c9b09-143">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="c9b09-144">Затем определите фильтр для поиска сообщений, отправленных на адрес roundingEndpoint.</span><span class="sxs-lookup"><span data-stu-id="c9b09-144">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="c9b09-145">Клиент может направлять запросы в эту конечную точку, чтобы указать, что сообщение должно быть направлено в службу roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="c9b09-145">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="c9b09-146">Следующая конфигурация определяет фильтр, который использует, <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> чтобы определить, поступило ли сообщение в конечную точку "округление/калькулятор".</span><span class="sxs-lookup"><span data-stu-id="c9b09-146">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="c9b09-147">Если сообщение получено по адресу, который начинается с, `http://localhost/routingservice/router/rounding/` то фильтр принимает **значение true**.</span><span class="sxs-lookup"><span data-stu-id="c9b09-147">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="c9b09-148">Поскольку базовый адрес, используемый этой конфигурацией, —, `http://localhost/routingservice/router` а адрес, указанный для раундинжендпоинт, — "округление/калькулятор", полный адрес, используемый для связи с этой конечной точкой `http://localhost/routingservice/router/rounding/calculator` , соответствует этому фильтру.</span><span class="sxs-lookup"><span data-stu-id="c9b09-148">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c9b09-149">Фильтр PrefixEndpointAddress не вычисляет имя узла при проведении сопоставления, поскольку одному узлу может соответствовать несколько имен узлов, все из которых могут быть допустимыми ссылками на узел из клиентского приложения.</span><span class="sxs-lookup"><span data-stu-id="c9b09-149">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="c9b09-150">Например, все следующие ссылки относятся к одному и тому же узлу:</span><span class="sxs-lookup"><span data-stu-id="c9b09-150">For example, all of the following may refer to the same host:</span></span>  
    >
    > - <span data-ttu-id="c9b09-151">localhost</span><span class="sxs-lookup"><span data-stu-id="c9b09-151">localhost</span></span>  
    > - <span data-ttu-id="c9b09-152">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="c9b09-152">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="c9b09-153">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="c9b09-153">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="c9b09-154">Конечный фильтр должен поддерживать маршрутизацию сообщений, прибывающих в общую конечную точку без пользовательского заголовка.</span><span class="sxs-lookup"><span data-stu-id="c9b09-154">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="c9b09-155">В этом сценарии сообщения должны отправляться либо в службу regularCalc, либо roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="c9b09-155">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="c9b09-156">Для поддержки маршрутизации этих сообщений с циклическим перебором используйте настраиваемый фильтр, позволяющий одному экземпляру фильтра соответствовать каждому обработанному сообщению.</span><span class="sxs-lookup"><span data-stu-id="c9b09-156">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="c9b09-157">В следующем примере определено два экземпляра фильтра RoundRobinMessageFilter, сгруппированных вместе, что означает, что они должны чередоваться.</span><span class="sxs-lookup"><span data-stu-id="c9b09-157">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     <span data-ttu-id="c9b09-158">Во время выполнения в этом типе фильтра чередуются все определенные экземпляры типа, настроенные в виде одной группы в одной коллекции.</span><span class="sxs-lookup"><span data-stu-id="c9b09-158">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="c9b09-159">Это приводит к тому, что сообщения, обрабатываемые этим настраиваемым фильтром, переходят между возвратами в `true` `RoundRobinFilter1` и `RoundRobinFilter2` .</span><span class="sxs-lookup"><span data-stu-id="c9b09-159">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="c9b09-160">Определение таблиц фильтров</span><span class="sxs-lookup"><span data-stu-id="c9b09-160">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="c9b09-161">Чтобы связать фильтры с определенными клиентскими конечными точками, нужно поместить их в таблицу фильтров.</span><span class="sxs-lookup"><span data-stu-id="c9b09-161">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="c9b09-162">В этом примере сценария также используются параметры приоритета фильтров, позволяющие указать очередность обработки фильтров.</span><span class="sxs-lookup"><span data-stu-id="c9b09-162">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="c9b09-163">Если приоритет фильтров не задан, все фильтры вычисляются одновременно.</span><span class="sxs-lookup"><span data-stu-id="c9b09-163">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c9b09-164">Хотя заданный приоритет фильтров позволяет управлять очередностью обработки фильтров, он может неблагоприятно сказаться на производительности службы маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="c9b09-164">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="c9b09-165">Если возможно, логику фильтрации следует строить так, чтобы задавать приоритет фильтров не требовалось.</span><span class="sxs-lookup"><span data-stu-id="c9b09-165">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="c9b09-166">Следующий пример определяет таблицу фильтров и добавляет «Кспасфилтер», определенный ранее, в таблицу с приоритетом 2.</span><span class="sxs-lookup"><span data-stu-id="c9b09-166">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="c9b09-167">Эта запись также указывает, что если объект `XPathFilter` соответствует сообщению, сообщение будет направляться в `roundingCalcEndpoint` .</span><span class="sxs-lookup"><span data-stu-id="c9b09-167">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          </filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="c9b09-168">Если приоритет фильтров задан, фильтр с наивысшим приоритетом выполняется первым.</span><span class="sxs-lookup"><span data-stu-id="c9b09-168">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="c9b09-169">Если удовлетворены критерии одного или нескольких фильтров с одним уровнем приоритета, фильтры с более низкими уровнями приоритета обрабатываться не будут.</span><span class="sxs-lookup"><span data-stu-id="c9b09-169">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="c9b09-170">В этом сценарии 2 это самый высокий указанный приоритет, на этом уровне имеется единственная запись фильтра.</span><span class="sxs-lookup"><span data-stu-id="c9b09-170">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="c9b09-171">Записи фильтров были определены, чтобы путем проверки имени конечной точки или префикса адреса выяснить, получено ли сообщение в определенной конечной точке.</span><span class="sxs-lookup"><span data-stu-id="c9b09-171">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="c9b09-172">В следующих записях обе записи фильтров добавляются в таблицу фильтров и связываются с целевыми конечными точками, в которые будут направляться сообщения.</span><span class="sxs-lookup"><span data-stu-id="c9b09-172">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="c9b09-173">Для этих фильтров задан приоритет 1, чтобы указать, что они должны выполняться, только если сообщение не соответствует предыдущему фильтру XPath.</span><span class="sxs-lookup"><span data-stu-id="c9b09-173">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="c9b09-174">Поскольку для этих фильтров задан приоритет 1, они будут вычисляться, только если сообщение не соответствует фильтру с уровнем приоритета 2.</span><span class="sxs-lookup"><span data-stu-id="c9b09-174">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="c9b09-175">Также, поскольку оба фильтра имеют одинаковый приоритет, они будут вычисляться одновременно.</span><span class="sxs-lookup"><span data-stu-id="c9b09-175">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="c9b09-176">Поскольку эти два фильтра являются взаимоисключающими, сообщение может соответствовать только одному из них.</span><span class="sxs-lookup"><span data-stu-id="c9b09-176">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="c9b09-177">Если сообщение не соответствует ни одному из предыдущих фильтров, это значит, что оно было получено через конечную точку общей службы и не содержит заголовка, указывающего, куда сообщение должно быть направлено.</span><span class="sxs-lookup"><span data-stu-id="c9b09-177">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="c9b09-178">Эти сообщения должны обрабатываться пользовательским фильтром, который распределяет нагрузку между двумя службами калькуляторов.</span><span class="sxs-lookup"><span data-stu-id="c9b09-178">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="c9b09-179">В следующем примере показано, как добавлять записи фильтров в таблицу фильтров. Каждый фильтр связывается с одной из двух целевых конечных точек.</span><span class="sxs-lookup"><span data-stu-id="c9b09-179">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="c9b09-180">Поскольку для этих записей задан приоритет 0, они будут вычисляться, только если сообщение не соответствует ни одному фильтру с более высоким уровнем приоритета.</span><span class="sxs-lookup"><span data-stu-id="c9b09-180">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="c9b09-181">Также, поскольку оба фильтра имеют одинаковый приоритет, они будут вычисляться одновременно.</span><span class="sxs-lookup"><span data-stu-id="c9b09-181">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="c9b09-182">Как упоминалось ранее, пользовательский фильтр, используемый этими определениями фильтров, возвращает значение `true` для каждого второго полученного сообщения.</span><span class="sxs-lookup"><span data-stu-id="c9b09-182">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="c9b09-183">Поскольку только два фильтра с одинаковыми параметрами группы определены с использованием этого фильтра, служба маршрутизации поочередно отправляет сообщения в конечные точки regularCalcEndpoint и RoundingCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="c9b09-183">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="c9b09-184">Для оценки сообщений с помощью фильтров таблица фильтров должна быть связана с конечными точками службы, которые будут получать сообщения.</span><span class="sxs-lookup"><span data-stu-id="c9b09-184">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="c9b09-185">В приведенном ниже примере показано, как связать таблицу маршрутизации с конечными точками службы с помощью поведения маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="c9b09-185">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="c9b09-186">Пример</span><span class="sxs-lookup"><span data-stu-id="c9b09-186">Example</span></span>  

 <span data-ttu-id="c9b09-187">Далее приведен полный листинг файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c9b09-187">The following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9b09-188">См. также</span><span class="sxs-lookup"><span data-stu-id="c9b09-188">See also</span></span>

- [<span data-ttu-id="c9b09-189">Службы маршрутизации</span><span class="sxs-lookup"><span data-stu-id="c9b09-189">Routing Services</span></span>](../samples/routing-services.md)
