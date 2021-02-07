---
description: 'Дополнительные сведения: Пользовательский токен'
title: Пользовательский маркер
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: 500cc187db0280e508ef079ca370483c716ea2c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752435"
---
# <a name="custom-token"></a><span data-ttu-id="2e52d-103">Пользовательский маркер</span><span class="sxs-lookup"><span data-stu-id="2e52d-103">Custom Token</span></span>

<span data-ttu-id="2e52d-104">В этом образце показано, как добавить пользовательскую реализацию токена в приложение Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2e52d-104">This sample demonstrates how to add a custom token implementation into a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="2e52d-105">В этом примере маркер `CreditCardToken` используется для безопасной передачи информации о кредитных картах клиента в службу.</span><span class="sxs-lookup"><span data-stu-id="2e52d-105">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="2e52d-106">Маркер передается в заголовок сообщения WS-Security, подписывается и шифруется с помощью симметричного элемента привязки безопасности вместе с телом и другими заголовками сообщения.</span><span class="sxs-lookup"><span data-stu-id="2e52d-106">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="2e52d-107">Это полезно в случаях, когда встроенных маркеров недостаточно.</span><span class="sxs-lookup"><span data-stu-id="2e52d-107">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="2e52d-108">В этом образце показано, как предоставить пользовательский маркер безопасности службы вместо того, чтобы использовать встроенные маркеры.</span><span class="sxs-lookup"><span data-stu-id="2e52d-108">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="2e52d-109">Служба реализует контракт, определяющий шаблон взаимодействия "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="2e52d-109">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="2e52d-110">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="2e52d-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="2e52d-111">Итак, этот образец демонстрирует следующее:</span><span class="sxs-lookup"><span data-stu-id="2e52d-111">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="2e52d-112">как клиент может передать в службу пользовательские маркеры безопасности;</span><span class="sxs-lookup"><span data-stu-id="2e52d-112">How a client can pass a custom security token to a service.</span></span>

- <span data-ttu-id="2e52d-113">как служба может использовать и проверить пользовательский маркер безопасности;</span><span class="sxs-lookup"><span data-stu-id="2e52d-113">How the service can consume and validate a custom security token.</span></span>

- <span data-ttu-id="2e52d-114">Как код службы WCF может получить сведения о полученных маркерах безопасности, включая настраиваемый маркер безопасности.</span><span class="sxs-lookup"><span data-stu-id="2e52d-114">How the WCF service code can obtain the information about received security tokens including the custom security token.</span></span>

- <span data-ttu-id="2e52d-115">как сертификат X.509 сервера используется для защиты симметричного ключа, служащего для шифрования и подписывания сообщений.</span><span class="sxs-lookup"><span data-stu-id="2e52d-115">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="2e52d-116">Проверка подлинности клиента с помощью пользовательского маркера безопасности</span><span class="sxs-lookup"><span data-stu-id="2e52d-116">Client Authentication Using a Custom Security Token</span></span>

 <span data-ttu-id="2e52d-117">Служба предоставляет одну конечную точку, создаваемую программно с помощью классов `BindingHelper` и `EchoServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-117">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="2e52d-118">Конечная точка состоит из адреса, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="2e52d-118">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="2e52d-119">Привязка настраивается с пользовательской привязкой с помощью элементов `SymmetricSecurityBindingElement` и `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-119">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="2e52d-120">В этом образце элементу `SymmetricSecurityBindingElement` задается использование сертификата X.509 службы для защиты симметричного ключа во время передачи и для передачи пользовательского маркера `CreditCardToken` в заголовке сообщения WS-Security в виде подписанного и зашифрованного маркера безопасности.</span><span class="sxs-lookup"><span data-stu-id="2e52d-120">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="2e52d-121">Поведение задает учетные данные службы, которые должны использоваться для проверки подлинности клиента, а также информацию о сертификате X.509 службы.</span><span class="sxs-lookup"><span data-stu-id="2e52d-121">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>

