---
description: 'Дополнительные сведения: System. ServiceModel. Тксфаиледтонеготиатеолеткс'
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: c7f18ef73ff9c09cc51ad3aa6c54c2bd672d0cc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735573"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="f05b4-103">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="f05b4-103">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>

<span data-ttu-id="f05b4-104">Согласование протокола OleTransactions невозможно завершить для заданного контекста координации.</span><span class="sxs-lookup"><span data-stu-id="f05b4-104">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f05b4-105">Описание</span><span class="sxs-lookup"><span data-stu-id="f05b4-105">Description</span></span>  

 <span data-ttu-id="f05b4-106">Трассируется, если входящая транзакция с информацией OleTx не может использовать прикрепленную информацию OleTx и вместо этого использует WS-AT.</span><span class="sxs-lookup"><span data-stu-id="f05b4-106">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f05b4-107">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="f05b4-107">Troubleshooting</span></span>  

 <span data-ttu-id="f05b4-108">Показывает возможную проблему обмена данными MSDTC RPC между компьютерами.</span><span class="sxs-lookup"><span data-stu-id="f05b4-108">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="f05b4-109">Появление большого количества таких трассировок в журнале может привести к значительному снижению производительности.</span><span class="sxs-lookup"><span data-stu-id="f05b4-109">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="f05b4-110">Если информация OleTx не требуется, установите `OleTxUpgradeEnabled` на значение 0 в конфигурации реестра WS-AT.</span><span class="sxs-lookup"><span data-stu-id="f05b4-110">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f05b4-111">См. также</span><span class="sxs-lookup"><span data-stu-id="f05b4-111">See also</span></span>

- [<span data-ttu-id="f05b4-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="f05b4-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="f05b4-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="f05b4-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f05b4-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="f05b4-114">Administration and Diagnostics</span></span>](../index.md)
