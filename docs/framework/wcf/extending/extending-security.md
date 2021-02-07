---
description: 'Дополнительные сведения: расширение безопасности'
title: Расширение безопасности
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 8dd514e16106ac5cdae072d92c7de66cefd39fe4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685729"
---
# <a name="extending-security"></a><span data-ttu-id="7cbe7-103">Расширение безопасности</span><span class="sxs-lookup"><span data-stu-id="7cbe7-103">Extending Security</span></span>

<span data-ttu-id="7cbe7-104">Для поддержки новых типов утверждений и пользовательских маркеров можно расширить инфраструктуру безопасности Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7cbe7-104">To accommodate new claim types and custom tokens, you can extend the security infrastructure of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="7cbe7-105">Это подробно описывается в следующих подразделах.</span><span class="sxs-lookup"><span data-stu-id="7cbe7-105">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7cbe7-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="7cbe7-106">In This Section</span></span>  
  
 [<span data-ttu-id="7cbe7-107">Пользовательские учетные данные и проверка учетных данных</span><span class="sxs-lookup"><span data-stu-id="7cbe7-107">Custom Credential and Credential Validation</span></span>](custom-credential-and-credential-validation.md)  
 <span data-ttu-id="7cbe7-108">Рассматривается, как модель удостоверения используется при проверке пользовательских учетных данных.</span><span class="sxs-lookup"><span data-stu-id="7cbe7-108">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="7cbe7-109">Пользовательские маркеры</span><span class="sxs-lookup"><span data-stu-id="7cbe7-109">Custom Tokens</span></span>](custom-tokens.md)  
 <span data-ttu-id="7cbe7-110">Маркеры, выдаваемые службой маркеров безопасности (STS), - обычно маркеры SAML.</span><span class="sxs-lookup"><span data-stu-id="7cbe7-110">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="7cbe7-111">В этом разделе описывается, как создать тип пользовательского маркера.</span><span class="sxs-lookup"><span data-stu-id="7cbe7-111">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="7cbe7-112">Пользовательская авторизация</span><span class="sxs-lookup"><span data-stu-id="7cbe7-112">Custom Authorization</span></span>](custom-authorization.md)  
 <span data-ttu-id="7cbe7-113">Объясняется, как реализовать пользовательскую авторизацию.</span><span class="sxs-lookup"><span data-stu-id="7cbe7-113">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="7cbe7-114">Переопределение идентификатора службы для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="7cbe7-114">Overriding the Identity of a Service for Authentication</span></span>](overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="7cbe7-115">Описывается, как переопределить идентификацию службы для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="7cbe7-115">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="7cbe7-116">Практическое руководство. Создание пользовательского средства проверки идентификации клиентов</span><span class="sxs-lookup"><span data-stu-id="7cbe7-116">How to: Create a Custom Client Identity Verifier</span></span>](how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="7cbe7-117">Демонстрирует, как проверить идентификацию пользовательской конечной точки.</span><span class="sxs-lookup"><span data-stu-id="7cbe7-117">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="7cbe7-118">Практическое руководство. Использование отдельных сертификатов X.509 для подписывания и шифрования</span><span class="sxs-lookup"><span data-stu-id="7cbe7-118">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="7cbe7-119">Обычно сообщения подписываются и шифруются одним сертификатом.</span><span class="sxs-lookup"><span data-stu-id="7cbe7-119">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="7cbe7-120">В этом разделе объясняется, как при необходимости использовать два сертификата.</span><span class="sxs-lookup"><span data-stu-id="7cbe7-120">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="7cbe7-121">Практическое руководство. Изменение поставщика служб шифрования для закрытого ключа сертификата X.509</span><span class="sxs-lookup"><span data-stu-id="7cbe7-121">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="7cbe7-122">Объясняет, как изменить поставщик служб шифрования, используемый для предоставления закрытого ключа сертификата X. 509, и как интегрировать поставщик в платформу Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7cbe7-122">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7cbe7-123">Справочник</span><span class="sxs-lookup"><span data-stu-id="7cbe7-123">Reference</span></span>  

 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="7cbe7-124">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="7cbe7-124">Related Sections</span></span>  

 [<span data-ttu-id="7cbe7-125">Безопасность</span><span class="sxs-lookup"><span data-stu-id="7cbe7-125">Security</span></span>](../feature-details/security.md)  
  
 [<span data-ttu-id="7cbe7-126">Базовое программирование для WCF</span><span class="sxs-lookup"><span data-stu-id="7cbe7-126">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="7cbe7-127">См. также</span><span class="sxs-lookup"><span data-stu-id="7cbe7-127">See also</span></span>

- [<span data-ttu-id="7cbe7-128">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="7cbe7-128">Security Overview</span></span>](../feature-details/security-overview.md)
