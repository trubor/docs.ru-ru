---
description: 'Дополнительные сведения: протоколы транзакций'
title: Протоколы транзакций
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: a790e5d79128fb606d89cb6a3b6a925b3084d481
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752695"
---
# <a name="transaction-protocols"></a><span data-ttu-id="75577-103">Протоколы транзакций</span><span class="sxs-lookup"><span data-stu-id="75577-103">Transaction Protocols</span></span>

<span data-ttu-id="75577-104">Windows Communication Foundation (WCF) реализует WS-Atomic протоколы транзакций и WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="75577-104">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="75577-105">Спецификация/документ</span><span class="sxs-lookup"><span data-stu-id="75577-105">Specification/Document</span></span>|<span data-ttu-id="75577-106">Версия</span><span class="sxs-lookup"><span data-stu-id="75577-106">Version</span></span>|<span data-ttu-id="75577-107">Ссылка</span><span class="sxs-lookup"><span data-stu-id="75577-107">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="75577-108">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="75577-108">WS-Coordination</span></span>|<span data-ttu-id="75577-109">1.0</span><span class="sxs-lookup"><span data-stu-id="75577-109">1.0</span></span><br /><br /> <span data-ttu-id="75577-110">1,1</span><span class="sxs-lookup"><span data-stu-id="75577-110">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="75577-111">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="75577-111">WS-AtomicTransaction</span></span>|<span data-ttu-id="75577-112">1.0</span><span class="sxs-lookup"><span data-stu-id="75577-112">1.0</span></span><br /><br /> <span data-ttu-id="75577-113">1,1</span><span class="sxs-lookup"><span data-stu-id="75577-113">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
  
 <span data-ttu-id="75577-114">Согласно этим спецификациям протоколов, требуется взаимодействие на двух уровнях: между приложениями и между диспетчерами транзакций (см. следующий рисунок).</span><span class="sxs-lookup"><span data-stu-id="75577-114">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="75577-115">В спецификациях подробно описываются форматы сообщений и обмен сообщениями для обоих уровней взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="75577-115">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="75577-116">При обмене между приложениями применяются определенные средства обеспечения безопасности, надежности и методы кодирования, как и при обычном обмене в пределах сообщения.</span><span class="sxs-lookup"><span data-stu-id="75577-116">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="75577-117">Однако для успешного взаимодействия между диспетчерами транзакций требуется соглашение по конкретной привязке, поскольку она обычно не настраивается пользователем.</span><span class="sxs-lookup"><span data-stu-id="75577-117">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="75577-118">В этом разделе описываются состав спецификации протокола WS-Atomic Transaction (WS-AT) со средствами безопасности, а также безопасная привязка, используемая для обмена данными между диспетчерами транзакций.</span><span class="sxs-lookup"><span data-stu-id="75577-118">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="75577-119">Подход, описанный в этом документе, успешно протестирован с другими реализациями протоколов WS-AT и WS-Coordination, включая IBM, IONA, Sun Microsystems и пр.</span><span class="sxs-lookup"><span data-stu-id="75577-119">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="75577-120">На следующем рисунке показано взаимодействие между двумя диспетчерами транзакций, диспетчером транзакций 1 и диспетчером транзакций 2, а также двумя приложениями, приложением 1 и приложением 2.</span><span class="sxs-lookup"><span data-stu-id="75577-120">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Снимок экрана, показывающий взаимодействие между диспетчерами транзакций.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="75577-122">Рассмотрим типовой сценарий WS-Coordination/WS-Atomic Transaction с одним инициатором (I) и одним участником (P).</span><span class="sxs-lookup"><span data-stu-id="75577-122">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="75577-123">И инициатор, и участник имеют диспетчеры транзакций (ITM и PTM, соответственно).</span><span class="sxs-lookup"><span data-stu-id="75577-123">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="75577-124">Двухфазная фиксация обозначается в этом разделе как 2PC.</span><span class="sxs-lookup"><span data-stu-id="75577-124">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="75577-125">1. Креатекурдинатионконтекст</span><span class="sxs-lookup"><span data-stu-id="75577-125">1. CreateCoordinationContext</span></span>|<span data-ttu-id="75577-126">12. ответ на сообщение приложения</span><span class="sxs-lookup"><span data-stu-id="75577-126">12. Application Message Response</span></span>|  
