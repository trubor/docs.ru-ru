---
description: Дополнительные сведения см. в статье поведение аудита служб.
title: Поведение аудита службы
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: 101f737d790d7e5ec0fdefc3a60695cb3c432c28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793133"
---
# <a name="service-auditing-behavior"></a><span data-ttu-id="e7bab-103">Поведение аудита службы</span><span class="sxs-lookup"><span data-stu-id="e7bab-103">Service Auditing Behavior</span></span>

<span data-ttu-id="e7bab-104">Этот образец демонстрирует, как использовать <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> для включения аудита событий безопасности во время выполнения операций службы.</span><span class="sxs-lookup"><span data-stu-id="e7bab-104">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span> <span data-ttu-id="e7bab-105">Этот образец основан на [Начало работы](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e7bab-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="e7bab-106">Служба и клиент были настроены с помощью [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e7bab-106">The service and client have been configured using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="e7bab-107">`mode`Атрибут [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) имеет значение `Message` и было `clientCredentialType` установлено в значение `Windows` .</span><span class="sxs-lookup"><span data-stu-id="e7bab-107">The `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="e7bab-108">В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="e7bab-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7bab-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="e7bab-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e7bab-110">В файле конфигурации службы для настройки аудита используется элемент `serviceSecurityAudit`.</span><span class="sxs-lookup"><span data-stu-id="e7bab-110">The service configuration file uses the `serviceSecurityAudit` element to configure auditing.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="e7bab-111">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="e7bab-111">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e7bab-112">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="e7bab-112">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="e7bab-113">Получающиеся журналы аудита можно просматривать в программе Просмотр событий.</span><span class="sxs-lookup"><span data-stu-id="e7bab-113">The resulting audit logs can be seen by running the Event Viewer.</span></span> <span data-ttu-id="e7bab-114">По умолчанию в Windows XP события аудита отображаются в журнале приложений, а в операционных системах Windows Server 2003 и Windows Vista события аудита можно просмотреть в журнале безопасности.</span><span class="sxs-lookup"><span data-stu-id="e7bab-114">By default, on Windows XP the audit events can be seen in the Application Log while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="e7bab-115">В Windows Server 2008 и Windows 7 события аудита можно увидеть в журналах приложений и служб.</span><span class="sxs-lookup"><span data-stu-id="e7bab-115">On Windows Server 2008 and Windows 7, the audit events can be seen in the Applications and Services logs.</span></span> <span data-ttu-id="e7bab-116">Расположение событий аудита можно задать, задав `auditLogLocation` для атрибута значение "Application" или "Security".</span><span class="sxs-lookup"><span data-stu-id="e7bab-116">The location of audit events can be specified by setting the `auditLogLocation` attribute to "Application" or "Security".</span></span> <span data-ttu-id="e7bab-117">Дополнительные сведения см. [в разделе инструкции. Аудит событий безопасности](../feature-details/how-to-audit-wcf-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="e7bab-117">For more information, see [How to: Audit Security Events](../feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="e7bab-118">Если события записываются в журнал безопасности, то Локалсекуритиполици-> включить доступ к объектам должен быть установлен для "Success" и "failure".</span><span class="sxs-lookup"><span data-stu-id="e7bab-118">If the events are written in the Security Log the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="e7bab-119">При просмотре журнала событий источником событий аудита является "ServiceModel Audit 3.0.0.0".</span><span class="sxs-lookup"><span data-stu-id="e7bab-119">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="e7bab-120">Записи аудита проверки подлинности сообщений имеют категорию "Мессажеаусентикатион", а записи аудита авторизации служб имеют категорию "ServiceAuthorization".</span><span class="sxs-lookup"><span data-stu-id="e7bab-120">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of "ServiceAuthorization".</span></span>  
  
 <span data-ttu-id="e7bab-121">События аудита проверки подлинности сообщений указывают, не было ли сообщение подделано, не истек ли срок его действия, а также может ли клиент пройти проверку подлинности при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="e7bab-121">Message authentication audit events cover whether the message was tampered with, whether the message has expired, and whether the client can authenticate to the service.</span></span> <span data-ttu-id="e7bab-122">Они предоставляют следующие сведения: результат проверки подлинности, идентификационные данные клиента и конечной точки, в которую было отправлено сообщение, а также действие, связанное с сообщением.</span><span class="sxs-lookup"><span data-stu-id="e7bab-122">They provide information about whether the authentication succeeded or failed along with the identity of the client, and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="e7bab-123">К событиям аудита авторизации службы относится решение об авторизации, принятое диспетчером авторизации служб.</span><span class="sxs-lookup"><span data-stu-id="e7bab-123">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="e7bab-124">Они содержат следующие сведения: результат авторизации, идентификационные данные клиента, конечная точка, в которую было направлено сообщение, действие, связанное с сообщением, идентификатор контекста авторизации, созданный на основании входящего сообщения, и тип диспетчера авторизации, принявшего решение о предоставлении доступа.</span><span class="sxs-lookup"><span data-stu-id="e7bab-124">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message, and the type of the authorization manager that made the access decision.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e7bab-125">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="e7bab-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e7bab-126">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e7bab-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e7bab-127">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e7bab-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e7bab-128">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e7bab-128">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7bab-129">См. также</span><span class="sxs-lookup"><span data-stu-id="e7bab-129">See also</span></span>

- [<span data-ttu-id="e7bab-130">Аудит</span><span class="sxs-lookup"><span data-stu-id="e7bab-130">Auditing</span></span>](../feature-details/auditing-security-events.md)
- [<span data-ttu-id="e7bab-131">Практическое руководство. Аудит событий безопасности</span><span class="sxs-lookup"><span data-stu-id="e7bab-131">How to: Audit Security Events</span></span>](../feature-details/how-to-audit-wcf-security-events.md)
