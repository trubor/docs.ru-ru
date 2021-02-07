---
description: 'Дополнительные сведения: Windows Communication Foundation сведения о конфиденциальности'
title: Сведения о политике конфиденциальности Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 4f942e84a072d15a12b6db7cc2c310d629a59f6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726693"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="c8086-103">Сведения о политике конфиденциальности Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c8086-103">Windows Communication Foundation Privacy Information</span></span>

<span data-ttu-id="c8086-104">Корпорация Майкрософт стремится защищать конфиденциальность конечных пользователей.</span><span class="sxs-lookup"><span data-stu-id="c8086-104">Microsoft is committed to protecting end user privacy.</span></span> <span data-ttu-id="c8086-105">При создании приложения с помощью Windows Communication Foundation (WCF) версии 3,0 приложение может повлиять на конфиденциальность конечных пользователей.</span><span class="sxs-lookup"><span data-stu-id="c8086-105">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end users' privacy.</span></span> <span data-ttu-id="c8086-106">Например, приложение может явным образом собирать контактные данные пользователей или запрашивать/отправлять информацию через Интернет на свой веб-сайт.</span><span class="sxs-lookup"><span data-stu-id="c8086-106">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="c8086-107">Если в приложение внедряется технология Майкрософт, у этой технологии может быть свое поведение, которое способно повлиять на конфиденциальность данных приложения.</span><span class="sxs-lookup"><span data-stu-id="c8086-107">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="c8086-108">WCF не отправляет сведения в корпорацию Майкрософт из вашего приложения, если вы или пользователь не решили отправить его нам.</span><span class="sxs-lookup"><span data-stu-id="c8086-108">WCF does not send any information to Microsoft from your application unless you or the end user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="c8086-109">Вкратце о WCF</span><span class="sxs-lookup"><span data-stu-id="c8086-109">WCF in Brief</span></span>  

 <span data-ttu-id="c8086-110">WCF — это распределенная платформа обмена сообщениями, использующая платформу Microsoft .NET, которая позволяет разработчикам создавать распределенные приложения.</span><span class="sxs-lookup"><span data-stu-id="c8086-110">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="c8086-111">Сообщения, обмен которыми осуществляется между двумя приложениями, содержат информацию заголовка и тела сообщения.</span><span class="sxs-lookup"><span data-stu-id="c8086-111">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="c8086-112">Заголовки могут содержать информацию о маршрутизации сообщений, безопасности, транзакциях, а также другие сведения в зависимости от служб, используемых приложением.</span><span class="sxs-lookup"><span data-stu-id="c8086-112">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="c8086-113">Как правило, по умолчанию выполняется шифрование сообщений.</span><span class="sxs-lookup"><span data-stu-id="c8086-113">Messages are typically encrypted by default.</span></span> <span data-ttu-id="c8086-114">Единственным исключением является использование привязки `BasicHttpBinding`, которая была создана для использования с небезопасными веб-службами прежних версий.</span><span class="sxs-lookup"><span data-stu-id="c8086-114">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="c8086-115">Разработчик приложения отвечает за окончательную версию приложения.</span><span class="sxs-lookup"><span data-stu-id="c8086-115">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="c8086-116">Сообщения в тексте SOAP содержат данные конкретного приложения; Однако такие данные, как определенные приложением персональные данные, могут быть защищены с помощью функций шифрования и конфиденциальности WCF.</span><span class="sxs-lookup"><span data-stu-id="c8086-116">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="c8086-117">В следующих разделах описаны возможности, которые теоретически могут повлиять на конфиденциальность.</span><span class="sxs-lookup"><span data-stu-id="c8086-117">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="c8086-118">Обмен сообщениями</span><span class="sxs-lookup"><span data-stu-id="c8086-118">Messaging</span></span>  

 <span data-ttu-id="c8086-119">Каждое сообщение WCF имеет заголовок адреса, указывающий назначение сообщения и место, где должен быть отправлен ответ.</span><span class="sxs-lookup"><span data-stu-id="c8086-119">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="c8086-120">Компонент адреса конечной точки является универсальным кодом ресурса (URI), определяющим конечную точку.</span><span class="sxs-lookup"><span data-stu-id="c8086-120">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="c8086-121">Адрес может быть сетевым или логическим.</span><span class="sxs-lookup"><span data-stu-id="c8086-121">The address can be a network address or a logical address.</span></span> <span data-ttu-id="c8086-122">Адрес может содержать имя компьютера (имя узла, полное доменное имя) и IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="c8086-122">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="c8086-123">Адрес конечной точки также может содержать глобальный уникальный идентификатор (GUID) или коллекцию таких идентификаторов для временной адресации, используемой для распознавания каждого адреса.</span><span class="sxs-lookup"><span data-stu-id="c8086-123">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="c8086-124">Каждое сообщение содержит идентификатор сообщения, который является глобальным уникальным идентификатором.</span><span class="sxs-lookup"><span data-stu-id="c8086-124">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="c8086-125">Эта возможность соответствует стандарту ссылок WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="c8086-125">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="c8086-126">Уровень обмена сообщениями WCF не записывает персональные данные на локальный компьютер.</span><span class="sxs-lookup"><span data-stu-id="c8086-126">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="c8086-127">Однако возможно их распространение на уровне сети, если разработчик создал службу, раскрывающую такую информацию (например за счет указания имени пользователя в имени конечной точки или включения персональных данных в язык описания веб-служб конечной точки, но не требуя при этом от клиентов использования HTTPS для доступа к WSDL).</span><span class="sxs-lookup"><span data-stu-id="c8086-127">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="c8086-128">Кроме того, если разработчик запускает средство [служебной программы метаданных ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) для конечной точки, предоставляющей персональные данные, выходные данные этого средства могут содержать эти сведения, а выходной файл записывается на локальный жесткий диск.</span><span class="sxs-lookup"><span data-stu-id="c8086-128">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="c8086-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="c8086-129">Hosting</span></span>  

 <span data-ttu-id="c8086-130">Функция размещения в WCF позволяет запускать приложения по требованию или включать совместное использование портов несколькими приложениями.</span><span class="sxs-lookup"><span data-stu-id="c8086-130">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="c8086-131">Приложение WCF может размещаться в службы IIS (IIS) аналогично ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c8086-131">A WCF application can be hosted in Internet Information Services (IIS), similar to ASP.NET.</span></span>  
  
 <span data-ttu-id="c8086-132">При размещении не раскрывается какая-либо особая информация в сети, и данные не сохраняются на компьютере.</span><span class="sxs-lookup"><span data-stu-id="c8086-132">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="c8086-133">Безопасность сообщений</span><span class="sxs-lookup"><span data-stu-id="c8086-133">Message Security</span></span>  

 <span data-ttu-id="c8086-134">Безопасность WCF предоставляет возможности безопасности для приложений обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="c8086-134">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="c8086-135">Предусмотренные функции безопасности включают в себя проверку подлинности и авторизацию.</span><span class="sxs-lookup"><span data-stu-id="c8086-135">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="c8086-136">Проверка подлинности осуществляется путем передачи учетных данных между клиентами и службами.</span><span class="sxs-lookup"><span data-stu-id="c8086-136">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="c8086-137">Проверка подлинности может выполняться либо через безопасность на транспортном уровне, либо через безопасность на уровне сообщений SOAP следующим образом.</span><span class="sxs-lookup"><span data-stu-id="c8086-137">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
