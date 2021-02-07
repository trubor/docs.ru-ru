---
description: 'Дополнительные сведения: известные проблемы и рекомендации в LINQ to Entities'
title: 'LINQ to Entities: рекомендации и известные проблемы'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 61377fc27770cb16583e0347fff1a03b6cd44af6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748314"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="a7a47-103">LINQ to Entities: рекомендации и известные проблемы</span><span class="sxs-lookup"><span data-stu-id="a7a47-103">Known Issues and Considerations in LINQ to Entities</span></span>

<span data-ttu-id="a7a47-104">В этом разделе содержатся сведения об известных проблемах с LINQ to Entities запросами.</span><span class="sxs-lookup"><span data-stu-id="a7a47-104">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="a7a47-105">Запросы LINQ, которые нельзя кэшировать</span><span class="sxs-lookup"><span data-stu-id="a7a47-105">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="a7a47-106">Потеря данных об упорядочении</span><span class="sxs-lookup"><span data-stu-id="a7a47-106">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="a7a47-107">Целые числа без знака не поддерживаются</span><span class="sxs-lookup"><span data-stu-id="a7a47-107">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="a7a47-108">Ошибки преобразования типа</span><span class="sxs-lookup"><span data-stu-id="a7a47-108">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="a7a47-109">Обращение к нескалярным переменным не поддерживается</span><span class="sxs-lookup"><span data-stu-id="a7a47-109">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="a7a47-110">Вложенные запросы могут не работать с SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="a7a47-110">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="a7a47-111">Проектирование анонимного типа</span><span class="sxs-lookup"><span data-stu-id="a7a47-111">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>

## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="a7a47-112">Запросы LINQ, которые нельзя кэшировать</span><span class="sxs-lookup"><span data-stu-id="a7a47-112">LINQ Queries That cannot be Cached</span></span>  

 <span data-ttu-id="a7a47-113">Начиная с .NET Framework 4.5, запросы LINQ to Entities автоматически сохраняются в кэше.</span><span class="sxs-lookup"><span data-stu-id="a7a47-113">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="a7a47-114">Тем не менее запросы LINQ to Entities, которые применяют оператор `Enumerable.Contains` к коллекции в памяти, автоматически не кэшируются.</span><span class="sxs-lookup"><span data-stu-id="a7a47-114">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="a7a47-115">Также в скомпилированных запросах LINQ не допускаются коллекции в памяти с параметрами.</span><span class="sxs-lookup"><span data-stu-id="a7a47-115">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>

## <a name="ordering-information-lost"></a><span data-ttu-id="a7a47-116">Потеря данных об упорядочении</span><span class="sxs-lookup"><span data-stu-id="a7a47-116">Ordering Information Lost</span></span>  

 <span data-ttu-id="a7a47-117">Проецирование столбцов в анонимный тип приведет к потере сведений о заказе в некоторых запросах, выполняемых для базы данных SQL Server 2005, для которой задан уровень совместимости "80".</span><span class="sxs-lookup"><span data-stu-id="a7a47-117">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="a7a47-118">Это происходит в том случае, если имя столбца в списке упорядочения соответствует имени столбца в селекторе, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a7a47-118">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>

## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="a7a47-119">Целые числа без знака не поддерживаются</span><span class="sxs-lookup"><span data-stu-id="a7a47-119">Unsigned Integers Not Supported</span></span>  

 <span data-ttu-id="a7a47-120">Указание целочисленного типа без знака в LINQ to Entitiesном запросе не поддерживается, так как Entity Framework не поддерживает целые числа без знака.</span><span class="sxs-lookup"><span data-stu-id="a7a47-120">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the Entity Framework does not support unsigned integers.</span></span> <span data-ttu-id="a7a47-121">Если указать целое число без знака, <xref:System.ArgumentException> во время преобразования выражения запроса будет создано исключение, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a7a47-121">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="a7a47-122">В этом примере производится запрос заказа с идентификатором 48000.</span><span class="sxs-lookup"><span data-stu-id="a7a47-122">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>

## <a name="type-conversion-errors"></a><span data-ttu-id="a7a47-123">Ошибки преобразования типа</span><span class="sxs-lookup"><span data-stu-id="a7a47-123">Type Conversion Errors</span></span>  

 <span data-ttu-id="a7a47-124">Когда в Visual Basic свойство сопоставляется со столбцом типа данных SQL Server bit, имеющим значение 1 при помощи функции `CByte`, то возникнет исключение <xref:System.Data.SqlClient.SqlException> с сообщением «Ошибка арифметического переполнения».</span><span class="sxs-lookup"><span data-stu-id="a7a47-124">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="a7a47-125">В следующем примере производится запрос столбца `Product.MakeFlag` в образце базы данных AdventureWorks, и при переборе результатов запроса выдается исключение.</span><span class="sxs-lookup"><span data-stu-id="a7a47-125">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>

## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="a7a47-126">Обращение к нескалярным переменным не поддерживается</span><span class="sxs-lookup"><span data-stu-id="a7a47-126">Referencing Non-Scalar Variables Not Supported</span></span>  

 <span data-ttu-id="a7a47-127">Обращение к нескалярным переменным, например к сущностям, в запросе не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="a7a47-127">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="a7a47-128">При выполнении такого запроса возникает исключение <xref:System.NotSupportedException> с сообщением «Невозможно создать константу типа `EntityType`.</span><span class="sxs-lookup"><span data-stu-id="a7a47-128">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="a7a47-129">В этом контексте поддерживаются только типы-примитивы (такие как Int32, String, и Guid)».</span><span class="sxs-lookup"><span data-stu-id="a7a47-129">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7a47-130">Обращение к набору скалярных переменных поддерживается.</span><span class="sxs-lookup"><span data-stu-id="a7a47-130">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>

## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="a7a47-131">Вложенные запросы могут не работать с SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="a7a47-131">Nested Queries May Fail with SQL Server 2000</span></span>  

 <span data-ttu-id="a7a47-132">В SQL Server 2000 запросы LINQ to Entities могут не работать, если они порождают вложенные запросы Transact-SQL с тремя и более уровнями вложенности.</span><span class="sxs-lookup"><span data-stu-id="a7a47-132">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>

## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="a7a47-133">Проектирование анонимного типа</span><span class="sxs-lookup"><span data-stu-id="a7a47-133">Projecting to an Anonymous Type</span></span>  

 <span data-ttu-id="a7a47-134">Если при определении первоначального пути запроса в него включены связанные объекты с помощью метода <xref:System.Data.Objects.ObjectQuery%601.Include%2A> для <xref:System.Data.Objects.ObjectQuery%601>, а затем возвращаемые объекты анонимного типа проектировались с помощью LINQ, то объекты, указанные в методе добавления, не включаются в результаты запроса.</span><span class="sxs-lookup"><span data-stu-id="a7a47-134">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="a7a47-135">Для получения связанных объектов не следует проектировать возвращаемые типы как анонимный тип.</span><span class="sxs-lookup"><span data-stu-id="a7a47-135">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="a7a47-136">См. также</span><span class="sxs-lookup"><span data-stu-id="a7a47-136">See also</span></span>

- [<span data-ttu-id="a7a47-137">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="a7a47-137">LINQ to Entities</span></span>](linq-to-entities.md)
