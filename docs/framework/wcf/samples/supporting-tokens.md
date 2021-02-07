---
description: 'Дополнительные сведения: поддержка маркеров'
title: Вспомогательные маркеры
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 455c69ce1ae03bd612f78a7977b013955bd81868
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668738"
---
# <a name="supporting-tokens"></a><span data-ttu-id="02fbc-103">Вспомогательные маркеры</span><span class="sxs-lookup"><span data-stu-id="02fbc-103">Supporting Tokens</span></span>

<span data-ttu-id="02fbc-104">Образец вспомогательных маркеров демонстрирует, как добавить дополнительные маркеры в сообщение, использующее WS-Security.</span><span class="sxs-lookup"><span data-stu-id="02fbc-104">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="02fbc-105">Пример добавляет двоичный маркер безопасности X.509 в дополнение к маркеру безопасности имени пользователя.</span><span class="sxs-lookup"><span data-stu-id="02fbc-105">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="02fbc-106">Этот маркер передается в заголовке сообщения WS-Security из клиента в службу, и часть сообщения подписывается закрытым ключом, связанным с маркером безопасности X.509, чтобы подтвердить получателю наличие сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="02fbc-106">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="02fbc-107">Это полезно в случае, когда для проверки подлинности или авторизации отправителя требуются несколько утверждений, связанных с сообщением.</span><span class="sxs-lookup"><span data-stu-id="02fbc-107">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="02fbc-108">Служба реализует контракт, определяющий шаблон взаимодействия "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="02fbc-108">The service implements a contract that defines a request-reply communication pattern.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="02fbc-109">Что демонстрирует</span><span class="sxs-lookup"><span data-stu-id="02fbc-109">Demonstrates</span></span>

 <span data-ttu-id="02fbc-110">Образец демонстрирует следующие приемы.</span><span class="sxs-lookup"><span data-stu-id="02fbc-110">The sample demonstrates:</span></span>

- <span data-ttu-id="02fbc-111">Как клиент может передать в службу дополнительные маркеры безопасности.</span><span class="sxs-lookup"><span data-stu-id="02fbc-111">How a client can pass additional security tokens to a service.</span></span>

- <span data-ttu-id="02fbc-112">Как сервер может получить доступ к утверждениям, связанным с дополнительными маркерами безопасности.</span><span class="sxs-lookup"><span data-stu-id="02fbc-112">How the server can access claims associated with additional security tokens.</span></span>

- <span data-ttu-id="02fbc-113">как сертификат X.509 сервера используется для защиты симметричного ключа, служащего для шифрования и подписывания сообщений.</span><span class="sxs-lookup"><span data-stu-id="02fbc-113">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

> [!NOTE]
> <span data-ttu-id="02fbc-114">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="02fbc-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="02fbc-115">Клиент производит проверку подлинности с помощью маркера имени пользователя и вспомогательного маркера безопасности X.509</span><span class="sxs-lookup"><span data-stu-id="02fbc-115">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>

 <span data-ttu-id="02fbc-116">Служба предоставляет одну конечную точку для взаимодействия, создаваемую программно с помощью классов `BindingHelper` и `EchoServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="02fbc-116">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="02fbc-117">Конечная точка состоит из адреса, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="02fbc-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="02fbc-118">Привязка настраивается с пользовательской привязкой с помощью элементов `SymmetricSecurityBindingElement` и `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="02fbc-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="02fbc-119">В этом образце в элементе `SymmetricSecurityBindingElement` задается использование сертификата X.509 службы для защиты симметричного ключа во время передачи и для передачи маркера `UserNameToken` вместе со вспомогательным маркером `X509SecurityToken` в заголовке сообщения WS-Security.</span><span class="sxs-lookup"><span data-stu-id="02fbc-119">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="02fbc-120">Симметричный ключ используется для шифрования тела сообщения и маркера безопасности с именем пользователя.</span><span class="sxs-lookup"><span data-stu-id="02fbc-120">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="02fbc-121">Вспомогательный маркер передается как дополнительный двоичный маркер безопасности в заголовке сообщения WS-Security.</span><span class="sxs-lookup"><span data-stu-id="02fbc-121">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="02fbc-122">Подлинность вспомогательного маркера подтверждается подписыванием части сообщения закрытым ключом, связанным со вспомогательным маркером безопасности X.509.</span><span class="sxs-lookup"><span data-stu-id="02fbc-122">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>

