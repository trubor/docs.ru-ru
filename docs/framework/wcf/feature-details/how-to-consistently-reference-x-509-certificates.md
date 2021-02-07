---
description: См. Дополнительные сведения о том, как согласованно ссылаться на сертификаты X. 509.
title: Практическое руководство. Согласованное обращение к сертификатам X.509
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: cdf5535373490e8cb78e28a8fc0cf881df40e041
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734806"
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="98409-103">Практическое руководство. Согласованное обращение к сертификатам X.509</span><span class="sxs-lookup"><span data-stu-id="98409-103">How to: Consistently Reference X.509 Certificates</span></span>

<span data-ttu-id="98409-104">Существует несколько способов идентификации сертификата: с помощью хэша сертификата, имени поставщика и серийного номера, а также идентификатора ключа субъекта (SKI).</span><span class="sxs-lookup"><span data-stu-id="98409-104">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="98409-105">Идентификатор ключа субъекта (SKI) обеспечивает уникальную идентификацию открытого ключа субъекта сертификата, поэтому он часто используется при работе с цифровой подписью XML.</span><span class="sxs-lookup"><span data-stu-id="98409-105">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="98409-106">Значение SKI обычно является частью сертификата X. 509 как *расширение сертификата x. 509*.</span><span class="sxs-lookup"><span data-stu-id="98409-106">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> <span data-ttu-id="98409-107">Windows Communication Foundation (WCF) имеет *стиль ссылок* по умолчанию, который использует поставщик и серийный номер, если в сертификате отсутствует расширение Ski.</span><span class="sxs-lookup"><span data-stu-id="98409-107">Windows Communication Foundation (WCF) has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="98409-108">Если в сертификате имеется расширение идентификатора ключа субъекта (SKI), стиль ссылки по умолчанию использует его для указания на сертификат.</span><span class="sxs-lookup"><span data-stu-id="98409-108">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="98409-109">Если при разработке приложения вы переходите от использования сертификатов, которые не используют расширение SKI, для сертификатов, использующих расширение SKI, также изменяется стиль ссылок, используемый в сообщениях, созданных WCF.</span><span class="sxs-lookup"><span data-stu-id="98409-109">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in WCF-generated messages also changes.</span></span>  
  
 <span data-ttu-id="98409-110">Если требуется согласованный стиль ссылки независимо от наличия расширения идентификатора ключа субъекта (SKI), необходимый стиль ссылки можно настроить, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="98409-110">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98409-111">Пример</span><span class="sxs-lookup"><span data-stu-id="98409-111">Example</span></span>  

 <span data-ttu-id="98409-112">В следующем примере кода создается пользовательский элемент привязки безопасности, использующий единый согласованный стиль ссылки с именем издателя и серийным номером.</span><span class="sxs-lookup"><span data-stu-id="98409-112">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98409-113">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="98409-113">Compiling the Code</span></span>  

 <span data-ttu-id="98409-114">Для компиляции кода требуются следующие пространства имен.</span><span class="sxs-lookup"><span data-stu-id="98409-114">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="98409-115">См. также</span><span class="sxs-lookup"><span data-stu-id="98409-115">See also</span></span>

- [<span data-ttu-id="98409-116">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="98409-116">Working with Certificates</span></span>](working-with-certificates.md)
