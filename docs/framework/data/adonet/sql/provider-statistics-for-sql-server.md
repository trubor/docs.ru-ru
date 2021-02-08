---
description: Дополнительные сведения см. в статье статистика поставщика для SQL Server
title: Статистика поставщика для SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: ece5a6214d438ecac64e8738755d5fb5d0ed7245
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767600"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="a09b2-103">Статистика поставщика для SQL Server</span><span class="sxs-lookup"><span data-stu-id="a09b2-103">Provider Statistics for SQL Server</span></span>

<span data-ttu-id="a09b2-104">Начиная с .NET Framework 2.0, поставщик данных .NET Framework для SQL Server поддерживает получение статистики во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="a09b2-104">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="a09b2-105">Для включения статистики задайте для свойства <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> объекта <xref:System.Data.SqlClient.SqlConnection> значение `True` после создания допустимого объекта подключения.</span><span class="sxs-lookup"><span data-stu-id="a09b2-105">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="a09b2-106">После включения статистики ее можно просмотреть как "моментальный снимок во времени". Для этого нужно извлечь ссылку <xref:System.Collections.IDictionary> с помощью метода <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> объекта <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="a09b2-106">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="a09b2-107">Выполните перечисление списка в виде набора записей пар "имя-значение" в словаре.</span><span class="sxs-lookup"><span data-stu-id="a09b2-107">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="a09b2-108">Эти пары "имя-значение" не упорядочены.</span><span class="sxs-lookup"><span data-stu-id="a09b2-108">These name/value pairs are unordered.</span></span> <span data-ttu-id="a09b2-109">В любой момент можно вызвать метод <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> объекта <xref:System.Data.SqlClient.SqlConnection>, чтобы сбросить счетчики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-109">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="a09b2-110">Если сбор статистики не включен, исключение не создается.</span><span class="sxs-lookup"><span data-stu-id="a09b2-110">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="a09b2-111">Кроме того, если <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> вызывается без вызова метода <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> перед этим, то полученные значения являются начальными значениями для каждой записи.</span><span class="sxs-lookup"><span data-stu-id="a09b2-111">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="a09b2-112">Если вы включите статистику, запустите приложение на некоторое время, а затем отключите статистику, то полученные значения будут отражать значения, собранные до момента отключения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-112">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="a09b2-113">Все статистические значения собираются отдельно для каждого подключения.</span><span class="sxs-lookup"><span data-stu-id="a09b2-113">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="a09b2-114">Доступные статистические значения</span><span class="sxs-lookup"><span data-stu-id="a09b2-114">Statistical Values Available</span></span>  

 <span data-ttu-id="a09b2-115">В настоящее время доступны 18 различных элементов от поставщика Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a09b2-115">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="a09b2-116">Доступ ко множеству элементов производится через свойство **Count** ссылки интерфейса <xref:System.Collections.IDictionary>, возвращенной <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span><span class="sxs-lookup"><span data-stu-id="a09b2-116">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="a09b2-117">Для всех счетчиков статистики поставщика используется тип среды CLR <xref:System.Int64> (**long** в C# и Visual Basic) с внутренним представлением длиной 64 бита.</span><span class="sxs-lookup"><span data-stu-id="a09b2-117">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="a09b2-118">Максимальное значение типа данных **int64**, определенное полем **int64.MaxValue**, равно ((2^63)-1)).</span><span class="sxs-lookup"><span data-stu-id="a09b2-118">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="a09b2-119">Если значения для счетчиков достигли этого максимального значения, они больше не должны считаться точными.</span><span class="sxs-lookup"><span data-stu-id="a09b2-119">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="a09b2-120">Это означает, что **int64.MaxValue**-1((2^63)-2) по существу является максимальным действительным значением любого статистического показателя.</span><span class="sxs-lookup"><span data-stu-id="a09b2-120">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a09b2-121">Словарь используется для возврата статистики поставщика, так как число, имена и порядок возвращаемой статистики могут измениться в будущем.</span><span class="sxs-lookup"><span data-stu-id="a09b2-121">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="a09b2-122">Приложения не должны полагаться на определенное значение в словаре, но вместо этого должны проверять, есть ли значение и ветвь соответственно.</span><span class="sxs-lookup"><span data-stu-id="a09b2-122">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="a09b2-123">В следующей таблице описаны доступные текущие статистические значения.</span><span class="sxs-lookup"><span data-stu-id="a09b2-123">The following table describes the current statistical values available.</span></span> <span data-ttu-id="a09b2-124">Обратите внимание, что имена ключей для отдельных значений в региональных версиях Microsoft .NET Framework не локализованы.</span><span class="sxs-lookup"><span data-stu-id="a09b2-124">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="a09b2-125">Имя ключа</span><span class="sxs-lookup"><span data-stu-id="a09b2-125">Key Name</span></span>|<span data-ttu-id="a09b2-126">Описание</span><span class="sxs-lookup"><span data-stu-id="a09b2-126">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="a09b2-127">Возвращает число пакетов потока табличных данных (TDS), полученных поставщиком из SQL Server после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-127">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="a09b2-128">Возвращает число пакетов TDS, отправленных в SQL Server поставщиком после включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-128">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="a09b2-129">Для больших команд может потребоваться несколько буферов.</span><span class="sxs-lookup"><span data-stu-id="a09b2-129">Large commands can require multiple buffers.</span></span> <span data-ttu-id="a09b2-130">Например, если на сервер отправляется большая команда и требуется шесть пакетов, `ServerRoundtrips` увеличивается на единицу, а `BuffersSent` — на шесть.</span><span class="sxs-lookup"><span data-stu-id="a09b2-130">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="a09b2-131">Возвращает число байтов данных в пакетах TDS, полученных поставщиком от SQL Server после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-131">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="a09b2-132">Возвращает число байтов данных, отправленных в SQL Server в пакетах TDS после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-132">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="a09b2-133">Время в миллисекундах, в течение которого было открыто соединение после включения статистики (или полное время соединения, если статистика была включена до открытия соединения).</span><span class="sxs-lookup"><span data-stu-id="a09b2-133">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="a09b2-134">Возвращает число открытий курсора через подключение после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-134">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="a09b2-135">Обратите внимание, что результаты только для чтения и последовательного доступа, возвращаемые инструкциями SELECT, не считаются курсорами и поэтому не влияют на этот счетчик.</span><span class="sxs-lookup"><span data-stu-id="a09b2-135">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="a09b2-136">Возвращает совокупное количество времени в миллисекундах, которое поставщик потратил на обработку после включения статистики, с учетом того времени, которое потрачено на ожидание ответов от сервера, а также времени, потраченного на выполнение кода самим поставщиком.</span><span class="sxs-lookup"><span data-stu-id="a09b2-136">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="a09b2-137">К классам, включающим код времени, относятся:</span><span class="sxs-lookup"><span data-stu-id="a09b2-137">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="a09b2-138">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="a09b2-138">SqlConnection</span></span><br /><br /> <span data-ttu-id="a09b2-139">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="a09b2-139">SqlCommand</span></span><br /><br /> <span data-ttu-id="a09b2-140">SqlDataReader;</span><span class="sxs-lookup"><span data-stu-id="a09b2-140">SqlDataReader</span></span><br /><br /> <span data-ttu-id="a09b2-141">SqlDataAdapter;</span><span class="sxs-lookup"><span data-stu-id="a09b2-141">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="a09b2-142">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="a09b2-142">SqlTransaction</span></span><br /><br /> <span data-ttu-id="a09b2-143">SqlCommandBuilder.</span><span class="sxs-lookup"><span data-stu-id="a09b2-143">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="a09b2-144">Чтобы критические для производительности элементы были максимально мелкими, для следующих элементов не фиксируется время:</span><span class="sxs-lookup"><span data-stu-id="a09b2-144">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="a09b2-145">SqlDataReader;</span><span class="sxs-lookup"><span data-stu-id="a09b2-145">SqlDataReader</span></span><br /><br /> <span data-ttu-id="a09b2-146">оператор this[] (все перегрузки);</span><span class="sxs-lookup"><span data-stu-id="a09b2-146">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="a09b2-147">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="a09b2-147">GetBoolean</span></span><br /><br /> <span data-ttu-id="a09b2-148">GetChar</span><span class="sxs-lookup"><span data-stu-id="a09b2-148">GetChar</span></span><br /><br /> <span data-ttu-id="a09b2-149">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="a09b2-149">GetDateTime</span></span><br /><br /> <span data-ttu-id="a09b2-150">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="a09b2-150">GetDecimal</span></span><br /><br /> <span data-ttu-id="a09b2-151">GetDouble</span><span class="sxs-lookup"><span data-stu-id="a09b2-151">GetDouble</span></span><br /><br /> <span data-ttu-id="a09b2-152">GetFloat</span><span class="sxs-lookup"><span data-stu-id="a09b2-152">GetFloat</span></span><br /><br /> <span data-ttu-id="a09b2-153">GetGuid</span><span class="sxs-lookup"><span data-stu-id="a09b2-153">GetGuid</span></span><br /><br /> <span data-ttu-id="a09b2-154">GetInt16</span><span class="sxs-lookup"><span data-stu-id="a09b2-154">GetInt16</span></span><br /><br /> <span data-ttu-id="a09b2-155">GetInt32</span><span class="sxs-lookup"><span data-stu-id="a09b2-155">GetInt32</span></span><br /><br /> <span data-ttu-id="a09b2-156">GetInt64</span><span class="sxs-lookup"><span data-stu-id="a09b2-156">GetInt64</span></span><br /><br /> <span data-ttu-id="a09b2-157">GetName</span><span class="sxs-lookup"><span data-stu-id="a09b2-157">GetName</span></span><br /><br /> <span data-ttu-id="a09b2-158">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="a09b2-158">GetOrdinal</span></span><br /><br /> <span data-ttu-id="a09b2-159">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="a09b2-159">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="a09b2-160">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="a09b2-160">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="a09b2-161">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="a09b2-161">GetSqlByte</span></span><br /><br /> <span data-ttu-id="a09b2-162">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="a09b2-162">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="a09b2-163">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="a09b2-163">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="a09b2-164">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="a09b2-164">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="a09b2-165">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="a09b2-165">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="a09b2-166">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="a09b2-166">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="a09b2-167">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="a09b2-167">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="a09b2-168">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="a09b2-168">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="a09b2-169">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="a09b2-169">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="a09b2-170">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="a09b2-170">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="a09b2-171">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="a09b2-171">GetSqlString</span></span><br /><br /> <span data-ttu-id="a09b2-172">GetString</span><span class="sxs-lookup"><span data-stu-id="a09b2-172">GetString</span></span><br /><br /> <span data-ttu-id="a09b2-173">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="a09b2-173">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="a09b2-174">Возвращает общее число инструкций INSERT, DELETE и UPDATE, выполненных через подключение после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-174">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="a09b2-175">Возвращает общее число строк, затронутых инструкциями INSERT, DELETE и UPDATE, которые выполнялись через подключение после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-175">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="a09b2-176">Возвращает совокупное количество времени в миллисекундах, которое поставщик потратил на ожидание ответов от сервера после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-176">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="a09b2-177">Возвращает число подготовленных команд, выполненных через подключение после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-177">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="a09b2-178">Возвращает число инструкций, подготовленных через подключение после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-178">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="a09b2-179">Возвращает число инструкций SELECT, выполненных через подключение после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-179">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="a09b2-180">Сюда входят инструкции FETCH для получения строк из курсоров, а счетчик для инструкций SELECT обновляется по достижении конца <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="a09b2-180">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="a09b2-181">Возвращает число строк, выбранных после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-181">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="a09b2-182">Этот счетчик отражает все строки, формируемые инструкциями SQL, даже те, которые фактически не использовались вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="a09b2-182">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="a09b2-183">Например, закрытие читателя данных до считывания всего результирующего набора не повлияет на число.</span><span class="sxs-lookup"><span data-stu-id="a09b2-183">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="a09b2-184">Сюда входят строки, полученные из курсоров с помощью инструкций FETCH.</span><span class="sxs-lookup"><span data-stu-id="a09b2-184">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="a09b2-185">Возвращает число команд, отправленных серверу в рамках подключения, и получения ответа после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-185">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="a09b2-186">Возвращает количество результирующих наборов, которые применялись после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-186">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="a09b2-187">Например, это может быть любой результирующий набор, возвращаемый клиенту.</span><span class="sxs-lookup"><span data-stu-id="a09b2-187">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="a09b2-188">Для курсоров каждая операция выборки или получения записи блока считается независимым результирующим набором.</span><span class="sxs-lookup"><span data-stu-id="a09b2-188">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="a09b2-189">Возвращает число пользовательских транзакций, запущенных после начала использования приложением поставщика и включения статистики (в том числе откаты).</span><span class="sxs-lookup"><span data-stu-id="a09b2-189">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="a09b2-190">Если подключение работает при включенной автоматической фиксации, каждая команда считается транзакцией.</span><span class="sxs-lookup"><span data-stu-id="a09b2-190">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="a09b2-191">Этот счетчик увеличивает число транзакций, как только выполняется инструкция BEGIN TRAN, независимо от того, была ли транзакция позже зафиксирована или подвержена откату.</span><span class="sxs-lookup"><span data-stu-id="a09b2-191">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="a09b2-192">Возвращает число неподготовленных инструкций, выполненных через подключение после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="a09b2-192">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="a09b2-193">Получение значения</span><span class="sxs-lookup"><span data-stu-id="a09b2-193">Retrieving a Value</span></span>  

 <span data-ttu-id="a09b2-194">В следующем консольном приложении показано, как включить статистику для подключения, получить четыре отдельных статистических значения и записать их в окно консоли.</span><span class="sxs-lookup"><span data-stu-id="a09b2-194">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a09b2-195">В следующем примере используется образец базы данных **AdventureWorks**, входящий в состав SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a09b2-195">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="a09b2-196">В строке подключения в примере кода предполагается, что база данных установлена и доступна на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="a09b2-196">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="a09b2-197">При необходимости измените строку подключения для вашей среды.</span><span class="sxs-lookup"><span data-stu-id="a09b2-197">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="a09b2-198">Получение всех значений</span><span class="sxs-lookup"><span data-stu-id="a09b2-198">Retrieving All Values</span></span>  

 <span data-ttu-id="a09b2-199">В следующем консольном приложении показано, как включить статистику для подключения, получить все доступные статистические значения с помощью перечислителя и записать их в окно консоли.</span><span class="sxs-lookup"><span data-stu-id="a09b2-199">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a09b2-200">В следующем примере используется образец базы данных **AdventureWorks**, входящий в состав SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a09b2-200">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="a09b2-201">В строке подключения в примере кода предполагается, что база данных установлена и доступна на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="a09b2-201">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="a09b2-202">При необходимости измените строку подключения для вашей среды.</span><span class="sxs-lookup"><span data-stu-id="a09b2-202">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a09b2-203">См. также</span><span class="sxs-lookup"><span data-stu-id="a09b2-203">See also</span></span>

- [<span data-ttu-id="a09b2-204">SQL Server и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a09b2-204">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="a09b2-205">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a09b2-205">ADO.NET Overview</span></span>](../ado-net-overview.md)