```csharp
public static Binding CreateMultiFactorAuthenticationBinding()
{
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();

    // the message security binding element will be configured to require 2 tokens:
    // 1) A username-password encrypted with the service token
    // 2) A client certificate used to sign the message

    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();

    // Create supporting token parameters for the client X509 certificate.
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();
    // Specify that the supporting token is passed in message send by the client to the service
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;
    // Turn off derived keys
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);

    // Create a CustomBinding based on the constructed security binding element.
    return new CustomBinding(messageSecurity, httpTransport);
}
```

 <span data-ttu-id="02fbc-123">Поведение задает учетные данные службы, которые должны использоваться для проверки подлинности клиента, а также информацию о сертификате X.509 службы.</span><span class="sxs-lookup"><span data-stu-id="02fbc-123">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="02fbc-124">В этом образце в качестве имени субъекта в сертификате X.509 службы используется `CN=localhost`.</span><span class="sxs-lookup"><span data-stu-id="02fbc-124">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>

```csharp
override protected void InitializeRuntime()
{
    // Extract the ServiceCredentials behavior or create one.
    ServiceCredentials serviceCredentials =
        this.Description.Behaviors.Find<ServiceCredentials>();
    if (serviceCredentials == null)
    {
        serviceCredentials = new ServiceCredentials();
        this.Description.Behaviors.Add(serviceCredentials);
    }

    // Set the service certificate
    serviceCredentials.ServiceCertificate.SetCertificate(
                                       "CN=localhost");

/*
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.
*/
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;

    // Create the custom binding and add an endpoint to the service.
    Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
    this.AddServiceEndpoint(typeof(IEchoService),
                          multipleTokensBinding, string.Empty);
    base.InitializeRuntime();
}
```

 <span data-ttu-id="02fbc-125">Код службы:</span><span class="sxs-lookup"><span data-stu-id="02fbc-125">Service code:</span></span>

```csharp
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]
public class EchoService : IEchoService
{
    public string Echo()
    {
        string userName;
        string certificateSubjectName;
        GetCallerIdentities(
            OperationContext.Current.ServiceSecurityContext,
            out userName,
            out certificateSubjectName);
            return $"Hello {userName}, {certificateSubjectName}";
    }

    public void Dispose()
    {
    }

    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,
            string claimType, out TClaimResource resourceValue)
            where TClaimResource : class
    {
        resourceValue = default(TClaimResource);
        IEnumerable<Claim> matchingClaims =
            claimSet.FindClaims(claimType, Rights.PossessProperty);
        if(matchingClaims == null)
            return false;
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
        if (enumerator.MoveNext())
        {
            resourceValue =
              (enumerator.Current.Resource == null) ? null :
              (enumerator.Current.Resource as TClaimResource);
            return true;
        }
        else
        {
            return false;
        }
    }

    // Returns the username and certificate subject name provided by
    //the client
    void GetCallerIdentities(ServiceSecurityContext
        callerSecurityContext,
        out string userName, out string certificateSubjectName)
    {
        userName = null;
        certificateSubjectName = null;

       // Look in all the claimsets in the authorization context
       foreach (ClaimSet claimSet in
               callerSecurityContext.AuthorizationContext.ClaimSets)
       {
            if (claimSet is WindowsClaimSet)
            {
                // Try to find a Name claim. This will have been
                // generated from the windows username.
                string tmpName;
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                      out tmpName))
                {
                    userName = tmpName;
                }
            }
            else if (claimSet is X509CertificateClaimSet)
            {
                // Try to find an X500DistinguishedName claim. This will
                // have been generated from the client certificate.
                X500DistinguishedName tmpDistinguishedName;
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,
                               ClaimTypes.X500DistinguishedName,
                               out tmpDistinguishedName))
                {
                    certificateSubjectName = tmpDistinguishedName.Name;
                }
            }
        }
    }
}
```

 <span data-ttu-id="02fbc-126">Конечная точка клиента настраивается таким же образом, как и конечная точка службы.</span><span class="sxs-lookup"><span data-stu-id="02fbc-126">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="02fbc-127">Для создания привязки в клиенте используется этот же класс `BindingHelper`.</span><span class="sxs-lookup"><span data-stu-id="02fbc-127">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="02fbc-128">Остальная часть настройки находится в классе `Client`.</span><span class="sxs-lookup"><span data-stu-id="02fbc-128">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="02fbc-129">Клиент в коде настройки задает сведения о маркере безопасности имени пользователя, вспомогательном маркере безопасности X.509 и о сертификате X.509 службы в коллекции поведений конечной точки клиента.</span><span class="sxs-lookup"><span data-stu-id="02fbc-129">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>

