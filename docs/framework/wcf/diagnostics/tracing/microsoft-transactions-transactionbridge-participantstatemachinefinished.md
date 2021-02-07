---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. ПартиЦипантстатемачинефинишед'
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: f49027b82957969779423d0895ff24a4a36d1f4f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759384"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="0d7d7-103">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="0d7d7-103">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>

<span data-ttu-id="0d7d7-104">Конечный автомат для перечисления участников перешел в конечное состояние.</span><span class="sxs-lookup"><span data-stu-id="0d7d7-104">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0d7d7-105">Описание</span><span class="sxs-lookup"><span data-stu-id="0d7d7-105">Description</span></span>  

 <span data-ttu-id="0d7d7-106">Трассируется, когда перечисление подчиненных участников завершило обработку 2pc.</span><span class="sxs-lookup"><span data-stu-id="0d7d7-106">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="0d7d7-107">Результатом для перечисления может быть значение Committed или Aborted.</span><span class="sxs-lookup"><span data-stu-id="0d7d7-107">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="0d7d7-108">Кроме того, это событие регистрируется, если на этапе подготовки любой из участников голосует за режим ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="0d7d7-108">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d7d7-109">См. также</span><span class="sxs-lookup"><span data-stu-id="0d7d7-109">See also</span></span>

- [<span data-ttu-id="0d7d7-110">Трассировка</span><span class="sxs-lookup"><span data-stu-id="0d7d7-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="0d7d7-111">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="0d7d7-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0d7d7-112">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="0d7d7-112">Administration and Diagnostics</span></span>](../index.md)
