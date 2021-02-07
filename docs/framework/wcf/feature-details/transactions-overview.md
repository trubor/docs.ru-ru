---
description: 'Дополнительные сведения: Общие сведения о Windows Communication Foundation Transactions'
title: Общие сведения о транзакциях Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: c9d251e4f49ee8e2edaa0ce2ff48738383a1b76c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752656"
---
# <a name="windows-communication-foundation-transactions-overview"></a><span data-ttu-id="4d18f-103">Общие сведения о транзакциях Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4d18f-103">Windows Communication Foundation Transactions Overview</span></span>

<span data-ttu-id="4d18f-104">Транзакции обеспечивают способ группировки набора действий или операций в одну неделимую единицу выполнения.</span><span class="sxs-lookup"><span data-stu-id="4d18f-104">Transactions provide a way to group a set of actions or operations into a single indivisible unit of execution.</span></span> <span data-ttu-id="4d18f-105">Транзакция является коллекцией операций с перечисленными ниже свойствами.</span><span class="sxs-lookup"><span data-stu-id="4d18f-105">A transaction is a collection of operations with the following properties:</span></span>  
  
- <span data-ttu-id="4d18f-106">Атомарность.</span><span class="sxs-lookup"><span data-stu-id="4d18f-106">Atomicity.</span></span> <span data-ttu-id="4d18f-107">Благодаря данному свойству все обновления, завершенные в отдельной транзакции, либо фиксируются и становятся стабильными, либо отменяются и возвращаются к предыдущему состоянию с помощью отката.</span><span class="sxs-lookup"><span data-stu-id="4d18f-107">This ensures that either all of the updates completed under a specific transaction are committed and made durable or they are all aborted and rolled back to their previous state.</span></span>  
  
- <span data-ttu-id="4d18f-108">Согласованность.</span><span class="sxs-lookup"><span data-stu-id="4d18f-108">Consistency.</span></span> <span data-ttu-id="4d18f-109">Данное свойство гарантирует, что все изменения, внесенные при транзакции, представляют собой трансформацию из одного состояния в другое.</span><span class="sxs-lookup"><span data-stu-id="4d18f-109">This guarantees that the changes made under a transaction represent a transformation from one consistent state to another.</span></span> <span data-ttu-id="4d18f-110">Например, транзакция, передающая деньги с текущего счета на сберегательный счет, не изменяет общее количество денег на банковском счете.</span><span class="sxs-lookup"><span data-stu-id="4d18f-110">For example, a transaction that transfers money from a checking account to a savings account does not change the amount of money in the overall bank account.</span></span>  
  
- <span data-ttu-id="4d18f-111">Изоляция.</span><span class="sxs-lookup"><span data-stu-id="4d18f-111">Isolation.</span></span> <span data-ttu-id="4d18f-112">Данное свойство предохраняет транзакцию от просмотра несохраненных изменений, относящихся к другим параллельным транзакциям.</span><span class="sxs-lookup"><span data-stu-id="4d18f-112">This prevents a transaction from observing uncommitted changes belonging to other concurrent transactions.</span></span> <span data-ttu-id="4d18f-113">Изоляция обеспечивает отвлечение параллелизма, а также невозможность непредвиденного влияния одной транзакции на выполнение другой транзакции.</span><span class="sxs-lookup"><span data-stu-id="4d18f-113">Isolation provides an abstraction of concurrency while ensuring one transaction cannot have an unexpected impact on the execution of another transaction.</span></span>  
  
