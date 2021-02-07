---
description: 'Дополнительные сведения: System. ServiceModel. Ткскомплетионстатусабортедонсессионклосе'
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: d47dc1a87c7f44b58f70f9590b4233f1e0a9074e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735716"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="8aef7-103">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="8aef7-103">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>

<span data-ttu-id="8aef7-104">Указанная транзакция прервана, поскольку она была незавершенной на момент закрытия сеанса и атрибуту TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute задано значение "false".</span><span class="sxs-lookup"><span data-stu-id="8aef7-104">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8aef7-105">Описание</span><span class="sxs-lookup"><span data-stu-id="8aef7-105">Description</span></span>  

 <span data-ttu-id="8aef7-106">Трассируется, если текущий активный сеанс был закрыт, транзакция не была завершена и TransactionAutoCompleteOnSessionClose имеет значение `false`.</span><span class="sxs-lookup"><span data-stu-id="8aef7-106">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8aef7-107">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="8aef7-107">Troubleshooting</span></span>  

 <span data-ttu-id="8aef7-108">Эта трассировка указывает о потенциальной ошибке в приложении, наличие которой требуется проверить.</span><span class="sxs-lookup"><span data-stu-id="8aef7-108">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aef7-109">См. также</span><span class="sxs-lookup"><span data-stu-id="8aef7-109">See also</span></span>

- [<span data-ttu-id="8aef7-110">Трассировка</span><span class="sxs-lookup"><span data-stu-id="8aef7-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="8aef7-111">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="8aef7-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8aef7-112">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="8aef7-112">Administration and Diagnostics</span></span>](../index.md)
