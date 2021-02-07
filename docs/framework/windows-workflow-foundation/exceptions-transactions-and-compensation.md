---
description: 'Дополнительные сведения: исключения, транзакции и компенсация'
title: Исключения, транзакции и компенсация
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: 3188b0238b1909847c289bb56274671ff4b307b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720193"
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="8b1cb-103">Исключения, транзакции и компенсация</span><span class="sxs-lookup"><span data-stu-id="8b1cb-103">Exceptions, Transactions, and Compensation</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="8b1cb-104">предоставляет несколько различных механизмов обработки состояний ошибок времени выполнения в рабочих процессах.</span><span class="sxs-lookup"><span data-stu-id="8b1cb-104">provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="8b1cb-105">Рабочие процессы могут использовать сочетание обработчиков исключений, транзакций, отмены и компенсации для обработки ошибочных состояний и верного возобновления работы.</span><span class="sxs-lookup"><span data-stu-id="8b1cb-105">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b1cb-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="8b1cb-106">In This Section</span></span>  

 [<span data-ttu-id="8b1cb-107">Исключения</span><span class="sxs-lookup"><span data-stu-id="8b1cb-107">Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="8b1cb-108">Показывается использование действия <xref:System.Activities.Statements.TryCatch> для обработки исключений в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="8b1cb-108">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="8b1cb-109">Транзакции</span><span class="sxs-lookup"><span data-stu-id="8b1cb-109">Transactions</span></span>](workflow-transactions.md)  
 <span data-ttu-id="8b1cb-110">Показывается использование действия <xref:System.Activities.Statements.TransactionScope> для использования транзакций в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="8b1cb-110">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="8b1cb-111">Компенсация</span><span class="sxs-lookup"><span data-stu-id="8b1cb-111">Compensation</span></span>](compensation.md)  
 <span data-ttu-id="8b1cb-112">Описывается компенсация в рабочих процессах и показывается использование действий компенсации, например <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate> и <xref:System.Activities.Statements.Confirm>.</span><span class="sxs-lookup"><span data-stu-id="8b1cb-112">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="8b1cb-113">Отмена</span><span class="sxs-lookup"><span data-stu-id="8b1cb-113">Cancellation</span></span>](modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="8b1cb-114">Описывает, как производить выполнение отмены в рабочих процессах с помощью встроенных и настраиваемых действий.</span><span class="sxs-lookup"><span data-stu-id="8b1cb-114">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="8b1cb-115">Отладка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="8b1cb-115">Debugging Workflows</span></span>](debugging-workflows.md)  
 <span data-ttu-id="8b1cb-116">Содержит описание способов отладки рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="8b1cb-116">Describes how to debug workflows.</span></span>
