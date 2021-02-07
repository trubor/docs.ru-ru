---
description: Дополнительные сведения о сертификате безопасности сообщений
title: Сертификат безопасности сообщений
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 6ed48466d0b5155a5f14a2ec2eae0d879b7377a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732440"
---
# <a name="message-security-certificate"></a><span data-ttu-id="c3d12-103">Сертификат безопасности сообщений</span><span class="sxs-lookup"><span data-stu-id="c3d12-103">Message Security Certificate</span></span>

<span data-ttu-id="c3d12-104">В этом образце показано, как реализовать приложение, использующее протокол WS-Security и проверку подлинности с использованием сертификата X.509 v3 для клиента и требующее проверки подлинности сервера с использованием сертификата X.509 v3 сервера.</span><span class="sxs-lookup"><span data-stu-id="c3d12-104">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="c3d12-105">В этом образце используются параметры по умолчанию, обеспечивающие подписывание и шифрование всех сообщений приложения, которыми обмениваются клиент и сервер.</span><span class="sxs-lookup"><span data-stu-id="c3d12-105">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="c3d12-106">Этот пример основан на [WSHttpBinding](wshttpbinding.md) и состоит из клиентской консольной программы и библиотеки служб, размещенной службы IIS (IIS).</span><span class="sxs-lookup"><span data-stu-id="c3d12-106">This sample is based on the [WSHttpBinding](wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="c3d12-107">Служба реализует контракт, определяющий шаблон взаимодействия "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="c3d12-107">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3d12-108">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="c3d12-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c3d12-109">В этом образце демонстрируется управление проверкой подлинности с помощью файла конфигурации, а также получение удостоверения вызывающего объекта из контекста безопасности, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="c3d12-109">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  

```csharp
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="c3d12-110">Служба предоставляет одну конечную точку для взаимодействия со службой и одну конечную точку для предоставления документа WSDL службы с использованием протокола WS-MetadataExchange, определенного с помощью файла конфигурации (Web.config).</span><span class="sxs-lookup"><span data-stu-id="c3d12-110">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="c3d12-111">Конечная точка состоит из адреса, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="c3d12-111">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="c3d12-112">Привязка настраивается с помощью стандартного [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) элемента, который по умолчанию использует безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="c3d12-112">The binding is configured with a standard [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="c3d12-113">В этом образце атрибуту `clientCredentialType` присваивается значение Certificate для запроса проверки подлинности клиента.</span><span class="sxs-lookup"><span data-stu-id="c3d12-113">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
```xml  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="c3d12-114">Поведение задает учетные данные службы, используемые при проверке подлинности службы клиентом.</span><span class="sxs-lookup"><span data-stu-id="c3d12-114">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="c3d12-115">Имя субъекта сертификата сервера указывается в `findValue` атрибуте [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="c3d12-115">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="c3d12-116">Конфигурация конечной точки клиента состоит из абсолютного адреса конечной точки службы, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="c3d12-116">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="c3d12-117">Привязка клиента настраивается с помощью соответствующих режимов безопасности и проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="c3d12-117">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="c3d12-118">Если сценарий выполняется на нескольких компьютерах, убедитесь, что адрес конечной точки службы изменен соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="c3d12-118">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="c3d12-119">Реализация клиента позволяет задать сертификат для использования посредством файла конфигурации или кода.</span><span class="sxs-lookup"><span data-stu-id="c3d12-119">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="c3d12-120">В следующем образце показано, как задать сертификат для использования в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c3d12-120">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="c3d12-121">В следующем образце показано, как вызвать службу в программе.</span><span class="sxs-lookup"><span data-stu-id="c3d12-121">The following sample shows how to call the service in your program.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 <span data-ttu-id="c3d12-122">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="c3d12-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c3d12-123">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="c3d12-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="c3d12-124">Пакетный файл Setup.bat, входящий в состав образцов реализации безопасности сообщений, позволяет настроить для клиента и сервера соответствующие сертификаты, необходимые для выполнения размещенного приложения, для которого требуется обеспечение безопасности на основе сертификата.</span><span class="sxs-lookup"><span data-stu-id="c3d12-124">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="c3d12-125">Пакетный файл можно выполнять в трех режимах.</span><span class="sxs-lookup"><span data-stu-id="c3d12-125">The batch file can be run in three modes.</span></span> <span data-ttu-id="c3d12-126">Для запуска в режиме одного компьютера введите **setup.bat** в Командная строка разработчика для Visual Studio. для типа режима обслуживания **setup.bat Service**; и для типа клиента **setup.bat клиент**.</span><span class="sxs-lookup"><span data-stu-id="c3d12-126">To run in single-computer mode type **setup.bat** in a Developer Command Prompt for Visual Studio ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="c3d12-127">Режимы клиента и сервера используются для выполнения образца на нескольких компьютерах.</span><span class="sxs-lookup"><span data-stu-id="c3d12-127">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="c3d12-128">Подробные сведения см. в описании процедуры настройки в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="c3d12-128">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="c3d12-129">Ниже представлен краткий обзор различных разделов пакетных файлов, позволяющий изменять их для выполнения в соответствующей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c3d12-129">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
- <span data-ttu-id="c3d12-130">Создание сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="c3d12-130">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="c3d12-131">Следующая строка пакетного файла создает сертификат клиента.</span><span class="sxs-lookup"><span data-stu-id="c3d12-131">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="c3d12-132">В качестве имени субъекта создаваемого сертификата используется указанное имя клиента.</span><span class="sxs-lookup"><span data-stu-id="c3d12-132">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="c3d12-133">Сертификат сохраняется в хранилище `My` в расположении `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="c3d12-133">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="c3d12-134">Установка сертификата клиента в хранилище доверенных сертификатов сервера.</span><span class="sxs-lookup"><span data-stu-id="c3d12-134">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="c3d12-135">Следующая строка пакетного файла копирует сертификат клиента в хранилище TrustedPeople сервера, чтобы сервер мог принимать соответствующие решения о доверии или недоверии.</span><span class="sxs-lookup"><span data-stu-id="c3d12-135">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="c3d12-136">Чтобы сертификат, установленный в хранилище TrustedPeople, был доверенным для службы Windows Communication Foundation (WCF), режим проверки сертификата клиента должен быть установлен в значение `PeerOrChainTrust` или `PeerTrust` .</span><span class="sxs-lookup"><span data-stu-id="c3d12-136">In order for a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="c3d12-137">Чтобы узнать, как это сделать с помощью файла конфигурации, см. приведенный выше образец конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="c3d12-137">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```  
  
- <span data-ttu-id="c3d12-138">Создание сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="c3d12-138">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="c3d12-139">Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="c3d12-139">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="c3d12-140">Переменная %SERVER_NAME% задает имя сервера.</span><span class="sxs-lookup"><span data-stu-id="c3d12-140">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="c3d12-141">Сертификат хранится в хранилище LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="c3d12-141">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="c3d12-142">Если пакетный файл Setup.bat запускается с аргументом service (например, **setup.bat Service**), то% server_name% содержит полное доменное имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="c3d12-142">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="c3d12-143">В противном случае по умолчанию используется значение localhost.</span><span class="sxs-lookup"><span data-stu-id="c3d12-143">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="c3d12-144">Установка сертификата сервера в хранилище доверенных сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="c3d12-144">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="c3d12-145">Следующая строка копирует сертификат сервера в хранилище доверенных лиц клиента.</span><span class="sxs-lookup"><span data-stu-id="c3d12-145">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="c3d12-146">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы.</span><span class="sxs-lookup"><span data-stu-id="c3d12-146">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="c3d12-147">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="c3d12-147">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="c3d12-148">Предоставление разрешений в отношении закрытого ключа сертификата.</span><span class="sxs-lookup"><span data-stu-id="c3d12-148">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="c3d12-149">Следующие строки в файле Setup.bat делают сертификат сервера, хранящийся в хранилище LocalMachine, доступным для учетной записи рабочего процесса ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c3d12-149">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="c3d12-150">Если используется не-U. S. Английской версии Windows, необходимо изменить файл Setup.bat и заменить имя учетной записи NT AUTHORITY\NETWORK SERVICE своим региональным эквивалентом.</span><span class="sxs-lookup"><span data-stu-id="c3d12-150">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3d12-151">Средства, используемые в этом пакетном файле, расположены в каталоге C:\Program Files\Microsoft Visual Studio 8\Common7\tools или C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span><span class="sxs-lookup"><span data-stu-id="c3d12-151">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="c3d12-152">Один из этих каталогов должен быть указан в системном пути.</span><span class="sxs-lookup"><span data-stu-id="c3d12-152">One of these directories must be in your system path.</span></span> <span data-ttu-id="c3d12-153">Если у вас установлена Visual Studio, самый простой способ получить этот каталог в пути — открыть Командная строка разработчика для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3d12-153">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="c3d12-154">Нажмите кнопку **Пуск** и выберите **все программы**, **Visual Studio 2012**, **инструменты**.</span><span class="sxs-lookup"><span data-stu-id="c3d12-154">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="c3d12-155">В командной строке уже должны быть настроены соответствующие пути.</span><span class="sxs-lookup"><span data-stu-id="c3d12-155">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="c3d12-156">В противном случае необходимо вручную добавить соответствующий каталог в путь.</span><span class="sxs-lookup"><span data-stu-id="c3d12-156">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c3d12-157">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="c3d12-157">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c3d12-158">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="c3d12-158">Check for the following (default) directory before continuing:</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c3d12-159">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="c3d12-159">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3d12-160">Этот образец находится в следующем каталоге:</span><span class="sxs-lookup"><span data-stu-id="c3d12-160">This sample is located in the following directory:</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c3d12-161">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="c3d12-161">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c3d12-162">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c3d12-162">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c3d12-163">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c3d12-163">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="c3d12-164">Запуск образца на одном компьютере</span><span class="sxs-lookup"><span data-stu-id="c3d12-164">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="c3d12-165">Откройте Командная строка разработчика для Visual Studio с правами администратора и запустите Setup.bat из примера установочной папки.</span><span class="sxs-lookup"><span data-stu-id="c3d12-165">Open a Developer Command Prompt for Visual Studio  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="c3d12-166">При этом устанавливаются все сертификаты, необходимые для выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="c3d12-166">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c3d12-167">Пакетный файл Setup.bat предназначен для запуска из Командная строка разработчика для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3d12-167">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="c3d12-168">Необходимо, чтобы переменная среды path указывала на каталог, в котором установлен пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="c3d12-168">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="c3d12-169">Эта переменная среды автоматически задается в Командная строка разработчика для Visual Studio (2010).</span><span class="sxs-lookup"><span data-stu-id="c3d12-169">This environment variable is automatically set within a Developer Command Prompt for Visual Studio (2010).</span></span>  
  
2. <span data-ttu-id="c3d12-170">Проверьте доступ к службе с помощью браузера, введя адрес `http://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="c3d12-170">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3. <span data-ttu-id="c3d12-171">Запустите программу Client.exe из каталога \client\bin.</span><span class="sxs-lookup"><span data-stu-id="c3d12-171">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="c3d12-172">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="c3d12-172">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="c3d12-173">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c3d12-173">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="c3d12-174">Запуск образца на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="c3d12-174">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="c3d12-175">Создайте каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="c3d12-175">Create a directory on the service computer.</span></span> <span data-ttu-id="c3d12-176">Создайте для этого каталога виртуальное приложение servicemodelsamples, с помощью средства управления службами IIS.</span><span class="sxs-lookup"><span data-stu-id="c3d12-176">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="c3d12-177">Скопируйте файлы служебной программы из каталога «\inetpub\wwwroot\servicemodelsamples» в виртуальный каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="c3d12-177">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="c3d12-178">Убедитесь, что скопированы все файлы из подкаталога \bin.</span><span class="sxs-lookup"><span data-stu-id="c3d12-178">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="c3d12-179">Также скопируйте файлы Setup.bat, Cleanup.bat и ImportClientCert.bat на компьютер службы.</span><span class="sxs-lookup"><span data-stu-id="c3d12-179">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="c3d12-180">Создайте на клиентском компьютере каталог для двоичных файлов клиента.</span><span class="sxs-lookup"><span data-stu-id="c3d12-180">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="c3d12-181">Скопируйте в клиентский каталог на клиентском компьютере файлы программы клиента.</span><span class="sxs-lookup"><span data-stu-id="c3d12-181">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="c3d12-182">Кроме того, скопируйте на клиент файлы Setup.bat, Cleanup.bat и ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="c3d12-182">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="c3d12-183">На сервере запустите **службуsetup.bat** в Командная строка разработчика для Visual Studio с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="c3d12-183">On the server, run **setup.bat service** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="c3d12-184">При запуске **setup.bat** с аргументом **службы** создается сертификат службы с полным доменным именем компьютера и экспортируется сертификат службы в файл с именем Service. cer.</span><span class="sxs-lookup"><span data-stu-id="c3d12-184">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="c3d12-185">Измените Web.config, чтобы отразить новое имя сертификата (в `findValue` атрибуте в [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), совпадающее с полным доменным именем компьютера.</span><span class="sxs-lookup"><span data-stu-id="c3d12-185">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="c3d12-186">Скопируйте файл Service.cer из каталога службы в клиентский каталог на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="c3d12-186">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="c3d12-187">На клиенте запустите **setup.bat клиент** в Командная строка разработчика для Visual Studio с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="c3d12-187">On the client, run **setup.bat client** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="c3d12-188">При выполнении **setup.bat** с аргументом **клиента** создается сертификат клиента с именем Client.com и экспортируется сертификат клиента в файл с именем Client. cer.</span><span class="sxs-lookup"><span data-stu-id="c3d12-188">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="c3d12-189">В файле Client.exe.config на клиентском компьютере измените значение адреса конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="c3d12-189">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="c3d12-190">Для этого замените имя localhost полным доменным именем сервера.</span><span class="sxs-lookup"><span data-stu-id="c3d12-190">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="c3d12-191">Скопируйте файл Client.cer из клиентского каталога в каталог службы на сервере.</span><span class="sxs-lookup"><span data-stu-id="c3d12-191">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="c3d12-192">На клиенте запустите ImportServiceCert.bat в Командная строка разработчика для Visual Studio с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="c3d12-192">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="c3d12-193">Он импортирует сертификат службы из файла Service.cer в хранилище CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="c3d12-193">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="c3d12-194">На сервере запустите ImportClientCert.bat в Командная строка разработчика для Visual Studio с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="c3d12-194">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="c3d12-195">При этом импортируется сертификат клиента из файла Client.cer в хранилище «LocalMachine - TrustedPeople».</span><span class="sxs-lookup"><span data-stu-id="c3d12-195">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="c3d12-196">На клиентском компьютере из окна командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="c3d12-196">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="c3d12-197">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c3d12-197">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="c3d12-198">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="c3d12-198">To clean up after the sample</span></span>  
  
- <span data-ttu-id="c3d12-199">После завершения работы образца запустите в папке образцов файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="c3d12-199">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c3d12-200">Этот скрипт не удаляет сертификаты службы на клиенте при запуске образца на нескольких компьютерах.</span><span class="sxs-lookup"><span data-stu-id="c3d12-200">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="c3d12-201">Если вы выполнили примеры Windows Communication Foundation (WCF), использующие сертификаты на нескольких компьютерах, обязательно очистите сертификаты службы, установленные в хранилище CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="c3d12-201">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="c3d12-202">Для этого воспользуйтесь следующей командой: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Например: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="c3d12-202">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
