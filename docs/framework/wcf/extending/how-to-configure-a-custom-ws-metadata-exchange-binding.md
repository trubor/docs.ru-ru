---
description: Дополнительные сведения см. в статье Настройка пользовательской привязки WS-Metadata Exchange.
title: Практическое руководство. Настройка пользовательской привязки для обмена WS-Metadata
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: ae9d1932e7539d25c117a98bd130d1def8e691fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743737"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="d9e79-103">Практическое руководство. Настройка пользовательской привязки для обмена WS-Metadata</span><span class="sxs-lookup"><span data-stu-id="d9e79-103">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>

<span data-ttu-id="d9e79-104">В этой статье объясняется, как настроить настраиваемую привязку WS-Metadata Exchange.</span><span class="sxs-lookup"><span data-stu-id="d9e79-104">This article explains how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="d9e79-105">Windows Communication Foundation (WCF) включает четыре определяемые системой привязки метаданных, но метаданные можно публиковать с помощью любой требуемой привязки.</span><span class="sxs-lookup"><span data-stu-id="d9e79-105">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="d9e79-106">В этой статье показано, как опубликовать метаданные с помощью `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="d9e79-106">This article shows you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="d9e79-107">Эта привязка позволяет предоставлять метаданные безопасным способом.</span><span class="sxs-lookup"><span data-stu-id="d9e79-107">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="d9e79-108">Код в этой статье основан на [Начало работы](../samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d9e79-108">The code in this article is based on the [Getting Started](../samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="d9e79-109">Использование файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="d9e79-109">Using a configuration file</span></span>  
  
1. <span data-ttu-id="d9e79-110">В файле конфигурации службы добавьте поведение службы, содержащее тег `serviceMetadata`:</span><span class="sxs-lookup"><span data-stu-id="d9e79-110">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="d9e79-111">Добавьте в тег службы, ссылающийся на новое поведение, атрибут `behaviorConfiguration`:</span><span class="sxs-lookup"><span data-stu-id="d9e79-111">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior" />
    ```  
  
3. <span data-ttu-id="d9e79-112">Добавьте конечную точку метаданных, указав mex в качестве адреса, `wsHttpBinding` как привязку и <xref:System.ServiceModel.Description.IMetadataExchange> как контракт:</span><span class="sxs-lookup"><span data-stu-id="d9e79-112">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="d9e79-113">Чтобы убедиться, что конечная точка обмена метаданными работает правильно, добавьте тег конечной точки в файл конфигурации клиента:</span><span class="sxs-lookup"><span data-stu-id="d9e79-113">To verify the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="d9e79-114">В методе клиента Main() создайте новый экземпляр <xref:System.ServiceModel.Description.MetadataExchangeClient>, задайте его свойство <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> как `true`, вызовите <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>, а затем выполните итерацию через коллекцию возвращенных метаданных:</span><span class="sxs-lookup"><span data-stu-id="d9e79-114">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="d9e79-115">Настройка кодом</span><span class="sxs-lookup"><span data-stu-id="d9e79-115">Configuring by code</span></span>  
  
1. <span data-ttu-id="d9e79-116">Создайте экземпляр привязки <xref:System.ServiceModel.WSHttpBinding>:</span><span class="sxs-lookup"><span data-stu-id="d9e79-116">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="d9e79-117">Создайте экземпляр <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="d9e79-117">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="d9e79-118">Добавьте конечную точку службы и экземпляр <xref:System.ServiceModel.Description.ServiceMetadataBehavior>:</span><span class="sxs-lookup"><span data-stu-id="d9e79-118">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="d9e79-119">Добавьте конечную точку обмена метаданными, указав ранее созданную <xref:System.ServiceModel.WSHttpBinding>:</span><span class="sxs-lookup"><span data-stu-id="d9e79-119">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="d9e79-120">Чтобы проверить правильность работы конечной точки обмена метаданными, добавьте тег конечной точки в файл конфигурации клиента:</span><span class="sxs-lookup"><span data-stu-id="d9e79-120">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="d9e79-121">В методе клиента Main() создайте новый экземпляр <xref:System.ServiceModel.Description.MetadataExchangeClient>, задайте его свойство <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> как `true`, вызовите <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>, а затем выполните итерацию через коллекцию возвращенных метаданных:</span><span class="sxs-lookup"><span data-stu-id="d9e79-121">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d9e79-122">См. также</span><span class="sxs-lookup"><span data-stu-id="d9e79-122">See also</span></span>

- [<span data-ttu-id="d9e79-123">Поведение публикации метаданных</span><span class="sxs-lookup"><span data-stu-id="d9e79-123">Metadata Publishing Behavior</span></span>](../samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="d9e79-124">Извлечение метаданных</span><span class="sxs-lookup"><span data-stu-id="d9e79-124">Retrieve Metadata</span></span>](../samples/retrieve-metadata.md)
- [<span data-ttu-id="d9e79-125">Метаданные</span><span class="sxs-lookup"><span data-stu-id="d9e79-125">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="d9e79-126">Публикация метаданных</span><span class="sxs-lookup"><span data-stu-id="d9e79-126">Publishing Metadata</span></span>](../feature-details/publishing-metadata.md)
- [<span data-ttu-id="d9e79-127">Публикация конечных точек метаданных</span><span class="sxs-lookup"><span data-stu-id="d9e79-127">Publishing Metadata Endpoints</span></span>](../publishing-metadata-endpoints.md)
