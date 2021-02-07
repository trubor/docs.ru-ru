---
description: 'Дополнительные сведения: поставщик маркеров'
title: Поставщик маркеров
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: 145d85eb0e0d8622c7cfb90ef4a6e24ccb7b9226
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668569"
---
# <a name="token-provider"></a><span data-ttu-id="ac418-103">Поставщик маркеров</span><span class="sxs-lookup"><span data-stu-id="ac418-103">Token Provider</span></span>

<span data-ttu-id="ac418-104">В этом образце показано, как реализовать пользовательский поставщик маркеров.</span><span class="sxs-lookup"><span data-stu-id="ac418-104">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="ac418-105">Поставщик маркеров в Windows Communication Foundation (WCF) используется для предоставления учетных данных инфраструктуре безопасности.</span><span class="sxs-lookup"><span data-stu-id="ac418-105">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="ac418-106">Поставщик токенов осуществляет общую проверку цели и выдает соответствующие учетные данные, чтобы инфраструктура безопасности смогла обеспечить защиту сообщения.</span><span class="sxs-lookup"><span data-stu-id="ac418-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="ac418-107">WCF поставляется с поставщиком маркеров диспетчера учетных данных по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ac418-107">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="ac418-108">WCF также поставляется с поставщиком токена CardSpace.</span><span class="sxs-lookup"><span data-stu-id="ac418-108">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="ac418-109">Пользовательские поставщики маркеров полезны в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="ac418-109">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="ac418-110">если используется хранилище учетных данных с которым эти поставщики не работают;</span><span class="sxs-lookup"><span data-stu-id="ac418-110">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="ac418-111">Если вы хотите предоставить собственный настраиваемый механизм для преобразования учетных данных с точки, когда пользователь предоставляет сведения о том, когда клиентская платформа WCF использует учетные данные.</span><span class="sxs-lookup"><span data-stu-id="ac418-111">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="ac418-112">если строится пользовательский маркер.</span><span class="sxs-lookup"><span data-stu-id="ac418-112">If you are building a custom token.</span></span>

 <span data-ttu-id="ac418-113">В этом образце показано, как построить поставщик пользовательских маркеров, преобразующий входные данные пользователя в другой формат.</span><span class="sxs-lookup"><span data-stu-id="ac418-113">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>

 <span data-ttu-id="ac418-114">Итак, этот образец демонстрирует следующее:</span><span class="sxs-lookup"><span data-stu-id="ac418-114">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="ac418-115">как клиент может проходить проверку подлинности с использованием пары "имя пользователя/пароль";</span><span class="sxs-lookup"><span data-stu-id="ac418-115">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="ac418-116">как настроить клиент с пользовательским поставщиком маркеров;</span><span class="sxs-lookup"><span data-stu-id="ac418-116">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="ac418-117">как сервер может проверить учетные данные клиента с помощью пользовательского объекта <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, проверяющего соответствие имени пользователя и пароля;</span><span class="sxs-lookup"><span data-stu-id="ac418-117">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>

- <span data-ttu-id="ac418-118">как сервер проходит проверку подлинности на клиенте с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="ac418-118">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="ac418-119">В данном образце также показано, как можно получить доступ к удостоверению вызывающего модуля после процесса проверки подлинности пользовательского маркера.</span><span class="sxs-lookup"><span data-stu-id="ac418-119">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>

 <span data-ttu-id="ac418-120">Служба предоставляет одну конечную точку для взаимодействия со службой, определенной в файле конфигурации App.config.</span><span class="sxs-lookup"><span data-stu-id="ac418-120">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="ac418-121">Конечная точка состоит из адреса, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="ac418-121">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="ac418-122">Привязка настраивается с помощью стандартного элемента `wsHttpBinding`, который по умолчанию использует безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="ac418-122">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="ac418-123">В этом образце стандартная привязка `wsHttpBinding` использует проверку подлинности имени пользователя клиента.</span><span class="sxs-lookup"><span data-stu-id="ac418-123">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="ac418-124">Кроме того, служба настраивает сертификат службы с помощью поведения serviceCredentials.</span><span class="sxs-lookup"><span data-stu-id="ac418-124">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="ac418-125">Поведение serviceCredentials позволяет настроить сертификат службы.</span><span class="sxs-lookup"><span data-stu-id="ac418-125">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="ac418-126">Сертификат службы используется клиентом для проверки подлинности службы и обеспечения защиты сообщения.</span><span class="sxs-lookup"><span data-stu-id="ac418-126">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="ac418-127">В следующей конфигурации делается ссылка на сертификат localhost, установленный во время установки образца, как описано в инструкциях по установке далее.</span><span class="sxs-lookup"><span data-stu-id="ac418-127">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
        The serviceCredentials behavior allows one to define a service certificate.
        A service certificate is used by a client to authenticate the service and provide message protection.
        This configuration references the "localhost" certificate installed during the setup instructions.
        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