- <span data-ttu-id="c8086-138">При безопасности на уровне сообщений SOAP проверка подлинности осуществляется с помощью учетных данных, например имен пользователей/паролей, сертификатов X.509, билетов Kerberos и маркеров SAML, каждый из которых может содержать персональные данные в зависимости от издателя.</span><span class="sxs-lookup"><span data-stu-id="c8086-138">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
- <span data-ttu-id="c8086-139">С помощью безопасности транспорта проверка подлинности осуществляется посредством таких обычных механизмов проверки подлинности транспорта, как схемы проверки подлинности HTTP (обычная, дайджест, Negotiate, Integrated Windows Authorization, NTLM, без проверки и анонимная) и проверка подлинности на основе формы.</span><span class="sxs-lookup"><span data-stu-id="c8086-139">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="c8086-140">Результатом проверки подлинности может стать безопасный сеанс, осуществляемый между взаимодействующими конечными точками.</span><span class="sxs-lookup"><span data-stu-id="c8086-140">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="c8086-141">Сеанс определяется идентификатором GUID, который существует на протяжении всего времени существования сеанса безопасности.</span><span class="sxs-lookup"><span data-stu-id="c8086-141">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="c8086-142">В следующей таблице указано, что и где хранится.</span><span class="sxs-lookup"><span data-stu-id="c8086-142">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="c8086-143">Данные</span><span class="sxs-lookup"><span data-stu-id="c8086-143">Data</span></span>|<span data-ttu-id="c8086-144">Память</span><span class="sxs-lookup"><span data-stu-id="c8086-144">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="c8086-145">Учетные данные представления, например имена пользователей, сертификаты X.509, маркеры Kerberos и ссылки на учетные данные.</span><span class="sxs-lookup"><span data-stu-id="c8086-145">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="c8086-146">Стандартные механизмы управления учетными данными в Windows, например хранилище сертификатов Windows.</span><span class="sxs-lookup"><span data-stu-id="c8086-146">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="c8086-147">Информация о членстве пользователя, например имена пользователей и пароли.</span><span class="sxs-lookup"><span data-stu-id="c8086-147">User membership information, such as usernames and passwords.</span></span>|<span data-ttu-id="c8086-148">Поставщики членства ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c8086-148">ASP.NET membership providers.</span></span>|  
|<span data-ttu-id="c8086-149">Данные идентификации о службе, используемой для проверки подлинности службы для клиентов.</span><span class="sxs-lookup"><span data-stu-id="c8086-149">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="c8086-150">Адрес конечной точки службы.</span><span class="sxs-lookup"><span data-stu-id="c8086-150">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="c8086-151">Сведения о вызывающем объекте.</span><span class="sxs-lookup"><span data-stu-id="c8086-151">Caller information.</span></span>|<span data-ttu-id="c8086-152">Журналы аудита.</span><span class="sxs-lookup"><span data-stu-id="c8086-152">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="c8086-153">Аудит</span><span class="sxs-lookup"><span data-stu-id="c8086-153">Auditing</span></span>  

 <span data-ttu-id="c8086-154">Во время аудита регистрируются события успешной и неудачной проверки подлинности и авторизации.</span><span class="sxs-lookup"><span data-stu-id="c8086-154">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="c8086-155">В журналах аудита содержатся следующие данные: URI службы, URI действия и идентификация вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="c8086-155">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="c8086-156">Во время аудита также регистрируется событие, когда администратор изменяет конфигурацию ведения журнала сообщений (включает или выключает), поскольку при ведении журнала сообщений данные, относящиеся к приложению, могут указываться в заголовках и телах.</span><span class="sxs-lookup"><span data-stu-id="c8086-156">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="c8086-157">В Windows XP запись записывается в журнал событий приложений.</span><span class="sxs-lookup"><span data-stu-id="c8086-157">For Windows XP, a record is logged in the application event log.</span></span> <span data-ttu-id="c8086-158">В Windows Vista и Windows Server 2003 запись записывается в журнал событий безопасности.</span><span class="sxs-lookup"><span data-stu-id="c8086-158">For Windows Vista and Windows Server 2003, a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="c8086-159">Transactions</span><span class="sxs-lookup"><span data-stu-id="c8086-159">Transactions</span></span>  

 <span data-ttu-id="c8086-160">Функция Transactions предоставляет службы транзакций для приложения WCF.</span><span class="sxs-lookup"><span data-stu-id="c8086-160">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="c8086-161">Заголовки транзакций, используемые при распространении транзакций, могут содержать идентификаторы транзакций или идентификаторы зачисления, которые являются идентификаторами GUID.</span><span class="sxs-lookup"><span data-stu-id="c8086-161">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="c8086-162">Возможность транзакций использует диспетчер транзакций координатора распределенных транзакций (Майкрософт) (компонент Windows) для управления состоянием транзакций.</span><span class="sxs-lookup"><span data-stu-id="c8086-162">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="c8086-163">По умолчанию взаимодействие между диспетчерами транзакций шифруется.</span><span class="sxs-lookup"><span data-stu-id="c8086-163">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="c8086-164">Диспетчеры транзакций могут вносить в журнал ссылки на конечные точки, идентификаторы транзакций и идентификаторы зачисления как часть их устойчивого состояния.</span><span class="sxs-lookup"><span data-stu-id="c8086-164">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="c8086-165">Время существования этого состояния определяется временем существования файла журнала диспетчера транзакций.</span><span class="sxs-lookup"><span data-stu-id="c8086-165">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="c8086-166">Этот журнал используется и обслуживается службой MSDTC.</span><span class="sxs-lookup"><span data-stu-id="c8086-166">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="c8086-167">Возможность транзакций реализует стандарты транзакций WS-Coordination и WS-Atomic.</span><span class="sxs-lookup"><span data-stu-id="c8086-167">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="c8086-168">Надежные сеансы</span><span class="sxs-lookup"><span data-stu-id="c8086-168">Reliable Sessions</span></span>  

 <span data-ttu-id="c8086-169">Надежные сеансы в WCF обеспечивают передачу сообщений при возникновении транспортных или промежуточных сбоев.</span><span class="sxs-lookup"><span data-stu-id="c8086-169">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="c8086-170">Они обеспечивают точную передачу сообщений даже при отключении базового транспорта (например подключение TCP в беспроводной сети) или потере сообщения (удаление прокси-сервером HTTP исходящего или входящего сообщения).</span><span class="sxs-lookup"><span data-stu-id="c8086-170">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="c8086-171">Надежные сеансы также восстанавливают измененный порядок передачи сообщений (что может произойти в случае многопутевой маршрутизации), сохраняя порядок, в котором были отправлены сообщения.</span><span class="sxs-lookup"><span data-stu-id="c8086-171">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="c8086-172">Надежные сеансы реализованы с использованием протокола WS-ReliableMessaging (WS-RM).</span><span class="sxs-lookup"><span data-stu-id="c8086-172">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="c8086-173">Они добавляют заголовки WS-RM, содержащие информацию о сеансе, которая используется для определения всех сообщений, связанных с определенным надежным сеансом.</span><span class="sxs-lookup"><span data-stu-id="c8086-173">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="c8086-174">У каждого сеанса WS-RM имеется идентификатор, являющийся идентификатором GUID.</span><span class="sxs-lookup"><span data-stu-id="c8086-174">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="c8086-175">Персональные данные не сосохранены на компьютере конечного пользователя.</span><span class="sxs-lookup"><span data-stu-id="c8086-175">No personal information is retained on the end user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="c8086-176">Очередь в каналах</span><span class="sxs-lookup"><span data-stu-id="c8086-176">Queued Channels</span></span>  

 <span data-ttu-id="c8086-177">В очередях хранятся сообщения отправляющего приложения от имени получающего приложения и позднее перенаправляющие эти сообщения получающему приложению.</span><span class="sxs-lookup"><span data-stu-id="c8086-177">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="c8086-178">Они обеспечивают передачу сообщений из отправляющих в получающие приложения, когда, например, получающее приложение служит посредником.</span><span class="sxs-lookup"><span data-stu-id="c8086-178">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="c8086-179">WCF обеспечивает поддержку очереди с помощью службы очередей сообщений Майкрософт (MSMQ) в качестве транспорта.</span><span class="sxs-lookup"><span data-stu-id="c8086-179">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="c8086-180">Функция очереди в каналах не добавляет заголовки в сообщение.</span><span class="sxs-lookup"><span data-stu-id="c8086-180">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="c8086-181">Вместо этого она создает сообщение очереди сообщений с соответствующим набором свойств этого сообщения и вызывает методы очереди сообщений, чтобы разместить сообщение в очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="c8086-181">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="c8086-182">Очередь сообщений является необязательным компонентом в поставляемой ОС Windows.</span><span class="sxs-lookup"><span data-stu-id="c8086-182">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="c8086-183">На компьютере конечного пользователя не будет храниться никаких сведений, так как она использует очередь сообщений в качестве инфраструктуры очереди.</span><span class="sxs-lookup"><span data-stu-id="c8086-183">No information is retained on the end user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="c8086-184">Интеграция с COM+</span><span class="sxs-lookup"><span data-stu-id="c8086-184">COM+ Integration</span></span>  

 <span data-ttu-id="c8086-185">Эта функция заключает существующие функциональные возможности COM и COM+ для создания служб, совместимых со службами WCF.</span><span class="sxs-lookup"><span data-stu-id="c8086-185">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="c8086-186">Эта функция не использует определенные заголовки и не удерживает данные на компьютере конечного пользователя.</span><span class="sxs-lookup"><span data-stu-id="c8086-186">This feature does not use specific headers and it does not retain data on the end user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="c8086-187">Моникер служб COM</span><span class="sxs-lookup"><span data-stu-id="c8086-187">COM Service Moniker</span></span>  

 <span data-ttu-id="c8086-188">Это обеспечивает неуправляемую оболочку для стандартного клиента WCF.</span><span class="sxs-lookup"><span data-stu-id="c8086-188">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="c8086-189">В этой возможности по сети не передаются специальные заголовки, и она не хранит данные на компьютере.</span><span class="sxs-lookup"><span data-stu-id="c8086-189">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="c8086-190">Одноранговый канал</span><span class="sxs-lookup"><span data-stu-id="c8086-190">Peer Channel</span></span>  

 <span data-ttu-id="c8086-191">Одноранговый канал позволяет разрабатывать многокомпонентные приложения с помощью WCF.</span><span class="sxs-lookup"><span data-stu-id="c8086-191">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="c8086-192">Многопользовательский обмен сообщениями возникает в контексте сетки.</span><span class="sxs-lookup"><span data-stu-id="c8086-192">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="c8086-193">Сетки определяются именем, с которым узел может соединиться.</span><span class="sxs-lookup"><span data-stu-id="c8086-193">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="c8086-194">Каждый узел в одноранговом канале создает прослушиватель TCP на указанном пользователем порту и устанавливает подключения к другим узлам в сетке, чтобы обеспечить устойчивую работу.</span><span class="sxs-lookup"><span data-stu-id="c8086-194">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="c8086-195">Чтобы подключиться к другим узлам в сетке, узлы также обмениваются некоторыми данными, включая адрес прослушивателя и IP-адреса компьютера, с другими узлами в сетке.</span><span class="sxs-lookup"><span data-stu-id="c8086-195">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="c8086-196">Сообщения, отправляемые по сетке, могут содержать сведения о безопасности, принадлежащие отправителю, с целью предотвращения спуфинга и подделки сообщений.</span><span class="sxs-lookup"><span data-stu-id="c8086-196">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="c8086-197">Личные данные не хранятся на компьютере конечного пользователя.</span><span class="sxs-lookup"><span data-stu-id="c8086-197">No personal information is stored on the end user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="c8086-198">Опыт работы ИТ-специалистов</span><span class="sxs-lookup"><span data-stu-id="c8086-198">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="c8086-199">Трассировка</span><span class="sxs-lookup"><span data-stu-id="c8086-199">Tracing</span></span>  

 <span data-ttu-id="c8086-200">Функция диагностики инфраструктуры WCF регистрирует сообщения, которые проходят через уровни модели транспорта и службы, а также действия и события, связанные с этими сообщениями.</span><span class="sxs-lookup"><span data-stu-id="c8086-200">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="c8086-201">Эта функция отключена по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c8086-201">This feature is turned off by default.</span></span> <span data-ttu-id="c8086-202">Он включается с помощью файла конфигурации приложения, и поведение трассировки может быть изменено с помощью поставщика WCF WMI во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="c8086-202">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="c8086-203">Во включенном состоянии инфраструктура трассировки выдает настроенным прослушивателям диагностическую трассировку, содержащую сообщения, действия и события обработки.</span><span class="sxs-lookup"><span data-stu-id="c8086-203">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="c8086-204">Формат и расположение выходных данных определяются выбранной администратором конфигурацией прослушивателя, однако, как правило, это файл в формате XML.</span><span class="sxs-lookup"><span data-stu-id="c8086-204">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="c8086-205">Администратор отвечает за настройку списка управления доступом (ACL) для файлов трассировки.</span><span class="sxs-lookup"><span data-stu-id="c8086-205">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="c8086-206">В частности, в случае размещения в системе Windows Activation System (WAS) администратор должен убедиться, что файлы не предоставляются с общедоступного виртуального корневого каталога, за исключением, если это сделано намеренно.</span><span class="sxs-lookup"><span data-stu-id="c8086-206">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="c8086-207">Существует два типа трассировки: ведение журналов сообщений и диагностическая трассировка модели служб, описание см. в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="c8086-207">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="c8086-208">Каждый тип настраивается через собственный источник трассировки: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> и <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="c8086-208">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="c8086-209">Оба этих источника трассировки для ведения журналов собирают данные, являющиеся локальными для приложения.</span><span class="sxs-lookup"><span data-stu-id="c8086-209">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="c8086-210">Ведение журналов сообщений</span><span class="sxs-lookup"><span data-stu-id="c8086-210">Message Logging</span></span>  

 <span data-ttu-id="c8086-211">Источник трассировки для ведения журнала сообщений (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) позволяет администратору вносить в журнал передаваемые в системе сообщения.</span><span class="sxs-lookup"><span data-stu-id="c8086-211">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="c8086-212">С помощью конфигурации пользователь может выбрать, следует ли вносить в журнал сообщения целиком или только их заголовки, либо вносить их в журнал на транспортном уровне или уровне модели службы, либо включать неправильно сформированные сообщения.</span><span class="sxs-lookup"><span data-stu-id="c8086-212">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="c8086-213">Кроме того, пользователь может настроить фильтрацию, чтобы ограничить внесение сообщений в журнал определенными типами.</span><span class="sxs-lookup"><span data-stu-id="c8086-213">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="c8086-214">По умолчанию ведение журнала сообщений отключено.</span><span class="sxs-lookup"><span data-stu-id="c8086-214">By default, message logging is disabled.</span></span> <span data-ttu-id="c8086-215">Администратор локального компьютера может запретить администратору на уровне приложения включение ведения журнала сообщений.</span><span class="sxs-lookup"><span data-stu-id="c8086-215">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="c8086-216">Ведение журнала зашифрованных и расшифрованных сообщений</span><span class="sxs-lookup"><span data-stu-id="c8086-216">Encrypted and Decrypted Message Logging</span></span>  

 <span data-ttu-id="c8086-217">Зашифрованные или расшифрованные сообщения вносятся в журнал в соответствии со следующими условиями.</span><span class="sxs-lookup"><span data-stu-id="c8086-217">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="c8086-218">Ведение журнала транспорта</span><span class="sxs-lookup"><span data-stu-id="c8086-218">Transport Logging</span></span>  
 <span data-ttu-id="c8086-219">Внесение в журнал сообщений, получаемых и отправляемых на транспортном уровне.</span><span class="sxs-lookup"><span data-stu-id="c8086-219">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="c8086-220">Эти сообщения содержат все заголовки и могут быть зашифрованы перед отправкой по сети и во время получения.</span><span class="sxs-lookup"><span data-stu-id="c8086-220">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="c8086-221">Если сообщения зашифрованы перед отправкой по сети и во время получения, они вносятся в журнал как зашифрованные.</span><span class="sxs-lookup"><span data-stu-id="c8086-221">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="c8086-222">Исключением является использование протокола безопасности (HTTPS): в этом случае они вносятся в журнал расшифрованными перед отправкой и после получения, даже если они зашифровываются в сети.</span><span class="sxs-lookup"><span data-stu-id="c8086-222">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="c8086-223">Ведение журнала служб</span><span class="sxs-lookup"><span data-stu-id="c8086-223">Service Logging</span></span>  
 <span data-ttu-id="c8086-224">Внесение в журнал сообщений, полученных или отправленных на уровне модели служб, после обработки заголовка канала, непосредственно перед и после ввода пользовательского кода.</span><span class="sxs-lookup"><span data-stu-id="c8086-224">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="c8086-225">Сообщения, внесенные в журнал на этом уровне, расшифровываются, даже если они были защищены и зашифрованы в сети.</span><span class="sxs-lookup"><span data-stu-id="c8086-225">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="c8086-226">Ведение журнала неправильно сформированных сообщений</span><span class="sxs-lookup"><span data-stu-id="c8086-226">Malformed Message Logging</span></span>  
 <span data-ttu-id="c8086-227">Записывает в журнал сообщения, которые инфраструктура WCF не может распознать или обработать.</span><span class="sxs-lookup"><span data-stu-id="c8086-227">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="c8086-228">Сообщения вносятся в журнал «как есть», т.е. либо зашифрованными, либо расшифрованными.</span><span class="sxs-lookup"><span data-stu-id="c8086-228">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="c8086-229">Когда сообщения регистрируются в расшифрованной или незашифрованной форме, по умолчанию WCF удаляет ключи безопасности и потенциально персональные данные из сообщений перед их регистрацией.</span><span class="sxs-lookup"><span data-stu-id="c8086-229">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="c8086-230">В следующих разделах представлено описание, какая информация удаляется и когда.</span><span class="sxs-lookup"><span data-stu-id="c8086-230">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="c8086-231">Администратор компьютера и специалист, выполняющий развертывание приложения, должны предпринять ряд действий в отношении конфигурации, чтобы изменить поведение по умолчанию, связанное с внесением в журнал ключей и потенциально персональных данных.</span><span class="sxs-lookup"><span data-stu-id="c8086-231">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="c8086-232">Информация, удаленная из заголовков сообщений при внесении в журнал зашифрованных/незашифрованных сообщений</span><span class="sxs-lookup"><span data-stu-id="c8086-232">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  

 <span data-ttu-id="c8086-233">Когда сообщения вносятся в журнал в зашифрованной или незашифрованной форме, ключи безопасности и потенциально персональные данные по умолчанию удаляются из заголовков и тел сообщений перед тем, как они будут внесены в журнал.</span><span class="sxs-lookup"><span data-stu-id="c8086-233">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="c8086-234">В следующем списке показано, что WCF учитывает ключи и потенциально персональные данные.</span><span class="sxs-lookup"><span data-stu-id="c8086-234">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="c8086-235">Удаляемые ключи:</span><span class="sxs-lookup"><span data-stu-id="c8086-235">Keys that are removed:</span></span>  
  
 <span data-ttu-id="c8086-236">\- Для xmlns: WST = " http://schemas.xmlsoap.org/ws/2004/04/trust " и xmlns: WST = " http://schemas.xmlsoap.org/ws/2005/02/trust "</span><span class="sxs-lookup"><span data-stu-id="c8086-236">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="c8086-237">wst:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="c8086-237">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="c8086-238">wst:Entropy</span><span class="sxs-lookup"><span data-stu-id="c8086-238">wst:Entropy</span></span>  
  
 <span data-ttu-id="c8086-239">\- Для xmlns: wsse = " http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd " и xmlns: wsse = " http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd "</span><span class="sxs-lookup"><span data-stu-id="c8086-239">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="c8086-240">wsse:Password</span><span class="sxs-lookup"><span data-stu-id="c8086-240">wsse:Password</span></span>  
  
 <span data-ttu-id="c8086-241">wsse:Nonce</span><span class="sxs-lookup"><span data-stu-id="c8086-241">wsse:Nonce</span></span>  
  
 <span data-ttu-id="c8086-242">Удаляемые потенциально персональные данные:</span><span class="sxs-lookup"><span data-stu-id="c8086-242">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="c8086-243">\- Для xmlns: wsse = " http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd " и xmlns: wsse = " http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd "</span><span class="sxs-lookup"><span data-stu-id="c8086-243">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="c8086-244">wsse:Username</span><span class="sxs-lookup"><span data-stu-id="c8086-244">wsse:Username</span></span>  
  
 <span data-ttu-id="c8086-245">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="c8086-245">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="c8086-246">\- Для xmlns: SAML = "urn: Oasis: Names: TC: SAML: 1.0: assertion" элементы, выделенные жирным шрифтом (ниже), удаляются:</span><span class="sxs-lookup"><span data-stu-id="c8086-246">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="c8086-247">\<Утверждение</span><span class="sxs-lookup"><span data-stu-id="c8086-247">\<Assertion</span></span>  
  
 <span data-ttu-id="c8086-248">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="c8086-248">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="c8086-249">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="c8086-249">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="c8086-250">AssertionId="[ID]"</span><span class="sxs-lookup"><span data-stu-id="c8086-250">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="c8086-251">Issuer="[string]"</span><span class="sxs-lookup"><span data-stu-id="c8086-251">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="c8086-252">IssueInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="c8086-252">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 \<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]">  
  
 \<AudienceRestrictionCondition>  
  
 <span data-ttu-id="c8086-253">\<Audience>URI\</Audience>+</span><span class="sxs-lookup"><span data-stu-id="c8086-253">\<Audience>[uri]\</Audience>+</span></span>  
  
 \</AudienceRestrictionCondition>*  
  
 \<DoNotCacheCondition />*  
  
 <span data-ttu-id="c8086-254"><\!--Абстрактный базовый тип</span><span class="sxs-lookup"><span data-stu-id="c8086-254"><\!-- abstract base type</span></span>  
  
 \<Condition />*  
  
 -->  
  
 <span data-ttu-id="c8086-255">\</Conditions>?</span><span class="sxs-lookup"><span data-stu-id="c8086-255">\</Conditions>?</span></span>  
  
 \<Advice>  
  
 <span data-ttu-id="c8086-256">\<AssertionIDReference>УДОСТОВЕРЕНИЯ\</AssertionIDReference>\*</span><span class="sxs-lookup"><span data-stu-id="c8086-256">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="c8086-257">\<Assertion>утверждение\</Assertion>\*</span><span class="sxs-lookup"><span data-stu-id="c8086-257">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="c8086-258">[any]\*</span><span class="sxs-lookup"><span data-stu-id="c8086-258">[any]\*</span></span>  
  
 <span data-ttu-id="c8086-259">\</Advice>?</span><span class="sxs-lookup"><span data-stu-id="c8086-259">\</Advice>?</span></span>  
  
 <span data-ttu-id="c8086-260"><\!--Абстрактные базовые типы</span><span class="sxs-lookup"><span data-stu-id="c8086-260"><\!-- Abstract base types</span></span>  
  
 \<Statement />*  
  
 \<SubjectStatement>  
  
 \<Subject>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 \<SubjectConfirmation>  
  
 <span data-ttu-id="c8086-261">\<ConfirmationMethod>AnyUri\</ConfirmationMethod>+</span><span class="sxs-lookup"><span data-stu-id="c8086-261">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="c8086-262">\<SubjectConfirmationData>[Any] \</SubjectConfirmationData> ?</span><span class="sxs-lookup"><span data-stu-id="c8086-262">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="c8086-263">\<ds:KeyInfo>...\</ds:KeyInfo>?</span><span class="sxs-lookup"><span data-stu-id="c8086-263">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="c8086-264">\</SubjectConfirmation>?</span><span class="sxs-lookup"><span data-stu-id="c8086-264">\</SubjectConfirmation>?</span></span>  
  
 \</Subject>  
  
 \</SubjectStatement>*  
  
 -->  
  
 <span data-ttu-id="c8086-265">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="c8086-265">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="c8086-266">AuthenticationMethod="[uri]"</span><span class="sxs-lookup"><span data-stu-id="c8086-266">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="c8086-267">AuthenticationInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="c8086-267">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="c8086-268">[Subject]</span><span class="sxs-lookup"><span data-stu-id="c8086-268">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="c8086-269"><AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="c8086-269"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="c8086-270">AuthorityKind="[QName]"</span><span class="sxs-lookup"><span data-stu-id="c8086-270">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="c8086-271">Location="[uri]"</span><span class="sxs-lookup"><span data-stu-id="c8086-271">Location="[uri]"</span></span>  
  
 <span data-ttu-id="c8086-272">Binding="[uri]"</span><span class="sxs-lookup"><span data-stu-id="c8086-272">Binding="[uri]"</span></span>  
  
 />*  
  
 \</AuthenticationStatement>*  
  
 \<AttributeStatement>  
  
 <span data-ttu-id="c8086-273">[Subject]</span><span class="sxs-lookup"><span data-stu-id="c8086-273">[Subject]</span></span>  
  
 <span data-ttu-id="c8086-274">\<attribute</span><span class="sxs-lookup"><span data-stu-id="c8086-274">\<Attribute</span></span>  
  
 <span data-ttu-id="c8086-275">AttributeName="[string]"</span><span class="sxs-lookup"><span data-stu-id="c8086-275">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="c8086-276">AttributeNamespace="[uri]"</span><span class="sxs-lookup"><span data-stu-id="c8086-276">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</Attribute>+  
  
 \</AttributeStatement>*  
  
 <span data-ttu-id="c8086-277">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="c8086-277">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="c8086-278">Resource="[uri]"</span><span class="sxs-lookup"><span data-stu-id="c8086-278">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="c8086-279">Решение = "[разрешить&#124;запретить&#124;неопределенного]"</span><span class="sxs-lookup"><span data-stu-id="c8086-279">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="c8086-280">[Subject]</span><span class="sxs-lookup"><span data-stu-id="c8086-280">[Subject]</span></span>  
  
 <span data-ttu-id="c8086-281">\<Action Namespace="[uri]">Строка\</Action>+</span><span class="sxs-lookup"><span data-stu-id="c8086-281">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 \<Evidence>  
  
 <span data-ttu-id="c8086-282">\<AssertionIDReference>УДОСТОВЕРЕНИЯ\</AssertionIDReference>+</span><span class="sxs-lookup"><span data-stu-id="c8086-282">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="c8086-283">\<Assertion>утверждение\</Assertion>+</span><span class="sxs-lookup"><span data-stu-id="c8086-283">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="c8086-284">\</Evidence>?</span><span class="sxs-lookup"><span data-stu-id="c8086-284">\</Evidence>?</span></span>  
  
 \</AuthorizationDecisionStatement>*  
  
 \</Assertion>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="c8086-285">Информация, удаленная из тел сообщений при внесении в журнал зашифрованных/незашифрованных сообщений</span><span class="sxs-lookup"><span data-stu-id="c8086-285">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  

 <span data-ttu-id="c8086-286">Как было сказано выше, WCF удаляет ключи и известные потенциально персональные данные из заголовков сообщений для зарегистрированных расшифрованных и незашифрованных сообщений.</span><span class="sxs-lookup"><span data-stu-id="c8086-286">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="c8086-287">Кроме того, WCF удаляет ключи и известные потенциально персональные данные из тела сообщений для элементов текста и действий в следующем списке, описывающих сообщения безопасности, связанные с обменом ключами.</span><span class="sxs-lookup"><span data-stu-id="c8086-287">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="c8086-288">Для следующих пространств имен:</span><span class="sxs-lookup"><span data-stu-id="c8086-288">For the following namespaces:</span></span>  
  
 <span data-ttu-id="c8086-289">xmlns: WST = " http://schemas.xmlsoap.org/ws/2004/04/trust " и xmlns: WST = " http://schemas.xmlsoap.org/ws/2005/02/trust " (например, если действие не доступно)</span><span class="sxs-lookup"><span data-stu-id="c8086-289">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="c8086-290">Информация удаляется для элементов тел, участвующих в обмене ключами:</span><span class="sxs-lookup"><span data-stu-id="c8086-290">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="c8086-291">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="c8086-291">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="c8086-292">wst:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="c8086-292">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="c8086-293">wst:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="c8086-293">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="c8086-294">Информация также удаляется для каждого из следующих действий:</span><span class="sxs-lookup"><span data-stu-id="c8086-294">Information is also removed for each of the following Actions:</span></span>  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="c8086-295">Информация не удаляется из данных заголовков и тел, относящихся к приложению</span><span class="sxs-lookup"><span data-stu-id="c8086-295">No Information Is Removed from Application-specific Headers and Body Data</span></span>  

 <span data-ttu-id="c8086-296">WCF не следит за личными данными в заголовках приложений (например, строках запросов) или данных текста (например, номер кредитной карты).</span><span class="sxs-lookup"><span data-stu-id="c8086-296">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="c8086-297">Когда включено ведение журнала сообщений, персональные данные в информации заголовков и тел, относящихся к приложению, могут отображаться в журналах.</span><span class="sxs-lookup"><span data-stu-id="c8086-297">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="c8086-298">И вновь, специалист, выполняющий развертывание приложения, отвечает за настройку элементов управления доступом для файлов конфигурации и журналов.</span><span class="sxs-lookup"><span data-stu-id="c8086-298">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="c8086-299">Они также могут отключить ведение журнала, если эти сведения не должны отображаться, или отфильтровать эти сведения из файлов журнала после их регистрации.</span><span class="sxs-lookup"><span data-stu-id="c8086-299">They also can turn off logging if they don't want this information to be visible, or filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="c8086-300">Трассировка модели службы</span><span class="sxs-lookup"><span data-stu-id="c8086-300">Service Model Tracing</span></span>  

 <span data-ttu-id="c8086-301">Источник трассировки модели службы (<xref:System.ServiceModel>) обеспечивает трассировку действий и событий, относящихся к обработке сообщений.</span><span class="sxs-lookup"><span data-stu-id="c8086-301">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="c8086-302">Эта возможность использует диагностические возможности .NET Framework из <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="c8086-302">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="c8086-303">Аналогично свойству <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>, ее расположение и элемент управления доступом настраиваются пользователем с помощью файлов конфигурации приложения на базе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8086-303">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="c8086-304">Как и при ведении журнала сообщений, расположение файла всегда настраивается при включении администратором трассировки. Таким образом, администратор управляет элементом управления доступом.</span><span class="sxs-lookup"><span data-stu-id="c8086-304">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="c8086-305">Трассировки содержат заголовки сообщений, когда сообщения находятся в области действия.</span><span class="sxs-lookup"><span data-stu-id="c8086-305">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="c8086-306">Применяются аналогичные правила скрытия потенциально персональных данных в заголовках сообщений, описанные в предыдущем разделе: ранее определенные персональные данные по умолчанию удаляются из заголовков в трассировках.</span><span class="sxs-lookup"><span data-stu-id="c8086-306">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="c8086-307">Администратор компьютера и специалист, выполняющий развертывание приложения, должны изменить конфигурацию, чтобы вносить в журнал потенциально персональные сведения.</span><span class="sxs-lookup"><span data-stu-id="c8086-307">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="c8086-308">Однако персональные данные в заголовках, относящихся к приложению, вносятся в журнал в трассировках.</span><span class="sxs-lookup"><span data-stu-id="c8086-308">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="c8086-309">Специалист, выполняющий развертывание приложения, отвечает за настройку элементов управления доступом в файлах конфигурации и трассировки.</span><span class="sxs-lookup"><span data-stu-id="c8086-309">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="c8086-310">Они также могут отключить трассировку, чтобы скрыть эти сведения, или отфильтровать эти сведения из файлов трассировки после их записи в журнал.</span><span class="sxs-lookup"><span data-stu-id="c8086-310">They can also turn off tracing to hide this information or filter out this information from the trace files after it's logged.</span></span>  
  
 <span data-ttu-id="c8086-311">Являясь частью трассировки ServiceModel, уникальные идентификаторы (называемые идентификаторами действий или, как правило, глобальными уникальными идентификаторами) связывают различные действия друг с другом как поток сообщений, проходящий через разные области инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="c8086-311">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="c8086-312">Пользовательские прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="c8086-312">Custom Trace Listeners</span></span>  

 <span data-ttu-id="c8086-313">Для ведения журнала сообщений и трассировки можно настроить пользовательский прослушиватель трассировки, который может отправлять трассировки и сообщения по сети (например в удаленную базу данных).</span><span class="sxs-lookup"><span data-stu-id="c8086-313">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="c8086-314">Специалист, выполняющий развертывание приложения, отвечает за настройку пользовательских прослушивателей или разрешение пользователям самостоятельно ее настраивать.</span><span class="sxs-lookup"><span data-stu-id="c8086-314">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="c8086-315">Кроме того, они отвечают за любые персональные данные, предоставляемые в удаленном расположении, и для правильного применения списков ACL к этому расположению.</span><span class="sxs-lookup"><span data-stu-id="c8086-315">They are also responsible for any personal information exposed at the remote location and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="c8086-316">Другие функции для ИТ-специалистов</span><span class="sxs-lookup"><span data-stu-id="c8086-316">Other features for IT Professionals</span></span>  

 <span data-ttu-id="c8086-317">В WCF имеется поставщик WMI, который предоставляет сведения о конфигурации инфраструктуры WCF через инструментарий WMI (поставляется вместе с Windows).</span><span class="sxs-lookup"><span data-stu-id="c8086-317">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="c8086-318">По умолчанию интерфейс WMI доступен для администраторов.</span><span class="sxs-lookup"><span data-stu-id="c8086-318">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="c8086-319">В конфигурации WCF используется механизм настройки платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8086-319">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="c8086-320">Файлы конфигурации хранятся на компьютере.</span><span class="sxs-lookup"><span data-stu-id="c8086-320">The configuration files are stored on the machine.</span></span> <span data-ttu-id="c8086-321">Разработчик приложения и администратор создают файлы конфигурации и элемент правления доступом для каждого требования приложения.</span><span class="sxs-lookup"><span data-stu-id="c8086-321">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="c8086-322">Файл конфигурации может содержать адреса конечных точек и ссылки на сертификаты в хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="c8086-322">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="c8086-323">Сертификаты можно использовать, чтобы предоставить данные приложения для настройки различных свойств возможностей, используемых приложением.</span><span class="sxs-lookup"><span data-stu-id="c8086-323">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="c8086-324">WCF также использует функцию дампа процесса платформа .NET Framework, вызывая <xref:System.Environment.FailFast%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="c8086-324">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="c8086-325">Профессиональные ИТ-средства</span><span class="sxs-lookup"><span data-stu-id="c8086-325">IT Pro Tools</span></span>  

 <span data-ttu-id="c8086-326">WCF также предоставляет следующие средства для ИТ Professional, которые поставляются в Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="c8086-326">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="c8086-327">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="c8086-327">SvcTraceViewer.exe</span></span>  

 <span data-ttu-id="c8086-328">В средстве просмотра отображаются файлы трассировки WCF.</span><span class="sxs-lookup"><span data-stu-id="c8086-328">The viewer displays WCF trace files.</span></span> <span data-ttu-id="c8086-329">Средство просмотра позволяет просмотреть информацию, содержащуюся в трассировках.</span><span class="sxs-lookup"><span data-stu-id="c8086-329">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="c8086-330">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="c8086-330">SvcConfigEditor.exe</span></span>  

 <span data-ttu-id="c8086-331">Редактор позволяет пользователю создавать и изменять файлы конфигурации WCF.</span><span class="sxs-lookup"><span data-stu-id="c8086-331">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="c8086-332">Редактор показывает всю информацию, содержащуюся в файлах конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c8086-332">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="c8086-333">Аналогичную задачу можно выполнить с помощью текстового редактора.</span><span class="sxs-lookup"><span data-stu-id="c8086-333">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodel_reg"></a><span data-ttu-id="c8086-334">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="c8086-334">ServiceModel_Reg</span></span>  

 <span data-ttu-id="c8086-335">Это средство позволяет пользователю управлять установкой ServiceModel на компьютере.</span><span class="sxs-lookup"><span data-stu-id="c8086-335">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="c8086-336">Средство отображает сообщения о состоянии в окне консоли при запуске и в процессе может отображать сведения о конфигурации установки WCF.</span><span class="sxs-lookup"><span data-stu-id="c8086-336">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="c8086-337">WSATConfig.exe и WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="c8086-337">WSATConfig.exe and WSATUI.dll</span></span>  

 <span data-ttu-id="c8086-338">Эти средства позволяют ИТ-специалистам настраивать взаимодействующую WS-AtomicTransactionную поддержку сети в WCF.</span><span class="sxs-lookup"><span data-stu-id="c8086-338">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="c8086-339">Средство отображает и позволяет пользователю изменять значения наиболее часто используемых параметров WS-AtomicTransaction, хранящихся в реестре.</span><span class="sxs-lookup"><span data-stu-id="c8086-339">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="c8086-340">Перекрестные функции</span><span class="sxs-lookup"><span data-stu-id="c8086-340">Cross-cutting Features</span></span>  

 <span data-ttu-id="c8086-341">Следующие функции являются перекрестными.</span><span class="sxs-lookup"><span data-stu-id="c8086-341">The following features are cross-cutting.</span></span> <span data-ttu-id="c8086-342">Это означает, что их можно сочетать с любыми указанными выше функциями.</span><span class="sxs-lookup"><span data-stu-id="c8086-342">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="c8086-343">Инфраструктура службы</span><span class="sxs-lookup"><span data-stu-id="c8086-343">Service Framework</span></span>  

 <span data-ttu-id="c8086-344">Заголовки могут содержать идентификатор экземпляра, который представляет собой глобальный уникальный идентификатор, связывающий сообщение с экземпляром класса CLR.</span><span class="sxs-lookup"><span data-stu-id="c8086-344">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="c8086-345">Язык описания веб-служб (WSDL) содержит определение порта.</span><span class="sxs-lookup"><span data-stu-id="c8086-345">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="c8086-346">У каждого порта имеется адрес конечной точки и привязка, представляющая службы, используемые приложением.</span><span class="sxs-lookup"><span data-stu-id="c8086-346">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="c8086-347">Предоставление WSDL можно отключить в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c8086-347">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="c8086-348">Информация на компьютере не сохраняется.</span><span class="sxs-lookup"><span data-stu-id="c8086-348">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8086-349">См. также</span><span class="sxs-lookup"><span data-stu-id="c8086-349">See also</span></span>

- [<span data-ttu-id="c8086-350">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c8086-350">Windows Communication Foundation</span></span>](index.md)
- [<span data-ttu-id="c8086-351">Безопасность</span><span class="sxs-lookup"><span data-stu-id="c8086-351">Security</span></span>](./feature-details/security.md)
