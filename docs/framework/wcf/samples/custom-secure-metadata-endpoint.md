---
description: 'Дополнительные сведения: Настраиваемая конечная точка безопасных метаданных'
title: Пользовательская конечная точка защищенных метаданных
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 11b8439fda74924ff17a101d3aa0b0db948ff8dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752461"
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="546ab-103">Пользовательская конечная точка защищенных метаданных</span><span class="sxs-lookup"><span data-stu-id="546ab-103">Custom Secure Metadata Endpoint</span></span>

<span data-ttu-id="546ab-104">В этом образце показано, как реализовать службу с защищенной конечной точкой метаданных, которая использует одну из привязок обмена, отличной от метаданных, и как настроить [средство служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) или клиенты для выборки метаданных из такой конечной точки метаданных.</span><span class="sxs-lookup"><span data-stu-id="546ab-104">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="546ab-105">Существует две системные привязки для предоставления конечных точек метаданных: mexHttpBinding и mexHttpsBinding.</span><span class="sxs-lookup"><span data-stu-id="546ab-105">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="546ab-106">Привязка mexHttpBinding используется для предоставления конечной точки метаданных через HTTP в незащищенном режиме.</span><span class="sxs-lookup"><span data-stu-id="546ab-106">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="546ab-107">Привязка mexHttpsBinding используется для предоставления конечной точки метаданных через HTTP в защищенном режиме.</span><span class="sxs-lookup"><span data-stu-id="546ab-107">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="546ab-108">В этом образце описывается предоставление защищенной конечной точки метаданных с использованием объекта <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="546ab-108">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="546ab-109">Такой подход следует использовать, если требуется изменить параметры безопасности привязки, но при этом нежелательно использовать протокол HTTPS.</span><span class="sxs-lookup"><span data-stu-id="546ab-109">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="546ab-110">При использовании привязки mexHttpsBinding конечная точка метаданных будет защищена, но изменение параметров привязки окажется невозможным.</span><span class="sxs-lookup"><span data-stu-id="546ab-110">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="546ab-111">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="546ab-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="546ab-112">Служба</span><span class="sxs-lookup"><span data-stu-id="546ab-112">Service</span></span>  

 <span data-ttu-id="546ab-113">Служба в образце имеет две конечные точки.</span><span class="sxs-lookup"><span data-stu-id="546ab-113">The service in this sample has two endpoints.</span></span> <span data-ttu-id="546ab-114">Конечная точка приложения служит в качестве контракта `ICalculator` для привязки `WSHttpBinding` с включенным сеансом `ReliableSession` и режимом безопасности `Message` с использованием сертификатов.</span><span class="sxs-lookup"><span data-stu-id="546ab-114">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="546ab-115">Конечная точка метаданных также использует привязку `WSHttpBinding` с аналогичными параметрами безопасности, но без `ReliableSession`.</span><span class="sxs-lookup"><span data-stu-id="546ab-115">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="546ab-116">Соответствующая конфигурация представлена ниже.</span><span class="sxs-lookup"><span data-stu-id="546ab-116">Here is the relevant configuration:</span></span>  
  
