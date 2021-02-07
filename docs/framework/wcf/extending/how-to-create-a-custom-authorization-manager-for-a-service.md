---
description: Дополнительные сведения о том, как создать пользовательский диспетчер авторизации для службы.
title: Практическое руководство. Создание пользовательского диспетчера авторизации для службы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: e5b5655bb8cd087e2c5140f45e80f8b079cf06c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743724"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="ef26e-103">Практическое руководство. Создание пользовательского диспетчера авторизации для службы</span><span class="sxs-lookup"><span data-stu-id="ef26e-103">How to: Create a Custom Authorization Manager for a Service</span></span>

<span data-ttu-id="ef26e-104">Инфраструктура модели удостоверений в Windows Communication Foundation (WCF) поддерживает расширяемую модель авторизации на основе утверждений.</span><span class="sxs-lookup"><span data-stu-id="ef26e-104">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="ef26e-105">Утверждения извлекаются из маркеров, дополнительно обрабатываемых пользовательской политикой авторизации, и затем помещаются в контекст <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="ef26e-105">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="ef26e-106">Диспетчер авторизации проверяет утверждения в контексте <xref:System.IdentityModel.Policy.AuthorizationContext> для принятия решений об авторизации.</span><span class="sxs-lookup"><span data-stu-id="ef26e-106">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>

<span data-ttu-id="ef26e-107">По умолчанию решения об авторизации принимаются классом <xref:System.ServiceModel.ServiceAuthorizationManager>; однако эти решения можно переопределить, создав пользовательский диспетчер авторизации.</span><span class="sxs-lookup"><span data-stu-id="ef26e-107">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="ef26e-108">Чтобы создать пользовательский диспетчер авторизации, создайте класс, наследующий от класса <xref:System.ServiceModel.ServiceAuthorizationManager>, и реализуйте метод <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef26e-108">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="ef26e-109">Решения об авторизации принимаются в методе <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>, который возвращает `true`, если доступ предоставлен, и `false`, если в доступе отказано.</span><span class="sxs-lookup"><span data-stu-id="ef26e-109">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>

<span data-ttu-id="ef26e-110">Если решение об авторизации зависит от содержимого тела сообщения, используйте метод <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef26e-110">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>

<span data-ttu-id="ef26e-111">В связи с вопросами производительности при возможности следует внести изменения в приложение, чтобы решение об авторизации не требовало доступа к телу сообщения.</span><span class="sxs-lookup"><span data-stu-id="ef26e-111">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>

<span data-ttu-id="ef26e-112">Пользовательский диспетчер авторизации для службы можно зарегистрировать в коде или конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ef26e-112">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>

### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="ef26e-113">Создание пользовательского диспетчера авторизации</span><span class="sxs-lookup"><span data-stu-id="ef26e-113">To create a custom authorization manager</span></span>

1. <span data-ttu-id="ef26e-114">Создайте класс, производный от класса <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="ef26e-114">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. <span data-ttu-id="ef26e-115">Переопределите метод <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> .</span><span class="sxs-lookup"><span data-stu-id="ef26e-115">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>

    <span data-ttu-id="ef26e-116">Для принятия решения об авторизации используйте метод <xref:System.ServiceModel.OperationContext>, передаваемый в метод <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29>.</span><span class="sxs-lookup"><span data-stu-id="ef26e-116">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>

    <span data-ttu-id="ef26e-117">В следующем примере кода метод <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> используется для поиска пользовательского утверждения `http://www.contoso.com/claims/allowedoperation` и принятия решения об авторизации.</span><span class="sxs-lookup"><span data-stu-id="ef26e-117">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="ef26e-118">Регистрация пользовательского диспетчера авторизации с помощью кода</span><span class="sxs-lookup"><span data-stu-id="ef26e-118">To register a custom authorization manager using code</span></span>

1. <span data-ttu-id="ef26e-119">Создайте экземпляр пользовательского диспетчера авторизации и назначьте его свойству <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef26e-119">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>

    <span data-ttu-id="ef26e-120">Доступ к поведению <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> возможен с помощью свойства <xref:System.ServiceModel.ServiceHostBase.Authorization%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef26e-120">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>

    <span data-ttu-id="ef26e-121">В следующем примере кода регистрируется пользовательский диспетчер авторизации `MyServiceAuthorizationManager`.</span><span class="sxs-lookup"><span data-stu-id="ef26e-121">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="ef26e-122">Регистрация пользовательского диспетчера авторизации с помощью конфигурации</span><span class="sxs-lookup"><span data-stu-id="ef26e-122">To register a custom authorization manager using configuration</span></span>

