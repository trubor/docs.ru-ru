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
# <a name="authorization-policy"></a><span data-ttu-id="c0ce7-103">Политика авторизации</span><span class="sxs-lookup"><span data-stu-id="c0ce7-103">Authorization Policy</span></span>

<span data-ttu-id="c0ce7-104">В этом образце показано, как реализовать пользовательскую политику авторизации утверждений и связанный с ней пользовательский диспетчер авторизации службы.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-104">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="c0ce7-105">Это бывает удобно, если служба осуществляет проверку прав доступа к операциям службы на основании утверждений и предоставляет вызывающей стороне определенные права, прежде чем проверить права доступа.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-105">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="c0ce7-106">В этом образце показан процесс добавления утверждений, а также процесс проверки прав доступа с использованием готового набора утверждений.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-106">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="c0ce7-107">Все сообщения приложений, которыми обмениваются служба и клиент, подписываются и шифруются.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-107">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="c0ce7-108">По умолчанию при использовании `wsHttpBinding` привязки имя пользователя и пароль, предоставленные клиентом, используются для входа в действительную учетную запись Windows.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-108">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="c0ce7-109">В этом образце показано, как проверять подлинность клиента с помощью пользовательского объекта <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-109">This sample demonstrates how to utilize a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to authenticate the client.</span></span> <span data-ttu-id="c0ce7-110">Кроме того, в этом образце показана проверка подлинности клиента на стороне службы с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-110">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="c0ce7-111">Этот образец показывает реализацию объектов <xref:System.IdentityModel.Policy.IAuthorizationPolicy> и <xref:System.ServiceModel.ServiceAuthorizationManager>, которые между собой предоставляют заданным пользователям доступ к определенным методам службы.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-111">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="c0ce7-112">Этот пример основан на [имени пользователя безопасности сообщений](message-security-user-name.md), но демонстрирует, как выполнить преобразование утверждения перед <xref:System.ServiceModel.ServiceAuthorizationManager> вызовом.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-112">This sample is based on the [Message Security User Name](message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="c0ce7-113">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="c0ce7-114">Таким образом, в данном образце демонстрируются указанные ниже возможности.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-114">In summary, this sample demonstrates how:</span></span>

- <span data-ttu-id="c0ce7-115">Подлинность клиента может проверяться с помощью имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-115">The client can be authenticated using a user name-password.</span></span>

- <span data-ttu-id="c0ce7-116">Подлинность клиента может проверяться с помощью сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-116">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="c0ce7-117">Сервер проверяет учетные данные клиента с помощью пользовательского проверяющего элемента управления `UsernamePassword`.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-117">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

- <span data-ttu-id="c0ce7-118">Сервер проходит проверку подлинности с использованием сертификата X.509 сервера.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-118">The server is authenticated using the server's X.509 certificate.</span></span>

- <span data-ttu-id="c0ce7-119">Сервер может использовать объект <xref:System.ServiceModel.ServiceAuthorizationManager> для управления доступом к определенным методам службы.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-119">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

- <span data-ttu-id="c0ce7-120">Реализация политики <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-120">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="c0ce7-121">Служба предоставляет две конечные точки для взаимодействия с ней; они определены в файле конфигурации App.config. Каждая конечная точка состоит из адреса, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-121">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="c0ce7-122">Одна привязка настраивается с помощью стандартной привязки `wsHttpBinding`, использующей протокол WS-Security и проверку подлинности имени пользователя клиента.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-122">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="c0ce7-123">Вторая привязка настраивается с помощью стандартной привязки `wsHttpBinding`, использующей протокол WS-Security и проверку подлинности сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-123">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="c0ce7-124">[\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)Указывает, что учетные данные пользователя должны использоваться для проверки подлинности служб.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-124">The [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="c0ce7-125">Сертификат сервера должен содержать то же значение для свойства, `SubjectName` что и `findValue` атрибут в [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="c0ce7-125">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

<span data-ttu-id="c0ce7-126">Конфигурация каждой из конечных точек клиента состоит из имени конфигурации, абсолютного адреса конечной точки службы, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-126">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="c0ce7-127">Привязка клиента настраивается с соответствующим режимом безопасности, как указано в этом случае в [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) и, `clientCredentialType` как указано в [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c0ce7-127">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

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