```csharp
public static class BindingHelper
{
    public static Binding CreateCreditCardBinding()
    {
        var httpTransport = new HttpTransportBindingElement();

        // The message security binding element will be configured to require a credit card.
        // The token that is encrypted with the service's certificate.
        var messageSecurity = new SymmetricSecurityBindingElement();
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;
        return new CustomBinding(messageSecurity, httpTransport);
    }
}
```

 <span data-ttu-id="2e52d-122">Чтобы реализовать возможность использования в сообщении маркера кредитной карты, в образце используются пользовательские учетные данные службы.</span><span class="sxs-lookup"><span data-stu-id="2e52d-122">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="2e52d-123">Класс учетных данных службы располагается в классе `CreditCardServiceCredentials` и добавляется к коллекциям поведений узла службы в методе `EchoServiceHost.InitializeRuntime`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-123">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>

```csharp
class EchoServiceHost : ServiceHost
{
    string creditCardFile;

    public EchoServiceHost(parameters Uri[] addresses)
        : base(typeof(EchoService), addresses)
    {
        creditCardFile = ConfigurationManager.AppSettings["creditCardFile"];
        if (string.IsNullOrEmpty(creditCardFile))
        {
            throw new ConfigurationErrorsException("creditCardFile not specified in service config");
        }

        creditCardFile = String.Format("{0}\\{1}", System.Web.Hosting.HostingEnvironment.ApplicationPhysicalPath, creditCardFile);
    }

    override protected void InitializeRuntime()
    {
        // Create a credit card service credentials and add it to the behaviors.
        CreditCardServiceCredentials serviceCredentials = new CreditCardServiceCredentials(this.creditCardFile);
        serviceCredentials.ServiceCertificate.SetCertificate("CN=localhost", StoreLocation.LocalMachine, StoreName.My);
        this.Description.Behaviors.Remove((typeof(ServiceCredentials)));
        this.Description.Behaviors.Add(serviceCredentials);

        // Register a credit card binding for the endpoint.
        Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
        this.AddServiceEndpoint(typeof(IEchoService), creditCardBinding, string.Empty);

        base.InitializeRuntime();
    }
}
```

 <span data-ttu-id="2e52d-124">Конечная точка клиента настраивается таким же образом, как и конечная точка службы.</span><span class="sxs-lookup"><span data-stu-id="2e52d-124">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="2e52d-125">Для создания привязки в клиенте используется этот же класс `BindingHelper`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-125">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="2e52d-126">Остальная часть настройки находится в классе `Client`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-126">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="2e52d-127">Клиент в коде настройки также задает сведения, которые должны содержаться в `CreditCardToken`, и сведения о сертификате X.509 службы посредством добавления экземпляра `CreditCardClientCredentials` с соответствующими данными в коллекцию поведений конечной точки клиента.</span><span class="sxs-lookup"><span data-stu-id="2e52d-127">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="2e52d-128">В этом образце в качестве сертификата службы используется сертификат X.509 службы, которому задано значение `CN=localhost`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-128">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>

```csharp
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
var serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration.
channelFactory = new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

// Configure the credit card credentials on the channel factory.
var credentials =
      new CreditCardClientCredentials(
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));
// Configure the service certificate on the credentials.
credentials.ServiceCertificate.SetDefaultCertificate(
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);

// Replace ClientCredentials with CreditCardClientCredentials.
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
channelFactory.Endpoint.Behaviors.Add(credentials);

client = channelFactory.CreateChannel();

Console.WriteLine($"Echo service returned: {client.Echo()}");

((IChannel)client).Close();
channelFactory.Close();
```

