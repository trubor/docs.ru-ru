---
description: 'Дополнительные сведения: Trusted фасад Service'
title: Доверенная фасадная служба
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: aebfa89c47d5e8ea37e210b2d7b19afbe204a1a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685482"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="f4e5d-103">Доверенная фасадная служба</span><span class="sxs-lookup"><span data-stu-id="f4e5d-103">Trusted Facade Service</span></span>

<span data-ttu-id="f4e5d-104">В этом образце сценария показано, как передать сведения об удостоверении вызывающего объекта из одной службы в другую с помощью инфраструктуры безопасности Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f4e5d-104">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="f4e5d-105">Обычно разработчики обеспечивают предоставление функциональных возможностей службы в открытую сеть через "фасадную" службу.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-105">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="f4e5d-106">Фасадная служба обычно размещается в демилитаризованной зоне (также называемой промежуточной подсетью или DMZ) и взаимодействует с серверной службой, реализующей бизнес-логику и имеющей доступ к внутренним данным.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-106">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="f4e5d-107">Коммуникационный канал между фасадной службой и серверной службой проходит через брандмауэр, и обычно он используется только для одной цели.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-107">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="f4e5d-108">Код в этом образце состоит из следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="f4e5d-108">This sample consists of the following components:</span></span>  
  
- <span data-ttu-id="f4e5d-109">Клиентская часть калькулятора</span><span class="sxs-lookup"><span data-stu-id="f4e5d-109">Calculator client</span></span>  
  
- <span data-ttu-id="f4e5d-110">Фасадная служба калькулятора</span><span class="sxs-lookup"><span data-stu-id="f4e5d-110">Calculator façade service</span></span>  
  
