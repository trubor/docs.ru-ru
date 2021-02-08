---
description: 'Подробнее: Настройка службы совместного использования портов net. TCP'
title: Настройка службы совместного использования портов Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: 9e6a09c1dd986bc96a9d518d25226dd211b3e6ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780704"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="cc7e2-103">Настройка службы совместного использования портов Net.TCP</span><span class="sxs-lookup"><span data-stu-id="cc7e2-103">Configuring the Net.TCP Port Sharing Service</span></span>

<span data-ttu-id="cc7e2-104">Резидентные службы, использующие транспорт Net.TCP, могут управлять несколькими дополнительными параметрами, такими как `ListenBacklog` и `MaxPendingAccepts`, которые, в свою очередь, управляют поведением базового сокета TCP, используемого для сетевого взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-104">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="cc7e2-105">Однако эти параметры для каждого сокета применяются только на уровне привязки, если в привязке транспорта отключено совместное использование портов (по умолчанию совместное использование включено).</span><span class="sxs-lookup"><span data-stu-id="cc7e2-105">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="cc7e2-106">Если привязка net.tcp включает поддержку общего использования портов (задавая значение `portSharingEnabled =true` для элемента привязки транспорта), она неявно разрешает внешнему процессу (а именно SMSvcHost.exe, в котором размещается служба совместного использования портов Net.TCP) управлять сокетом TCP от своего имени.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-106">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="cc7e2-107">Например, при использовании протокола TCP необходимо задать следующее.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-107">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="cc7e2-108">Подобная настройка позволяет игнорировать любые параметры сокета, заданные в элементе привязки транспорта службы, и использовать параметры сокета, задаваемые SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-108">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="cc7e2-109">Для настройки SMSvcHost.exe необходимо создать файл конфигурации XML с именем SmSvcHost.exe.config и разместить его в том же физическом каталоге, что и исполняемый файл SMSvcHost.exe (например, C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="cc7e2-109">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="cc7e2-110">В следующем примере представлен образец файла SMSvcHost.exe.config с заданными явно параметрами по умолчанию для всех настраиваемых значений.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-110">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!-- 16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!-- 30 seconds -->  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->  
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->  
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
    </system.serviceModel.activation>
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="cc7e2-111">Определение необходимости изменения файла SMSvcHost.exe.config</span><span class="sxs-lookup"><span data-stu-id="cc7e2-111">When to Modify SMSvcHost.exe.config</span></span>  

 <span data-ttu-id="cc7e2-112">В целом, при изменении содержимого файла SMSvcHost.exe.config необходимо соблюдать осторожность, так как любые параметры конфигурации, заданные в этом файле, влияют на работу всех служб на компьютере с поддержкой службы совместного использования портов Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-112">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="cc7e2-113">Сюда входят приложения в Windows Vista, использующие функции активации TCP службы активации Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="cc7e2-113">This includes applications on Windows Vista that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="cc7e2-114">Однако иногда возникает необходимость в изменении конфигурации службы совместного использования портов Net.TCP по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-114">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="cc7e2-115">Например, значение по умолчанию для `maxPendingAccepts` равняется количеству процессоров, помноженному на 4.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-115">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="cc7e2-116">Требуется увеличить это значение для серверов, на которых размещено много служб, совместно использующих порты, чтобы обеспечить максимальную пропускную способность.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-116">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="cc7e2-117">Значение по умолчанию для `maxPendingConnections` равно 100.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-117">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="cc7e2-118">Также следует рассмотреть возможность увеличения этого значения, если наблюдаются потери клиентских подключений вследствие множества одновременных вызовов службы со стороны клиентов.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-118">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="cc7e2-119">Файл SMSvcHost.exe.config также содержит информацию об удостоверениях процессов, реализуемых с помощью службы совместного использования портов.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-119">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="cc7e2-120">При подключении процесса к службе совместного использования портов для работы с общим портом TCP удостоверение подключающегося процесса проверяется по списку удостоверений, которым разрешено работать со службой совместного использования портов.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-120">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="cc7e2-121">Эти удостоверения указываются в виде идентификаторов безопасности (SID) в \<allowAccounts> разделе файла SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-121">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="cc7e2-122">По умолчанию разрешение на работу со службой совместного использования портов предоставляется системным учетным записям (LocalService, LocalSystem и NetworkService), а также участникам группы "Администраторы".</span><span class="sxs-lookup"><span data-stu-id="cc7e2-122">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="cc7e2-123">Приложения, которые разрешают выполняемому под другим удостоверением (например, удостоверением пользователя) процессу подключаться к службе совместного использования портов, должны явно добавить в файл SMSvcHost.exe.config соответствующие SID (эти изменения не применяются до перезапуска процесса SMSvc.exe).</span><span class="sxs-lookup"><span data-stu-id="cc7e2-123">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc7e2-124">В системах Windows Vista с включенным контролем учетных записей (UAC) локальным пользователям требуются повышенные разрешения, даже если их учетная запись является членом группы администраторов.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-124">On Windows Vista systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="cc7e2-125">Чтобы разрешить этим пользователям использовать службу общего доступа к портам без повышения прав, в раздел SMSvcHost.exe.config необходимо явно добавить идентификатор безопасности пользователя (или идентификатор безопасности группы, в которую входит пользователь) \<allowAccounts> .</span><span class="sxs-lookup"><span data-stu-id="cc7e2-125">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="cc7e2-126">В файле SMSvcHost.exe.config по умолчанию задается пользовательское значение `etwProviderId`, чтобы трассировка SMSvcHost.exe не вмешивалась в работу трассировок служб.</span><span class="sxs-lookup"><span data-stu-id="cc7e2-126">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7e2-127">См. также</span><span class="sxs-lookup"><span data-stu-id="cc7e2-127">See also</span></span>

- [\<net.tcp>](../../configure-apps/file-schema/wcf/net-tcp.md)
