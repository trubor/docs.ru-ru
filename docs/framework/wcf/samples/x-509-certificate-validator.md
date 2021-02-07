---
description: Дополнительные сведения о средстве проверки сертификатов X. 509
title: Проверяющий элемент управления для сертификатов X.509
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: 3fead47cab4d639640f5af755717636ca2e8d01e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726238"
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="92816-103">Проверяющий элемент управления для сертификатов X.509</span><span class="sxs-lookup"><span data-stu-id="92816-103">X.509 Certificate Validator</span></span>

<span data-ttu-id="92816-104">В этом образце показано, как реализовать пользовательский проверяющий элемент управления для сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="92816-104">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="92816-105">Это бывает полезным в случаях, когда ни один из встроенных режимов проверки сертификатов X.509 не соответствует требованиям приложения.</span><span class="sxs-lookup"><span data-stu-id="92816-105">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="92816-106">В этом образце показана служба, содержащая пользовательский проверяющий элемент управления, который принимает самостоятельно выданные сертификаты.</span><span class="sxs-lookup"><span data-stu-id="92816-106">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="92816-107">Клиент использует такие сертификаты для проверки подлинности службы.</span><span class="sxs-lookup"><span data-stu-id="92816-107">The client uses such a certificate to authenticate to the service.</span></span>

<span data-ttu-id="92816-108">Примечание. Поскольку выдаваемый самостоятельно сертификат может создаваться кем угодно, используемый службой пользовательский проверяющий элемент управления менее безопасен по сравнению с поведением по умолчанию, которое предоставляется режимом ChainTrust X509CertificateValidationMode.</span><span class="sxs-lookup"><span data-stu-id="92816-108">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="92816-109">Перед использованием логики проверки в рабочей среде следует внимательно изучить связанные с этим проблемы безопасности.</span><span class="sxs-lookup"><span data-stu-id="92816-109">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>

<span data-ttu-id="92816-110">Таким образом, в этом образце демонстрируются указанные ниже возможности.</span><span class="sxs-lookup"><span data-stu-id="92816-110">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="92816-111">Подлинность клиента может проверяться с помощью сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="92816-111">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="92816-112">Сервер проверяет учетные данные клиента с помощью пользовательского элемента X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="92816-112">The server validates the client credentials against a custom X509CertificateValidator.</span></span>

- <span data-ttu-id="92816-113">Сервер проходит проверку подлинности с использованием сертификата X.509 сервера.</span><span class="sxs-lookup"><span data-stu-id="92816-113">The server is authenticated using the server's X.509 certificate.</span></span>

<span data-ttu-id="92816-114">Служба предоставляет одну конечную точку для взаимодействия с нею; она определяется в файле конфигурации App.config. Конечная точка состоит из адреса, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="92816-114">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="92816-115">Привязка настроена со стандартом `wsHttpBinding` , который по умолчанию использует `WSSecurity` и проверку подлинности сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-115">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="92816-116">В поведении службы задается пользовательский режим проверки сертификатов X.509 клиентов, а также тип класса проверяющего элемента управления.</span><span class="sxs-lookup"><span data-stu-id="92816-116">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="92816-117">Коме того, поведение с помощью элемента serviceCertificate задает сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="92816-117">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="92816-118">Сертификат сервера должен содержать то же значение, `SubjectName` что и `findValue` в [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="92816-118">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- use host/baseAddresses to configure base address -->
        <!-- provided by host -->
        <host>
          <baseAddresses>
            <add baseAddress =
                "http://localhost:8001/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address specified above, provide one endpoint -->
        <endpoint address="certificate"
               binding="wsHttpBinding"
               bindingConfiguration="Binding"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <!-- X509 certificate binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults ="true"/>
          <serviceCredentials>
            <!-- The serviceCredentials behavior allows one -->
            <!-- to specify authentication constraints on -->
            <!-- client certificates. -->
            <clientCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- Custom means that if the custom -->
              <!-- X509CertificateValidator does NOT throw -->
              <!-- an exception, then the provided certificate -->
              <!-- will be trusted without performing any -->
              <!-- validation beyond that performed by the custom -->
              <!-- validator. The security implications of this -->
              <!-- setting should be carefully considered before -->
              <!-- using Custom in production code. -->
              <authentication
                 certificateValidationMode="Custom"
                 customCertificateValidatorType =
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />
            </clientCertificate>
            <!-- The serviceCredentials behavior allows one to -->
            <!-- define a service certificate. -->
            <!-- A service certificate is used by a client to -->
            <!-- authenticate the service and provide message -->
            <!-- protection. This configuration references the -->
            <!-- "localhost" certificate installed during the setup -->
            <!-- instructions. -->
            <serviceCertificate findValue="localhost"
                 storeLocation="LocalMachine"
                 storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
      </system.serviceModel>
