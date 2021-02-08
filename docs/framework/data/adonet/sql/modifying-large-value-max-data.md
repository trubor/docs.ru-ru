---
description: 'Дополнительные сведения: изменение данных Large-Value (max) в ADO.NET'
title: Изменение данных Large-Value (max)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 2d4721d2de24399a33322bde9e70eb68e59480cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767678"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="d0112-103">Изменение данных больших объемов (max) в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d0112-103">Modifying Large-Value (max) Data in ADO.NET</span></span>

<span data-ttu-id="d0112-104">Типы данных LOB — это данные, размер которых превышает максимальный размер строки в 8 килобайт (КБ).</span><span class="sxs-lookup"><span data-stu-id="d0112-104">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="d0112-105">SQL Server представляет описатель `max` для типов данных `varchar`, `nvarchar` и `varbinary`, позволяющий сохранять значения размером до 2^32 байт.</span><span class="sxs-lookup"><span data-stu-id="d0112-105">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="d0112-106">В столбцах таблицы и переменных Transact-SQL может быть указан тип данных `varchar(max)`, `nvarchar(max)` или `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="d0112-106">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="d0112-107">В ADO.NET типы данных `max` можно выбрать с помощью объекта `DataReader`, а также их можно задавать в качестве значений входных и выходных параметров без какой-либо специальной обработки.</span><span class="sxs-lookup"><span data-stu-id="d0112-107">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="d0112-108">В случае типов больших значений `varchar` данные могут извлекаться и обновляться постепенно.</span><span class="sxs-lookup"><span data-stu-id="d0112-108">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="d0112-109">Типы данных `max` можно использовать для сравнения как переменные языка Transact-SQL, а также для объединения.</span><span class="sxs-lookup"><span data-stu-id="d0112-109">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="d0112-110">Кроме того, их можно использовать в предложениях DISTINCT, ORDER BY и GROUP BY инструкции SELECT, а также в агрегатах, объединениях и вложенных запросах.</span><span class="sxs-lookup"><span data-stu-id="d0112-110">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="d0112-111">В приведенной ниже таблице указаны ссылки на разделы электронной документации по SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d0112-111">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="d0112-112">**Документация по SQL Server**</span><span class="sxs-lookup"><span data-stu-id="d0112-112">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="d0112-113">[Использование типов данных большого размера](/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="d0112-113">[Using Large-Value Data Types](/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span></span>  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="d0112-114">Ограничения для типов данных большого размера</span><span class="sxs-lookup"><span data-stu-id="d0112-114">Large-Value Type Restrictions</span></span>  

 <span data-ttu-id="d0112-115">Приведенные ниже ограничения применяются к типам данных `max`, которые не существуют для типов данных меньших значений.</span><span class="sxs-lookup"><span data-stu-id="d0112-115">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
- <span data-ttu-id="d0112-116">`sql_variant` не может содержать тип данных больших значений `varchar`.</span><span class="sxs-lookup"><span data-stu-id="d0112-116">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
- <span data-ttu-id="d0112-117">Столбцы с данными больших значений `varchar` нельзя указать в качестве ключевого столбца в индексе.</span><span class="sxs-lookup"><span data-stu-id="d0112-117">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="d0112-118">Они разрешены в столбце, включенном в некластеризованный индекс.</span><span class="sxs-lookup"><span data-stu-id="d0112-118">They are allowed in an included column in a non-clustered index.</span></span>  
  
- <span data-ttu-id="d0112-119">Столбцы с данными больших значений `varchar` нельзя использовать в качестве ключевых столбцов секционирования.</span><span class="sxs-lookup"><span data-stu-id="d0112-119">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="d0112-120">Работа с типами большого размера на языке Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d0112-120">Working with Large-Value Types in Transact-SQL</span></span>  

 <span data-ttu-id="d0112-121">Функция Transact-SQL `OPENROWSET` — это одноразовый метод подключения и получения доступа к удаленным данным.</span><span class="sxs-lookup"><span data-stu-id="d0112-121">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="d0112-122">Включает все сведения о соединении, необходимые для доступа к удаленным данным источника данных OLE DB.</span><span class="sxs-lookup"><span data-stu-id="d0112-122">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="d0112-123">Из предложения FROM запроса можно ссылаться на функцию `OPENROWSET` как на имя таблицы.</span><span class="sxs-lookup"><span data-stu-id="d0112-123">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="d0112-124">Она также может быть использована в качестве целевой таблицы в инструкциях INSERT, UPDATE или DELETE. Это зависит от возможностей поставщика OLE DB.</span><span class="sxs-lookup"><span data-stu-id="d0112-124">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="d0112-125">Функция `OPENROWSET` содержит поставщик наборов строк `BULK`, который позволяет считывать данные напрямую из файла без загрузки в целевую таблицу.</span><span class="sxs-lookup"><span data-stu-id="d0112-125">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="d0112-126">Это позволяет использовать функцию `OPENROWSET` в обычной инструкции INSERT SELECT.</span><span class="sxs-lookup"><span data-stu-id="d0112-126">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="d0112-127">С помощью аргументов параметра `OPENROWSET BULK` можно управлять началом и концом считывания данных, отладкой ошибок и способом представления полученных данных.</span><span class="sxs-lookup"><span data-stu-id="d0112-127">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="d0112-128">Например, можно указать, что файл с данными будет считан как однострочный или как набор строк типа `varbinary`, `varchar` или `nvarchar` в один столбец.</span><span class="sxs-lookup"><span data-stu-id="d0112-128">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="d0112-129">Полное описание синтаксиса и параметров см. в электронной документации на SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d0112-129">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="d0112-130">Следующий пример вставляет фотографию в таблицу ProductPhoto в примере базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d0112-130">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="d0112-131">При использовании поставщика `BULK OPENROWSET` необходимо указывать именованный список столбцов, даже если значения не вставляются в каждый столбец.</span><span class="sxs-lookup"><span data-stu-id="d0112-131">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="d0112-132">В этом случае первичный ключ определяется как столбец идентификаторов и может быть опущен в списке столбцов.</span><span class="sxs-lookup"><span data-stu-id="d0112-132">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="d0112-133">Обратите внимание, что вам необходимо лишь указать имя корреляции (в данном случае ThumbnailPhoto) в конце инструкции `OPENROWSET`.</span><span class="sxs-lookup"><span data-stu-id="d0112-133">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="d0112-134">Оно соотносится со столбцом в таблице `ProductPhoto`, в которую загружается файл.</span><span class="sxs-lookup"><span data-stu-id="d0112-134">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,
    ThumbnailPhotoFilePath,
    LargePhoto,
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="d0112-135">Обновление данных с помощью инструкций UPDATE .WRITE</span><span class="sxs-lookup"><span data-stu-id="d0112-135">Updating Data Using UPDATE .WRITE</span></span>  

 <span data-ttu-id="d0112-136">В инструкции Transact-SQL UPDATE имеется новый синтаксис WRITE, используемый для изменения содержимого столбцов `varchar(max)`, `nvarchar(max)` или `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="d0112-136">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="d0112-137">Он позволяет выполнять частичные обновления данных.</span><span class="sxs-lookup"><span data-stu-id="d0112-137">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="d0112-138">Синтаксис UPDATE .WRITE указан здесь в сокращенной форме.</span><span class="sxs-lookup"><span data-stu-id="d0112-138">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="d0112-139">UPDATE</span><span class="sxs-lookup"><span data-stu-id="d0112-139">UPDATE</span></span>  
  
 <span data-ttu-id="d0112-140">{ *\<object>* }</span><span class="sxs-lookup"><span data-stu-id="d0112-140">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="d0112-141">SET</span><span class="sxs-lookup"><span data-stu-id="d0112-141">SET</span></span>  
  
 <span data-ttu-id="d0112-142">{ *column_name* = {. WRITE ( *выражение* , @Offset , @Length )}</span><span class="sxs-lookup"><span data-stu-id="d0112-142">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="d0112-143">Метод WRITE указывает, что часть значения *column_name* будет изменена.</span><span class="sxs-lookup"><span data-stu-id="d0112-143">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="d0112-144">Выражение является значением, которое будет скопировано в поле *column_name*. Аргумент `@Offset` является начальной точкой записи выражения, а аргумент `@Length` — длиной изменяемой секции в столбце.</span><span class="sxs-lookup"><span data-stu-id="d0112-144">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="d0112-145">If</span><span class="sxs-lookup"><span data-stu-id="d0112-145">If</span></span>|<span data-ttu-id="d0112-146">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="d0112-146">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="d0112-147">Для выражения задано значение NULL.</span><span class="sxs-lookup"><span data-stu-id="d0112-147">The expression is set to NULL</span></span>|<span data-ttu-id="d0112-148">Аргумент `@Length` не обрабатывается, а значение в поле *column_name* усекается в соответствии с указанным аргументом `@Offset`.</span><span class="sxs-lookup"><span data-stu-id="d0112-148">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="d0112-149">`@Offset` равно NULL</span><span class="sxs-lookup"><span data-stu-id="d0112-149">`@Offset` is NULL</span></span>|<span data-ttu-id="d0112-150">Операция обновления добавляет выражение в конец существующего значения *column_name*, и аргумент `@Length` не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="d0112-150">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="d0112-151">Значение аргумента `@Offset` больше, чем длина значения аргумента column_name.</span><span class="sxs-lookup"><span data-stu-id="d0112-151">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="d0112-152">SQL Server возвращает ошибку.</span><span class="sxs-lookup"><span data-stu-id="d0112-152">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="d0112-153">`@Length` равно NULL</span><span class="sxs-lookup"><span data-stu-id="d0112-153">`@Length` is NULL</span></span>|<span data-ttu-id="d0112-154">Операция обновления удаляет все данные, начиная с позиции `@Offset` до конца значения `column_name`.</span><span class="sxs-lookup"><span data-stu-id="d0112-154">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="d0112-155">Ни `@Offset`, ни `@Length` не может быть отрицательным числом.</span><span class="sxs-lookup"><span data-stu-id="d0112-155">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0112-156">Пример</span><span class="sxs-lookup"><span data-stu-id="d0112-156">Example</span></span>  

 <span data-ttu-id="d0112-157">Этот пример Transact-SQL обновляет частичное значение в DocumentSummary, столбце `nvarchar(max)` таблицы Document в базе данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d0112-157">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="d0112-158">Слово components заменяется словом features, при этом указывается новое слово, начальное смещение слова, заменяемого в исходном тексте, и число заменяемых символов (длина).</span><span class="sxs-lookup"><span data-stu-id="d0112-158">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="d0112-159">Этот пример содержит инструкцию SELECT перед и после инструкции UPDATE для сравнения результатов.</span><span class="sxs-lookup"><span data-stu-id="d0112-159">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="d0112-160">Работа с типами данных большого размера в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d0112-160">Working with Large-Value Types in ADO.NET</span></span>  

 <span data-ttu-id="d0112-161">В ADO.NET можно работать с типами больших значений, указав их в качестве параметров <xref:System.Data.SqlClient.SqlParameter> в <xref:System.Data.SqlClient.SqlDataReader> для возврата результирующего набора либо воспользовавшись объектом <xref:System.Data.SqlClient.SqlDataAdapter> для заполнения набора `DataSet`/`DataTable`.</span><span class="sxs-lookup"><span data-stu-id="d0112-161">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="d0112-162">Обработка типов больших значений и связанных с ними типов данных меньших значений ничем не отличается.</span><span class="sxs-lookup"><span data-stu-id="d0112-162">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="d0112-163">Извлечение данных с помощью GetSqlBytes</span><span class="sxs-lookup"><span data-stu-id="d0112-163">Using GetSqlBytes to Retrieve Data</span></span>  

 <span data-ttu-id="d0112-164">Метод `GetSqlBytes` класса <xref:System.Data.SqlClient.SqlDataReader> можно использовать для извлечения содержимого столбца `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="d0112-164">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="d0112-165">В приведенном ниже фрагменте кода предполагается наличие объекта <xref:System.Data.SqlClient.SqlCommand> с именем `cmd`, который выбирает данные `varbinary(max)` из таблицы, и объекта <xref:System.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает данные в качестве класса <xref:System.Data.SqlTypes.SqlBytes>.</span><span class="sxs-lookup"><span data-stu-id="d0112-165">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="d0112-166">Использование метода GetSqlChars для получения данных</span><span class="sxs-lookup"><span data-stu-id="d0112-166">Using GetSqlChars to Retrieve Data</span></span>  

 <span data-ttu-id="d0112-167">Метод `GetSqlChars` класса <xref:System.Data.SqlClient.SqlDataReader> можно использовать для извлечения содержимого столбца `varchar(max)` или `nvarchar(max)`.</span><span class="sxs-lookup"><span data-stu-id="d0112-167">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="d0112-168">В приведенном ниже фрагменте кода предполагается наличие объекта <xref:System.Data.SqlClient.SqlCommand> с именем `cmd`, который выбирает данные `nvarchar(max)` из таблицы, и объекта <xref:System.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает данные.</span><span class="sxs-lookup"><span data-stu-id="d0112-168">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="d0112-169">Использование метода GetSqlBinary для получения данных</span><span class="sxs-lookup"><span data-stu-id="d0112-169">Using GetSqlBinary to Retrieve Data</span></span>  

 <span data-ttu-id="d0112-170">Метод `GetSqlBinary` класса <xref:System.Data.SqlClient.SqlDataReader> можно использовать для извлечения содержимого столбца `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="d0112-170">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="d0112-171">В приведенном ниже фрагменте кода предполагается наличие объекта <xref:System.Data.SqlClient.SqlCommand> с именем `cmd`, который выбирает данные `varbinary(max)` из таблицы, и объекта <xref:System.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает данные в качестве потока <xref:System.Data.SqlTypes.SqlBinary>.</span><span class="sxs-lookup"><span data-stu-id="d0112-171">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="d0112-172">Использование метода GetBytes для получения данных</span><span class="sxs-lookup"><span data-stu-id="d0112-172">Using GetBytes to Retrieve Data</span></span>  

 <span data-ttu-id="d0112-173">Метод `GetBytes` класса <xref:System.Data.SqlClient.SqlDataReader> считывает поток байтов с указанного смещения столбца в массив байтов, начиная с указанного смещения массива.</span><span class="sxs-lookup"><span data-stu-id="d0112-173">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="d0112-174">В приведенном ниже фрагменте кода предполагается наличие объекта <xref:System.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает байты в массив байтов.</span><span class="sxs-lookup"><span data-stu-id="d0112-174">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="d0112-175">Обратите внимание, что в отличие от `GetSqlBytes` для метода `GetBytes` требуется размер для буфера массива.</span><span class="sxs-lookup"><span data-stu-id="d0112-175">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="d0112-176">Использование метода GetValue для получения данных</span><span class="sxs-lookup"><span data-stu-id="d0112-176">Using GetValue to Retrieve Data</span></span>  

 <span data-ttu-id="d0112-177">Метод `GetValue` класса <xref:System.Data.SqlClient.SqlDataReader> считывает значение из указанного смещения столбца в массив.</span><span class="sxs-lookup"><span data-stu-id="d0112-177">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="d0112-178">В приведенном ниже фрагменте кода предполагается наличие объекта <xref:System.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает двоичные данные из первого смещения столбца, а затем данные строки из второго смещения столбца.</span><span class="sxs-lookup"><span data-stu-id="d0112-178">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="d0112-179">Преобразование типов больших значений в типы CLR</span><span class="sxs-lookup"><span data-stu-id="d0112-179">Converting from Large Value Types to CLR Types</span></span>  

 <span data-ttu-id="d0112-180">Вы можете преобразовать содержимое столбца `varchar(max)` или `nvarchar(max)` с использованием любого метода преобразования строк, например `ToString`.</span><span class="sxs-lookup"><span data-stu-id="d0112-180">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="d0112-181">В приведенном ниже фрагменте кода предполагается наличие объекта <xref:System.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает данные.</span><span class="sxs-lookup"><span data-stu-id="d0112-181">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a><span data-ttu-id="d0112-182">Пример</span><span class="sxs-lookup"><span data-stu-id="d0112-182">Example</span></span>  

 <span data-ttu-id="d0112-183">Приведенный ниже код извлекает имя и объект `LargePhoto` из таблицы `ProductPhoto` в базе данных `AdventureWorks` и сохраняет его в файле.</span><span class="sxs-lookup"><span data-stu-id="d0112-183">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="d0112-184">Сборку необходимо скомпилировать со ссылкой на пространство имен <xref:System.Drawing>.</span><span class="sxs-lookup"><span data-stu-id="d0112-184">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="d0112-185">Метод <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> класса <xref:System.Data.SqlClient.SqlDataReader> возвращает объект <xref:System.Data.SqlTypes.SqlBytes>, который предоставляет свойство `Stream`.</span><span class="sxs-lookup"><span data-stu-id="d0112-185">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="d0112-186">Код использует его для создания нового объекта `Bitmap`, а затем сохраняет его как изображение `ImageFormat` в формате Gif.</span><span class="sxs-lookup"><span data-stu-id="d0112-186">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="d0112-187">Использование параметров типа больших значений</span><span class="sxs-lookup"><span data-stu-id="d0112-187">Using Large Value Type Parameters</span></span>  

 <span data-ttu-id="d0112-188">Типы больших значений можно использовать в объектах <xref:System.Data.SqlClient.SqlParameter> точно так же, как и типы меньших значений в объектах <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="d0112-188">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="d0112-189">Типы больших значений можно извлекать в виде значений <xref:System.Data.SqlClient.SqlParameter>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d0112-189">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="d0112-190">В коде предполагается существование в примере базы данных AdventureWorks приведенной ниже хранимой процедуры GetDocumentSummary.</span><span class="sxs-lookup"><span data-stu-id="d0112-190">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="d0112-191">Хранимая процедура принимает входной параметр @DocumentID и возвращает содержимое столбца DocumentSummary в выходной параметр @DocumentSummary.</span><span class="sxs-lookup"><span data-stu-id="d0112-191">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
```sql
CREATE PROCEDURE GetDocumentSummary
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a><span data-ttu-id="d0112-192">Пример</span><span class="sxs-lookup"><span data-stu-id="d0112-192">Example</span></span>  

 <span data-ttu-id="d0112-193">Код ADO.NET создает объекты <xref:System.Data.SqlClient.SqlConnection> и <xref:System.Data.SqlClient.SqlCommand> для выполнения хранимой процедуры GetDocumentSummary и извлечения сводки документа, которая сохраняется как тип больших значений.</span><span class="sxs-lookup"><span data-stu-id="d0112-193">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="d0112-194">Код передает значение входному параметру @DocumentID и отображает результаты, переданные обратно в выходной параметр @DocumentSummary, в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="d0112-194">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d0112-195">См. также</span><span class="sxs-lookup"><span data-stu-id="d0112-195">See also</span></span>

- [<span data-ttu-id="d0112-196">Двоичные данные и данные больших значений SQL Server</span><span class="sxs-lookup"><span data-stu-id="d0112-196">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="d0112-197">Сопоставления типов данных SQL Server</span><span class="sxs-lookup"><span data-stu-id="d0112-197">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="d0112-198">SQL Serverные операции с данными в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d0112-198">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="d0112-199">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d0112-199">ADO.NET Overview</span></span>](../ado-net-overview.md)