<span data-ttu-id="c0ce7-128">Для конечной точки, выполняющей проверку подлинности имени пользователя, реализация клиента задает имя пользователя и пароль, которые следует использовать.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-128">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

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

<span data-ttu-id="c0ce7-129">Для конечной точки, выполняющей проверку подлинности сертификата, реализация клиента задает сертификат клиента, который следует использовать.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-129">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

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

<span data-ttu-id="c0ce7-130">В этом образце для проверки имен пользователей и паролей применяется пользовательский объект <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-130">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="c0ce7-131">В этом образце реализуется класс `MyCustomUserNamePasswordValidator`, наследуемый от класса <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-131">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="c0ce7-132">Дополнительные сведения см. в документации по классу <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-132">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="c0ce7-133">В целях демонстрации интеграции с <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> в этом образце пользовательского проверяющего элемента управления реализуется метод <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>, который принимает пары "имя пользователя-пароль", где имя пользователя соответствует паролю, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-133">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

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

<span data-ttu-id="c0ce7-134">После реализации в коде службы проверяющего элемента управления необходимо проинформировать узел службы о проверяющем элементе управления, который следует использовать.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-134">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="c0ce7-135">Это делается с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="c0ce7-135">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="c0ce7-136">Вы также можете сделать то же самое в конфигурации:</span><span class="sxs-lookup"><span data-stu-id="c0ce7-136">Or you can do the same thing in configuration:</span></span>

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

<span data-ttu-id="c0ce7-137">Windows Communication Foundation (WCF) предоставляет обширную модель на основе утверждений для выполнения проверок доступа.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-137">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="c0ce7-138">Для контроля прав доступа и проверки, удовлетворяют ли связанные с клиентом удостоверения требованиям, необходимым для доступа к методу службы, используется объект <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-138">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="c0ce7-139">Для демонстрации в этом примере показана реализация <xref:System.ServiceModel.ServiceAuthorizationManager> , которая реализует <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> метод, чтобы предоставить пользователю доступ к методам на основе утверждений типа, `http://example.com/claims/allowedoperation` значение которого является универсальным кодом ресурса (URI) операции, которую можно вызвать.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-139">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type `http://example.com/claims/allowedoperation` whose value is the Action URI of the operation that is allowed to be called.</span></span>

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

<span data-ttu-id="c0ce7-140">После реализации пользовательского объекта <xref:System.ServiceModel.ServiceAuthorizationManager> необходимо проинформировать узел службы об объекте<xref:System.ServiceModel.ServiceAuthorizationManager>, который следует использовать.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-140">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="c0ce7-141">Это можно сделать с помощью следующего фрагмента кода.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-141">This is done as shown in the following code.</span></span>

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="c0ce7-142">Основным реализуемым методом <xref:System.IdentityModel.Policy.IAuthorizationPolicy> является метод <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29>.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-142">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

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

<span data-ttu-id="c0ce7-143">В приведенном выше примере кода показано, каким образом метод <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> проверяет, что не было добавлено новых утверждений, которые влияют на обработку, и добавляет нужные утверждения.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-143">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="c0ce7-144">Разрешенные утверждения получаются из метода `GetAllowedOpList`, реализация которого возвращает заданный список операций, которые разрешено выполнять пользователю.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-144">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="c0ce7-145">Политика авторизации добавляет утверждения для доступа к определенной операции.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-145">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="c0ce7-146">Впоследствии эта политика используется объектом <xref:System.ServiceModel.ServiceAuthorizationManager> для принятия решений о предоставлении доступа.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-146">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="c0ce7-147">После реализации интерфейса <xref:System.IdentityModel.Policy.IAuthorizationPolicy> необходимо проинформировать узел службы о политиках авторизации, которые следует использовать.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-147">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="c0ce7-148">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-148">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c0ce7-149">Клиент успешно вызывает методы Add, Subtract и Multiple и получает сообщение "Access is denied" при попытке вызывать метод Divide.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-149">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="c0ce7-150">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-150">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="c0ce7-151">Пакетный файл Setup</span><span class="sxs-lookup"><span data-stu-id="c0ce7-151">Setup Batch File</span></span>

