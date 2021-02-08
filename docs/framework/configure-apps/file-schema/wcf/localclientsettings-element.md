---
description: 'Дополнительные сведения о: <localClientSettings> element'
title: <localClientSettings> - элемент
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: 6393a460b5a58ab9bf7933df8643df3530da5f14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802220"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="b8625-103">Элемент \<localClientSettings></span><span class="sxs-lookup"><span data-stu-id="b8625-103">\<localClientSettings> element</span></span>

<span data-ttu-id="b8625-104">Задает параметры безопасности локального клиента для этой привязки.</span><span class="sxs-lookup"><span data-stu-id="b8625-104">Specifies the security settings of a local client for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="b8625-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b8625-105">Syntax</span></span>  
  
```xml  
<security>
   <localClientSettings cacheCookies="Boolean"
                        cookieRenewalThresholdPercentage="Integer"
                        detectReplays="Boolean"
                        maxClockSkew="TimeSpan"
                        maxCookieCachingTime="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8625-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b8625-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b8625-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b8625-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8625-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b8625-108">Attributes</span></span>  
  
|<span data-ttu-id="b8625-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b8625-109">Attribute</span></span>|<span data-ttu-id="b8625-110">Описание</span><span class="sxs-lookup"><span data-stu-id="b8625-110">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="b8625-111">Логическое значение, указывающее, включено ли кэширование файлов cookie.</span><span class="sxs-lookup"><span data-stu-id="b8625-111">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="b8625-112">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="b8625-112">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="b8625-113">Целое число, задающее максимальный процент файлов cookie, которые могут обновляться.</span><span class="sxs-lookup"><span data-stu-id="b8625-113">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="b8625-114">Это значение должно быть в диапазоне от 0 до 100 включительно.</span><span class="sxs-lookup"><span data-stu-id="b8625-114">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="b8625-115">Значение по умолчанию — 90.</span><span class="sxs-lookup"><span data-stu-id="b8625-115">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="b8625-116">Логическое значение, показывающее, будут ли атаки с повторением обнаружены и ликвидированы на канале автоматически.</span><span class="sxs-lookup"><span data-stu-id="b8625-116">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="b8625-117">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="b8625-117">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="b8625-118">Значение типа <xref:System.TimeSpan>, указывающее максимальный разброс времени между системными часами взаимодействующих сторон.</span><span class="sxs-lookup"><span data-stu-id="b8625-118">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="b8625-119">Значение по умолчанию - 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="b8625-119">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="b8625-120">Если задано значение по умолчанию, получатель принимает сообщения с отметками времени отправки, которое на пять минут раньше или позже времени получения сообщения.</span><span class="sxs-lookup"><span data-stu-id="b8625-120">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="b8625-121">Сообщения, которые не прошли проверку времени отправки, отклоняются.</span><span class="sxs-lookup"><span data-stu-id="b8625-121">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="b8625-122">Данная настройка используется в сочетании с атрибутом `replayWindow`.</span><span class="sxs-lookup"><span data-stu-id="b8625-122">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="b8625-123">Значение <xref:System.TimeSpan>, которое задает максимальное время существования файлов cookie.</span><span class="sxs-lookup"><span data-stu-id="b8625-123">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="b8625-124">Значение по умолчанию - 10675199.02:48:05.4775807.</span><span class="sxs-lookup"><span data-stu-id="b8625-124">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="b8625-125">Логическое значение, указывающее, будет ли после транспортных сбоев выполняться попытка восстановления подключений, использующих режим обмена сообщениями WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="b8625-125">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="b8625-126">По умолчанию используется значение `true`, что означает бесконечное число попыток повторного подключения.</span><span class="sxs-lookup"><span data-stu-id="b8625-126">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="b8625-127">Цикл нарушается при возникновении тайм-аута бездействия, в результате чего канал вызывает исключение при невозможности повторного подключения.</span><span class="sxs-lookup"><span data-stu-id="b8625-127">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="b8625-128">Положительное целое число, указывающее количество кэшированных параметров nonce, используемых для определения ответов.</span><span class="sxs-lookup"><span data-stu-id="b8625-128">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="b8625-129">При превышении лимита самые старые параметры nonce удаляются, и создаются новые параметры nonce для новых сообщений.</span><span class="sxs-lookup"><span data-stu-id="b8625-129">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="b8625-130">Значение по умолчанию — 500000.</span><span class="sxs-lookup"><span data-stu-id="b8625-130">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="b8625-131">Значение типа <xref:System.TimeSpan>, которое указывает срок действия параметров nonce отдельного сообщения.</span><span class="sxs-lookup"><span data-stu-id="b8625-131">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="b8625-132">По истечении данного срока сообщение с тем же параметром nonce, что и у сообщения, отправленного ранее, приниматься не будет.</span><span class="sxs-lookup"><span data-stu-id="b8625-132">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="b8625-133">Данный атрибут используется вместе с атрибутом `maxClockSkew` в целях предотвращения атак с повторением передачи пакетов.</span><span class="sxs-lookup"><span data-stu-id="b8625-133">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="b8625-134">Злоумышленник может повторно отправить сообщение после закрытия окна повторной отправки сообщения.</span><span class="sxs-lookup"><span data-stu-id="b8625-134">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="b8625-135">Данное сообщение, тем не менее, не пройдет проверку `maxClockSkew`, в результате которой отклоняются сообщения с отметками времени отправки, превышающими указанный период до или после времени получения сообщения.</span><span class="sxs-lookup"><span data-stu-id="b8625-135">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="b8625-136">Значение <xref:System.TimeSpan>, которое задает интервал времени, по истечении которого инициатор будет обновлять ключ сеанса безопасности.</span><span class="sxs-lookup"><span data-stu-id="b8625-136">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="b8625-137">Значение по умолчанию - 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="b8625-137">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="b8625-138">Значение <xref:System.TimeSpan>, которое задает интервал времени, в течение которого предыдущий сеансовый ключ остается действительным для входящих сообщений, пока выполняется обновление ключа.</span><span class="sxs-lookup"><span data-stu-id="b8625-138">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="b8625-139">Значение по умолчанию - 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="b8625-139">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="b8625-140">Во время обновления ключа отправка сообщения клиентом и сервером всегда должна выполняться с помощью самого последнего доступного ключа.</span><span class="sxs-lookup"><span data-stu-id="b8625-140">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="b8625-141">Обе стороны принимают входящие сообщения, защищенные с помощью предыдущего сеансового ключа, вплоть до истечения времени смены ключа.</span><span class="sxs-lookup"><span data-stu-id="b8625-141">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="b8625-142">Положительное значение типа <xref:System.TimeSpan>, указывающее срок действия отметки времени.</span><span class="sxs-lookup"><span data-stu-id="b8625-142">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="b8625-143">Значение по умолчанию - 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="b8625-143">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8625-144">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b8625-144">Child Elements</span></span>  

 <span data-ttu-id="b8625-145">None</span><span class="sxs-lookup"><span data-stu-id="b8625-145">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8625-146">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b8625-146">Parent Elements</span></span>  
  
|<span data-ttu-id="b8625-147">Элемент</span><span class="sxs-lookup"><span data-stu-id="b8625-147">Element</span></span>|<span data-ttu-id="b8625-148">Описание</span><span class="sxs-lookup"><span data-stu-id="b8625-148">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="b8625-149">Задает параметры безопасности для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="b8625-149">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="b8625-150">Задает значения по умолчанию, используемые для инициализации службы безопасного обмена данными.</span><span class="sxs-lookup"><span data-stu-id="b8625-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8625-151">Remarks</span><span class="sxs-lookup"><span data-stu-id="b8625-151">Remarks</span></span>  

 <span data-ttu-id="b8625-152">Параметры являются локальными, в том смысле, что они не наследуются от политики безопасности службы.</span><span class="sxs-lookup"><span data-stu-id="b8625-152">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8625-153">См. также</span><span class="sxs-lookup"><span data-stu-id="b8625-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b8625-154">Привязки</span><span class="sxs-lookup"><span data-stu-id="b8625-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b8625-155">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="b8625-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b8625-156">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="b8625-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="b8625-157">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b8625-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="b8625-158">Безопасность пользовательской привязки</span><span class="sxs-lookup"><span data-stu-id="b8625-158">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
