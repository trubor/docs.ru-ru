---
description: 'Дополнительные сведения: использование нескольких схем проверки подлинности в WCF'
title: Использование в WCF нескольких схем проверки подлинности
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: fd03a13c5d38bbf26e2b6079d1320bc389c9f20b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779716"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="5d6b9-103">Использование в WCF нескольких схем проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="5d6b9-103">Using Multiple Authentication Schemes with WCF</span></span>

<span data-ttu-id="5d6b9-104">В WCF теперь можно указать несколько схем проверки подлинности на одной конечной точке.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-104">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="5d6b9-105">Кроме того, службы, размещенные на веб-серверах, могут наследовать свои параметры проверки подлинности непосредственно из IIS.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-105">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="5d6b9-106">Резидентные службы могут указывать, какие схемы проверки подлинности можно использовать.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-106">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="5d6b9-107">Дополнительные сведения о настройке параметров проверки подлинности в IIS см. в разделе [Проверка подлинности IIS](https://go.microsoft.com/fwlink/?LinkId=232458) .</span><span class="sxs-lookup"><span data-stu-id="5d6b9-107">For more information about setting authentication settings in IIS, see [IIS Authentication](https://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="5d6b9-108">Службы, размещенные в IIS</span><span class="sxs-lookup"><span data-stu-id="5d6b9-108">IIS-Hosted Services</span></span>  

 <span data-ttu-id="5d6b9-109">Для служб, размещенных в IIS, задайте схемы проверки подлинности, которые планируется использовать в IIS.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-109">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="5d6b9-110">Затем в файле web.config службы в конфигурации привязки укажите тип clientCredential в виде "InheritedFromHost", как показано в следующем фрагменте кода XML:</span><span class="sxs-lookup"><span data-stu-id="5d6b9-110">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="5d6b9-111">Можно указать, что для службы необходимо использовать только подмножество схем проверки подлинности с помощью Сервицеаусентикатионбехавиор или \<serviceAuthenticationManager> элемента.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-111">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="5d6b9-112">Настраивая это в коде, используйте ServiceAuthenticationBehavior, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-112">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="5d6b9-113">При настройке этого элемента в файле конфигурации используйте элемент, \<serviceAuthenticationManager> как показано в следующем фрагменте кода XML.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-113">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="5d6b9-114">Это гарантирует использование только подмножество перечисленных здесь схем проверки подлинности для применения на конечной точке службы в зависимости от того, что было выбрано на IIS.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-114">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="5d6b9-115">Это означает, что разработчик может исключить, например, простую проверку подлинности из списка путем исключения ее из списка serviceAuthenticationManager, и она не будет применена на конечной точке службы, даже если она активирована в IIS.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-115">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="5d6b9-116">Резидентные службы</span><span class="sxs-lookup"><span data-stu-id="5d6b9-116">Self-Hosted Services</span></span>  

 <span data-ttu-id="5d6b9-117">Резидентные службы настраиваются несколько иначе, так как отсутствует наследование параметров из IIS.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-117">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="5d6b9-118">Здесь вы используете \<serviceAuthenticationManager> Element или сервицеаусентикатионбехавиор, чтобы указать параметры проверки подлинности, которые будут унаследованы.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-118">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="5d6b9-119">Соответствующий код выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5d6b9-119">In code it looks like this:</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="5d6b9-120">В конфигурации это выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5d6b9-120">In config, it looks like this:</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="5d6b9-121">Затем можно указать InheritFromHost в параметрах привязки, как показано в следующем фрагменте кода XML.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-121">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="5d6b9-122">Кроме того, можно определить схемы проверки подлинности в пользовательской привязке, задав схемы проверки подлинности на элементе привязки транспорта HTTP, как показано в следующем фрагменте конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5d6b9-122">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d6b9-123">См. также</span><span class="sxs-lookup"><span data-stu-id="5d6b9-123">See also</span></span>

- [<span data-ttu-id="5d6b9-124">Привязки и безопасность</span><span class="sxs-lookup"><span data-stu-id="5d6b9-124">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="5d6b9-125">Конечные точки: адреса, привязки и контракты</span><span class="sxs-lookup"><span data-stu-id="5d6b9-125">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="5d6b9-126">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="5d6b9-126">Configuring System-Provided Bindings</span></span>](configuring-system-provided-bindings.md)
- [<span data-ttu-id="5d6b9-127">Возможности безопасности при использовании пользовательских привязок</span><span class="sxs-lookup"><span data-stu-id="5d6b9-127">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="5d6b9-128">Привязки</span><span class="sxs-lookup"><span data-stu-id="5d6b9-128">Bindings</span></span>](bindings.md)
- [<span data-ttu-id="5d6b9-129">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="5d6b9-129">Custom Bindings</span></span>](../extending/custom-bindings.md)
