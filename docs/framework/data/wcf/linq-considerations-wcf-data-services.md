---
description: 'Дополнительные сведения: рекомендации по LINQ (службы данных WCF)'
title: Рекомендации по LINQ (службы WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 4205fc5c67c5939377e2a964d5a82d8855b03fce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764968"
---
# <a name="linq-considerations-wcf-data-services"></a><span data-ttu-id="1277a-103">Рекомендации по LINQ (службы WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="1277a-103">LINQ Considerations (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="1277a-104">В этом разделе содержатся сведения о способе, с помощью которого запросы LINQ формируются и выполняются при использовании клиента службы данных WCF, а также об ограничениях использования LINQ для запроса службы данных, которая реализует Open Data Protocol (OData).</span><span class="sxs-lookup"><span data-stu-id="1277a-104">This topic provides information about the way in which LINQ queries are composed and executed when you are using the WCF Data Services client and limitations of using LINQ to query a data service that implements the Open Data Protocol (OData).</span></span> <span data-ttu-id="1277a-105">Дополнительные сведения о создании и выполнении запросов к службе данных на основе OData см. в разделе [запросы к службе данных](querying-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="1277a-105">For more information about composing and executing queries against an OData-based data service, see [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="composing-linq-queries"></a><span data-ttu-id="1277a-106">Составление LINQ-запросов</span><span class="sxs-lookup"><span data-stu-id="1277a-106">Composing LINQ Queries</span></span>  

 <span data-ttu-id="1277a-107">LINQ позволяет составлять запросы к коллекции объектов, которая реализует <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1277a-107">LINQ enables you to compose queries against a collection of objects that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="1277a-108">Как диалоговое окно **Добавление ссылки на службу** в Visual Studio, так и средство DataSvcUtil.exe используются для создания представления службы OData в виде класса контейнера сущностей, наследуемого от <xref:System.Data.Services.Client.DataServiceContext> , а также объектов, представляющих сущности, возвращаемые в веб-каналах.</span><span class="sxs-lookup"><span data-stu-id="1277a-108">Both the **Add Service Reference** dialog box in Visual Studio and the DataSvcUtil.exe tool are used to generate a representation of an OData service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>, as well as objects that represent the entities returned in feeds.</span></span> <span data-ttu-id="1277a-109">Эти средства также создают свойства для класса контейнера сущностей для коллекций, представляемых службой в виде потоков.</span><span class="sxs-lookup"><span data-stu-id="1277a-109">These tools also generate properties on the entity container class for the collections that are exposed as feeds by the service.</span></span> <span data-ttu-id="1277a-110">Каждое свойство класса, инкапсулирующего службу данных, возвращает объект <xref:System.Data.Services.Client.DataServiceQuery%601>.</span><span class="sxs-lookup"><span data-stu-id="1277a-110">Each of these properties of the class that encapsulates the data service return a <xref:System.Data.Services.Client.DataServiceQuery%601>.</span></span> <span data-ttu-id="1277a-111">Поскольку класс <xref:System.Data.Services.Client.DataServiceQuery%601> реализует интерфейс <xref:System.Linq.IQueryable%601>, определяемый LINQ, можно составить LINQ-запрос для потоков, предоставляемых службой данных, которые преобразуются клиентской библиотекой в URI-запрос, отправляемый службе данных при выполнении.</span><span class="sxs-lookup"><span data-stu-id="1277a-111">Because the <xref:System.Data.Services.Client.DataServiceQuery%601> class implements the <xref:System.Linq.IQueryable%601> interface defined by LINQ, you can compose a LINQ query against feeds exposed by the data service, which are translated by the client library into a query request URI that is sent to the data service on execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1277a-112">Набор запросов, представленный в синтаксисе LINQ, более широк, чем включенный в синтаксисе URI, который используется службами данных OData.</span><span class="sxs-lookup"><span data-stu-id="1277a-112">The set of queries expressible in the LINQ syntax is broader than those enabled in the URI syntax that is used by OData data services.</span></span> <span data-ttu-id="1277a-113">Исключение <xref:System.NotSupportedException> возникает, если запрос не может быть сопоставлен с URI в целевой службе данных.</span><span class="sxs-lookup"><span data-stu-id="1277a-113">A <xref:System.NotSupportedException> is raised when the query cannot be mapped to a URI in the target data service.</span></span> <span data-ttu-id="1277a-114">Дополнительные сведения см. в разделе [неподдерживаемые методы LINQ](linq-considerations-wcf-data-services.md#unsupportedMethods) этой статьи.</span><span class="sxs-lookup"><span data-stu-id="1277a-114">For more information, see the [Unsupported LINQ Methods](linq-considerations-wcf-data-services.md#unsupportedMethods) in this topic.</span></span>  
  
 <span data-ttu-id="1277a-115">В следующем примере показан запрос LINQ, который возвращает объекты `Orders` со стоимостью транспортировки более 30 долларов и упорядочивает результаты по дате отправки, начиная с самой последней.</span><span class="sxs-lookup"><span data-stu-id="1277a-115">The following example is a LINQ query that returns `Orders` that have a freight cost of more than $30 and sorts the results by the shipping date, starting with the latest ship date:</span></span>  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]
  
 <span data-ttu-id="1277a-116">Этот запрос LINQ преобразуется в следующий универсальный код ресурса (URI) запроса, который выполняется для службы данных [краткого руководства](quickstart-wcf-data-services.md) на основе Northwind:</span><span class="sxs-lookup"><span data-stu-id="1277a-116">This LINQ query is translated into the following query URI that is executed against the Northwind-based [quickstart](quickstart-wcf-data-services.md) data service:</span></span>  
  
```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 <span data-ttu-id="1277a-117">Дополнительные общие сведения о LINQ см. в разделе LINQ — [C#](../../../csharp/programming-guide/concepts/linq/index.md) или [LINQ-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="1277a-117">For more general information about LINQ, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
 <span data-ttu-id="1277a-118">LINQ позволяет составлять запросы как с помощью декларативного синтаксиса запросов на основе определенного языка (как показано в предыдущем примере), так и в виде набора методов запроса, известных как стандартные операторы запроса.</span><span class="sxs-lookup"><span data-stu-id="1277a-118">LINQ enables you to compose queries by using both the language-specific declarative query syntax, shown in the previous example, as well as a set of query methods known as standard query operators.</span></span> <span data-ttu-id="1277a-119">Запрос, эквивалентный запросу из предыдущего примера, может быть составлен только с помощью синтаксиса на основе методов, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="1277a-119">An equivalent query to the previous example can be composed by using only the method-based syntax, as shown the following example:</span></span>  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpressionspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpressionspecific)]
  
 <span data-ttu-id="1277a-120">Клиент службы данных WCF может преобразовывать оба вида составных запросов в универсальный код ресурса (URI) запроса, а запрос LINQ можно расширить путем добавления методов запроса в выражение запроса.</span><span class="sxs-lookup"><span data-stu-id="1277a-120">The WCF Data Services client is able to translate both kinds of composed queries into a query URI, and you can extend a LINQ query by appending query methods to a query expression.</span></span> <span data-ttu-id="1277a-121">При составлении LINQ-запросов путем добавления синтаксиса запросов в выражение запроса или в объект <xref:System.Data.Services.Client.DataServiceQuery%601> операторы добавляются в URI-запрос в порядке вызова методов.</span><span class="sxs-lookup"><span data-stu-id="1277a-121">When you compose LINQ queries by appending method syntax to a query expression or a <xref:System.Data.Services.Client.DataServiceQuery%601>, the operations are added to the query URI in the order in which methods are called.</span></span> <span data-ttu-id="1277a-122">Это эквивалентно вызову метода <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> для добавления параметров запроса в URI-запрос.</span><span class="sxs-lookup"><span data-stu-id="1277a-122">This is equivalent to calling the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method to add each query option to the query URI.</span></span>  
  
## <a name="executing-linq-queries"></a><span data-ttu-id="1277a-123">Выполнение LINQ-запросов</span><span class="sxs-lookup"><span data-stu-id="1277a-123">Executing LINQ Queries</span></span>  

 <span data-ttu-id="1277a-124">Некоторые методы LINQ-запроса, такие как <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> или <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, приводят к выполнению запроса при добавлении в запрос.</span><span class="sxs-lookup"><span data-stu-id="1277a-124">Certain LINQ query methods, such as <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> or <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, when appended to the query, cause the query to be executed.</span></span> <span data-ttu-id="1277a-125">Запрос также выполняется, если результаты неявно перечисляются, например в цикле `foreach` или когда запрос приписывается к коллекции `List`.</span><span class="sxs-lookup"><span data-stu-id="1277a-125">A query is also executed when results are enumerated implicitly, such as during a `foreach` loop or when the query is assigned to a `List` collection.</span></span> <span data-ttu-id="1277a-126">Дополнительные сведения см. [в разделе запросы к службе данных](querying-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="1277a-126">For more information, see [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="1277a-127">Клиент выполняет LINQ-запрос в два этапа.</span><span class="sxs-lookup"><span data-stu-id="1277a-127">The client executes a LINQ query in two parts.</span></span> <span data-ttu-id="1277a-128">По возможности сначала вычисляются LINQ-выражения в запросе на стороне клиента, а затем создается URI-запрос, который будет отправлен службе данных для проведения вычислений по отношению к данным в службе.</span><span class="sxs-lookup"><span data-stu-id="1277a-128">Whenever possible, LINQ expressions in a query are first evaluated on the client, and then a URI-based query is generated and sent to the data service for evaluation against data in the service.</span></span> <span data-ttu-id="1277a-129">Дополнительные сведения см. в разделе [клиент и выполнение сервера](querying-the-data-service-wcf-data-services.md#executingQueries) в [запросах к службе данных](querying-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="1277a-129">For more information, see the section [Client versus Server Execution](querying-the-data-service-wcf-data-services.md#executingQueries) in [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="1277a-130">Если запрос LINQ не может быть преобразован в URI запроса, совместимого с OData, при выполнении попытки выполнения возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="1277a-130">When a LINQ query cannot be translated in an OData-compliant query URI, an exception is raised when execution is attempted.</span></span> <span data-ttu-id="1277a-131">Дополнительные сведения см. [в разделе запросы к службе данных](querying-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="1277a-131">For more information, see [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="linq-query-examples"></a><span data-ttu-id="1277a-132">Примеры LINQ-запросов</span><span class="sxs-lookup"><span data-stu-id="1277a-132">LINQ Query Examples</span></span>  

 <span data-ttu-id="1277a-133">В примерах в следующих разделах демонстрируются типы запросов LINQ, которые могут быть выполнены со службой OData.</span><span class="sxs-lookup"><span data-stu-id="1277a-133">The examples in the following sections demonstrate the kinds of LINQ queries that can be executed against an OData service.</span></span>  
  
<a name="filtering"></a>

### <a name="filtering"></a><span data-ttu-id="1277a-134">Фильтрация</span><span class="sxs-lookup"><span data-stu-id="1277a-134">Filtering</span></span>  

 <span data-ttu-id="1277a-135">Образцы LINQ-запросов в этом подразделе сортируют данные в потоке, возвращаемом службой.</span><span class="sxs-lookup"><span data-stu-id="1277a-135">The LINQ query examples in this section filter data in the feed returned by the service.</span></span>  
  
 <span data-ttu-id="1277a-136">Следующие примеры эквиваленты запросам, которые фильтруют возвращаемые `Orders` сущности так, чтобы были возвращены только заказы со стоимостью более 30 долларов.</span><span class="sxs-lookup"><span data-stu-id="1277a-136">The following examples are equivalent queries that filter the returned `Orders` entities so that only orders with a freight cost greater than $30 are returned:</span></span>  
  
- <span data-ttu-id="1277a-137">Использование синтаксиса LINQ-запросов</span><span class="sxs-lookup"><span data-stu-id="1277a-137">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwhereclausespecific)]
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwhereclausespecific)]
  
- <span data-ttu-id="1277a-138">Использование методов LINQ-запросов</span><span class="sxs-lookup"><span data-stu-id="1277a-138">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwheremethodspecific)]
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwheremethodspecific)]
  
- <span data-ttu-id="1277a-139">Параметр строки URI-запроса `$filter`:</span><span class="sxs-lookup"><span data-stu-id="1277a-139">The URI query string `$filter` option:</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitquerywheremethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitquerywheremethodspecific)]
  
 <span data-ttu-id="1277a-140">Все вышеприведенные примеры преобразуются в URI-запрос: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.</span><span class="sxs-lookup"><span data-stu-id="1277a-140">All of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.</span></span>  
  
<a name="sorting"></a>

### <a name="sorting"></a><span data-ttu-id="1277a-141">Сортировка</span><span class="sxs-lookup"><span data-stu-id="1277a-141">Sorting</span></span>  

 <span data-ttu-id="1277a-142">Далее приведены примеры эквивалентных запросов, которые сортируют возвращаемые данные как по названию компании, так и по почтовому индексу в порядке убывания.</span><span class="sxs-lookup"><span data-stu-id="1277a-142">The following examples show equivalent queries that sort returned data both by the company name and by postal code, descending:</span></span>  
  
- <span data-ttu-id="1277a-143">Использование синтаксиса LINQ-запросов</span><span class="sxs-lookup"><span data-stu-id="1277a-143">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbyclausespecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbyclausespecific)]
  
- <span data-ttu-id="1277a-144">Использование методов LINQ-запросов</span><span class="sxs-lookup"><span data-stu-id="1277a-144">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbymethodspecific)]
  
- <span data-ttu-id="1277a-145">Параметр строки URI-запроса `$orderby`):</span><span class="sxs-lookup"><span data-stu-id="1277a-145">URI query string `$orderby` option):</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryorderbymethodspecific)]
  
 <span data-ttu-id="1277a-146">Все вышеприведенные примеры преобразуются в URI-запрос: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.</span><span class="sxs-lookup"><span data-stu-id="1277a-146">All of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.</span></span>  
  
<a name="projection"></a>

### <a name="projection"></a><span data-ttu-id="1277a-147">Прогнозирование</span><span class="sxs-lookup"><span data-stu-id="1277a-147">Projection</span></span>  

 <span data-ttu-id="1277a-148">Далее приведены примеры эквивалентных запросов, которые проецируют возвращаемые данные в более узкий тип `CustomerAddress`.</span><span class="sxs-lookup"><span data-stu-id="1277a-148">The following examples show equivalent queries that project returned data into the narrower `CustomerAddress` type:</span></span>  
  
- <span data-ttu-id="1277a-149">Использование синтаксиса LINQ-запросов</span><span class="sxs-lookup"><span data-stu-id="1277a-149">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectclausespecific)]
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectclausespecific)]
  
- <span data-ttu-id="1277a-150">Использование методов LINQ-запросов</span><span class="sxs-lookup"><span data-stu-id="1277a-150">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectmethodspecific)]

> [!NOTE]
> <span data-ttu-id="1277a-151">Параметр запроса `$select` нельзя добавить в URI-запрос с помощью метода <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>.</span><span class="sxs-lookup"><span data-stu-id="1277a-151">The `$select` query option cannot be added to a query URI by using the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method.</span></span> <span data-ttu-id="1277a-152">Рекомендуется использовать метод <xref:System.Linq.Enumerable.Select%2A> на основе LINQ для создания параметра запроса `$select` в URI-запросе.</span><span class="sxs-lookup"><span data-stu-id="1277a-152">We recommend that you use the LINQ <xref:System.Linq.Enumerable.Select%2A> method to have the client generate the `$select` query option in the request URI.</span></span>  
  
 <span data-ttu-id="1277a-153">Оба приведенных выше примера преобразуются в URI-запрос: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.</span><span class="sxs-lookup"><span data-stu-id="1277a-153">Both of the previous examples are translated to the query URI: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.</span></span>  
  
<a name="paging"></a>

### <a name="client-paging"></a><span data-ttu-id="1277a-154">Клиент разбиения по страницам</span><span class="sxs-lookup"><span data-stu-id="1277a-154">Client Paging</span></span>  

 <span data-ttu-id="1277a-155">Далее приведены примеры эквивалентных запросов, запрашивающих страницу сущностей отсортированных заказов, которая включает 25 заказов и не включает первые 50 заказов.</span><span class="sxs-lookup"><span data-stu-id="1277a-155">The following examples show equivalent queries that request a page of sorted order entities that includes 25 orders, skipping the first 50 orders:</span></span>  
  
- <span data-ttu-id="1277a-156">Применение методов запроса к LINQ-запросу:</span><span class="sxs-lookup"><span data-stu-id="1277a-156">Applying query methods to a LINQ query:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqskiptakemethodspecific)]
  
- <span data-ttu-id="1277a-157">Параметры строки URI-запроса `$skip` и `$top`):</span><span class="sxs-lookup"><span data-stu-id="1277a-157">URI query string `$skip` and `$top` options):</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryskiptakemethodspecific)]
  
 <span data-ttu-id="1277a-158">Оба приведенных выше примера преобразуются в URI-запрос: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.</span><span class="sxs-lookup"><span data-stu-id="1277a-158">Both of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.</span></span>  
  
<a name="expand"></a>

### <a name="expand"></a><span data-ttu-id="1277a-159">Разверните</span><span class="sxs-lookup"><span data-stu-id="1277a-159">Expand</span></span>  

 <span data-ttu-id="1277a-160">При запросе к службе данных OData можно запросить, чтобы сущности, связанные с сущностью, для которой предназначен запрос, включали возвращенный канал.</span><span class="sxs-lookup"><span data-stu-id="1277a-160">When you query an OData data service, you can request that entities related to the entity targeted by the query be included the returned feed.</span></span> <span data-ttu-id="1277a-161">Метод <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> вызывается для <xref:System.Data.Services.Client.DataServiceQuery%601> для набора сущностей, заданного LINQ-запросом, при этом имя связанного набора сущностей предоставляется в виде параметра `path`.</span><span class="sxs-lookup"><span data-stu-id="1277a-161">The <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is called on the <xref:System.Data.Services.Client.DataServiceQuery%601> for the entity set targeted by the LINQ query, with the related entity set name supplied as the `path` parameter.</span></span> <span data-ttu-id="1277a-162">Дополнительные сведения см. в разделе [Загрузка отложенного содержимого](loading-deferred-content-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="1277a-162">For more information, see [Loading Deferred Content](loading-deferred-content-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="1277a-163">В следующих примерах показаны эквивалентные способы использования метода <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> в запросе.</span><span class="sxs-lookup"><span data-stu-id="1277a-163">The following examples show equivalent ways to use the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method in a query:</span></span>  
  
- <span data-ttu-id="1277a-164">Синтаксис LINQ-запроса:</span><span class="sxs-lookup"><span data-stu-id="1277a-164">In LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandspecific)]  
  
- <span data-ttu-id="1277a-165">С помощью методов LINQ-запроса:</span><span class="sxs-lookup"><span data-stu-id="1277a-165">With LINQ query methods:</span></span>  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandmethodspecific)]

 <span data-ttu-id="1277a-166">Оба приведенных выше примера преобразуются в URI-запрос: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.</span><span class="sxs-lookup"><span data-stu-id="1277a-166">Both of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.</span></span>  
  
<a name="unsupportedMethods"></a>

## <a name="unsupported-linq-methods"></a><span data-ttu-id="1277a-167">Неподдерживаемые LINQ-методы</span><span class="sxs-lookup"><span data-stu-id="1277a-167">Unsupported LINQ Methods</span></span>  

 <span data-ttu-id="1277a-168">В следующей таблице содержатся классы методов LINQ, которые не поддерживаются и не могут быть включены в запрос, выполняемый для службы OData:</span><span class="sxs-lookup"><span data-stu-id="1277a-168">The following table contains the classes of LINQ methods are not supported and cannot be included in a query executed against an OData service:</span></span>  
  
|<span data-ttu-id="1277a-169">Тип операции</span><span class="sxs-lookup"><span data-stu-id="1277a-169">Operation Type</span></span>|<span data-ttu-id="1277a-170">Неподдерживаемый метод</span><span class="sxs-lookup"><span data-stu-id="1277a-170">Unsupported Method</span></span>|  
|--------------------|------------------------|  
|<span data-ttu-id="1277a-171">Операторы набора</span><span class="sxs-lookup"><span data-stu-id="1277a-171">Set operators</span></span>|<span data-ttu-id="1277a-172">Все операторы набора не поддерживаются в запросе <xref:System.Data.Services.Client.DataServiceQuery%601>, включая следующие запросы:</span><span class="sxs-lookup"><span data-stu-id="1277a-172">All set operators are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, which included the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|<span data-ttu-id="1277a-173">Операторы упорядочивания</span><span class="sxs-lookup"><span data-stu-id="1277a-173">Ordering operators</span></span>|<span data-ttu-id="1277a-174">Следующие операторы упорядочивания, которым требуется метод <xref:System.Collections.Generic.IComparer%601>, не поддерживаются в запросе <xref:System.Data.Services.Client.DataServiceQuery%601>:</span><span class="sxs-lookup"><span data-stu-id="1277a-174">The following ordering operators that require <xref:System.Collections.Generic.IComparer%601> are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|<span data-ttu-id="1277a-175">Операторы проецирования и фильтрации</span><span class="sxs-lookup"><span data-stu-id="1277a-175">Projection and filtering operators</span></span>|<span data-ttu-id="1277a-176">Следующие операторы проецирования и фильтрации, принимающие аргументы положения, не поддерживаются в запросе <xref:System.Data.Services.Client.DataServiceQuery%601>:</span><span class="sxs-lookup"><span data-stu-id="1277a-176">The following projection and filtering operators that accept a positional argument are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|<span data-ttu-id="1277a-177">Операторы группирования</span><span class="sxs-lookup"><span data-stu-id="1277a-177">Grouping operators</span></span>|<span data-ttu-id="1277a-178">Все операторы группирования не поддерживаются в запросе <xref:System.Data.Services.Client.DataServiceQuery%601>, включая следующие запросы:</span><span class="sxs-lookup"><span data-stu-id="1277a-178">All grouping operators are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, including the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> <span data-ttu-id="1277a-179">Операции группирования следует выполнять на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="1277a-179">Grouping operations must be performed on the client.</span></span>|  
|<span data-ttu-id="1277a-180">Статистические операторы</span><span class="sxs-lookup"><span data-stu-id="1277a-180">Aggregate operators</span></span>|<span data-ttu-id="1277a-181">Все статистические операторы не поддерживаются в запросе <xref:System.Data.Services.Client.DataServiceQuery%601>, включая следующие запросы:</span><span class="sxs-lookup"><span data-stu-id="1277a-181">All aggregate operations are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, including the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> <span data-ttu-id="1277a-182">Статистические операции должны выполняться на стороне клиента либо инкапсулироваться операцией службы.</span><span class="sxs-lookup"><span data-stu-id="1277a-182">Aggregate operations must either be performed on the client or be encapsulated by a service operation.</span></span>|  
|<span data-ttu-id="1277a-183">Операторы разбиения на страницы</span><span class="sxs-lookup"><span data-stu-id="1277a-183">Paging operators</span></span>|<span data-ttu-id="1277a-184">Следующие операторы разбиения на страницы не поддерживаются в запросе <xref:System.Data.Services.Client.DataServiceQuery%601>:</span><span class="sxs-lookup"><span data-stu-id="1277a-184">The following paging operators are not supported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A><br/><br/><span data-ttu-id="1277a-185">**Примечание.**  Операторы разбиения на страницы, выполняемые в пустой последовательности, возвращают значение null.</span><span class="sxs-lookup"><span data-stu-id="1277a-185">**Note:**  Paging operators that are executed on an empty sequence return null.</span></span>|  
|<span data-ttu-id="1277a-186">Другие операторы</span><span class="sxs-lookup"><span data-stu-id="1277a-186">Other operators</span></span>|<span data-ttu-id="1277a-187">Следующие операторы также не поддерживаются для <xref:System.Data.Services.Client.DataServiceQuery%601> :</span><span class="sxs-lookup"><span data-stu-id="1277a-187">The following operators are also not supported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> - <xref:System.Linq.Enumerable.Empty%2A><br />- <xref:System.Linq.Enumerable.Range%2A><br />- <xref:System.Linq.Enumerable.Repeat%2A><br />- <xref:System.Linq.Enumerable.ToDictionary%2A><br />- <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>

## <a name="supported-expression-functions"></a><span data-ttu-id="1277a-188">Поддерживаемые функции выражений</span><span class="sxs-lookup"><span data-stu-id="1277a-188">Supported Expression Functions</span></span>  

 <span data-ttu-id="1277a-189">Поддерживаются следующие методы и свойства среды CLR, так как их можно преобразовать в выражение запроса для включения в URI запроса в службу OData:</span><span class="sxs-lookup"><span data-stu-id="1277a-189">The following common-language runtime (CLR) methods and properties are supported because they can be translated in a query expression for inclusion in the request URI to an OData service:</span></span>  
  
|<span data-ttu-id="1277a-190">Элемент <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="1277a-190"><xref:System.String> Member</span></span>|<span data-ttu-id="1277a-191">Поддерживаемая функция OData</span><span class="sxs-lookup"><span data-stu-id="1277a-191">Supported OData Function</span></span>|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<span data-ttu-id="1277a-192"><xref:System.DateTime> Член<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1277a-192"><xref:System.DateTime> Member<sup>1</sup></span></span>|<span data-ttu-id="1277a-193">Поддерживаемая функция OData</span><span class="sxs-lookup"><span data-stu-id="1277a-193">Supported OData Function</span></span>|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <span data-ttu-id="1277a-194"><sup>1</sup> Также поддерживаются эквивалентные свойства даты и времени <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType> <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> метода и в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1277a-194"><sup>1</sup>The equivalent date and time properties of <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType> and the <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> method in Visual Basic are also supported.</span></span>  
  
|<span data-ttu-id="1277a-195">Элемент <xref:System.Math></span><span class="sxs-lookup"><span data-stu-id="1277a-195"><xref:System.Math> Member</span></span>|<span data-ttu-id="1277a-196">Поддерживаемая функция OData</span><span class="sxs-lookup"><span data-stu-id="1277a-196">Supported OData Function</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<span data-ttu-id="1277a-197">Элемент <xref:System.Linq.Expressions.Expression></span><span class="sxs-lookup"><span data-stu-id="1277a-197"><xref:System.Linq.Expressions.Expression> Member</span></span>|<span data-ttu-id="1277a-198">Поддерживаемая функция OData</span><span class="sxs-lookup"><span data-stu-id="1277a-198">Supported OData Function</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 <span data-ttu-id="1277a-199">Клиент может также вычислить дополнительные функции среды CLR на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="1277a-199">The client may also be able to evaluate additional CLR functions on the client.</span></span> <span data-ttu-id="1277a-200">Исключение <xref:System.NotSupportedException> возникает для любого выражения, которое не может быть вычислено на стороне клиента и преобразовано в действительный URI-запрос для вычисления на сервере.</span><span class="sxs-lookup"><span data-stu-id="1277a-200">A <xref:System.NotSupportedException> is raised for any expression that cannot be evaluated on the client and cannot be translated into a valid request URI for evaluation on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1277a-201">См. также</span><span class="sxs-lookup"><span data-stu-id="1277a-201">See also</span></span>

- [<span data-ttu-id="1277a-202">Выполнение запросов к службе данных</span><span class="sxs-lookup"><span data-stu-id="1277a-202">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)
- [<span data-ttu-id="1277a-203">Проекции запросов</span><span class="sxs-lookup"><span data-stu-id="1277a-203">Query Projections</span></span>](query-projections-wcf-data-services.md)
- [<span data-ttu-id="1277a-204">Материализация объектов</span><span class="sxs-lookup"><span data-stu-id="1277a-204">Object Materialization</span></span>](object-materialization-wcf-data-services.md)
- [<span data-ttu-id="1277a-205">OData: условные обозначения URI</span><span class="sxs-lookup"><span data-stu-id="1277a-205">OData: URI Conventions</span></span>](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)