- <span data-ttu-id="4d18f-114">Устойчивость.</span><span class="sxs-lookup"><span data-stu-id="4d18f-114">Durability.</span></span> <span data-ttu-id="4d18f-115">Данное свойство обозначает, что при однократной фиксации обновления в управляемых ресурсах (такие как запись базы данных) станут устойчивыми к сбоям.</span><span class="sxs-lookup"><span data-stu-id="4d18f-115">This means that once committed, updates to managed resources (such as a database record) will be persistent in the face of failures.</span></span>  
  
 <span data-ttu-id="4d18f-116">Windows Communication Foundation (WCF) предоставляет широкий набор функций, позволяющих создавать распределенные транзакции в приложении веб-службы.</span><span class="sxs-lookup"><span data-stu-id="4d18f-116">Windows Communication Foundation (WCF) provides a rich set of features that enable you to create distributed transactions in your Web service application.</span></span>  
  
 <span data-ttu-id="4d18f-117">В WCF реализована поддержка протокола WS-AtomicTransaction (WS-AT), который позволяет приложениям WCF передавать транзакции в совместимые приложения, такие как веб-службы с возможностью взаимодействия, созданные с помощью сторонних технологий.</span><span class="sxs-lookup"><span data-stu-id="4d18f-117">WCF implements support for the WS-AtomicTransaction (WS-AT) protocol that enables WCF applications to flow transactions to interoperable applications, such as interoperable Web services built using third-party technology.</span></span> <span data-ttu-id="4d18f-118">В WCF также реализована поддержка протокола OLE Transactions, которую можно использовать в сценариях, где не требуется функциональность взаимодействия для включения потока транзакций.</span><span class="sxs-lookup"><span data-stu-id="4d18f-118">WCF also implements support for the OLE Transactions protocol, which can be used in scenarios where you do not need interop functionality to enable transaction flow.</span></span>  
  
 <span data-ttu-id="4d18f-119">Для настройки привязок можно использовать файл конфигурации приложения, позволяющий включать или отключать передачу транзакций, а также задавать необходимый протокол транзакций для привязки.</span><span class="sxs-lookup"><span data-stu-id="4d18f-119">You can use an application configuration file to configure bindings to enable or disable transaction flow, as well as set the desired transaction protocol on a binding.</span></span> <span data-ttu-id="4d18f-120">Кроме того, можно задать время ожидания транзакций на уровне службы с помощью файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="4d18f-120">In addition, you can set transaction time-outs at the service level using the configuration file.</span></span> <span data-ttu-id="4d18f-121">Дополнительные сведения см. в разделе [Включение потока транзакций](enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="4d18f-121">For more information, see [Enabling Transaction Flow](enabling-transaction-flow.md).</span></span>  
  
 <span data-ttu-id="4d18f-122">Атрибуты транзакции в пространстве имен <xref:System.ServiceModel> позволяют выполнять перечисленные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="4d18f-122">Transaction attributes in the <xref:System.ServiceModel> namespace allow you to do the following:</span></span>  
  
- <span data-ttu-id="4d18f-123">Настраивать время ожидания транзакций и фильтрацию уровня изоляции с помощью атрибута <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4d18f-123">Configure transaction time-outs and isolation-level filtering using the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span>  
  
- <span data-ttu-id="4d18f-124">Включать функциональность транзакций и настраивать поведение при завершении транзакции с помощью атрибута <xref:System.ServiceModel.OperationBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4d18f-124">Enable transactions functionality and configure transaction completion behavior using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span>  
  
- <span data-ttu-id="4d18f-125">Для требования, разрешения или запрещения потока транзакций используйте атрибуты <xref:System.ServiceModel.ServiceContractAttribute> и <xref:System.ServiceModel.OperationContractAttribute> метода контракта.</span><span class="sxs-lookup"><span data-stu-id="4d18f-125">Use the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes on a contract method to require, allow or deny transaction flow.</span></span>  
  
 <span data-ttu-id="4d18f-126">Дополнительные сведения см. в разделе [атрибуты транзакций ServiceModel](servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="4d18f-126">For more information, see [ServiceModel Transaction Attributes](servicemodel-transaction-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d18f-127">См. также</span><span class="sxs-lookup"><span data-stu-id="4d18f-127">See also</span></span>

- [<span data-ttu-id="4d18f-128">Атрибуты транзакции ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4d18f-128">ServiceModel Transaction Attributes</span></span>](servicemodel-transaction-attributes.md)
- [<span data-ttu-id="4d18f-129">Включение потока транзакций</span><span class="sxs-lookup"><span data-stu-id="4d18f-129">Enabling Transaction Flow</span></span>](enabling-transaction-flow.md)