## <a name="custom-security-token-implementation"></a><span data-ttu-id="2e52d-129">Реализация пользовательского маркера безопасности</span><span class="sxs-lookup"><span data-stu-id="2e52d-129">Custom Security Token Implementation</span></span>

 <span data-ttu-id="2e52d-130">Чтобы включить настраиваемый маркер безопасности в WCF, создайте объектное представление пользовательского маркера безопасности.</span><span class="sxs-lookup"><span data-stu-id="2e52d-130">To enable a custom security token in WCF, create an object representation of the custom security token.</span></span> <span data-ttu-id="2e52d-131">В этом образце представление находится в классе `CreditCardToken`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-131">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="2e52d-132">Представление объекта отвечает за хранение всех данных, относящихся к маркеру безопасности, и предоставление списка ключей безопасности, содержащихся в маркере безопасности.</span><span class="sxs-lookup"><span data-stu-id="2e52d-132">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="2e52d-133">В этом случае маркер безопасности кредитной карты не содержит ключ безопасности.</span><span class="sxs-lookup"><span data-stu-id="2e52d-133">In this case, the credit card security token does not contain any security key.</span></span>

 <span data-ttu-id="2e52d-134">В следующем разделе описывается, что необходимо сделать, чтобы включить настраиваемый токен для передачи по сети и использования в конечной точке WCF.</span><span class="sxs-lookup"><span data-stu-id="2e52d-134">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a WCF endpoint.</span></span>

```csharp
class CreditCardToken : SecurityToken
{
    CreditCardInfo cardInfo;
    DateTime effectiveTime = DateTime.UtcNow;
    string id;
    ReadOnlyCollection<SecurityKey> securityKeys;

    public CreditCardToken(CreditCardInfo cardInfo) : this(cardInfo, Guid.NewGuid().ToString()) { }

    public CreditCardToken(CreditCardInfo cardInfo, string id)
    {
        if (cardInfo == null)
            throw new ArgumentNullException(nameof(cardInfo));

        if (id == null)
            throw new ArgumentNullException(nameof(id));

        this.cardInfo = cardInfo;
        this.id = id;

        // The credit card token is not capable of any cryptography.
        this.securityKeys = new ReadOnlyCollection<SecurityKey>(new List<SecurityKey>());
    }

    public CreditCardInfo CardInfo { get { return this.cardInfo; } }

    public override ReadOnlyCollection<SecurityKey> SecurityKeys { get { return this.securityKeys; } }

    public override DateTime ValidFrom { get { return this.effectiveTime; } }
    public override DateTime ValidTo { get { return this.cardInfo.ExpirationDate; } }
    public override string Id { get { return this.id; } }
}
```

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="2e52d-135">Возвращение пользовательского маркера кредитной карты в сообщение и из сообщения</span><span class="sxs-lookup"><span data-stu-id="2e52d-135">Getting the Custom Credit Card Token to and from the Message</span></span>

 <span data-ttu-id="2e52d-136">Сериализаторы маркеров безопасности в WCF отвечают за создание объектного представления маркеров безопасности из XML-кода в сообщении и создание XML-формы маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="2e52d-136">Security token serializers in WCF are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="2e52d-137">Они также выполняют другие действия, такие как чтение и запись идентификаторов ключей, указывающих на маркеры безопасности, но в этом примере используются только функции, связанные с маркерами безопасности.</span><span class="sxs-lookup"><span data-stu-id="2e52d-137">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="2e52d-138">Чтобы включить пользовательский маркер необходимо реализовать собственный сериализатор маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="2e52d-138">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="2e52d-139">В этом образце для этой цели используется класс `CreditCardSecurityTokenSerializer`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-139">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>

 <span data-ttu-id="2e52d-140">На стороне службы пользовательский сериализатор считывает XML-форму пользовательского маркера и создает из нее представление объекта пользовательского маркера.</span><span class="sxs-lookup"><span data-stu-id="2e52d-140">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>

 <span data-ttu-id="2e52d-141">На стороне клиента класс `CreditCardSecurityTokenSerializer` записывает данные, содержащиеся в представлении объекта маркера безопасности, в средство записи XML.</span><span class="sxs-lookup"><span data-stu-id="2e52d-141">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>

