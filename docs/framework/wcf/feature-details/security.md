---
description: 'Дополнительные сведения: Windows Communication Foundation безопасность'
title: Безопасность Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
ms.openlocfilehash: 8cf748504c85844f82f8941be1b60bb29478f730
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726797"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="85c06-103">Безопасность Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="85c06-103">Windows Communication Foundation Security</span></span>

<span data-ttu-id="85c06-104">В подразделах этого раздела описываются функции безопасности Windows Communication Foundation (WCF) и способы их использования для защиты сообщений.</span><span class="sxs-lookup"><span data-stu-id="85c06-104">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="85c06-105">Дополнительные сведения о Windows Server AppFabric и безопасности см. в статье [модель безопасности для Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10)) .</span><span class="sxs-lookup"><span data-stu-id="85c06-105">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85c06-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="85c06-106">In This Section</span></span>  

 [<span data-ttu-id="85c06-107">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="85c06-107">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="85c06-108">Описание функций безопасности в WCF.</span><span class="sxs-lookup"><span data-stu-id="85c06-108">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="85c06-109">Основные понятия безопасности</span><span class="sxs-lookup"><span data-stu-id="85c06-109">Security Concepts</span></span>](security-concepts.md)  
 <span data-ttu-id="85c06-110">Описывает основные термины и понятия, используемые в безопасности WCF.</span><span class="sxs-lookup"><span data-stu-id="85c06-110">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="85c06-111">Типовые сценарии безопасности</span><span class="sxs-lookup"><span data-stu-id="85c06-111">Common Security Scenarios</span></span>](common-security-scenarios.md)  
 <span data-ttu-id="85c06-112">Описание сценариев и топологий, которые можно настроить с помощью WCF.</span><span class="sxs-lookup"><span data-stu-id="85c06-112">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="85c06-113">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="85c06-113">Security Behaviors</span></span>](security-behaviors-in-wcf.md)  
 <span data-ttu-id="85c06-114">Общие сведения о поведении WCF, которые оказывают влияние на безопасность, например на настройки учетных данных.</span><span class="sxs-lookup"><span data-stu-id="85c06-114">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="85c06-115">Привязки и безопасность</span><span class="sxs-lookup"><span data-stu-id="85c06-115">Bindings and Security</span></span>](bindings-and-security.md)  
 <span data-ttu-id="85c06-116">Описание привязок с точки зрения безопасности, в том числе демонстрация создания настраиваемых привязок безопасности.</span><span class="sxs-lookup"><span data-stu-id="85c06-116">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="85c06-117">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="85c06-117">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
 <span data-ttu-id="85c06-118">Описывает, как защитить сообщения с помощью функций безопасности WCF.</span><span class="sxs-lookup"><span data-stu-id="85c06-118">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="85c06-119">Аутентификация</span><span class="sxs-lookup"><span data-stu-id="85c06-119">Authentication</span></span>](authentication-in-wcf.md)  
 <span data-ttu-id="85c06-120">Примеры типичных задач, связанных с проверкой подлинности.</span><span class="sxs-lookup"><span data-stu-id="85c06-120">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="85c06-121">Авторизация</span><span class="sxs-lookup"><span data-stu-id="85c06-121">Authorization</span></span>](authorization-in-wcf.md)  
 <span data-ttu-id="85c06-122">Типичные сценарии авторизации с реализацией системы безопасности.</span><span class="sxs-lookup"><span data-stu-id="85c06-122">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="85c06-123">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="85c06-123">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
 <span data-ttu-id="85c06-124">Основы федерации и принципы создания клиентов, взаимодействующих с федеративными серверами.</span><span class="sxs-lookup"><span data-stu-id="85c06-124">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="85c06-125">Частичное доверие</span><span class="sxs-lookup"><span data-stu-id="85c06-125">Partial Trust</span></span>](partial-trust.md)  
 <span data-ttu-id="85c06-126">Описывает, как выполнять частично доверенные сценарии и ограничения WCF при выполнении частичного доверия.</span><span class="sxs-lookup"><span data-stu-id="85c06-126">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="85c06-127">Аудит</span><span class="sxs-lookup"><span data-stu-id="85c06-127">Auditing</span></span>](auditing-security-events.md)  
 <span data-ttu-id="85c06-128">Принципы аудита событий безопасности.</span><span class="sxs-lookup"><span data-stu-id="85c06-128">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="85c06-129">Руководство и рекомендации по безопасности</span><span class="sxs-lookup"><span data-stu-id="85c06-129">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
 <span data-ttu-id="85c06-130">Рекомендации по созданию безопасных приложений WCF.</span><span class="sxs-lookup"><span data-stu-id="85c06-130">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="85c06-131">Справочник</span><span class="sxs-lookup"><span data-stu-id="85c06-131">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="85c06-132">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="85c06-132">Related Sections</span></span>  

 [<span data-ttu-id="85c06-133">Сведения о функции WCF</span><span class="sxs-lookup"><span data-stu-id="85c06-133">WCF Feature Details</span></span>](index.md)  
  
 [<span data-ttu-id="85c06-134">Базовое программирование для WCF</span><span class="sxs-lookup"><span data-stu-id="85c06-134">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="85c06-135">Учебник по началу работы</span><span class="sxs-lookup"><span data-stu-id="85c06-135">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)  
  
 [<span data-ttu-id="85c06-136">Общие сведения об основных понятиях</span><span class="sxs-lookup"><span data-stu-id="85c06-136">Conceptual Overview</span></span>](../conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="85c06-137">См. также</span><span class="sxs-lookup"><span data-stu-id="85c06-137">See also</span></span>

- [<span data-ttu-id="85c06-138">Настройка приложения</span><span class="sxs-lookup"><span data-stu-id="85c06-138">Configuring Your Application</span></span>](../diagnostics/configuring-your-application.md)
