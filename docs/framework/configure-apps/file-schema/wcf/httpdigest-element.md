---
description: 'Дополнительные сведения о: <httpDigest> element'
title: Элемент <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 2b11edcaab88ff3a2b437b1e886997e08b8c9fee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749666"
---
# <a name="httpdigest-element"></a><span data-ttu-id="7f51c-103">Элемент \<httpDigest></span><span class="sxs-lookup"><span data-stu-id="7f51c-103">\<httpDigest> Element</span></span>

<span data-ttu-id="7f51c-104">Задает учетные данные, используемые для дайджест-проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="7f51c-104">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**  
  
## <a name="syntax"></a><span data-ttu-id="7f51c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7f51c-105">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f51c-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="7f51c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7f51c-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="7f51c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f51c-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="7f51c-108">Attributes</span></span>  
  
|<span data-ttu-id="7f51c-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="7f51c-109">Attribute</span></span>|<span data-ttu-id="7f51c-110">Описание</span><span class="sxs-lookup"><span data-stu-id="7f51c-110">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="7f51c-111">Задает параметры олицетворения, сообщаемые клиентом серверу.</span><span class="sxs-lookup"><span data-stu-id="7f51c-111">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="7f51c-112">Режим олицетворения, выбираемый клиентом, не задается принудительно для сервера.</span><span class="sxs-lookup"><span data-stu-id="7f51c-112">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="7f51c-113">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="7f51c-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7f51c-114">-Identification: сервер может получить удостоверение и привилегии клиента, но не может олицетворять клиента.</span><span class="sxs-lookup"><span data-stu-id="7f51c-114">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="7f51c-115">— Олицетворение. сервер может олицетворять контекст безопасности клиента в локальной системе.</span><span class="sxs-lookup"><span data-stu-id="7f51c-115">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="7f51c-116">-Делегирование. сервер может олицетворять контекст безопасности клиента в удаленных системах.</span><span class="sxs-lookup"><span data-stu-id="7f51c-116">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="7f51c-117">— Анонимно: сервер не может олицетворять или опознать клиента.</span><span class="sxs-lookup"><span data-stu-id="7f51c-117">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="7f51c-118">-None: уровень олицетворения не назначен.</span><span class="sxs-lookup"><span data-stu-id="7f51c-118">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="7f51c-119">Значение по умолчанию - Identification.</span><span class="sxs-lookup"><span data-stu-id="7f51c-119">The default is Identification.</span></span> <span data-ttu-id="7f51c-120">Это атрибут типа <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="7f51c-120">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f51c-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="7f51c-121">Child Elements</span></span>  

 <span data-ttu-id="7f51c-122">None</span><span class="sxs-lookup"><span data-stu-id="7f51c-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f51c-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="7f51c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7f51c-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="7f51c-124">Element</span></span>|<span data-ttu-id="7f51c-125">Описание</span><span class="sxs-lookup"><span data-stu-id="7f51c-125">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="7f51c-126">Задает учетные данные, используемые для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="7f51c-126">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f51c-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="7f51c-127">Remarks</span></span>  

 <span data-ttu-id="7f51c-128">Хэш-кода — это хэш, определяемый с помощью алгоритма и набора входных данных.</span><span class="sxs-lookup"><span data-stu-id="7f51c-128">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="7f51c-129">Структура проверки подлинности и проверяемый объект согласуют алгоритм и обмениваются данными, используемыми в качестве входных.</span><span class="sxs-lookup"><span data-stu-id="7f51c-129">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="7f51c-130">Клиент может вычислить хэш и отправить его службе.</span><span class="sxs-lookup"><span data-stu-id="7f51c-130">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="7f51c-131">Служба также вычисляет хэш и сравнивает значения.</span><span class="sxs-lookup"><span data-stu-id="7f51c-131">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="7f51c-132">Совпадение значений подтверждает подлинность клиента.</span><span class="sxs-lookup"><span data-stu-id="7f51c-132">A match validates the client.</span></span>  
  
 <span data-ttu-id="7f51c-133">Эта функция должна быть включена с помощью Active Directory в Windows и службах IIS.</span><span class="sxs-lookup"><span data-stu-id="7f51c-133">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="7f51c-134">Дополнительные сведения см. [в статье дайджест-проверка подлинности в IIS 6,0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="7f51c-134">For more information, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f51c-135">См. также</span><span class="sxs-lookup"><span data-stu-id="7f51c-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="7f51c-136">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="7f51c-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7f51c-137">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="7f51c-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="7f51c-138">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="7f51c-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="7f51c-139">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="7f51c-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
