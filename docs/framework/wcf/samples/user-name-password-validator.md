---
description: 'Дополнительные сведения: средство проверки пароля для имени пользователя'
title: Проверяющий элемент управления для имен пользователей и паролей
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 8195549da81c8fbb7259d2b3e00db39017817c41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755750"
---
# <a name="user-name-password-validator"></a><span data-ttu-id="af927-103">Проверяющий элемент управления для имен пользователей и паролей</span><span class="sxs-lookup"><span data-stu-id="af927-103">User Name Password Validator</span></span>

<span data-ttu-id="af927-104">В этом образце показано, как реализовать пользовательский проверяющий элемент управления UserNamePassword.</span><span class="sxs-lookup"><span data-stu-id="af927-104">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="af927-105">Это бывает полезно в случаях, когда ни один из встроенных режимов проверки имени пользователя и пароля не соответствует требования приложениям, например, когда пары "имя пользователя-пароль" хранятся во внешнем хранилище, например в базе данных.</span><span class="sxs-lookup"><span data-stu-id="af927-105">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="af927-106">В этом образце показана служба, имеющая пользовательский проверяющий элемент управления, который проверяет две конкретных пары "имя пользователя-пароль".</span><span class="sxs-lookup"><span data-stu-id="af927-106">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="af927-107">Клиент использует такие пары "имя пользователя-пароль" для проверки подлинности у службы.</span><span class="sxs-lookup"><span data-stu-id="af927-107">The client uses such a username/password pair to authenticate to the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af927-108">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="af927-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="af927-109">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="af927-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="af927-110">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="af927-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af927-111">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="af927-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> <span data-ttu-id="af927-112">Поскольку учетные данные имени пользователя, использующие пары "имя пользователя-пароль", принимаемые пользовательским проверяющим элементом управления, могут создаваться кем угодно, такая служба является менее безопасной по сравнению с поведением по умолчанию, которое предоставляется стандартным проверяющим элементом управления UserNamePassword.</span><span class="sxs-lookup"><span data-stu-id="af927-112">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="af927-113">Стандартный проверяющий элемент управления UserNamePassword предпринимает попытку сопоставить заданную пару "имя пользователя-пароль" с учетной записью Windows, и если выполнить такое сопоставление не удается, проверка подлинности завершается неудачно.</span><span class="sxs-lookup"><span data-stu-id="af927-113">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="af927-114">Пользовательский проверяющий элемент управления UserNamePassword в этом образце НЕ ДОЛЖЕН использоваться в рабочей среде; он предназначен только для иллюстрации.</span><span class="sxs-lookup"><span data-stu-id="af927-114">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>

 <span data-ttu-id="af927-115">Таким образом, в этом образце демонстрируются указанные ниже возможности.</span><span class="sxs-lookup"><span data-stu-id="af927-115">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="af927-116">Подлинность клиента может проверяться с помощью маркера имени пользователя.</span><span class="sxs-lookup"><span data-stu-id="af927-116">The client can be authenticated using a Username Token.</span></span>

- <span data-ttu-id="af927-117">Сервер проверяет учетные данные клиента с помощью проверяющего элемента управления, а пользовательские ошибки из логики проверки имени пользователя и пароля распространяются на клиент.</span><span class="sxs-lookup"><span data-stu-id="af927-117">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>

