---
description: Дополнительные сведения см. в статье безопасность сообщений с помощью клиента Windows без согласования учетных данных.
title: Безопасность сообщений с использованием клиента Windows без согласования учетных данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: e9edd63c80d868024d8a4b664c42456bb454cb69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99727018"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a><span data-ttu-id="b6b7a-103">Безопасность сообщений с использованием клиента Windows без согласования учетных данных</span><span class="sxs-lookup"><span data-stu-id="b6b7a-103">Message Security with a Windows Client without Credential Negotiation</span></span>

<span data-ttu-id="b6b7a-104">В следующем сценарии показан клиент Windows Communication Foundation (WCF) и служба, защищенные протоколом Kerberos.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-104">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by the Kerberos protocol.</span></span>

<span data-ttu-id="b6b7a-105">Клиент и служба находятся в одном и том же домене или в доверенных доменах.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-105">Both the service and the client are in the same domain or trusted domains.</span></span>

> [!NOTE]
> <span data-ttu-id="b6b7a-106">Разница между этим сценарием и [безопасностью сообщений с помощью клиента Windows](message-security-with-a-windows-client.md) заключается в том, что этот сценарий не согласовывает учетные данные службы с службой до отправки сообщения приложения.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-106">The difference between this scenario and [Message Security with a Windows Client](message-security-with-a-windows-client.md) is that this scenario does not negotiate the service credential with the service prior to sending the application message.</span></span> <span data-ttu-id="b6b7a-107">И так как для этого требуется протокол Kerberos, для этого сценария необходима среда домена Windows.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-107">Additionally, because this requires the Kerberos protocol, this scenario requires a Windows domain environment.</span></span>