```

<span data-ttu-id="92816-119">Конфигурация конечной точки клиента состоит из имени конфигурации, абсолютного адреса конечной точки службы, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="92816-119">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="92816-120">Привязка клиента настраивается с помощью соответствующего режима и `clientCredentialType` сообщения.</span><span class="sxs-lookup"><span data-stu-id="92816-120">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
    <client>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
        address=
        "http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>
    <bindings>
        <wsHttpBinding>
            <!-- X509 certificate binding -->
            <binding name="Binding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
               </security>
            </binding>
       </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- PeerOrChainTrust means that if the certificate -->
              <!-- is in the user's Trusted People store, then it -->
              <!-- is trusted without performing a validation of -->
              <!-- the certificate's issuer chain. -->
              <!-- This setting is used here for convenience so -->
              <!-- that the sample can be run without having to -->
              <!-- have certificates issued by a certification -->
              <!-- authority (CA). This setting is less secure -->
              <!-- than the default, ChainTrust. The security -->
              <!-- implications of this setting should be -->
              <!-- carefully considered before using -->
              <!-- PeerOrChainTrust in production code.-->
              <authentication
                  certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>
```

<span data-ttu-id="92816-121">Реализация клиента задает используемый сертификат клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-121">The client implementation sets the client certificate to use.</span></span>

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client = new CalculatorClient("Certificate");
try
{
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

    // Call the Subtract service operation.
    value1 = 145.00D;
    value2 = 76.54D;
    result = client.Subtract(value1, value2);
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

    // Call the Multiply service operation.
    value1 = 9.00D;
    value2 = 81.25D;
    result = client.Multiply(value1, value2);
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

    // Call the Divide service operation.
    value1 = 22.00D;
    value2 = 7.00D;
    result = client.Divide(value1, value2);
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
    client.Close();
}
catch (TimeoutException e)
{
    Console.WriteLine("Call timed out : {0}", e.Message);
    client.Abort();
}
catch (CommunicationException e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
```

<span data-ttu-id="92816-122">В этом образце для проверки сертификатов используется пользовательский элемент X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="92816-122">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="92816-123">В образце реализуется элемент CustomX509CertificateValidator, унаследованный от <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="92816-123">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="92816-124">Дополнительные сведения см. в документации по <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="92816-124">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="92816-125">В данном образце пользовательского элемента управления реализуется метод Validate, принимающий все выданные самостоятельно сертификаты X.509, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="92816-125">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>

```csharp
public class CustomX509CertificateValidator : X509CertificateValidator
{
  public override void Validate ( X509Certificate2 certificate )
  {
   // Only accept self-issued certificates
   if (certificate.Subject != certificate.Issuer)
     throw new Exception("Certificate is not self-issued");
   }
}
```

 <span data-ttu-id="92816-126">После реализации в коде службы проверяющего элемента управления необходимо проинформировать узел службы о проверяющем элементе управления, который следует использовать.</span><span class="sxs-lookup"><span data-stu-id="92816-126">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="92816-127">Для этого можно воспользоваться следующим фрагментом кода.</span><span class="sxs-lookup"><span data-stu-id="92816-127">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 <span data-ttu-id="92816-128">Либо можно решить эту же задачу с помощью файла конфигурации, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="92816-128">Or you can do the same thing in configuration as follows.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
     <behavior name="CalculatorServiceBehavior">
       ...
   <serviceCredentials>
    <!--The serviceCredentials behavior allows one to specify -->
    <!--authentication constraints on client certificates.-->
    <clientCertificate>
    <!-- Setting the certificateValidationMode to Custom means -->
    <!--that if the custom X509CertificateValidator does NOT -->
    <!--throw an exception, then the provided certificate will -->
    <!--be trusted without performing any validation beyond that -->
    <!--performed by the custom validator. The security -->
    <!--implications of this setting should be carefully -->
    <!--considered before using Custom in production code. -->
    <authentication certificateValidationMode="Custom"
       customCertificateValidatorType =
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />
   </clientCertificate>
   </serviceCredentials>
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="92816-129">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-129">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="92816-130">Клиент должен успешно вызывать все методы.</span><span class="sxs-lookup"><span data-stu-id="92816-130">The client should successfully call all the methods.</span></span> <span data-ttu-id="92816-131">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-131">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="92816-132">Пакетный файл Setup</span><span class="sxs-lookup"><span data-stu-id="92816-132">Setup Batch File</span></span>

<span data-ttu-id="92816-133">Входящий в состав образца файл Setup.bat позволяет настроить для сервера соответствующие сертификаты, необходимые для выполнения резидентного приложения, которое требует обеспечения безопасности на основе сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="92816-133">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="92816-134">Этот пакетный файл необходимо изменить, чтобы его можно было использовать на нескольких компьютерах или без размещения приложения.</span><span class="sxs-lookup"><span data-stu-id="92816-134">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

<span data-ttu-id="92816-135">Ниже представлен краткие общие сведения о различных разделах пакетных файлов, позволяющий изменять их для выполнения в соответствующей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="92816-135">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="92816-136">Создание сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="92816-136">Creating the server certificate:</span></span>

     <span data-ttu-id="92816-137">Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="92816-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="92816-138">Переменная %SERVER_NAME% задает имя сервера.</span><span class="sxs-lookup"><span data-stu-id="92816-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="92816-139">Измените эту переменную, чтобы задать собственное имя сервера.</span><span class="sxs-lookup"><span data-stu-id="92816-139">Change this variable to specify your own server name.</span></span> <span data-ttu-id="92816-140">Значением по умолчанию является localhost.</span><span class="sxs-lookup"><span data-stu-id="92816-140">The default value is localhost.</span></span>

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="92816-141">Установка сертификата сервера в хранилище доверенных сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-141">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="92816-142">Следующие строки из файла Setup.bat копируют сертификат сервера в хранилище доверенных лиц клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-142">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="92816-143">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы.</span><span class="sxs-lookup"><span data-stu-id="92816-143">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="92816-144">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="92816-144">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="92816-145">Создание сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-145">Creating the client certificate:</span></span>

     <span data-ttu-id="92816-146">Следующие строки из файла Setup.bat создают сертификат клиента, который будет использоваться.</span><span class="sxs-lookup"><span data-stu-id="92816-146">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="92816-147">Переменная %USER_NAME% задает имя клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-147">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="92816-148">Эта переменная имеет значение "test1", поскольку код клиента ищет именно это имя.</span><span class="sxs-lookup"><span data-stu-id="92816-148">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="92816-149">Если изменить значение переменной %USER_NAME%, необходимо изменить и соответствующее значение в файле Client.cs и повторить построение клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-149">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>

     <span data-ttu-id="92816-150">Сертификат хранится в хранилище "My store" (Личном хранилище) в расположении CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="92816-150">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="92816-151">Установка сертификата клиента в хранилище доверенных сертификатов сервера.</span><span class="sxs-lookup"><span data-stu-id="92816-151">Installing the client certificate into server's trusted certificate store:</span></span>

     <span data-ttu-id="92816-152">Следующие строки из файла Setup.bat копируют сертификат клиента в хранилище доверенных лиц.</span><span class="sxs-lookup"><span data-stu-id="92816-152">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="92816-153">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны серверной системы.</span><span class="sxs-lookup"><span data-stu-id="92816-153">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="92816-154">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата клиента в хранилище сертификатов сервера не требуется.</span><span class="sxs-lookup"><span data-stu-id="92816-154">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="92816-155">Настройка и сборка образца</span><span class="sxs-lookup"><span data-stu-id="92816-155">To set up and build the sample</span></span>

1. <span data-ttu-id="92816-156">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92816-156">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="92816-157">Чтобы запустить образец на одном или нескольких компьютерах, следуйте приведенным далее инструкциям.</span><span class="sxs-lookup"><span data-stu-id="92816-157">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="92816-158">Запуск образца на одном компьютере</span><span class="sxs-lookup"><span data-stu-id="92816-158">To run the sample on the same computer</span></span>

1. <span data-ttu-id="92816-159">Запустите Setup.bat из папки примера установки в командной строке Visual Studio 2012, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="92816-159">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="92816-160">При этом устанавливаются все сертификаты, необходимые для выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="92816-160">This installs all the certificates required for running the sample.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="92816-161">Пакетный файл Setup.bat предназначен для запуска из командной строки Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="92816-161">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="92816-162">Переменная среды PATH, заданная в командной строке Visual Studio 2012, указывает на каталог, содержащий исполняемые файлы, необходимые для скрипта Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="92816-162">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

2. <span data-ttu-id="92816-163">Запустите программу Service.exe из папки service\bin.</span><span class="sxs-lookup"><span data-stu-id="92816-163">Launch Service.exe from service\bin.</span></span>

3. <span data-ttu-id="92816-164">Запустите программу Client.exe из каталога \client\bin.</span><span class="sxs-lookup"><span data-stu-id="92816-164">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="92816-165">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-165">Client activity is displayed on the client console application.</span></span>

4. <span data-ttu-id="92816-166">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="92816-166">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="92816-167">Запуск образца на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="92816-167">To run the sample across computers</span></span>

1. <span data-ttu-id="92816-168">Создайте каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="92816-168">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="92816-169">Скопируйте файлы служебной программы из каталога \service\bin в виртуальный каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="92816-169">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="92816-170">Кроме того, скопируйте на компьютер службы файлы Setup.bat, Cleanup.bat, GetComputerName.vbs и ImportClientCert.bat.</span><span class="sxs-lookup"><span data-stu-id="92816-170">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="92816-171">Создайте на клиентском компьютере каталог для двоичных файлов клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-171">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="92816-172">Скопируйте в клиентский каталог на клиентском компьютере файлы программы клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-172">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="92816-173">Кроме того, скопируйте на клиент файлы Setup.bat, Cleanup.bat и ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="92816-173">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="92816-174">На сервере запустите `setup.bat service` в Командная строка разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="92816-174">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="92816-175">`setup.bat`При запуске с `service` аргументом создается сертификат службы с полным доменным именем компьютера и экспортируется сертификат службы в файл с именем Service. cer.</span><span class="sxs-lookup"><span data-stu-id="92816-175">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>

6. <span data-ttu-id="92816-176">Измените Service.exe.config, чтобы отразить новое имя сертификата (в `findValue` атрибуте в [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), совпадающее с полным доменным именем компьютера.</span><span class="sxs-lookup"><span data-stu-id="92816-176">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="92816-177">Также измените имя компьютера в \<service> / \<baseAddresses> элементе с localhost на полное имя компьютера службы.</span><span class="sxs-lookup"><span data-stu-id="92816-177">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="92816-178">Скопируйте файл Service.cer из каталога службы в клиентский каталог на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="92816-178">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="92816-179">На клиенте запустите `setup.bat client` в Командная строка разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="92816-179">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="92816-180">При выполнении команды `setup.bat`с аргументом `client` создается сертификат клиента с именем client.com, который экспортируется в файл с именем Client.cer.</span><span class="sxs-lookup"><span data-stu-id="92816-180">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>

9. <span data-ttu-id="92816-181">В файле Client.exe.config на клиентском компьютере измените значение адреса конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="92816-181">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="92816-182">Для этого замените имя localhost полным доменным именем сервера.</span><span class="sxs-lookup"><span data-stu-id="92816-182">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>

10. <span data-ttu-id="92816-183">Скопируйте файл Client.cer из клиентского каталога в каталог службы на сервере.</span><span class="sxs-lookup"><span data-stu-id="92816-183">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="92816-184">На клиенте запустите ImportServiceCert.bat в Командная строка разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="92816-184">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="92816-185">Он импортирует сертификат службы из файла Service.cer в хранилище CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="92816-185">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>

12. <span data-ttu-id="92816-186">На сервере запустите ImportClientCert.bat в Командная строка разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="92816-186">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="92816-187">При этом импортируется сертификат клиента из файла Client.cer в хранилище «LocalMachine - TrustedPeople».</span><span class="sxs-lookup"><span data-stu-id="92816-187">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>

13. <span data-ttu-id="92816-188">На сервере запустите из окна командной строки программу Service.exe.</span><span class="sxs-lookup"><span data-stu-id="92816-188">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="92816-189">На клиентском компьютере из окна командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="92816-189">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="92816-190">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="92816-190">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="92816-191">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="92816-191">To clean up after the sample</span></span>

1. <span data-ttu-id="92816-192">После завершения работы примера запустите в папке примеров файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="92816-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="92816-193">Он удалит из хранилища сертификатов сертификаты сервера и клиента.</span><span class="sxs-lookup"><span data-stu-id="92816-193">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="92816-194">Этот скрипт не удаляет сертификаты службы на клиенте при запуске образца на нескольких компьютерах.</span><span class="sxs-lookup"><span data-stu-id="92816-194">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="92816-195">Если вы выполнили примеры Windows Communication Foundation (WCF), использующие сертификаты на нескольких компьютерах, обязательно очистите сертификаты службы, установленные в хранилище CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="92816-195">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="92816-196">Для этого воспользуйтесь следующей командой: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Например: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="92816-196">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
