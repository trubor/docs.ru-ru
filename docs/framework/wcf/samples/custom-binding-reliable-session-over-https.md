---
description: 'Дополнительные сведения о: настраиваемая привязка надежного сеанса по протоколу HTTPS'
title: Надежный сеанс по протоколу HTTPS с использованием пользовательской привязки
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: ed02ce8ea199b5e7ae744fb0eacf168ea5fa85df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778299"
---
# <a name="custom-binding-reliable-session-over-https"></a><span data-ttu-id="8b22a-103">Надежный сеанс по протоколу HTTPS с использованием пользовательской привязки</span><span class="sxs-lookup"><span data-stu-id="8b22a-103">Custom Binding Reliable Session over HTTPS</span></span>

<span data-ttu-id="8b22a-104">В этом образце показано использование безопасности транспорта SSL с надежными сеансами.</span><span class="sxs-lookup"><span data-stu-id="8b22a-104">This sample demonstrates the use of SSL transport security with Reliable Sessions.</span></span> <span data-ttu-id="8b22a-105">Надежные сеансы реализуют протокол WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="8b22a-105">Reliable Sessions implements the WS-Reliable Messaging protocol.</span></span> <span data-ttu-id="8b22a-106">Чтобы создать безопасный надежный сеанс, можно объединить протокол WS-Security с надежными сеансами.</span><span class="sxs-lookup"><span data-stu-id="8b22a-106">You can have a secure reliable session by composing WS-Security over Reliable Sessions.</span></span> <span data-ttu-id="8b22a-107">Но в некоторых случаях может потребоваться использовать безопасность транспорта HTTP с протоколом SSL.</span><span class="sxs-lookup"><span data-stu-id="8b22a-107">But sometimes, you may choose to instead use HTTP transport security with SSL.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8b22a-108">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="8b22a-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8b22a-109">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="8b22a-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8b22a-110">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="8b22a-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8b22a-111">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="8b22a-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a><span data-ttu-id="8b22a-112">Подробные сведения об образце</span><span class="sxs-lookup"><span data-stu-id="8b22a-112">Sample Details</span></span>  

 <span data-ttu-id="8b22a-113">Протокол SSL гарантирует защищенность пакетов.</span><span class="sxs-lookup"><span data-stu-id="8b22a-113">SSL ensures that the packets themselves are secured.</span></span> <span data-ttu-id="8b22a-114">Важно отметить, что этот подход отличается от защиты надежных сеансов с помощью протокола WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="8b22a-114">It is important to note that this is different from securing the reliable session using WS-Secure Conversation.</span></span>  
  
 <span data-ttu-id="8b22a-115">Чтобы использовать надежные сеансы поверх протокола HTTPS, необходимо создать пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="8b22a-115">To use reliable session over HTTPS, you must create a custom binding.</span></span> <span data-ttu-id="8b22a-116">Этот образец основан на [Начало работы](getting-started-sample.md) , который реализует службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="8b22a-116">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="8b22a-117">Пользовательская привязка создается с помощью элемента привязки надежного сеанса и [\<httpsTransport>](../../configure-apps/file-schema/wcf/httpstransport.md) .</span><span class="sxs-lookup"><span data-stu-id="8b22a-117">A custom binding is created using the reliable session binding element and the [\<httpsTransport>](../../configure-apps/file-schema/wcf/httpstransport.md).</span></span> <span data-ttu-id="8b22a-118">Ниже представлена конфигурация пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="8b22a-118">The following configuration is of the custom binding.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="8b22a-119">Код программы в примере идентичен службе [Начало работы](getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="8b22a-119">The program code in the sample is identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="8b22a-120">Перед построением и запуском примера необходимо с помощью мастера сертификатов веб-сервера создать и назначить сертификат.</span><span class="sxs-lookup"><span data-stu-id="8b22a-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="8b22a-121">Определения конечной точки и привязки в файле конфигурации включают использование пользовательской привязки, как показано в следующем образце файла конфигурации клиента.</span><span class="sxs-lookup"><span data-stu-id="8b22a-121">The endpoint definition and binding definition in the configuration file settings enable the use of custom binding as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"
                binding="customBinding"
                bindingConfiguration="reliableSessionOverHttps"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="8b22a-122">Указанный адрес использует `https://` схему.</span><span class="sxs-lookup"><span data-stu-id="8b22a-122">The address specified uses the `https://` scheme.</span></span>  
  
 <span data-ttu-id="8b22a-123">Так как сертификат, используемый в этом примере, является тестовым сертификатом, созданным с помощью Makecert.exe, оповещение системы безопасности появляется при попытке доступа к адресу https:, например `https://localhost/servicemodelsamples/service.svc` , из браузера.</span><span class="sxs-lookup"><span data-stu-id="8b22a-123">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="8b22a-124">Чтобы клиент Windows Communication Foundation (WCF) работал с тестовым сертификатом на месте, к клиенту был добавлен дополнительный код для подавления оповещения системы безопасности.</span><span class="sxs-lookup"><span data-stu-id="8b22a-124">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="8b22a-125">При использовании рабочих сертификатов этот код и соответствующие классы не требуются.</span><span class="sxs-lookup"><span data-stu-id="8b22a-125">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="8b22a-126">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="8b22a-126">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8b22a-127">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="8b22a-127">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8b22a-128">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="8b22a-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8b22a-129">Установите ASP.NET 4,0 с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="8b22a-129">Install  ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="8b22a-130">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8b22a-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="8b22a-131">Убедитесь, что выполнены инструкции по [установке сертификата сервера службы IIS (IIS)](iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="8b22a-131">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="8b22a-132">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8b22a-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="8b22a-133">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8b22a-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
