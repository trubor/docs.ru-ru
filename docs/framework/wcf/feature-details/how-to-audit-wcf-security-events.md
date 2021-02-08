---
description: Дополнительные сведения см. в статье аудит Windows Communication Foundation событий безопасности.
title: Практическое руководство. Аудит событий безопасности Windows Communication Foundation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: b9cd258f51dbc726108fef0bbf173c7ee26c1d0f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780210"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="f6b62-103">Практическое руководство. Аудит событий безопасности Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f6b62-103">How to: Audit Windows Communication Foundation Security Events</span></span>

<span data-ttu-id="f6b62-104">Windows Communication Foundation (WCF) позволяет регистрировать события безопасности в журнале событий Windows, который можно просмотреть с помощью Просмотр событий Windows.</span><span class="sxs-lookup"><span data-stu-id="f6b62-104">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="f6b62-105">В этом разделе описано, как настроить приложение, чтобы события безопасности регистрировались в журнале.</span><span class="sxs-lookup"><span data-stu-id="f6b62-105">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="f6b62-106">Дополнительные сведения об аудите WCF см. в разделе [Audit](auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="f6b62-106">For more information about WCF auditing, see [Auditing](auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="f6b62-107">Аудит событий безопасности в коде</span><span class="sxs-lookup"><span data-stu-id="f6b62-107">To audit security events in code</span></span>  
  
1. <span data-ttu-id="f6b62-108">Укажите расположение журнала аудита.</span><span class="sxs-lookup"><span data-stu-id="f6b62-108">Specify the audit log location.</span></span> <span data-ttu-id="f6b62-109">Для этого присвойте свойству <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> класса <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> одно из значений перечисления <xref:System.ServiceModel.AuditLogLocation>, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="f6b62-109">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="f6b62-110"><xref:System.ServiceModel.AuditLogLocation>Перечисление имеет три значения: `Application` , `Security` или `Default` .</span><span class="sxs-lookup"><span data-stu-id="f6b62-110">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="f6b62-111">Эти значения определяют один журналов, доступных в средстве "Просмотр событий" - журнал безопасности или журнал приложения.</span><span class="sxs-lookup"><span data-stu-id="f6b62-111">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="f6b62-112">Если установлено значение `Default`, выбор журнала будет зависеть от параметров операционной системы, в которой выполняется приложение.</span><span class="sxs-lookup"><span data-stu-id="f6b62-112">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="f6b62-113">Если аудит включен, а расположение журнала аудита не задано, по умолчанию для платформ, поддерживающих ведение журнала безопасности, используется значение `Security`; в противном случае используется значение `Application`.</span><span class="sxs-lookup"><span data-stu-id="f6b62-113">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="f6b62-114">Только Windows Server 2003 и Windows Vista поддерживают запись в журнал безопасности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f6b62-114">Only Windows Server 2003 and Windows Vista support writing to the Security log by default.</span></span>  
  
2. <span data-ttu-id="f6b62-115">Настройте типы событий для аудита.</span><span class="sxs-lookup"><span data-stu-id="f6b62-115">Set up the types of events to audit.</span></span> <span data-ttu-id="f6b62-116">Возможен одновременный аудит событий уровня службы и событий авторизации уровня сообщений.</span><span class="sxs-lookup"><span data-stu-id="f6b62-116">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="f6b62-117">Для этого присвойте свойству <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> или свойству <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> одно из значений перечисления <xref:System.ServiceModel.AuditLevel>, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="f6b62-117">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. <span data-ttu-id="f6b62-118">Укажите, нужно ли подавлять сбои приложения, связанные с событиями аудита.</span><span class="sxs-lookup"><span data-stu-id="f6b62-118">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="f6b62-119">Задайте для свойства <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> значение `true` или `false`, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="f6b62-119">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="f6b62-120">По умолчанию свойство `SuppressAuditFailure` имеет значение `true`, т. е. сбои аудита не отражаются на приложении.</span><span class="sxs-lookup"><span data-stu-id="f6b62-120">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="f6b62-121">В противном случае создается исключение.</span><span class="sxs-lookup"><span data-stu-id="f6b62-121">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="f6b62-122">В случае успешного аудита записывается подробная трассировка.</span><span class="sxs-lookup"><span data-stu-id="f6b62-122">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="f6b62-123">В случае неудачного аудита трассировка записывается на уровне ошибки.</span><span class="sxs-lookup"><span data-stu-id="f6b62-123">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4. <span data-ttu-id="f6b62-124">Удалите существующий объект <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> из коллекции поведений в описании <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="f6b62-124">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="f6b62-125">Коллекция поведений доступна по свойству <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>, которое в свою очередь доступно по свойству <xref:System.ServiceModel.ServiceHostBase.Description%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6b62-125">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="f6b62-126">После этого добавьте новое поведение <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> в ту же коллекцию, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="f6b62-126">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="f6b62-127">Настройка аудита в файле конфигурации</span><span class="sxs-lookup"><span data-stu-id="f6b62-127">To set up auditing in configuration</span></span>  
  
1. <span data-ttu-id="f6b62-128">Чтобы настроить аудит в конфигурации, добавьте [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) элемент в [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) раздел файла web.config.</span><span class="sxs-lookup"><span data-stu-id="f6b62-128">To set up auditing in configuration, add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="f6b62-129">Затем добавьте [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) элемент и задайте различные атрибуты, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="f6b62-129">Then add a [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <behavior name="myAuditBehavior">  
          <serviceSecurityAudit auditLogLocation="Application"  
                suppressAuditFailure="false"
                serviceAuthorizationAuditLevel="None"
                messageAuthenticationAuditLevel="SuccessOrFailure" />  
          </behavior>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="f6b62-130">Необходимо задать поведение службы, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="f6b62-130">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
    ```xml  
    <services>  
        <service type="WCS.Samples.Service.Echo"
        behaviorConfiguration=" myAuditBehavior">  
           <endpoint address=""  
                    binding="wsHttpBinding"  
                    bindingConfiguration="CertificateDefault"
                    contract="WCS.Samples.Service.IEcho" />  
        </service>  
    </services>  
    ```  
  
## <a name="example"></a><span data-ttu-id="f6b62-131">Пример</span><span class="sxs-lookup"><span data-stu-id="f6b62-131">Example</span></span>  

 <span data-ttu-id="f6b62-132">В следующем примере кода показано, как создать экземпляр класса <xref:System.ServiceModel.ServiceHost> и добавить новый <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> в его коллекцию поведений.</span><span class="sxs-lookup"><span data-stu-id="f6b62-132">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="f6b62-133">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f6b62-133">.NET Framework Security</span></span>  

 <span data-ttu-id="f6b62-134">Если для свойства <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> задать значение `true`, все неудачные попытки создания аудита безопасности будут подавляться (если задано значение `false`, будет создаваться исключение).</span><span class="sxs-lookup"><span data-stu-id="f6b62-134">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="f6b62-135">Однако если включить следующее свойство **локального параметра безопасности** Windows, ошибка создания событий аудита приведет к немедленному завершению работы Windows:</span><span class="sxs-lookup"><span data-stu-id="f6b62-135">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="f6b62-136">**Аудит: немедленное отключение системы, если невозможно внести в журнал записи об аудите безопасности.**</span><span class="sxs-lookup"><span data-stu-id="f6b62-136">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="f6b62-137">Чтобы задать свойство, откройте диалоговое окно **локальные параметры безопасности** .</span><span class="sxs-lookup"><span data-stu-id="f6b62-137">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="f6b62-138">В разделе **Параметры безопасности** щелкните **Локальные политики**.</span><span class="sxs-lookup"><span data-stu-id="f6b62-138">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="f6b62-139">Затем щелкните **Параметры безопасности**.</span><span class="sxs-lookup"><span data-stu-id="f6b62-139">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="f6b62-140">Если <xref:System.ServiceModel.AuditLogLocation> свойство имеет значение <xref:System.ServiceModel.AuditLogLocation.Security> и **Аудит доступа к объектам** не задан в **локальной политике безопасности**, события аудита не будут записываться в журнал безопасности.</span><span class="sxs-lookup"><span data-stu-id="f6b62-140">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="f6b62-141">Обратите внимание, что ошибка не возвращается, а события аудита не регистрируются в журнале безопасности.</span><span class="sxs-lookup"><span data-stu-id="f6b62-141">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b62-142">См. также</span><span class="sxs-lookup"><span data-stu-id="f6b62-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="f6b62-143">Аудит</span><span class="sxs-lookup"><span data-stu-id="f6b62-143">Auditing</span></span>](auditing-security-events.md)