- <span data-ttu-id="af927-118">Сервер проходит проверку подлинности с использованием сертификата X.509 сервера.</span><span class="sxs-lookup"><span data-stu-id="af927-118">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="af927-119">Служба предоставляет одну конечную точку для взаимодействия с нею; она определена в файле конфигурации App.config. Конечная точка состоит из адреса, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="af927-119">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="af927-120">Привязка настроена со стандартным `wsHttpBinding` значением, которое по умолчанию использует проверку подлинности WS-Security и username.</span><span class="sxs-lookup"><span data-stu-id="af927-120">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Security and username authentication.</span></span> <span data-ttu-id="af927-121">В поведении службы задается режим `Custom` проверки пар "имя пользователя-пароль" клиента, а также тип класса проверяющего элемента управления.</span><span class="sxs-lookup"><span data-stu-id="af927-121">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="af927-122">Коме того, поведение с помощью элемента `serviceCertificate` задает сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="af927-122">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="af927-123">Сертификат сервера должен содержать то же значение, `SubjectName` что и `findValue` в [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="af927-123">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <!-- use host/baseAddresses to configure base address provided by host -->
      <host>
        <baseAddresses>
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service" />
        </baseAddresses>
      </host>
      <!-- use base address specified above, provide one endpoint -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- username binding -->
      <binding name="Binding">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceDebug includeExceptionDetailInFaults ="true"/>
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to
          specify a custom validator for username/password
          combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom"
                                  customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate. A service certificate is used by a client to authenticate the service and provide message protection. You must specify a server certificate when passing username/passwords to encrypt the information as it is sent on the wire. Otherwise the username and password information would be sent as clear text. This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

 <span data-ttu-id="af927-124">Конфигурация конечной точки клиента состоит из имени конфигурации, абсолютного адреса конечной точки службы, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="af927-124">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="af927-125">Привязка клиента настраивается с помощью соответствующего режима и `clientCredentialType` сообщения.</span><span class="sxs-lookup"><span data-stu-id="af927-125">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
address="http://localhost:8001/servicemodelsamples/service/username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
```

 <span data-ttu-id="af927-126">Реализация клиента запрашивает у пользователя имя пользователя и пароль.</span><span class="sxs-lookup"><span data-stu-id="af927-126">The client implementation prompts the user to enter a username and password.</span></span>

```csharp
// Get the username and password
Console.WriteLine("Username authentication required.");
Console.WriteLine("Provide a username.");
Console.WriteLine("   Enter username: (test1)");
string username = Console.ReadLine();
Console.WriteLine("   Enter password:");
string password = "";
ConsoleKeyInfo info = Console.ReadKey(true);
while (info.Key != ConsoleKey.Enter)
{
    if (info.Key != ConsoleKey.Backspace)
    {
        if (info.KeyChar != '\0')
        {
            password += info.KeyChar;
        }
        info = Console.ReadKey(true);
    }
    else if (info.Key == ConsoleKey.Backspace)
    {
        if (password != "")
        {
            password = password.Substring(0, password.Length - 1);
        }
        info = Console.ReadKey(true);
    }
}
for (int i = 0; i < password.Length; i++)
{
    Console.Write("*");
}
Console.WriteLine();
// Create a proxy with Certificate endpoint configuration
CalculatorProxy proxy = new CalculatorProxy("Username")
try
{
  proxy.ClientCredentials.Username.Username = username;
  proxy.ClientCredentials.Username.Password = password;
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = proxy.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
  }
  catch (Exception e)
  {
      Console.WriteLine("Call failed:");
      while (e != null)
      {
          Console.WriteLine("\t{0}", e.Message);
          e = e.InnerException;
      }
      proxy.Abort();
  }
}
```

 <span data-ttu-id="af927-127">В этом образце для проверки пар "имя пользователя-пароль" используется пользовательский элемент UserNamePasswordValidator.</span><span class="sxs-lookup"><span data-stu-id="af927-127">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="af927-128">В этом образце реализуется класс `CustomUserNamePasswordValidator`, наследуемый от класса <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="af927-128">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="af927-129">Дополнительные сведения см. в разделе, посвященном <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="af927-129">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="af927-130">В данном образце пользовательского элемента управления реализуется метод `Validate`, принимающий две конкретные пары "имя пользователя-пароль", как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="af927-130">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>

```csharp
public class CustomUserNameValidator : UserNamePasswordValidator
{
 // This method validates users. It allows in two users,
 // test1 and test2 with passwords 1tset and 2tset respectively.
 // This code is for illustration purposes only and
 // MUST NOT be used in a production environment because it
 // is NOT secure.
 public override void Validate(string userName, string password)
 {
  if (null == userName || null == password)
  {
   throw new ArgumentNullException();
  }

  if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
  {
   throw new FaultException("Unknown Username or Incorrect Password");
   }
  }
 }
```

 <span data-ttu-id="af927-131">После реализации в коде службы проверяющего элемента управления необходимо проинформировать узел службы о проверяющем элементе управления, который следует использовать.</span><span class="sxs-lookup"><span data-stu-id="af927-131">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="af927-132">Для этого можно воспользоваться следующим фрагментом кода.</span><span class="sxs-lookup"><span data-stu-id="af927-132">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 <span data-ttu-id="af927-133">Либо можно решить эту же задачу с помощью файла конфигурации, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="af927-133">Or you can do the same thing in configuration as follows.</span></span>

```xml
<behaviors>
 <serviceBehaviors>
  <behavior name="CalculatorServiceBehavior">
  ...
   <serviceCredentials>
    <!--
    The serviceCredentials behavior allows one to specify authentication constraints on username / password combinations.
    -->
    <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+CustomUserNameValidator, service" />
   ...
   </serviceCredentials>
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="af927-134">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="af927-134">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="af927-135">Клиент должен успешно вызывать все методы.</span><span class="sxs-lookup"><span data-stu-id="af927-135">The client should successfully call all the methods.</span></span> <span data-ttu-id="af927-136">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="af927-136">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="af927-137">Пакетный файл Setup</span><span class="sxs-lookup"><span data-stu-id="af927-137">Setup Batch File</span></span>

 <span data-ttu-id="af927-138">Входящий в состав образца файл Setup.bat позволяет настроить для сервера соответствующие сертификаты, необходимые для выполнения резидентного приложения, которое требует обеспечения безопасности на основе сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="af927-138">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="af927-139">Этот пакетный файл необходимо изменить, чтобы его можно было использовать на нескольких компьютерах или без резидентного размещения приложения.</span><span class="sxs-lookup"><span data-stu-id="af927-139">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>

 <span data-ttu-id="af927-140">Ниже представлены общие сведения о различных разделах пакетных файлов, позволяющие изменять их для выполнения в соответствующей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="af927-140">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="af927-141">Создание сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="af927-141">Creating the server certificate:</span></span>

     <span data-ttu-id="af927-142">Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="af927-142">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="af927-143">Переменная %SERVER_NAME% задает имя сервера.</span><span class="sxs-lookup"><span data-stu-id="af927-143">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="af927-144">Измените эту переменную, чтобы задать собственное имя сервера.</span><span class="sxs-lookup"><span data-stu-id="af927-144">Change this variable to specify your own server name.</span></span> <span data-ttu-id="af927-145">Значением по умолчанию является localhost.</span><span class="sxs-lookup"><span data-stu-id="af927-145">The default value is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="af927-146">Установка сертификата сервера в хранилище доверенных сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="af927-146">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="af927-147">Следующие строки из файла Setup.bat копируют сертификат сервера в хранилище доверенных лиц клиента.</span><span class="sxs-lookup"><span data-stu-id="af927-147">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="af927-148">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы.</span><span class="sxs-lookup"><span data-stu-id="af927-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="af927-149">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="af927-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="af927-150">Настройка и сборка образца</span><span class="sxs-lookup"><span data-stu-id="af927-150">To set up and build the sample</span></span>

