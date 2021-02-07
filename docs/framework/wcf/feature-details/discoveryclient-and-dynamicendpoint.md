---
description: 'Дополнительные сведения о: удалено клиентом DiscoveryClient и Динамицендпоинт'
title: DiscoveryClient и DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 34f6c5d7d8958f4a28a6bff950f3f6dad81871ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743178"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="894ab-103">DiscoveryClient и DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="894ab-103">DiscoveryClient and DynamicEndpoint</span></span>

<span data-ttu-id="894ab-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> и <xref:System.ServiceModel.Discovery.DynamicEndpoint> представляют собой два класса, используемые на стороне клиента для поиска служб.</span><span class="sxs-lookup"><span data-stu-id="894ab-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="894ab-105"><xref:System.ServiceModel.Discovery.DiscoveryClient> предоставляет список служб, соответствующих конкретному набору требований, и позволяет подключиться к службам.</span><span class="sxs-lookup"><span data-stu-id="894ab-105"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="894ab-106"><xref:System.ServiceModel.Discovery.DynamicEndpoint> выполняет те же функции и, кроме того, автоматически подключается к одной из найденных служб.</span><span class="sxs-lookup"><span data-stu-id="894ab-106"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="894ab-107">Все конечные точки могут быть преобразованы в <xref:System.ServiceModel.Discovery.DynamicEndpoint>, условие поиска также может быть добавлено в конфигурацию, поэтому <xref:System.ServiceModel.Discovery.DynamicEndpoint> полезен в случаях, когда в решении необходима функция обнаружения, но изменения логики клиента нежелательны (нужно лишь изменить конечные точки).</span><span class="sxs-lookup"><span data-stu-id="894ab-107">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="894ab-108">С другой стороны, <xref:System.ServiceModel.Discovery.DiscoveryClient> можно использовать для более точного контроля над операцией поиска.</span><span class="sxs-lookup"><span data-stu-id="894ab-108"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="894ab-109">Использование и преимущества каждого класса уточняются далее.</span><span class="sxs-lookup"><span data-stu-id="894ab-109">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="894ab-110">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="894ab-110">DiscoveryClient</span></span>  

 <span data-ttu-id="894ab-111">Класс <xref:System.ServiceModel.Discovery.DiscoveryClient> определяет синхронный и асинхронный методы Find, а также события <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> и <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>.</span><span class="sxs-lookup"><span data-stu-id="894ab-111">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="894ab-112">Он также определяет синхронные и асинхронные методы Resolve и событие <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted>.</span><span class="sxs-lookup"><span data-stu-id="894ab-112">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="894ab-113">Методы <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> и <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> служат для поиска служб.</span><span class="sxs-lookup"><span data-stu-id="894ab-113">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="894ab-114">Оба эти метода принимают экземпляр <xref:System.ServiceModel.Discovery.FindCriteria>, что позволяет указать имя типа контракта, область действия, максимальное количество запрошенных результатов и область сопоставления результатов.</span><span class="sxs-lookup"><span data-stu-id="894ab-114">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="894ab-115">События <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> и <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> могут использоваться при вызове метода <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="894ab-115">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="894ab-116">Событие <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> инициируется каждый раз, когда <xref:System.ServiceModel.Discovery.DiscoveryClient> получает ответ от службы.</span><span class="sxs-lookup"><span data-stu-id="894ab-116"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="894ab-117">Оно может быть использовано для отображения индикатора выполнения, показывающего ход выполнения операции поиска.</span><span class="sxs-lookup"><span data-stu-id="894ab-117">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="894ab-118">Оно также может быть использовано для обработки запросов поиска при их поступлении.</span><span class="sxs-lookup"><span data-stu-id="894ab-118">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="894ab-119">Событие <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> вызывается при завершении операции поиска.</span><span class="sxs-lookup"><span data-stu-id="894ab-119">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="894ab-120">Это может произойти при получении максимального количества ответов или по истечении времени, определенного свойством <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>.</span><span class="sxs-lookup"><span data-stu-id="894ab-120">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="894ab-121">При завершении операции поиска результаты возвращаются в экземпляре <xref:System.ServiceModel.Discovery.FindResponse>.</span><span class="sxs-lookup"><span data-stu-id="894ab-121">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="894ab-122">Объект <xref:System.ServiceModel.Discovery.FindResponse> содержит коллекцию объектов <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, содержащих адреса, имена типов контрактов, расширения, URI-прослушивания, области сопоставления служб.</span><span class="sxs-lookup"><span data-stu-id="894ab-122">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="894ab-123">Далее эти сведения могут быть использованы для соединения и вызова одной из сопоставленных служб.</span><span class="sxs-lookup"><span data-stu-id="894ab-123">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="894ab-124">В следующем примере показано, как вызвать метод System. ServiceModel. обнаружения. удалено клиентом DiscoveryClient. Find (System. ServiceModel. Discovery. FindCriteria) и использовать возвращенные метаданные для вызова найденной службы.</span><span class="sxs-lookup"><span data-stu-id="894ab-124">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="894ab-125">Преимущество использования заключается в <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> том, что вы можете кэшировать список найденных конечных точек и использовать их позже.</span><span class="sxs-lookup"><span data-stu-id="894ab-125">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="894ab-126">Этот кэш позволяет создать логику для обработки различных условий отказа.</span><span class="sxs-lookup"><span data-stu-id="894ab-126">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