```csharp
 static void Main()
 {
     // Create the custom binding and an endpoint address for
     // the service.
     Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
         EndpointAddress serviceAddress = new EndpointAddress(
         "http://localhost/servicemodelsamples/service.svc");
       ChannelFactory<IEchoService> channelFactory = null;
       IEchoService client = null;

       Console.WriteLine("Username authentication required.");
       Console.WriteLine(
         "Provide a valid machine or domain account. [domain\\user]");
       Console.WriteLine("   Enter username:");
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
                    password =
                       password.Substring(0, password.Length - 1);
                }
                info = Console.ReadKey(true);
            }
         }
         for (int i = 0; i < password.Length; i++)
            Console.Write("*");
         Console.WriteLine();
         try
         {
           // Create a proxy with the previously create binding and
           // endpoint address
              channelFactory =
                 new ChannelFactory<IEchoService>(
                     multipleTokensBinding, serviceAddress);
           // configure the username credentials, the client
           // certificate and the server certificate on the channel
           // factory
           channelFactory.Credentials.UserName.UserName = username;
           channelFactory.Credentials.UserName.Password = password;
           channelFactory.Credentials.ClientCertificate.SetCertificate(
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);
           client = channelFactory.CreateChannel();
           Console.WriteLine("Echo service returned: {0}",
                                           client.Echo());

           ((IChannel)client).Close();
           channelFactory.Close();
        }
        catch (CommunicationException e)
        {
         Abort((IChannel)client, channelFactory);
         // if there is a fault then print it out
         FaultException fe = null;
         Exception tmp = e;
         while (tmp != null)
         {
            fe = tmp as FaultException;
            if (fe != null)
            {
                break;
            }
            tmp = tmp.InnerException;
        }
        if (fe != null)
        {
           Console.WriteLine("The server sent back a fault: {0}",
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);
        }
        else
        {
         Console.WriteLine("The request failed with exception: {0}",e);
        }
    }
    catch (TimeoutException)
    {
        Abort((IChannel)client, channelFactory);
        Console.WriteLine("The request timed out");
    }
    catch (Exception e)
    {
         Abort((IChannel)client, channelFactory);
          Console.WriteLine(
          "The request failed with unexpected exception: {0}", e);
    }
    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();
}
```

## <a name="displaying-callers-information"></a><span data-ttu-id="02fbc-130">Отображение информации об абоненте</span><span class="sxs-lookup"><span data-stu-id="02fbc-130">Displaying Callers' Information</span></span>

 <span data-ttu-id="02fbc-131">Для вывода информации об абоненте можно использовать свойство `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="02fbc-131">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="02fbc-132">Свойство `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` содержит утверждения авторизации, связанные с текущим абонентом.</span><span class="sxs-lookup"><span data-stu-id="02fbc-132">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="02fbc-133">Эти утверждения предоставляются автоматически Windows Communication Foundation (WCF) для каждого токена, полученного в сообщении.</span><span class="sxs-lookup"><span data-stu-id="02fbc-133">Those claims are supplied automatically by Windows Communication Foundation (WCF) for every token received in the message.</span></span>

```csharp
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string
                         claimType, out TClaimResource resourceValue)
    where TClaimResource : class
{
    resourceValue = default(TClaimResource);
    IEnumerable<Claim> matchingClaims =
    claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
          return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    if (enumerator.MoveNext())
    {
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);
        return true;
    }
    else
    {
         return false;
    }
}