1. <span data-ttu-id="af927-151">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="af927-151">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="af927-152">Чтобы выполнить образец на одном или нескольких компьютерах, выполните следующие инструкции.</span><span class="sxs-lookup"><span data-stu-id="af927-152">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="af927-153">Запуск образца на том же компьютере</span><span class="sxs-lookup"><span data-stu-id="af927-153">To run the sample on the same machine</span></span>

1. <span data-ttu-id="af927-154">Запустите Setup.bat из папки примера установки в командной строке Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="af927-154">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt.</span></span> <span data-ttu-id="af927-155">При этом устанавливаются все сертификаты, необходимые для выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="af927-155">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="af927-156">Пакетный файл Setup.bat предназначен для запуска из командной строки Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="af927-156">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="af927-157">Переменная среды PATH, заданная в командной строке Visual Studio 2012, указывает на каталог, содержащий исполняемые файлы, необходимые для скрипта Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="af927-157">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="af927-158">Запустите программу Service.exe из папки service\bin.</span><span class="sxs-lookup"><span data-stu-id="af927-158">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="af927-159">Запустите программу Client.exe из каталога \client\bin.</span><span class="sxs-lookup"><span data-stu-id="af927-159">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="af927-160">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="af927-160">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="af927-161">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="af927-161">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="af927-162">Выполнение примера на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="af927-162">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="af927-163">Создайте на компьютере службы каталог для двоичных файлов службы.</span><span class="sxs-lookup"><span data-stu-id="af927-163">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="af927-164">Скопируйте файлы служебной программы из каталога службы на компьютер службы.</span><span class="sxs-lookup"><span data-stu-id="af927-164">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="af927-165">Кроме того, скопируйте файлы Setup.bat и Cleanup.bat на компьютер службы.</span><span class="sxs-lookup"><span data-stu-id="af927-165">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="af927-166">Необходимо иметь сертификат сервера с именем субъекта, содержащим полное доменное имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="af927-166">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="af927-167">Необходимо обновить файл конфигурации сервера, чтобы в нем отражалось это новое имя сертификата.</span><span class="sxs-lookup"><span data-stu-id="af927-167">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4. <span data-ttu-id="af927-168">Скопируйте сертификат сервера в хранилище CurrentUser-TrustedPeople клиента.</span><span class="sxs-lookup"><span data-stu-id="af927-168">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="af927-169">Это нужно делать только в том случае, если сертификат сервера не выдан центром выдачи, которому доверяет клиент.</span><span class="sxs-lookup"><span data-stu-id="af927-169">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="af927-170">В файле App.config компьютера службы также измените значение базового адреса для указания полного доменного имени компьютера вместо localhost.</span><span class="sxs-lookup"><span data-stu-id="af927-170">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6. <span data-ttu-id="af927-171">На компьютере службы из окна командной строки запустите программу Service.exe.</span><span class="sxs-lookup"><span data-stu-id="af927-171">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7. <span data-ttu-id="af927-172">Скопируйте на клиентский компьютер файлы программы клиента из папки \client\bin\ в языковой папке.</span><span class="sxs-lookup"><span data-stu-id="af927-172">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8. <span data-ttu-id="af927-173">В файле Client.exe.config на клиентском компьютере измените значение адреса конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="af927-173">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="af927-174">На клиентском компьютере из окна командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="af927-174">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="af927-175">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="af927-175">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="af927-176">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="af927-176">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="af927-177">После завершения работы примера запустите в папке примеров файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="af927-177">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="af927-178">Он удалит из хранилища сертификатов сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="af927-178">This removes the server certificate from the certificate store.</span></span>