- <span data-ttu-id="f4e5d-111">Серверная служба калькулятора</span><span class="sxs-lookup"><span data-stu-id="f4e5d-111">Calculator backend service</span></span>  
  
 <span data-ttu-id="f4e5d-112">Фасадная служба проверяет запрос и подлинность вызывающей стороны.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-112">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="f4e5d-113">После успешного выполнения этих проверок она передает запрос серверной службе по управляемому коммуникационному каналу из демилитаризованной зоны во внутреннюю сеть.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-113">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="f4e5d-114">В передаваемый запрос фасадная служба добавляет удостоверение вызывающей стороны, чтобы серверная служба могла использовать его при обработке.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-114">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="f4e5d-115">Это удостоверение передается с помощью маркера безопасности `Username` в заголовке сообщения `Security` .</span><span class="sxs-lookup"><span data-stu-id="f4e5d-115">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="f4e5d-116">В примере используется инфраструктура безопасности WCF для передачи и извлечения этих сведений из `Security` заголовка.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-116">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f4e5d-117">Серверная служба доверяет результатам проверки подлинности вызывающей стороны, выполненной фасадной службой.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-117">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="f4e5d-118">Поэтому серверная служба не выполняет проверку подлинности повторно. Она использует удостоверение, предоставленное фасадной службой в переданном запросе.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-118">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="f4e5d-119">Это отношение доверия требует, чтобы серверная служба проверяла подлинность фасадной службы, чтобы убедиться, что сообщение передано из надежного источника (в данном случае - от фасадной службы).</span><span class="sxs-lookup"><span data-stu-id="f4e5d-119">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="f4e5d-120">Реализация</span><span class="sxs-lookup"><span data-stu-id="f4e5d-120">Implementation</span></span>  

 <span data-ttu-id="f4e5d-121">В этом образце используются два пути обмена данными:</span><span class="sxs-lookup"><span data-stu-id="f4e5d-121">There are two communication paths in this sample.</span></span> <span data-ttu-id="f4e5d-122">между клиентом и фасадной службой и между фасадной службой и серверной службой.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-122">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="f4e5d-123">Путь обмена данными между клиентом и фасадной службой</span><span class="sxs-lookup"><span data-stu-id="f4e5d-123">Communication Path between Client and Façade Service</span></span>  

 <span data-ttu-id="f4e5d-124">На пути обмена данными между клиентом и фасадной службой используется привязка `wsHttpBinding` и тип учетных данных клиента `UserName` .</span><span class="sxs-lookup"><span data-stu-id="f4e5d-124">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="f4e5d-125">Это означает, что фасадная служба проверяет подлинность клиента по имени пользователя и паролю, а клиент проверяет подлинность фасадной службы с помощью сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-125">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="f4e5d-126">Конфигурация привязки выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-126">The binding configuration looks like the following example.</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="f4e5d-127">Фасадная служба проверяет подлинность вызывающей стороны с помощью пользовательской реализации класса `UserNamePasswordValidator` .</span><span class="sxs-lookup"><span data-stu-id="f4e5d-127">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="f4e5d-128">Для простоты примера проверка подлинности проверяет только соответствие имени пользователя представленному паролю.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-128">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="f4e5d-129">На практике проверка подлинности пользователя обычно выполняется с помощью Active Directory или пользовательского поставщика членства ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-129">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="f4e5d-130">Код, реализующий проверку подлинности, находится в файле `FacadeService.cs` .</span><span class="sxs-lookup"><span data-stu-id="f4e5d-130">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="f4e5d-131">Пользовательский модуль проверки настроен для использования в рамках поведения `serviceCredentials` в файле конфигурации фасадной службы.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-131">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="f4e5d-132">Это поведение также используется для настройки сертификата X.509 службы.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-132">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate
               findValue="localhost"
               storeLocation="LocalMachine"
               storeName="My"
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="f4e5d-133">Путь обмена данными между фасадной службой и серверной службой</span><span class="sxs-lookup"><span data-stu-id="f4e5d-133">Communication Path between Façade Service and Backend Service</span></span>  

 <span data-ttu-id="f4e5d-134">На пути обмена данными между фасадной службой и серверной службой используется привязка `customBinding` , включающая в себя несколько элементов привязки.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-134">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="f4e5d-135">Эта привязка выполняет две задачи.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-135">This binding accomplishes two things.</span></span> <span data-ttu-id="f4e5d-136">Она проверяет подлинность фасадной службы и серверной службы, обеспечивая безопасность связи и надежность источника данных.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-136">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="f4e5d-137">Кроме того, она передает удостоверение изначальной вызывающей стороны в маркере безопасности `Username` .</span><span class="sxs-lookup"><span data-stu-id="f4e5d-137">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="f4e5d-138">В этом случае серверной службе передается только имя пользователя изначальной вызывающей стороны (пароль не указывается в сообщении).</span><span class="sxs-lookup"><span data-stu-id="f4e5d-138">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="f4e5d-139">Это обуславливается тем, что серверная служба доверяет фасадной службе проверку подлинности вызывающей стороны, выполняемую перед отправкой запроса.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-139">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="f4e5d-140">Поскольку серверная служба проверяет подлинность фасадной службы, она доверяет информации, содержащейся в переданном от нее запросе.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-140">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="f4e5d-141">Ниже приведена конфигурация привязки для этого пути обмена данными.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-141">The following is the binding configuration for this communication path.</span></span>  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="f4e5d-142">[\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)Элемент Binding следит за передачей и извлечением имени пользователя вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-142">The [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="f4e5d-143">[\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md)А также [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) позаботится о проверке подлинности фасадной и серверных служб и защиты сообщений.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-143">The [\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="f4e5d-144">Чтобы перенаправить запрос, реализация службы фасадной должна предоставить имя пользователя исходного вызывающего объекта, чтобы инфраструктура безопасности WCF могла поместить его в перенаправленное сообщение.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-144">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="f4e5d-145">Фасадная служба предоставляет имя пользователя изначальной вызывающей стороны в виде значения свойства `ClientCredentials` экземпляра клиентского прокси-класса, используемого для обмена информацией между фасадной и серверной службами.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-145">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="f4e5d-146">В следующем примере кода показана реализация метода `GetCallerIdentity` фасадной службы.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-146">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="f4e5d-147">В прочих методах используются аналогичные принципы.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-147">Other methods use the same pattern.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 <span data-ttu-id="f4e5d-148">Как показано в предыдущем примере кода, в свойстве `ClientCredentials` не задается пароль (в нем содержится только имя пользователя).</span><span class="sxs-lookup"><span data-stu-id="f4e5d-148">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="f4e5d-149">Инфраструктура безопасности WCF создает маркер безопасности имени пользователя без пароля в этом случае, что именно необходимо в этом сценарии.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-149">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="f4e5d-150">В серверной службе должна быть проверена подлинность информации, содержащейся в маркере безопасности.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-150">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="f4e5d-151">По умолчанию система безопасности WCF пытается сопоставлять пользователя с учетной записью Windows, используя указанный пароль.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-151">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="f4e5d-152">В данном случае пароль не предоставляется, и серверной службе не требуется проверять имя пользователя, поскольку эта процедура уже выполнена фасадной службой.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-152">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="f4e5d-153">Для реализации этой функции в WCF предоставляется пользовательский интерфейс `UserNamePasswordValidator` , который обеспечивает только принудительное использование имени пользователя в маркере и не выполняет дополнительной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-153">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="f4e5d-154">Пользовательский модуль проверки настроен для использования в рамках поведения `serviceCredentials` в файле конфигурации фасадной службы.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-154">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="f4e5d-155">Для извлечения имени пользователя и информации об учетной записи доверенной фасадной службы в серверной службе реализован класс `ServiceSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="f4e5d-155">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="f4e5d-156">В следующем примере кода показана реализация метода `GetCallerIdentity` .</span><span class="sxs-lookup"><span data-stu-id="f4e5d-156">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 <span data-ttu-id="f4e5d-157">Информация об учетной записи фасадной службы извлекается с помощью свойства `ServiceSecurityContext.Current.WindowsIdentity` .</span><span class="sxs-lookup"><span data-stu-id="f4e5d-157">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="f4e5d-158">Для доступа к информации об изначальной вызывающей стороне серверная служба использует свойство `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` .</span><span class="sxs-lookup"><span data-stu-id="f4e5d-158">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="f4e5d-159">Она выполняет поиск утверждения `Identity` , принадлежащего к типу `Name`.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-159">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="f4e5d-160">Это утверждение автоматически создается инфраструктурой безопасности WCF на основе сведений, содержащихся в `Username` маркере безопасности.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-160">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="f4e5d-161">Выполнение примера</span><span class="sxs-lookup"><span data-stu-id="f4e5d-161">Running the sample</span></span>  

 <span data-ttu-id="f4e5d-162">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-162">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f4e5d-163">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-163">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="f4e5d-164">Можно нажать клавишу ВВОД в окнах консолей фасадной и серверной служб, чтобы закрыть их.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-164">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
```console  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="f4e5d-165">В состав образца сценария, где используется доверенная фасадная служба, входит пакетный файл Setup.bat, позволяющий настроить для сервера соответствующий сертификат для запуска фасадной службы, необходимый для проверки ее подлинности клиентом.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-165">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="f4e5d-166">Подробные сведения см. в описании процедуры настройки в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-166">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="f4e5d-167">Ниже приводится краткое описание различных разделов пакетного файла.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-167">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="f4e5d-168">Создание сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-168">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="f4e5d-169">Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-169">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="f4e5d-170">В переменной `%SERVER_NAME%` указывается имя сервера. Значение по умолчанию - localhost.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-170">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="f4e5d-171">Сертификат хранится в хранилище LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-171">The certificate is stored in the LocalMachine store.</span></span>  
  
- <span data-ttu-id="f4e5d-172">Установка сертификата фасадной службы в хранилище доверенных сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-172">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="f4e5d-173">Следующая строка копирует сертификат фасадной службы в хранилище доверенных лиц клиента.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-173">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="f4e5d-174">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-174">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="f4e5d-175">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-175">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f4e5d-176">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="f4e5d-176">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f4e5d-177">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4e5d-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f4e5d-178">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4e5d-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="f4e5d-179">Запуск образца на том же компьютере</span><span class="sxs-lookup"><span data-stu-id="f4e5d-179">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="f4e5d-180">Убедитесь, что путь включает папку, в которой хранится файл Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-180">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="f4e5d-181">Запустите файл Setup.bat из папки установки примера.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-181">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="f4e5d-182">При этом устанавливаются все сертификаты, необходимые для выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-182">This installs all the certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="f4e5d-183">Запустите программу BackendService.exe из каталога \BackendService\bin в отдельном окне консоли.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-183">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4. <span data-ttu-id="f4e5d-184">Запустите программу FacadeService.exe из каталога \FacadeService\bin в отдельном окне консоли.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-184">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5. <span data-ttu-id="f4e5d-185">Запустите программу Client.exe из каталога \client\bin.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-185">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="f4e5d-186">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-186">Client activity is displayed on the client console application.</span></span>  
  
6. <span data-ttu-id="f4e5d-187">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="f4e5d-187">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="f4e5d-188">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="f4e5d-188">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="f4e5d-189">После завершения работы примера запустите в папке примеров файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-189">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f4e5d-190">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-190">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f4e5d-191">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="f4e5d-191">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f4e5d-192">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-192">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f4e5d-193">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="f4e5d-193">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`
