---
description: 'Дополнительные сведения о: <windows> <clientCredentials> element'
title: <windows> элемента <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: d693ad914dfa02ef12a7c8520ca84be3a9595e73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682427"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="0e7fb-103">\<windows> элемента \<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="0e7fb-103">\<windows> of \<clientCredentials> Element</span></span>

<span data-ttu-id="0e7fb-104">Определяет параметры учетных данных Windows, которые используются для представления клиента.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-104">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**  
  
## <a name="syntax"></a><span data-ttu-id="0e7fb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0e7fb-105">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e7fb-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0e7fb-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0e7fb-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e7fb-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0e7fb-108">Attributes</span></span>  
  
|<span data-ttu-id="0e7fb-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0e7fb-109">Attribute</span></span>|<span data-ttu-id="0e7fb-110">Описание</span><span class="sxs-lookup"><span data-stu-id="0e7fb-110">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="0e7fb-111">Задает параметры олицетворения, сообщаемые клиентом серверу.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-111">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="0e7fb-112">Режим олицетворения, выбираемый клиентом, не задается принудительно для сервера.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-112">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="0e7fb-113">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0e7fb-114">-Identification: сервер может получить удостоверение и привилегии клиента, но не может олицетворять клиента.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-114">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="0e7fb-115">— Олицетворение. сервер может олицетворять контекст безопасности клиента в локальной системе.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-115">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="0e7fb-116">-Делегирование. сервер может олицетворять контекст безопасности клиента в удаленных системах.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-116">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="0e7fb-117">— Анонимно: сервер не может олицетворять или опознать клиента.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-117">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="0e7fb-118">-None: уровень олицетворения не назначен.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-118">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="0e7fb-119">Значение по умолчанию - Identification.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-119">The default is Identification.</span></span> <span data-ttu-id="0e7fb-120">Это атрибут типа <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-120">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="0e7fb-121">Если установить для данного свойства значение `true`, то проверка подлинности может понижаться до NTLM в том случае, если проверка Kerberos недоступна.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-121">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="0e7fb-122">Если задать для этого свойства значение `false` Windows Communication Foundation (WCF), лучше будет создавать исключение, если используется NTLM.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-122">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="0e7fb-123">Обратите внимание, что установка для данного свойства значения `false` не предотвращает отправки учетных данных NTLM по сети.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-123">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e7fb-124">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0e7fb-124">Child Elements</span></span>  

 <span data-ttu-id="0e7fb-125">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e7fb-126">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0e7fb-126">Parent Elements</span></span>  
  
|<span data-ttu-id="0e7fb-127">Элемент</span><span class="sxs-lookup"><span data-stu-id="0e7fb-127">Element</span></span>|<span data-ttu-id="0e7fb-128">Описание</span><span class="sxs-lookup"><span data-stu-id="0e7fb-128">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="0e7fb-129">Задает учетные данные, используемые для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="0e7fb-129">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e7fb-130">См. также</span><span class="sxs-lookup"><span data-stu-id="0e7fb-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="0e7fb-131">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="0e7fb-131">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="0e7fb-132">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="0e7fb-132">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="0e7fb-133">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="0e7fb-133">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
