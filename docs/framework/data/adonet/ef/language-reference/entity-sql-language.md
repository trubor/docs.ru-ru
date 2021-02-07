---
description: 'Дополнительные сведения: язык Entity SQL'
title: Язык Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: c05e561e5da3f9ee8788a25f8ca97b22444e109f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724574"
---
# <a name="entity-sql-language"></a><span data-ttu-id="7112e-103">Язык Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7112e-103">Entity SQL Language</span></span>

<span data-ttu-id="7112e-104">Entity SQL представляет собой независимый от хранилища язык запросов, аналогичный языку SQL.</span><span class="sxs-lookup"><span data-stu-id="7112e-104">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="7112e-105">Entity SQL позволяет выполнять запросы к данным сущности, представленным либо в виде объектов, либо в табличной форме.</span><span class="sxs-lookup"><span data-stu-id="7112e-105">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="7112e-106">Возможность использования Entity SQL необходимо рассматривать в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="7112e-106">You should consider using Entity SQL in the following cases:</span></span>  
  
- <span data-ttu-id="7112e-107">Если запрос должен создаваться динамически во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="7112e-107">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="7112e-108">В этом случае следует также рассмотреть возможность использования методов построителя запросов <xref:System.Data.Objects.ObjectQuery%601> вместо создания строки запроса Entity SQL во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="7112e-108">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
- <span data-ttu-id="7112e-109">Если требуется определить запрос как часть определения модели.</span><span class="sxs-lookup"><span data-stu-id="7112e-109">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="7112e-110">В модели данных поддерживается только Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="7112e-110">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="7112e-111">Дополнительные сведения см. в разделе [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl) .</span><span class="sxs-lookup"><span data-stu-id="7112e-111">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
- <span data-ttu-id="7112e-112">Если EntityClient применяется для возврата допускающих только для чтения данных сущности в виде наборов строк с использованием <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="7112e-112">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="7112e-113">Дополнительные сведения см. [в разделе Поставщик EntityClient для Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="7112e-113">For more information, see [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span></span>  
  
- <span data-ttu-id="7112e-114">Для специалиста по языкам запросов на основе SQL язык Entity SQL может оказаться самым естественным выбором.</span><span class="sxs-lookup"><span data-stu-id="7112e-114">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="7112e-115">Использование Entity SQL с поставщиком EntityClient</span><span class="sxs-lookup"><span data-stu-id="7112e-115">Using Entity SQL with the EntityClient provider</span></span>  

 <span data-ttu-id="7112e-116">Если требуется использовать Entity SQL с поставщиком EntityClient, см. дополнительные сведения в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="7112e-116">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="7112e-117">Поставщик EntityClient для Entity Framework</span><span class="sxs-lookup"><span data-stu-id="7112e-117">EntityClient Provider for the Entity Framework</span></span>](../entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="7112e-118">Практическое руководство. Сборка строки соединения EntityConnection</span><span class="sxs-lookup"><span data-stu-id="7112e-118">How to: Build an EntityConnection Connection String</span></span>](../how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="7112e-119">Практическое руководство. Выполнение запроса, возвращающего типы-примитивы</span><span class="sxs-lookup"><span data-stu-id="7112e-119">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="7112e-120">Практическое руководство. Выполнение запроса, возвращающего результаты типа StructuralType</span><span class="sxs-lookup"><span data-stu-id="7112e-120">How to: Execute a Query that Returns StructuralType Results</span></span>](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="7112e-121">Практическое руководство. Выполнение запроса, возвращающего результаты RefType</span><span class="sxs-lookup"><span data-stu-id="7112e-121">How to: Execute a Query that Returns RefType Results</span></span>](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="7112e-122">Практическое руководство. Выполнение запроса, возвращающего сложные типы</span><span class="sxs-lookup"><span data-stu-id="7112e-122">How to: Execute a Query that Returns Complex Types</span></span>](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="7112e-123">Практическое руководство. Выполнение запроса, возвращающего вложенные коллекции</span><span class="sxs-lookup"><span data-stu-id="7112e-123">How to: Execute a Query that Returns Nested Collections</span></span>](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="7112e-124">Практическое руководство. Выполнение SQL-запроса к параметрическому объекту с использованием EntityCommand</span><span class="sxs-lookup"><span data-stu-id="7112e-124">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="7112e-125">Практическое руководство. Выполнение параметризованной хранимой процедуры с использованием EntityCommand</span><span class="sxs-lookup"><span data-stu-id="7112e-125">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="7112e-126">Практическое руководство. Выполнение полиморфного запроса</span><span class="sxs-lookup"><span data-stu-id="7112e-126">How to: Execute a Polymorphic Query</span></span>](../how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="7112e-127">Практическое руководство. Переход по отношениям с помощью оператора Navigate</span><span class="sxs-lookup"><span data-stu-id="7112e-127">How to: Navigate Relationships with the Navigate Operator</span></span>](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="7112e-128">Использование Entity SQL с запросами объектов</span><span class="sxs-lookup"><span data-stu-id="7112e-128">Using Entity SQL with object queries</span></span>  

 <span data-ttu-id="7112e-129">Если требуется использовать Entity SQL с запросами объектов, см. дополнительные сведения в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="7112e-129">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 <span data-ttu-id="7112e-130">[Практическое руководство. Выполнение запроса, возвращающего объекты типа сущностей](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-130">[How to: Execute a Query that Returns Entity Type Objects](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span></span>  
  
 <span data-ttu-id="7112e-131">[Практическое руководство. Выполнение параметризованного запроса](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-131">[How to: Execute a Parameterized Query](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>  
  
 <span data-ttu-id="7112e-132">[Практическое руководство. Навигация по отношениям с помощью свойств навигации](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-132">[How to: Navigate Relationships Using Navigation Properties](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span></span>  
  
 <span data-ttu-id="7112e-133">[Практическое руководство. Вызов пользовательских функций](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-133">[How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span></span>  
  
 <span data-ttu-id="7112e-134">[Практическое руководство. Фильтрация данных](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-134">[How to: Filter Data](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span></span>  
  
 <span data-ttu-id="7112e-135">[Практическое руководство. Сортировка данных](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-135">[How to: Sort Data](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span></span>  
  
 <span data-ttu-id="7112e-136">[Практическое руководство. Группировка данных](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-136">[How to: Group Data](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span></span>  
  
 <span data-ttu-id="7112e-137">[Практическое руководство. Агрегирование данных](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-137">[How to: Aggregate Data](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span></span>  
  
 <span data-ttu-id="7112e-138">[Практическое руководство. Выполнение запроса, возвращающего объекты анонимного типа](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-138">[How to: Execute a Query that Returns Anonymous Type Objects](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>  
  
 <span data-ttu-id="7112e-139">[Практическое руководство. Выполнение запроса, возвращающего коллекцию примитивных типов](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-139">[How to: Execute a Query that Returns a Collection of Primitive Types](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span></span>  
  
 <span data-ttu-id="7112e-140">[Практическое руководство. Запросы связанных объектов в EntityCollection](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-140">[How to: Query Related Objects in an EntityCollection](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span></span>  
  
 <span data-ttu-id="7112e-141">[Практическое руководство. Порядок объединения двух запросов](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-141">[How to: Order the Union of Two Queries](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span></span>  
  
 <span data-ttu-id="7112e-142">[Практическое руководство. Разбивка на страницы результатов запроса](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7112e-142">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7112e-143">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="7112e-143">In This Section</span></span>  

 [<span data-ttu-id="7112e-144">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7112e-144">Entity SQL Overview</span></span>](entity-sql-overview.md)  
  
 [<span data-ttu-id="7112e-145">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7112e-145">Entity SQL Reference</span></span>](entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="7112e-146">См. также</span><span class="sxs-lookup"><span data-stu-id="7112e-146">See also</span></span>

- [<span data-ttu-id="7112e-147">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="7112e-147">ADO.NET Entity Framework</span></span>](../index.md)
- [<span data-ttu-id="7112e-148">Справочник по языку</span><span class="sxs-lookup"><span data-stu-id="7112e-148">Language Reference</span></span>](index.md)
