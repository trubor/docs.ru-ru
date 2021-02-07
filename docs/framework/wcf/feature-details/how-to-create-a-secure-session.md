---
description: 'Дополнительные сведения: как создать безопасный сеанс'
title: Практическое руководство. Создание сеанса безопасности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: 7d1c76ed2925c3c4cca4242f3f02b8850fb64f19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734715"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="e8418-103">Практическое руководство. Создание сеанса безопасности</span><span class="sxs-lookup"><span data-stu-id="e8418-103">How to: Create a Secure Session</span></span>

<span data-ttu-id="e8418-104">За исключением [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) привязки, предоставляемые системой привязки в Windows Communication Foundation (WCF) автоматически используют защищенные сеансы при включенной безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="e8418-104">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="e8418-105">По умолчанию безопасные сеансы не сохраняются на перезапускаемом веб-сервере.</span><span class="sxs-lookup"><span data-stu-id="e8418-105">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="e8418-106">После установления безопасного сеанса клиент и служба кэшируют ключ, связанный с безопасным сеансом.</span><span class="sxs-lookup"><span data-stu-id="e8418-106">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="e8418-107">При обмене сообщениями происходит только обмен идентификатором кэшированного ключа.</span><span class="sxs-lookup"><span data-stu-id="e8418-107">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="e8418-108">При перезапуске веб-сервера кэш также перезапускается, следовательно, веб-сервер не может извлечь кэшированный ключ для идентификатора.</span><span class="sxs-lookup"><span data-stu-id="e8418-108">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="e8418-109">В этом случае исключение передается назад клиенту.</span><span class="sxs-lookup"><span data-stu-id="e8418-109">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="e8418-110">Безопасные сеансы, использующие токен контекста безопасности с отслеживанием состояния (SCT), сохраняются при перезапуске веб-сервера.</span><span class="sxs-lookup"><span data-stu-id="e8418-110">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="e8418-111">Дополнительные сведения об использовании SCT с отслеживанием состояния в безопасном сеансе см. в разделе [инструкции. Создание маркера контекста безопасности для безопасного сеанса](how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="e8418-111">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="e8418-112">Задание использования службой безопасных сеансов с помощью одной из предоставляемых системой привязок</span><span class="sxs-lookup"><span data-stu-id="e8418-112">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
- <span data-ttu-id="e8418-113">Настройте службу на использование предоставляемой системой привязки, поддерживающей безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="e8418-113">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="e8418-114">За исключением [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) привязки, когда предоставляемые системой привязки настроены для использования безопасности сообщений, WCF автоматически использует защищенные сеансы.</span><span class="sxs-lookup"><span data-stu-id="e8418-114">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="e8418-115">В следующей таблице перечислены предоставляемые системой привязки, поддерживающие безопасность сообщений, и указано, является ли безопасность сообщений механизмом безопасности по умолчанию для данной привязки.</span><span class="sxs-lookup"><span data-stu-id="e8418-115">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="e8418-116">Предоставляемая системой привязка</span><span class="sxs-lookup"><span data-stu-id="e8418-116">System-provided binding</span></span>|<span data-ttu-id="e8418-117">Элемент конфигурации</span><span class="sxs-lookup"><span data-stu-id="e8418-117">Configuration element</span></span>|<span data-ttu-id="e8418-118">Безопасность сообщений включена по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e8418-118">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="e8418-119">Нет</span><span class="sxs-lookup"><span data-stu-id="e8418-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="e8418-120">Да</span><span class="sxs-lookup"><span data-stu-id="e8418-120">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="e8418-121">Да</span><span class="sxs-lookup"><span data-stu-id="e8418-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="e8418-122">Да</span><span class="sxs-lookup"><span data-stu-id="e8418-122">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="e8418-123">Нет</span><span class="sxs-lookup"><span data-stu-id="e8418-123">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="e8418-124">Нет</span><span class="sxs-lookup"><span data-stu-id="e8418-124">No</span></span>|  
  
     <span data-ttu-id="e8418-125">В следующем примере кода используется конфигурация для указания привязки с именем, `wsHttpBinding_Calculator` которая использует [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) , безопасность сообщений и защищенные сеансы.</span><span class="sxs-lookup"><span data-stu-id="e8418-125">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="e8418-126">В следующем примере кода указывается, что [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) для защиты службы используются, безопасность сообщений и безопасные сеансы `secureCalculator` .</span><span class="sxs-lookup"><span data-stu-id="e8418-126">The following code example specifies that the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="e8418-127">Защищенные сеансы можно отключить для, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) задав `establishSecurityContext` для атрибута значение `false` .</span><span class="sxs-lookup"><span data-stu-id="e8418-127">Secure sessions can be turned off for the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="e8418-128">Безопасные сеансы для других предоставляемых системой привязок можно отключить, только создав пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="e8418-128">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="e8418-129">Задание использования службой безопасных сеансов с помощью пользовательской привязки</span><span class="sxs-lookup"><span data-stu-id="e8418-129">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
- <span data-ttu-id="e8418-130">Создайте пользовательскую привязку, которая задает, что сообщения SOAP защищаются безопасным сеансом.</span><span class="sxs-lookup"><span data-stu-id="e8418-130">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="e8418-131">Дополнительные сведения о создании пользовательской привязки см. в разделе [инструкции. Настройка привязки System-Provided](../extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="e8418-131">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="e8418-132">В следующем примере кода с помощью конфигурации задается пользовательская привязка для обмена сообщениями с использованием безопасного сеанса.</span><span class="sxs-lookup"><span data-stu-id="e8418-132">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="e8418-133">В следующем примере кода создается пользовательская привязка, которая использует режим проверки подлинности <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> для начальной загрузки безопасного сеанса.</span><span class="sxs-lookup"><span data-stu-id="e8418-133">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e8418-134">См. также</span><span class="sxs-lookup"><span data-stu-id="e8418-134">See also</span></span>

- [<span data-ttu-id="e8418-135">Общие сведения о привязках WCF</span><span class="sxs-lookup"><span data-stu-id="e8418-135">WCF Bindings Overview</span></span>](../bindings-overview.md)