|<span data-ttu-id="75577-127">2. Креатекурдинатионконтекстреспонсе</span><span class="sxs-lookup"><span data-stu-id="75577-127">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="75577-128">13. Фиксация (завершение)</span><span class="sxs-lookup"><span data-stu-id="75577-128">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="75577-129">3. Регистрация (завершение)</span><span class="sxs-lookup"><span data-stu-id="75577-129">3. Register (Completion)</span></span>|<span data-ttu-id="75577-130">14. подготовка (2PC)</span><span class="sxs-lookup"><span data-stu-id="75577-130">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="75577-131">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="75577-131">4. RegisterResponse</span></span>|<span data-ttu-id="75577-132">15. подготовка (2PC)</span><span class="sxs-lookup"><span data-stu-id="75577-132">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="75577-133">5. сообщение приложения</span><span class="sxs-lookup"><span data-stu-id="75577-133">5. Application Message</span></span>|<span data-ttu-id="75577-134">16. Prepared (2PC)</span><span class="sxs-lookup"><span data-stu-id="75577-134">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="75577-135">6. Креатекурдинатионконтекст с контекстом</span><span class="sxs-lookup"><span data-stu-id="75577-135">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="75577-136">17. подготовлено (2PC)</span><span class="sxs-lookup"><span data-stu-id="75577-136">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="75577-137">7. Регистрация (устойчивая)</span><span class="sxs-lookup"><span data-stu-id="75577-137">7. Register (Durable)</span></span>|<span data-ttu-id="75577-138">18. зафиксировано (завершение)</span><span class="sxs-lookup"><span data-stu-id="75577-138">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="75577-139">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="75577-139">8. RegisterResponse</span></span>|<span data-ttu-id="75577-140">19. Фиксация (2PC)</span><span class="sxs-lookup"><span data-stu-id="75577-140">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="75577-141">9. Креатекурдинатионконтекстреспонсе</span><span class="sxs-lookup"><span data-stu-id="75577-141">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="75577-142">20. Фиксация (2PC)</span><span class="sxs-lookup"><span data-stu-id="75577-142">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="75577-143">10. Регистрация (устойчивая)</span><span class="sxs-lookup"><span data-stu-id="75577-143">10. Register (Durable)</span></span>|<span data-ttu-id="75577-144">21. зафиксировано (2PC)</span><span class="sxs-lookup"><span data-stu-id="75577-144">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="75577-145">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="75577-145">11. RegisterResponse</span></span>|<span data-ttu-id="75577-146">22. зафиксировано (2PC)</span><span class="sxs-lookup"><span data-stu-id="75577-146">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="75577-147">В этом документе описываются состав спецификации протокола WS-AtomicTransaction со средствами безопасности, а также безопасная привязка, используемая для взаимодействия между диспетчерами транзакций.</span><span class="sxs-lookup"><span data-stu-id="75577-147">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="75577-148">Подход, описанный в этом документе, успешно протестирован с другими реализациями протоколов WS-AT и WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="75577-148">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="75577-149">На рисунке и в таблице представлены четыре класса сообщений с точки зрения безопасности:</span><span class="sxs-lookup"><span data-stu-id="75577-149">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="75577-150">сообщения активации (CreateCoordinationContext и CreateCoordinationContextResponse);</span><span class="sxs-lookup"><span data-stu-id="75577-150">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="75577-151">сообщения регистрации (Register и RegisterResponse);</span><span class="sxs-lookup"><span data-stu-id="75577-151">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="75577-152">протокольные сообщения (Prepare, Rollback, Commit, Aborted и т. д.);</span><span class="sxs-lookup"><span data-stu-id="75577-152">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="75577-153">сообщения приложений.</span><span class="sxs-lookup"><span data-stu-id="75577-153">Application messages.</span></span>  
  
 <span data-ttu-id="75577-154">Первые три класса сообщений считаются сообщениями диспетчера транзакций и их конфигурация привязки описывается в разделе "Обмен сообщениями приложений" ниже в данном разделе.</span><span class="sxs-lookup"><span data-stu-id="75577-154">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="75577-155">Четвертый класс сообщений - это сообщения, передаваемые между приложениями, которые описываются в разделе "Примеры сообщений" ниже в данном разделе.</span><span class="sxs-lookup"><span data-stu-id="75577-155">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="75577-156">В этом разделе описываются привязки протоколов, используемые для каждого из этих классов в WCF.</span><span class="sxs-lookup"><span data-stu-id="75577-156">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="75577-157">Во всем данном документе используются следующие пространства имен XML и связанные с ними префиксы.</span><span class="sxs-lookup"><span data-stu-id="75577-157">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="75577-158">Prefix</span><span class="sxs-lookup"><span data-stu-id="75577-158">Prefix</span></span>|<span data-ttu-id="75577-159">Версия</span><span class="sxs-lookup"><span data-stu-id="75577-159">Version</span></span>|<span data-ttu-id="75577-160">Универсальный код ресурса (URI) пространства имен</span><span class="sxs-lookup"><span data-stu-id="75577-160">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="75577-161">s11</span><span class="sxs-lookup"><span data-stu-id="75577-161">s11</span></span>||<https://schemas.xmlsoap.org/soap/envelope/>|  