```

 <span data-ttu-id="ac418-128">Конфигурация конечной точки клиента состоит из имени конфигурации, абсолютного адреса конечной точки службы, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="ac418-128">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="ac418-129">Привязка клиента настраивается с помощью соответствующего режима (`Mode`) и типа (`clientCredentialType`) сообщения.</span><span class="sxs-lookup"><span data-stu-id="ac418-129">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
              address="http://localhost:8000/servicemodelsamples/service"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator">
    </endpoint>
  </client>

  <bindings>
    <wsHttpBinding>
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
</system.serviceModel>
```

 <span data-ttu-id="ac418-130">В следующих шагах показано, как разработать пользовательский поставщик маркеров и интегрировать его с платформой безопасности WCF:</span><span class="sxs-lookup"><span data-stu-id="ac418-130">The following steps show how to develop a custom token provider and integrate it with the WCF security framework:</span></span>

1. <span data-ttu-id="ac418-131">Создание пользовательского поставщика маркеров.</span><span class="sxs-lookup"><span data-stu-id="ac418-131">Write a custom token provider.</span></span>

     <span data-ttu-id="ac418-132">В образце реализуется пользовательский поставщик маркеров, получающий имя пользователя и пароль.</span><span class="sxs-lookup"><span data-stu-id="ac418-132">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="ac418-133">Пароль должен соответствовать данному имени пользователя.</span><span class="sxs-lookup"><span data-stu-id="ac418-133">The password must match this username.</span></span> <span data-ttu-id="ac418-134">Этот пользовательский поставщик маркеров приводится исключительно с целью демонстрации; его не рекомендуется использовать в реальном развертывании.</span><span class="sxs-lookup"><span data-stu-id="ac418-134">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>

     <span data-ttu-id="ac418-135">Для выполнения этой задачи пользовательский поставщик маркеров наследует класс <xref:System.IdentityModel.Selectors.SecurityTokenProvider> и переопределяет метод <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29>.</span><span class="sxs-lookup"><span data-stu-id="ac418-135">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="ac418-136">Этот метод создает и возвращает новый маркер `UserNameSecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="ac418-136">This method creates and returns a new `UserNameSecurityToken`.</span></span>

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
        // obtain username and password from the user using console window
        string username = GetUserName();
        string password = GetPassword();
        Console.WriteLine("username: {0}", username);

        // return new UserNameSecurityToken containing information obtained from user
        return new UserNameSecurityToken(username, password);
    }
    ```

2. <span data-ttu-id="ac418-137">Создание пользовательского диспетчера маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="ac418-137">Write custom security token manager.</span></span>

     <span data-ttu-id="ac418-138">Класс <xref:System.IdentityModel.Selectors.SecurityTokenManager> используется для создания объекта <xref:System.IdentityModel.Selectors.SecurityTokenProvider> для конкретного конструктора <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>, который передается в него в методе `CreateSecurityTokenProvider`.</span><span class="sxs-lookup"><span data-stu-id="ac418-138">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="ac418-139">Диспетчер маркеров безопасности также используется для создания структур проверки подлинности маркеров и сериализатора маркеров. В этом образце они не представлены.</span><span class="sxs-lookup"><span data-stu-id="ac418-139">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="ac418-140">В данном образце пользовательский диспетчер маркеров безопасности наследуется от класса <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> и переопределяет метод `CreateSecurityTokenProvider`, возвращающий пользовательский поставщик маркеров, когда переданные требования маркера указывают на запрос пользовательского поставщика.</span><span class="sxs-lookup"><span data-stu-id="ac418-140">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>

    ```csharp
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        MyUserNameClientCredentials myUserNameClientCredentials;

        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)
            : base(myUserNameClientCredentials)
        {
            this.myUserNameClientCredentials = myUserNameClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // if token requirement matches username token return custom username token provider
            // otherwise use base implementation
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)
            {
                return new MyUserNameTokenProvider();
            }
            else
            {
                return base.CreateSecurityTokenProvider(tokenRequirement);
            }
        }
    }
    ```

