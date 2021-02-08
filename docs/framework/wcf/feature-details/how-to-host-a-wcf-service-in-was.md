---
description: Дополнительные сведения см. в статье как разместить службу WCF в WAS.
title: Практическое руководство. Размещение службы WCF в WAS
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: dcc5d553cc864050c5d1641fa86effc5a8129d4c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793770"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="8ae2f-103">Практическое руководство. Размещение службы WCF в WAS</span><span class="sxs-lookup"><span data-stu-id="8ae2f-103">How to: Host a WCF Service in WAS</span></span>

<span data-ttu-id="8ae2f-104">В этом разделе описаны основные шаги, необходимые для создания службы активации процессов Windows (также известной как WAS), размещенной Windows Communication Foundation служб (WCF).</span><span class="sxs-lookup"><span data-stu-id="8ae2f-104">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="8ae2f-105">WAS является службой активации нового процесса, представляющей собой обобщение возможностей Internet Information Services (IIS), которые работают с транспортными протоколами, отличными от HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-105">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="8ae2f-106">WCF использует интерфейс адаптера прослушивателя для передачи запросов на активацию, полученных через протоколы, отличные от HTTP, которые поддерживаются WCF, такие как TCP, именованные каналы и очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-106">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="8ae2f-107">Данный параметр размещения требует правильно установленных и настроенных компонентов активации WAS, но не требует написания кода размещения как части приложения.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-107">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="8ae2f-108">Дополнительные сведения об установке и настройке см. в разделе [как установить и настроить компоненты активации WCF](how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="8ae2f-108">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="8ae2f-109">Активация WAS не поддерживается, если канал обработки запросов веб-сервера работает в классическом режиме.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-109">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="8ae2f-110">Чтобы использовать активацию WAS, канал обработки запросов веб-сервера необходимо перевести в интегрированный режим.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-110">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="8ae2f-111">Если служба WCF размещена в WAS, стандартные привязки используются обычным способом.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-111">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="8ae2f-112">Однако при использовании <xref:System.ServiceModel.NetTcpBinding> и <xref:System.ServiceModel.NetNamedPipeBinding> для настройки служб, размещенных на WAS, ограничение должно быть удовлетворено.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-112">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="8ae2f-113">Если разные конечные точки используют один и тот же транспорт, параметры привязки должны соответствовать семи следующим свойствам:</span><span class="sxs-lookup"><span data-stu-id="8ae2f-113">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="8ae2f-114">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="8ae2f-114">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="8ae2f-115">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="8ae2f-115">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="8ae2f-116">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="8ae2f-116">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="8ae2f-117">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="8ae2f-117">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="8ae2f-118">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="8ae2f-118">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="8ae2f-119">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="8ae2f-119">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="8ae2f-120">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="8ae2f-120">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="8ae2f-121">В противном случае, конечная точка, запущенная первой, всегда определяет значения этих параметров, а добавленные позже конечные точки, если они не совпадают с этими настройками, вызывают <xref:System.ServiceModel.ServiceActivationException>.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-121">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="8ae2f-122">Исходный экземпляр этого примера см. в разделе [Активация TCP](../samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="8ae2f-122">For the source copy of this example, see [TCP Activation](../samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="8ae2f-123">Создание базовой службы, размещенной на WAS</span><span class="sxs-lookup"><span data-stu-id="8ae2f-123">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="8ae2f-124">Определите контракт службы для данного типа службы.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-124">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="8ae2f-125">Реализуйте контракт службы в классе службы.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-125">Implement the service contract in a service class.</span></span> <span data-ttu-id="8ae2f-126">Обратите внимание, что информация об адресе или привязке не указывается внутри реализации службы.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-126">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="8ae2f-127">Кроме того, для извлечения этих сведений из файла конфигурации не требуется писать код.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-127">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="8ae2f-128">Создайте файл Web.config, чтобы определить привязку <xref:System.ServiceModel.NetTcpBinding> для использования конечными точками `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-128">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="8ae2f-129">Создайте файл Service.svc, содержащий следующий код.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-129">Create a Service.svc file that contains the following code.</span></span>  
  
   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="8ae2f-130">Разместите файл Service.svc в виртуальном каталоге своего IIS.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-130">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="8ae2f-131">Создание клиента для использования службы</span><span class="sxs-lookup"><span data-stu-id="8ae2f-131">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="8ae2f-132">Используйте [служебную программу метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) из командной строки, чтобы создать код из метаданных службы.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-132">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="8ae2f-133">Создаваемый клиент содержит интерфейс `ICalculator`, определяющий контракт службы, которому должна удовлетворять реализация клиента.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-133">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="8ae2f-134">Созданное клиентское приложение также содержит реализацию `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-134">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="8ae2f-135">Обратите внимание, что информация об адресе и привязке нигде внутри реализации службы не указывается.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-135">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="8ae2f-136">Кроме того, для извлечения этих сведений из файла конфигурации не требуется писать код.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-136">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="8ae2f-137">Конфигурация для клиента, использующего <xref:System.ServiceModel.NetTcpBinding>, также создается программой Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-137">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="8ae2f-138">Имя этого файла должно задаваться в файле App.config, если используется Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-138">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. <span data-ttu-id="8ae2f-139">Создайте экземпляр класса `ClientCalculator` в приложении и вызовите операции службы.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-139">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="8ae2f-140">Скомпилируйте и запустите клиент.</span><span class="sxs-lookup"><span data-stu-id="8ae2f-140">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae2f-141">См. также</span><span class="sxs-lookup"><span data-stu-id="8ae2f-141">See also</span></span>

- [<span data-ttu-id="8ae2f-142">Активация TCP</span><span class="sxs-lookup"><span data-stu-id="8ae2f-142">TCP Activation</span></span>](../samples/tcp-activation.md)
- <span data-ttu-id="8ae2f-143">[Функции размещения Windows Server App Fabric](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8ae2f-143">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