|<span data-ttu-id="75577-162">wsa</span><span class="sxs-lookup"><span data-stu-id="75577-162">wsa</span></span>|<span data-ttu-id="75577-163">До 1.0</span><span class="sxs-lookup"><span data-stu-id="75577-163">Pre-1.0</span></span><br /><br /> <span data-ttu-id="75577-164">1.0</span><span class="sxs-lookup"><span data-stu-id="75577-164">1.0</span></span>|`http://www.w3.org/2004/08/addressing`<br /><br /> <https://www.w3.org/2005/08/addressing/>|  
|<span data-ttu-id="75577-165">wscoor</span><span class="sxs-lookup"><span data-stu-id="75577-165">wscoor</span></span>|<span data-ttu-id="75577-166">1.0</span><span class="sxs-lookup"><span data-stu-id="75577-166">1.0</span></span><br /><br /> <span data-ttu-id="75577-167">1,1</span><span class="sxs-lookup"><span data-stu-id="75577-167">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="75577-168">wsat</span><span class="sxs-lookup"><span data-stu-id="75577-168">wsat</span></span>|<span data-ttu-id="75577-169">1.0</span><span class="sxs-lookup"><span data-stu-id="75577-169">1.0</span></span><br /><br /> <span data-ttu-id="75577-170">1,1</span><span class="sxs-lookup"><span data-stu-id="75577-170">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
|<span data-ttu-id="75577-171">t</span><span class="sxs-lookup"><span data-stu-id="75577-171">t</span></span>|<span data-ttu-id="75577-172">До 1.3</span><span class="sxs-lookup"><span data-stu-id="75577-172">Pre-1.3</span></span><br /><br /> <span data-ttu-id="75577-173">1,3</span><span class="sxs-lookup"><span data-stu-id="75577-173">1.3</span></span>|<http://schemas.xmlsoap.org/ws/2005/02/trust/><br /><br /> <https://docs.oasis-open.org/ws-sx/ws-trust/200512>|  
|<span data-ttu-id="75577-174">o</span><span class="sxs-lookup"><span data-stu-id="75577-174">o</span></span>||<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd>|  
|<span data-ttu-id="75577-175">xsd</span><span class="sxs-lookup"><span data-stu-id="75577-175">xsd</span></span>||<https://www.w3.org/2001/XMLSchema>|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="75577-176">Привязки диспетчеров транзакций</span><span class="sxs-lookup"><span data-stu-id="75577-176">Transaction Manager Bindings</span></span>  

 <span data-ttu-id="75577-177">R1001: диспетчеры транзакций, участвующие в транзакции WS-AT 1,0, должны использовать SOAP 1,1 и WS-Addressing 2004/08 для WS-Atomic транзакций и WS-Coordination обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="75577-177">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="75577-178">R1002: для обмена сообщениями протоколов WS-Atomic Transaction и WS-Coordination диспетчеры транзакций, участвующие в транзакции по протоколу WS-AT 1.1, должны использовать SOAP 1.1 и WS-Addressing 2005/08.</span><span class="sxs-lookup"><span data-stu-id="75577-178">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="75577-179">Сообщения приложений не ограничиваются этими привязками и описываются ниже.</span><span class="sxs-lookup"><span data-stu-id="75577-179">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="75577-180">Привязка HTTPS диспетчера транзакций</span><span class="sxs-lookup"><span data-stu-id="75577-180">Transaction Manager HTTPS Binding</span></span>  

 <span data-ttu-id="75577-181">Для обеспечения безопасности и установления доверия между каждой парой "отправитель-получатель" в дереве транзакций привязка HTTPS диспетчера транзакций полагается только на механизм безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="75577-181">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="75577-182">Конфигурация транспорта HTTPS</span><span class="sxs-lookup"><span data-stu-id="75577-182">HTTPS Transport Configuration</span></span>  

 <span data-ttu-id="75577-183">Сертификаты X. 509 используются для установления удостоверения диспетчера транзакций.</span><span class="sxs-lookup"><span data-stu-id="75577-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="75577-184">Проверка подлинности клиента и сервера является обязательной, а авторизация клиента и сервера зависит от реализации:</span><span class="sxs-lookup"><span data-stu-id="75577-184">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="75577-185">R1111: сертификаты X.509, представляемые по линии связи, должны иметь имя субъекта, соответствующее полному доменному имени исходного компьютера;</span><span class="sxs-lookup"><span data-stu-id="75577-185">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="75577-186">B1112: для успешного выполнения проверок имени субъекта X.509 между каждой парой "отправитель-получатель" в системе должна работать служба DNS.</span><span class="sxs-lookup"><span data-stu-id="75577-186">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="75577-187">Конфигурация привязки активации и регистрации</span><span class="sxs-lookup"><span data-stu-id="75577-187">Activation and Registration Binding Configuration</span></span>  

 <span data-ttu-id="75577-188">Для WCF требуется дуплексная привязка запроса/ответа с корреляцией по протоколу HTTPS.</span><span class="sxs-lookup"><span data-stu-id="75577-188">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="75577-189">(Дополнительные сведения о корреляции и описание шаблонов обмена сообщениями "запрос-ответ" см. в разделе 8 спецификации WS-Atomic Transaction.)</span><span class="sxs-lookup"><span data-stu-id="75577-189">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="75577-190">Конфигурация привязки протокола 2PC</span><span class="sxs-lookup"><span data-stu-id="75577-190">2PC Protocol Binding Configuration</span></span>  

 <span data-ttu-id="75577-191">WCF поддерживает односторонние (датаграммы) сообщения по протоколу HTTPS.</span><span class="sxs-lookup"><span data-stu-id="75577-191">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="75577-192">Корреляция между сообщениями зависит от реализации.</span><span class="sxs-lookup"><span data-stu-id="75577-192">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="75577-193">B1131: реализации должны поддерживаться `wsa:ReferenceParameters` , как описано в WS-Addressing для достижения корреляции сообщений 2pc WCF.</span><span class="sxs-lookup"><span data-stu-id="75577-193">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="75577-194">Привязка безопасности диспетчера транзакций смешанного режима</span><span class="sxs-lookup"><span data-stu-id="75577-194">Transaction Manager Mixed Security Binding</span></span>  

 <span data-ttu-id="75577-195">Это альтернативная привязка (смешанного режима), которая для установления идентификации использует механизм безопасности транспорта в сочетании с моделью маркера, выдаваемого протоколом WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="75577-195">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="75577-196">В двух привязках отличаются только элементы "Активация" и "Регистрация".</span><span class="sxs-lookup"><span data-stu-id="75577-196">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="75577-197">Конфигурация транспорта HTTPS</span><span class="sxs-lookup"><span data-stu-id="75577-197">HTTPS Transport Configuration</span></span>  

 <span data-ttu-id="75577-198">Сертификаты X. 509 используются для установления удостоверения диспетчера транзакций.</span><span class="sxs-lookup"><span data-stu-id="75577-198">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="75577-199">Проверка подлинности клиента и сервера является обязательной, а авторизация клиента и сервера зависит от реализации.</span><span class="sxs-lookup"><span data-stu-id="75577-199">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="75577-200">Конфигурация привязки сообщений активации</span><span class="sxs-lookup"><span data-stu-id="75577-200">Activation Message Binding Configuration</span></span>  

 <span data-ttu-id="75577-201">Сообщения активации обычно не участвуют во взаимодействии, поскольку они, как правило, передаются между приложением и его локальным диспетчером транзакций.</span><span class="sxs-lookup"><span data-stu-id="75577-201">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="75577-202">B1221: в WCF используется дуплексная HTTPS-привязка (описанная в разделе [протоколы обмена сообщениями](messaging-protocols.md)) для сообщений активации.</span><span class="sxs-lookup"><span data-stu-id="75577-202">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="75577-203">Сообщения запроса и ответа коррелируются с использованием протокола WS-Addressing 2004/08 в случае WS-AT 1.0 и протокола WS-Addressing 2005/08 в случае WS-AT 1.1.</span><span class="sxs-lookup"><span data-stu-id="75577-203">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="75577-204">В разделе 8 спецификации WS-Atomic Transaction приводятся дополнительные сведения о корреляции и шаблонах обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="75577-204">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="75577-205">R1222: при получении сообщения `CreateCoordinationContext` координатор должен выдать маркер `SecurityContextToken` со связанным с ним паролем `STx`.</span><span class="sxs-lookup"><span data-stu-id="75577-205">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="75577-206">Этот маркер возвращается в заголовке `t:IssuedTokens` согласно спецификации WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="75577-206">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="75577-207">R1223: если активация происходит в пределах существующего контекста координации, в сообщении `t:IssuedTokens` должен передаваться заголовок `SecurityContextToken` с маркером `CreateCoordinationContext`, связанным с существующим контекстом.</span><span class="sxs-lookup"><span data-stu-id="75577-207">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="75577-208">`t:IssuedTokens`Для присоединения к исходящему сообщению должен быть создан новый заголовок `wscoor:CreateCoordinationContextResponse` .</span><span class="sxs-lookup"><span data-stu-id="75577-208">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="75577-209">Конфигурация привязки сообщений регистрации</span><span class="sxs-lookup"><span data-stu-id="75577-209">Registration Message Binding Configuration</span></span>  

 <span data-ttu-id="75577-210">B1231: в WCF используется дуплексная привязка HTTPS (описывается в разделе [протоколы обмена сообщениями](messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="75577-210">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](messaging-protocols.md)).</span></span> <span data-ttu-id="75577-211">Сообщения запроса и ответа коррелируются с использованием протокола WS-Addressing 2004/08 в случае WS-AT 1.0 и протокола WS-Addressing 2005/08 в случае WS-AT 1.1.</span><span class="sxs-lookup"><span data-stu-id="75577-211">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="75577-212">В разделе 8 спецификации WS-AtomicTransaction приводятся дополнительные сведения о корреляции и описание шаблонов обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="75577-212">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="75577-213">R1232: исходящие `wscoor:Register` сообщения должны использовать `IssuedTokenOverTransport` режим проверки подлинности, описанный в разделе [протоколы безопасности](security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="75577-213">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](security-protocols.md).</span></span>  
  
 <span data-ttu-id="75577-214">`wsse:Timestamp`Элемент должен быть подписан с помощью `SecurityContextToken STx` выданного.</span><span class="sxs-lookup"><span data-stu-id="75577-214">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="75577-215">Эта подпись является доказательством владения маркером, связанным с конкретной транзакцией, и используется для проверки подлинности зачисления участника в транзакцию.</span><span class="sxs-lookup"><span data-stu-id="75577-215">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="75577-216">Сообщение RegistrationResponse отправляется обратно по протоколу HTTPS.</span><span class="sxs-lookup"><span data-stu-id="75577-216">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="75577-217">Конфигурация привязки протокола 2PC</span><span class="sxs-lookup"><span data-stu-id="75577-217">2PC Protocol Binding Configuration</span></span>  

 <span data-ttu-id="75577-218">WCF поддерживает односторонние (датаграммы) сообщения по протоколу HTTPS.</span><span class="sxs-lookup"><span data-stu-id="75577-218">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="75577-219">Корреляция между сообщениями зависит от реализации.</span><span class="sxs-lookup"><span data-stu-id="75577-219">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="75577-220">B1241: реализации должны поддерживаться `wsa:ReferenceParameters` , как описано в WS-Addressing для достижения корреляции сообщений 2pc WCF.</span><span class="sxs-lookup"><span data-stu-id="75577-220">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="75577-221">Обмен сообщениями приложений</span><span class="sxs-lookup"><span data-stu-id="75577-221">Application Message Exchange</span></span>  

 <span data-ttu-id="75577-222">Для сообщений, передаваемых между приложениями, приложения могут использовать любую привязку, если она удовлетворяет следующим требованиям безопасности.</span><span class="sxs-lookup"><span data-stu-id="75577-222">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="75577-223">R2001: заголовок сообщений, передаваемых между приложениями, должен содержать заголовок `t:IssuedTokens` наряду с `CoordinationContext`.</span><span class="sxs-lookup"><span data-stu-id="75577-223">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="75577-224">R2002: необходимо обеспечение целостности и конфиденциальности `t:IssuedToken`.</span><span class="sxs-lookup"><span data-stu-id="75577-224">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="75577-225">Заголовок `CoordinationContext` содержит `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="75577-225">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="75577-226">Хотя определение `xsd:AnyURI` позволяет использовать как абсолютные, так и относительные URI, WCF поддерживает только `wscoor:Identifiers` абсолютные URI.</span><span class="sxs-lookup"><span data-stu-id="75577-226">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="75577-227">B2003: Если объект `wscoor:Identifier` `wscoor:CoordinationContext` является относительным URI, то ошибки будут возвращены из транзакционных служб WCF.</span><span class="sxs-lookup"><span data-stu-id="75577-227">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="75577-228">Примеры сообщений</span><span class="sxs-lookup"><span data-stu-id="75577-228">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="75577-229">Сообщения запроса и ответа CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="75577-229">CreateCoordinationContext Request/Response Messages</span></span>  

 <span data-ttu-id="75577-230">Следующие сообщения соответствуют шаблону "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="75577-230">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="75577-231">Креатекурдинатионконтекст с ВСКУР 1,0</span><span class="sxs-lookup"><span data-stu-id="75577-231">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="75577-232">CreateCoordinationContext по WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="75577-232">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>
<s:Header>  
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContext</Action>  
<a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
<a:ReplyTo>
<Address>https://...</a:Address>
</a:ReplyTo>
<a:To>https://...</a:To>
<wsse:Security>  
 <u:Timestamp>  
<wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
<wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
</u:Timestamp>
</wsse:Security>
</s:Header>
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
<wscoor:CreateCoordinationContext>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
</wscoor:CreateCoordinationContext>  
 </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="75577-233">CreateCoordinationContextResponse по Trust версии до 1.3 и WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="75577-233">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="75577-234">CreateCoordinationContextResponse по Trust 1.3 и WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="75577-234">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<!-- Data below is shown in the clear for illustration purposes only. -->
<s:Header>
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContextResponse </a:Action>  
<a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
<a:To s:mustUnderstand="1">https://... </a:To>
<t:IssuedTokens>
<wst:RequestSecurityTokenResponse
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512"  
xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
<wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
<wst:RequestedSecurityToken>
<wsc:SecurityContextToken>
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>
</wsc:SecurityContextToken>
</wst:RequestedSecurityToken>
<wsp:AppliesTo> http://fabrikam123.com/CCi </wsp:AppliesTo>  
<wst:RequestedAttachedReference>
<wsse:SecurityTokenReference >
<wsse:Reference  
  ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
  URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>
</wst:RequestedAttachedReference>
<wst:RequestedUnattachedReference>
<wsse:SecurityTokenReference>
<wsse:Reference  
 ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
 URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>
</wst:RequestedUnattachedReference>
<wst:RequestedProofToken>
<wst:BinarySecret  
  Type="http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey">  
  <!-- base64 encoded value -->
</wst:BinarySecret>
</wst:RequestedProofToken>
<wst:Lifetime>
<wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
<wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
</wst:Lifetime>
<wst:KeySize>256</wst:KeySize>
</wst:RequestSecurityTokenResponse>
</t:IssuedTokens>
<o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
<u:Timestamp u:Id="_0">
<u:Created>2005-12-15T23:36:12.015Z</u:Created>
<u:Expires>2005-12-15T23:41:12.015Z</u:Expires>
</u:Timestamp>
</o:Security>
</s:Header>
<s:Body>
<wscoor:CreateCoordinationContextResponse>
<wscoor:CoordinationContext>
<wscoor:Identifier> http://fabrikam123.com/CCi  
</wscoor:Identifier>
<wscoor:Expires>...</wscoor:Expires>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
<wscoor:RegistrationService>
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ...  
</a:ReferenceParameters>  
</wscoor:RegistrationService>
</wscoor:CoordinationContext>
</wscoor:CreateCoordinationContextResponse>
</s:Body>
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="75577-235">Сообщения регистрации</span><span class="sxs-lookup"><span data-stu-id="75577-235">Registration Messages</span></span>  

 <span data-ttu-id="75577-236">Следующие сообщения являются сообщениями регистрации.</span><span class="sxs-lookup"><span data-stu-id="75577-236">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="75577-237">Регистрация с помощью ВСКУР 1,0</span><span class="sxs-lookup"><span data-stu-id="75577-237">Register with WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="75577-238">Register по WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="75577-238">Register with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/Register</a:Action>
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
<a:ReplyTo>
<a:Address>https://...</a:Address>
</a:ReplyTo>  
<a:To>https://...</a:To>
<wsse:Security
s:mustUnderstand="1"
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wssu:Timestamp wssu:Id="_0" >
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>
<wsc:SecurityContextToken>
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>
</wsc:SecurityContextToken>
<!-- supporting signature over the timestamp -->  
<wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
<ds:SignedInfo>
<ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
<ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>
<ds:Reference URI="#_0">
<ds:Transforms>
<ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
</ds:Transforms>
<ds:DigestMethod  
Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
<ds:DigestValue> alRzyhjLgoUOYoh8cx4n75eTcUk=  
</ds:DigestValue>
</ds:Reference>
</ds:SignedInfo>  
<ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=  
</ds:SignatureValue>  
<ds:KeyInfo>
<wsse:SecurityTokenReference xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
  <wsse:Reference URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>
</ds:KeyInfo>
</wsse:Signature>
</wsse:Security>
</s:Header>
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
<wscoor:Register>
<wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
<wscoor:ParticipantProtocolService>
<a:Address>https://... </a:Address>  
</wscoor:ParticipantProtocolService>
</wscoor:Register>
</s:Body>
</s:Envelope>  
```  
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="75577-239">Регистрация ответа с помощью ВСКУР 1,0</span><span class="sxs-lookup"><span data-stu-id="75577-239">Register Response with WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="75577-240">RegisterResponse по WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="75577-240">Register Response with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>
<a:Action> http://docs.oasis-open.org/ws-tx/wscoor/2006/06/RegisterResponse  
</a:Action>
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
<a:RelatesTo> urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e </a:RelatesTo>  
<a:To>https://...</a:To>
<wsse:Security
s:mustUnderstand="1"
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
<wssu:Timestamp>
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>
</wsse:Security>
</s:Header>
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
<wscoor:RegisterResponse>
<wscoor:CoordinatorProtocolService>  
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ... </a:ReferenceParameters>  
</wscoor:CoordinatorProtocolService>
</wscoor:RegisterResponse>
</s:Body>
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="75577-241">Сообщения протокола двухфазной фиксации</span><span class="sxs-lookup"><span data-stu-id="75577-241">Two Phase Commit Protocol Messages</span></span>  

 <span data-ttu-id="75577-242">Следующее сообщение относится к протоколу двухфазной фиксации (2PC).</span><span class="sxs-lookup"><span data-stu-id="75577-242">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="75577-243">Фиксация с помощью WSAT 1,0</span><span class="sxs-lookup"><span data-stu-id="75577-243">Commit with WSAT 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="75577-244">Commit по WSAT 1.1</span><span class="sxs-lookup"><span data-stu-id="75577-244">Commit with WSAT 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>
<a:Action>http://docs.oasis-open.org/ws-tx/wsat/2006/06</a:Action>  
<a:To>https://...</a:To>
<wsse:Security
s:mustUnderstand="1"
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
<wssu:Timestamp wssu:Id="_0" >
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>
</wsse:Security>
</s:Header>
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
<wsat:Commit />
</s:Body>
</s:Envelope>  
```  
  
### <a name="application-messages"></a><span data-ttu-id="75577-245">Сообщения приложений</span><span class="sxs-lookup"><span data-stu-id="75577-245">Application Messages</span></span>  

 <span data-ttu-id="75577-246">Следующие сообщения являются сообщениями приложений.</span><span class="sxs-lookup"><span data-stu-id="75577-246">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="75577-247">Сообщение приложения - запрос</span><span class="sxs-lookup"><span data-stu-id="75577-247">Application message-Request</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken
          wssu:Id="IA_Certificate"
          ValueType="...#X509v3"
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader>  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader>
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->
    <e:EncryptedData Id="encrypted_body"
           Type="http://www.w3.org/2001/04/xmlenc#Content"
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