3. <span data-ttu-id="ac418-141">Создание пользовательских учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="ac418-141">Write a custom client credential.</span></span>

     <span data-ttu-id="ac418-142">Класс учетных данных клиента используется для представления учетных данных, которые сконфигурированы для прокси клиента, и создает диспетчер маркеров безопасности, который используется для получения структур проверки подлинности маркеров, поставщиков маркеров и сериализаторов маркеров.</span><span class="sxs-lookup"><span data-stu-id="ac418-142">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>

    ```csharp
    public class MyUserNameClientCredentials : ClientCredentials
    {
        public MyUserNameClientCredentials()
            : base()
        {
        }

        protected override ClientCredentials CloneCore()
        {
            return new MyUserNameClientCredentials();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            // return custom security token manager
            return new MyUserNameSecurityTokenManager(this);
        }
    }
    ```

4. <span data-ttu-id="ac418-143">Настройка клиента для использования пользовательских учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="ac418-143">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="ac418-144">Чтобы клиент мог использовать пользовательские учетные данные клиента, образец удаляет класс учетных данных клиента по умолчанию и предоставляет новый класс учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="ac418-144">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>

    ```csharp
    static void Main()
    {
        // ...
           // Create a client with given client endpoint configuration
          CalculatorClient client = new CalculatorClient();

          // set new credentials
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());
       // ...
    }
    ```

 <span data-ttu-id="ac418-145">На стороне службы для вывода информации о вызывающем модуле можно использовать свойство <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="ac418-145">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="ac418-146">Свойство <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> содержит информацию об утверждениях о текущем вызывающем модуле.</span><span class="sxs-lookup"><span data-stu-id="ac418-146">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 <span data-ttu-id="ac418-147">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="ac418-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ac418-148">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="ac418-148">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="ac418-149">Пакетный файл Setup</span><span class="sxs-lookup"><span data-stu-id="ac418-149">Setup Batch File</span></span>

 <span data-ttu-id="ac418-150">Входящий в состав образца файл Setup.bat позволяет настроить для сервера соответствующий сертификат, необходимый для выполнения резидентного приложения, для которого требуется обеспечение безопасности на основе сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="ac418-150">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="ac418-151">Этот пакетный файл необходимо изменить, чтобы его можно было использовать на нескольких компьютерах или без размещения приложения.</span><span class="sxs-lookup"><span data-stu-id="ac418-151">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="ac418-152">Ниже представлен краткие общие сведения о различных разделах пакетных файлов, позволяющий изменять их для выполнения в соответствующей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ac418-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="ac418-153">Создание сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="ac418-153">Creating the server certificate.</span></span>

     <span data-ttu-id="ac418-154">Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="ac418-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="ac418-155">Переменная `%SERVER_NAME%`задает имя сервера.</span><span class="sxs-lookup"><span data-stu-id="ac418-155">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="ac418-156">Измените эту переменную, чтобы задать собственное имя сервера.</span><span class="sxs-lookup"><span data-stu-id="ac418-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="ac418-157">По умолчанию в этом пакетном файле используется имя localhost.</span><span class="sxs-lookup"><span data-stu-id="ac418-157">The default value in this batch file is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="ac418-158">Установка сертификата сервера в хранилище доверенных сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="ac418-158">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="ac418-159">Следующие строки из файла Setup.bat копируют сертификат сервера в хранилище доверенных лиц клиента.</span><span class="sxs-lookup"><span data-stu-id="ac418-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ac418-160">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы.</span><span class="sxs-lookup"><span data-stu-id="ac418-160">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ac418-161">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="ac418-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
> <span data-ttu-id="ac418-162">Пакетный файл Setup.bat предназначен для запуска из командной строки Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="ac418-162">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="ac418-163">Требуется, чтобы переменная среды MSSDK указывала на каталог, в котором установлен пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="ac418-163">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="ac418-164">Эта переменная среды автоматически устанавливается в командной строке Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="ac418-164">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="ac418-165">Настройка и сборка образца</span><span class="sxs-lookup"><span data-stu-id="ac418-165">To set up and build the sample</span></span>

