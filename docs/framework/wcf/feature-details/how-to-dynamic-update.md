---
description: Дополнительные сведения см. в статье как динамическое обновление
title: 'Как выполнить: Динамическое обновление'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: 877cb58dd271fa70176a4197da273d923ec253f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704723"
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="93e6f-103">Как выполнить: Динамическое обновление</span><span class="sxs-lookup"><span data-stu-id="93e6f-103">How To: Dynamic Update</span></span>

<span data-ttu-id="93e6f-104">В этом разделе описаны основные действия по созданию и динамическому обновлению конфигурации маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="93e6f-104">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="93e6f-105">В данном примере первоначальная конфигурация маршрутизации получена из файла конфигурации, согласно этой конфигурации все сообщения направляются службе калькулятора regularCalc. Однако впоследствии она будет программно обновлена, чтобы изменить конечную точку назначения на службу roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="93e6f-105">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93e6f-106">Во многих системах используется полностью динамическая конфигурация, конфигурация по умолчанию при этом не используется. В некоторых случаях, как в этом разделе, желательно, чтобы при запуске службы конфигурация находилась в состоянии по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="93e6f-106">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93e6f-107">Динамическое обновление выполняется только в памяти, сам файл конфигурации при этом не изменяется.</span><span class="sxs-lookup"><span data-stu-id="93e6f-107">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="93e6f-108">Обе службы, regularCalc и roundingCalc, поддерживают одинаковые операции сложения, вычитания, умножения и деления, однако служба roundingCalc, прежде чем возвратить результаты вычислений, округляет их до ближайшего целого числа.</span><span class="sxs-lookup"><span data-stu-id="93e6f-108">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="93e6f-109">С помощью файла конфигурации выполняется настройка службы для перенаправления всех сообщений службе regularCalc.</span><span class="sxs-lookup"><span data-stu-id="93e6f-109">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="93e6f-110">После запуска службы маршрутизации она перенастраивается с помощью метода <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> для перенаправления сообщений службе roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="93e6f-110">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="93e6f-111">Реализация первоначальной конфигурации</span><span class="sxs-lookup"><span data-stu-id="93e6f-111">Implement Initial Configuration</span></span>  
  
