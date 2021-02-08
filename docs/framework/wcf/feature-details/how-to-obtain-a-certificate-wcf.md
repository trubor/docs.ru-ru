---
description: Дополнительные сведения о том, как получить сертификат (WCF).
title: Практическое руководство. Получение сертификата (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 2ca40c9646bbdeb6c29a94966fd24ec00d9b5306
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793705"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="8838f-103">Практическое руководство. Получение сертификата (WCF)</span><span class="sxs-lookup"><span data-stu-id="8838f-103">How to: Obtain a Certificate (WCF)</span></span>

<span data-ttu-id="8838f-104">Чтобы использовать любую из функций Windows Communication Foundation (WCF), использующих сертификаты X. 509, сначала нужно получить сертификаты.</span><span class="sxs-lookup"><span data-stu-id="8838f-104">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="8838f-105">Получение сертификата X.509</span><span class="sxs-lookup"><span data-stu-id="8838f-105">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="8838f-106">Выберите один из следующих вариантов.</span><span class="sxs-lookup"><span data-stu-id="8838f-106">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="8838f-107">Приобретите сертификат в центре сертификации, например VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="8838f-107">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="8838f-108">Создайте собственную службу сертификатов и настройте ее так, чтобы центр сертификации подписывал сертификаты.</span><span class="sxs-lookup"><span data-stu-id="8838f-108">Set up your own certificate service and have a certification authority sign the certificates.</span></span> <span data-ttu-id="8838f-109">Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter и Windows 2000 Datacenter Server включают службы сертификации, поддерживающие инфраструктуру открытых ключей (PKI).</span><span class="sxs-lookup"><span data-stu-id="8838f-109">Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="8838f-110">В Windows Server 2008 для управления центром сертификации используется [Active Directory роль служб сертификации](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) .</span><span class="sxs-lookup"><span data-stu-id="8838f-110">In Windows Server 2008, use the [Active Directory Certificate Services](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="8838f-111">Создайте собственную службу сертификатов и не настраивайте подпись сертификатов.</span><span class="sxs-lookup"><span data-stu-id="8838f-111">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8838f-112">Независимо от того, какой способ выбран, получатель запроса SOAP, который содержит сертификат X.509, должен доверять сертификату X.509.</span><span class="sxs-lookup"><span data-stu-id="8838f-112">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="8838f-113">Это означает, что сертификат X.509 или издатель в цепи сертификатов находится в хранилище сертификатов "Доверенные лица" и сертификат X.509 не помещен в хранилище ненадежных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="8838f-113">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8838f-114">См. также</span><span class="sxs-lookup"><span data-stu-id="8838f-114">See also</span></span>

- [<span data-ttu-id="8838f-115">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="8838f-115">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="8838f-116">Практическое руководство. Создание временных сертификатов для использования во время разработки</span><span class="sxs-lookup"><span data-stu-id="8838f-116">How to: Create Temporary Certificates for Use During Development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
