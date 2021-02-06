---
description: Дополнительные сведения см. в статье Авторизация в WCF.
title: Авторизация в WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 3fda699a33d8b512d047232398e9cfac63661a85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643713"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="4c1f4-103">Авторизация в WCF</span><span class="sxs-lookup"><span data-stu-id="4c1f4-103">Authorization in WCF</span></span>

<span data-ttu-id="4c1f4-104">Авторизация - процесс управления доступом и правами на ресурсы, например службы и файлы.</span><span class="sxs-lookup"><span data-stu-id="4c1f4-104">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="4c1f4-105">В подразделах этого раздела показано, как выполнить эту базовую задачу в Windows Communication Foundation (WCF) различными способами.</span><span class="sxs-lookup"><span data-stu-id="4c1f4-105">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c1f4-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="4c1f4-106">In This Section</span></span>  

 [<span data-ttu-id="4c1f4-107">Механизмы управления доступом</span><span class="sxs-lookup"><span data-stu-id="4c1f4-107">Access Control Mechanisms</span></span>](access-control-mechanisms.md)  
 <span data-ttu-id="4c1f4-108">Краткий обзор механизмов авторизации в WCF и предлагаемых вариантов использования.</span><span class="sxs-lookup"><span data-stu-id="4c1f4-108">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="4c1f4-109">Практическое руководство. Ограничение доступа с использованием класса PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="4c1f4-109">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="4c1f4-110">Показывает процесс ограничения доступа к сервису с помощью класса <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4c1f4-110">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="4c1f4-111">Практическое руководство. Использование поставщика ролей ASP.NET со службой</span><span class="sxs-lookup"><span data-stu-id="4c1f4-111">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="4c1f4-112">Пошаговые инструкции по настройке службы, позволяющие использовать функцию поставщика ролей ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4c1f4-112">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="4c1f4-113">Практическое руководство. Использование поставщика ролей диспетчера авторизации ASP.NET со службой</span><span class="sxs-lookup"><span data-stu-id="4c1f4-113">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="4c1f4-114">ASP.NET может использовать диспетчер авторизации для управления авторизацией веб-сайта.</span><span class="sxs-lookup"><span data-stu-id="4c1f4-114">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="4c1f4-115">WCF также может использовать сочетание ASP.NET/Authorization Manager для авторизации клиентов.</span><span class="sxs-lookup"><span data-stu-id="4c1f4-115">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="4c1f4-116">Управление утверждениями и авторизацией с помощью модели удостоверения</span><span class="sxs-lookup"><span data-stu-id="4c1f4-116">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="4c1f4-117">Объясняет основы использования инфраструктуры модели удостоверения для механизма авторизации на основе утверждений.</span><span class="sxs-lookup"><span data-stu-id="4c1f4-117">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="4c1f4-118">Делегирование и олицетворение</span><span class="sxs-lookup"><span data-stu-id="4c1f4-118">Delegation and Impersonation</span></span>](delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="4c1f4-119">Объясняет разницу между делегированием и олицетворением.</span><span class="sxs-lookup"><span data-stu-id="4c1f4-119">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4c1f4-120">Справочник</span><span class="sxs-lookup"><span data-stu-id="4c1f4-120">Reference</span></span>  

 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="4c1f4-121">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="4c1f4-121">Related Sections</span></span>  

 [<span data-ttu-id="4c1f4-122">Аутентификация</span><span class="sxs-lookup"><span data-stu-id="4c1f4-122">Authentication</span></span>](authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="4c1f4-123">См. также</span><span class="sxs-lookup"><span data-stu-id="4c1f4-123">See also</span></span>

- [<span data-ttu-id="4c1f4-124">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="4c1f4-124">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="4c1f4-125">[Модель безопасности для Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="4c1f4-125">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
