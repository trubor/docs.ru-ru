---
description: Дополнительные сведения см. в статье протоколы безопасности версии 1,0.
title: Протоколы безопасности версии 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: c807f0b844fb9cb861148afa63d83826a9740c98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752734"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="47571-103">Протоколы безопасности версии 1.0</span><span class="sxs-lookup"><span data-stu-id="47571-103">Security Protocols version 1.0</span></span>

<span data-ttu-id="47571-104">Протоколы WS-Security предоставляют механизмы обеспечения безопасности веб-служб, охватывающие все существующие требования к безопасности обмена сообщениями на предприятии.</span><span class="sxs-lookup"><span data-stu-id="47571-104">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="47571-105">В этом разделе описаны сведения о Windows Communication Foundation (WCF) версии 1,0 (реализован в <xref:System.ServiceModel.Channels.SecurityBindingElement> ) для следующих протоколов безопасности веб-служб.</span><span class="sxs-lookup"><span data-stu-id="47571-105">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="47571-106">Спецификация/документ</span><span class="sxs-lookup"><span data-stu-id="47571-106">Specification/Document</span></span>|<span data-ttu-id="47571-107">Ссылка</span><span class="sxs-lookup"><span data-stu-id="47571-107">Link</span></span>|  
|-|-|  
|<span data-ttu-id="47571-108">WSS: SOAP Message Security 1,0</span><span class="sxs-lookup"><span data-stu-id="47571-108">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="47571-109">WSS: Username Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="47571-109">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="47571-110">WSS: X509 Token Profile 1,0</span><span class="sxs-lookup"><span data-stu-id="47571-110">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="47571-111">WSS: SAML 1.1 Token Profile 1,0</span><span class="sxs-lookup"><span data-stu-id="47571-111">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="47571-112">WSS: SOAP Message Security 1.1</span><span class="sxs-lookup"><span data-stu-id="47571-112">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="47571-113">WSS Username Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="47571-113">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="47571-114">WSS: X.509 Token Profile 1,1</span><span class="sxs-lookup"><span data-stu-id="47571-114">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="47571-115">WSS: Kerberos Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="47571-115">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="47571-116">WSS: SAML 1.1 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="47571-116">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="47571-117">WS-Secure Conversation</span><span class="sxs-lookup"><span data-stu-id="47571-117">WS-Secure Conversation</span></span>|<http://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="47571-118">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="47571-118">WS-Trust</span></span>|<http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="47571-119">Замечания по применению.</span><span class="sxs-lookup"><span data-stu-id="47571-119">Application Note:</span></span><br /><br /> <span data-ttu-id="47571-120">Использование WS-Trust для подтверждения TLS</span><span class="sxs-lookup"><span data-stu-id="47571-120">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="47571-121">Готовится к публикации</span><span class="sxs-lookup"><span data-stu-id="47571-121">To be published</span></span>|  
|<span data-ttu-id="47571-122">Замечания по применению.</span><span class="sxs-lookup"><span data-stu-id="47571-122">Application Note:</span></span><br /><br /> <span data-ttu-id="47571-123">Использование WS-Trust для подтверждения SPNEGO</span><span class="sxs-lookup"><span data-stu-id="47571-123">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="47571-124">Готовится к публикации</span><span class="sxs-lookup"><span data-stu-id="47571-124">To be published</span></span>|  
|<span data-ttu-id="47571-125">Замечания по применению.</span><span class="sxs-lookup"><span data-stu-id="47571-125">Application Note:</span></span><br /><br /> <span data-ttu-id="47571-126">Ссылки и идентификация конечной точки адресации веб-служб</span><span class="sxs-lookup"><span data-stu-id="47571-126">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="47571-127">Готовится к публикации</span><span class="sxs-lookup"><span data-stu-id="47571-127">To be published</span></span>|  
|<span data-ttu-id="47571-128">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="47571-128">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="47571-129">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="47571-129">(2005/07)</span></span>|<http://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="47571-130">как исправлено в [перечне ошибок](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) , отправленных в технический комитет OASIS WS-SX</span><span class="sxs-lookup"><span data-stu-id="47571-130">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="47571-131">WCF версии 1 предоставляет 17 режимов проверки подлинности, которые можно использовать в качестве базиса для настройки безопасности веб-служб.</span><span class="sxs-lookup"><span data-stu-id="47571-131">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="47571-132">Каждый из режимов оптимизирован для того или иного типичного набора требований к развертыванию, например следующих:</span><span class="sxs-lookup"><span data-stu-id="47571-132">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="47571-133">учетные данные, используемые для проверки подлинности клиента и службы;</span><span class="sxs-lookup"><span data-stu-id="47571-133">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="47571-134">механизмы обеспечения безопасности на уровне сообщений или транспорта;</span><span class="sxs-lookup"><span data-stu-id="47571-134">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="47571-135">шаблоны обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="47571-135">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="47571-136">Режим проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="47571-136">Authentication Mode</span></span>|<span data-ttu-id="47571-137">Аутентификация клиента</span><span class="sxs-lookup"><span data-stu-id="47571-137">Client Authentication</span></span>|<span data-ttu-id="47571-138">Проверка подлинности сервера</span><span class="sxs-lookup"><span data-stu-id="47571-138">Server Authentication</span></span>|<span data-ttu-id="47571-139">Режим</span><span class="sxs-lookup"><span data-stu-id="47571-139">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="47571-140">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="47571-140">UserNameOverTransport</span></span>|<span data-ttu-id="47571-141">Имя пользователя/пароль</span><span class="sxs-lookup"><span data-stu-id="47571-141">User name/password</span></span>|<span data-ttu-id="47571-142">X509</span><span class="sxs-lookup"><span data-stu-id="47571-142">X509</span></span>|<span data-ttu-id="47571-143">Транспорт</span><span class="sxs-lookup"><span data-stu-id="47571-143">Transport</span></span>|  
|<span data-ttu-id="47571-144">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="47571-144">CertificateOverTransport</span></span>|<span data-ttu-id="47571-145">X509</span><span class="sxs-lookup"><span data-stu-id="47571-145">X509</span></span>|<span data-ttu-id="47571-146">X509</span><span class="sxs-lookup"><span data-stu-id="47571-146">X509</span></span>|<span data-ttu-id="47571-147">Транспорт</span><span class="sxs-lookup"><span data-stu-id="47571-147">Transport</span></span>|  
|<span data-ttu-id="47571-148">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="47571-148">KerberosOverTransport</span></span>|<span data-ttu-id="47571-149">Windows</span><span class="sxs-lookup"><span data-stu-id="47571-149">Windows</span></span>|<span data-ttu-id="47571-150">X509</span><span class="sxs-lookup"><span data-stu-id="47571-150">X509</span></span>|<span data-ttu-id="47571-151">Транспорт</span><span class="sxs-lookup"><span data-stu-id="47571-151">Transport</span></span>|  
|<span data-ttu-id="47571-152">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="47571-152">IssuedTokenOverTransport</span></span>|<span data-ttu-id="47571-153">Федеративные</span><span class="sxs-lookup"><span data-stu-id="47571-153">Federated</span></span>|<span data-ttu-id="47571-154">X509</span><span class="sxs-lookup"><span data-stu-id="47571-154">X509</span></span>|<span data-ttu-id="47571-155">Транспорт</span><span class="sxs-lookup"><span data-stu-id="47571-155">Transport</span></span>|  
|<span data-ttu-id="47571-156">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="47571-156">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="47571-157">Согласование Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="47571-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="47571-158">Согласование Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="47571-158">Windows Sspi Negotiated</span></span>|<span data-ttu-id="47571-159">Транспорт</span><span class="sxs-lookup"><span data-stu-id="47571-159">Transport</span></span>|  
|<span data-ttu-id="47571-160">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="47571-160">AnonymousForCertificate</span></span>|<span data-ttu-id="47571-161">None</span><span class="sxs-lookup"><span data-stu-id="47571-161">None</span></span>|<span data-ttu-id="47571-162">X509</span><span class="sxs-lookup"><span data-stu-id="47571-162">X509</span></span>|<span data-ttu-id="47571-163">Сообщение</span><span class="sxs-lookup"><span data-stu-id="47571-163">Message</span></span>|  
|<span data-ttu-id="47571-164">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="47571-164">UserNameForCertificate</span></span>|<span data-ttu-id="47571-165">Имя пользователя/пароль</span><span class="sxs-lookup"><span data-stu-id="47571-165">User name/password</span></span>|<span data-ttu-id="47571-166">X509</span><span class="sxs-lookup"><span data-stu-id="47571-166">X509</span></span>|<span data-ttu-id="47571-167">Сообщение</span><span class="sxs-lookup"><span data-stu-id="47571-167">Message</span></span>|  
|<span data-ttu-id="47571-168">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="47571-168">MutualCertificate</span></span>|<span data-ttu-id="47571-169">X509</span><span class="sxs-lookup"><span data-stu-id="47571-169">X509</span></span>|<span data-ttu-id="47571-170">X509</span><span class="sxs-lookup"><span data-stu-id="47571-170">X509</span></span>|<span data-ttu-id="47571-171">Сообщение</span><span class="sxs-lookup"><span data-stu-id="47571-171">Message</span></span>|  
|<span data-ttu-id="47571-172">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="47571-172">MutualCertificateDuplex</span></span>|<span data-ttu-id="47571-173">X509</span><span class="sxs-lookup"><span data-stu-id="47571-173">X509</span></span>|<span data-ttu-id="47571-174">X509</span><span class="sxs-lookup"><span data-stu-id="47571-174">X509</span></span>|<span data-ttu-id="47571-175">Сообщение</span><span class="sxs-lookup"><span data-stu-id="47571-175">Message</span></span>|  
|<span data-ttu-id="47571-176">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="47571-176">IssuedTokenForCertificate</span></span>|<span data-ttu-id="47571-177">Федеративные</span><span class="sxs-lookup"><span data-stu-id="47571-177">Federated</span></span>|<span data-ttu-id="47571-178">X509</span><span class="sxs-lookup"><span data-stu-id="47571-178">X509</span></span>|<span data-ttu-id="47571-179">Сообщение</span><span class="sxs-lookup"><span data-stu-id="47571-179">Message</span></span>|  
|<span data-ttu-id="47571-180">Kerberos</span><span class="sxs-lookup"><span data-stu-id="47571-180">Kerberos</span></span>|<span data-ttu-id="47571-181">Windows</span><span class="sxs-lookup"><span data-stu-id="47571-181">Windows</span></span>|<span data-ttu-id="47571-182">Windows</span><span class="sxs-lookup"><span data-stu-id="47571-182">Windows</span></span>|<span data-ttu-id="47571-183">Сообщение</span><span class="sxs-lookup"><span data-stu-id="47571-183">Message</span></span>|  
|<span data-ttu-id="47571-184">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="47571-184">IssuedToken</span></span>|<span data-ttu-id="47571-185">Федеративные</span><span class="sxs-lookup"><span data-stu-id="47571-185">Federated</span></span>|<span data-ttu-id="47571-186">Федеративные</span><span class="sxs-lookup"><span data-stu-id="47571-186">Federated</span></span>|<span data-ttu-id="47571-187">Сообщение</span><span class="sxs-lookup"><span data-stu-id="47571-187">Message</span></span>|  
|<span data-ttu-id="47571-188">SspiNegotiation</span><span class="sxs-lookup"><span data-stu-id="47571-188">SspiNegotiated</span></span>|<span data-ttu-id="47571-189">Согласование Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="47571-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="47571-190">Согласование Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="47571-190">Windows Sspi Negotiated</span></span>|<span data-ttu-id="47571-191">Сообщение</span><span class="sxs-lookup"><span data-stu-id="47571-191">Message</span></span>|  
|<span data-ttu-id="47571-192">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="47571-192">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="47571-193">None</span><span class="sxs-lookup"><span data-stu-id="47571-193">None</span></span>|<span data-ttu-id="47571-194">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="47571-194">X509, TLS-Nego</span></span>|<span data-ttu-id="47571-195">Сообщение</span><span class="sxs-lookup"><span data-stu-id="47571-195">Message</span></span>|  
|<span data-ttu-id="47571-196">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="47571-196">UserNameForSslNegotiated</span></span>|<span data-ttu-id="47571-197">Имя пользователя/пароль</span><span class="sxs-lookup"><span data-stu-id="47571-197">User name/password</span></span>|<span data-ttu-id="47571-198">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="47571-198">X509, TLS-Nego</span></span>|<span data-ttu-id="47571-199">Сообщение</span><span class="sxs-lookup"><span data-stu-id="47571-199">Message</span></span>|  
|<span data-ttu-id="47571-200">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="47571-200">MutualSslNegotiated</span></span>|<span data-ttu-id="47571-201">X509</span><span class="sxs-lookup"><span data-stu-id="47571-201">X509</span></span>|<span data-ttu-id="47571-202">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="47571-202">X509, TLS-Nego</span></span>|<span data-ttu-id="47571-203">Сообщение</span><span class="sxs-lookup"><span data-stu-id="47571-203">Message</span></span>|  
|<span data-ttu-id="47571-204">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="47571-204">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="47571-205">Федеративные</span><span class="sxs-lookup"><span data-stu-id="47571-205">Federated</span></span>|<span data-ttu-id="47571-206">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="47571-206">X509, TLS-Nego</span></span>|<span data-ttu-id="47571-207">Сообщение</span><span class="sxs-lookup"><span data-stu-id="47571-207">Message</span></span>|  
  
 <span data-ttu-id="47571-208">Конечные точки, использующие такие режимы проверки подлинности, могут выражать свои требования безопасности с помощью WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="47571-208">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="47571-209">В этом документе описывается структура заголовка безопасности и инфраструктурные сообщения для каждого режима проверки подлинности, а также приводятся примеры политик и сообщений.</span><span class="sxs-lookup"><span data-stu-id="47571-209">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="47571-210">WCF использует WS-SecureConversation для обеспечения поддержки безопасных сеансов для защиты обмена сообщениями между приложениями.</span><span class="sxs-lookup"><span data-stu-id="47571-210">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="47571-211">Сведения о реализации см. ниже в подразделе "Безопасные сеансы".</span><span class="sxs-lookup"><span data-stu-id="47571-211">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="47571-212">В дополнение к режимам проверки подлинности, WCF предоставляет параметры для управления общими механизмами защиты, которые применяются к большинству режимов проверки подлинности на основе безопасности сообщений, например: порядок подписи и операции шифрования, наборы алгоритмов, получение ключа и Подтверждение сигнатуры.</span><span class="sxs-lookup"><span data-stu-id="47571-212">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="47571-213">В данном документе используются перечисленные ниже префиксы и пространства имен.</span><span class="sxs-lookup"><span data-stu-id="47571-213">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="47571-214">Prefix</span><span class="sxs-lookup"><span data-stu-id="47571-214">Prefix</span></span>|<span data-ttu-id="47571-215">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="47571-215">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="47571-216">s</span><span class="sxs-lookup"><span data-stu-id="47571-216">s</span></span>|<http://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="47571-217">sp</span><span class="sxs-lookup"><span data-stu-id="47571-217">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="47571-218">а</span><span class="sxs-lookup"><span data-stu-id="47571-218">a</span></span>|<http://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="47571-219">wsse</span><span class="sxs-lookup"><span data-stu-id="47571-219">wsse</span></span>|<span data-ttu-id="47571-220">Подлежит определению - универсальный код ресурса (URI) OASIS WSS 1,0</span><span class="sxs-lookup"><span data-stu-id="47571-220">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="47571-221">wsse11</span><span class="sxs-lookup"><span data-stu-id="47571-221">wsse11</span></span>|<span data-ttu-id="47571-222">Подлежит определению - универсальный код ресурса (URI) OASIS WSS 1.1</span><span class="sxs-lookup"><span data-stu-id="47571-222">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="47571-223">wsu</span><span class="sxs-lookup"><span data-stu-id="47571-223">wsu</span></span>|<span data-ttu-id="47571-224">Подлежит определению - универсальный код ресурса (URI) OASIS WSS 1.0 Utility</span><span class="sxs-lookup"><span data-stu-id="47571-224">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="47571-225">ds</span><span class="sxs-lookup"><span data-stu-id="47571-225">ds</span></span>|<span data-ttu-id="47571-226">Подлежит определению - универсальный код ресурса (URI) W3C XMLDSig</span><span class="sxs-lookup"><span data-stu-id="47571-226">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="47571-227">wst</span><span class="sxs-lookup"><span data-stu-id="47571-227">wst</span></span>|<span data-ttu-id="47571-228">Подлежит определению - универсальный код ресурса (URI) WS-Trust 2005/02</span><span class="sxs-lookup"><span data-stu-id="47571-228">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="47571-229">wssc</span><span class="sxs-lookup"><span data-stu-id="47571-229">wssc</span></span>|<span data-ttu-id="47571-230">Подлежит определению - универсальный код ресурса (URI) WS-SecureConversation 2005/02</span><span class="sxs-lookup"><span data-stu-id="47571-230">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="47571-231">wsaw</span><span class="sxs-lookup"><span data-stu-id="47571-231">wsaw</span></span>|<span data-ttu-id="47571-232">Подлежит определению - пространство имен политики WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="47571-232">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="47571-233">wsp</span><span class="sxs-lookup"><span data-stu-id="47571-233">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="47571-234">mssp</span><span class="sxs-lookup"><span data-stu-id="47571-234">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="47571-235">1. Профили маркеров</span><span class="sxs-lookup"><span data-stu-id="47571-235">1. Token Profiles</span></span>  

 <span data-ttu-id="47571-236">В спецификациях WS-Security учетные данные представляются в виде токенов безопасности.</span><span class="sxs-lookup"><span data-stu-id="47571-236">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="47571-237">WCF поддерживает следующие типы токенов:</span><span class="sxs-lookup"><span data-stu-id="47571-237">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="47571-238">1.1 Маркер UsernameToken</span><span class="sxs-lookup"><span data-stu-id="47571-238">1.1 UsernameToken</span></span>  

 <span data-ttu-id="47571-239">WCF использует профили UsernameToken10 и UsernameToken11 со следующими ограничениями:</span><span class="sxs-lookup"><span data-stu-id="47571-239">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="47571-240">R1101 Атрибут PasswordType элемента UsernameToken\Password ДОЛЖЕН быть либо опущен, либо иметь значение #PasswordText (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="47571-240">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="47571-241">Можно реализовать #PasswordDigest с помощью расширяемости.</span><span class="sxs-lookup"><span data-stu-id="47571-241">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="47571-242">Замечено, что #PasswordDigest часто ошибочно считается достаточно безопасным механизмом защиты пароля.</span><span class="sxs-lookup"><span data-stu-id="47571-242">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="47571-243">Однако #PasswordDigest не может служить заменой шифрованию маркера UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="47571-243">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="47571-244">Основной целью #PasswordDigest является защита от атак с повторением.</span><span class="sxs-lookup"><span data-stu-id="47571-244">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="47571-245">В режимах проверки подлинности WCF угрозы атак с целью воспроизведения снижаются с помощью подписей сообщений.</span><span class="sxs-lookup"><span data-stu-id="47571-245">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="47571-246">B1102 WCF никогда не выдает nonce и создает вложенные элементы UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="47571-246">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="47571-247">Эти подэлементы предназначены для упрощения обнаружения атак с повторением.</span><span class="sxs-lookup"><span data-stu-id="47571-247">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="47571-248">В WCF вместо этого используются сигнатуры сообщений.</span><span class="sxs-lookup"><span data-stu-id="47571-248">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="47571-249">В профиле OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) введена возможность создания производного ключа из пароля.</span><span class="sxs-lookup"><span data-stu-id="47571-249">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="47571-250">B1103 Пароль UsernameToken НЕ ДОЛЖЕН использоваться для создания производного ключа и, следовательно, для операций шифрования.</span><span class="sxs-lookup"><span data-stu-id="47571-250">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="47571-251">Обоснование: пароли обычно считаются слишком слабой защитой, для того чтобы использовать их в операциях шифрования.</span><span class="sxs-lookup"><span data-stu-id="47571-251">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="47571-252">1.2 Маркер X509</span><span class="sxs-lookup"><span data-stu-id="47571-252">1.2 X509 Token</span></span>  

 <span data-ttu-id="47571-253">WCF поддерживает сертификаты X509v3 в качестве типа учетных данных и соответствует X509TokenProfile 1.0 и X509TokenProfile 1.1 со следующими ограничениями:</span><span class="sxs-lookup"><span data-stu-id="47571-253">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="47571-254">R1201 Атрибут ValueType элемента BinarySecurityToken должен иметь значение #X509v3, если он содержит сертификат X509v3.</span><span class="sxs-lookup"><span data-stu-id="47571-254">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="47571-255">Профили WSS X509 Token Profile 1.0 и 1.1 также определяют типы значений #X509PKIPathv1 и #PKCS7.</span><span class="sxs-lookup"><span data-stu-id="47571-255">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="47571-256">WCF не поддерживает эти типы.</span><span class="sxs-lookup"><span data-stu-id="47571-256">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="47571-257">R1202 Если в сертификате X509 имеется расширение SubjectKeyIdentifier (SKI), для внешних ссылок на маркер должен использоваться wsse:KeyIdentifier, со значением #X509SubjectKeyIdentifier атрибута ValueType и содержащий значение расширения SKI сертификата в кодировке base64.</span><span class="sxs-lookup"><span data-stu-id="47571-257">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="47571-258">Ссылки SKI имеют множество реализаций и зарекомендовали себя как внешний ссылочный тип с широкими возможностями совместимости.</span><span class="sxs-lookup"><span data-stu-id="47571-258">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="47571-259">R1203 Внешняя ссылка на маркер безопасности X509 НЕ ДОЛЖНА использовать ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="47571-259">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="47571-260">R1204 Если используется профиль X509TokenProfile1.1, внешняя ссылка на маркер безопасности X509 ДОЛЖНА использовать отпечаток, введенный в протоколе WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="47571-260">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="47571-261">WCF поддерживает X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="47571-261">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="47571-262">Однако существуют проблемы взаимодействия с X509IssuerSerial: WCF использует строку для сравнения двух значений X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="47571-262">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="47571-263">Поэтому, если один из способов переупорядочивает компоненты имени субъекта и отправляет в службу WCF ссылку на сертификат, он может быть не найден.</span><span class="sxs-lookup"><span data-stu-id="47571-263">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="47571-264">1.3 Маркер Kerberos</span><span class="sxs-lookup"><span data-stu-id="47571-264">1.3 Kerberos Token</span></span>  

 <span data-ttu-id="47571-265">WCF поддерживает Керберостокенпрофиле 1.1 в целях проверки подлинности Windows со следующими ограничениями:</span><span class="sxs-lookup"><span data-stu-id="47571-265">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="47571-266">R1301 Маркер Kerberos должен содержать значение GSS в оболочке Kerberos v4 AP_REQ, как определено в GSS_API и спецификации Kerberos, и должен иметь атрибут ValueType со значением #GSS_Kerberosv5_AP_REQ.</span><span class="sxs-lookup"><span data-stu-id="47571-266">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="47571-267">WCF использует GSS, инкапсулированные Kerberos AP-REQ, а не несамостоятельный AP-REQ.</span><span class="sxs-lookup"><span data-stu-id="47571-267">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="47571-268">Это рекомендуется в целях безопасности.</span><span class="sxs-lookup"><span data-stu-id="47571-268">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="47571-269">1.4 Маркер SAML 1.1</span><span class="sxs-lookup"><span data-stu-id="47571-269">1.4 SAML v1.1 Token</span></span>  

 <span data-ttu-id="47571-270">В WCF поддерживаются профили маркеров WSS SAML 1,0 и 1,1 для маркеров SAML v 1.1.</span><span class="sxs-lookup"><span data-stu-id="47571-270">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="47571-271">Возможна реализация других версий форматов маркеров SAML.</span><span class="sxs-lookup"><span data-stu-id="47571-271">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="47571-272">1.5 Маркер контекста безопасности</span><span class="sxs-lookup"><span data-stu-id="47571-272">1.5 Security Context Token</span></span>  

 <span data-ttu-id="47571-273">WCF поддерживает маркер контекста безопасности (SCT), появившийся в WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="47571-273">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="47571-274">Маркер контекста безопасности служит для представления контекста безопасности, установленного в спецификации SecureConversation, а также протоколов двоичного согласования TLS и SSPI, описываемых ниже.</span><span class="sxs-lookup"><span data-stu-id="47571-274">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="47571-275">2. Общие параметры безопасности сообщений</span><span class="sxs-lookup"><span data-stu-id="47571-275">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="47571-276">2.1 TimeStamp</span><span class="sxs-lookup"><span data-stu-id="47571-276">2.1 TimeStamp</span></span>  

 <span data-ttu-id="47571-277">Наличие отметки времени определяется с помощью свойства <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> класса <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="47571-277">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="47571-278">WCF всегда сериализует wsse: TimeStamp с wsse: Created и wsse: Expires.</span><span class="sxs-lookup"><span data-stu-id="47571-278">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="47571-279">Если используется подписывание, wsse:TimeStamp всегда подписывается.</span><span class="sxs-lookup"><span data-stu-id="47571-279">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="47571-280">2.2. Порядок защиты</span><span class="sxs-lookup"><span data-stu-id="47571-280">2.2 Protection Order</span></span>  

 <span data-ttu-id="47571-281">WCF поддерживает порядок защиты сообщений "подписывать перед шифрованием" и "шифровать перед подписью" (политика безопасности 1,1).</span><span class="sxs-lookup"><span data-stu-id="47571-281">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="47571-282">По ряду причин рекомендуется использовать порядок «подпись перед шифрованием», в том числе по следующим причинам: если не используется механизм WS-Security 1.1 SignatureConfirmation, сообщения, защищенные в порядке «шифрование перед подписью», подвержены атакам подмены подписи и при подписывании зашифрованного содержимого сложнее производить аудит.</span><span class="sxs-lookup"><span data-stu-id="47571-282">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="47571-283">2.3 Защита сигнатуры</span><span class="sxs-lookup"><span data-stu-id="47571-283">2.3 Signature Protection</span></span>  

 <span data-ttu-id="47571-284">Если используется порядок "шифрование перед сигнатурой", рекомендуется защищать сигнатура, чтобы предотвратить атаки методом подбора для угадывания зашифрованного содержимого или ключа сигнатуры (особенно при использовании пользовательского маркера с ненадежным ключевым материалом).</span><span class="sxs-lookup"><span data-stu-id="47571-284">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="47571-285">2.4 Набор алгоритмов</span><span class="sxs-lookup"><span data-stu-id="47571-285">2.4 Algorithm Suite</span></span>  

 <span data-ttu-id="47571-286">WCF поддерживает все наборы алгоритмов, перечисленные в политике безопасности 1,1.</span><span class="sxs-lookup"><span data-stu-id="47571-286">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="47571-287">2.5 Формирование ключей</span><span class="sxs-lookup"><span data-stu-id="47571-287">2.5 Key Derivation</span></span>  

 <span data-ttu-id="47571-288">WCF использует "ключ наследования для симметричных ключей", как описано в разделе WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="47571-288">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="47571-289">2.6 Подтверждение сигнатуры</span><span class="sxs-lookup"><span data-stu-id="47571-289">2.6 Signature Confirmation</span></span>  

 <span data-ttu-id="47571-290">Подтверждение сигнатуры может использоваться в качестве защиты от атак типа «злоумышленник в середине», чтобы защитить набор подписей.</span><span class="sxs-lookup"><span data-stu-id="47571-290">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="47571-291">2.7 Структура заголовка безопасности</span><span class="sxs-lookup"><span data-stu-id="47571-291">2.7 Security Header Layout</span></span>  

 <span data-ttu-id="47571-292">Каждый режим проверки подлинности описывает определенную структуру заголовка безопасности.</span><span class="sxs-lookup"><span data-stu-id="47571-292">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="47571-293">Элементы в заголовке безопасности полуупорядочены.</span><span class="sxs-lookup"><span data-stu-id="47571-293">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="47571-294">Чтобы определить порядок дочерних элементов заголовка безопасности, в спецификации WS-Security Policy определены следующие режимы структуры заголовка безопасности:</span><span class="sxs-lookup"><span data-stu-id="47571-294">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47571-295">Strict</span><span class="sxs-lookup"><span data-stu-id="47571-295">Strict</span></span>|<span data-ttu-id="47571-296">Элементы добавляются в заголовок безопасности в соответствии с правилами нумерованной структуры, описанными в разделе 7.7.1 спецификаций Security Policy, на основе общего принципа "объявить перед использованием".</span><span class="sxs-lookup"><span data-stu-id="47571-296">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="47571-297">Lax</span><span class="sxs-lookup"><span data-stu-id="47571-297">Lax</span></span>|<span data-ttu-id="47571-298">Элементы добавляются в заголовок безопасности в любом порядке, отвечающем требованиям безопасности сообщений WSS: SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="47571-298">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="47571-299">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="47571-299">LaxTimestampFirst</span></span>|<span data-ttu-id="47571-300">Аналогично Lax, но первым элементом в заголовке безопасности должен быть элемент wsse:Timestamp.</span><span class="sxs-lookup"><span data-stu-id="47571-300">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="47571-301">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="47571-301">LaxTimestampLast</span></span>|<span data-ttu-id="47571-302">Аналогично Lax, но последним элементом в заголовке безопасности должен быть элемент wsse:Timestamp.</span><span class="sxs-lookup"><span data-stu-id="47571-302">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="47571-303">WCF поддерживает все четыре режима для макета заголовка безопасности.</span><span class="sxs-lookup"><span data-stu-id="47571-303">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="47571-304">В приведенных ниже структурах заголовков безопасности и примерах сообщений для режимов проверки подлинности используется режим "Strict".</span><span class="sxs-lookup"><span data-stu-id="47571-304">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="47571-305">2. Общие параметры безопасности сообщений</span><span class="sxs-lookup"><span data-stu-id="47571-305">2. Common Message Security Parameters</span></span>  

 <span data-ttu-id="47571-306">В этом подразделе приведены примеры политик для каждого режима проверки подлинности, а также примеры, показывающие структуру заголовка безопасности в сообщениях, которыми обмениваются клиент и служба.</span><span class="sxs-lookup"><span data-stu-id="47571-306">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="47571-307">6.1 Защита транспорта</span><span class="sxs-lookup"><span data-stu-id="47571-307">6.1 Transport Protection</span></span>  

 <span data-ttu-id="47571-308">WCF предоставляет пять режимов проверки подлинности, использующих защищенный транспорт для защиты сообщений; Усернамеовертранспорт, Цертификатеовертранспорт, Керберосовертранспорт, Иссуедтокеновертранспорт и SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="47571-308">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="47571-309">Эти режимы проверки подлинности построены с использованием привязок транспорта, описанных в спецификации SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="47571-309">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="47571-310">Для режима проверки подлинности UserNameOverTransport маркер UsernameToken является подписанным поддерживающим маркером.</span><span class="sxs-lookup"><span data-stu-id="47571-310">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="47571-311">Для других режимов проверки подлинности этот маркер является подписанным подтверждающим маркером.</span><span class="sxs-lookup"><span data-stu-id="47571-311">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="47571-312">В приложениях C.1.2 и C.1.3 спецификации SecurityPolicy подробно описана структура заголовка безопасности.</span><span class="sxs-lookup"><span data-stu-id="47571-312">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="47571-313">В приведенных ниже примерах заголовки безопасности для определенного режима проверки подлинности показаны со структурой Strict.</span><span class="sxs-lookup"><span data-stu-id="47571-313">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="47571-314">Свойство Derived Keys для маркеров во всех случаях имеет значение "false".</span><span class="sxs-lookup"><span data-stu-id="47571-314">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="47571-315">Различные свойства привязок транспорта имеют следующие значения:</span><span class="sxs-lookup"><span data-stu-id="47571-315">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="47571-316">Отметка времени: true</span><span class="sxs-lookup"><span data-stu-id="47571-316">Timestamp: true</span></span>  
  
 <span data-ttu-id="47571-317">Структура заголовка безопасности: Strict</span><span class="sxs-lookup"><span data-stu-id="47571-317">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="47571-318">Набор алгоритмов: Basic256</span><span class="sxs-lookup"><span data-stu-id="47571-318">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="47571-319">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="47571-319">6.1.1 UsernameOverTransport</span></span>  

 <span data-ttu-id="47571-320">В этом режиме проверка подлинности клиента осуществляется с использованием маркера Username, который доступен на уровне SOAP в качестве подписанного поддерживающего маркера, всегда отправляемого от инициатора получателю.</span><span class="sxs-lookup"><span data-stu-id="47571-320">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="47571-321">Служба проходит проверку подлинности с использованием сертификата X.509 на транспортном уровне.</span><span class="sxs-lookup"><span data-stu-id="47571-321">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="47571-322">Используется привязка транспорта.</span><span class="sxs-lookup"><span data-stu-id="47571-322">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="47571-323">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-323">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="47571-324">Структура заголовка безопасности</span><span class="sxs-lookup"><span data-stu-id="47571-324">Security Header Layout</span></span>  
  
 <span data-ttu-id="47571-325">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-325">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken>  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-326">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-326">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="47571-327">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="47571-327">6.1.2 CertificateOverTransport</span></span>  

 <span data-ttu-id="47571-328">В этом режиме проверка подлинности клиента осуществляется с использованием сертификата X.509, который доступен на уровне SOAP в качестве подтверждающего поддерживающего маркера, всегда отправляемого от инициатора получателю.</span><span class="sxs-lookup"><span data-stu-id="47571-328">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="47571-329">Служба проходит проверку подлинности с использованием сертификата X.509 на транспортном уровне.</span><span class="sxs-lookup"><span data-stu-id="47571-329">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="47571-330">Используется привязка транспорта.</span><span class="sxs-lookup"><span data-stu-id="47571-330">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="47571-331">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-331">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />
              <sp:WssX509V3Token10 />
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="47571-332">Структура заголовка безопасности</span><span class="sxs-lookup"><span data-stu-id="47571-332">Security Header Layout</span></span>  
  
 <span data-ttu-id="47571-333">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-333">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-334">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-334">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="47571-335">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="47571-335">6.1.3 IssuedTokenOverTransport</span></span>  

 <span data-ttu-id="47571-336">В этом режиме проверки подлинности клиент не проходит как таковую проверку подлинности на стороне службы; вместо этого он предоставляет маркер, выданный службой маркеров безопасности (STS) и подтверждает знание общего ключа.</span><span class="sxs-lookup"><span data-stu-id="47571-336">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="47571-337">Выданный маркер доступен на уровне SOAP в качестве подтверждающего поддерживающего маркера, всегда отправляемого от инициатора получателю.</span><span class="sxs-lookup"><span data-stu-id="47571-337">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="47571-338">Служба проходит проверку подлинности с использованием сертификата X.509 на транспортном уровне.</span><span class="sxs-lookup"><span data-stu-id="47571-338">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="47571-339">Используется привязка транспорта.</span><span class="sxs-lookup"><span data-stu-id="47571-339">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="47571-340">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-340">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="47571-341">Структура заголовка безопасности</span><span class="sxs-lookup"><span data-stu-id="47571-341">Security Header Layout</span></span>  
  
 <span data-ttu-id="47571-342">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-342">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-343">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-343">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="47571-344">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="47571-344">6.1.4 KerberosOverTransport</span></span>  

 <span data-ttu-id="47571-345">В этом режиме проверка подлинности клиента на стороне службы осуществляется с использованием билета Kerberos.</span><span class="sxs-lookup"><span data-stu-id="47571-345">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="47571-346">Маркер Kerberos доступен на уровне SOAP в качестве подтверждающего поддерживающего маркера.</span><span class="sxs-lookup"><span data-stu-id="47571-346">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="47571-347">Служба проходит проверку подлинности с использованием сертификата X.509 на транспортном уровне.</span><span class="sxs-lookup"><span data-stu-id="47571-347">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="47571-348">Используется привязка транспорта.</span><span class="sxs-lookup"><span data-stu-id="47571-348">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="47571-349">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-349">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="47571-350">Структура заголовка безопасности</span><span class="sxs-lookup"><span data-stu-id="47571-350">Security Header Layout</span></span>  
  
 <span data-ttu-id="47571-351">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-351">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-352">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-352">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="47571-353">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="47571-353">6.1.5 SspiNegotiatedOverTransport</span></span>  

 <span data-ttu-id="47571-354">В этом режиме для проверки подлинности клиента и сервера используется протокол согласования.</span><span class="sxs-lookup"><span data-stu-id="47571-354">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="47571-355">Если это возможно, используется протокол Kerberos, в противном случае - протокол NTLM.</span><span class="sxs-lookup"><span data-stu-id="47571-355">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="47571-356">Итоговый маркер контекста безопасности доступен на уровне SOAP в качестве подтверждающего поддерживающего маркера, всегда отправляемого от инициатора получателю.</span><span class="sxs-lookup"><span data-stu-id="47571-356">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="47571-357">Служба проходит дополнительную проверку подлинности на транспортном уровне с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="47571-357">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="47571-358">Используется привязка транспорта.</span><span class="sxs-lookup"><span data-stu-id="47571-358">The binding used is a transport binding.</span></span> <span data-ttu-id="47571-359">"SPNEGO" (согласование) описывает, как WCF использует протокол согласования с двоичным кодом SSPI с WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="47571-359">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="47571-360">В этом разделе приведены примеры заголовков безопасности после установления маркера контекста безопасности с помощью подтверждения SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="47571-360">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="47571-361">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-361">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="47571-362">Примеры заголовков безопасности</span><span class="sxs-lookup"><span data-stu-id="47571-362">Security Header Examples</span></span>  

 <span data-ttu-id="47571-363">После установления маркера контекста безопасности с помощью подтверждения SPNEGO при использовании двоичного согласования WS-Trust заголовки безопасности в сообщениях приложения имеют следующую структуру.</span><span class="sxs-lookup"><span data-stu-id="47571-363">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="47571-364">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-364">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-365">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-365">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="47571-366">6.2 Использование сертификатов X.509 для проверки подлинности службы</span><span class="sxs-lookup"><span data-stu-id="47571-366">6.2 Using X.509 Certificates for Service Authentication</span></span>  

 <span data-ttu-id="47571-367">В этом разделе рассматриваются следующие режимы проверки подлинности: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate и IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="47571-367">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="47571-368">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="47571-368">6.2.1 MutualCertificate WSS1.0</span></span>  

 <span data-ttu-id="47571-369">В этом режиме проверка подлинности клиента осуществляется с использованием сертификата X.509, который доступен на уровне SOAP в качестве маркера инициатора.</span><span class="sxs-lookup"><span data-stu-id="47571-369">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="47571-370">Служба также проходит проверку подлинности с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="47571-370">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="47571-371">Используется асимметричная привязка со следующими значениями свойств.</span><span class="sxs-lookup"><span data-stu-id="47571-371">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="47571-372">Маркер инициатора: сертификат X.509 клиента, задан режим включения …/IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="47571-372">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="47571-373">Маркер получателя: сертификат X.509 сервера, задан режим включения …/IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="47571-373">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="47571-374">Защита маркера: False</span><span class="sxs-lookup"><span data-stu-id="47571-374">Token Protection: False</span></span>  
  
 <span data-ttu-id="47571-375">Сигнатуры всего заголовка и тела: True</span><span class="sxs-lookup"><span data-stu-id="47571-375">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="47571-376">Порядок защиты: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="47571-376">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="47571-377">Шифрование подписи: True</span><span class="sxs-lookup"><span data-stu-id="47571-377">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="47571-378">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-378">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-379">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-379">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-380">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-380">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-381">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-381">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-382">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-382">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="47571-383">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-383">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-384">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-384">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="47571-385">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="47571-385">6.2.2 MutualCertificateDuplex</span></span>  

 <span data-ttu-id="47571-386">В этом режиме проверка подлинности клиента осуществляется с использованием сертификата X.509, который доступен на уровне SOAP в качестве маркера инициатора.</span><span class="sxs-lookup"><span data-stu-id="47571-386">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="47571-387">Служба также проходит проверку подлинности с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="47571-387">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="47571-388">Используется асимметричная привязка со следующими значениями свойств.</span><span class="sxs-lookup"><span data-stu-id="47571-388">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="47571-389">Маркер инициатора: сертификат X.509 клиента, задан режим включения …/IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="47571-389">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="47571-390">Маркер получателя: сертификат X.509 сервера, задан режим включения …/IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="47571-390">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="47571-391">Защита маркера: False</span><span class="sxs-lookup"><span data-stu-id="47571-391">Token Protection: False</span></span>  
  
 <span data-ttu-id="47571-392">Сигнатуры всего заголовка и тела: True</span><span class="sxs-lookup"><span data-stu-id="47571-392">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="47571-393">Порядок защиты: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="47571-393">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="47571-394">Шифрование подписи: True</span><span class="sxs-lookup"><span data-stu-id="47571-394">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="47571-395">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-395">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-396">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-396">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-397">Запрос и ответ</span><span class="sxs-lookup"><span data-stu-id="47571-397">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-398">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-398">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-399">Запрос и ответ</span><span class="sxs-lookup"><span data-stu-id="47571-399">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="47571-400">6.2.3 Использование SymmetricBinding с проверкой подлинности службы X.509</span><span class="sxs-lookup"><span data-stu-id="47571-400">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  

 <span data-ttu-id="47571-401">Спецификация "WSS10" обеспечивает ограниченную поддержку сценариев с маркерами X509.</span><span class="sxs-lookup"><span data-stu-id="47571-401">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="47571-402">Например, в этой версии не было способа обеспечить защиту сообщений сигнатурой и шифрованием, используя только маркер X509 службы.</span><span class="sxs-lookup"><span data-stu-id="47571-402">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="47571-403">В спецификации "WSS11" вводится использование EncryptedKey в качестве симметричного маркера.</span><span class="sxs-lookup"><span data-stu-id="47571-403">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="47571-404">Теперь временный ключ, зашифрованный для сертификата X.509 службы, может использоваться для защиты как сообщений запроса, так и сообщений ответа.</span><span class="sxs-lookup"><span data-stu-id="47571-404">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="47571-405">Эта схема используется в режимах проверки подлинности, описанных ниже в разделе 6.4.</span><span class="sxs-lookup"><span data-stu-id="47571-405">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="47571-406">В спецификации WS-SecurityPolicy эта схема описывается с помощью привязки SymmetricBinding с маркером X509 службы в качестве маркера защиты.</span><span class="sxs-lookup"><span data-stu-id="47571-406">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="47571-407">В режимах проверки подлинности AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 и IssuedTokenForCertificate используется аналогичный экземпляр sp:SymmetricBinding со следующими значениями свойств.</span><span class="sxs-lookup"><span data-stu-id="47571-407">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="47571-408">Токен защиты: сертификат X.509 сервера, задан режим включения …/IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="47571-408">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="47571-409">Защита маркера: False</span><span class="sxs-lookup"><span data-stu-id="47571-409">Token Protection: False</span></span>  
  
 <span data-ttu-id="47571-410">Сигнатуры всего заголовка и тела: True</span><span class="sxs-lookup"><span data-stu-id="47571-410">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="47571-411">Порядок защиты: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="47571-411">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="47571-412">Шифрование подписи: True</span><span class="sxs-lookup"><span data-stu-id="47571-412">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="47571-413">Перечисленные выше режимы проверки подлинности различаются только используемыми поддерживающими маркерами.</span><span class="sxs-lookup"><span data-stu-id="47571-413">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="47571-414">В режиме AnonymousForCertificate поддерживающие маркеры отсутствуют, в режиме MutualCertificate (WSS 1.1) сертификат X509 клиента используется как подтверждающие поддерживающие маркеры, в режиме UserNameForCertificate маркер UserName используется как подписанный поддерживающий маркер, а в режиме IssuedTokenForCertificate выданный маркер используется как подтверждающий поддерживающий маркер.</span><span class="sxs-lookup"><span data-stu-id="47571-414">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="47571-415">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-415">Policy</span></span>  
  
 <span data-ttu-id="47571-416">Симметричная привязка</span><span class="sxs-lookup"><span data-stu-id="47571-416">Symmetric Binding</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:RequireThumbprintReference />
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
          <sp:RequireSignatureConfirmation />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="47571-417">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="47571-417">6.2.4 AnonymousForCertificate</span></span>  

 <span data-ttu-id="47571-418">В этом режиме проверки подлинности клиент является анонимным, а проверка подлинности службы осуществляется с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="47571-418">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="47571-419">Используется экземпляр симметричной привязки, как описано в разделе 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="47571-419">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="47571-420">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-420">Policy</span></span>  
  
 <span data-ttu-id="47571-421">Сведения о привязке см. в пункте «Политика» раздела 6.2.3</span><span class="sxs-lookup"><span data-stu-id="47571-421">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-422">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-422">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-423">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-423">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-424">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-424">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-425">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-425">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-426">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-426">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-427">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-427">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="47571-428">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="47571-428">6.2.5 UserNameForCertificate</span></span>  

 <span data-ttu-id="47571-429">В этом режиме проверка подлинности клиента в службе осуществляется с использованием маркера Username, который доступен на уровне SOAP в качестве подписанного поддерживающего маркера.</span><span class="sxs-lookup"><span data-stu-id="47571-429">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="47571-430">Проверка подлинности службы на стороне клиента осуществляется с помощью сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="47571-430">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="47571-431">Используется симметричная привязка, в которой маркер защиты создан с помощью ключа клиента и зашифрован с помощью открытого ключа службы.</span><span class="sxs-lookup"><span data-stu-id="47571-431">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="47571-432">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-432">Policy</span></span>  
  
 <span data-ttu-id="47571-433">Сведения о привязке см. в пункте «Политика» раздела 6.2.3</span><span class="sxs-lookup"><span data-stu-id="47571-433">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="47571-434">Подписанный поддерживающий маркер</span><span class="sxs-lookup"><span data-stu-id="47571-434">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-435">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-435">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-436">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-436">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-437">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-437">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-438">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-438">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-439">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-439">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-440">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-440">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="47571-441">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="47571-441">6.2.6 MutualCertificate (WSS 1.1)</span></span>  

 <span data-ttu-id="47571-442">В этом режиме проверка подлинности клиента осуществляется с использованием сертификата X.509, который доступен на уровне SOAP в качестве подтверждающего поддерживающего маркера.</span><span class="sxs-lookup"><span data-stu-id="47571-442">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="47571-443">Служба также проходит проверку подлинности с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="47571-443">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="47571-444">Используется симметричная привязка, в которой маркер защиты создан с помощью ключа клиента и зашифрован с помощью открытого ключа службы.</span><span class="sxs-lookup"><span data-stu-id="47571-444">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="47571-445">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-445">Policy</span></span>  
  
 <span data-ttu-id="47571-446">Сведения о привязке см. в пункте «Политика» раздела 6.2.3</span><span class="sxs-lookup"><span data-stu-id="47571-446">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="47571-447">Подтверждающий поддерживающий маркер</span><span class="sxs-lookup"><span data-stu-id="47571-447">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />
        <sp:WssX509V3Token10 />
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-448">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-448">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-449">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-449">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-450">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-450">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-451">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-451">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-452">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-452">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-453">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-453">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="47571-454">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="47571-454">6.2.7 IssuedTokenForCertificate</span></span>  

 <span data-ttu-id="47571-455">В этом режиме проверки подлинности клиент не проходит как таковую проверку подлинности на стороне службы; вместо этого он предоставляет маркер, выданный службой маркеров безопасности и подтверждает знание общего ключа.</span><span class="sxs-lookup"><span data-stu-id="47571-455">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="47571-456">Выданный маркер доступен на уровне SOAP в качестве подтверждающего поддерживающего маркера.</span><span class="sxs-lookup"><span data-stu-id="47571-456">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="47571-457">Проверка подлинности службы на стороне клиента осуществляется с помощью сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="47571-457">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="47571-458">Используется симметричная привязка, в которой маркер защиты создан с помощью ключа клиента и зашифрован с помощью открытого ключа службы.</span><span class="sxs-lookup"><span data-stu-id="47571-458">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="47571-459">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-459">Policy</span></span>  
  
 <span data-ttu-id="47571-460">Сведения о привязке см. в пункте «Политика» раздела 6.2.3</span><span class="sxs-lookup"><span data-stu-id="47571-460">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="47571-461">Подтверждающий поддерживающий маркер</span><span class="sxs-lookup"><span data-stu-id="47571-461">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />
       <sp:RequireInternalReference />
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-462">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-462">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-463">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-463">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-464">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-464">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-465">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-465">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-466">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-466">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-467">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-467">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## <a name="63-kerberos"></a><span data-ttu-id="47571-468">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="47571-468">6.3 Kerberos</span></span>  

 <span data-ttu-id="47571-469">В этом режиме проверка подлинности клиента на стороне службы осуществляется с использованием билета Kerberos.</span><span class="sxs-lookup"><span data-stu-id="47571-469">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="47571-470">Этот же билет обеспечивает проверку подлинности сервера.</span><span class="sxs-lookup"><span data-stu-id="47571-470">That same ticket also provides server authentication.</span></span> <span data-ttu-id="47571-471">Используется симметричная привязка со следующими свойствами.</span><span class="sxs-lookup"><span data-stu-id="47571-471">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="47571-472">Токен защиты: билет kerberos, задан режим включения …/IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="47571-472">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="47571-473">Защита маркера: False</span><span class="sxs-lookup"><span data-stu-id="47571-473">Token Protection: False</span></span>  
  
 <span data-ttu-id="47571-474">Сигнатуры всего заголовка и тела: True</span><span class="sxs-lookup"><span data-stu-id="47571-474">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="47571-475">Порядок защиты: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="47571-475">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="47571-476">Шифрование подписи: True</span><span class="sxs-lookup"><span data-stu-id="47571-476">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="47571-477">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-477">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:WssGssKerberosV5ApReqToken11 />
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-478">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-478">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-479">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-479">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-480">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-480">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-481">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-481">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-482">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-482">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-483">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-483">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="47571-484">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="47571-484">6.4 IssuedToken</span></span>  

 <span data-ttu-id="47571-485">В этом режиме проверки подлинности клиент не проходит как таковую проверку подлинности на стороне службы; вместо этого клиент предоставляет маркер, выданный службой маркеров безопасности и подтверждает знание общего ключа.</span><span class="sxs-lookup"><span data-stu-id="47571-485">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="47571-486">Служба не проходит как таковую проверку подлинности на стороне клиента, но служба маркеров безопасности шифрует общий ключ как часть выдаваемого маркера, чтобы только служба могла расшифровать этот ключ.</span><span class="sxs-lookup"><span data-stu-id="47571-486">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="47571-487">Используется симметричная привязка со следующими свойствами.</span><span class="sxs-lookup"><span data-stu-id="47571-487">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="47571-488">Токен защиты: выданный токен, задан режим включения .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="47571-488">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="47571-489">Защита маркера: False</span><span class="sxs-lookup"><span data-stu-id="47571-489">Token Protection: False</span></span>  
  
 <span data-ttu-id="47571-490">Сигнатуры всего заголовка и тела: True</span><span class="sxs-lookup"><span data-stu-id="47571-490">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="47571-491">Порядок защиты: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="47571-491">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="47571-492">Шифрование подписи: True</span><span class="sxs-lookup"><span data-stu-id="47571-492">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="47571-493">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-493">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:RequireInternalReference />
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-494">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-494">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-495">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-495">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-496">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-496">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-497">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-497">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-498">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-498">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-499">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-499">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="47571-500">6.5 Использование SslNegotiated для проверки подлинности службы</span><span class="sxs-lookup"><span data-stu-id="47571-500">6.5 Using SslNegotiated for Service Authentication</span></span>  

 <span data-ttu-id="47571-501">В этом разделе рассматривается группа режимов проверки подлинности, в которых используется симметричная привязка с маркером защиты, являющимся маркером контекста безопасности в соответствии со спецификацией WS-SecureConversation (WS-SC), значение ключа которого согласовывается путем выполнения протокола TLS с помощью сообщений RST/RSTR спецификации WS-Trust (WS-T).</span><span class="sxs-lookup"><span data-stu-id="47571-501">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="47571-502">Сведения о реализации подтверждения TLS с помощью спецификации WS-Trust приведены в спецификации TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="47571-502">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="47571-503">В приведенных ниже примерах сообщений предполагается, что маркер контекста безопасности со связанным контекстом безопасности уже установлен путем подтверждения.</span><span class="sxs-lookup"><span data-stu-id="47571-503">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="47571-504">Используется симметричная привязка со следующими свойствами.</span><span class="sxs-lookup"><span data-stu-id="47571-504">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="47571-505">Токен защиты: SslContextToken, задан режим включения .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="47571-505">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="47571-506">Защита маркера: False</span><span class="sxs-lookup"><span data-stu-id="47571-506">Token Protection: False</span></span>  
  
 <span data-ttu-id="47571-507">Сигнатуры всего заголовка и тела: True</span><span class="sxs-lookup"><span data-stu-id="47571-507">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="47571-508">Порядок защиты: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="47571-508">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="47571-509">Шифрование подписи: True</span><span class="sxs-lookup"><span data-stu-id="47571-509">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="47571-510">6.5.1 Политика для проверки подлинности службы SslNegotiated</span><span class="sxs-lookup"><span data-stu-id="47571-510">6.5.1 Policy for SslNegotiated service authentication</span></span>  

 <span data-ttu-id="47571-511">Политики для всех режимов проверки подлинности в этом разделе аналогичны и различаются только определенными используемыми подписанными поддерживающими или подтверждающими маркерами.</span><span class="sxs-lookup"><span data-stu-id="47571-511">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient'>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="47571-512">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="47571-512">6.5.2 AnonymousForSslNegotiated</span></span>  

 <span data-ttu-id="47571-513">В этом режиме проверки подлинности клиент является анонимным, а проверка подлинности службы осуществляется с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="47571-513">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="47571-514">Используется экземпляр симметричной привязки, как описано выше в разделе 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="47571-514">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="47571-515">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-515">Policy</span></span>  
  
 <span data-ttu-id="47571-516">Сведения о привязке см. в пункте «Политика» раздела 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="47571-516">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-517">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-517">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-518">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-518">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-519">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-519">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-520">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-520">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-521">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-521">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-522">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-522">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="47571-523">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="47571-523">6.5.3 UserNameForSslNegotiated</span></span>  

 <span data-ttu-id="47571-524">В этом режиме проверка подлинности клиента осуществляется с использованием маркера Username, который доступен на уровне SOAP в качестве подписанного поддерживающего маркера.</span><span class="sxs-lookup"><span data-stu-id="47571-524">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="47571-525">Служба проходит проверку подлинности с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="47571-525">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="47571-526">Используется экземпляр симметричной привязки, как описано в разделе 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="47571-526">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="47571-527">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-527">Policy</span></span>  
  
 <span data-ttu-id="47571-528">Сведения о привязке см. в разделе 6.5.1</span><span class="sxs-lookup"><span data-stu-id="47571-528">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="47571-529">Подписанный поддерживающий маркер</span><span class="sxs-lookup"><span data-stu-id="47571-529">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-530">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-530">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-531">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-531">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-532">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-532">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-533">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-533">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-534">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-534">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-535">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-535">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="47571-536">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="47571-536">6.5.4 IssuedTokenForSslNegotiated</span></span>  

 <span data-ttu-id="47571-537">В этом режиме проверки подлинности клиент не проходит как таковую проверку подлинности на стороне службы; вместо этого он предоставляет маркер, выданный службой маркеров безопасности и подтверждает знание общего ключа.</span><span class="sxs-lookup"><span data-stu-id="47571-537">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="47571-538">Выданный маркер доступен на уровне SOAP в качестве подтверждающего поддерживающего маркера.</span><span class="sxs-lookup"><span data-stu-id="47571-538">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="47571-539">Служба проходит проверку подлинности с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="47571-539">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="47571-540">Используется экземпляр симметричной привязки, как описано выше в разделе 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="47571-540">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="47571-541">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-541">Policy</span></span>  
  
 <span data-ttu-id="47571-542">Сведения о привязке см. в разделе 6.5.1</span><span class="sxs-lookup"><span data-stu-id="47571-542">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="47571-543">Подтверждающий поддерживающий маркер</span><span class="sxs-lookup"><span data-stu-id="47571-543">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />
        <sp:RequireInternalReference />
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-544">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-544">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-545">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-545">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-546">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-546">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-547">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-547">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-548">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-548">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-549">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-549">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="47571-550">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="47571-550">6.5.5 MutualSslNegotiated</span></span>  

 <span data-ttu-id="47571-551">В этом режиме проверка подлинности клиента и службы осуществляется с использованием сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="47571-551">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="47571-552">Используется экземпляр симметричной привязки, как описано выше в разделе 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="47571-552">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="47571-553">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-553">Policy</span></span>  
  
 <span data-ttu-id="47571-554">Сведения о привязке см. в разделе 6.5.1</span><span class="sxs-lookup"><span data-stu-id="47571-554">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="47571-555">Подтверждающий поддерживающий маркер</span><span class="sxs-lookup"><span data-stu-id="47571-555">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />
        <sp:WssX509V3Token10 />
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-556">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-556">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-557">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-557">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-558">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-558">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-559">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-559">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-560">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-560">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-561">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-561">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="47571-562">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="47571-562">6.6 SspiNegotiated</span></span>  

 <span data-ttu-id="47571-563">В этом режиме для проверки подлинности клиента и сервера используется протокол согласования.</span><span class="sxs-lookup"><span data-stu-id="47571-563">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="47571-564">Если это возможно, используется протокол Kerberos, в противном случае - протокол NTLM.</span><span class="sxs-lookup"><span data-stu-id="47571-564">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="47571-565">Используется симметричная привязка со следующими свойствами.</span><span class="sxs-lookup"><span data-stu-id="47571-565">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="47571-566">Токен защиты: SpnegoContextToken, задан режим включения .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="47571-566">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="47571-567">Защита маркера: False</span><span class="sxs-lookup"><span data-stu-id="47571-567">Token Protection: False</span></span>  
  
 <span data-ttu-id="47571-568">Сигнатуры всего заголовка и тела: True</span><span class="sxs-lookup"><span data-stu-id="47571-568">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="47571-569">Порядок защиты: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="47571-569">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="47571-570">Шифрование подписи: True</span><span class="sxs-lookup"><span data-stu-id="47571-570">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="47571-571">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-571">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-572">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-572">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-573">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-573">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-574">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-574">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-575">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-575">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-576">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-576">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-577">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-577">Response</span></span>  
  
