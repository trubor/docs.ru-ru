---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. Курдинаторстатемачинефинишед'
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 83cbc6fe80d0fc611c88e8074805cae870261305
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759397"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="5e1dc-103">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="5e1dc-103">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>

<span data-ttu-id="5e1dc-104">Конечный автомат для перечисления координаторов перешел в конечное состояние.</span><span class="sxs-lookup"><span data-stu-id="5e1dc-104">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5e1dc-105">Описание</span><span class="sxs-lookup"><span data-stu-id="5e1dc-105">Description</span></span>  

 <span data-ttu-id="5e1dc-106">Регистрируется, если локальный диспетчер транзакция полагает, что перечисление координаторов более высокого уровня завершило обработку 2pc.</span><span class="sxs-lookup"><span data-stu-id="5e1dc-106">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="5e1dc-107">Результатом перечисления может быть значение Committed, Aborted или Forgotten.</span><span class="sxs-lookup"><span data-stu-id="5e1dc-107">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="5e1dc-108">Кроме того, это событие регистрируется, если на этапе подготовки локальный диспетчер транзакций голосует за режим ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="5e1dc-108">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e1dc-109">См. также</span><span class="sxs-lookup"><span data-stu-id="5e1dc-109">See also</span></span>

- [<span data-ttu-id="5e1dc-110">Трассировка</span><span class="sxs-lookup"><span data-stu-id="5e1dc-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="5e1dc-111">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="5e1dc-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="5e1dc-112">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="5e1dc-112">Administration and Diagnostics</span></span>](../index.md)