<span data-ttu-id="c0ce7-152">Входящий в состав образца файл Setup.bat позволяет настроить для сервера соответствующие сертификаты, необходимые для выполнения резидентного приложения, которое требует обеспечения безопасности на основе сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-152">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="c0ce7-153">Ниже представлен краткие общие сведения о различных разделах пакетных файлов, позволяющий изменять их для выполнения в соответствующей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-153">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="c0ce7-154">Создание сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-154">Creating the server certificate.</span></span>

    <span data-ttu-id="c0ce7-155">Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-155">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="c0ce7-156">Переменная %SERVER_NAME% задает имя сервера.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-156">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="c0ce7-157">Измените эту переменную, чтобы задать собственное имя сервера.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-157">Change this variable to specify your own server name.</span></span> <span data-ttu-id="c0ce7-158">Значением по умолчанию является localhost.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-158">The default value is localhost.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="c0ce7-159">Установка сертификата сервера в хранилище доверенных сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-159">Installing the server certificate into client's trusted certificate store.</span></span>

    <span data-ttu-id="c0ce7-160">Следующие строки из файла Setup.bat копируют сертификат сервера в хранилище доверенных лиц клиента.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="c0ce7-161">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-161">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="c0ce7-162">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="c0ce7-163">Создание сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-163">Creating the client certificate.</span></span>

    <span data-ttu-id="c0ce7-164">Следующие строки из файла Setup.bat создают сертификат клиента, который будет использоваться.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-164">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="c0ce7-165">Переменная %USER_NAME% задает имя сервера.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-165">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="c0ce7-166">Эта переменная имеет значение "test1", поскольку политика `IAuthorizationPolicy` ищет именно это имя.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-166">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="c0ce7-167">Если изменить значение переменной %USER_NAME%, необходимо изменить и соответствующее значение в методе `IAuthorizationPolicy.Evaluate`.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-167">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

    <span data-ttu-id="c0ce7-168">Сертификат хранится в хранилище "My store" (Личном хранилище) в расположении CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-168">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="c0ce7-169">Установка сертификата клиента в хранилище доверенных сертификатов сервера.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-169">Installing the client certificate into server's trusted certificate store.</span></span>

    <span data-ttu-id="c0ce7-170">Следующие строки из файла Setup.bat копируют сертификат клиента в хранилище доверенных лиц.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-170">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="c0ce7-171">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны серверной системы.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-171">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="c0ce7-172">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата клиента в хранилище сертификатов сервера не требуется.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-172">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="c0ce7-173">Настройка и сборка образца</span><span class="sxs-lookup"><span data-stu-id="c0ce7-173">To set up and build the sample</span></span>

1. <span data-ttu-id="c0ce7-174">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c0ce7-174">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="c0ce7-175">Чтобы запустить образец на одном или нескольких компьютерах, следуйте приведенным далее инструкциям.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-175">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="c0ce7-176">Если для восстановления конфигурации этого образца используется программа Svcutil.exe, измените имя конечной точки в конфигурации клиента, чтобы оно соответствовало клиентскому коду.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-176">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="c0ce7-177">Запуск образца на одном компьютере</span><span class="sxs-lookup"><span data-stu-id="c0ce7-177">To run the sample on the same computer</span></span>

1. <span data-ttu-id="c0ce7-178">Откройте Командная строка разработчика для Visual Studio с правами администратора и запустите *Setup.bat* из примера установочной папки.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-178">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="c0ce7-179">При этом устанавливаются все сертификаты, необходимые для выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-179">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c0ce7-180">Пакетный файл Setup.bat предназначен для запуска из Командная строка разработчика для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-180">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="c0ce7-181">Переменная среды PATH, заданная в Командная строка разработчика для Visual Studio, указывает на каталог, содержащий исполняемые файлы, необходимые для скрипта *Setup.bat* .</span><span class="sxs-lookup"><span data-stu-id="c0ce7-181">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="c0ce7-182">Запустите Service.exe из *сервице\бин*.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-182">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="c0ce7-183">Запустите Client.exe из \*\client\bin\*.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-183">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="c0ce7-184">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-184">Client activity is displayed on the client console application.</span></span>