// Returns the username and certificate subject name provided by the client
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)
{
    userName = null;
    certificateSubjectName = null;

    // Look in all the claimsets in the authorization context
    foreach (ClaimSet claimSet in
      callerSecurityContext.AuthorizationContext.ClaimSets)
    {
        if (claimSet is WindowsClaimSet)
        {
            // Try to find a Name claim. This will have been generated
            //from the windows username.
            string tmpName;
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                     out tmpName))
            {
                userName = tmpName;
            }
        }
        else if (claimSet is X509CertificateClaimSet)
         {
            //Try to find an X500DistinguishedName claim.
            //This will have been generated from the client
            //certificate.
            X500DistinguishedName tmpDistinguishedName;
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,
               ClaimTypes.X500DistinguishedName,
               out tmpDistinguishedName))
            {
                    certificateSubjectName = tmpDistinguishedName.Name;
            }
        }
    }
}
```

## <a name="running-the-sample"></a><span data-ttu-id="02fbc-134">Запуск примера</span><span class="sxs-lookup"><span data-stu-id="02fbc-134">Running the Sample</span></span>

 <span data-ttu-id="02fbc-135">При выполнении образца клиент сначала запрашивает имя пользователя и пароль для маркера имени пользователя.</span><span class="sxs-lookup"><span data-stu-id="02fbc-135">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="02fbc-136">Обязательно укажите правильные значения для системной учетной записи, так как WCF в службе сопоставляет значения, указанные в маркере имени пользователя, с удостоверением, предоставленным системой.</span><span class="sxs-lookup"><span data-stu-id="02fbc-136">Be sure to provide correct values for your system account, because WCF on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="02fbc-137">После этого клиент отображает ответ от службы.</span><span class="sxs-lookup"><span data-stu-id="02fbc-137">After that, the client displays the response from the service.</span></span> <span data-ttu-id="02fbc-138">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="02fbc-138">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="02fbc-139">Пакетный файл Setup</span><span class="sxs-lookup"><span data-stu-id="02fbc-139">Setup Batch File</span></span>

 <span data-ttu-id="02fbc-140">Входящий в состав образца файл Setup.bat позволяет настроить для сервера соответствующие сертификаты, необходимые для выполнения приложения, размещенного в службах IIS, которое требует обеспечения безопасности на основе сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="02fbc-140">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="02fbc-141">Этот пакетный файл необходимо изменить, чтобы его можно было использовать на нескольких компьютерах или без размещения приложения.</span><span class="sxs-lookup"><span data-stu-id="02fbc-141">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>

 <span data-ttu-id="02fbc-142">Ниже представлен краткий обзор различных разделов пакетных файлов, позволяющий изменять их для выполнения в соответствующей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="02fbc-142">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

### <a name="creating-the-client-certificate"></a><span data-ttu-id="02fbc-143">Создание сертификата клиента</span><span class="sxs-lookup"><span data-stu-id="02fbc-143">Creating the Client Certificate</span></span>

 <span data-ttu-id="02fbc-144">Следующие строки из файла Setup.bat создают сертификат клиента, который будет использоваться.</span><span class="sxs-lookup"><span data-stu-id="02fbc-144">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="02fbc-145">Переменная `%CLIENT_NAME%` задает субъект сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="02fbc-145">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="02fbc-146">В этом образце в качестве имени субъекта используется "client.com".</span><span class="sxs-lookup"><span data-stu-id="02fbc-146">This sample uses "client.com" as the subject name.</span></span>

 <span data-ttu-id="02fbc-147">Сертификат хранится в хранилище "My store" (Личном хранилище) в расположении `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="02fbc-147">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>

