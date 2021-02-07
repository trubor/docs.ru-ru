---
description: 'Дополнительные сведения: разбиение результатов запроса по страницам'
title: Разбивка на страницы результатов запроса
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: ead2c74e19cfb81c83c7bf1e73b0c0d7a0a7cc67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672365"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="d7e56-103">Разбивка на страницы результатов запроса</span><span class="sxs-lookup"><span data-stu-id="d7e56-103">Paging Through a Query Result</span></span>

<span data-ttu-id="d7e56-104">Постраничный просмотр результатов запроса - это процесс возврата результатов запроса небольшими подмножествами данных (страницами).</span><span class="sxs-lookup"><span data-stu-id="d7e56-104">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="d7e56-105">Этот метод часто используется для вывода результатов пользователю в виде небольших фрагментов, с которыми легко работать.</span><span class="sxs-lookup"><span data-stu-id="d7e56-105">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="d7e56-106">**DataAdapter** предоставляет средство для возвращения только страницы данных с помощью перегрузок метода **Fill** .</span><span class="sxs-lookup"><span data-stu-id="d7e56-106">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="d7e56-107">Однако это может быть не лучшим решением для постраничного просмотра большого числа результатов запроса. Хотя класс **DataAdapter** заполняет целевые объекты <xref:System.Data.DataTable> или <xref:System.Data.DataSet> только запрошенными записями, при этом все равно используются ресурсы, необходимые для возврата всех результатов запроса.</span><span class="sxs-lookup"><span data-stu-id="d7e56-107">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="d7e56-108">Для возврата страницы данных из источника данных без использования лишних ресурсов задайте для запроса дополнительные критерии, которые ограничат число возвращаемых строки только необходимыми.</span><span class="sxs-lookup"><span data-stu-id="d7e56-108">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="d7e56-109">Чтобы использовать метод **Fill** для возврата страницы данных, укажите параметр **startRecord** для первой записи на странице данных и параметр **maxRecords** для количества записей на странице данных.</span><span class="sxs-lookup"><span data-stu-id="d7e56-109">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="d7e56-110">В следующем примере кода показано, как использовать метод **Fill** для возврата первой страницы результата запроса, в котором размер страницы составляет пять записей.</span><span class="sxs-lookup"><span data-stu-id="d7e56-110">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 <span data-ttu-id="d7e56-111">В предыдущем примере **DataSet** заполняется только пятью записями, но возвращается вся таблица **Orders**.</span><span class="sxs-lookup"><span data-stu-id="d7e56-111">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="d7e56-112">Чтобы заполнить **набор данных** теми же пятью записями, но возвращать только пять записей, используйте предложения TOP и WHERE в инструкции SQL, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="d7e56-112">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 <span data-ttu-id="d7e56-113">Обратите внимание, что при таком способе постраничного просмотра результатов запроса необходимо сохранять уникальный идентификатор, с помощью которого выполняется упорядочение строк. Этот уникальный идентификатор нужно будет передать команде, служащей для возврата следующей страницы записей, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="d7e56-113">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="d7e56-114">Чтобы вернуть следующую страницу записей с помощью перегрузки метода **Fill** , который принимает параметры **startRecord** и **maxRecords** , увеличьте индекс текущей записи по размеру страницы и заполните таблицу.</span><span class="sxs-lookup"><span data-stu-id="d7e56-114">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="d7e56-115">Следует помнить, что сервер базы данных возвращает все результаты запроса, даже если к **DataSet** добавляется только одна страница записей.</span><span class="sxs-lookup"><span data-stu-id="d7e56-115">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="d7e56-116">В следующем примере кода строки таблицы очищаются, а затем заполняются следующей страницей данных.</span><span class="sxs-lookup"><span data-stu-id="d7e56-116">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="d7e56-117">Может быть необходимым сохранить определенное число возвращенных строк в локальном кэше, чтобы уменьшить число обращений к серверу базы данных.</span><span class="sxs-lookup"><span data-stu-id="d7e56-117">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 <span data-ttu-id="d7e56-118">Чтобы возвратить следующую страницу записей, не заставляя сервер баз данных возвращать сразу все результаты запроса, укажите ограничивающие критерии для инструкции SELECT.</span><span class="sxs-lookup"><span data-stu-id="d7e56-118">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="d7e56-119">Так как код предыдущего примера сохранил последнюю возвращенную запись, ее можно использовать в предложении WHERE, чтобы указать для запроса начальную точку, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="d7e56-119">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7e56-120">См. также</span><span class="sxs-lookup"><span data-stu-id="d7e56-120">See also</span></span>

- [<span data-ttu-id="d7e56-121">Объекты DataAdapter и DataReader</span><span class="sxs-lookup"><span data-stu-id="d7e56-121">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="d7e56-122">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d7e56-122">ADO.NET Overview</span></span>](ado-net-overview.md)