<span data-ttu-id="c0ce7-185">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c0ce7-185">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="c0ce7-186">Запуск образца на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="c0ce7-186">To run the sample across computers</span></span>

1. <span data-ttu-id="c0ce7-187">Создайте каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-187">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="c0ce7-188">Скопируйте файлы служебной программы из *\сервице\бин* в каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-188">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="c0ce7-189">Кроме того, скопируйте на компьютер службы файлы Setup.bat, Cleanup.bat, GetComputerName.vbs и ImportClientCert.bat.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-189">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="c0ce7-190">Создайте на клиентском компьютере каталог для двоичных файлов клиента.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-190">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="c0ce7-191">Скопируйте в клиентский каталог на клиентском компьютере файлы программы клиента.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-191">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="c0ce7-192">Кроме того, скопируйте на клиент файлы Setup.bat, Cleanup.bat и ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-192">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="c0ce7-193">На сервере запустите `setup.bat service` в Командная строка разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-193">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="c0ce7-194">`setup.bat`При запуске с `service` аргументом создается сертификат службы с полным доменным именем компьютера и экспортируется сертификат службы в файл с именем *Service. cer*.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-194">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="c0ce7-195">Измените *Service.exe.config* , чтобы отразить новое имя сертификата (в `findValue` атрибуте в [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), совпадающее с полным доменным именем компьютера.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-195">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="c0ce7-196">Кроме того, измените **ComputerName** в \<service> / \<baseAddresses> элементе с localhost на полное имя компьютера службы.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-196">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="c0ce7-197">Скопируйте файл *Service. cer* из каталога службы в каталог клиента на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-197">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="c0ce7-198">На клиенте запустите `setup.bat client` в Командная строка разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-198">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="c0ce7-199">`setup.bat`При выполнении с `client` аргументом создается сертификат клиента с именем **test1** и экспортируется сертификат клиента в файл с именем *Client. cer*.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-199">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="c0ce7-200">В файле *Client.exe.config* на клиентском компьютере измените значение адреса конечной точки, чтобы оно совпадало с новым адресом службы.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-200">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="c0ce7-201">Для этого замените **localhost** на полное доменное имя сервера.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-201">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="c0ce7-202">Скопируйте файл Client.cer из клиентского каталога в каталог службы на сервере.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-202">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="c0ce7-203">На клиенте запустите *ImportServiceCert.bat* в Командная строка разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-203">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="c0ce7-204">Сертификат службы будет импортирован из файла Service. cer в хранилище **CurrentUser-TrustedPeople** .</span><span class="sxs-lookup"><span data-stu-id="c0ce7-204">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="c0ce7-205">На сервере запустите *ImportClientCert.bat* в Командная строка разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-205">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="c0ce7-206">При этом сертификат клиента будет импортирован из файла Client. cer в хранилище **LocalMachine-TrustedPeople** .</span><span class="sxs-lookup"><span data-stu-id="c0ce7-206">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="c0ce7-207">На сервере запустите из окна командной строки программу Service.exe.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-207">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="c0ce7-208">На клиентском компьютере из окна командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-208">On the client computer, launch Client.exe from a command prompt window.</span></span>

    <span data-ttu-id="c0ce7-209">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c0ce7-209">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="c0ce7-210">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="c0ce7-210">Clean up after the sample</span></span>

<span data-ttu-id="c0ce7-211">Чтобы очистить после примера, запустите *Cleanup.bat* в папке Samples после завершения выполнения примера.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-211">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="c0ce7-212">Он удалит из хранилища сертификатов сертификаты сервера и клиента.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-212">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="c0ce7-213">Этот скрипт не удаляет сертификаты службы на клиенте при запуске образца на нескольких компьютерах.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-213">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="c0ce7-214">Если вы выполнили примеры WCF, использующие сертификаты на нескольких компьютерах, обязательно очистите сертификаты службы, установленные в хранилище CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-214">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="c0ce7-215">Для этого воспользуйтесь следующей командой: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Например: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="c0ce7-215">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
