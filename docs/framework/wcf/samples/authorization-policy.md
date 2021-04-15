---
description: 'Дополнительные сведения: политика авторизации'
title: Политика авторизации
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 0d982c800f35654c6b509edf9a26f86cdf9dfabd
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494614"
---
# <a name="authorization-policy"></a>Политика авторизации

В этом образце показано, как реализовать пользовательскую политику авторизации утверждений и связанный с ней пользовательский диспетчер авторизации службы. Это бывает удобно, если служба осуществляет проверку прав доступа к операциям службы на основании утверждений и предоставляет вызывающей стороне определенные права, прежде чем проверить права доступа. В этом образце показан процесс добавления утверждений, а также процесс проверки прав доступа с использованием готового набора утверждений. Все сообщения приложений, которыми обмениваются служба и клиент, подписываются и шифруются. По умолчанию при использовании `wsHttpBinding` привязки имя пользователя и пароль, предоставленные клиентом, используются для входа в действительную учетную запись Windows. В этом образце показано, как проверять подлинность клиента с помощью пользовательского объекта <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Кроме того, в этом образце показана проверка подлинности клиента на стороне службы с использованием сертификата X.509. Этот образец показывает реализацию объектов <xref:System.IdentityModel.Policy.IAuthorizationPolicy> и <xref:System.ServiceModel.ServiceAuthorizationManager>, которые между собой предоставляют заданным пользователям доступ к определенным методам службы. Этот пример основан на [имени пользователя безопасности сообщений](message-security-user-name.md), но демонстрирует, как выполнить преобразование утверждения перед <xref:System.ServiceModel.ServiceAuthorizationManager> вызовом.

> [!NOTE]
> Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.

 Таким образом, в данном образце демонстрируются указанные ниже возможности.

- Подлинность клиента может проверяться с помощью имени пользователя и пароля.

- Подлинность клиента может проверяться с помощью сертификата X.509.

- Сервер проверяет учетные данные клиента с помощью пользовательского проверяющего элемента управления `UsernamePassword`.

- Сервер проходит проверку подлинности с использованием сертификата X.509 сервера.

- Сервер может использовать объект <xref:System.ServiceModel.ServiceAuthorizationManager> для управления доступом к определенным методам службы.

- Реализация политики <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.

