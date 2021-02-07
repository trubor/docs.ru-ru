---
description: Дополнительные сведения о действиях транзакций в WF
title: Действия транзакций в WF
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: f088c586998d3dbec8b94dcf0f02603a68b55a40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755139"
---
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="f2e02-103">Действия транзакций в WF</span><span class="sxs-lookup"><span data-stu-id="f2e02-103">Transaction Activities in WF</span></span>

<span data-ttu-id="f2e02-104">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] содержит несколько предоставляемых системой действий для моделирования транзакций, компенсации и отмены.</span><span class="sxs-lookup"><span data-stu-id="f2e02-104">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="f2e02-105">Эти модели программирования позволяют рабочему процессу продолжаться при возникновении изменений в бизнес-логике и обработке ошибок.</span><span class="sxs-lookup"><span data-stu-id="f2e02-105">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> <span data-ttu-id="f2e02-106">Дополнительные сведения о транзакциях, компенсации и отмене см. в разделе [транзакции](workflow-transactions.md), [компенсация](compensation.md)и [Отмена](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="f2e02-106">For more information about transactions, compensation, and cancellation, see [Transactions](workflow-transactions.md), [Compensation](compensation.md), and [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="f2e02-107">Действия транзакций</span><span class="sxs-lookup"><span data-stu-id="f2e02-107">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="f2e02-108">Связывает логику отмены в виде действия с главным путем выполнения, который тоже выражен в виде действия.</span><span class="sxs-lookup"><span data-stu-id="f2e02-108">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="f2e02-109">Поддерживает компенсацию своих дочерних действий.</span><span class="sxs-lookup"><span data-stu-id="f2e02-109">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="f2e02-110">Явно вызывает обработчика компенсации объекта <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="f2e02-110">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="f2e02-111">Явно вызывает обработчика подтверждения объекта <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="f2e02-111">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="f2e02-112">Указывает границу транзакции.</span><span class="sxs-lookup"><span data-stu-id="f2e02-112">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="f2e02-113">Область совпадает со временем существования транзакции, инициированной при получении сообщения.</span><span class="sxs-lookup"><span data-stu-id="f2e02-113">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="f2e02-114">Транзакция может быть введена в рабочий процесс с помощью инициирующего сообщения либо создана диспетчером при его получении.</span><span class="sxs-lookup"><span data-stu-id="f2e02-114">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="f2e02-115">**Примечание.**  Объект находится <xref:System.ServiceModel.Activities.TransactedReceiveScope> в разделе « **Обмен сообщениями** » **области элементов**.</span><span class="sxs-lookup"><span data-stu-id="f2e02-115">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
