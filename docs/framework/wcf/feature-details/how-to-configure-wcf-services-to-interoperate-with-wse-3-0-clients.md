---
description: Дополнительные сведения см. в статье Настройка служб WCF для взаимодействия с клиентами WSE 3,0.
title: Практическое руководство. Настройка служб WCF для взаимодействия с клиентами WSE 3.0
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: d48b24ac7787a9863744ee9b6a4a984cb6b371e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779937"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="ace0e-103">Практическое руководство. Настройка служб WCF для взаимодействия с клиентами WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="ace0e-103">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>

<span data-ttu-id="ace0e-104">Службы Windows Communication Foundation (WCF) являются совместимыми с расширениями веб-служб 3,0 для клиентов Microsoft .NET (WSE), если службы WCF настроены для использования версии спецификации WS-Addressing, Август 2004.</span><span class="sxs-lookup"><span data-stu-id="ace0e-104">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="ace0e-105">Включение службы WCF для взаимодействия с клиентами WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="ace0e-105">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>

1. <span data-ttu-id="ace0e-106">Определите пользовательскую привязку для службы WCF.</span><span class="sxs-lookup"><span data-stu-id="ace0e-106">Define a custom binding for the WCF service.</span></span>

    <span data-ttu-id="ace0e-107">Чтобы указать, что для кодирования сообщений используется версия спецификации WS-Addressing от августа 2004 г., необходимо создать пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="ace0e-107">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>

    1. <span data-ttu-id="ace0e-108">Добавьте дочерний элемент в [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) файл конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="ace0e-108">Add a child [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>

    2. <span data-ttu-id="ace0e-109">Укажите имя привязки, добавив в [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) и установив `name` атрибут.</span><span class="sxs-lookup"><span data-stu-id="ace0e-109">Specify a name for the binding, by adding a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>

    3. <span data-ttu-id="ace0e-110">Укажите режим проверки подлинности и версию спецификаций WS-Security, которые используются для защиты сообщений, совместимых с WSE 3,0, добавив дочерний элемент [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) в [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="ace0e-110">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md).</span></span>

        <span data-ttu-id="ace0e-111">Чтобы задать режим проверки подлинности, задайте `authenticationMode` атрибут [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ace0e-111">To set the authentication mode, set the `authenticationMode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="ace0e-112">Режим проверки подлинности примерно соответствует готовому к использованию утверждению безопасности в WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="ace0e-112">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="ace0e-113">Следующая таблица сопоставляет режимы проверки подлинности в WCF с готовыми утверждениями безопасности в WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="ace0e-113">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>

        |<span data-ttu-id="ace0e-114">Режим проверки подлинности WCF</span><span class="sxs-lookup"><span data-stu-id="ace0e-114">WCF Authentication Mode</span></span>|<span data-ttu-id="ace0e-115">Готовое к использованию утверждение безопасности WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="ace0e-115">WSE 3.0 turnkey security assertion</span></span>|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        <span data-ttu-id="ace0e-116">\* Одним из основных различий между `mutualCertificate10Security` `mutualCertificate11Security` утверждениями безопасности и готовностью является версия спецификации WS-Security, которую WSE использует для защиты сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="ace0e-116">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="ace0e-117">Для `mutualCertificate10Security` используется версия WS-Security 1.0, а для `mutualCertificate11Security` - версия WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="ace0e-117">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="ace0e-118">Для WCF версия спецификации WS-Security указана в `messageSecurityVersion` атрибуте [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ace0e-118">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>

        <span data-ttu-id="ace0e-119">Чтобы задать версию спецификации WS-Security, которая используется для защиты сообщений SOAP, установите `messageSecurityVersion` атрибут [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ace0e-119">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="ace0e-120">Для взаимодействия с WSE 3.0 установите для атрибута `messageSecurityVersion` значение <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span><span class="sxs-lookup"><span data-stu-id="ace0e-120">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>

    4. <span data-ttu-id="ace0e-121">Укажите, что в WCF используется версия спецификации WS-Addressing в августе 2004, добавив [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) и присвойте свойству `messageVersion` значение <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A> .</span><span class="sxs-lookup"><span data-stu-id="ace0e-121">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>

        > [!NOTE]
        > <span data-ttu-id="ace0e-122">При использовании протокола SOAP 1.2 задайте для атрибута `messageVersion` значение <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="ace0e-122">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>

2. <span data-ttu-id="ace0e-123">Укажите, что служба использует пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="ace0e-123">Specify that the service uses the custom binding.</span></span>

    1. <span data-ttu-id="ace0e-124">Присвойте `binding` атрибуту [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) элемента значение `customBinding` .</span><span class="sxs-lookup"><span data-stu-id="ace0e-124">Set the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>

    2. <span data-ttu-id="ace0e-125">Присвойте `bindingConfiguration` атрибуту [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) элемента значение, указанное в `name` атрибуте объекта [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="ace0e-125">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) for the custom binding.</span></span>

## <a name="example"></a><span data-ttu-id="ace0e-126">Пример</span><span class="sxs-lookup"><span data-stu-id="ace0e-126">Example</span></span>

<span data-ttu-id="ace0e-127">Следующий пример кода задает, что служба `Service.HelloWorldService` использует для взаимодействия с клиентами WSE 3.0 пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="ace0e-127">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="ace0e-128">Пользовательская привязка задает, что для кодирования пересылаемых сообщений используется версия спецификация WS-Addressing от августа 2004 г. и набор спецификаций WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="ace0e-128">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="ace0e-129">Защита сообщений обеспечивается с помощью режима проверки подлинности <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>.</span><span class="sxs-lookup"><span data-stu-id="ace0e-129">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <services>
      <service
        behaviorConfiguration="ServiceBehavior"
        name="Service.HelloWorldService">
        <endpoint binding="customBinding" address=""
          bindingConfiguration="ServiceBinding"
          contract="Service.IHelloWorld"></endpoint>
      </service>
    </services>

    <bindings>
      <customBinding>
        <binding name="ServiceBinding">
          <security authenticationMode="AnonymousForCertificate"
                  messageProtectionOrder="SignBeforeEncrypt"
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"
                  requireDerivedKeys="false">
          </security>
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>
          <httpTransport/>
        </binding>
      </customBinding>
    </bindings>
    <behaviors>
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">
        <serviceCredentials>
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>
        </serviceCredentials>
      </behavior>
    </behaviors>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ace0e-130">См. также</span><span class="sxs-lookup"><span data-stu-id="ace0e-130">See also</span></span>

- [<span data-ttu-id="ace0e-131">Практическое руководство. Изменение привязки, предоставляемой системой</span><span class="sxs-lookup"><span data-stu-id="ace0e-131">How to: Customize a System-Provided Binding</span></span>](../extending/how-to-customize-a-system-provided-binding.md)
