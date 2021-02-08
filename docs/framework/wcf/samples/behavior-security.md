---
description: 'Дополнительные сведения: безопасность поведения'
title: Безопасность поведений
ms.date: 03/30/2017
ms.assetid: 19710ae3-f197-4d28-ba9d-52e465006819
ms.openlocfilehash: ba245a2c9558d40f22b9126ee0cf1560ed700ce8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778715"
---
# <a name="behavior-security"></a><span data-ttu-id="8cf98-103">Безопасность поведений</span><span class="sxs-lookup"><span data-stu-id="8cf98-103">Behavior Security</span></span>

<span data-ttu-id="8cf98-104">В этом разделе приведены образцы, демонстрирующие настройку безопасности для поведения служб.</span><span class="sxs-lookup"><span data-stu-id="8cf98-104">This section includes samples that demonstrate configuring security for service behaviors.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8cf98-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="8cf98-105">In This Section</span></span>  

 [<span data-ttu-id="8cf98-106">Поведение аудита службы</span><span class="sxs-lookup"><span data-stu-id="8cf98-106">Service Auditing Behavior</span></span>](service-auditing-behavior.md)  
 <span data-ttu-id="8cf98-107">Этот образец демонстрирует, как использовать <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> для включения аудита событий безопасности во время выполнения операций службы.</span><span class="sxs-lookup"><span data-stu-id="8cf98-107">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span>  
  
 [<span data-ttu-id="8cf98-108">Поставщик членства и ролей</span><span class="sxs-lookup"><span data-stu-id="8cf98-108">Membership and Role Provider</span></span>](membership-and-role-provider.md)  
 <span data-ttu-id="8cf98-109">В этом примере показано, как служба может использовать поставщиков членства и ролей ASP.NET для проверки подлинности и авторизации клиентов.</span><span class="sxs-lookup"><span data-stu-id="8cf98-109">This sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 [<span data-ttu-id="8cf98-110">Авторизация доступа к операциям службы</span><span class="sxs-lookup"><span data-stu-id="8cf98-110">Authorizing Access to Service Operations</span></span>](authorizing-access-to-service-operations.md)  
 <span data-ttu-id="8cf98-111">В этом примере показано, как использовать [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) атрибут, чтобы разрешить использование <xref:System.Security.Permissions.PrincipalPermissionAttribute> атрибута для авторизации доступа к операциям службы.</span><span class="sxs-lookup"><span data-stu-id="8cf98-111">This sample demonstrates how to use the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span>  
  
 [<span data-ttu-id="8cf98-112">Олицетворение клиента</span><span class="sxs-lookup"><span data-stu-id="8cf98-112">Impersonating the Client</span></span>](impersonating-the-client.md)  
 <span data-ttu-id="8cf98-113">В этом образце показано, как олицетворять приложение абонента в службе таким образом, чтобы служба могла получить доступ к ресурсам системы от лица абонента.</span><span class="sxs-lookup"><span data-stu-id="8cf98-113">This sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>
