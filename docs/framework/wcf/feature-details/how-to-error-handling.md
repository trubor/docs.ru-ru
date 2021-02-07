---
description: 'Дополнительные сведения: как обрабатываются ошибки'
title: 'Как выполнить: Обработка ошибок'
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 1d385070e4cc0d55bc3327114baf4e4ff543171f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704658"
---
# <a name="how-to-error-handling"></a><span data-ttu-id="a19f0-103">Как выполнить: Обработка ошибок</span><span class="sxs-lookup"><span data-stu-id="a19f0-103">How To: Error Handling</span></span>

<span data-ttu-id="a19f0-104">В этом разделе описаны основные шаги по созданию конфигурации маршрутизации с применением обработки ошибок.</span><span class="sxs-lookup"><span data-stu-id="a19f0-104">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="a19f0-105">В данном примере сообщения перенаправляются в целевую конечную точку.</span><span class="sxs-lookup"><span data-stu-id="a19f0-105">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="a19f0-106">Если сообщение не удается доставить из-за сбоя сети или канала связи (<xref:System.ServiceModel.CommunicationException>), оно повторно отправляется в альтернативную конечную точку.</span><span class="sxs-lookup"><span data-stu-id="a19f0-106">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="a19f0-107">Чтобы смоделировать сбой сети, в данном примере в целевую конечную точку включен неверный адрес.</span><span class="sxs-lookup"><span data-stu-id="a19f0-107">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="a19f0-108">Направление сообщений в эту конечную точку будет завершаться ошибкой, поскольку ни одна служба не прослушивает указанный адрес.</span><span class="sxs-lookup"><span data-stu-id="a19f0-108">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>

> [!NOTE]
> <span data-ttu-id="a19f0-109">Хотя пример, приведенный в данном разделе, специально не затрагивает параметры времени ожидания, при обработке ошибок их тоже нужно учитывать.</span><span class="sxs-lookup"><span data-stu-id="a19f0-109">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="a19f0-110">При возникновении ошибок клиент получает ответ с дополнительной задержкой.</span><span class="sxs-lookup"><span data-stu-id="a19f0-110">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="a19f0-111">Это происходит потому, что служба маршрутизации получает ошибку и пытается отправить сообщение в резервную конечную точку.</span><span class="sxs-lookup"><span data-stu-id="a19f0-111">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="a19f0-112">Если значения времени ожидания, связанные с основной и резервной целевыми конечными точками, велики, клиент может столкнуться с длительной задержкой, вызванной тем, что до успешной отправки сообщение может безрезультатно направляться в разные конечные точки из резервного списка.</span><span class="sxs-lookup"><span data-stu-id="a19f0-112">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>
>
> <span data-ttu-id="a19f0-113">Поскольку служба маршрутизации может столкнуться с наибольшей задержкой, равной сумме значений времени ожидания для всех конечных точек, связанных с фильтром, рекомендуется соответствующим образом увеличить значение времени ожидания на клиенте.</span><span class="sxs-lookup"><span data-stu-id="a19f0-113">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>

### <a name="implement-error-handling"></a><span data-ttu-id="a19f0-114">Реализация обработки ошибок</span><span class="sxs-lookup"><span data-stu-id="a19f0-114">Implement Error Handling</span></span>

1. <span data-ttu-id="a19f0-115">Создайте базовую конфигурацию службы маршрутизации, указав конечную точку службы, предоставленную службой.</span><span class="sxs-lookup"><span data-stu-id="a19f0-115">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="a19f0-116">В следующем примере определяется отдельная конечная точка службы, которая используется для получения сообщений.</span><span class="sxs-lookup"><span data-stu-id="a19f0-116">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="a19f0-117">Также будут определены конечные точки клиента, которые используются для отправки сообщений - deadDestination и realDestination.</span><span class="sxs-lookup"><span data-stu-id="a19f0-117">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="a19f0-118">Конечная точка deadDestination содержит адрес, который не ссылается на работающую службу и используется для моделирования сбоя сети при отправке сообщений в эту конечную точку.</span><span class="sxs-lookup"><span data-stu-id="a19f0-118">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>

    ```xml
    <services>
      <service behaviorConfiguration="routingConfiguration"
               name="System.ServiceModel.Routing.RoutingService">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost/routingservice/" />
          </baseAddresses>
        </host>
        <!-- Create the Routing Service endpoint -->
        <endpoint address="router"
                  binding="basicHttpBinding"
                  name="RoutingServiceEndpoint"
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>
    </services>

    <!-- Create the destination endpoints that we want to send to -->
    <client>
      <!-- Create a dummy endpoint that we know will be down -->
      <endpoint name="deadDestination"
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"
                binding="netTcpBinding"
                contract="*" />

      <!-- Now create the real service endpoint -->
      <endpoint name="realDestination"
                address="net.tcp://localhost:8080/servicemodelsamples/service"
                binding="netTcpBinding"
                contract="*" />
    </client>
    ```

