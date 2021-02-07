---
description: 'Дополнительные сведения <message> о: <netMsmqBinding>'
title: <message> из <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 0e8cf641ef8ba5361318f7b658d5d60beef6ce56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749588"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="5fc6c-103">\<message> из \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="5fc6c-103">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="5fc6c-104">Определяет параметры безопасности сообщений SOAP для данной привязки `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-104">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  

## <a name="syntax"></a><span data-ttu-id="5fc6c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5fc6c-105">Syntax</span></span>

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5fc6c-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="5fc6c-106">Attributes and Elements</span></span>

<span data-ttu-id="5fc6c-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5fc6c-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5fc6c-108">Attributes</span></span>

|<span data-ttu-id="5fc6c-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="5fc6c-109">Attribute</span></span>|<span data-ttu-id="5fc6c-110">Описание</span><span class="sxs-lookup"><span data-stu-id="5fc6c-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="5fc6c-111">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="5fc6c-111">algorithmSuite</span></span>|<span data-ttu-id="5fc6c-112">Задает алгоритмы шифрования сообщений и ключей, которые используются для обеспечения безопасности на уровне сообщений для сообщений, которые отправляются с помощью транспорта MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-112">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="5fc6c-113">Значение по умолчанию — `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-113">The default value is `Aes256`.</span></span> <span data-ttu-id="5fc6c-114">Это атрибут типа <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-114">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="5fc6c-115">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="5fc6c-115">clientCredentialType</span></span>|<span data-ttu-id="5fc6c-116">Задает тип учетных данных, используемых при проверке подлинности клиента для сообщений, которые отправляются с помощью транспорта MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-116">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="5fc6c-117">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5fc6c-118">-None: Это позволяет службе взаимодействовать с анонимными клиентами.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-118">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="5fc6c-119">Как для службы, так и для клиента учетные данные не требуются.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-119">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="5fc6c-120">-Windows: Это позволяет обмениваться сообщениями SOAP в контексте с проверкой подлинности учетных данных Windows.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-120">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="5fc6c-121">В этом случае всегда выполняется проверка подлинности на основе Kerberos.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-121">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="5fc6c-122">-UserName: Это позволяет службе требовать проверку подлинности клиента с помощью учетных данных имени пользователя.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-122">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="5fc6c-123">Учетные данные в этом случае необходимо указать с помощью `clientCredentials` **предупреждения:**  Windows Communication Foundation (WCF) не поддерживает отправку дайджеста пароля или получение ключей с помощью пароля и использование таких ключей для обеспечения безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-123">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="5fc6c-124">Таким образом, WCF обеспечивает защиту Exchange при использовании учетных данных пользователя.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-124">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="5fc6c-125">В данном режиме требуется, чтобы сертификат службы был указан на стороне клиента при помощи поведения `clientCredential` и при помощи `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-125">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="5fc6c-126">-Certificate: Это позволяет службе требовать проверку подлинности клиента с помощью сертификата.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-126">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="5fc6c-127">В этом случае учетные данные клиента должны быть определены с помощью поведения `clientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-127">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="5fc6c-128">Учетные данные службы в данном случае должны быть определены с помощью поведения `clientCredentials`, которому задается значение `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-128">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="5fc6c-129">-CardSpace: Это позволяет службе требовать проверку подлинности клиента с помощью CardSpace.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-129">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="5fc6c-130">Необходимо определить `serviceCertificate` в поведении `clientCredential`.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-130">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="5fc6c-131">Значение по умолчанию — `Windows`.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-131">The default value is `Windows`.</span></span> <span data-ttu-id="5fc6c-132">Это атрибут типа <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-132">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5fc6c-133">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5fc6c-133">Child Elements</span></span>

<span data-ttu-id="5fc6c-134">None</span><span class="sxs-lookup"><span data-stu-id="5fc6c-134">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5fc6c-135">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5fc6c-135">Parent Elements</span></span>

|<span data-ttu-id="5fc6c-136">Элемент</span><span class="sxs-lookup"><span data-stu-id="5fc6c-136">Element</span></span>|<span data-ttu-id="5fc6c-137">Описание</span><span class="sxs-lookup"><span data-stu-id="5fc6c-137">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="5fc6c-138">Определяет параметры безопасности для привязки.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-138">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="5fc6c-139">См. также</span><span class="sxs-lookup"><span data-stu-id="5fc6c-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="5fc6c-140">Очереди в WCF</span><span class="sxs-lookup"><span data-stu-id="5fc6c-140">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="5fc6c-141">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="5fc6c-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5fc6c-142">Привязки</span><span class="sxs-lookup"><span data-stu-id="5fc6c-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5fc6c-143">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="5fc6c-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5fc6c-144">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="5fc6c-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
