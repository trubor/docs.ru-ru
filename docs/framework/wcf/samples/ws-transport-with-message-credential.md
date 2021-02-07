---
description: Дополнительные сведения см. в статье Транспорт WS с учетными данными сообщений.
title: Транспорт WS с учетными данными сообщения
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 02514ad4d0bfd103126667f5ecdd21a6bc9151fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668335"
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="d1b9b-103">Транспорт WS с учетными данными сообщения</span><span class="sxs-lookup"><span data-stu-id="d1b9b-103">WS Transport With Message Credential</span></span>

<span data-ttu-id="d1b9b-104">В этом примере показано использовании безопасности транспорта SSL в сочетании с передаваемыми в сообщении учетными данными клиента.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-104">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="d1b9b-105">В этом примере используется привязка `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-105">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="d1b9b-106">По умолчанию привязка `wsHttpBinding` обеспечивает взаимодействие по протоколу HTTP.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-106">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="d1b9b-107">При настройке для безопасности транспорта привязка поддерживает взаимодействие по протоколу HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-107">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="d1b9b-108">Протокол HTTPS обеспечивает конфиденциальность и защиту целостности передаваемых по каналам связи сообщений.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-108">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="d1b9b-109">Тем не менее набор механизмов аутентификации, который можно использовать для проверки подлинности клиента при соединении со службой, ограничен механизмами, поддерживаемыми транспортом HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-109">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> <span data-ttu-id="d1b9b-110">Windows Communication Foundation (WCF) предлагает `TransportWithMessageCredential` режим безопасности, предназначенный для преодоления этого ограничения.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-110">Windows Communication Foundation (WCF) offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="d1b9b-111">Если включен этот режим безопасности, для обеспечения конфиденциальности и целостности передаваемых сообщений, а также для проверки подлинности службы, используется безопасность транспорта.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-111">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="d1b9b-112">Однако проверка подлинности клиента выполняется путем помещения учетных данных клиента непосредственно в сообщение.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-112">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="d1b9b-113">Это позволяет использовать любой тип учетных данных, поддерживаемый режимом безопасности сообщений для проверки подлинности клиента, сохраняя при этом преимущества производительности в режиме безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-113">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="d1b9b-114">В этом примере для проверки подлинности клиента на стороне службы используется тип учетных данных `UserName`.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-114">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="d1b9b-115">Этот образец основан на [Начало работы](getting-started-sample.md) , который реализует службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-115">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="d1b9b-116">В файлах конфигурации клиента и службы задана и настроена привязка `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-116">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1b9b-117">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-117">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d1b9b-118">Код программы в образце практически идентичен службе [Начало работы](getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="d1b9b-118">The program code in the sample is almost identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="d1b9b-119">Имеется одна дополнительная операция, предоставляемая контрактом службы - `GetCallerIdentity`.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-119">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="d1b9b-120">Операция возвращает вызывающей стороне имя удостоверения вызывающей стороны.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-120">This operation returns the name of the caller's identity to the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="d1b9b-121">Перед построением и запуском примера необходимо с помощью мастера сертификатов веб-сервера создать и назначить сертификат.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-121">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="d1b9b-122">Определения конечной точки и привязки в файле конфигурации устанавливают режим безопасности `TransportWithMessageCredential`, как показано в следующем примере файла конфигурации клиента.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-122">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="d1b9b-123">Указанный адрес использует `https://` схему.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-123">The address specified uses the `https://` scheme.</span></span> <span data-ttu-id="d1b9b-124">Конфигурация привязки задает режим безопасности `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-124">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="d1b9b-125">Тот же режим безопасности необходимо задать в файле Web.config службы.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-125">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="d1b9b-126">Так как сертификат, используемый в этом примере, является тестовым сертификатом, созданным с помощью Makecert.exe, оповещение системы безопасности появляется при попытке доступа к адресу https:, например  `https://localhost/servicemodelsamples/service.svc` , из браузера.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-126">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as  `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="d1b9b-127">Чтобы разрешить клиенту WCF работать с тестовым сертификатом, к клиенту был добавлен дополнительный код для подавления оповещения системы безопасности.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-127">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="d1b9b-128">При использовании рабочих сертификатов этот код и соответствующие классы не требуются.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-128">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 <span data-ttu-id="d1b9b-129">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-129">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d1b9b-130">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="d1b9b-130">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:
YourDomainName\YourAccountName  
   Enter password:
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d1b9b-131">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="d1b9b-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d1b9b-132">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1b9b-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d1b9b-133">Убедитесь, что выполнены инструкции по [установке сертификата сервера службы IIS (IIS)](iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="d1b9b-133">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>  
  
3. <span data-ttu-id="d1b9b-134">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1b9b-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="d1b9b-135">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1b9b-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