```console
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="02fbc-148">Установка сертификата клиента в хранилище доверенных сертификатов сервера</span><span class="sxs-lookup"><span data-stu-id="02fbc-148">Installing the Client Certificate into the Server's Trusted Store</span></span>

 <span data-ttu-id="02fbc-149">Следующая строка из файла Setup.bat копирует сертификат клиента в хранилище доверенных лиц сервера.</span><span class="sxs-lookup"><span data-stu-id="02fbc-149">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="02fbc-150">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны серверной системы.</span><span class="sxs-lookup"><span data-stu-id="02fbc-150">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="02fbc-151">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="02fbc-151">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```console
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a><span data-ttu-id="02fbc-152">Создание сертификата сервера</span><span class="sxs-lookup"><span data-stu-id="02fbc-152">Creating the Server Certificate</span></span>

 <span data-ttu-id="02fbc-153">Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="02fbc-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="02fbc-154">Переменная `%SERVER_NAME%`задает имя сервера.</span><span class="sxs-lookup"><span data-stu-id="02fbc-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="02fbc-155">Измените эту переменную, чтобы задать собственное имя сервера.</span><span class="sxs-lookup"><span data-stu-id="02fbc-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="02fbc-156">По умолчанию в этом пакетном файле используется имя localhost.</span><span class="sxs-lookup"><span data-stu-id="02fbc-156">The default in this batch file is localhost.</span></span>

 <span data-ttu-id="02fbc-157">Сертификат хранится в хранилище «My store (Личном хранилище)» в расположении LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="02fbc-157">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="02fbc-158">Для служб, размещенных в службах IIS, сертификат хранится в хранилище LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="02fbc-158">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="02fbc-159">Для резидентных служб необходимо изменить пакетный файл, чтобы сертификат сервера хранился в местоположении хранения CurrentUser, заменив строку LocalMachine строкой CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="02fbc-159">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

```console
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="02fbc-160">Установка сертификата сервера в хранилище доверенных сертификатов клиента</span><span class="sxs-lookup"><span data-stu-id="02fbc-160">Installing Server Certificate into Client's Trusted Certificate Store</span></span>

 <span data-ttu-id="02fbc-161">Следующие строки из файла Setup.bat копируют сертификат сервера в хранилище доверенных лиц клиента.</span><span class="sxs-lookup"><span data-stu-id="02fbc-161">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="02fbc-162">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы.</span><span class="sxs-lookup"><span data-stu-id="02fbc-162">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="02fbc-163">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="02fbc-163">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```console
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="02fbc-164">Обеспечение доступа к закрытому ключу сертификата</span><span class="sxs-lookup"><span data-stu-id="02fbc-164">Enabling Access to the Certificate's Private Key</span></span>

 <span data-ttu-id="02fbc-165">Чтобы разрешить доступ к закрытому ключу сертификата из службы, размещенной в службах IIS, учетной записи пользователя, под которой выполняется процесс, размещенный в службах IIS, должны быть предоставлены соответствующие разрешения для закрытого ключа.</span><span class="sxs-lookup"><span data-stu-id="02fbc-165">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="02fbc-166">Это производится в последних шагах скрипта Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="02fbc-166">This is accomplished by last steps in the Setup.bat script.</span></span>

```console
echo ************
echo setting privileges on server certificates
echo ************
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
iisreset
```

##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="02fbc-167">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="02fbc-167">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="02fbc-168">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="02fbc-168">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="02fbc-169">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="02fbc-169">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="02fbc-170">Чтобы выполнить образец на одном или нескольких компьютерах, выполните следующие инструкции.</span><span class="sxs-lookup"><span data-stu-id="02fbc-170">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="02fbc-171">Запуск образца на том же компьютере</span><span class="sxs-lookup"><span data-stu-id="02fbc-171">To run the sample on the same machine</span></span>

1. <span data-ttu-id="02fbc-172">Запустите Setup.bat из папки примера установки в командной строке Visual Studio 2012 и выполните команду с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="02fbc-172">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="02fbc-173">При этом устанавливаются все сертификаты, необходимые для выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="02fbc-173">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="02fbc-174">Пакетный файл Setup.bat предназначен для запуска из командной строки Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="02fbc-174">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="02fbc-175">Переменная среды PATH, заданная в командной строке Visual Studio 2012, указывает на каталог, содержащий исполняемые файлы, необходимые для скрипта Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="02fbc-175">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="02fbc-176">После завершения работы с образцом для удаления сертификатов обязательно запустите файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="02fbc-176">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="02fbc-177">В других образцах обеспечения безопасности используются те же сертификаты.</span><span class="sxs-lookup"><span data-stu-id="02fbc-177">Other security samples use the same certificates.</span></span>  
  
