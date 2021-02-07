---
description: 'Дополнительные сведения: Федерация'
title: Федерация
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: 069017097b46ef0b86e74fb94c2e2823172fb1e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756335"
---
# <a name="federation"></a><span data-ttu-id="b484d-103">Федерация</span><span class="sxs-lookup"><span data-stu-id="b484d-103">Federation</span></span>

<span data-ttu-id="b484d-104">В этом разделе приведен краткий обзор концепции федеративной безопасности.</span><span class="sxs-lookup"><span data-stu-id="b484d-104">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="b484d-105">В нем также описывается поддержка Windows Communication Foundation (WCF) для развертывания федеративных архитектур безопасности.</span><span class="sxs-lookup"><span data-stu-id="b484d-105">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="b484d-106">Пример приложения, демонстрирующий Федерацию, см. в разделе [Пример Федерации](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b484d-106">For a sample application that demonstrates federation, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="b484d-107">Определение федеративной безопасности</span><span class="sxs-lookup"><span data-stu-id="b484d-107">Definition of Federated Security</span></span>  

 <span data-ttu-id="b484d-108">Федеративная безопасность обеспечивает четкое разделение между службой, к которой обращается клиент, и связанными процедурами проверки подлинности и авторизации.</span><span class="sxs-lookup"><span data-stu-id="b484d-108">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="b484d-109">Федеративная безопасность также делает возможной совместную работу групп из нескольких систем, сетей и организаций, принадлежащих к различным областям доверия.</span><span class="sxs-lookup"><span data-stu-id="b484d-109">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="b484d-110">WCF обеспечивает поддержку для создания и развертывания распределенных систем, использующих Федеративные средства безопасности.</span><span class="sxs-lookup"><span data-stu-id="b484d-110">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="b484d-111">Элементы архитектуры федеративной безопасности</span><span class="sxs-lookup"><span data-stu-id="b484d-111">Elements of a Federated Security Architecture</span></span>  

 <span data-ttu-id="b484d-112">Архитектура федеративной безопасности включает три основных элемента, рассмотренных в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="b484d-112">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="b484d-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="b484d-113">Element</span></span>|<span data-ttu-id="b484d-114">Описание</span><span class="sxs-lookup"><span data-stu-id="b484d-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b484d-115">Домен/область</span><span class="sxs-lookup"><span data-stu-id="b484d-115">Domain/realm</span></span>|<span data-ttu-id="b484d-116">Единица администрирования безопасности или доверия.</span><span class="sxs-lookup"><span data-stu-id="b484d-116">A single unit of security administration or trust.</span></span> <span data-ttu-id="b484d-117">Типичный домен может включать одну организацию.</span><span class="sxs-lookup"><span data-stu-id="b484d-117">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="b484d-118">Федерация</span><span class="sxs-lookup"><span data-stu-id="b484d-118">Federation</span></span>|<span data-ttu-id="b484d-119">Совокупность доменов, между которыми установлено отношение доверия.</span><span class="sxs-lookup"><span data-stu-id="b484d-119">A collection of domains that have established trust.</span></span> <span data-ttu-id="b484d-120">Уровень доверия может отличаться, но обычно предусматривает проверку подлинности и почти всегда — авторизацию.</span><span class="sxs-lookup"><span data-stu-id="b484d-120">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="b484d-121">Типичная федерация может включать ряд организаций, для которых установлено отношение доверия для общего доступа к набору ресурсов.</span><span class="sxs-lookup"><span data-stu-id="b484d-121">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="b484d-122">Служба маркеров безопасности (STS)</span><span class="sxs-lookup"><span data-stu-id="b484d-122">Security Token Service (STS)</span></span>|<span data-ttu-id="b484d-123">Веб-служба, выдающая маркеры безопасности, т. е. делающая утверждения на основании свидетельств, которым она доверяет, перед теми, кто доверяет ей.</span><span class="sxs-lookup"><span data-stu-id="b484d-123">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="b484d-124">Эти утверждения образуют основу посредничества с доверием между доменами.</span><span class="sxs-lookup"><span data-stu-id="b484d-124">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="b484d-125">Пример сценария</span><span class="sxs-lookup"><span data-stu-id="b484d-125">Example Scenario</span></span>  

 <span data-ttu-id="b484d-126">На следующем рисунке показан пример федеративной безопасности.</span><span class="sxs-lookup"><span data-stu-id="b484d-126">The following illustration shows an example of federated security:</span></span>  
  
 ![Схема, демонстрирующая типичный сценарий федеративной безопасности.](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="b484d-128">В сценарии участвует две организации: A и B. Организация B имеет веб-ресурс (веб-службу), которую некоторые пользователи в организации A находят полезной.</span><span class="sxs-lookup"><span data-stu-id="b484d-128">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b484d-129">В этом разделе термины « *ресурс*», « *Служба*» и « *веб-служба* » используются взаимозаменяемыми.</span><span class="sxs-lookup"><span data-stu-id="b484d-129">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="b484d-130">Как правило, организация B требует, чтобы пользователь из организации A предоставил какое-либо допустимое доказательство своей подлинности, прежде чем обращаться к службе.</span><span class="sxs-lookup"><span data-stu-id="b484d-130">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="b484d-131">Кроме того, организация может также потребовать, чтобы пользователь был авторизован для доступа к данному ресурсу.</span><span class="sxs-lookup"><span data-stu-id="b484d-131">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="b484d-132">Один из способов решить эту проблему и дать пользователям в организации A возможность доступа к ресурсу в организации B заключается в следующем.</span><span class="sxs-lookup"><span data-stu-id="b484d-132">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="b484d-133">Пользователи из организации A регистрируют свои учетные данные (имя пользователя и пароль) в организации B.</span><span class="sxs-lookup"><span data-stu-id="b484d-133">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="b484d-134">При обращении к ресурсу пользователи из организации A предъявляют свои учетные данные организации B, т. е. подлинность пользователей проверяется, прежде чем они получают доступ к ресурсу.</span><span class="sxs-lookup"><span data-stu-id="b484d-134">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="b484d-135">Это подход имеет три существенных недостатка.</span><span class="sxs-lookup"><span data-stu-id="b484d-135">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="b484d-136">Организации B приходится управлять учетными данными пользователей из организации A, помимо управления учетными данными своих локальных пользователей.</span><span class="sxs-lookup"><span data-stu-id="b484d-136">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="b484d-137">Пользователям в организации A приходится иметь дополнительный набор учетных данных (т. е. помнить дополнительные имя пользователя и пароль) помимо учетных данных, которыми они пользуются для получения доступа к ресурсам в пределах организации A. В таких случаях пользователи часто используют одни и те же имя пользователя и пароль для доступа к нескольким сайтам служб, что ослабляет защиту.</span><span class="sxs-lookup"><span data-stu-id="b484d-137">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="b484d-138">Архитектура не масштабируется, если другие организации посчитают ресурс в организации B полезным для своих пользователей.</span><span class="sxs-lookup"><span data-stu-id="b484d-138">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="b484d-139">Альтернативный подход, лишенный упомянутых выше недостатков - это использование федеративной безопасности.</span><span class="sxs-lookup"><span data-stu-id="b484d-139">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="b484d-140">В соответствии с этим подходом организации A и B устанавливают отношения доверия и используют службу маркеров безопасности (Security Token Service, STS) как посредника для установленного доверия.</span><span class="sxs-lookup"><span data-stu-id="b484d-140">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="b484d-141">В архитектуре федеративной безопасности пользователи из организации A знают, что если им требуется обратиться к веб-службе в организации B, они должны предъявить в организации B допустимый маркер безопасности от службы STS, который используется для проверки их подлинности и авторизации их доступа к определенной службе.</span><span class="sxs-lookup"><span data-stu-id="b484d-141">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="b484d-142">При обращении к службе STS B пользователи приобретают еще один уровень косвенного обращения от политики, связанной со службой STS.</span><span class="sxs-lookup"><span data-stu-id="b484d-142">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="b484d-143">Прежде чем служба STS B сможет выдать им маркер безопасности, они должны предъявить допустимый маркер безопасности от службы STS A (т. е. из области доверия клиента).</span><span class="sxs-lookup"><span data-stu-id="b484d-143">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="b484d-144">Это логическое следствие из отношения доверия, установленного между двумя организациями, подразумевающее, что организации B не требуется управлять удостоверениями пользователей из организации A. На практике служба STS B обычно имеет пустые адреса `issuerAddress` и `issuerMetadataAddress`.</span><span class="sxs-lookup"><span data-stu-id="b484d-144">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="b484d-145">Дополнительные сведения см. [в разделе руководство. Настройка локального издателя](how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="b484d-145">For more information, see [How to: Configure a Local Issuer](how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="b484d-146">В этом случае клиент обращается к локальной политике, чтобы найти STS. Эта конфигурация называется *Федерации домашней области* и масштабируется лучше, так как STS B не требуется хранить сведения о службе STS A.</span><span class="sxs-lookup"><span data-stu-id="b484d-146">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="b484d-147">Затем пользователи связываются со службой STS в организации A и получают маркер безопасности, предъявляя для проверки подлинности учетные данные, которыми они обычно пользуются для доступа к любому другому ресурсу в пределах организации A. Это также решает проблему пользователей, которым приходится либо помнить несколько наборов учетных данных, либо использовать один и тот же набор учетных данных на нескольких сайтах служб.</span><span class="sxs-lookup"><span data-stu-id="b484d-147">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="b484d-148">Получив маркер безопасности от службы STS A, пользователи предъявляют маркер службе STS B. Далее организация B авторизует запросы пользователей и выдает пользователям маркер безопасности из собственного набора маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="b484d-148">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="b484d-149">Пользователи затем могут предъявить свой маркер ресурсу в организации B и получить доступ к службе.</span><span class="sxs-lookup"><span data-stu-id="b484d-149">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="b484d-150">Поддержка федеративной безопасности в WCF</span><span class="sxs-lookup"><span data-stu-id="b484d-150">Support for Federated Security in WCF</span></span>  

 <span data-ttu-id="b484d-151">WCF обеспечивает собственную поддержку развертывания федеративных архитектур безопасности с помощью [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b484d-151">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="b484d-152">[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)Элемент обеспечивает безопасную, надежную, взаимодействующую привязку, которая влечет за собой использование HTTP в качестве базового транспортного механизма для стиля связи «запрос-ответ», применение текста и XML в качестве формата подключения для кодирования.</span><span class="sxs-lookup"><span data-stu-id="b484d-152">The [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="b484d-153">Использование [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) в Федеративной ситуации безопасности может быть отделено от двух логически независимых этапов, как описано в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="b484d-153">The use of [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="b484d-154">Фаза 1: фаза проектирования</span><span class="sxs-lookup"><span data-stu-id="b484d-154">Phase 1: Design Phase</span></span>  

 <span data-ttu-id="b484d-155">На этапе проектирования клиент использует [средство служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) для чтения политики, предоставляемой конечной точкой службы, и для получения требований к проверке подлинности и авторизации службы.</span><span class="sxs-lookup"><span data-stu-id="b484d-155">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="b484d-156">Строятся соответствующие прокси-объекты для создания следующей схемы обмена данными федеративной безопасности на стороне клиента:</span><span class="sxs-lookup"><span data-stu-id="b484d-156">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="b484d-157">получение маркера безопасности от службы STS в области доверия клиента;</span><span class="sxs-lookup"><span data-stu-id="b484d-157">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="b484d-158">предъявление маркера службе STS в области доверия службы;</span><span class="sxs-lookup"><span data-stu-id="b484d-158">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="b484d-159">получение маркера безопасности от службы STS в области доверия службы;</span><span class="sxs-lookup"><span data-stu-id="b484d-159">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="b484d-160">предъявление маркера службе для доступа к службе.</span><span class="sxs-lookup"><span data-stu-id="b484d-160">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="b484d-161">Фаза 2: фаза времени выполнения</span><span class="sxs-lookup"><span data-stu-id="b484d-161">Phase 2: Run-Time Phase</span></span>  

 <span data-ttu-id="b484d-162">Во время этапа выполнения клиент создает экземпляр класса клиента WCF и выполняет вызов с помощью клиента WCF.</span><span class="sxs-lookup"><span data-stu-id="b484d-162">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="b484d-163">Базовая платформа WCF обрабатывает описанные ранее действия в Федеративной модели связи безопасности и позволяет клиенту эффективно использовать службу.</span><span class="sxs-lookup"><span data-stu-id="b484d-163">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="b484d-164">Пример реализации с использованием WCF</span><span class="sxs-lookup"><span data-stu-id="b484d-164">Sample Implementation Using WCF</span></span>  

 <span data-ttu-id="b484d-165">На следующем рисунке показан пример реализации для Федеративной архитектуры безопасности с использованием собственной поддержки из WCF.</span><span class="sxs-lookup"><span data-stu-id="b484d-165">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![Схема, на которой показан пример реализации безопасности Федерации.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="b484d-167">Служба MyService</span><span class="sxs-lookup"><span data-stu-id="b484d-167">Example MyService</span></span>  

 <span data-ttu-id="b484d-168">Служба `MyService` предоставляет одну конечную точку - `MyServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="b484d-168">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="b484d-169">На следующем рисунке показаны адрес, привязка и контракт, связанные с конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="b484d-169">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![Схема, показывающая сведения о Мисервицеендпоинт.](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="b484d-171">Конечная точка службы `MyServiceEndpoint` использует для [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) и требует допустимый токен SAML с `accessAuthorized` утверждением, выданным STS B. Это декларативно указывается в конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="b484d-171">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="b484d-172">Относительно утверждений, которые требует служба `MyService`, необходимо отметить один небольшой момент.</span><span class="sxs-lookup"><span data-stu-id="b484d-172">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="b484d-173">Из второго рисунка видно, что служба `MyService` требует маркер SAML с утверждением `accessAuthorized`.</span><span class="sxs-lookup"><span data-stu-id="b484d-173">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="b484d-174">Точнее, эта строка задает тип утверждения, которого требует служба `MyService`.</span><span class="sxs-lookup"><span data-stu-id="b484d-174">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="b484d-175">Полное имя этого типа утверждения `http://tempuri.org:accessAuthorized` (вместе с связанным пространством имен) используется в файле конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="b484d-175">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="b484d-176">Значение этого утверждения указывает на присутствие этого утверждения, и предполагается, что служба STS B установила его равным `true`.</span><span class="sxs-lookup"><span data-stu-id="b484d-176">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="b484d-177">Во время выполнения эта политика применяется классом `MyServiceOperationRequirement`, реализованным в составе службы `MyService`.</span><span class="sxs-lookup"><span data-stu-id="b484d-177">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="b484d-178">Служба STS B</span><span class="sxs-lookup"><span data-stu-id="b484d-178">STS B</span></span>  

 <span data-ttu-id="b484d-179">На следующем рисунке показана служба STS B. Как говорилось выше, служба маркеров безопасности (STS) также представляет собой веб-службу и может иметь свои конечные точки, политику и т. д.</span><span class="sxs-lookup"><span data-stu-id="b484d-179">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![Схема, показывающая службу маркеров безопасности B.](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="b484d-181">Служба STS B предоставляет одну конечную точку, `STSEndpoint`, которую можно использовать для запроса маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="b484d-181">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="b484d-182">В частности, служба STS B выдает маркеры SAML с утверждением `accessAuthorized`, которые могут быть предъявлены на сайте службы `MyService` для доступа к службе.</span><span class="sxs-lookup"><span data-stu-id="b484d-182">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="b484d-183">В то же время служба STS B требует от пользователей предъявления допустимого маркера SAML, выданного службой STS A и содержащего утверждение `userAuthenticated`.</span><span class="sxs-lookup"><span data-stu-id="b484d-183">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="b484d-184">Это декларативно указано в конфигурации службы STS.</span><span class="sxs-lookup"><span data-stu-id="b484d-184">This is declaratively specified in the STS configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="b484d-185">Опять же, `userAuthenticated` утверждение — это тип утверждения, необходимый для STS B. Полное имя этого типа утверждения — `http://tempuri.org:userAuthenticated` (вместе с связанным пространством имен), которое используется в файле конфигурации STS.</span><span class="sxs-lookup"><span data-stu-id="b484d-185">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="b484d-186">Значение этого утверждения указывает на присутствие этого утверждения, и предполагается, что служба STS A установила его равным `true`.</span><span class="sxs-lookup"><span data-stu-id="b484d-186">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="b484d-187">Во время выполнения эта политика применяется классом `STS_B_OperationRequirement`, реализованным в составе службы STS B.</span><span class="sxs-lookup"><span data-stu-id="b484d-187">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="b484d-188">Если проверка доступа пройдена, служба STS B выдает маркер SAML с утверждением `accessAuthorized`.</span><span class="sxs-lookup"><span data-stu-id="b484d-188">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="b484d-189">Служба STS A</span><span class="sxs-lookup"><span data-stu-id="b484d-189">STS A</span></span>  

 <span data-ttu-id="b484d-190">На следующем рисунке показана служба STS A.</span><span class="sxs-lookup"><span data-stu-id="b484d-190">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="b484d-191">![Федерация](media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="b484d-191">![Federation](media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="b484d-192">Как и STS B, служба STS A также представляет собой веб-службу, выдающую маркеры безопасности и предоставляющую с этой целью одну конечную точку.</span><span class="sxs-lookup"><span data-stu-id="b484d-192">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="b484d-193">Однако он использует другую привязку ( `wsHttpBinding` ) и требует, чтобы пользователи представими допустимый CardSpace с `emailAddress` утверждением.</span><span class="sxs-lookup"><span data-stu-id="b484d-193">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid CardSpace with an `emailAddress` claim.</span></span> <span data-ttu-id="b484d-194">В ответ она выдает маркеры SAML с утверждением `userAuthenticated`.</span><span class="sxs-lookup"><span data-stu-id="b484d-194">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="b484d-195">Это декларативно указано в конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="b484d-195">This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"
                       storeName="My" />  
       </identity>  
    </endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b484d-196">Во время выполнения эта политика применяется классом `STS_A_OperationRequirement`, реализованным в составе службы STS A.</span><span class="sxs-lookup"><span data-stu-id="b484d-196">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="b484d-197">Если проверка доступа возвратила значение `true`, служба STS A выдает маркер SAML с утверждением `userAuthenticated`.</span><span class="sxs-lookup"><span data-stu-id="b484d-197">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="b484d-198">Клиент в организации A</span><span class="sxs-lookup"><span data-stu-id="b484d-198">Client at Organization A</span></span>  

 <span data-ttu-id="b484d-199">На следующем рисунке показан клиент в организации A и шаги, которые включает в себя вызов функции `MyService`.</span><span class="sxs-lookup"><span data-stu-id="b484d-199">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="b484d-200">Для полноты картины включены также другие функциональные компоненты.</span><span class="sxs-lookup"><span data-stu-id="b484d-200">The other functional components are also included for completeness.</span></span>  
  
 ![Схема, демонстрирующая шаги в вызове службы MyService.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="b484d-202">Итоги</span><span class="sxs-lookup"><span data-stu-id="b484d-202">Summary</span></span>  

 <span data-ttu-id="b484d-203">Федеративная безопасность обеспечивает четкое разделение ответственности и позволяет выстраивать безопасные, масштабируемые архитектуры служб.</span><span class="sxs-lookup"><span data-stu-id="b484d-203">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="b484d-204">В качестве платформы для создания и развертывания распределенных приложений WCF предоставляет встроенную поддержку реализации федеративной безопасности.</span><span class="sxs-lookup"><span data-stu-id="b484d-204">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b484d-205">См. также</span><span class="sxs-lookup"><span data-stu-id="b484d-205">See also</span></span>

- [<span data-ttu-id="b484d-206">Безопасность</span><span class="sxs-lookup"><span data-stu-id="b484d-206">Security</span></span>](security.md)
