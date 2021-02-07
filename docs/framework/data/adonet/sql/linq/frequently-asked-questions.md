---
description: 'Дополнительные сведения: часто задаваемые вопросы'
title: Часто задаваемые вопросы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 476e9adc3dc88bce786b8b8423e05e800c821320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739083"
---
# <a name="frequently-asked-questions"></a><span data-ttu-id="8c242-103">Часто задаваемые вопросы</span><span class="sxs-lookup"><span data-stu-id="8c242-103">Frequently Asked Questions</span></span>

<span data-ttu-id="8c242-104">В следующих разделах содержатся ответы на некоторые распространенные проблемы, которые могут возникнуть при реализации LINQ.</span><span class="sxs-lookup"><span data-stu-id="8c242-104">The following sections answer some common issues that you might encounter when you implement LINQ.</span></span>

<span data-ttu-id="8c242-105">Дополнительные проблемы описаны в [статье Устранение неполадок](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="8c242-105">Additional issues are addressed in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="cannot-connect"></a><span data-ttu-id="8c242-106">Не удается подключиться</span><span class="sxs-lookup"><span data-stu-id="8c242-106">Cannot Connect</span></span>

<span data-ttu-id="8c242-107">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-107">Q.</span></span> <span data-ttu-id="8c242-108">Не удается соединиться с базой данных.</span><span class="sxs-lookup"><span data-stu-id="8c242-108">I cannot connect to my database.</span></span>

<span data-ttu-id="8c242-109">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-109">A.</span></span> <span data-ttu-id="8c242-110">Убедитесь в правильности строки подключения и в том, что экземпляр SQL Server работает.</span><span class="sxs-lookup"><span data-stu-id="8c242-110">Make sure your connection string is correct and that your SQL Server instance is running.</span></span> <span data-ttu-id="8c242-111">Обратите внимание, что для [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] требуется включенный протокол именованных каналов.</span><span class="sxs-lookup"><span data-stu-id="8c242-111">Note also that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requires the Named Pipes protocol to be enabled.</span></span> <span data-ttu-id="8c242-112">Дополнительные сведения см. [в разделе обучение по пошаговым руководствам](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="8c242-112">For more information, see [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

## <a name="changes-to-database-lost"></a><span data-ttu-id="8c242-113">Потеряны изменения, внесенные в базу данных</span><span class="sxs-lookup"><span data-stu-id="8c242-113">Changes to Database Lost</span></span>

<span data-ttu-id="8c242-114">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-114">Q.</span></span> <span data-ttu-id="8c242-115">В базу данных были внесены изменения, однако при повторном запуске приложения их там не оказалось.</span><span class="sxs-lookup"><span data-stu-id="8c242-115">I made a change to data in the database, but when I reran my application, the change was no longer there.</span></span>

<span data-ttu-id="8c242-116">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-116">A.</span></span> <span data-ttu-id="8c242-117">Проверьте, что для сохранения результатов в базе данных был вызван метод <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c242-117">Make sure that you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> to save results to the database.</span></span>

## <a name="database-connection-open-how-long"></a><span data-ttu-id="8c242-118">Как долго сохраняется открытым соединение с базой данных?</span><span class="sxs-lookup"><span data-stu-id="8c242-118">Database Connection: Open How Long?</span></span>

<span data-ttu-id="8c242-119">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-119">Q.</span></span> <span data-ttu-id="8c242-120">Как долго соединение с базой данных будет оставаться открытым?</span><span class="sxs-lookup"><span data-stu-id="8c242-120">How long does my database connection remain open?</span></span>

<span data-ttu-id="8c242-121">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-121">A.</span></span> <span data-ttu-id="8c242-122">Как правило, подключение остается открытым до тех пор, пока не будут использованы результаты запроса.</span><span class="sxs-lookup"><span data-stu-id="8c242-122">A connection typically remains open until you consume the query results.</span></span> <span data-ttu-id="8c242-123">Если планируется выделить время для обработки и кэширования всех результатов, к запросу следует применить <xref:System.Linq.Enumerable.ToList%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c242-123">If you expect to take time to process all the results and are not opposed to caching the results, apply <xref:System.Linq.Enumerable.ToList%2A> to the query.</span></span> <span data-ttu-id="8c242-124">В типичных сценариях, где каждый объект обрабатывается только один раз, потоковая модель является предпочтительной в `DataReader` и [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c242-124">In common scenarios where each object is processed only one time, the streaming model is superior in both `DataReader` and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

<span data-ttu-id="8c242-125">Точные сведения об использовании подключения зависят от следующих моментов.</span><span class="sxs-lookup"><span data-stu-id="8c242-125">The exact details of connection usage depend on the following:</span></span>

- <span data-ttu-id="8c242-126">Состояние подключения, если <xref:System.Data.Linq.DataContext> создан с помощью объекта подключения.</span><span class="sxs-lookup"><span data-stu-id="8c242-126">Connection status if the <xref:System.Data.Linq.DataContext> is constructed with a connection object.</span></span>

- <span data-ttu-id="8c242-127">Параметры строки подключения (например, включение режима MARS).</span><span class="sxs-lookup"><span data-stu-id="8c242-127">Connection string settings (for example, enabling Multiple Active Result Sets (MARS).</span></span> <span data-ttu-id="8c242-128">Дополнительные сведения см. в разделе [Несколько активных результирующих наборов (MARS)](../multiple-active-result-sets-mars.md).</span><span class="sxs-lookup"><span data-stu-id="8c242-128">For more information, see [Multiple Active Result Sets (MARS)](../multiple-active-result-sets-mars.md).</span></span>

## <a name="updating-without-querying"></a><span data-ttu-id="8c242-129">Обновление без выполнения запросов</span><span class="sxs-lookup"><span data-stu-id="8c242-129">Updating Without Querying</span></span>

<span data-ttu-id="8c242-130">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-130">Q.</span></span> <span data-ttu-id="8c242-131">Можно ли обновить данные таблицы, не отправляя запрос в базу данных?</span><span class="sxs-lookup"><span data-stu-id="8c242-131">Can I update table data without first querying the database?</span></span>

<span data-ttu-id="8c242-132">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-132">A.</span></span> <span data-ttu-id="8c242-133">Хотя в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] отсутствуют команды обновления на основе наборов, для обновления без выполнения запроса можно воспользоваться любым из следующих способов.</span><span class="sxs-lookup"><span data-stu-id="8c242-133">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not have set-based update commands, you can use either of the following techniques to update without first querying:</span></span>

- <span data-ttu-id="8c242-134">Чтобы отправить код SQL, используйте <xref:System.Data.Linq.DataContext.ExecuteCommand%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c242-134">Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to send SQL code.</span></span>

- <span data-ttu-id="8c242-135">Создайте новый экземпляр объекта и инициализируйте все текущие значения (поля), влияющие на обновление.</span><span class="sxs-lookup"><span data-stu-id="8c242-135">Create a new instance of the object and initialize all the current values (fields) that affect the update.</span></span> <span data-ttu-id="8c242-136">Затем прикрепите объект к <xref:System.Data.Linq.DataContext> с помощью <xref:System.Data.Linq.Table%601.Attach%2A> и отредактируйте поле, которое нужно изменить.</span><span class="sxs-lookup"><span data-stu-id="8c242-136">Then attach the object to the <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.Table%601.Attach%2A> and modify the field you want to change.</span></span>

## <a name="unexpected-query-results"></a><span data-ttu-id="8c242-137">Неожиданные результаты запроса</span><span class="sxs-lookup"><span data-stu-id="8c242-137">Unexpected Query Results</span></span>

<span data-ttu-id="8c242-138">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-138">Q.</span></span> <span data-ttu-id="8c242-139">Запрос возвращает непредвиденные результаты.</span><span class="sxs-lookup"><span data-stu-id="8c242-139">My query is returning unexpected results.</span></span> <span data-ttu-id="8c242-140">Как узнать, что случилось?</span><span class="sxs-lookup"><span data-stu-id="8c242-140">How can I inspect what is occurring?</span></span>

<span data-ttu-id="8c242-141">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-141">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8c242-142">предусматривает несколько средств для проверки создаваемого кода SQL.</span><span class="sxs-lookup"><span data-stu-id="8c242-142">provides several tools for inspecting the SQL code it generates.</span></span> <span data-ttu-id="8c242-143">Одним из наиболее важных <xref:System.Data.Linq.DataContext.Log%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c242-143">One of the most important is <xref:System.Data.Linq.DataContext.Log%2A>.</span></span> <span data-ttu-id="8c242-144">Дополнительные сведения см. в разделе [Поддержка отладки](debugging-support.md).</span><span class="sxs-lookup"><span data-stu-id="8c242-144">For more information, see [Debugging Support](debugging-support.md).</span></span>

## <a name="unexpected-stored-procedure-results"></a><span data-ttu-id="8c242-145">Неожиданные результаты хранимой процедуры</span><span class="sxs-lookup"><span data-stu-id="8c242-145">Unexpected Stored Procedure Results</span></span>

<span data-ttu-id="8c242-146">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-146">Q.</span></span> <span data-ttu-id="8c242-147">Имеется хранимая процедура, возвращаемое значение которой вычислено с помощью функции `MAX()`.</span><span class="sxs-lookup"><span data-stu-id="8c242-147">I have a stored procedure whose return value is calculated by `MAX()`.</span></span> <span data-ttu-id="8c242-148">При перетаскивании хранимой процедуры в область конструктора O/R возвращаемое значение неверно.</span><span class="sxs-lookup"><span data-stu-id="8c242-148">When I drag the stored procedure to the O/R Designer surface, the return value is not correct.</span></span>

<span data-ttu-id="8c242-149">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-149">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8c242-150">обеспечивает два способа возврата значений, сформированных в базе данных, с помощью хранимых процедур.</span><span class="sxs-lookup"><span data-stu-id="8c242-150">provides two ways to return database-generated values by way of stored procedures:</span></span>

- <span data-ttu-id="8c242-151">Путем именования выходного результата.</span><span class="sxs-lookup"><span data-stu-id="8c242-151">By naming the output result.</span></span>

- <span data-ttu-id="8c242-152">Путем явного указания выходного параметра.</span><span class="sxs-lookup"><span data-stu-id="8c242-152">By explicitly specifying an output parameter.</span></span>

<span data-ttu-id="8c242-153">Ниже представлен пример неверных выходных данных.</span><span class="sxs-lookup"><span data-stu-id="8c242-153">The following is an example of incorrect output.</span></span> <span data-ttu-id="8c242-154">Поскольку [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] не может сопоставить результаты, он всегда возвращает 0.</span><span class="sxs-lookup"><span data-stu-id="8c242-154">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot map the results, it always returns 0:</span></span>

```sql
create procedure proc2

as

begin

select max(i) from t where name like 'hello'

end
```

<span data-ttu-id="8c242-155">Ниже представлен пример правильных выходных данных с использованием выходного параметра.</span><span class="sxs-lookup"><span data-stu-id="8c242-155">The following is an example of correct output by using an output parameter:</span></span>

```sql
create procedure proc2

@result int OUTPUT

as

select @result = MAX(i) from t where name like 'hello'

go
```

<span data-ttu-id="8c242-156">Ниже представлен пример правильных выходных данных с именованием выходного результата.</span><span class="sxs-lookup"><span data-stu-id="8c242-156">The following is an example of correct output by naming the output result:</span></span>

```sql
create procedure proc2

as

begin

select nax(i) AS MaxResult from t where name like 'hello'

end
```

<span data-ttu-id="8c242-157">Дополнительные сведения см. в разделе [Настройка операций с помощью хранимых процедур](customizing-operations-by-using-stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8c242-157">For more information, see [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md).</span></span>

## <a name="serialization-errors"></a><span data-ttu-id="8c242-158">Ошибки сериализации</span><span class="sxs-lookup"><span data-stu-id="8c242-158">Serialization Errors</span></span>

<span data-ttu-id="8c242-159">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-159">Q.</span></span> <span data-ttu-id="8c242-160">При попытке сериализации возникает следующая ошибка: "тип" System. Data. LINQ. ChangeTracker + Стандардчанжетраккер "... не помечен как сериализуемый.</span><span class="sxs-lookup"><span data-stu-id="8c242-160">When I try to serialize, I get the following error: "Type 'System.Data.Linq.ChangeTracker+StandardChangeTracker' ... is not marked as serializable."</span></span>

<span data-ttu-id="8c242-161">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-161">A.</span></span> <span data-ttu-id="8c242-162">Формирование кода в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] поддерживает сериализацию <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8c242-162">Code generation in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports <xref:System.Runtime.Serialization.DataContractSerializer> serialization.</span></span> <span data-ttu-id="8c242-163">Оно не поддерживает <xref:System.Xml.Serialization.XmlSerializer> или <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="8c242-163">It does not support <xref:System.Xml.Serialization.XmlSerializer> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="8c242-164">Дополнительные сведения см. в разделе [Сериализация](serialization.md).</span><span class="sxs-lookup"><span data-stu-id="8c242-164">For more information, see [Serialization](serialization.md).</span></span>

## <a name="multiple-dbml-files"></a><span data-ttu-id="8c242-165">Несколько DBML-файлов</span><span class="sxs-lookup"><span data-stu-id="8c242-165">Multiple DBML Files</span></span>

<span data-ttu-id="8c242-166">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-166">Q.</span></span> <span data-ttu-id="8c242-167">При работе с несколькими DBML-файлами, использующими общие таблицы, возникает ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="8c242-167">When I have multiple DBML files that share some tables in common, I get a compiler error.</span></span>

<span data-ttu-id="8c242-168">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-168">A.</span></span> <span data-ttu-id="8c242-169">Задайте для свойств **пространства имен контекста** и **пространства имен сущности** реляционный конструктор объектов различные значения для каждого DBML-файла.</span><span class="sxs-lookup"><span data-stu-id="8c242-169">Set the **Context Namespace** and **Entity Namespace** properties from the Object Relational Designer to a distinct value for each DBML file.</span></span> <span data-ttu-id="8c242-170">Это способ исключает конфликты имен/пространств имен.</span><span class="sxs-lookup"><span data-stu-id="8c242-170">This approach eliminates the name/namespace collision.</span></span>

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a><span data-ttu-id="8c242-171">Предупреждение явного задания значений, созданных базой данных, в Insert или Update</span><span class="sxs-lookup"><span data-stu-id="8c242-171">Avoiding Explicit Setting of Database-Generated Values on Insert or Update</span></span>

<span data-ttu-id="8c242-172">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-172">Q.</span></span> <span data-ttu-id="8c242-173">В базе данных имеется таблица со столбцом `DateCreated`, в качестве значения по умолчанию которой указана функция SQL `Getdate()`.</span><span class="sxs-lookup"><span data-stu-id="8c242-173">I have a database table with a `DateCreated` column that defaults to SQL `Getdate()`.</span></span> <span data-ttu-id="8c242-174">При попытке вставить новую запись с помощью [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] возвращается значение `NULL`.</span><span class="sxs-lookup"><span data-stu-id="8c242-174">When I try to insert a new record by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the value gets set to `NULL`.</span></span> <span data-ttu-id="8c242-175">Хотя ожидается заданное по умолчанию значение базы данных.</span><span class="sxs-lookup"><span data-stu-id="8c242-175">I would expect it to be set to the database default.</span></span>

<span data-ttu-id="8c242-176">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-176">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8c242-177">автоматически обрабатывает данную ситуацию для столбцов identity (автоувеличение), rowguidcol (формируемые базой данных идентификаторы GUID) и timestamp.</span><span class="sxs-lookup"><span data-stu-id="8c242-177">handles this situation automatically for identity (auto-increment) and rowguidcol (database-generated GUID) and timestamp columns.</span></span> <span data-ttu-id="8c242-178">В других случаях следует задавать <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> = `true` Свойства и вручную <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = <xref:System.Data.Linq.Mapping.AutoSync.Always> / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> .</span><span class="sxs-lookup"><span data-stu-id="8c242-178">In other cases, you should manually set <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` and <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> properties.</span></span>

## <a name="multiple-dataloadoptions"></a><span data-ttu-id="8c242-179">Несколько параметров DataLoadOptions</span><span class="sxs-lookup"><span data-stu-id="8c242-179">Multiple DataLoadOptions</span></span>

<span data-ttu-id="8c242-180">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-180">Q.</span></span> <span data-ttu-id="8c242-181">Можно ли задать дополнительные параметры загрузки, не переопределяя исходные?</span><span class="sxs-lookup"><span data-stu-id="8c242-181">Can I specify additional load options without overwriting the first?</span></span>

<span data-ttu-id="8c242-182">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-182">A.</span></span> <span data-ttu-id="8c242-183">Да.</span><span class="sxs-lookup"><span data-stu-id="8c242-183">Yes.</span></span> <span data-ttu-id="8c242-184">Исходные параметры не переопределяются, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="8c242-184">The first is not overwritten, as in the following example:</span></span>

```vb
Dim dlo As New DataLoadOptions()
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)
```

```csharp
DataLoadOptions dlo = new DataLoadOptions();
dlo.LoadWith<Order>(o => o.Customer);
dlo.LoadWith<Order>(o => o.OrderDetails);
```

## <a name="errors-using-sql-compact-35"></a><span data-ttu-id="8c242-185">Ошибки при использовании SQL Compact 3.5</span><span class="sxs-lookup"><span data-stu-id="8c242-185">Errors Using SQL Compact 3.5</span></span>

<span data-ttu-id="8c242-186">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-186">Q.</span></span> <span data-ttu-id="8c242-187">При перетаскивании таблиц из базы данных SQL Server Compact 3,5 возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="8c242-187">I get an error when I drag tables out of a SQL Server Compact 3.5 database.</span></span>

<span data-ttu-id="8c242-188">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-188">A.</span></span> <span data-ttu-id="8c242-189">Реляционный конструктор объектов не поддерживает SQL Server Compact 3,5, хотя [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Среда выполнения выполняет.</span><span class="sxs-lookup"><span data-stu-id="8c242-189">The Object Relational Designer does not support SQL Server Compact 3.5, although the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime does.</span></span> <span data-ttu-id="8c242-190">В этом случае необходимо создать собственные классы сущностей и добавить соответствующие атрибуты.</span><span class="sxs-lookup"><span data-stu-id="8c242-190">In this situation, you must create your own entity classes and add the appropriate attributes.</span></span>

## <a name="errors-in-inheritance-relationships"></a><span data-ttu-id="8c242-191">Ошибки в связях наследования</span><span class="sxs-lookup"><span data-stu-id="8c242-191">Errors in Inheritance Relationships</span></span>

<span data-ttu-id="8c242-192">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-192">Q.</span></span> <span data-ttu-id="8c242-193">Я использовал фигуру наследования панели элементов в реляционный конструктор объектов для соединения двух сущностей, но выдает ошибки.</span><span class="sxs-lookup"><span data-stu-id="8c242-193">I used the toolbox inheritance shape in the Object Relational Designer to connect two entities, but I get errors.</span></span>

<span data-ttu-id="8c242-194">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-194">A.</span></span> <span data-ttu-id="8c242-195">Простого создания связи недостаточно.</span><span class="sxs-lookup"><span data-stu-id="8c242-195">Creating the relationship is not enough.</span></span> <span data-ttu-id="8c242-196">Необходимо предоставить сведения, такие как столбец дискриминатора, значение дискриминатора базового класса и значение дискриминатора производного класса.</span><span class="sxs-lookup"><span data-stu-id="8c242-196">You must provide information such as the discriminator column, base class discriminator value, and derived class discriminator value.</span></span>

## <a name="provider-model"></a><span data-ttu-id="8c242-197">Модель поставщика</span><span class="sxs-lookup"><span data-stu-id="8c242-197">Provider Model</span></span>

<span data-ttu-id="8c242-198">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-198">Q.</span></span> <span data-ttu-id="8c242-199">Доступна ли модель общего поставщика?</span><span class="sxs-lookup"><span data-stu-id="8c242-199">Is a public provider model available?</span></span>

<span data-ttu-id="8c242-200">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-200">A.</span></span> <span data-ttu-id="8c242-201">Такая модель отсутствует.</span><span class="sxs-lookup"><span data-stu-id="8c242-201">No public provider model is available.</span></span> <span data-ttu-id="8c242-202">В настоящее время [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] поддерживает только SQL Server и SQL Server Compact 3,5.</span><span class="sxs-lookup"><span data-stu-id="8c242-202">At this time, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports SQL Server and SQL Server Compact 3.5 only.</span></span>

## <a name="sql-injection-attacks"></a><span data-ttu-id="8c242-203">Атаки путем внедрения кода SQL</span><span class="sxs-lookup"><span data-stu-id="8c242-203">SQL-Injection Attacks</span></span>

<span data-ttu-id="8c242-204">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-204">Q.</span></span> <span data-ttu-id="8c242-205">Каким образом [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] защищен от атак путем внедрения кода SQL?</span><span class="sxs-lookup"><span data-stu-id="8c242-205">How is [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] protected from SQL-injection attacks?</span></span>

<span data-ttu-id="8c242-206">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-206">A.</span></span> <span data-ttu-id="8c242-207">Внедрение SQL-кода представляло серьезную угрозу для традиционных SQL-запросов, создаваемых путем объединения данных, вводимых пользователем.</span><span class="sxs-lookup"><span data-stu-id="8c242-207">SQL injection has been a significant risk for traditional SQL queries formed by concatenating user input.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8c242-208">предотвращает подобное внедрение за счет использования в запросах объектов <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="8c242-208">avoids such injection by using <xref:System.Data.SqlClient.SqlParameter> in queries.</span></span> <span data-ttu-id="8c242-209">Вводимые данные преобразуются в значения параметров.</span><span class="sxs-lookup"><span data-stu-id="8c242-209">User input is turned into parameter values.</span></span> <span data-ttu-id="8c242-210">Этот способ исключает использование вредоносных команд из введенных данных.</span><span class="sxs-lookup"><span data-stu-id="8c242-210">This approach prevents malicious commands from being used from customer input.</span></span>

## <a name="changing-read-only-flag-in-dbml-files"></a><span data-ttu-id="8c242-211">Создание флага "Только чтение" в файлах DBML.</span><span class="sxs-lookup"><span data-stu-id="8c242-211">Changing Read-only Flag in DBML Files</span></span>

<span data-ttu-id="8c242-212">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-212">Q.</span></span> <span data-ttu-id="8c242-213">Как можно избавиться от некоторых методов задания свойств при создании объектной модели из файла DBM?</span><span class="sxs-lookup"><span data-stu-id="8c242-213">How do I eliminate setters from some properties when I create an object model from a DBML file?</span></span>

<span data-ttu-id="8c242-214">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-214">A.</span></span> <span data-ttu-id="8c242-215">Выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8c242-215">Take the following steps for this advanced scenario:</span></span>

1. <span data-ttu-id="8c242-216">В файле DBML измените свойство, присвоив флагу <xref:System.Data.Linq.ITable.IsReadOnly%2A> значение `True`.</span><span class="sxs-lookup"><span data-stu-id="8c242-216">In the .dbml file, modify the property by changing the <xref:System.Data.Linq.ITable.IsReadOnly%2A> flag to `True`.</span></span>

2. <span data-ttu-id="8c242-217">Добавьте разделяемый класс.</span><span class="sxs-lookup"><span data-stu-id="8c242-217">Add a partial class.</span></span> <span data-ttu-id="8c242-218">Создайте конструктор с параметрами для членов, доступных только для чтения.</span><span class="sxs-lookup"><span data-stu-id="8c242-218">Create a constructor with parameters for the read-only members.</span></span>

3. <span data-ttu-id="8c242-219">Проверьте значение по умолчанию <xref:System.Data.Linq.Mapping.UpdateCheck> (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>), чтобы определить, является ли оно правильным для приложения.</span><span class="sxs-lookup"><span data-stu-id="8c242-219">Review the default <xref:System.Data.Linq.Mapping.UpdateCheck> value (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) to determine whether that is the correct value for your application.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="8c242-220">Если вы используете реляционный конструктор объектов в Visual Studio, изменения могут быть перезаписаны.</span><span class="sxs-lookup"><span data-stu-id="8c242-220">If you are using the Object Relational Designer in Visual Studio, your changes might be overwritten.</span></span>

## <a name="aptca"></a><span data-ttu-id="8c242-221">APTCA</span><span class="sxs-lookup"><span data-stu-id="8c242-221">APTCA</span></span>

<span data-ttu-id="8c242-222">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-222">Q.</span></span> <span data-ttu-id="8c242-223">Помечена ли сборка System.Data.Linq для использования кодом с частичным доверием?</span><span class="sxs-lookup"><span data-stu-id="8c242-223">Is System.Data.Linq marked for use by partially trusted code?</span></span>

<span data-ttu-id="8c242-224">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-224">A.</span></span> <span data-ttu-id="8c242-225">Да, System.Data.Linq.dll сборка состоит из платформа .NET Framework сборок, помеченных <xref:System.Security.AllowPartiallyTrustedCallersAttribute> атрибутом.</span><span class="sxs-lookup"><span data-stu-id="8c242-225">Yes, the System.Data.Linq.dll assembly is among those .NET Framework assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="8c242-226">Без этой маркировки сборки в платформа .NET Framework предназначены для использования только полностью доверенным кодом.</span><span class="sxs-lookup"><span data-stu-id="8c242-226">Without this marking, assemblies in the .NET Framework are intended for use only by fully trusted code.</span></span>

<span data-ttu-id="8c242-227">Основной сценарий в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] для разрешения частично доверенных вызывающих объектов заключается в том [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , чтобы обеспечить доступ к сборке из веб-приложений, где конфигурация *доверия* является средней.</span><span class="sxs-lookup"><span data-stu-id="8c242-227">The principal scenario in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] for allowing partially trusted callers is to enable the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly to be accessed from Web applications, where the *trust* configuration is Medium.</span></span>

## <a name="mapping-data-from-multiple-tables"></a><span data-ttu-id="8c242-228">Сопоставление данных из нескольких таблиц</span><span class="sxs-lookup"><span data-stu-id="8c242-228">Mapping Data from Multiple Tables</span></span>

<span data-ttu-id="8c242-229">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-229">Q.</span></span> <span data-ttu-id="8c242-230">Данные в сущность поступают из нескольких таблиц.</span><span class="sxs-lookup"><span data-stu-id="8c242-230">The data in my entity comes from multiple tables.</span></span> <span data-ttu-id="8c242-231">Как их сопоставить?</span><span class="sxs-lookup"><span data-stu-id="8c242-231">How do I map it?</span></span>

<span data-ttu-id="8c242-232">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-232">A.</span></span> <span data-ttu-id="8c242-233">В базе данных можно создать представление и сопоставить с ним сущность.</span><span class="sxs-lookup"><span data-stu-id="8c242-233">You can create a view in a database and map the entity to the view.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8c242-234">создает одинаковый SQL-код для представлений и таблиц.</span><span class="sxs-lookup"><span data-stu-id="8c242-234">generates the same SQL for views as it does for tables.</span></span>

> [!NOTE]
> <span data-ttu-id="8c242-235">В данном сценарии использование представлений имеет ограничения.</span><span class="sxs-lookup"><span data-stu-id="8c242-235">The use of views in this scenario has limitations.</span></span> <span data-ttu-id="8c242-236">Способ работает с максимальной безопасностью, если операции, выполняемые в <xref:System.Data.Linq.Table%601>, поддерживаются базовым представлением.</span><span class="sxs-lookup"><span data-stu-id="8c242-236">This approach works most safely when the operations performed on <xref:System.Data.Linq.Table%601> are supported by the underlying view.</span></span> <span data-ttu-id="8c242-237">Операции, которые предполагается использовать, известны только вам.</span><span class="sxs-lookup"><span data-stu-id="8c242-237">Only you know which operations are intended.</span></span> <span data-ttu-id="8c242-238">Например, большинство приложений доступны только для чтения, а другой немалым номер выполняет `Create` / `Update` / `Delete` операции только с помощью хранимых процедур в представлениях.</span><span class="sxs-lookup"><span data-stu-id="8c242-238">For example, most applications are read-only, and another sizeable number perform `Create`/`Update`/`Delete` operations only by using stored procedures against views.</span></span>

## <a name="connection-pooling"></a><span data-ttu-id="8c242-239">Объединение подключений в пул</span><span class="sxs-lookup"><span data-stu-id="8c242-239">Connection Pooling</span></span>

<span data-ttu-id="8c242-240">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-240">Q.</span></span> <span data-ttu-id="8c242-241">Существует ли конструкция, которая поможет в организации пула объектов <xref:System.Data.Linq.DataContext>?</span><span class="sxs-lookup"><span data-stu-id="8c242-241">Is there a construct that can help with <xref:System.Data.Linq.DataContext> pooling?</span></span>

<span data-ttu-id="8c242-242">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-242">A.</span></span> <span data-ttu-id="8c242-243">Не пытайтесь повторно использовать экземпляры <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="8c242-243">Do not try to reuse instances of <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="8c242-244">Каждый <xref:System.Data.Linq.DataContext> сохраняет состояние (включая кэш идентификации) для одного определенного сеанса редактирования/запроса.</span><span class="sxs-lookup"><span data-stu-id="8c242-244">Each <xref:System.Data.Linq.DataContext> maintains state (including an identity cache) for one particular edit/query session.</span></span> <span data-ttu-id="8c242-245">Для получения новых экземпляров на основе текущего состояния базы данных используйте новый <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="8c242-245">To obtain new instances based on the current state of the database, use a new <xref:System.Data.Linq.DataContext>.</span></span>

<span data-ttu-id="8c242-246">Вы по-прежнему можете использовать базовые пулы соединений ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8c242-246">You can still use underlying ADO.NET connection pooling.</span></span> <span data-ttu-id="8c242-247">Дополнительные сведения см. в разделе [Пулы подключений SQL Server (ADO.NET)](../../sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="8c242-247">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../sql-server-connection-pooling.md).</span></span>

## <a name="second-datacontext-is-not-updated"></a><span data-ttu-id="8c242-248">Не выполняется обновление второго DataContext</span><span class="sxs-lookup"><span data-stu-id="8c242-248">Second DataContext Is Not Updated</span></span>

<span data-ttu-id="8c242-249">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-249">Q.</span></span> <span data-ttu-id="8c242-250">Для хранения значения в базе данных использовался один экземпляр <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="8c242-250">I used one instance of <xref:System.Data.Linq.DataContext> to store values in the database.</span></span> <span data-ttu-id="8c242-251">Однако второй <xref:System.Data.Linq.DataContext> в той же базе данных не отражает обновленные значения.</span><span class="sxs-lookup"><span data-stu-id="8c242-251">However, a second <xref:System.Data.Linq.DataContext> on the same database does not reflect the updated values.</span></span> <span data-ttu-id="8c242-252">Второй экземпляр <xref:System.Data.Linq.DataContext>, вероятно, возвращает кэшированные значения.</span><span class="sxs-lookup"><span data-stu-id="8c242-252">The second <xref:System.Data.Linq.DataContext> instance seems to return cached values.</span></span>

<span data-ttu-id="8c242-253">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-253">A.</span></span> <span data-ttu-id="8c242-254">В этом весь замысел.</span><span class="sxs-lookup"><span data-stu-id="8c242-254">This behavior is by design.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8c242-255">по-прежнему возвращает те же экземпляры и значения, которые отображались в первом экземпляре.</span><span class="sxs-lookup"><span data-stu-id="8c242-255">continues to return the same instances/values that you saw in the first instance.</span></span> <span data-ttu-id="8c242-256">При выполнении обновлений используется оптимистическая блокировка.</span><span class="sxs-lookup"><span data-stu-id="8c242-256">When you make updates, you use optimistic concurrency.</span></span> <span data-ttu-id="8c242-257">Для проверки текущего состояния базы данных используются исходные данные, которые подтверждают неизменность ее состояния.</span><span class="sxs-lookup"><span data-stu-id="8c242-257">The original data is used to check against the current database state to assert that it is in fact still unchanged.</span></span> <span data-ttu-id="8c242-258">Если состояние изменилось, возникает конфликт, который должен быть устранен приложением.</span><span class="sxs-lookup"><span data-stu-id="8c242-258">If it has changed, a conflict occurs and your application must resolve it.</span></span> <span data-ttu-id="8c242-259">Одним вариантом является сброс исходного состояния до текущего состояния базы данных и повторная попытка обновления.</span><span class="sxs-lookup"><span data-stu-id="8c242-259">One option of your application is to reset the original state to the current database state and to try the update again.</span></span> <span data-ttu-id="8c242-260">Дополнительные сведения см. [в разделе руководство. Управление конфликтами изменений](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="8c242-260">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>

<span data-ttu-id="8c242-261">Кроме того, <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> можно задать значение «false», которое отключает кэширование и отслеживание изменений.</span><span class="sxs-lookup"><span data-stu-id="8c242-261">You can also set <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to false, which turns off caching and change tracking.</span></span> <span data-ttu-id="8c242-262">После этого самые последние значения можно будет извлекать при каждом запросе.</span><span class="sxs-lookup"><span data-stu-id="8c242-262">You can then retrieve the latest values every time that you query.</span></span>

## <a name="cannot-call-submitchanges-in-read-only-mode"></a><span data-ttu-id="8c242-263">Не удается вызвать метод SubmitChanges в режиме "только чтение"</span><span class="sxs-lookup"><span data-stu-id="8c242-263">Cannot Call SubmitChanges in Read-only Mode</span></span>

<span data-ttu-id="8c242-264">У.</span><span class="sxs-lookup"><span data-stu-id="8c242-264">Q.</span></span> <span data-ttu-id="8c242-265">При попытке вызова метода <xref:System.Data.Linq.DataContext.SubmitChanges%2A> в режиме только для чтения возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="8c242-265">When I try to call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> in read-only mode, I get an error.</span></span>

<span data-ttu-id="8c242-266">A.</span><span class="sxs-lookup"><span data-stu-id="8c242-266">A.</span></span> <span data-ttu-id="8c242-267">Режим только для чтения отключает для контекста возможность отслеживания изменений.</span><span class="sxs-lookup"><span data-stu-id="8c242-267">Read-only mode turns off the ability of the context to track changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c242-268">См. также</span><span class="sxs-lookup"><span data-stu-id="8c242-268">See also</span></span>

- [<span data-ttu-id="8c242-269">Ссылки</span><span class="sxs-lookup"><span data-stu-id="8c242-269">Reference</span></span>](reference.md)
- [<span data-ttu-id="8c242-270">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="8c242-270">Troubleshooting</span></span>](troubleshooting.md)
- [<span data-ttu-id="8c242-271">Безопасность в LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8c242-271">Security in LINQ to SQL</span></span>](security-in-linq-to-sql.md)