2. <span data-ttu-id="a19f0-119">Определите фильтры, используемые для маршрутизации сообщений до конечных точек назначения.</span><span class="sxs-lookup"><span data-stu-id="a19f0-119">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="a19f0-120">В данном примере фильтр MatchAll используется для соответствия всем сообщениям, полученным службой маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="a19f0-120">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. <span data-ttu-id="a19f0-121">Задайте список резервных конечных точек, в которые сообщение отправляется в случае сбоя сети или канала связи при отправке сообщения в основную целевую конечную точку.</span><span class="sxs-lookup"><span data-stu-id="a19f0-121">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="a19f0-122">В следующем примере задается резервный список с одной конечной точкой, хотя он может содержать несколько конечных точек.</span><span class="sxs-lookup"><span data-stu-id="a19f0-122">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>

     <span data-ttu-id="a19f0-123">Если в резервном списке содержится несколько конечных точек, то при возникновении сбоя сети или канала связи служба маршрутизации попытается отправить сообщение в первую из них.</span><span class="sxs-lookup"><span data-stu-id="a19f0-123">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="a19f0-124">Если при отправке сообщения в эту точку возникает сбой сети или канала связи, служба маршрутизации попытается отправить сообщение в следующую конечную точку в списке.</span><span class="sxs-lookup"><span data-stu-id="a19f0-124">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="a19f0-125">Служба продолжает отправлять сообщение в каждую из резервных конечных точек в списке до успешной отправки сообщения, или до получения от всех точек сообщения об ошибке сети или канала связи, или до получения от конечной точки сообщения об ошибке, не связанной с сетью или каналом связи, после отправки сообщения.</span><span class="sxs-lookup"><span data-stu-id="a19f0-125">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. <span data-ttu-id="a19f0-126">Задайте таблицу фильтра, сопоставляющую фильтр с конечной точкой deadDestination и списком резервных конечных точек.</span><span class="sxs-lookup"><span data-stu-id="a19f0-126">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="a19f0-127">Служба маршрутизации сначала попытается отправить сообщение в целевую конечную точку, сопоставленную с фильтром.</span><span class="sxs-lookup"><span data-stu-id="a19f0-127">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="a19f0-128">Поскольку конечная точка deadDestination содержит адрес, не ссылающийся на работающую службу, эта попытка приведет к ошибке сети.</span><span class="sxs-lookup"><span data-stu-id="a19f0-128">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="a19f0-129">Затем служба маршрутизации пытается отправить сообщение в конечную точку, указанную в параметре Баккупендпоинтлист.</span><span class="sxs-lookup"><span data-stu-id="a19f0-129">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointList.</span></span>

    ```xml
    <filterTables>
            <!-- Set up the Routing Service's Message Filter Table -->
            <filterTable name="filterTable1">
                <!-- Add an entity that maps the MatchAllMessageFilter to the dead destination -->
                <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
                <!-- Listed in the backupEndpointList -->
                <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
            </filterTable>
          </filterTables>
    ```

5. <span data-ttu-id="a19f0-130">Для оценки входящих сообщений с помощью фильтра, содержащегося в таблице фильтров, необходимо сопоставить таблицу фильтров с конечными точками службы при помощи поведения маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="a19f0-130">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="a19f0-131">В следующем примере демонстрируется связывание "filterTable1" с конечными точками службы.</span><span class="sxs-lookup"><span data-stu-id="a19f0-131">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>

    ```xml
    <behaviors>
      <serviceBehaviors>
        <!-- Set up the Routing Behavior -->
        <behavior name="routingConfiguration">
          <routing filterTableName="filterTable1" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    ```

## <a name="example"></a><span data-ttu-id="a19f0-132">Пример</span><span class="sxs-lookup"><span data-stu-id="a19f0-132">Example</span></span>

<span data-ttu-id="a19f0-133">Ниже приведен полный список файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a19f0-133">The following is a complete listing of the configuration file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<!-- Copyright (c) Microsoft Corporation.  All Rights Reserved. -->
<configuration>
  <system.serviceModel>
    <services>
      <service behaviorConfiguration="routingConfiguration"
               name="System.ServiceModel.Routing.RoutingService">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost/routingservice/" />
          </baseAddresses>
        </host>
        <!-- Create the Routing Service endpoint -->
        <endpoint address="router"
                  binding="basicHttpBinding"
                  name="RoutingServiceEndpoint"
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <!-- Set up the Routing Behavior -->
        <behavior name="routingConfiguration">
          <routing filterTableName="filterTable1" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <!-- Create the destination endpoints that we want to send to -->
    <client>
      <!-- Create a dummy endpoint that we know will be down -->
      <endpoint name="deadDestination"
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"
                binding="netTcpBinding"
                contract="*" />

      <!-- Now create the real service endpoint -->
      <endpoint name="realDestination"
                address="net.tcp://localhost:8080/servicemodelsamples/service"
                binding="netTcpBinding"
                contract="*" />
    </client>
    <routing>
      <filters>
        <!-- Create a MatchAll filter which will catch all messages -->
        <filter name="MatchAllFilter1" filterType="MatchAll" />
      </filters>
      <filterTables>
        <!-- Set up the Routing Service's Message Filter Table -->
        <filterTable name="filterTable1">
            <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->
            <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
            <!-- Listed in the backupEndpointList -->
            <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
        </filterTable>
      </filterTables>
      <!-- Create the backup endpoint list -->
      <backupLists>
        <backupList name="backupEndpointList">
            <add endpointName="realDestination" />
        </backupList>
      </backupLists>
      </routing>
  </system.serviceModel>
</configuration>
```