```csharp
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer
{
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }

    protected override bool CanReadTokenCore(XmlReader reader)
    {
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);

        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
            return true;

        return base.CanReadTokenCore(reader);
    }

    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)
    {
        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
        {
            string id = reader.GetAttribute(Constants.Id, Constants.WsUtilityNamespace);

            reader.ReadStartElement();

            // Read the credit card number.
            string creditCardNumber = reader.ReadElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace);

            // Read the expiration date.
            string expirationTimeString = reader.ReadElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace);
            DateTime expirationTime = XmlConvert.ToDateTime(expirationTimeString, XmlDateTimeSerializationMode.Utc);

            // Read the issuer of the credit card.
            string creditCardIssuer = reader.ReadElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace);
            reader.ReadEndElement();

            var cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);

            return new CreditCardToken(cardInfo, id);
        }
        else
        {
            return WSSecurityTokenSerializer.DefaultInstance.ReadToken(reader, tokenResolver);
        }
    }

    protected override bool CanWriteTokenCore(SecurityToken token)
    {
        if (token is CreditCardToken)
            return true;
        return base.CanWriteTokenCore(token);
    }

    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)
    {
        if (writer == null)
            throw new ArgumentNullException(nameof(writer));
        if (token == null)
            throw new ArgumentNullException(nameof(token));

        CreditCardToken c = token as CreditCardToken;
        if (c != null)
        {
            writer.WriteStartElement(Constants.CreditCardTokenPrefix, Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace);
            writer.WriteAttributeString(Constants.WsUtilityPrefix, Constants.Id, Constants.WsUtilityNamespace, token.Id);
            writer.WriteElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardNumber);
            writer.WriteElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace, XmlConvert.ToString(c.CardInfo.ExpirationDate, XmlDateTimeSerializationMode.Utc));
            writer.WriteElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardIssuer);
            writer.WriteEndElement();
            writer.Flush();
        }
        else
        {
            base.WriteTokenCore(writer, token);
        }
    }
}
```

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="2e52d-142">Создание поставщика маркеров и классов структуры проверки подлинности маркеров</span><span class="sxs-lookup"><span data-stu-id="2e52d-142">How Token Provider and Token Authenticator Classes are Created</span></span>

 <span data-ttu-id="2e52d-143">Учетные данные клиента и службы отвечают за предоставление экземпляра диспетчера маркера безопасности.</span><span class="sxs-lookup"><span data-stu-id="2e52d-143">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="2e52d-144">Экземпляр диспетчера маркера безопасности используется для возвращения поставщиков, структур проверки подлинности и сериализаторов маркеров.</span><span class="sxs-lookup"><span data-stu-id="2e52d-144">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>

 <span data-ttu-id="2e52d-145">Поставщик маркеров создает представление объекта маркера на основании сведений учетных данных клиента или службы.</span><span class="sxs-lookup"><span data-stu-id="2e52d-145">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="2e52d-146">Затем представление объекта маркера записывается в сообщение с помощью сериализатора маркеров (об этом говорится в предыдущем разделе).</span><span class="sxs-lookup"><span data-stu-id="2e52d-146">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>

 <span data-ttu-id="2e52d-147">Структура проверки подлинности маркеров проверяет маркеры, получаемые в сообщении.</span><span class="sxs-lookup"><span data-stu-id="2e52d-147">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="2e52d-148">Сериализатор маркера создает представление объекта входящего маркера.</span><span class="sxs-lookup"><span data-stu-id="2e52d-148">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="2e52d-149">Это представление объекта затем передается в структуру проверки подлинности маркеров для проверки.</span><span class="sxs-lookup"><span data-stu-id="2e52d-149">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="2e52d-150">После успешной проверки маркера структура проверки подлинности возвращает коллекцию объектов `IAuthorizationPolicy`, представляющих сведения, содержащиеся в маркере.</span><span class="sxs-lookup"><span data-stu-id="2e52d-150">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="2e52d-151">Эти сведения затем используются при обработке сообщения для принятия решений об авторизации и предоставления утверждений для приложения.</span><span class="sxs-lookup"><span data-stu-id="2e52d-151">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="2e52d-152">В этом примере с этой целью структура проверки подлинности маркера кредитной карты использует `CreditCardTokenAuthorizationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-152">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>

 <span data-ttu-id="2e52d-153">Сериализатор маркеров отвечает за возвращение представления объекта маркера в сеть и из сети.</span><span class="sxs-lookup"><span data-stu-id="2e52d-153">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="2e52d-154">Об этом говорилось в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="2e52d-154">This is discussed in the previous section.</span></span>

 <span data-ttu-id="2e52d-155">В этом образце поставщик маркеров используется только на стороне клиента, а структура проверки подлинности только на стороне службы, поскольку маркер кредитной карты требуется передать только в направлении от клиента к службе.</span><span class="sxs-lookup"><span data-stu-id="2e52d-155">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>

 <span data-ttu-id="2e52d-156">Функции на стороне клиента находятся в классах `CreditCardClientCredentials`, `CreditCardClientCredentialsSecurityTokenManager` и `CreditCardTokenProvider`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-156">The functionality on the client is located in the `CreditCardClientCredentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>

 <span data-ttu-id="2e52d-157">Функции на стороне службы находятся в классах `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` и `CreditCardTokenAuthorizationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-157">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>

```csharp
    public class CreditCardClientCredentials : ClientCredentials
    {
        CreditCardInfo creditCardInfo;

        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)
            : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

            this.creditCardInfo = creditCardInfo;
        }

        public CreditCardInfo CreditCardInfo
        {
            get { return this.creditCardInfo; }
        }

        protected override ClientCredentials CloneCore()
        {
            return new CreditCardClientCredentials(this.creditCardInfo);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardClientCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardClientCredentialsSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        CreditCardClientCredentials creditCardClientCredentials;

        public CreditCardClientCredentialsSecurityTokenManager(CreditCardClientCredentials creditCardClientCredentials)
            : base (creditCardClientCredentials)
        {
            this.creditCardClientCredentials = creditCardClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // Handle this token for Custom.
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);
            // Return server cert.
            else if (tokenRequirement is InitiatorServiceModelSecurityTokenRequirement)
            {
                if (tokenRequirement.TokenType == SecurityTokenTypes.X509Certificate)
                {
                    return new X509SecurityTokenProvider(creditCardClientCredentials.ServiceCertificate.DefaultCertificate);
                }
            }

            return base.CreateSecurityTokenProvider(tokenRequirement);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {

            return new CreditCardSecurityTokenSerializer(version);
        }

    }

    class CreditCardTokenProvider : SecurityTokenProvider
    {
        CreditCardInfo creditCardInfo;

        public CreditCardTokenProvider(CreditCardInfo creditCardInfo) : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

            this.creditCardInfo = creditCardInfo;
        }

        protected override SecurityToken GetTokenCore(TimeSpan timeout)
        {
            SecurityToken result = new CreditCardToken(this.creditCardInfo);
            return result;
        }
    }

    public class CreditCardServiceCredentials : ServiceCredentials
    {
        string creditCardFile;

        public CreditCardServiceCredentials(string creditCardFile)
            : base()
        {
            if (creditCardFile == null)
                throw new ArgumentNullException(nameof(creditCardFile));

            this.creditCardFile = creditCardFile;
        }

        public string CreditCardDataFile
        {
            get { return this.creditCardFile; }
        }

        protected override ServiceCredentials CloneCore()
        {
            return new CreditCardServiceCredentials(this.creditCardFile);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardServiceCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardServiceCredentialsSecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        CreditCardServiceCredentials creditCardServiceCredentials;

        public CreditCardServiceCredentialsSecurityTokenManager(CreditCardServiceCredentials creditCardServiceCredentials)
            : base(creditCardServiceCredentials)
        {
            this.creditCardServiceCredentials = creditCardServiceCredentials;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
            {
                outOfBandTokenResolver = null;
                return new CreditCardTokenAuthenticator(creditCardServiceCredentials.CreditCardDataFile);
            }

            return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {
            return new CreditCardSecurityTokenSerializer(version);
        }
    }

    class CreditCardTokenAuthenticator : SecurityTokenAuthenticator
    {
        string creditCardsFile;
        public CreditCardTokenAuthenticator(string creditCardsFile)
        {
            this.creditCardsFile = creditCardsFile;
        }

        protected override bool CanValidateTokenCore(SecurityToken token)
        {
            return (token is CreditCardToken);
        }

        protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateTokenCore(SecurityToken token)
        {
            CreditCardToken creditCardToken = token as CreditCardToken;

            if (creditCardToken.CardInfo.ExpirationDate < DateTime.UtcNow)
                throw new SecurityTokenValidationException("The credit card has expired.");
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))
                throw new SecurityTokenValidationException("Unknown or invalid credit card.");

            // the credit card token has only 1 claim - the card number. The issuer for the claim is the
            // credit card issuer

            var cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));
            var cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));
            var policies = new List<IAuthorizationPolicy>(1);
            policies.Add(new CreditCardTokenAuthorizationPolicy(cardClaimSet));
            return policies.AsReadOnly();
        }

        /// <summary>
        /// Helper method to check if a given credit card entry is present in the User DB
        /// </summary>
        private bool IsCardNumberAndExpirationValid(CreditCardInfo cardInfo)
        {
            try
            {
                using (var myStreamReader = new StreamReader(this.creditCardsFile))
                {
                    string line = "";
                    while ((line = myStreamReader.ReadLine()) != null)
                    {
                        string[] splitEntry = line.Split('#');
                        if (splitEntry[0] == cardInfo.CardNumber)
                        {
                            string expirationDateString = splitEntry[1].Trim();
                            DateTime expirationDateOnFile = DateTime.Parse(expirationDateString, System.Globalization.DateTimeFormatInfo.InvariantInfo, System.Globalization.DateTimeStyles.AdjustToUniversal);
                            if (cardInfo.ExpirationDate == expirationDateOnFile)
                            {
                                string issuer = splitEntry[2];
                                return issuer.Equals(cardInfo.CardIssuer, StringComparison.InvariantCultureIgnoreCase);
                            }
                            else
                            {
                                return false;
                            }
                        }
                    }
                    return false;
                }
            }
            catch (Exception e)
            {
                throw new Exception("BookStoreService: Error while retrieving credit card information from User DB " + e.ToString());
            }
        }
    }

    public class CreditCardTokenAuthorizationPolicy : IAuthorizationPolicy
    {
        string id;
        ClaimSet issuer;
        IEnumerable<ClaimSet> issuedClaimSets;

        public CreditCardTokenAuthorizationPolicy(ClaimSet issuedClaims)
        {
            if (issuedClaims == null)
                throw new ArgumentNullException(nameof(issuedClaims));
            this.issuer = issuedClaims.Issuer;
            this.issuedClaimSets = new ClaimSet[] { issuedClaims };
            this.id = Guid.NewGuid().ToString();
        }

        public ClaimSet Issuer { get { return this.issuer; } }

        public string Id { get { return this.id; } }

        public bool Evaluate(EvaluationContext context, ref object state)
        {
            foreach (ClaimSet issuance in this.issuedClaimSets)
            {
                context.AddClaimSet(this, issuance);
            }

            return true;
        }
    }
