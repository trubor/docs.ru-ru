---
description: Дополнительные сведения см. в статье как получить метаданные через привязку не MEX.
title: Практическое руководство. Получение метаданных через привязку, не использующую MEX
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 521e48d90e9dbed2e0ded61c60af59d063d2b3dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644220"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="f7ee9-103">Практическое руководство. Получение метаданных через привязку, не использующую MEX</span><span class="sxs-lookup"><span data-stu-id="f7ee9-103">How to: Retrieve Metadata Over a non-MEX Binding</span></span>

<span data-ttu-id="f7ee9-104">В этом разделе описывается получение метаданных из конечной точки MEX через привязку, не использующую MEX.</span><span class="sxs-lookup"><span data-stu-id="f7ee9-104">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="f7ee9-105">Код в этом примере основан на образце [пользовательской защищенной конечной точки метаданных](../samples/custom-secure-metadata-endpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="f7ee9-105">The code in this sample is based on the [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="f7ee9-106">Получение метаданных через привязку, не использующую MEX</span><span class="sxs-lookup"><span data-stu-id="f7ee9-106">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="f7ee9-107">Определите привязку, используемую конечной точкой MEX.</span><span class="sxs-lookup"><span data-stu-id="f7ee9-107">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="f7ee9-108">Для служб Windows Communication Foundation (WCF) можно определить привязку MEX, обратившись к файлу конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="f7ee9-108">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="f7ee9-109">В этом случае привязка MEX определяется в следующей конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="f7ee9-109">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
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
  
2. <span data-ttu-id="f7ee9-110">В файле конфигурации клиента настройте такую же пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="f7ee9-110">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="f7ee9-111">В данном случае для клиента также определено поведение `clientCredentials` - для предоставления сертификата, который будет использоваться для проверки его подлинности службой при запросе метаданных от конечной точки MEX.</span><span class="sxs-lookup"><span data-stu-id="f7ee9-111">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="f7ee9-112">При использовании Svcutil.exe для запроса метаданных через пользовательскую привязку необходимо добавить конфигурацию конечной точки MEX в файл конфигурации для Svcutil.exe (Svcutil.exe.config), причем имя конфигурации конечной точки должно соответствовать схеме URI адреса конечной точки MEX, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="f7ee9-112">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>
    </system.serviceModel>  
    ```  
  
3. <span data-ttu-id="f7ee9-113">Создайте объект `MetadataExchangeClient` и вызовите метод `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="f7ee9-113">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="f7ee9-114">Существует два способа это сделать: указать пользовательскую привязку в конфигурации или указать пользовательскую привязку в коде, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="f7ee9-114">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
    ```csharp
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4. <span data-ttu-id="f7ee9-115">Создайте объект `WsdlImporter` и вызовите метод `ImportAllEndpoints`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="f7ee9-115">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="f7ee9-116">На данном этапе имеется коллекция конечных точек службы.</span><span class="sxs-lookup"><span data-stu-id="f7ee9-116">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="f7ee9-117">Дополнительные сведения об импорте метаданных см. [в разделе инструкции. Импорт метаданных в конечные точки службы](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="f7ee9-117">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ee9-118">См. также</span><span class="sxs-lookup"><span data-stu-id="f7ee9-118">See also</span></span>

- [<span data-ttu-id="f7ee9-119">Метаданные</span><span class="sxs-lookup"><span data-stu-id="f7ee9-119">Metadata</span></span>](../feature-details/metadata.md)
