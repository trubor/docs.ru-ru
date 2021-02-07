---
description: 'Дополнительные сведения: пользовательские учетные данные и проверка учетных данных'
title: Пользовательские учетные данные и проверка учетных данных
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: f1ceb8cf46cca01ac31faeb9485cbeb6c8663d31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735313"
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="be37a-103">Пользовательские учетные данные и проверка учетных данных</span><span class="sxs-lookup"><span data-stu-id="be37a-103">Custom Credential and Credential Validation</span></span>

<span data-ttu-id="be37a-104">Безопасность в Windows Communication Foundation (WCF) основана на обмене учетными данными между службами и клиентами.</span><span class="sxs-lookup"><span data-stu-id="be37a-104">Security in Windows Communication Foundation (WCF) is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="be37a-105">Большинство сценариев обеспечения безопасности можно реализовать с использованием стандартных типов учетных данных, например Windows (Kerberos), имен пользователей и паролей, а также сертификатов.</span><span class="sxs-lookup"><span data-stu-id="be37a-105">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="be37a-106">Если требуются учетные данные новых типов, в приведенных ниже разделах можно найти сведения о том, как обрабатывать и проверять эти типы.</span><span class="sxs-lookup"><span data-stu-id="be37a-106">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="be37a-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="be37a-107">In This Section</span></span>  

 [<span data-ttu-id="be37a-108">Практическое руководство. Создание службы, использующей пользовательский проверяющий элемент управления для сертификатов</span><span class="sxs-lookup"><span data-stu-id="be37a-108">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="be37a-109">Объясняется, как настроить проверку WCF путем наследования от <xref:System.IdentityModel.Selectors.X509CertificateValidator> класса.</span><span class="sxs-lookup"><span data-stu-id="be37a-109">Explains how to customize WCF validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="be37a-110">Пошаговое руководство. Создание пользовательских учетных данных для клиента и службы</span><span class="sxs-lookup"><span data-stu-id="be37a-110">Walkthrough: Creating Custom Client and Service Credentials</span></span>](walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="be37a-111">Демонстрирует, как расширить <xref:System.ServiceModel.Description.ClientCredentials> классы и <xref:System.ServiceModel.Description.ServiceCredentials> для размещения новых типов учетных данных.</span><span class="sxs-lookup"><span data-stu-id="be37a-111">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="be37a-112">Это первый раздел в серии, посвященной созданию пользовательских типов учетных данных.</span><span class="sxs-lookup"><span data-stu-id="be37a-112">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="be37a-113">Практическое руководство. Создание поставщика пользовательских маркеров безопасности</span><span class="sxs-lookup"><span data-stu-id="be37a-113">How to: Create a Custom Security Token Provider</span></span>](how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="be37a-114">Создание поставщика маркеров безопасности для обработки новых типов учетных данных и возврата новых маркеров для учетных данных.</span><span class="sxs-lookup"><span data-stu-id="be37a-114">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="be37a-115">Это второй раздел в данной серии.</span><span class="sxs-lookup"><span data-stu-id="be37a-115">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="be37a-116">Практическое руководство. Создание пользовательской структуры проверки подлинности маркера безопасности</span><span class="sxs-lookup"><span data-stu-id="be37a-116">How to: Create a Custom Security Token Authenticator</span></span>](how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="be37a-117">Создание пользовательских структур проверки подлинности для проверки подлинности учетных данных новых типов.</span><span class="sxs-lookup"><span data-stu-id="be37a-117">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="be37a-118">Это третий раздел в данной серии.</span><span class="sxs-lookup"><span data-stu-id="be37a-118">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="be37a-119">Справочник</span><span class="sxs-lookup"><span data-stu-id="be37a-119">Reference</span></span>  

 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="be37a-120">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="be37a-120">Related Sections</span></span>  

 [<span data-ttu-id="be37a-121">Аутентификация</span><span class="sxs-lookup"><span data-stu-id="be37a-121">Authentication</span></span>](../feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="be37a-122">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="be37a-122">Federation and Issued Tokens</span></span>](../feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="be37a-123">Авторизация</span><span class="sxs-lookup"><span data-stu-id="be37a-123">Authorization</span></span>](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="be37a-124">См. также</span><span class="sxs-lookup"><span data-stu-id="be37a-124">See also</span></span>

- [<span data-ttu-id="be37a-125">Безопасность</span><span class="sxs-lookup"><span data-stu-id="be37a-125">Security</span></span>](../feature-details/security.md)
