---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. Препаремессажеретри'
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: 7555336f1082eb097017f9440015f6ab201cdeae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770785"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="7798a-103">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="7798a-103">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>

<span data-ttu-id="7798a-104">Повторная попытка сообщения подготовки была отправлена участнику, который не отвечает.</span><span class="sxs-lookup"><span data-stu-id="7798a-104">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7798a-105">Описание</span><span class="sxs-lookup"><span data-stu-id="7798a-105">Description</span></span>  

 <span data-ttu-id="7798a-106">Трассируется, потребовалось ли локальному диспетчеру транзакций заново отправить сообщение подготовки подчиненному участнику, так как за заданное время не был получен отклик.</span><span class="sxs-lookup"><span data-stu-id="7798a-106">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7798a-107">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="7798a-107">Troubleshooting</span></span>  

 <span data-ttu-id="7798a-108">Рассмотрите потенциальные проблемы с сетью или продуктом, которые могут препятствовать своевременной доставке отклика.</span><span class="sxs-lookup"><span data-stu-id="7798a-108">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="7798a-109">Если таких сообщений много, это может указывать на проблемы инфраструктуры или чрезмерно большое время отклика.</span><span class="sxs-lookup"><span data-stu-id="7798a-109">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="7798a-110">Обе проблемы могут значительно снизить пропускную способность транзакций в системе.</span><span class="sxs-lookup"><span data-stu-id="7798a-110">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7798a-111">См. также</span><span class="sxs-lookup"><span data-stu-id="7798a-111">See also</span></span>

- [<span data-ttu-id="7798a-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="7798a-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="7798a-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="7798a-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7798a-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="7798a-114">Administration and Diagnostics</span></span>](../index.md)