```xml  
<services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 <span data-ttu-id="546ab-117">Во многих других образцах конечная точка метаданных использует привязку по умолчанию `mexHttpBinding`, которая не является безопасной.</span><span class="sxs-lookup"><span data-stu-id="546ab-117">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="546ab-118">В данном примере безопасность метаданных обеспечивается с помощью привязки `WSHttpBinding` с режимом безопасности `Message`.</span><span class="sxs-lookup"><span data-stu-id="546ab-118">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="546ab-119">Чтобы клиенты метаданных могли извлекать эти метаданные, они должны быть настроены с соответствующей привязкой.</span><span class="sxs-lookup"><span data-stu-id="546ab-119">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="546ab-120">В образце показаны два таких клиента.</span><span class="sxs-lookup"><span data-stu-id="546ab-120">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="546ab-121">Первый клиент использует Svcutil.exe для извлечения метаданных, а также создания клиентского кода и конфигурации во время разработки.</span><span class="sxs-lookup"><span data-stu-id="546ab-121">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="546ab-122">Поскольку служба использует для метаданных привязку, отличную от привязки по умолчанию, средство Svcutil.exe необходимо настроить определенным образом, чтобы оно могло получать метаданные из службы с помощью данной привязки.</span><span class="sxs-lookup"><span data-stu-id="546ab-122">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="546ab-123">Второй клиент использует распознаватель `MetadataResolver` с целью динамического извлечения метаданных для известного контракта с последующим вызовом операций на динамически создаваемом клиенте.</span><span class="sxs-lookup"><span data-stu-id="546ab-123">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="546ab-124">Клиент Svcutil</span><span class="sxs-lookup"><span data-stu-id="546ab-124">Svcutil client</span></span>  

 <span data-ttu-id="546ab-125">При использовании привязки по умолчанию для размещения конечной точки `IMetadataExchange` можно запустить Svcutil.exe с указанием адреса этой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="546ab-125">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="546ab-126">И это будет работать.</span><span class="sxs-lookup"><span data-stu-id="546ab-126">and it works.</span></span> <span data-ttu-id="546ab-127">Однако в этом образце для размещения метаданных сервер использует привязку, отличную от привязки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="546ab-127">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="546ab-128">Поэтому средство Svcutil.exe необходимо настроить на использование правильной привязки.</span><span class="sxs-lookup"><span data-stu-id="546ab-128">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="546ab-129">Это можно сделать с помощью файла Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="546ab-129">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="546ab-130">Файл Svcutil.exe.config выглядит как обычный файл конфигурации клиента.</span><span class="sxs-lookup"><span data-stu-id="546ab-130">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="546ab-131">Единственными необычными аспектами являются имя и контракт конечной точки клиента:</span><span class="sxs-lookup"><span data-stu-id="546ab-131">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="546ab-132">Имя конечной точки должно совпадать с именем схемы адреса, по которому размещаются метаданные, а контрактом конечной точки должен быть `IMetadataExchange`.</span><span class="sxs-lookup"><span data-stu-id="546ab-132">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="546ab-133">Таким образом, при запуске команды</span><span class="sxs-lookup"><span data-stu-id="546ab-133">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="546ab-134">выполняется поиск конечной точки с именем "http" и контракта `IMetadataExchange` для настройки привязки и поведения при взаимодействии с конечной точкой метаданных.</span><span class="sxs-lookup"><span data-stu-id="546ab-134">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="546ab-135">В остальной части файла Svcutil.exe.config в образце определяются конфигурация привязки и учетные данные поведения для соответствия конфигурации сервера конечной точки метаданных.</span><span class="sxs-lookup"><span data-stu-id="546ab-135">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="546ab-136">Чтобы средство Svcutil.exe могло использовать конфигурацию, заданную в файле Svcutil.exe.config, файл Svcutil.exe должен находиться в одном каталоге с файлом конфигурации.</span><span class="sxs-lookup"><span data-stu-id="546ab-136">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="546ab-137">Таким образом, необходимо скопировать файл Svcutil.exe из расположения установки в каталог, содержащий файл Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="546ab-137">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="546ab-138">Затем из этого каталога необходимо выполнить следующую команду:</span><span class="sxs-lookup"><span data-stu-id="546ab-138">Then from that directory, run the following command:</span></span>  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="546ab-139">Начальное значение ". \\ " гарантирует, что выполняется копирование Svcutil.exe в этом каталоге (с соответствующим Svcutil.exe.config).</span><span class="sxs-lookup"><span data-stu-id="546ab-139">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="546ab-140">Клиент MetadataResolver</span><span class="sxs-lookup"><span data-stu-id="546ab-140">MetadataResolver client</span></span>  

 <span data-ttu-id="546ab-141">Если клиенту известен контракт и способ обращения к метаданным во время разработки, клиент может динамически определять привязку и адрес конечных точек приложения с помощью распознавателя `MetadataResolver`.</span><span class="sxs-lookup"><span data-stu-id="546ab-141">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="546ab-142">Это демонстрируется в данном образце клиента: показано, как настроить привязку и учетные данные, используемые распознавателем `MetadataResolver`, путем создания и настройки клиента `MetadataExchangeClient`.</span><span class="sxs-lookup"><span data-stu-id="546ab-142">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="546ab-143">Информацию о привязке и сертификате, указанную в файле Svcutil.exe.config, можно задать императивно в клиенте `MetadataExchangeClient`:</span><span class="sxs-lookup"><span data-stu-id="546ab-143">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```csharp  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="546ab-144">При настроенном клиенте `mexClient` можно перечислить требуемые контракты и использовать распознаватель `MetadataResolver` для получения списка конечных точек с этими контрактами.</span><span class="sxs-lookup"><span data-stu-id="546ab-144">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="546ab-145">Наконец, можно использовать информацию из этих конечных точек для инициализации привязки и адреса фабрики `ChannelFactory`, используемой для создания каналов взаимодействия с конечными точками приложения.</span><span class="sxs-lookup"><span data-stu-id="546ab-145">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="546ab-146">Основная задача данного образца клиента - показать, что при использовании распознавателя `MetadataResolver` и необходимости задания пользовательских привязок или поведений для обмена метаданными можно использовать клиент `MetadataExchangeClient` для задания этих пользовательских параметров.</span><span class="sxs-lookup"><span data-stu-id="546ab-146">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="546ab-147">Настройка и сборка образца</span><span class="sxs-lookup"><span data-stu-id="546ab-147">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="546ab-148">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="546ab-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="546ab-149">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="546ab-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="546ab-150">Запуск образца на том же компьютере</span><span class="sxs-lookup"><span data-stu-id="546ab-150">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="546ab-151">Запустите файл Setup.bat из папки установки примера.</span><span class="sxs-lookup"><span data-stu-id="546ab-151">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="546ab-152">При этом устанавливаются все сертификаты, необходимые для выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="546ab-152">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="546ab-153">Обратите внимание, что Setup.bat использует средство FindPrivateKey.exe, которое устанавливается путем запуска setupCertTool.bat из [процедуры однократной настройки для примеров Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="546ab-153">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="546ab-154">Запустите клиентское приложение из каталога \MetadataResolverClient\bin или \SvcutilClient\bin.</span><span class="sxs-lookup"><span data-stu-id="546ab-154">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="546ab-155">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="546ab-155">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="546ab-156">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="546ab-156">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
4. <span data-ttu-id="546ab-157">После завершения работы образца запустите файл Cleanup.bat, чтобы удалить сертификаты.</span><span class="sxs-lookup"><span data-stu-id="546ab-157">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="546ab-158">В других образцах обеспечения безопасности используются те же сертификаты.</span><span class="sxs-lookup"><span data-stu-id="546ab-158">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="546ab-159">Выполнение примера на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="546ab-159">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="546ab-160">На сервере выполните команду `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="546ab-160">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="546ab-161">`setup.bat`При запуске с `service` аргументом создается сертификат службы с полным доменным именем компьютера и экспортируется сертификат службы в файл с именем Service. cer.</span><span class="sxs-lookup"><span data-stu-id="546ab-161">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2. <span data-ttu-id="546ab-162">Измените Web.config на сервере так, чтобы в файле отражалось новое имя сертификата.</span><span class="sxs-lookup"><span data-stu-id="546ab-162">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="546ab-163">То есть измените `findValue` атрибут в [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) элементе на полное доменное имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="546ab-163">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3. <span data-ttu-id="546ab-164">Скопируйте файл Service.cer из каталога службы в клиентский каталог на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="546ab-164">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4. <span data-ttu-id="546ab-165">На клиенте выполните команду `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="546ab-165">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="546ab-166">`setup.bat`При запуске с `client` аргументом создается сертификат клиента с именем Client.com и экспортируется сертификат клиента в файл с именем Client. cer.</span><span class="sxs-lookup"><span data-stu-id="546ab-166">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5. <span data-ttu-id="546ab-167">В файле App.config клиента `MetadataResolverClient` на клиентском компьютере измените значение адреса конечной точки обмена метаданными, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="546ab-167">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="546ab-168">Для этого замените имя localhost полным именем домена сервера.</span><span class="sxs-lookup"><span data-stu-id="546ab-168">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="546ab-169">Кроме того, замените вхождение "localhost" в файле metadataResolverClient.cs новым именем сертификата службы (полным доменным именем сервера).</span><span class="sxs-lookup"><span data-stu-id="546ab-169">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="546ab-170">Выполните то же самое для файла App.config проекта SvcutilClient.</span><span class="sxs-lookup"><span data-stu-id="546ab-170">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6. <span data-ttu-id="546ab-171">Скопируйте файл Client.cer из клиентского каталога в каталог службы на сервере.</span><span class="sxs-lookup"><span data-stu-id="546ab-171">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7. <span data-ttu-id="546ab-172">На клиенте выполните команду `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="546ab-172">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="546ab-173">Он импортирует сертификат службы из файла Service.cer в хранилище CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="546ab-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8. <span data-ttu-id="546ab-174">На сервере запустите файл `ImportClientCert.bat`. Он импортирует сертификат клиента из файла Client.cer в хранилище LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="546ab-174">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="546ab-175">На компьютере службы выполните построение проекта службы в Visual Studio и выберите страницу справки в веб-браузере, чтобы проверить что она запущена.</span><span class="sxs-lookup"><span data-stu-id="546ab-175">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="546ab-176">На клиентском компьютере запустите клиент MetadataResolverClient или SvcutilClient из VS.</span><span class="sxs-lookup"><span data-stu-id="546ab-176">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1. <span data-ttu-id="546ab-177">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="546ab-177">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="546ab-178">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="546ab-178">To clean up after the sample</span></span>  
  
- <span data-ttu-id="546ab-179">После завершения работы примера запустите в папке примеров файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="546ab-179">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="546ab-180">Этот скрипт не удаляет сертификаты службы на клиенте при выполнении примера на нескольких компьютерах.</span><span class="sxs-lookup"><span data-stu-id="546ab-180">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="546ab-181">Если вы выполнили примеры Windows Communication Foundation (WCF), использующие сертификаты на разных компьютерах, обязательно очистите сертификаты службы, установленные в хранилище CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="546ab-181">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="546ab-182">Для этого используйте следующую команду: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span><span class="sxs-lookup"><span data-stu-id="546ab-182">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="546ab-183">Например, `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="546ab-183">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="546ab-184">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="546ab-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="546ab-185">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="546ab-185">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="546ab-186">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="546ab-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="546ab-187">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="546ab-187">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`