1. <span data-ttu-id="ef26e-123">Откройте файл конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="ef26e-123">Open the configuration file for the service.</span></span>

2. <span data-ttu-id="ef26e-124">Добавьте в [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="ef26e-124">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md).</span></span>

    <span data-ttu-id="ef26e-125">В [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) добавьте `serviceAuthorizationManagerType` атрибут и задайте для его значения тип, представляющий пользовательский диспетчер авторизации.</span><span class="sxs-lookup"><span data-stu-id="ef26e-125">To the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>

3. <span data-ttu-id="ef26e-126">Добавьте привязку, обеспечивающую безопасность связи между клиентом и службой.</span><span class="sxs-lookup"><span data-stu-id="ef26e-126">Add a binding that secures the communication between the client and service.</span></span>

    <span data-ttu-id="ef26e-127">Привязка, выбранная для этой связи, определяет утверждения, добавляемые в контекст <xref:System.IdentityModel.Policy.AuthorizationContext> и используемые пользовательским диспетчером авторизации для принятия решений об авторизации.</span><span class="sxs-lookup"><span data-stu-id="ef26e-127">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="ef26e-128">Дополнительные сведения о привязках, предоставляемых системой, см. в разделе [привязки, предоставляемые системой](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="ef26e-128">For more details about the system-provided bindings, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

4. <span data-ttu-id="ef26e-129">Свяжите поведение с конечной точкой службы, добавив [\<service>](../../configure-apps/file-schema/wcf/service.md) элемент и задав `behaviorConfiguration` для атрибута значение атрибута Name для [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="ef26e-129">Associate the behavior to a service endpoint, by adding a [\<service>](../../configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    <span data-ttu-id="ef26e-130">Дополнительные сведения о настройке конечной точки службы см. в разделе [инструкции. Создание конечной точки службы в конфигурации](../feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ef26e-130">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>

    <span data-ttu-id="ef26e-131">В следующем примере кода регистрируется пользовательский диспетчер авторизации `Samples.MyServiceAuthorizationManager`.</span><span class="sxs-lookup"><span data-stu-id="ef26e-131">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <services>
          <service
              name="Microsoft.ServiceModel.Samples.CalculatorService"
              behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <endpoint address=""
                      binding="wsHttpBinding_Calculator"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
          </service>
        </services>
        <bindings>
          <WSHttpBinding>
           <binding name = "wsHttpBinding_Calculator">
             <security mode="Message">
               <message clientCredentialType="Windows"/>
             </security>
            </binding>
          </WSHttpBinding>
        </bindings>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />
             </behavior>
         </serviceBehaviors>
       </behaviors>
      </system.serviceModel>
    </configuration>
    ```

    > [!WARNING]
    > <span data-ttu-id="ef26e-132">Обратите внимание, что при указании serviceAuthorizationManagerType строка должна содержать полное имя типа.</span><span class="sxs-lookup"><span data-stu-id="ef26e-132">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="ef26e-133">запятая и имя сборки, в которой определен тип.</span><span class="sxs-lookup"><span data-stu-id="ef26e-133">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="ef26e-134">Если опустить имя сборки, WCF попытается загрузить тип из System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="ef26e-134">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>

## <a name="example"></a><span data-ttu-id="ef26e-135">Пример</span><span class="sxs-lookup"><span data-stu-id="ef26e-135">Example</span></span>

<span data-ttu-id="ef26e-136">В следующем образце кода показана базовая реализация класса <xref:System.ServiceModel.ServiceAuthorizationManager>, которая содержит переопределение метода <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef26e-136">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="ef26e-137">В этом примере кода производится проверка <xref:System.IdentityModel.Policy.AuthorizationContext> на наличие пользовательского утверждения и возвращается `true`, если ресурс для этого пользовательского утверждения соответствует значению действия из контекста <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="ef26e-137">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="ef26e-138">Более полную реализацию <xref:System.ServiceModel.ServiceAuthorizationManager> класса см. в разделе [Политика авторизации](../samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="ef26e-138">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../samples/authorization-policy.md).</span></span>

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a><span data-ttu-id="ef26e-139">См. также</span><span class="sxs-lookup"><span data-stu-id="ef26e-139">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="ef26e-140">Политика авторизации</span><span class="sxs-lookup"><span data-stu-id="ef26e-140">Authorization Policy</span></span>](../samples/authorization-policy.md)