Служба предоставляет две конечные точки для взаимодействия с ней; они определены в файле конфигурации App.config. Каждая конечная точка состоит из адреса, привязки и контракта. Одна привязка настраивается с помощью стандартной привязки `wsHttpBinding`, использующей протокол WS-Security и проверку подлинности имени пользователя клиента. Вторая привязка настраивается с помощью стандартной привязки `wsHttpBinding`, использующей протокол WS-Security и проверку подлинности сертификата клиента. [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)Указывает, что учетные данные пользователя должны использоваться для проверки подлинности служб. Сертификат сервера должен содержать то же значение для свойства, `SubjectName` что и `findValue` атрибут в [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <!-- configure base address provided by host -->
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service"/>
        </baseAddresses>
      </host>
      <!-- use base address provided by host, provide two endpoints -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <endpoint address="certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding2"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
    <message clientCredentialType="UserName" />
        </security>
      </binding>
      <!-- X509 certificate binding -->
      <binding name="Binding2">
        <security mode="Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior" >
        <serviceDebug includeExceptionDetailInFaults ="true" />
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to specify authentication constraints on client certificates.
          -->
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
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
        <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
          <!--
          The serviceAuthorization behavior allows one to specify custom authorization policies.
          -->
          <authorizationPolicies>
            <add policyType="Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary" />
          </authorizationPolicies>
        </serviceAuthorization>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

Конфигурация каждой из конечных точек клиента состоит из имени конфигурации, абсолютного адреса конечной точки службы, привязки и контракта. Привязка клиента настраивается с соответствующим режимом безопасности, как указано в этом случае в [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) и, `clientCredentialType` как указано в [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) .

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
            address="http://localhost:8001/servicemodelsamples/service/username"
    binding="wsHttpBinding"
    bindingConfiguration="Binding1"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" >
      </endpoint>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
                        address="http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
            bindingConfiguration="Binding2"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
        <!-- X509 certificate binding -->
        <binding name="Binding2">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
    </wsHttpBinding>
    </bindings>

    <behaviors>
      <behavior name="ClientCertificateBehavior">
        <clientCredentials>
          <serviceCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust
            means that if the certificate
            is in the user's Trusted People store, then it will be
            trusted without performing a
            validation of the certificate's issuer chain. This setting
            is used here for convenience so that the
            sample can be run without having to have certificates
            issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust.
            The security implications of this
            setting should be carefully considered before using
            PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode = "PeerOrChainTrust" />
          </serviceCertificate>
        </clientCredentials>
      </behavior>
    </behaviors>

  </system.serviceModel>
```

Для конечной точки, выполняющей проверку подлинности имени пользователя, реализация клиента задает имя пользователя и пароль, которые следует использовать.

```csharp
// Create a client with Username endpoint configuration
CalculatorClient client1 = new CalculatorClient("Username");

client1.ClientCredentials.UserName.UserName = "test1";
client1.ClientCredentials.UserName.Password = "1tset";

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client1.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client1.Close();
```

Для конечной точки, выполняющей проверку подлинности сертификата, реализация клиента задает сертификат клиента, который следует использовать.

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client2 = new CalculatorClient("Certificate");

client2.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client2.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client2.Close();
```

В этом образце для проверки имен пользователей и паролей применяется пользовательский объект <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. В этом образце реализуется класс `MyCustomUserNamePasswordValidator`, наследуемый от класса <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Дополнительные сведения см. в документации по классу <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. В целях демонстрации интеграции с <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> в этом образце пользовательского проверяющего элемента управления реализуется метод <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>, который принимает пары "имя пользователя-пароль", где имя пользователя соответствует паролю, как показано в следующем примере кода.

```csharp
public class MyCustomUserNamePasswordValidator : UserNamePasswordValidator
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
      throw new SecurityTokenException("Unknown Username or Password");
    }
  }
}
```

После реализации в коде службы проверяющего элемента управления необходимо проинформировать узел службы о проверяющем элементе управления, который следует использовать. Это делается с помощью следующего кода:

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Вы также можете сделать то же самое в конфигурации:

```xml
<behavior>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

Windows Communication Foundation (WCF) предоставляет обширную модель на основе утверждений для выполнения проверок доступа. Для контроля прав доступа и проверки, удовлетворяют ли связанные с клиентом удостоверения требованиям, необходимым для доступа к методу службы, используется объект <xref:System.ServiceModel.ServiceAuthorizationManager>.

Для демонстрации в этом примере показана реализация <xref:System.ServiceModel.ServiceAuthorizationManager> , которая реализует <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> метод, чтобы предоставить пользователю доступ к методам на основе утверждений типа, `http://example.com/claims/allowedoperation` значение которого является универсальным кодом ресурса (URI) операции, которую можно вызвать.

```csharp
public class MyServiceAuthorizationManager : ServiceAuthorizationManager
{
  protected override bool CheckAccessCore(OperationContext operationContext)
  {
    string action = operationContext.RequestContext.RequestMessage.Headers.Action;
    Console.WriteLine("action: {0}", action);
    foreach(ClaimSet cs in operationContext.ServiceSecurityContext.AuthorizationContext.ClaimSets)
    {
      if ( cs.Issuer == ClaimSet.System )
      {
        foreach (Claim c in cs.FindClaims("http://example.com/claims/allowedoperation", Rights.PossessProperty))
        {
          Console.WriteLine("resource: {0}", c.Resource.ToString());
          if (action == c.Resource.ToString())
            return true;
        }
      }
    }
    return false;
  }
}
```

После реализации пользовательского объекта <xref:System.ServiceModel.ServiceAuthorizationManager> необходимо проинформировать узел службы об объекте<xref:System.ServiceModel.ServiceAuthorizationManager>, который следует использовать. Это можно сделать с помощью следующего фрагмента кода.

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

Основным реализуемым методом <xref:System.IdentityModel.Policy.IAuthorizationPolicy> является метод <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29>.

```csharp
public class MyAuthorizationPolicy : IAuthorizationPolicy
{
    string id;

    public MyAuthorizationPolicy()
    {
    id =  Guid.NewGuid().ToString();
    }

    public bool Evaluate(EvaluationContext evaluationContext,
                                            ref object state)
    {
        bool bRet = false;
        CustomAuthState customstate = null;

        if (state == null)
        {
            customstate = new CustomAuthState();
            state = customstate;
        }
        else
            customstate = (CustomAuthState)state;
        Console.WriteLine("In Evaluate");
        if (!customstate.ClaimsAdded)
        {
           IList<Claim> claims = new List<Claim>();

           foreach (ClaimSet cs in evaluationContext.ClaimSets)
              foreach (Claim c in cs.FindClaims(ClaimTypes.Name,
                                         Rights.PossessProperty))
                  foreach (string s in
                        GetAllowedOpList(c.Resource.ToString()))
                  {
                       claims.Add(new
               Claim("http://example.com/claims/allowedoperation",
                                    s, Rights.PossessProperty));
                            Console.WriteLine("Claim added {0}", s);
                      }
                   evaluationContext.AddClaimSet(this,
                           new DefaultClaimSet(this.Issuer,claims));
                   customstate.ClaimsAdded = true;
                   bRet = true;
                }
         else
         {
              bRet = true;
         }
         return bRet;
     }
...
}
```

В приведенном выше примере кода показано, каким образом метод <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> проверяет, что не было добавлено новых утверждений, которые влияют на обработку, и добавляет нужные утверждения. Разрешенные утверждения получаются из метода `GetAllowedOpList`, реализация которого возвращает заданный список операций, которые разрешено выполнять пользователю. Политика авторизации добавляет утверждения для доступа к определенной операции. Впоследствии эта политика используется объектом <xref:System.ServiceModel.ServiceAuthorizationManager> для принятия решений о предоставлении доступа.

После реализации интерфейса <xref:System.IdentityModel.Policy.IAuthorizationPolicy> необходимо проинформировать узел службы о политиках авторизации, которые следует использовать.

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

При выполнении примера запросы и ответы операций отображаются в окне консоли клиента. Клиент успешно вызывает методы Add, Subtract и Multiple и получает сообщение "Access is denied" при попытке вызывать метод Divide. Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.

## <a name="setup-batch-file"></a>Пакетный файл Setup

Входящий в состав образца файл Setup.bat позволяет настроить для сервера соответствующие сертификаты, необходимые для выполнения резидентного приложения, которое требует обеспечения безопасности на основе сертификата сервера.

Ниже представлен краткие общие сведения о различных разделах пакетных файлов, позволяющий изменять их для выполнения в соответствующей конфигурации.

- Создание сертификата сервера.

    Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера. Переменная %SERVER_NAME% задает имя сервера. Измените эту переменную, чтобы задать собственное имя сервера. Значением по умолчанию является localhost.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Установка сертификата сервера в хранилище доверенных сертификатов клиента.

    Следующие строки из файла Setup.bat копируют сертификат сервера в хранилище доверенных лиц клиента. Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы. Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Создание сертификата клиента.

    Следующие строки из файла Setup.bat создают сертификат клиента, который будет использоваться. Переменная %USER_NAME% задает имя сервера. Эта переменная имеет значение "test1", поскольку политика `IAuthorizationPolicy` ищет именно это имя. Если изменить значение переменной %USER_NAME%, необходимо изменить и соответствующее значение в методе `IAuthorizationPolicy.Evaluate`.

    Сертификат хранится в хранилище "My store" (Личном хранилище) в расположении CurrentUser.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Установка сертификата клиента в хранилище доверенных сертификатов сервера.

    Следующие строки из файла Setup.bat копируют сертификат клиента в хранилище доверенных лиц. Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны серверной системы. Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата клиента в хранилище сертификатов сервера не требуется.

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>Настройка и сборка образца

1. Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).