1. <span data-ttu-id="ac418-166">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ac418-166">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ac418-167">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ac418-167">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="ac418-168">Запуск образца на одном компьютере</span><span class="sxs-lookup"><span data-stu-id="ac418-168">To run the sample on the same computer</span></span>

1. <span data-ttu-id="ac418-169">Запустите Setup.bat из папки образца установки в командной строке Visual Studio 2012, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="ac418-169">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="ac418-170">При этом устанавливаются все сертификаты, необходимые для выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="ac418-170">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ac418-171">Пакетный файл Setup.bat предназначен для запуска из командной строки Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="ac418-171">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="ac418-172">Переменная среды PATH, заданная в командной строке Visual Studio 2012, указывает на каталог, содержащий исполняемые файлы, необходимые для скрипта Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="ac418-172">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="ac418-173">Запустите программу Service.exe из каталога \service\bin.</span><span class="sxs-lookup"><span data-stu-id="ac418-173">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="ac418-174">Запустите программу Client.exe из каталога \client\bin.</span><span class="sxs-lookup"><span data-stu-id="ac418-174">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="ac418-175">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="ac418-175">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="ac418-176">При запросе имени пользователя введите имя пользователя.</span><span class="sxs-lookup"><span data-stu-id="ac418-176">At the username prompt, type a user name.</span></span>  
  
5. <span data-ttu-id="ac418-177">При запросе пароля используйте ту же строку, которая была введена при запросе имени пользователя.</span><span class="sxs-lookup"><span data-stu-id="ac418-177">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6. <span data-ttu-id="ac418-178">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ac418-178">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="ac418-179">Запуск образца на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="ac418-179">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="ac418-180">Создайте на компьютере службы каталог для двоичных файлов службы.</span><span class="sxs-lookup"><span data-stu-id="ac418-180">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="ac418-181">Скопируйте файлы служебной программы в каталог службы на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="ac418-181">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="ac418-182">Кроме того, скопируйте файлы Setup.bat и Cleanup.bat на компьютер службы.</span><span class="sxs-lookup"><span data-stu-id="ac418-182">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="ac418-183">Необходимо иметь сертификат сервера с именем субъекта, содержащим полное имя домена компьютера.</span><span class="sxs-lookup"><span data-stu-id="ac418-183">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="ac418-184">Для отображения этого нового имени сертификата необходимо обновить файл Service.exe.config.</span><span class="sxs-lookup"><span data-stu-id="ac418-184">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="ac418-185">Сертификат сервера можно создать путем изменения пакетного файла Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="ac418-185">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="ac418-186">Обратите внимание, что файл setup.bat должен быть запущен из Командная строка разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="ac418-186">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="ac418-187">Необходимо присвоить переменной `%SERVER_NAME%` полное имя узла компьютера, используемого для размещения службы.</span><span class="sxs-lookup"><span data-stu-id="ac418-187">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="ac418-188">Скопируйте сертификат сервера в хранилище CurrentUser-TrustedPeople клиента.</span><span class="sxs-lookup"><span data-stu-id="ac418-188">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="ac418-189">Это нужно делать, когда сертификат сервера выдан издателем, которому доверяет клиент.</span><span class="sxs-lookup"><span data-stu-id="ac418-189">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="ac418-190">В файле Service.exe.config компьютера службы измените значение базового адреса для указания полного имени компьютера вместо localhost.</span><span class="sxs-lookup"><span data-stu-id="ac418-190">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="ac418-191">На компьютере службы запустите из командной строки программу service.exe.</span><span class="sxs-lookup"><span data-stu-id="ac418-191">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="ac418-192">Скопируйте на клиентские компьютеры файлы из папки \client\bin\ в папку языка.</span><span class="sxs-lookup"><span data-stu-id="ac418-192">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="ac418-193">В файле Client.exe.config на клиентском компьютере измените значение адреса конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="ac418-193">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="ac418-194">На клиентском компьютере из командной строки запустите программу `Client.exe`.</span><span class="sxs-lookup"><span data-stu-id="ac418-194">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="ac418-195">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ac418-195">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ac418-196">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="ac418-196">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="ac418-197">После завершения работы примера запустите в папке примеров файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="ac418-197">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
