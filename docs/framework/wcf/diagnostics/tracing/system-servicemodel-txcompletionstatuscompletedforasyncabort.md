---
description: 'Дополнительные сведения: System. ServiceModel. Ткскомплетионстатускомплетедфорасинкаборт'
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.date: 03/30/2017
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
ms.openlocfilehash: 892a867607d1c6d34c06a59947cc336db067fb19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735690"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="1b4f9-103">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="1b4f9-103">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>

<span data-ttu-id="1b4f9-104">Заданная транзакция для заданной операции завершена в результате асинхронного прерывания.</span><span class="sxs-lookup"><span data-stu-id="1b4f9-104">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1b4f9-105">Описание</span><span class="sxs-lookup"><span data-stu-id="1b4f9-105">Description</span></span>  

 <span data-ttu-id="1b4f9-106">Текущая транзакция была прервана, потому что другой участник спровоцировал прерывание, истекло время ожидания или из-за внутренней ошибки участника транзакции.</span><span class="sxs-lookup"><span data-stu-id="1b4f9-106">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1b4f9-107">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="1b4f9-107">Troubleshooting</span></span>  

 <span data-ttu-id="1b4f9-108">Если это прерывание произошло неожиданно, проверьте системные журналы, чтобы определить истинную причину прерывания.</span><span class="sxs-lookup"><span data-stu-id="1b4f9-108">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b4f9-109">См. также</span><span class="sxs-lookup"><span data-stu-id="1b4f9-109">See also</span></span>

- [<span data-ttu-id="1b4f9-110">Трассировка</span><span class="sxs-lookup"><span data-stu-id="1b4f9-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="1b4f9-111">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="1b4f9-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1b4f9-112">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="1b4f9-112">Administration and Diagnostics</span></span>](../index.md)
