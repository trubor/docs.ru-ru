---
description: 'Дополнительные сведения: System. ServiceModel. Channels. Хттпсклиентцертификатенотпресент'
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 1bca23915a55561c76b73c6b96750f324cb0e4dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99654490"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="84cc3-103">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="84cc3-103">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>

<span data-ttu-id="84cc3-104">Требуется сертификат клиента.</span><span class="sxs-lookup"><span data-stu-id="84cc3-104">Client certificate is required.</span></span> <span data-ttu-id="84cc3-105">В запросе не было найдено ни одного сертификата.</span><span class="sxs-lookup"><span data-stu-id="84cc3-105">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="84cc3-106">Описание</span><span class="sxs-lookup"><span data-stu-id="84cc3-106">Description</span></span>  

 <span data-ttu-id="84cc3-107">Эта трассировка показывает, что прослушиватель HTTPS получил запрос HTTPS, который не был связан с сертификатом клиента.</span><span class="sxs-lookup"><span data-stu-id="84cc3-107">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="84cc3-108">Так как прослушиватель был настроен на требование сертификатов клиента от всех запросов HTTPS, прослушивателю не удалось проверить подлинность клиента.</span><span class="sxs-lookup"><span data-stu-id="84cc3-108">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84cc3-109">См. также</span><span class="sxs-lookup"><span data-stu-id="84cc3-109">See also</span></span>

- [<span data-ttu-id="84cc3-110">Трассировка</span><span class="sxs-lookup"><span data-stu-id="84cc3-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="84cc3-111">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="84cc3-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="84cc3-112">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="84cc3-112">Administration and Diagnostics</span></span>](../index.md)