1. <span data-ttu-id="93e6f-112">Создайте базовую конфигурацию службы маршрутизации, указав конечные точки службы, предоставленные службой.</span><span class="sxs-lookup"><span data-stu-id="93e6f-112">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="93e6f-113">В следующем примере определяется отдельная конечная точка службы, которая будет использоваться для получения сообщений.</span><span class="sxs-lookup"><span data-stu-id="93e6f-113">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="93e6f-114">Также будет определена конечная точка клиента, которая будет использоваться для отправки сообщений службе regularCalc.</span><span class="sxs-lookup"><span data-stu-id="93e6f-114">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <client>  
    <!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    ```  
  
2. <span data-ttu-id="93e6f-115">Определите фильтр, используемый для перенаправления сообщений в конечные точки назначения.</span><span class="sxs-lookup"><span data-stu-id="93e6f-115">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="93e6f-116">В этом примере фильтр MatchAll используется для перенаправления всех сообщений в заданную ранее конечную точку regularCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="93e6f-116">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="93e6f-117">Ниже приведен пример этого фильтра и таблицы фильтра.</span><span class="sxs-lookup"><span data-stu-id="93e6f-117">The following example defines the filter and filter table.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the message filter-->  
      <filter name="MatchAllFilter" filterType="MatchAll"/>  
    </filters>  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filter to the message filter table-->  
          <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
3. <span data-ttu-id="93e6f-118">Для оценки входящих сообщений с помощью фильтров, содержащихся в таблице фильтров, следует связать таблицу фильтров с конечными точками службы при помощи поведения маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="93e6f-118">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="93e6f-119">В следующем примере демонстрируется связывание "filterTable1" с конечной точкой службы.</span><span class="sxs-lookup"><span data-stu-id="93e6f-119">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
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
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="93e6f-120">Реализация динамической конфигурации</span><span class="sxs-lookup"><span data-stu-id="93e6f-120">Implement Dynamic Configuration</span></span>  

 <span data-ttu-id="93e6f-121">Динамическая настройка службы маршрутизации может выполняться только в коде путем создания нового экземпляра <xref:System.ServiceModel.Routing.RoutingConfiguration> и замены текущей конфигурации с помощью метода <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A>.</span><span class="sxs-lookup"><span data-stu-id="93e6f-121">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="93e6f-122">В этом примере служба маршрутизации является резидентной в консольном приложении.</span><span class="sxs-lookup"><span data-stu-id="93e6f-122">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="93e6f-123">После запуска приложения изменить конфигурацию маршрутизации можно, введя в окне консоли «regular» или «rounding», чтобы настроить конечную току назначения, в которую будут направляться сообщения. При значении «regular» это regularCalc, в противном случае при значении «rounding» это roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="93e6f-123">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1. <span data-ttu-id="93e6f-124">Для поддержки службы маршрутизации необходимо добавить следующие операторы using.</span><span class="sxs-lookup"><span data-stu-id="93e6f-124">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. <span data-ttu-id="93e6f-125">Чтобы сделать службу маршрутизации резидентной в консольном приложении, используется следующий код.</span><span class="sxs-lookup"><span data-stu-id="93e6f-125">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="93e6f-126">Служба маршрутизации при этом инициализируется с конфигурацией, описанной в предыдущем шаге, которая содержится в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="93e6f-126">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="93e6f-127">Цикл while содержит код, используемый для изменения конфигурации маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="93e6f-127">The while loop contains the code used to change the routing configuration.</span></span>  
  
    ```csharp  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost =  
            new ServiceHost(typeof(RoutingService)))  
        {  
            // Open the ServiceHost to create listeners
            // and start listening for messages.  
            Console.WriteLine("The Routing Service configured, opening....");  
            serviceHost.Open();  
            Console.WriteLine("The Routing Service is now running.");  
             Console.WriteLine("Type 'quit' to terminate router.");  
             Console.WriteLine("<ENTER> to change routing configuration.");  
             while (Console.ReadLine() != "quit")  
             {  
            ....  
            }  
        }  
    }  
    ```  
  
3. <span data-ttu-id="93e6f-128">Чтобы динамически обновить конфигурацию маршрутизации, необходимо создать новую конфигурацию маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="93e6f-128">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="93e6f-129">В ней должны быть указаны все конечные точки, фильтры и таблицы фильтров, которые требуются для новой конфигурации маршрутизации, поскольку она полностью заменит существующую конфигурацию маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="93e6f-129">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="93e6f-130">Чтобы использовать новую конфигурацию маршрутизации, необходимо вызвать метод <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> и передать новую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="93e6f-130">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="93e6f-131">Добавьте следующий код в определенный ранее цикл while, чтобы разрешить перенастройку службы с использованием пользовательского ввода.</span><span class="sxs-lookup"><span data-stu-id="93e6f-131">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
    ```csharp  
    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
    string destEndpoint = Console.ReadLine();  
    // Create a new RoutingConfiguration  
    RoutingConfiguration rc = new RoutingConfiguration();  
    // Determine the endpoint to configure for  
    switch (destEndpoint)  
    {  
        case "regular":  
            // Define the destination endpoint  
            ServiceEndpoint regularCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        case "rounding":  
            // Define the destination endpoint  
            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        default:  
            Console.WriteLine("Incorrect value entered, no change.");  
            break;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="93e6f-132">Поскольку метод для предоставления новой конфигурации маршрутизации содержится в расширении службы RoutingExtension, новые объекты RoutingConfiguration могут быть предоставлены в любом месте модели расширяемости WCF, которая имеет или может получить ссылку на ServiceHost или ServiceExtensions (например, в другом ServiceExtension).</span><span class="sxs-lookup"><span data-stu-id="93e6f-132">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span>
  
## <a name="example"></a><span data-ttu-id="93e6f-133">Пример</span><span class="sxs-lookup"><span data-stu-id="93e6f-133">Example</span></span>  

<span data-ttu-id="93e6f-134">Ниже приведен полный список консольного приложения, используемого в этом примере.</span><span class="sxs-lookup"><span data-stu-id="93e6f-134">The following is a complete listing of the console application used in this example:</span></span>
  
```csharp
//-----------------------------------------------------------------  
//  Copyright (c) Microsoft Corporation.  All Rights Reserved.  
//-----------------------------------------------------------------  
  
using System;  
using System.Collections.Generic;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.ServiceModel.Description;  
using System.ServiceModel.Dispatcher;  
using System.ServiceModel.Routing;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    public class Router  
    {  
        // Host the service within this EXE console application.  
        public static void Main()  
        {
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
            {  
                // Open the ServiceHost to create listeners
                // and start listening for messages.  
                Console.WriteLine("The Routing Service configured, opening....");  
                serviceHost.Open();  
                Console.WriteLine("The Routing Service is now running.");  
                Console.WriteLine("Type 'quit' to terminate router.");  
                Console.WriteLine("<ENTER> to change routing configuration.");  
                while (Console.ReadLine() != "quit")  
                {  
                    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
                    string destEndpoint = Console.ReadLine();  
                    // Create a new RoutingConfiguration  
                    RoutingConfiguration rc = new RoutingConfiguration();  
                    // Determine the endpoint to configure for  
                    switch (destEndpoint)  
                    {  
                        case "regular":  
                            // Define the destination endpoint  
                            ServiceEndpoint regularCalc = new ServiceEndpoint(  
                            ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                            new NetTcpBinding(),  
                            new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        case "rounding":  
                            // Define the destination endpoint  
                            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
                                ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                                new NetTcpBinding(),  
                                new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        default:  
                            Console.WriteLine("Incorrect value entered, no change.");  
                            break;  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="93e6f-135">Пример</span><span class="sxs-lookup"><span data-stu-id="93e6f-135">Example</span></span>  

<span data-ttu-id="93e6f-136">Ниже приведен полный список файлов конфигурации, используемых в этом примере.</span><span class="sxs-lookup"><span data-stu-id="93e6f-136">The following is a complete listing of the configuration file used in this example:</span></span>
  
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
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
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
<!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
  
      <filters>  
        <!--define the message filter-->  
        <filter name="MatchAllFilter" filterType="MatchAll"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filter to the message filter table-->  
            <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="93e6f-137">См. также</span><span class="sxs-lookup"><span data-stu-id="93e6f-137">See also</span></span>

- [<span data-ttu-id="93e6f-138">Службы маршрутизации</span><span class="sxs-lookup"><span data-stu-id="93e6f-138">Routing Services</span></span>](../samples/routing-services.md)