2. <span data-ttu-id="02fbc-178">Запустите программу Client.exe из каталога \client\bin.</span><span class="sxs-lookup"><span data-stu-id="02fbc-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="02fbc-179">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="02fbc-179">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="02fbc-180">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="02fbc-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="02fbc-181">Выполнение примера на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="02fbc-181">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="02fbc-182">Создайте каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="02fbc-182">Create a directory on the service machine.</span></span> <span data-ttu-id="02fbc-183">Создайте для этого каталога виртуальное приложение servicemodelsamples, воспользовавшись для этого средством управления службами IIS.</span><span class="sxs-lookup"><span data-stu-id="02fbc-183">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="02fbc-184">Скопируйте файлы программы службы из каталога \inetpub\wwwroot\servicemodelsamples в виртуальный каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="02fbc-184">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="02fbc-185">Убедитесь, что скопированы все файлы из подкаталога \bin.</span><span class="sxs-lookup"><span data-stu-id="02fbc-185">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="02fbc-186">Кроме того, скопируйте файлы Cleanup.bat и ImportClientCert.bat на компьютер службы.</span><span class="sxs-lookup"><span data-stu-id="02fbc-186">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="02fbc-187">Создайте на клиентском компьютере каталог для двоичных файлов клиента.</span><span class="sxs-lookup"><span data-stu-id="02fbc-187">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="02fbc-188">Скопируйте в клиентский каталог на клиентском компьютере файлы программы клиента.</span><span class="sxs-lookup"><span data-stu-id="02fbc-188">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="02fbc-189">Кроме того, скопируйте на клиент файлы Setup.bat, Cleanup.bat и ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="02fbc-189">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="02fbc-190">На сервере запустите `setup.bat service` в Командная строка разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="02fbc-190">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="02fbc-191">`setup.bat`При запуске с `service` аргументом создается сертификат службы с полным доменным именем компьютера и экспортируется сертификат службы в файл с именем Service. cer.</span><span class="sxs-lookup"><span data-stu-id="02fbc-191">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="02fbc-192">Измените Web.config, чтобы отразить новое имя сертификата (в `findValue` атрибуте в [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), совпадающее с полным доменным именем компьютера.</span><span class="sxs-lookup"><span data-stu-id="02fbc-192">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7. <span data-ttu-id="02fbc-193">Скопируйте файл Service.cer из каталога службы в клиентский каталог на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="02fbc-193">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="02fbc-194">На клиенте запустите `setup.bat client` в Командная строка разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="02fbc-194">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="02fbc-195">При выполнении команды `setup.bat`с аргументом `client` создается сертификат клиента с именем client.com, который экспортируется в файл с именем Client.cer.</span><span class="sxs-lookup"><span data-stu-id="02fbc-195">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="02fbc-196">В файле Client.exe.config на клиентском компьютере измените значение адреса конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="02fbc-196">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="02fbc-197">Для этого замените имя localhost полным доменным именем сервера.</span><span class="sxs-lookup"><span data-stu-id="02fbc-197">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="02fbc-198">Скопируйте файл Client.cer из клиентского каталога в каталог службы на сервере.</span><span class="sxs-lookup"><span data-stu-id="02fbc-198">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="02fbc-199">Запустите на клиенте файл ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="02fbc-199">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="02fbc-200">Он импортирует сертификат службы из файла Service.cer в хранилище CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="02fbc-200">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="02fbc-201">На сервере запустите файл ImportClientCert.bat. Он импортирует сертификат клиента из файла Client.cer в хранилище LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="02fbc-201">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="02fbc-202">На клиентском компьютере из окна командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="02fbc-202">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="02fbc-203">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="02fbc-203">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="02fbc-204">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="02fbc-204">To clean up after the sample</span></span>  
  
- <span data-ttu-id="02fbc-205">После завершения работы примера запустите в папке примеров файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="02fbc-205">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02fbc-206">Этот скрипт не удаляет сертификаты службы на клиенте при выполнении примера на нескольких компьютерах.</span><span class="sxs-lookup"><span data-stu-id="02fbc-206">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="02fbc-207">Если вы выполнили примеры WCF, использующие сертификаты на разных компьютерах, не забудьте очистить сертификаты службы, установленные в хранилище CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="02fbc-207">If you have run WCF samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="02fbc-208">Для этого воспользуйтесь следующей командой: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Например: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="02fbc-208">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
