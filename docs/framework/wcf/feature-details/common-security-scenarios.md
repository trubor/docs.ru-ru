---
description: 'Дополнительные сведения: общие сценарии безопасности'
title: Типовые сценарии безопасности
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: ad4e3964a4a018793653b5eb48b91ca566840abb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743516"
---
# <a name="common-security-scenarios"></a><span data-ttu-id="0f6b6-103">Типовые сценарии безопасности</span><span class="sxs-lookup"><span data-stu-id="0f6b6-103">Common Security Scenarios</span></span>

<span data-ttu-id="0f6b6-104">В подразделах этого раздела рассматривается множество возможных конфигураций безопасности клиентов и служб.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-104">The topics in this section catalog a number of possible client and service security configurations.</span></span> <span data-ttu-id="0f6b6-105">Конфигурация зависит от ряда факторов:</span><span class="sxs-lookup"><span data-stu-id="0f6b6-105">Configurations vary according to a number of factors.</span></span> <span data-ttu-id="0f6b6-106">например, находится ли служба или клиент в интрасети, или чем обеспечивается безопасность - Windows или транспортом (таким как HTTPS).</span><span class="sxs-lookup"><span data-stu-id="0f6b6-106">For example, whether a service or client is on an intranet, or whether the security is provided by Windows or transport (such as HTTPS).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f6b6-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="0f6b6-107">In This Section</span></span>  

 [<span data-ttu-id="0f6b6-108">Незащищенные интернет-клиент и служба</span><span class="sxs-lookup"><span data-stu-id="0f6b6-108">Internet Unsecured Client and Service</span></span>](internet-unsecured-client-and-service.md)  
 <span data-ttu-id="0f6b6-109">Пример общедоступных, незащищенных клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-109">An example of a public, unsecured client and service.</span></span>  
  
 [<span data-ttu-id="0f6b6-110">Незащищенные интранет-клиент и служба</span><span class="sxs-lookup"><span data-stu-id="0f6b6-110">Intranet Unsecured Client and Service</span></span>](intranet-unsecured-client-and-service.md)  
 <span data-ttu-id="0f6b6-111">Служба Basic Windows Communication Foundation (WCF), разработанная для предоставления информации о защищенной частной сети приложению WCF.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-111">A basic Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span>  
  
 [<span data-ttu-id="0f6b6-112">Безопасность транспорта с обычной проверкой подлинности</span><span class="sxs-lookup"><span data-stu-id="0f6b6-112">Transport Security with Basic Authentication</span></span>](transport-security-with-basic-authentication.md)  
 <span data-ttu-id="0f6b6-113">Приложение, позволяющее клиентам входить в систему с использованием пользовательской проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-113">The application allows clients to log on using custom authentication.</span></span>  
  
 [<span data-ttu-id="0f6b6-114">Безопасность транспорта с проверкой подлинности Windows</span><span class="sxs-lookup"><span data-stu-id="0f6b6-114">Transport Security with Windows Authentication</span></span>](transport-security-with-windows-authentication.md)  
 <span data-ttu-id="0f6b6-115">Клиент и служба, защищенные механизмом безопасности Windows.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-115">Shows a client and service secured by Windows security.</span></span>  
  
 [<span data-ttu-id="0f6b6-116">Безопасность транспорта с анонимным клиентом</span><span class="sxs-lookup"><span data-stu-id="0f6b6-116">Transport Security with an Anonymous Client</span></span>](transport-security-with-an-anonymous-client.md)  
 <span data-ttu-id="0f6b6-117">Сценарий с использованием механизма безопасности транспорта (такого как HTTPS) для обеспечения конфиденциальности и целостности.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-117">This scenario uses transport security (such as HTTPS) to ensure confidentiality and integrity.</span></span>  
  
 [<span data-ttu-id="0f6b6-118">Безопасность транспорта с проверкой подлинности с использованием сертификатов</span><span class="sxs-lookup"><span data-stu-id="0f6b6-118">Transport Security with Certificate Authentication</span></span>](transport-security-with-certificate-authentication.md)  
 <span data-ttu-id="0f6b6-119">Клиент и служба, защищенные сертификатом.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-119">Shows a client and service secured by a certificate.</span></span>  
  
 [<span data-ttu-id="0f6b6-120">Безопасность сообщений с анонимным клиентом</span><span class="sxs-lookup"><span data-stu-id="0f6b6-120">Message Security with an Anonymous Client</span></span>](message-security-with-an-anonymous-client.md)  
 <span data-ttu-id="0f6b6-121">Показывает клиент и службу, защищенные с помощью безопасности сообщений WCF.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-121">Shows a client and service secured by WCF message security.</span></span>  
  
 [<span data-ttu-id="0f6b6-122">Безопасность сообщений при использовании клиентом учетных данных пользователя</span><span class="sxs-lookup"><span data-stu-id="0f6b6-122">Message Security with a User Name Client</span></span>](message-security-with-a-user-name-client.md)  
 <span data-ttu-id="0f6b6-123">Клиент - приложение Windows Forms, позволяющее клиентам входить в систему с использованием имени пользователя и пароля домена.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-123">The client is a Windows Forms application that allows clients to log on using a domain user name and password.</span></span>  
  
 [<span data-ttu-id="0f6b6-124">Безопасность сообщений при использовании клиентом сертификата</span><span class="sxs-lookup"><span data-stu-id="0f6b6-124">Message Security with a Certificate Client</span></span>](message-security-with-a-certificate-client.md)  
 <span data-ttu-id="0f6b6-125">Серверы имеют сертификаты и каждый клиент имеет сертификат.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-125">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="0f6b6-126">Контекст безопасности устанавливается посредством согласования по протоколу TLS.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-126">A security context is established through Transport Layer Security (TLS) negotiation.</span></span>  
  
 [<span data-ttu-id="0f6b6-127">Безопасность сообщений с клиентом Windows</span><span class="sxs-lookup"><span data-stu-id="0f6b6-127">Message Security with a Windows Client</span></span>](message-security-with-a-windows-client.md)  
 <span data-ttu-id="0f6b6-128">Разновидность клиента с сертификатом.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-128">A variation of the certificate client.</span></span> <span data-ttu-id="0f6b6-129">Серверы имеют сертификаты и каждый клиент имеет сертификат.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-129">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="0f6b6-130">Контекст безопасности устанавливается посредством согласования TLS.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-130">A security context is established through TLS negotiation.</span></span>  
  
 [<span data-ttu-id="0f6b6-131">Безопасность сообщений с использованием клиента Windows без согласования учетных данных</span><span class="sxs-lookup"><span data-stu-id="0f6b6-131">Message Security with a Windows Client without Credential Negotiation</span></span>](message-security-with-a-windows-client-without-credential-negotiation.md)  
 <span data-ttu-id="0f6b6-132">Клиент и служба, защищенные доменом Kerberos.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-132">Shows a client and service secured by a Kerberos domain.</span></span>  
  
 [<span data-ttu-id="0f6b6-133">Безопасность сообщений с использованием взаимных сертификатов</span><span class="sxs-lookup"><span data-stu-id="0f6b6-133">Message Security with Mutual Certificates</span></span>](message-security-with-mutual-certificates.md)  
 <span data-ttu-id="0f6b6-134">Серверы имеют сертификаты и каждый клиент имеет сертификат.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-134">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="0f6b6-135">Сертификат сервера распространяется вместе с приложением и доступен внештатно.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-135">The server certificate is distributed with the application and is available out of band.</span></span>  
  
 [<span data-ttu-id="0f6b6-136">Безопасность сообщений с использованием выданных маркеров</span><span class="sxs-lookup"><span data-stu-id="0f6b6-136">Message Security with Issued Tokens</span></span>](message-security-with-issued-tokens.md)  
 <span data-ttu-id="0f6b6-137">Федеративная безопасность, позволяющая установить доверие между независимыми доменами.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-137">Federated security that enables the establishment of trust between independent domains.</span></span>  
  
 [<span data-ttu-id="0f6b6-138">Доверенная подсистема</span><span class="sxs-lookup"><span data-stu-id="0f6b6-138">Trusted Subsystem</span></span>](trusted-subsystem.md)  
 <span data-ttu-id="0f6b6-139">Клиент обращается к одной или нескольким веб-службам, распределенным по сети.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-139">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="0f6b6-140">Веб-службы обращаются к дополнительным ресурсам (таким как базы данных или другие веб-службы), которые должны быть защищены.</span><span class="sxs-lookup"><span data-stu-id="0f6b6-140">The Web services access additional resources (such as databases or other Web services) that must be secured.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0f6b6-141">Справочник</span><span class="sxs-lookup"><span data-stu-id="0f6b6-141">Reference</span></span>  

 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="0f6b6-142">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="0f6b6-142">Related Sections</span></span>  

 [<span data-ttu-id="0f6b6-143">Авторизация</span><span class="sxs-lookup"><span data-stu-id="0f6b6-143">Authorization</span></span>](authorization-in-wcf.md)  
  
 [<span data-ttu-id="0f6b6-144">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="0f6b6-144">Security Overview</span></span>](security-overview.md)  
  
 [<span data-ttu-id="0f6b6-145">Безопасность</span><span class="sxs-lookup"><span data-stu-id="0f6b6-145">Security</span></span>](security.md)  
  
 [<span data-ttu-id="0f6b6-146">Привязки и безопасность</span><span class="sxs-lookup"><span data-stu-id="0f6b6-146">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="0f6b6-147">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="0f6b6-147">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
 [<span data-ttu-id="0f6b6-148">Аутентификация</span><span class="sxs-lookup"><span data-stu-id="0f6b6-148">Authentication</span></span>](authentication-in-wcf.md)  
  
 [<span data-ttu-id="0f6b6-149">Авторизация</span><span class="sxs-lookup"><span data-stu-id="0f6b6-149">Authorization</span></span>](authorization-in-wcf.md)  
  
 [<span data-ttu-id="0f6b6-150">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="0f6b6-150">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="0f6b6-151">Аудит</span><span class="sxs-lookup"><span data-stu-id="0f6b6-151">Auditing</span></span>](auditing-security-events.md)  
  
## <a name="see-also"></a><span data-ttu-id="0f6b6-152">См. также</span><span class="sxs-lookup"><span data-stu-id="0f6b6-152">See also</span></span>

- [<span data-ttu-id="0f6b6-153">Руководство и рекомендации по безопасности</span><span class="sxs-lookup"><span data-stu-id="0f6b6-153">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)
- <span data-ttu-id="0f6b6-154">[Модель безопасности для Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0f6b6-154">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