2. Чтобы запустить образец на одном или нескольких компьютерах, следуйте приведенным далее инструкциям.

> [!NOTE]
> Если для восстановления конфигурации этого образца используется программа Svcutil.exe, измените имя конечной точки в конфигурации клиента, чтобы оно соответствовало клиентскому коду.

### <a name="to-run-the-sample-on-the-same-computer"></a>Запуск образца на одном компьютере

1. Откройте Командная строка разработчика для Visual Studio с правами администратора и запустите *Setup.bat* из примера установочной папки. При этом устанавливаются все сертификаты, необходимые для выполнения образца.

    > [!NOTE]
    > Пакетный файл Setup.bat предназначен для запуска из Командная строка разработчика для Visual Studio. Переменная среды PATH, заданная в Командная строка разработчика для Visual Studio, указывает на каталог, содержащий исполняемые файлы, необходимые для скрипта *Setup.bat* .

1. Запустите Service.exe из *сервице\бин*.

1. Запустите Client.exe из *\client\bin\*. Действия клиента отображаются в консольном приложении клиента.

Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="to-run-the-sample-across-computers"></a>Запуск образца на нескольких компьютерах

1. Создайте каталог на компьютере службы.

2. Скопируйте файлы служебной программы из *\сервице\бин* в каталог на компьютере службы. Кроме того, скопируйте на компьютер службы файлы Setup.bat, Cleanup.bat, GetComputerName.vbs и ImportClientCert.bat.

