---
description: Дополнительные сведения см. в статье как создать дуплексную федеративный привязку
title: Практическое руководство. Создание дуплексной федеративной привязки
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 92d5eeeffab88d88aa245b51738048dced2d5d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779911"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="94a20-103">Практическое руководство. Создание дуплексной федеративной привязки</span><span class="sxs-lookup"><span data-stu-id="94a20-103">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="94a20-104">Привязка <xref:System.ServiceModel.WSFederationHttpBinding> поддерживает только датаграмму и контракты обмена сообщениями «запрос-ответ».</span><span class="sxs-lookup"><span data-stu-id="94a20-104"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="94a20-105">Чтобы использовать контакт дуплексного обмена сообщениями, необходимо создать пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="94a20-105">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="94a20-106">В процедурах ниже показана методика выполнения этой операции в конфигурации с использованием режима безопасности сообщений для транспортов HTTP и TCP и с использованием смешанного режима безопасности для транспорта TCP.</span><span class="sxs-lookup"><span data-stu-id="94a20-106">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="94a20-107">Образец кода, в котором показаны все 3 привязки, представлен в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="94a20-107">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="94a20-108">Также можно создать привязку в коде.</span><span class="sxs-lookup"><span data-stu-id="94a20-108">You can also create the binding in code.</span></span> <span data-ttu-id="94a20-109">Описание создаваемого стека элементов привязки см. в разделе [инструкции. Создание пользовательской привязки с помощью SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="94a20-109">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="94a20-110">Создание дуплексной федеративной пользовательской привязки с использованием HTTP</span><span class="sxs-lookup"><span data-stu-id="94a20-110">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="94a20-111">В [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) узле файла конфигурации создайте [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="94a20-111">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="94a20-112">Внутри [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) элемента создайте [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) элемент с `name` атрибутом, для которого задано значение `FederationDuplexHttpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="94a20-112">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="94a20-113">Внутри [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) элемента создайте [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) элемент с `authenticationMode` атрибутом, для которого задано значение `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="94a20-113">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="94a20-114">Внутри [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) элемента создайте элемент, атрибут которого имеет [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` значение `IssuedTokenForCertificate` или `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="94a20-114">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="94a20-115">После [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) элемента создайте пустой [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="94a20-115">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="94a20-116">После [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) элемента создайте пустой [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="94a20-116">Following the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="94a20-117">После [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) элемента создайте пустой [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="94a20-117">Following the [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="94a20-118">Создание дуплексной федеративной пользовательской привязки с использованием режима безопасности сообщения TCP</span><span class="sxs-lookup"><span data-stu-id="94a20-118">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="94a20-119">В [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) узле файла конфигурации создайте [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="94a20-119">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="94a20-120">Внутри [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) элемента создайте [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) элемент с `name` атрибутом, для которого задано значение `FederationDuplexTcpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="94a20-120">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="94a20-121">Внутри [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) элемента создайте [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) элемент с `authenticationMode` атрибутом, для которого задано значение `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="94a20-121">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="94a20-122">Внутри [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) элемента создайте элемент, атрибут которого имеет [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` значение `IssuedTokenForCertificate` или `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="94a20-122">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="94a20-123">После [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) элемента создайте пустой [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="94a20-123">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="94a20-124">Создание дуплексной федеративной пользовательской привязки с использованием смешанного режима безопасности TCP</span><span class="sxs-lookup"><span data-stu-id="94a20-124">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="94a20-125">В [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) узле файла конфигурации создайте [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="94a20-125">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="94a20-126">Внутри [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) элемента создайте [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) элемент с `name` атрибутом, для которого задано значение `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` .</span><span class="sxs-lookup"><span data-stu-id="94a20-126">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="94a20-127">Внутри [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) элемента создайте [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) элемент с `authenticationMode` атрибутом, для которого задано значение `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="94a20-127">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="94a20-128">Внутри [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) элемента создайте элемент, атрибут которого имеет [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` значение `IssuedTokenForCertificate` или `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="94a20-128">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="94a20-129">После [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) элемента создайте пустой [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="94a20-129">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="94a20-130">После [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) элемента создайте пустой [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="94a20-130">Following the [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="94a20-131">Образец кода</span><span class="sxs-lookup"><span data-stu-id="94a20-131">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="94a20-132">Образец с 3 привязками</span><span class="sxs-lookup"><span data-stu-id="94a20-132">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="94a20-133">Вставьте следующий код в свой файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="94a20-133">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="94a20-134">Пример</span><span class="sxs-lookup"><span data-stu-id="94a20-134">Example</span></span>

```xml
<bindings>
   <customBinding>
      <binding name="FederationDuplexHttpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <compositeDuplex />
          <oneWay />
          <httpTransport />
       </binding>
<!-- duplex over https is not supported -->
       <binding name="FederationDuplexTcpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <tcpTransport />
       </binding>
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />
          </security>
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->
          <sslStreamSecurity />
          <tcpTransport />
       </binding>
    </customBinding>
</bindings>
```
