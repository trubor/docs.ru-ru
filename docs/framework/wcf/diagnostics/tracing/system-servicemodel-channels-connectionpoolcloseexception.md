---
description: 'Дополнительные сведения: System. ServiceModel. Channels. Коннектионпулклосиксцептион'
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: a65739cc872f3cd175d76e9113380f9f4185d498
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644636"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="7a0c5-103">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="7a0c5-103">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>

<span data-ttu-id="7a0c5-104">При закрытии подключений в этом пуле подключений возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="7a0c5-104">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7a0c5-105">Описание</span><span class="sxs-lookup"><span data-stu-id="7a0c5-105">Description</span></span>  

 <span data-ttu-id="7a0c5-106">Эта трассировка уровня ошибок указывает на то, что при закрытии пулов соединений, используемых компонентом пулов соединений Windows Communication Foundation (WCF), произошла ошибка.</span><span class="sxs-lookup"><span data-stu-id="7a0c5-106">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="7a0c5-107">Эта ошибка может быть вызвана тем, что не удалось закрыть подключение (или набор подключений) из пула в течение времени ожидания (CloseTimeout).</span><span class="sxs-lookup"><span data-stu-id="7a0c5-107">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="7a0c5-108">При выдаче этого исключения все оставшиеся незакрытые подключения из этого пула прерываются. Незакрытые подключения из других пулов оставляются.</span><span class="sxs-lookup"><span data-stu-id="7a0c5-108">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0c5-109">См. также</span><span class="sxs-lookup"><span data-stu-id="7a0c5-109">See also</span></span>

- [<span data-ttu-id="7a0c5-110">Трассировка</span><span class="sxs-lookup"><span data-stu-id="7a0c5-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="7a0c5-111">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="7a0c5-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7a0c5-112">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="7a0c5-112">Administration and Diagnostics</span></span>](../index.md)
