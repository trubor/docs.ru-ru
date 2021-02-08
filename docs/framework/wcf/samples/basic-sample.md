---
description: 'Дополнительные сведения: базовый пример'
title: Базовый образец
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 064c3d616a911f789050ccd5da433ed10fcfb596
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778845"
---
# <a name="basic-sample"></a><span data-ttu-id="39c0f-103">Базовый образец</span><span class="sxs-lookup"><span data-stu-id="39c0f-103">Basic Sample</span></span>

<span data-ttu-id="39c0f-104">В этом образце показано, как сделать службу обнаруживаемой, а также как искать и вызывать обнаруживаемую службу.</span><span class="sxs-lookup"><span data-stu-id="39c0f-104">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="39c0f-105">Этот образец состоит из двух проектов: службы и клиента.</span><span class="sxs-lookup"><span data-stu-id="39c0f-105">This sample is composed of two projects: service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="39c0f-106">Этот образец реализует возможность обнаружения в коде.</span><span class="sxs-lookup"><span data-stu-id="39c0f-106">This sample implements discovery in code.</span></span>  <span data-ttu-id="39c0f-107">Пример, в котором реализуется обнаружение в конфигурации, см. в разделе [Configuration](configuration-sample.md).</span><span class="sxs-lookup"><span data-stu-id="39c0f-107">For a sample that implements discovery in configuration, see [Configuration](configuration-sample.md).</span></span>

## <a name="service"></a><span data-ttu-id="39c0f-108">Служба</span><span class="sxs-lookup"><span data-stu-id="39c0f-108">Service</span></span>

<span data-ttu-id="39c0f-109">Это простая реализация службы калькулятора.</span><span class="sxs-lookup"><span data-stu-id="39c0f-109">This is a simple calculator service implementation.</span></span> <span data-ttu-id="39c0f-110">Код обнаружения можно найти в `Main`, где к узлу службы добавляется <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> и добавляется <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="39c0f-110">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new
      WSHttpBinding(), String.Empty);

    // Make the service discoverable over UDP multicast
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    serviceHost.Open();
    // ...
}
```

## <a name="client"></a><span data-ttu-id="39c0f-111">Клиент</span><span class="sxs-lookup"><span data-stu-id="39c0f-111">Client</span></span>

<span data-ttu-id="39c0f-112">Клиент использует <xref:System.ServiceModel.Discovery.DynamicEndpoint> для определения местоположения службы.</span><span class="sxs-lookup"><span data-stu-id="39c0f-112">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="39c0f-113">Стандартная конечная точка <xref:System.ServiceModel.Discovery.DynamicEndpoint> вычисляет конечную точку службы, когда открывается клиент.</span><span class="sxs-lookup"><span data-stu-id="39c0f-113">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="39c0f-114">В этом случае <xref:System.ServiceModel.Discovery.DynamicEndpoint> ищет службу на основе контракта службы.</span><span class="sxs-lookup"><span data-stu-id="39c0f-114">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="39c0f-115">Конечная точка <xref:System.ServiceModel.Discovery.DynamicEndpoint> ведет поиск по <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="39c0f-115">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="39c0f-116">Когда конечная точка службы найдена, клиент подключается к этой службе по заданной привязке.</span><span class="sxs-lookup"><span data-stu-id="39c0f-116">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

<span data-ttu-id="39c0f-117">Клиент определяет метод `InvokeCalculatorService`, который использует класс <xref:System.ServiceModel.Discovery.DiscoveryClient> для поиска служб.</span><span class="sxs-lookup"><span data-stu-id="39c0f-117">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="39c0f-118">Класс <xref:System.ServiceModel.Discovery.DynamicEndpoint> наследует от класса <xref:System.ServiceModel.Description.ServiceEndpoint>, чтобы он мог быть передан в метод `InvokeCalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="39c0f-118">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="39c0f-119">В примере затем используется конечная точка <xref:System.ServiceModel.Discovery.DynamicEndpoint> для создания экземпляра `CalculatorServiceClient` и вызываются различные операции службы калькулятора.</span><span class="sxs-lookup"><span data-stu-id="39c0f-119">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>

```csharp
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)
{
   // Create a client
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);

   Console.WriteLine("Invoking CalculatorService");
   Console.WriteLine();

   double value1 = 100.00D;
   double value2 = 15.99D;

   // Call the Add service operation.
   double result = client.Add(value1, value2);
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

   // Call the Subtract service operation.
   result = client.Subtract(value1, value2);
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

   // Call the Multiply service operation.
   result = client.Multiply(value1, value2);
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

   // Call the Divide service operation.
   result = client.Divide(value1, value2);
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
   Console.WriteLine();

   //Closing the client gracefully closes the connection and cleans up resources
   client.Close();
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="39c0f-120">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="39c0f-120">To use this sample</span></span>

1. <span data-ttu-id="39c0f-121">В этом образце используются конечные точки HTTP, и для работы этого образца необходимо добавить соответствующие списки управления доступом по URL-адресу.</span><span class="sxs-lookup"><span data-stu-id="39c0f-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="39c0f-122">Дополнительные сведения см. в разделе [Настройка HTTP и HTTPS](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="39c0f-122">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="39c0f-123">Нужные списки управления доступом будут добавлены после выполнения следующей команды с повышенными привилегиями.</span><span class="sxs-lookup"><span data-stu-id="39c0f-123">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="39c0f-124">Если команда не работает, следует указать домен и имя пользователя в следующих аргументах.</span><span class="sxs-lookup"><span data-stu-id="39c0f-124">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="39c0f-125">С помощью Visual Studio 2012 откройте файл Basic. sln и создайте пример.</span><span class="sxs-lookup"><span data-stu-id="39c0f-125">Using Visual Studio 2012, open the Basic.sln and build the sample.</span></span>

3. <span data-ttu-id="39c0f-126">Запустите приложение service.exe.</span><span class="sxs-lookup"><span data-stu-id="39c0f-126">Run the service.exe application.</span></span>

4. <span data-ttu-id="39c0f-127">После запуска службы запустите client.exe.</span><span class="sxs-lookup"><span data-stu-id="39c0f-127">After the service has started, run the client.exe.</span></span>

5. <span data-ttu-id="39c0f-128">Заметьте, что клиенту удалось найти службу, не зная ее адреса.</span><span class="sxs-lookup"><span data-stu-id="39c0f-128">Observe that the client was able to find the service without knowing its address.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39c0f-129">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="39c0f-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="39c0f-130">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="39c0f-130">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="39c0f-131">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="39c0f-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="39c0f-132">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="39c0f-132">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
