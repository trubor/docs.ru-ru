---
description: 'Дополнительные сведения: пример безопасности сообщений'
title: Пример безопасности сообщений
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: adec9df3b2a3b5ba022ec2123a8d90d85869246b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752305"
---
# <a name="message-security-sample"></a><span data-ttu-id="d4dd3-103">Пример безопасности сообщений</span><span class="sxs-lookup"><span data-stu-id="d4dd3-103">Message Security Sample</span></span>

<span data-ttu-id="d4dd3-104">Данный образец демонстрирует реализацию приложения, в котором используется привязка `basicHttpBinding` и безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-104">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="d4dd3-105">Этот образец основан на [Начало работы](getting-started-sample.md) , который реализует службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4dd3-106">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d4dd3-107">Режим безопасности `basicHttpBinding` может быть установлен в следующие значения: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` и `None`.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-107">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="d4dd3-108">В следующем образце файла службы App.config, в определении конечной точки задаются привязка `basicHttpBinding` и ссылки на конфигурацию привязки с именем `Binding1`, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-108">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="d4dd3-109">Конфигурация привязки задает `mode` атрибуту значение [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `Message` и задает атрибуту в значение, `clientCredentialType` [\<message>](../../configure-apps/file-schema/wcf/message-of-basichttpbinding.md) `Certificate` как показано в следующем образце конфигурации:</span><span class="sxs-lookup"><span data-stu-id="d4dd3-109">The binding configuration sets the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="d4dd3-110">Сертификат, используемый службой для проверки своей подлинности при подключении к клиенту, установлен в разделе поведений элемента `serviceCredentials` файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-110">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="d4dd3-111">Режим проверки, применяемый к сертификату, который клиент использует для проверки своей подлинности при подключении к службе, также задается в разделе поведений элемента `clientCertificate`.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-111">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="d4dd3-112">Та же привязка и данные безопасности задаются в файле конфигурации клиента.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-112">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="d4dd3-113">Идентификация абонента отображается в окне консоли службы с помощью следующего кода.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-113">The identity of the caller is displayed in the service console window by using the following code:</span></span>  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 <span data-ttu-id="d4dd3-114">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d4dd3-115">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-115">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="d4dd3-116">Настройка и сборка образца</span><span class="sxs-lookup"><span data-stu-id="d4dd3-116">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="d4dd3-117">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4dd3-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d4dd3-118">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4dd3-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="d4dd3-119">Запуск образца на том же компьютере</span><span class="sxs-lookup"><span data-stu-id="d4dd3-119">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="d4dd3-120">Запустите файл Setup.bat из папки установки примера.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-120">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="d4dd3-121">При этом устанавливаются все сертификаты, необходимые для выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-121">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d4dd3-122">Пакетный файл Setup.bat предназначен для запуска из командной строки Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-122">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="d4dd3-123">Требуется, чтобы переменная среды MSSDK указывала на каталог, в котором установлен пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-123">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="d4dd3-124">Эта переменная среды автоматически устанавливается в командной строке Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-124">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2. <span data-ttu-id="d4dd3-125">Запустите приложение службы из \service\bin.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-125">Run the service application from \service\bin.</span></span>  
  
3. <span data-ttu-id="d4dd3-126">Запустите клиентское приложение из \service\bin.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-126">Run the client application from \client\bin.</span></span> <span data-ttu-id="d4dd3-127">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-127">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="d4dd3-128">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d4dd3-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
5. <span data-ttu-id="d4dd3-129">После завершения работы образца запустите файл Cleanup.bat, чтобы удалить сертификаты.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-129">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="d4dd3-130">В других образцах обеспечения безопасности используются те же сертификаты.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-130">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="d4dd3-131">Выполнение примера на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="d4dd3-131">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="d4dd3-132">Создайте на компьютере службы каталог для двоичных файлов службы.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-132">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="d4dd3-133">Скопируйте файлы программ службы из каталога службы на сервер.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-133">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="d4dd3-134">Также скопируйте на сервер файлы Setup.bat, Cleanup.bat и ImportClientCert.bat.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-134">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3. <span data-ttu-id="d4dd3-135">Создайте на клиентском компьютере каталог для двоичных файлов клиента.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-135">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="d4dd3-136">Скопируйте в клиентский каталог на клиентском компьютере файлы программы клиента.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-136">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="d4dd3-137">Кроме того, скопируйте на клиент файлы Setup.bat, Cleanup.bat и ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-137">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="d4dd3-138">На сервере выполните команду `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-138">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="d4dd3-139">`setup.bat`При запуске с `service` аргументом создается сертификат службы с полным доменным именем компьютера и экспортируется сертификат службы в файл с именем Service. cer.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-139">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="d4dd3-140">Измените Service.exe.config, чтобы отразить новое имя сертификата (в `findValue` атрибуте [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) элемента), совпадающее с полным доменным именем компьютера.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-140">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="d4dd3-141">Также измените значение базового адреса для указания полного доменного имени компьютера вместо localhost`.`</span><span class="sxs-lookup"><span data-stu-id="d4dd3-141">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7. <span data-ttu-id="d4dd3-142">Скопируйте файл Service.cer из каталога службы в клиентский каталог на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-142">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="d4dd3-143">На клиенте выполните команду `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-143">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="d4dd3-144">При выполнении команды `setup.bat`с аргументом `client` создается сертификат клиента с именем client.com, который экспортируется в файл с именем Client.cer.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-144">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="d4dd3-145">В файле Client.exe.config на клиентском компьютере измените значение адреса конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-145">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="d4dd3-146">Для этого замените имя localhost полным именем домена сервера.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-146">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="d4dd3-147">Также измените `findValue` атрибут объекта на [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) новое имя сертификата службы, которое является полным доменным именем сервера.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-147">Also change the `findValue` attribute of the [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="d4dd3-148">Скопируйте файл Client.cer из клиентского каталога в каталог службы на сервере.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-148">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="d4dd3-149">Запустите на клиенте файл ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-149">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="d4dd3-150">Он импортирует сертификат службы из файла Service.cer в хранилище CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-150">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="d4dd3-151">На сервере запустите файл ImportClientCert.bat. Он импортирует сертификат клиента из файла Client.cer в хранилище LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-151">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="d4dd3-152">Запустите программу Service.exe из командной строки на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-152">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="d4dd3-153">На клиентском компьютере из окна командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-153">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1. <span data-ttu-id="d4dd3-154">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d4dd3-154">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="d4dd3-155">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="d4dd3-155">To clean up after the sample</span></span>  
  
- <span data-ttu-id="d4dd3-156">После завершения работы примера запустите в папке примеров файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-156">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d4dd3-157">Этот скрипт не удаляет сертификаты службы на клиенте при выполнении примера на нескольких компьютерах.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-157">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="d4dd3-158">Если вы выполнили примеры Windows Communication Foundation (WCF), использующие сертификаты на разных компьютерах, обязательно очистите сертификаты службы, установленные в хранилище CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-158">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="d4dd3-159">Для этого воспользуйтесь следующей командой: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Пример: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="d4dd3-159">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d4dd3-160">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-160">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4dd3-161">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="d4dd3-161">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d4dd3-162">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-162">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4dd3-163">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="d4dd3-163">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`
