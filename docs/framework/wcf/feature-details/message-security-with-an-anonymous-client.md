---
description: Дополнительные сведения о безопасности сообщений с анонимным клиентом
title: Безопасность сообщений с анонимным клиентом
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 921ddd9e8e7d2a860f3516c452870bc2bb150911
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726979"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="02ed0-103">Безопасность сообщений с анонимным клиентом</span><span class="sxs-lookup"><span data-stu-id="02ed0-103">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="02ed0-104">В следующем сценарии показан клиент и служба, защищенные с помощью защиты сообщений Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="02ed0-104">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="02ed0-105">Задача, поставленная при разработке, заключается в использовании безопасности сообщений, а не безопасности транспорта, чтобы в будущем возможно было использование более глубокой модели, использующей утверждения.</span><span class="sxs-lookup"><span data-stu-id="02ed0-105">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="02ed0-106">Дополнительные сведения об использовании расширенных утверждений для авторизации см. [в статье Управление утверждениями и авторизацией с помощью модели удостоверений](managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="02ed0-106">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="02ed0-107">Пример приложения см. в разделе [безопасность сообщений анонимно](../samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="02ed0-107">For a sample application, see [Message Security Anonymous](../samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="02ed0-108">![Безопасность сообщений с анонимным клиентом](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="02ed0-108">![Message security with an anonymous client](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="02ed0-109">Характеристика</span><span class="sxs-lookup"><span data-stu-id="02ed0-109">Characteristic</span></span>|<span data-ttu-id="02ed0-110">Описание</span><span class="sxs-lookup"><span data-stu-id="02ed0-110">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="02ed0-111">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="02ed0-111">Security Mode</span></span>|<span data-ttu-id="02ed0-112">Сообщение</span><span class="sxs-lookup"><span data-stu-id="02ed0-112">Message</span></span>|
|<span data-ttu-id="02ed0-113">Совместимость</span><span class="sxs-lookup"><span data-stu-id="02ed0-113">Interoperability</span></span>|<span data-ttu-id="02ed0-114">Только WCF</span><span class="sxs-lookup"><span data-stu-id="02ed0-114">WCF only</span></span>|
|<span data-ttu-id="02ed0-115">Проверка подлинности (сервера)</span><span class="sxs-lookup"><span data-stu-id="02ed0-115">Authentication (Server)</span></span>|<span data-ttu-id="02ed0-116">Первоначальное согласование возможно только после проверки подлинности сервера, но не клиента</span><span class="sxs-lookup"><span data-stu-id="02ed0-116">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="02ed0-117">Проверка подлинности (клиента)</span><span class="sxs-lookup"><span data-stu-id="02ed0-117">Authentication (Client)</span></span>|<span data-ttu-id="02ed0-118">None</span><span class="sxs-lookup"><span data-stu-id="02ed0-118">None</span></span>|
|<span data-ttu-id="02ed0-119">Целостность</span><span class="sxs-lookup"><span data-stu-id="02ed0-119">Integrity</span></span>|<span data-ttu-id="02ed0-120">Да, используется общий контекст безопасности</span><span class="sxs-lookup"><span data-stu-id="02ed0-120">Yes, using shared security context</span></span>|
|<span data-ttu-id="02ed0-121">Конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="02ed0-121">Confidentiality</span></span>|<span data-ttu-id="02ed0-122">Да, используется общий контекст безопасности</span><span class="sxs-lookup"><span data-stu-id="02ed0-122">Yes, using shared security context</span></span>|
|<span data-ttu-id="02ed0-123">Транспорт</span><span class="sxs-lookup"><span data-stu-id="02ed0-123">Transport</span></span>|<span data-ttu-id="02ed0-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="02ed0-124">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="02ed0-125">Служба</span><span class="sxs-lookup"><span data-stu-id="02ed0-125">Service</span></span>

<span data-ttu-id="02ed0-126">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="02ed0-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="02ed0-127">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="02ed0-127">Do one of the following:</span></span>

- <span data-ttu-id="02ed0-128">Создайте автономную службу, используя код без конфигурации.</span><span class="sxs-lookup"><span data-stu-id="02ed0-128">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="02ed0-129">Создайте службу, используя предоставленную конфигурацию, но не определяйте конечные точки.</span><span class="sxs-lookup"><span data-stu-id="02ed0-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="02ed0-130">Код</span><span class="sxs-lookup"><span data-stu-id="02ed0-130">Code</span></span>

<span data-ttu-id="02ed0-131">В следующем коде показано, как создать конечную точку службы, которая использует безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="02ed0-131">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="02ed0-132">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="02ed0-132">Configuration</span></span>

<span data-ttu-id="02ed0-133">Вместо кода можно использовать следующую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="02ed0-133">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="02ed0-134">Элемент поведения службы используется для указания сертификата, который используется для проверки подлинности службы для клиента.</span><span class="sxs-lookup"><span data-stu-id="02ed0-134">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="02ed0-135">Элемент службы должен задавать поведение с помощью атрибута `behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="02ed0-135">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="02ed0-136">Элемент привязки указывает, что типу учетных данных клиента присвоено значение `None`, позволяя анонимному клиенту использовать службу.</span><span class="sxs-lookup"><span data-stu-id="02ed0-136">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="02ed0-137">Клиент</span><span class="sxs-lookup"><span data-stu-id="02ed0-137">Client</span></span>

<span data-ttu-id="02ed0-138">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="02ed0-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="02ed0-139">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="02ed0-139">Do one of the following:</span></span>

- <span data-ttu-id="02ed0-140">Создайте автономный клиент, используя код (и код клиента).</span><span class="sxs-lookup"><span data-stu-id="02ed0-140">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="02ed0-141">Создайте клиент, который не определяет никаких адресов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="02ed0-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="02ed0-142">Вместо этого используйте конструктор клиента, который принимает в качестве аргумента имя конфигурации.</span><span class="sxs-lookup"><span data-stu-id="02ed0-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="02ed0-143">Пример:</span><span class="sxs-lookup"><span data-stu-id="02ed0-143">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="02ed0-144">Код</span><span class="sxs-lookup"><span data-stu-id="02ed0-144">Code</span></span>

<span data-ttu-id="02ed0-145">В следующем примере кода создается экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="02ed0-145">The following code creates an instance of the client.</span></span> <span data-ttu-id="02ed0-146">Привязка использует безопасность режима сообщений, и тип учетных данных клиента задан как None.</span><span class="sxs-lookup"><span data-stu-id="02ed0-146">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="02ed0-147">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="02ed0-147">Configuration</span></span>

<span data-ttu-id="02ed0-148">Следующий код служит для настройки клиента.</span><span class="sxs-lookup"><span data-stu-id="02ed0-148">The following code configures the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="02ed0-149">См. также</span><span class="sxs-lookup"><span data-stu-id="02ed0-149">See also</span></span>

- [<span data-ttu-id="02ed0-150">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="02ed0-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="02ed0-151">Защита распределенных приложений</span><span class="sxs-lookup"><span data-stu-id="02ed0-151">Distributed Application Security</span></span>](distributed-application-security.md)
- [<span data-ttu-id="02ed0-152">Безопасность сообщений с возможностью анонимного доступа</span><span class="sxs-lookup"><span data-stu-id="02ed0-152">Message Security Anonymous</span></span>](../samples/message-security-anonymous.md)
- [<span data-ttu-id="02ed0-153">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="02ed0-153">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="02ed0-154">[Модель безопасности для Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="02ed0-154">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