```xml  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="67-secureconversation"></a><span data-ttu-id="47571-578">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="47571-578">6.7 SecureConversation</span></span>  

 <span data-ttu-id="47571-579">Используется симметричная привязка, в которой маркером защиты является маркер контекста безопасности в соответствии со спецификацией WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="47571-579">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="47571-580">Согласование маркера контекста безопасности производится с использованием спецификации WS-Trust (WS-Trust) или WS-SecureConversation (WS-SC) в соответствии с вложенной привязкой, которая сама является симметричной привязкой, использующей протокол согласования.</span><span class="sxs-lookup"><span data-stu-id="47571-580">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="47571-581">При возможности в протоколе согласования для проверки подлинности клиента и сервера используется протокол Kerberos.</span><span class="sxs-lookup"><span data-stu-id="47571-581">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="47571-582">Если использование протокола Kerberos невозможно, используется резервный протокол NTLM.</span><span class="sxs-lookup"><span data-stu-id="47571-582">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="47571-583">Политика</span><span class="sxs-lookup"><span data-stu-id="47571-583">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />
                          <sp:EncryptSignature />
                          <sp:OnlySignEntireHeadersAndBody />
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />
                          <sp:MustSupportRefIssuerSerial />
                          <sp:MustSupportRefThumbprint />
                          <sp:MustSupportRefEncryptedKey />
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />
                          <sp:RequireClientEntropy />
                          <sp:RequireServerEntropy />
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="47571-584">Примеры заголовков безопасности: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="47571-584">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="47571-585">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-585">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-586">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-586">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="47571-587">Примеры заголовков безопасности: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="47571-587">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="47571-588">Запрос</span><span class="sxs-lookup"><span data-stu-id="47571-588">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="47571-589">Ответ</span><span class="sxs-lookup"><span data-stu-id="47571-589">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```