3. Создайте на клиентском компьютере каталог для двоичных файлов клиента.

4. Скопируйте в клиентский каталог на клиентском компьютере файлы программы клиента. Кроме того, скопируйте на клиент файлы Setup.bat, Cleanup.bat и ImportServiceCert.bat.

5. На сервере запустите `setup.bat service` в Командная строка разработчика для Visual Studio, открытой с правами администратора.

    `setup.bat`При запуске с `service` аргументом создается сертификат службы с полным доменным именем компьютера и экспортируется сертификат службы в файл с именем *Service. cer*.

6. Измените *Service.exe.config* , чтобы отразить новое имя сертификата (в `findValue` атрибуте в [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), совпадающее с полным доменным именем компьютера. Кроме того, измените **ComputerName** в \<service> / \<baseAddresses> элементе с localhost на полное имя компьютера службы.

7. Скопируйте файл *Service. cer* из каталога службы в каталог клиента на клиентском компьютере.

8. На клиенте запустите `setup.bat client` в Командная строка разработчика для Visual Studio, открытой с правами администратора.

    `setup.bat`При выполнении с `client` аргументом создается сертификат клиента с именем **test1** и экспортируется сертификат клиента в файл с именем *Client. cer*.

9. В файле *Client.exe.config* на клиентском компьютере измените значение адреса конечной точки, чтобы оно совпадало с новым адресом службы. Для этого замените **localhost** на полное доменное имя сервера.

10. Скопируйте файл Client.cer из клиентского каталога в каталог службы на сервере.

11. На клиенте запустите *ImportServiceCert.bat* в Командная строка разработчика для Visual Studio, открытой с правами администратора.

    Сертификат службы будет импортирован из файла Service. cer в хранилище **CurrentUser-TrustedPeople** .

12. На сервере запустите *ImportClientCert.bat* в Командная строка разработчика для Visual Studio, открытой с правами администратора.

    При этом сертификат клиента будет импортирован из файла Client. cer в хранилище **LocalMachine-TrustedPeople** .

13. На сервере запустите из окна командной строки программу Service.exe.

14. На клиентском компьютере из окна командной строки запустите программу Client.exe.

    Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="clean-up-after-the-sample"></a>Очистка после образца

Чтобы очистить после примера, запустите *Cleanup.bat* в папке Samples после завершения выполнения примера. Он удалит из хранилища сертификатов сертификаты сервера и клиента.

> [!NOTE]
> Этот скрипт не удаляет сертификаты службы на клиенте при запуске образца на нескольких компьютерах. Если вы выполнили примеры WCF, использующие сертификаты на нескольких компьютерах, обязательно очистите сертификаты службы, установленные в хранилище CurrentUser-TrustedPeople. Для этого воспользуйтесь следующей командой: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Например: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