<span data-ttu-id="b6b7a-108">![Безопасность сообщений с согласованием учетных данных](media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span><span class="sxs-lookup"><span data-stu-id="b6b7a-108">![Message security without credential negotiation](media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span></span>

|<span data-ttu-id="b6b7a-109">Характеристика</span><span class="sxs-lookup"><span data-stu-id="b6b7a-109">Characteristic</span></span>|<span data-ttu-id="b6b7a-110">Описание</span><span class="sxs-lookup"><span data-stu-id="b6b7a-110">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="b6b7a-111">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="b6b7a-111">Security Mode</span></span>|<span data-ttu-id="b6b7a-112">Сообщение</span><span class="sxs-lookup"><span data-stu-id="b6b7a-112">Message</span></span>|
|<span data-ttu-id="b6b7a-113">Совместимость</span><span class="sxs-lookup"><span data-stu-id="b6b7a-113">Interoperability</span></span>|<span data-ttu-id="b6b7a-114">Да, WS-Security с клиентами, совместимыми с профилем маркера Kerberos</span><span class="sxs-lookup"><span data-stu-id="b6b7a-114">Yes, WS-Security with Kerberos token-profile compatible clients</span></span>|
|<span data-ttu-id="b6b7a-115">Проверка подлинности (сервера)</span><span class="sxs-lookup"><span data-stu-id="b6b7a-115">Authentication (Server)</span></span>|<span data-ttu-id="b6b7a-116">Взаимная проверка подлинности сервера и клиента</span><span class="sxs-lookup"><span data-stu-id="b6b7a-116">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="b6b7a-117">Проверка подлинности (клиента)</span><span class="sxs-lookup"><span data-stu-id="b6b7a-117">Authentication (Client)</span></span>|<span data-ttu-id="b6b7a-118">Взаимная проверка подлинности сервера и клиента</span><span class="sxs-lookup"><span data-stu-id="b6b7a-118">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="b6b7a-119">Целостность</span><span class="sxs-lookup"><span data-stu-id="b6b7a-119">Integrity</span></span>|<span data-ttu-id="b6b7a-120">Да</span><span class="sxs-lookup"><span data-stu-id="b6b7a-120">Yes</span></span>|
|<span data-ttu-id="b6b7a-121">Конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="b6b7a-121">Confidentiality</span></span>|<span data-ttu-id="b6b7a-122">Да</span><span class="sxs-lookup"><span data-stu-id="b6b7a-122">Yes</span></span>|
|<span data-ttu-id="b6b7a-123">Транспорт</span><span class="sxs-lookup"><span data-stu-id="b6b7a-123">Transport</span></span>|<span data-ttu-id="b6b7a-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="b6b7a-124">HTTP</span></span>|
|<span data-ttu-id="b6b7a-125">Привязка</span><span class="sxs-lookup"><span data-stu-id="b6b7a-125">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="b6b7a-126">Служба</span><span class="sxs-lookup"><span data-stu-id="b6b7a-126">Service</span></span>

<span data-ttu-id="b6b7a-127">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b6b7a-128">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-128">Do one of the following:</span></span>

- <span data-ttu-id="b6b7a-129">Создайте автономную службу, используя код без конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-129">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="b6b7a-130">Создайте службу, используя предоставленную конфигурацию, но не определяйте конечные точки.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="b6b7a-131">Код</span><span class="sxs-lookup"><span data-stu-id="b6b7a-131">Code</span></span>

<span data-ttu-id="b6b7a-132">В следующем коде создается конечная точка службы, которая использует безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-132">The following code creates a service endpoint that uses message security.</span></span> <span data-ttu-id="b6b7a-133">Этот код отключает согласование учетных данных службы и установку маркера контекста безопасности (SCT).</span><span class="sxs-lookup"><span data-stu-id="b6b7a-133">The code disables service credential negotiation, and the establishment of a security context token (SCT).</span></span>

> [!NOTE]
> <span data-ttu-id="b6b7a-134">Для использования типа учетных данных Windows без согласования учетная запись пользователя службы должна иметь доступ к имени участника-службы (SPN), зарегистрированному с доменом Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-134">To use the Windows credential type without negotiation, the service's user account must have access to service principal name (SPN) that is registered with the Active Directory domain.</span></span> <span data-ttu-id="b6b7a-135">Это можно сделать двумя способами.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-135">You can do this in two ways:</span></span>

1. <span data-ttu-id="b6b7a-136">Используйте учетную запись `NetworkService` или `LocalSystem` для запуска службы.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-136">Use the `NetworkService` or `LocalSystem` account to run your service.</span></span> <span data-ttu-id="b6b7a-137">Поскольку эти учетные записи имеют доступ к имени участника-службы (SPN), установленному при присоединении компьютера к домену Active Directory, WCF автоматически создает соответствующий элемент SPN внутри конечной точки службы в метаданных службы (язык описания веб-служб или WSDL).</span><span class="sxs-lookup"><span data-stu-id="b6b7a-137">Because those accounts have access to the machine SPN that is established when the machine joins the Active Directory domain, WCF automatically generates the proper SPN element inside the service's endpoint in the service's metadata (Web Services Description Language, or WSDL).</span></span>

2. <span data-ttu-id="b6b7a-138">Запустите службу из любой учетной записи домена Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-138">Use an arbitrary Active Directory domain account to run your service.</span></span> <span data-ttu-id="b6b7a-139">В этом случае потребуется установить SPN для учетной записи домена.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-139">In this case, you need to establish an SPN for that domain account.</span></span> <span data-ttu-id="b6b7a-140">Это можно сделать, например, с помощью средства Setspn.exe.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-140">One way of doing this is to use the Setspn.exe utility tool.</span></span> <span data-ttu-id="b6b7a-141">После создания имени SPN для учетной записи службы настройте WCF для публикации имени участника-службы на клиентах службы через ее метаданные (WSDL).</span><span class="sxs-lookup"><span data-stu-id="b6b7a-141">Once the SPN is created for the service's account, configure WCF to publish that SPN to the service's clients through its metadata (WSDL).</span></span> <span data-ttu-id="b6b7a-142">Это можно сделать, настроив удостоверение конечной точки для предоставляемой конечной точки либо в файле конфигурации приложения, либо в коде.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-142">This is done by setting the endpoint identity for the exposed endpoint, either though an application configuration file or code.</span></span> <span data-ttu-id="b6b7a-143">В следующем примере описывается программный способ публикации удостоверения.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-143">The following example publishes the identity programmatically.</span></span>

<span data-ttu-id="b6b7a-144">Дополнительные сведения об именах участников-служб, протоколе Kerberos и Active Directory см. в статье [Техническая поддержка Kerberos для Windows](/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b6b7a-144">For more information about SPNs, the Kerberos protocol, and Active Directory, see [Kerberos Technical Supplement for Windows](/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span> <span data-ttu-id="b6b7a-145">Дополнительные сведения о идентификаторах конечных точек см. в разделе [режимы проверки подлинности SecurityBindingElement](securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="b6b7a-145">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md).</span></span>

[!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
[!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]

### <a name="configuration"></a><span data-ttu-id="b6b7a-146">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="b6b7a-146">Configuration</span></span>

<span data-ttu-id="b6b7a-147">Вместо кода можно использовать следующую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-147">The following configuration can be used instead of the code.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors />
    <services>
      <service behaviorConfiguration="" name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="KerberosBinding"
                  name="WSHttpBinding_ICalculator"
                  contract="ServiceModel.ICalculator"
                  listenUri="net.tcp://localhost/metadata" >
         <identity>
            <servicePrincipalName value="service_spn_name" />
         </identity>
        </endpoint>
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="KerberosBinding">
          <security>
            <message negotiateServiceCredential="false"
                     establishSecurityContext="false" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="b6b7a-148">Клиент</span><span class="sxs-lookup"><span data-stu-id="b6b7a-148">Client</span></span>

<span data-ttu-id="b6b7a-149">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-149">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b6b7a-150">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-150">Do one of the following:</span></span>

- <span data-ttu-id="b6b7a-151">Создайте автономный клиент, используя код (и код клиента).</span><span class="sxs-lookup"><span data-stu-id="b6b7a-151">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="b6b7a-152">Создайте клиент, который не определяет никаких адресов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-152">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="b6b7a-153">Вместо этого используйте конструктор клиента, который принимает в качестве аргумента имя конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-153">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="b6b7a-154">Пример:</span><span class="sxs-lookup"><span data-stu-id="b6b7a-154">For example:</span></span>

  [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
  [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="b6b7a-155">Код</span><span class="sxs-lookup"><span data-stu-id="b6b7a-155">Code</span></span>

<span data-ttu-id="b6b7a-156">Следующий код служит для настройки клиента.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-156">The following code configures the client.</span></span> <span data-ttu-id="b6b7a-157">Для режима безопасности задано значение Message, типу учетных данных клиента присвоено значение Windows.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-157">The security mode is set to Message, and the client credential type is set to Windows.</span></span> <span data-ttu-id="b6b7a-158">Обратите внимание: свойствам <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> и <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> задается значение `false`.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-158">Note that the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> and <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> properties are set to `false`.</span></span>

> [!NOTE]
> <span data-ttu-id="b6b7a-159">Для использования типа учетных данных Windows без согласования требуется настроить SPN учетной записи службы до начала обмена данными со службой.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-159">To use Windows credential type without negotiation, the client must be configured with the service's account SPN prior to commencing the communication with the service.</span></span> <span data-ttu-id="b6b7a-160">Клиент использует имя SPN, чтобы получить маркер Kerberos для проверки подлинности и обеспечения безопасности обмена данными со службой.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-160">The client uses the SPN to get the Kerberos token to authenticate and secure the communication with the service.</span></span> <span data-ttu-id="b6b7a-161">В следующем образце показано, как настроить SPN службы для клиента.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-161">The following sample shows how to configure the client with the service's SPN.</span></span> <span data-ttu-id="b6b7a-162">Если для создания клиента используется [служебная программа метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , то SPN службы автоматически распространяется на клиент из метаданных службы (WSDL), если метаданные службы содержат эти сведения.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-162">If you are using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the client, the service's SPN will be automatically propagated to the client from the service's metadata (WSDL), if the service's metadata contains that information.</span></span> <span data-ttu-id="b6b7a-163">Дополнительные сведения о настройке службы для включения имени участника-службы в метаданные службы см. в подразделе "служба" Далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-163">For more information about how to configure the service to include its SPN in the service's metadata, see the "Service" section later in this topic .</span></span>
>
> <span data-ttu-id="b6b7a-164">Дополнительные сведения о SPN, Kerberos и Active Directory см. в статье [Техническая поддержка Kerberos для Windows](/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b6b7a-164">For more information about SPNs, Kerberos, and Active Directory, see [Kerberos Technical Supplement for Windows](/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span> <span data-ttu-id="b6b7a-165">Дополнительные сведения о удостоверениях конечных точек см. в разделе [SecurityBindingElement Authentication modes](securitybindingelement-authentication-modes.md) .</span><span class="sxs-lookup"><span data-stu-id="b6b7a-165">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md) topic.</span></span>

[!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
[!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]

### <a name="configuration"></a><span data-ttu-id="b6b7a-166">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="b6b7a-166">Configuration</span></span>

<span data-ttu-id="b6b7a-167">Следующий код служит для настройки клиента.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-167">The following code configures the client.</span></span> <span data-ttu-id="b6b7a-168">Обратите внимание, что [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) элемент должен быть установлен в соответствие имени SPN службы, зарегистрированному для учетной записи службы в домене Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b6b7a-168">Note that the [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) element must be set to match the service's SPN as registered for the service's account in the Active Directory domain.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     establishSecurityContext="false" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://localhost/Calculator"
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"
                name="WSHttpBinding_ICalculator">
        <identity>
          <servicePrincipalName value="service_spn_name" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b6b7a-169">См. также</span><span class="sxs-lookup"><span data-stu-id="b6b7a-169">See also</span></span>

- [<span data-ttu-id="b6b7a-170">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="b6b7a-170">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="b6b7a-171">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="b6b7a-171">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="b6b7a-172">[Модель безопасности для Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b6b7a-172">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
