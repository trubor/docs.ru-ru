---
description: Дополнительные сведения см. в статье интеграция System. Transactions с SQL Server
title: Интеграция System.Transactions с SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 977ff18600256613dabc0212c2f7aa1bc2650408
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766781"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="21480-103">Интеграция System.Transactions с SQL Server</span><span class="sxs-lookup"><span data-stu-id="21480-103">System.Transactions Integration with SQL Server</span></span>

<span data-ttu-id="21480-104">В платформа .NET Framework версии 2,0 появилась платформа транзакций, доступ к которой можно получить через <xref:System.Transactions> пространство имен.</span><span class="sxs-lookup"><span data-stu-id="21480-104">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="21480-105">Эта платформа предоставляет транзакции в виде, который полностью интегрирован в платформа .NET Framework, включая ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="21480-105">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="21480-106">Помимо улучшенных способов программирования, <xref:System.Transactions> и ADO.NET могут работать вместе для координации оптимизации при работе с транзакциями.</span><span class="sxs-lookup"><span data-stu-id="21480-106">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="21480-107">Повышаемая транзакция — это упрощенная (локальная) транзакция, которая по необходимости может быть автоматически повышена до полностью распределенной транзакции.</span><span class="sxs-lookup"><span data-stu-id="21480-107">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="21480-108">Начиная с ADO.NET 2,0, <xref:System.Data.SqlClient> поддерживает продвижение транзакций при работе с SQL Server.</span><span class="sxs-lookup"><span data-stu-id="21480-108">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="21480-109">Повышаемая транзакция не вызывает дополнительную нагрузку распределенной транзакции, если таковая не требуется.</span><span class="sxs-lookup"><span data-stu-id="21480-109">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="21480-110">Повышаемые транзакции выполняются автоматически и не требуют вмешательства разработчика.</span><span class="sxs-lookup"><span data-stu-id="21480-110">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="21480-111">Операции повышения доступны только при использовании платформа .NET Framework поставщика данных для SQL Server ( `SqlClient` ) с SQL Server.</span><span class="sxs-lookup"><span data-stu-id="21480-111">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="21480-112">Создание повышаемых транзакций</span><span class="sxs-lookup"><span data-stu-id="21480-112">Creating Promotable Transactions</span></span>  

 <span data-ttu-id="21480-113">Поставщик платформа .NET Framework для SQL Server предоставляет поддержку для продвижения транзакций, которые обрабатываются с помощью классов в <xref:System.Transactions> пространстве имен платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21480-113">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="21480-114">Повышаемые транзакции оптимизируют работу с распределенными транзакциями за счет отсрочки создания распределенной транзакции до того момента, когда она будет необходима.</span><span class="sxs-lookup"><span data-stu-id="21480-114">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="21480-115">Если требуется только один диспетчер ресурсов, то распределенная транзакция не создается.</span><span class="sxs-lookup"><span data-stu-id="21480-115">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21480-116">В частично доверенном сценарии при повышении транзакции до распределенной требуется право доступа <xref:System.Transactions.DistributedTransactionPermission> .</span><span class="sxs-lookup"><span data-stu-id="21480-116">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="21480-117">Сценарии использования повышаемых транзакций</span><span class="sxs-lookup"><span data-stu-id="21480-117">Promotable Transaction Scenarios</span></span>  

 <span data-ttu-id="21480-118">Как правило, для распределенных транзакций требуются значительные системные ресурсы, поскольку они управляются координатором распределенных транзакций (Майкрософт), который интегрирует все диспетчеры ресурсов, используемые в транзакции.</span><span class="sxs-lookup"><span data-stu-id="21480-118">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="21480-119">Повышаемая транзакция — это особая форма транзакции <xref:System.Transactions>, эффективно делегирующая работу простой транзакции SQL Server.</span><span class="sxs-lookup"><span data-stu-id="21480-119">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="21480-120"><xref:System.Transactions>, <xref:System.Data.SqlClient> и SQL Server координируют работу, выполняемую при обработке транзакции, при необходимости повышая ее до полностью распределенной транзакции.</span><span class="sxs-lookup"><span data-stu-id="21480-120"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="21480-121">Преимущество использования повышаемых транзакций заключается в том, что при открытии соединения с помощью активной транзакции <xref:System.Transactions.TransactionScope> и отсутствии других открытых соединений такая транзакция фиксируется как упрощенная, что позволяет избежать излишних затрат ресурсов на полностью распределенную транзакцию.</span><span class="sxs-lookup"><span data-stu-id="21480-121">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="21480-122">Ключевые слова в строке подключения</span><span class="sxs-lookup"><span data-stu-id="21480-122">Connection String Keywords</span></span>  

 <span data-ttu-id="21480-123">В свойстве <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> поддерживается использование ключевого слова `Enlist`, которое указывает, будет ли клиент <xref:System.Data.SqlClient> обнаруживать контексты транзакций и автоматически прикреплять соединение к распределенной транзакции.</span><span class="sxs-lookup"><span data-stu-id="21480-123">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="21480-124">Если `Enlist=true`, то соединение автоматически прикрепляется к текущему контексту транзакции открывающего потока.</span><span class="sxs-lookup"><span data-stu-id="21480-124">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="21480-125">Если `Enlist=false`, то соединение `SqlClient` не будет взаимодействовать с распределенной транзакцией.</span><span class="sxs-lookup"><span data-stu-id="21480-125">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="21480-126">Значение `Enlist` по умолчанию - true.</span><span class="sxs-lookup"><span data-stu-id="21480-126">The default value for `Enlist` is true.</span></span> <span data-ttu-id="21480-127">Если ключевое слово `Enlist` в строке соединения не задано, то соединение автоматически прикрепляется к распределенной транзакции, если она будет обнаружена при открытии соединения.</span><span class="sxs-lookup"><span data-stu-id="21480-127">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="21480-128">Ключевые слова `Transaction Binding` в строке соединения <xref:System.Data.SqlClient.SqlConnection> управляют связью соединения с прикрепленной транзакцией `System.Transactions` .</span><span class="sxs-lookup"><span data-stu-id="21480-128">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="21480-129">Эта связь также доступна через свойство <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> построителя <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="21480-129">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="21480-130">В следующей таблице описаны возможные значения.</span><span class="sxs-lookup"><span data-stu-id="21480-130">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="21480-131">Ключевое слово</span><span class="sxs-lookup"><span data-stu-id="21480-131">Keyword</span></span>|<span data-ttu-id="21480-132">Описание</span><span class="sxs-lookup"><span data-stu-id="21480-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21480-133">Implicit Unbind</span><span class="sxs-lookup"><span data-stu-id="21480-133">Implicit Unbind</span></span>|<span data-ttu-id="21480-134">Это значение используется по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="21480-134">The default.</span></span> <span data-ttu-id="21480-135">Соединение отсоединяется от транзакции по ее завершении, вновь переходя в режим автоматической фиксации.</span><span class="sxs-lookup"><span data-stu-id="21480-135">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="21480-136">Explicit Unbind</span><span class="sxs-lookup"><span data-stu-id="21480-136">Explicit Unbind</span></span>|<span data-ttu-id="21480-137">Соединение остается прикрепленным к транзакции до ее закрытия.</span><span class="sxs-lookup"><span data-stu-id="21480-137">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="21480-138">Соединение будет потеряно, если связанная с ним транзакция не активна или не соответствует <xref:System.Transactions.Transaction.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="21480-138">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="21480-139">Использование класса TransactionScope</span><span class="sxs-lookup"><span data-stu-id="21480-139">Using TransactionScope</span></span>  

 <span data-ttu-id="21480-140">Класс <xref:System.Transactions.TransactionScope> делает блок кода транзакционным, неявно прикрепляя соединения к распределенной транзакции.</span><span class="sxs-lookup"><span data-stu-id="21480-140">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="21480-141">В конце блока <xref:System.Transactions.TransactionScope.Complete%2A> перед тем, как выйти из него, необходимо вызвать метод <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="21480-141">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="21480-142">При выходе из этого блока вызывается метод <xref:System.Transactions.TransactionScope.Dispose%2A> .</span><span class="sxs-lookup"><span data-stu-id="21480-142">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="21480-143">При возникновении исключения, в результате которого исполнение кода выходит за пределы области, транзакция считается прерванной.</span><span class="sxs-lookup"><span data-stu-id="21480-143">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="21480-144">Рекомендуется использовать блок `using` , чтобы гарантировать вызов метода <xref:System.Transactions.TransactionScope.Dispose%2A> для объекта <xref:System.Transactions.TransactionScope> при выходе из блока using.</span><span class="sxs-lookup"><span data-stu-id="21480-144">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="21480-145">Неудачная попытка зафиксировать или откатить незавершенные транзакции может значительно снизить производительность, поскольку время ожидания по умолчанию для объекта <xref:System.Transactions.TransactionScope> составляет одну минуту.</span><span class="sxs-lookup"><span data-stu-id="21480-145">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="21480-146">Если инструкция `using` не используется, необходимо явно выполнить все действия в блоке `Try` и вызвать метод <xref:System.Transactions.TransactionScope.Dispose%2A> в блоке `Finally`.</span><span class="sxs-lookup"><span data-stu-id="21480-146">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="21480-147">Если в объекте <xref:System.Transactions.TransactionScope>возникает исключение, транзакция помечается как несогласованная и прерывается.</span><span class="sxs-lookup"><span data-stu-id="21480-147">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="21480-148">При удалении объекта <xref:System.Transactions.TransactionScope> будет произведен ее откат.</span><span class="sxs-lookup"><span data-stu-id="21480-148">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="21480-149">Если исключений не возникает, то участвующие транзакции будут зафиксированы.</span><span class="sxs-lookup"><span data-stu-id="21480-149">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21480-150">Класс `TransactionScope` создает транзакцию с уровнем изоляции <xref:System.Transactions.Transaction.IsolationLevel%2A>, равным `Serializable` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="21480-150">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="21480-151">В зависимости от приложения уровень изоляции можно понижать во избежание большого количества состязаний данных в приложении.</span><span class="sxs-lookup"><span data-stu-id="21480-151">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21480-152">В рамках распределенных транзакций рекомендуется выполнять только операции обновления, вставки и удаления, поскольку они потребляют значительные ресурсы базы данных.</span><span class="sxs-lookup"><span data-stu-id="21480-152">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="21480-153">Инструкции выборки могут без необходимости блокировать ресурсы базы данных, и в некоторых случаях для выборки может потребоваться использование транзакций.</span><span class="sxs-lookup"><span data-stu-id="21480-153">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="21480-154">Любые не связанные с базой данных действия должны выполняться за пределами области транзакции, если только в ней не задействованы другие диспетчеры ресурсов транзакций.</span><span class="sxs-lookup"><span data-stu-id="21480-154">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="21480-155">Хотя исключение в области транзакции не позволяет зафиксировать транзакцию, класс <xref:System.Transactions.TransactionScope> не имеет возможности отката каких-либо изменений, внесенных кодом за пределами области самой транзакции.</span><span class="sxs-lookup"><span data-stu-id="21480-155">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="21480-156">При необходимости предпринять какие-либо действия, когда производится откат транзакции, следует написать собственную реализацию интерфейса <xref:System.Transactions.IEnlistmentNotification> и явно прикрепить его к транзакции.</span><span class="sxs-lookup"><span data-stu-id="21480-156">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21480-157">Пример</span><span class="sxs-lookup"><span data-stu-id="21480-157">Example</span></span>  

 <span data-ttu-id="21480-158">Для работы с <xref:System.Transactions> необходима ссылка на файл System.Transactions.dll.</span><span class="sxs-lookup"><span data-stu-id="21480-158">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="21480-159">Следующая функция показывает, как создать повышаемую транзакцию для двух разных экземпляров SQL Server, представленных двумя разными объектами <xref:System.Data.SqlClient.SqlConnection> , которые заключены в оболочку с помощью блок <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="21480-159">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="21480-160">В коде создается блок <xref:System.Transactions.TransactionScope> с инструкцией `using` и открывается первое соединение, которое автоматически прикрепляется к транзакции <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="21480-160">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="21480-161">Изначально транзакция прикрепляется как упрощенная, а не полностью распределенная транзакция.</span><span class="sxs-lookup"><span data-stu-id="21480-161">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="21480-162">Второе соединение прикрепляется к транзакции <xref:System.Transactions.TransactionScope> , только если при выполнении команды в первом соединении не возникает исключения.</span><span class="sxs-lookup"><span data-stu-id="21480-162">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="21480-163">При открытии второго соединения транзакция автоматически повышается до полностью распределенной.</span><span class="sxs-lookup"><span data-stu-id="21480-163">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="21480-164">Вызывается метод <xref:System.Transactions.TransactionScope.Complete%2A> , который фиксирует транзакцию, только если не возникло ни одного исключения.</span><span class="sxs-lookup"><span data-stu-id="21480-164">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="21480-165">Если в любой точке блока <xref:System.Transactions.TransactionScope> возникло исключение, метод `Complete` вызван не будет и при удалении транзакции <xref:System.Transactions.TransactionScope> в конце ее блока `using` будет произведен откат распределенной транзакции.</span><span class="sxs-lookup"><span data-stu-id="21480-165">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2
                // only when there is a chance that the transaction can commit.
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2
                ' only when there is a chance that the transaction can commit.
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="21480-166">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="21480-166">See also</span></span>

- [<span data-ttu-id="21480-167">Транзакции и параллелизм</span><span class="sxs-lookup"><span data-stu-id="21480-167">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="21480-168">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="21480-168">ADO.NET Overview</span></span>](ado-net-overview.md)
