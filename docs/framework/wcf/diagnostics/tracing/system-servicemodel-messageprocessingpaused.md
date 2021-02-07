---
description: 'Дополнительные сведения: System. ServiceModel. Мессажепроцессингпаусед'
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 77e4742bc5617904136b2ddd9cb90fe886d38b10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716185"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="b9b6e-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="b9b6e-103">System.ServiceModel.MessageProcessingPaused</span></span>

<span data-ttu-id="b9b6e-104">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="b9b6e-104">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="b9b6e-105">Описание</span><span class="sxs-lookup"><span data-stu-id="b9b6e-105">Description</span></span>  

 <span data-ttu-id="b9b6e-106">При обработке сообщения произошло переключение потоков.</span><span class="sxs-lookup"><span data-stu-id="b9b6e-106">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="b9b6e-107">Обработка сообщения может быть приостановлена по следующим причинам:</span><span class="sxs-lookup"><span data-stu-id="b9b6e-107">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="b9b6e-108">ConcurrencyMode является единственным или реентерабельным; служба обрабатывает другое сообщение.</span><span class="sxs-lookup"><span data-stu-id="b9b6e-108">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="b9b6e-109">Транзакция разрешена; служба обрабатывает другую транзакцию.</span><span class="sxs-lookup"><span data-stu-id="b9b6e-109">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="b9b6e-110">Контекст синхронизации устарел.</span><span class="sxs-lookup"><span data-stu-id="b9b6e-110">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b6e-111">См. также</span><span class="sxs-lookup"><span data-stu-id="b9b6e-111">See also</span></span>

- [<span data-ttu-id="b9b6e-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="b9b6e-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="b9b6e-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="b9b6e-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b9b6e-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="b9b6e-114">Administration and Diagnostics</span></span>](../index.md)
