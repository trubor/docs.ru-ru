---
description: 'Дополнительные сведения: транзакции и параллелизм'
title: Транзакции и параллельность
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: c77b9abc72ae662eec76fc40a9856ad73f000c27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766768"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="96f5e-103">Транзакции и параллельность</span><span class="sxs-lookup"><span data-stu-id="96f5e-103">Transactions and Concurrency</span></span>

<span data-ttu-id="96f5e-104">Транзакция состоит из одной команды или группы команд, которые выполняются как пакет.</span><span class="sxs-lookup"><span data-stu-id="96f5e-104">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="96f5e-105">Транзакции позволяют объединить несколько операций в одну единицу работы.</span><span class="sxs-lookup"><span data-stu-id="96f5e-105">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="96f5e-106">Если в какой-либо точке транзакции возникает ошибка, может быть выполнен откат всех обновлений к их состоянию до начала транзакции.</span><span class="sxs-lookup"><span data-stu-id="96f5e-106">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="96f5e-107">Для обеспечения согласованности данных транзакция должна соответствовать свойствам ACID (атомарность, согласованность, изоляция и устойчивость).</span><span class="sxs-lookup"><span data-stu-id="96f5e-107">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="96f5e-108">Большая часть систем реляционных баз данных, таких как Microsoft SQL Server, поддерживает транзакции, предоставляя блокировку, ведение журнала и средства управления транзакцией при выполнении клиентским приложением операций обновления, вставки или удаления.</span><span class="sxs-lookup"><span data-stu-id="96f5e-108">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96f5e-109">Транзакции, которые задействуют множество ресурсов, могут снизить параллелизм, если слишком долго удерживают блокировки.</span><span class="sxs-lookup"><span data-stu-id="96f5e-109">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="96f5e-110">Поэтому транзакции следует делать как можно короче.</span><span class="sxs-lookup"><span data-stu-id="96f5e-110">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="96f5e-111">В том случае, если в транзакции участвует несколько таблиц одной базы данных или одного сервера, явные транзакции в хранимых процедурах часто выполняются лучше.</span><span class="sxs-lookup"><span data-stu-id="96f5e-111">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="96f5e-112">Транзакции можно создавать в хранимых процедурах SQL Server с использованием инструкций Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION` и `ROLLBACK TRANSACTION`.</span><span class="sxs-lookup"><span data-stu-id="96f5e-112">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="96f5e-113">Дополнительные сведения см. в электронной документации по SQL Server.</span><span class="sxs-lookup"><span data-stu-id="96f5e-113">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="96f5e-114">Если для выполнения транзакций требуются различные диспетчеры ресурсов, например для транзакций между SQL Server и Oracle, необходимо использовать распределенную транзакцию.</span><span class="sxs-lookup"><span data-stu-id="96f5e-114">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96f5e-115">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="96f5e-115">In This Section</span></span>  

 [<span data-ttu-id="96f5e-116">Локальные транзакции</span><span class="sxs-lookup"><span data-stu-id="96f5e-116">Local Transactions</span></span>](local-transactions.md)  
 <span data-ttu-id="96f5e-117">Демонстрирует выполнение транзакций на базе данных.</span><span class="sxs-lookup"><span data-stu-id="96f5e-117">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="96f5e-118">Распределенные транзакции</span><span class="sxs-lookup"><span data-stu-id="96f5e-118">Distributed Transactions</span></span>](distributed-transactions.md)  
 <span data-ttu-id="96f5e-119">Описывает выполнение распределенных транзакций в ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="96f5e-119">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="96f5e-120">Интеграция System. Transactions с SQL Server</span><span class="sxs-lookup"><span data-stu-id="96f5e-120">System.Transactions Integration with SQL Server</span></span>](system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="96f5e-121">Описывает интеграцию <xref:System.Transactions> с SQL Server для работы с распределенными транзакциями.</span><span class="sxs-lookup"><span data-stu-id="96f5e-121">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="96f5e-122">Оптимистичный параллелизм</span><span class="sxs-lookup"><span data-stu-id="96f5e-122">Optimistic Concurrency</span></span>](optimistic-concurrency.md)  
 <span data-ttu-id="96f5e-123">Описывается оптимистичный и пессимистичный параллелизм и проверка на выявление нарушений параллелизма.</span><span class="sxs-lookup"><span data-stu-id="96f5e-123">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f5e-124">См. также</span><span class="sxs-lookup"><span data-stu-id="96f5e-124">See also</span></span>

- [<span data-ttu-id="96f5e-125">Основные сведения о транзакциях</span><span class="sxs-lookup"><span data-stu-id="96f5e-125">Transaction Fundamentals</span></span>](../transactions/transaction-fundamentals.md)
- [<span data-ttu-id="96f5e-126">Подключение к источнику данных</span><span class="sxs-lookup"><span data-stu-id="96f5e-126">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="96f5e-127">Команды и параметры</span><span class="sxs-lookup"><span data-stu-id="96f5e-127">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="96f5e-128">Объекты DataAdapter и DataReader</span><span class="sxs-lookup"><span data-stu-id="96f5e-128">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="96f5e-129">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="96f5e-129">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="96f5e-130">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="96f5e-130">ADO.NET Overview</span></span>](ado-net-overview.md)