```csharp
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 <span data-ttu-id="894ab-127">В следующем примере описано асинхронное выполнение операции поиска.</span><span class="sxs-lookup"><span data-stu-id="894ab-127">The following example shows how to perform a find operation asynchronously.</span></span>  
  
```csharp
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));
}
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```
  
 <span data-ttu-id="894ab-128">Для поиска службы по ее адресу конечной точки используйте методы <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> и <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29>.</span><span class="sxs-lookup"><span data-stu-id="894ab-128">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="894ab-129">Это может оказаться полезным в тех случаях, когда конечная точка не может быть адресована через сеть.</span><span class="sxs-lookup"><span data-stu-id="894ab-129">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="894ab-130">Метод Resolve принимает экземпляр <xref:System.ServiceModel.Discovery.ResolveCriteria>, что позволяет задать разрешаемый адрес конечной точки, максимальную продолжительность операции разрешения, набор расширений.</span><span class="sxs-lookup"><span data-stu-id="894ab-130">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="894ab-131">В следующем примере показано, каким образом производится разрешение службы с помощью метода <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="894ab-131">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="894ab-132">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="894ab-132">DynamicEndpoint</span></span>  

 <span data-ttu-id="894ab-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint> — Это стандартная конечная точка (Дополнительные сведения см. в разделе [Стандартные конечные точки](standard-endpoints.md)), которая выполняет обнаружение и автоматически выбирает соответствующую службу.</span><span class="sxs-lookup"><span data-stu-id="894ab-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="894ab-134">Необходимо всего лишь создать <xref:System.ServiceModel.Discovery.DynamicEndpoint>, передав ей искомый контракт и используемую привязку, и передать экземпляр <xref:System.ServiceModel.Discovery.DynamicEndpoint> клиенту WCF.</span><span class="sxs-lookup"><span data-stu-id="894ab-134">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="894ab-135">В следующем примере показано создание и использование <xref:System.ServiceModel.Discovery.DynamicEndpoint> для вызова службы калькулятора.</span><span class="sxs-lookup"><span data-stu-id="894ab-135">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="894ab-136">Поиск выполняется при каждом открытии клиента.</span><span class="sxs-lookup"><span data-stu-id="894ab-136">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="894ab-137">Любую конечную точку, определенную в конфигурации, можно также включить в, <xref:System.ServiceModel.Discovery.DynamicEndpoint> добавив `kind ="dynamicEndpoint"` атрибут к элементу конфигурации конечной точки.</span><span class="sxs-lookup"><span data-stu-id="894ab-137">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
```csharp  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a><span data-ttu-id="894ab-138">См. также</span><span class="sxs-lookup"><span data-stu-id="894ab-138">See also</span></span>

- [<span data-ttu-id="894ab-139">Обнаружение с помощью областей</span><span class="sxs-lookup"><span data-stu-id="894ab-139">Discovery with Scopes</span></span>](../samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="894ab-140">Основной</span><span class="sxs-lookup"><span data-stu-id="894ab-140">Basic</span></span>](../samples/basic-sample.md)
