---
description: Дополнительные сведения см. в статье Включение обнаружения воспроизведения сообщений.
title: Практическое руководство. Включение обнаружения повтора сообщений
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: 743452195d5bf78360909a22ea81997c2712dd06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704671"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="9ff32-103">Практическое руководство. Включение обнаружения повтора сообщений</span><span class="sxs-lookup"><span data-stu-id="9ff32-103">How to: Enable Message Replay Detection</span></span>

<span data-ttu-id="9ff32-104">Атака воспроизведения заключается в том, что злоумышленник копирует поток сообщений между двумя сторонами и воспроизводит его для одной или нескольких сторон.</span><span class="sxs-lookup"><span data-stu-id="9ff32-104">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="9ff32-105">Если не приняты ответные меры, атакованные компьютеры обрабатывают этот поток как надлежащие сообщения, что приводит к ряду негативных последствий, таких как повторные заказы одного элемента.</span><span class="sxs-lookup"><span data-stu-id="9ff32-105">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="9ff32-106">Дополнительные сведения об обнаружении воспроизведения сообщений см. в разделе [обнаружение воспроизведения сообщений](/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="9ff32-106">For more information about message replay detection, see [Message Replay Detection](/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="9ff32-107">В следующей процедуре показаны различные свойства, которые можно использовать для управления обнаружением воспроизведения с помощью Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9ff32-107">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="9ff32-108">Управление обнаружением воспроизведения на стороне клиента с помощью кода</span><span class="sxs-lookup"><span data-stu-id="9ff32-108">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="9ff32-109">Создайте элемент <xref:System.ServiceModel.Channels.SecurityBindingElement> для использования в привязке <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="9ff32-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="9ff32-110">Дополнительные сведения см. в разделе [инструкции. Создание пользовательской привязки с помощью SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="9ff32-110">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="9ff32-111">В следующем примере используется объект <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, созданный с помощью объекта <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> класса <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="9ff32-111">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="9ff32-112">С помощью свойства <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> получите ссылку на класс <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> и задайте некоторые из следующих свойств согласно необходимости:</span><span class="sxs-lookup"><span data-stu-id="9ff32-112">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="9ff32-113">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-113">`DetectReplay`.</span></span> <span data-ttu-id="9ff32-114">Значение типа Boolean.</span><span class="sxs-lookup"><span data-stu-id="9ff32-114">A Boolean value.</span></span> <span data-ttu-id="9ff32-115">Управляет тем, пытается ли клиент обнаружить воспроизведение сообщений сервера.</span><span class="sxs-lookup"><span data-stu-id="9ff32-115">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="9ff32-116">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-116">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="9ff32-117">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-117">`MaxClockSkew`.</span></span> <span data-ttu-id="9ff32-118">Значение <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="9ff32-118">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="9ff32-119">Задает максимальную разницу по времени, допускаемую механизмом обнаружения воспроизведения между клиентом и сервером.</span><span class="sxs-lookup"><span data-stu-id="9ff32-119">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="9ff32-120">Механизм безопасности проверяет отправленную отметку времени и определяет, не слишком ли давно она отправлена.</span><span class="sxs-lookup"><span data-stu-id="9ff32-120">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="9ff32-121">Значение по умолчанию равно 5 минутам.</span><span class="sxs-lookup"><span data-stu-id="9ff32-121">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="9ff32-122">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-122">`ReplayWindow`.</span></span> <span data-ttu-id="9ff32-123">Значение `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-123">A `TimeSpan` value.</span></span> <span data-ttu-id="9ff32-124">Задает максимальное время жизни сообщения в сети с момента его отправки сервером (через промежуточные узлы), прежде чем оно доставляется клиенту.</span><span class="sxs-lookup"><span data-stu-id="9ff32-124">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="9ff32-125">Клиент отслеживает подписи сообщений, отправленных в течение последнего промежутка времени `ReplayWindow`, с целью обнаружения воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="9ff32-125">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="9ff32-126">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-126">`ReplayCacheSize`.</span></span> <span data-ttu-id="9ff32-127">Целочисленное значение.</span><span class="sxs-lookup"><span data-stu-id="9ff32-127">An integer value.</span></span> <span data-ttu-id="9ff32-128">Клиент сохраняет подписи сообщений в кэше.</span><span class="sxs-lookup"><span data-stu-id="9ff32-128">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="9ff32-129">Этот параметр задает максимальное количество подписей, которое может храниться в кэше.</span><span class="sxs-lookup"><span data-stu-id="9ff32-129">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="9ff32-130">Если количество сообщений, отправленных в пределах последнего окна воспроизведения, достигает предела кэша, новые сообщения отклоняются, пока не будет достигнут предел по времени для самых старых подписей в кэше.</span><span class="sxs-lookup"><span data-stu-id="9ff32-130">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="9ff32-131">Значение по умолчанию — 500000.</span><span class="sxs-lookup"><span data-stu-id="9ff32-131">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="9ff32-132">Управление обнаружением воспроизведения на стороне службы с помощью кода</span><span class="sxs-lookup"><span data-stu-id="9ff32-132">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="9ff32-133">Создайте элемент <xref:System.ServiceModel.Channels.SecurityBindingElement> для использования в привязке <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="9ff32-133">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="9ff32-134">С помощью свойства <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> получите ссылку на класс <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> и задайте свойства, как указано выше.</span><span class="sxs-lookup"><span data-stu-id="9ff32-134">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="9ff32-135">Управление обнаружением воспроизведения с помощью конфигурации для клиента или службы</span><span class="sxs-lookup"><span data-stu-id="9ff32-135">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="9ff32-136">Создайте [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="9ff32-136">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="9ff32-137">Создайте элемент `<security>`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-137">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="9ff32-138">Создайте [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) или [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="9ff32-138">Create a [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="9ff32-139">Задайте следующие значение атрибутов (согласно необходимости): `detectReplays`, `maxClockSkew`, `replayWindow` и `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-139">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="9ff32-140">В следующем примере задаются атрибуты для обоих элементов: `<localServiceSettings>`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-140">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings
          replayCacheSize="800000"
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings
          replayCacheSize="800000"
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="9ff32-141">Пример</span><span class="sxs-lookup"><span data-stu-id="9ff32-141">Example</span></span>  

 <span data-ttu-id="9ff32-142">В следующем примере создается элемент <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> с помощью метода <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> и задает свойства воспроизведения привязки.</span><span class="sxs-lookup"><span data-stu-id="9ff32-142">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="9ff32-143">Область воспроизведения: только для режима безопасности сообщений</span><span class="sxs-lookup"><span data-stu-id="9ff32-143">Scope of Replay: Message Security Only</span></span>  

 <span data-ttu-id="9ff32-144">Обратите внимание, что следующие процедуры применяются только для режима безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="9ff32-144">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="9ff32-145">В режиме транспорта и в режиме транспорта с учетными данными сообщения воспроизведение обнаруживает транспортный механизм.</span><span class="sxs-lookup"><span data-stu-id="9ff32-145">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="9ff32-146">Примечания о безопасном диалоге</span><span class="sxs-lookup"><span data-stu-id="9ff32-146">Secure Conversation Notes</span></span>  

 <span data-ttu-id="9ff32-147">Для привязок, обеспечивающих безопасные диалоги, можно изменить эти настройки и для канала приложения, и для привязки начальной загрузки безопасного диалога.</span><span class="sxs-lookup"><span data-stu-id="9ff32-147">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="9ff32-148">Например, можно отключить воспроизведение для канала приложения, но разрешить его для канала начальной загрузки, устанавливающего безопасный диалог.</span><span class="sxs-lookup"><span data-stu-id="9ff32-148">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="9ff32-149">Если сеансы безопасных диалогов не используются, средства обнаружения воспроизведения не гарантируют обнаружение воспроизведения в случаях использования фермы серверов и перезапуска процесса.</span><span class="sxs-lookup"><span data-stu-id="9ff32-149">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="9ff32-150">Это относится к следующим привязкам, предоставляемым системой:</span><span class="sxs-lookup"><span data-stu-id="9ff32-150">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="9ff32-151"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="9ff32-151"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="9ff32-152">Привязка <xref:System.ServiceModel.WSHttpBinding>, в которой свойство <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> имеет значение `false`.</span><span class="sxs-lookup"><span data-stu-id="9ff32-152"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ff32-153">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="9ff32-153">Compiling the Code</span></span>  
  
- <span data-ttu-id="9ff32-154">Для компиляции кода требуются следующие пространства имен.</span><span class="sxs-lookup"><span data-stu-id="9ff32-154">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="9ff32-155">См. также</span><span class="sxs-lookup"><span data-stu-id="9ff32-155">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="9ff32-156">Безопасные диалоги и безопасные сеансы</span><span class="sxs-lookup"><span data-stu-id="9ff32-156">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="9ff32-157">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9ff32-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