```

## <a name="displaying-the-callers-information"></a><span data-ttu-id="2e52d-158">Отображение информации об абоненте</span><span class="sxs-lookup"><span data-stu-id="2e52d-158">Displaying the Callers' Information</span></span>

 <span data-ttu-id="2e52d-159">Для вывода информации об абоненте можно использовать свойство `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="2e52d-159">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="2e52d-160">Свойство `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` содержит утверждения авторизации, связанные с текущим абонентом.</span><span class="sxs-lookup"><span data-stu-id="2e52d-160">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="2e52d-161">Утверждения предоставляются классом `CreditCardToken` в его коллекции `AuthorizationPolicies`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-161">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>

```csharp
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)
{
    claimValue = null;
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
        return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    enumerator.MoveNext();
    claimValue = (enumerator.Current.Resource == null) ? null :
        enumerator.Current.Resource.ToString();
    return true;
}

string GetCallerCreditCardNumber()
{
     foreach (ClaimSet claimSet in
         ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)
     {
         string creditCardNumber = null;
         if (TryGetStringClaimValue(claimSet,
             Constants.CreditCardNumberClaim, out creditCardNumber))
             {
                 string issuer;
                 if (!TryGetStringClaimValue(claimSet.Issuer,
                        ClaimTypes.Name, out issuer))
                 {
                     issuer = "Unknown";
                 }
                 return $"Credit card '{creditCardNumber}' issued by '{issuer}'";
        }
    }
    return "Credit card is not known";
}
```

 <span data-ttu-id="2e52d-162">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="2e52d-162">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2e52d-163">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="2e52d-163">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="2e52d-164">Пакетный файл Setup</span><span class="sxs-lookup"><span data-stu-id="2e52d-164">Setup Batch File</span></span>

 <span data-ttu-id="2e52d-165">Входящий в состав образца пакетный файл Setup.bat позволяет настроить для сервера соответствующие сертификаты, необходимые для выполнения приложения, размещенного в службах IIS, которое требует обеспечения безопасности на основе сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="2e52d-165">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="2e52d-166">Этот пакетный файл необходимо изменить, чтобы его можно было использовать на нескольких компьютерах или без размещения приложения.</span><span class="sxs-lookup"><span data-stu-id="2e52d-166">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="2e52d-167">Ниже представлены общие сведения о различных разделах пакетных файлов, позволяющие изменять их для выполнения в соответствующей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="2e52d-167">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="2e52d-168">Создание сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="2e52d-168">Creating the server certificate:</span></span>

     <span data-ttu-id="2e52d-169">Следующие строки из файла `Setup.bat` создают используемый в дальнейшем сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="2e52d-169">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="2e52d-170">Переменная `%SERVER_NAME%`задает имя сервера.</span><span class="sxs-lookup"><span data-stu-id="2e52d-170">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="2e52d-171">Измените эту переменную, чтобы задать собственное имя сервера.</span><span class="sxs-lookup"><span data-stu-id="2e52d-171">Change this variable to specify your own server name.</span></span> <span data-ttu-id="2e52d-172">По умолчанию в этом пакетном файле используется имя localhost.</span><span class="sxs-lookup"><span data-stu-id="2e52d-172">The default in this batch file is localhost.</span></span> <span data-ttu-id="2e52d-173">При изменении переменной `%SERVER_NAME%` требуется заменить все вхождения "localhost" в файлах Client.cs и Service.cs именем сервера, используемым в скрипте Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="2e52d-173">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>

     <span data-ttu-id="2e52d-174">Сертификат хранится в хранилище "My store" (Личном хранилище) в расположении `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="2e52d-174">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="2e52d-175">Для служб, размещенных в службах IIS, сертификат хранится в хранилище LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="2e52d-175">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="2e52d-176">Для резидентных служб необходимо изменить пакетный файл, чтобы сертификат клиента хранился в местоположении хранения CurrentUser, заменив строку LocalMachine строкой CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="2e52d-176">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="2e52d-177">Установка сертификата сервера в хранилище доверенных сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="2e52d-177">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="2e52d-178">Следующие строки из файла Setup.bat копируют сертификат сервера в хранилище доверенных лиц клиента.</span><span class="sxs-lookup"><span data-stu-id="2e52d-178">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="2e52d-179">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы.</span><span class="sxs-lookup"><span data-stu-id="2e52d-179">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="2e52d-180">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="2e52d-180">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bat
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="2e52d-181">Чтобы разрешить доступ к закрытому ключу сертификата из службы, размещенной в службах IIS, учетной записи пользователя, под которой выполняется процесс, размещенный в службах IIS, должны быть предоставлены соответствующие разрешения для закрытого ключа.</span><span class="sxs-lookup"><span data-stu-id="2e52d-181">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="2e52d-182">Это производится в последних шагах скрипта Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="2e52d-182">This is accomplished by last steps in the Setup.bat script.</span></span>

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
> <span data-ttu-id="2e52d-183">Пакетный файл Setup.bat предназначен для запуска из командной строки Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="2e52d-183">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="2e52d-184">Переменная среды PATH, заданная в командной строке Visual Studio 2012, указывает на каталог, содержащий исполняемые файлы, необходимые для скрипта Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="2e52d-184">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="2e52d-185">Настройка и сборка образца</span><span class="sxs-lookup"><span data-stu-id="2e52d-185">To set up and build the sample</span></span>

1. <span data-ttu-id="2e52d-186">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e52d-186">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="2e52d-187">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e52d-187">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="2e52d-188">Запуск образца на одном компьютере</span><span class="sxs-lookup"><span data-stu-id="2e52d-188">To run the sample on the same computer</span></span>

1. <span data-ttu-id="2e52d-189">Откройте окно командной строки Visual Studio 2012 с правами администратора и запустите Setup.bat из папки примеров установки.</span><span class="sxs-lookup"><span data-stu-id="2e52d-189">Open a Visual Studio 2012 Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="2e52d-190">При этом устанавливаются все сертификаты, необходимые для выполнения образца. Убедитесь, что папка, в которой находится файл Makecert.exe, входит в путь поиска.</span><span class="sxs-lookup"><span data-stu-id="2e52d-190">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>

> [!NOTE]
> <span data-ttu-id="2e52d-191">После завершения работы с образцом для удаления сертификатов обязательно запустите файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="2e52d-191">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="2e52d-192">В других образцах обеспечения безопасности используются те же сертификаты.</span><span class="sxs-lookup"><span data-stu-id="2e52d-192">Other security samples use the same certificates.</span></span>  
  
1. <span data-ttu-id="2e52d-193">Запустите Client.exe из каталога \client\bin.</span><span class="sxs-lookup"><span data-stu-id="2e52d-193">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="2e52d-194">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="2e52d-194">Client activity is displayed on the client console application.</span></span>  
  
2. <span data-ttu-id="2e52d-195">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2e52d-195">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="2e52d-196">Выполнение образца на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="2e52d-196">To run the sample across computer</span></span>  
  
1. <span data-ttu-id="2e52d-197">Создайте на компьютере службы каталог для двоичных файлов службы.</span><span class="sxs-lookup"><span data-stu-id="2e52d-197">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="2e52d-198">Скопируйте файлы служебной программы в каталог службы на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="2e52d-198">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="2e52d-199">Не забудьте скопировать файл CreditCardFile.txt; в противном случае структура проверки подлинности кредитной карты не сможет выполнить проверку подлинности данных кредитной карты, отправленных клиентом.</span><span class="sxs-lookup"><span data-stu-id="2e52d-199">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="2e52d-200">Кроме того, скопируйте файлы Setup.bat и Cleanup.bat на компьютер службы.</span><span class="sxs-lookup"><span data-stu-id="2e52d-200">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="2e52d-201">Необходимо иметь сертификат сервера с именем субъекта, содержащим полное имя домена компьютера.</span><span class="sxs-lookup"><span data-stu-id="2e52d-201">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="2e52d-202">Можно создать его с помощью файла Setup.bat, если заменить имя переменной `%SERVER_NAME%` полным именем компьютера, на котором будет размещаться служба.</span><span class="sxs-lookup"><span data-stu-id="2e52d-202">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="2e52d-203">Обратите внимание, что файл Setup.bat должен быть запущен в Командная строка разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="2e52d-203">Note that the Setup.bat file must be run in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="2e52d-204">Скопируйте сертификат сервера в хранилище CurrentUser-TrustedPeople на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="2e52d-204">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="2e52d-205">Это необходимо сделать только в том случае, если сертификат сервера не был выдан доверенным издателем.</span><span class="sxs-lookup"><span data-stu-id="2e52d-205">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="2e52d-206">В файле EchoServiceHost.cs измените значение имени субъекта сертификата, чтобы указать полное имя компьютера вместо localhost.</span><span class="sxs-lookup"><span data-stu-id="2e52d-206">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="2e52d-207">Скопируйте на клиентские компьютеры файлы из папки \client\bin\ в папку языка.</span><span class="sxs-lookup"><span data-stu-id="2e52d-207">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7. <span data-ttu-id="2e52d-208">В файле Client.cs измените значение адреса конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="2e52d-208">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8. <span data-ttu-id="2e52d-209">В файле Client.cs измените значение имени субъекта сертификата X.509 службы, чтобы оно соответствовало полному имени компьютера удаленного узла вместо localhost.</span><span class="sxs-lookup"><span data-stu-id="2e52d-209">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="2e52d-210">На клиентском компьютере из окна командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="2e52d-210">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="2e52d-211">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2e52d-211">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="2e52d-212">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="2e52d-212">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="2e52d-213">После завершения работы примера запустите в папке примеров файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="2e52d-213">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
