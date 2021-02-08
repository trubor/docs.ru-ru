---
description: Дополнительные сведения см. в статье как опубликовать метаданные для службы с помощью кода.
title: Практическое руководство. Публикация метаданных для службы с использованием кода
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 94939c77b1c66643b0cc378516479e35c41aefbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793692"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="fa8a4-103">Практическое руководство. Публикация метаданных для службы с использованием кода</span><span class="sxs-lookup"><span data-stu-id="fa8a4-103">How to: Publish Metadata for a Service Using Code</span></span>

<span data-ttu-id="fa8a4-104">Это один из двух инструкций, посвященных публикации метаданных для службы Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="fa8a4-104">This is one of two how-to topics that discuss publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="fa8a4-105">Существуют два способа указать, как служба должна публиковать метаданные: с помощью файла конфигурации и с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-105">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="fa8a4-106">В этом разделе показано, как публиковать метаданные для службы с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-106">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="fa8a4-107">В этом разделе показано, как опубликовать метаданные незащищенным образом.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-107">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="fa8a4-108">Любой клиент может получить метаданные из службы.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-108">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="fa8a4-109">Если требуется защита данных при публикации метаданных службой,</span><span class="sxs-lookup"><span data-stu-id="fa8a4-109">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="fa8a4-110">см. раздел [Настраиваемая конечная точка безопасных метаданных](../samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="fa8a4-110">see [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="fa8a4-111">Дополнительные сведения о публикации метаданных в файле конфигурации см. в разделе [инструкции. Публикация метаданных для службы с помощью файла конфигурации](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="fa8a4-111">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="fa8a4-112">Публикация метаданных позволяет клиентам извлекать метаданные с помощью запроса WS-Transfer GET или запроса HTTP/GET, используя строку запроса `?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-112">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="fa8a4-113">Чтобы быть уверенным, что код работает, необходимо создать базовую службу WCF.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-113">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="fa8a4-114">Базовая резидентная служба представлена в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-114">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="fa8a4-115">Публикация метаданных в коде</span><span class="sxs-lookup"><span data-stu-id="fa8a4-115">To publish metadata in code</span></span>  
  
1. <span data-ttu-id="fa8a4-116">В главном методе консольного приложения создайте экземпляр объекта <xref:System.ServiceModel.ServiceHost>, передав тип и базовый адрес службы.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-116">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. <span data-ttu-id="fa8a4-117">Создайте блок try сразу же после кода для шага 1, который перехватывает любые исключения, возникающие во время работы службы.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-117">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. <span data-ttu-id="fa8a4-118">Проверьте, не содержит ли ведущее приложение службы <xref:System.ServiceModel.Description.ServiceMetadataBehavior>; если не содержит, создайте новый экземпляр <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-118">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <span data-ttu-id="fa8a4-119">Задайте свойству <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> значение `true.`</span><span class="sxs-lookup"><span data-stu-id="fa8a4-119">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <span data-ttu-id="fa8a4-120"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> содержит свойство <xref:System.ServiceModel.Description.MetadataExporter>.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-120">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="fa8a4-121"><xref:System.ServiceModel.Description.MetadataExporter> содержит свойство <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-121">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="fa8a4-122">Задайте для свойства <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> значение <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-122">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="fa8a4-123">Свойству <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> можно также присвоить значение <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-123">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="fa8a4-124">Если задано <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> средство экспорта метаданных, создает сведения о политике с метаданными, которые соответствует WS-Policy 1,5.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="fa8a4-125">Если задано значение <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>, модуль экспорта метаданных генерирует информацию о политике, соответствующую спецификации WS-Policy 1.2.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-125">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <span data-ttu-id="fa8a4-126">Добавьте экземпляр <xref:System.ServiceModel.Description.ServiceMetadataBehavior> в коллекцию поведений ведущего приложения службы.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-126">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. <span data-ttu-id="fa8a4-127">Добавьте конечную точку обмена метаданными в ведущее приложение службы.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-127">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. <span data-ttu-id="fa8a4-128">Добавьте конечную точку приложения в ведущее приложение службы.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-128">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    > <span data-ttu-id="fa8a4-129">Если в службу не добавлена ни одна конечная точка, то среда выполнения добавляет конечные точки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-129">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="fa8a4-130">В этом примере, поскольку параметр <xref:System.ServiceModel.Description.ServiceMetadataBehavior> установлен в значение `true`, для службы включена публикация метаданных.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-130">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="fa8a4-131">Дополнительные сведения о конечных точках по умолчанию см. в разделе [упрощенная конфигурация](../simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="fa8a4-131">For more information about default endpoints, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="fa8a4-132">Откройте ведущее приложение службы и ожидайте входящие сообщения.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-132">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="fa8a4-133">Когда пользователь нажмет клавишу ВВОД, закройте ведущее приложение службы.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-133">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="fa8a4-134">Скомпилируйте и запустите консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-134">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="fa8a4-135">С помощью Internet Explorer перейдите к базовому адресу службы ( `http://localhost:8001/MetadataSample` в этом примере) и убедитесь, что публикация метаданных включена.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-135">Use Internet Explorer to browse to the base address of the service (`http://localhost:8001/MetadataSample` in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="fa8a4-136">Вверху веб-страницы должен отображаться заголовок «Простая служба», а сразу под ним - текст «Вы создали службу».</span><span class="sxs-lookup"><span data-stu-id="fa8a4-136">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="fa8a4-137">В противном случае вверху страницы отображается сообщение "Публикация метаданных для этой службы в настоящее время отключена".</span><span class="sxs-lookup"><span data-stu-id="fa8a4-137">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa8a4-138">Пример</span><span class="sxs-lookup"><span data-stu-id="fa8a4-138">Example</span></span>  

 <span data-ttu-id="fa8a4-139">В следующем примере кода показана реализация базовой службы WCF, которая публикует метаданные для службы в коде.</span><span class="sxs-lookup"><span data-stu-id="fa8a4-139">The following code example shows the implementation of a basic WCF service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="fa8a4-140">См. также</span><span class="sxs-lookup"><span data-stu-id="fa8a4-140">See also</span></span>

- [<span data-ttu-id="fa8a4-141">Практическое руководство. Размещение службы WCF в управляемом приложении</span><span class="sxs-lookup"><span data-stu-id="fa8a4-141">How to: Host a WCF Service in a Managed Application</span></span>](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="fa8a4-142">Резидентное размещение</span><span class="sxs-lookup"><span data-stu-id="fa8a4-142">Self-Host</span></span>](../samples/self-host.md)
- [<span data-ttu-id="fa8a4-143">Общие сведения об архитектуре метаданных</span><span class="sxs-lookup"><span data-stu-id="fa8a4-143">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="fa8a4-144">Использование метаданных</span><span class="sxs-lookup"><span data-stu-id="fa8a4-144">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="fa8a4-145">Практическое руководство. Публикация метаданных для службы с использованием файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="fa8a4-145">How to: Publish Metadata for a Service Using a Configuration File</span></span>](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
