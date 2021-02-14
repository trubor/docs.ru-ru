---
description: 'Дополнительные сведения: LINQ to ADO.NET (страница портала)'
title: LINQ to ADO.NET (Страница портала)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 5fe670be0bb87fb9a18ee73b3c3ea341d787b13e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426755"
---
# <a name="linq-to-adonet-portal-page"></a><span data-ttu-id="b8a39-103">LINQ to ADO.NET (Страница портала)</span><span class="sxs-lookup"><span data-stu-id="b8a39-103">LINQ to ADO.NET (Portal Page)</span></span>

<span data-ttu-id="b8a39-104">LINQ to ADO.NET позволяет запрашивать любой перечисляемый объект в ADO.NET с помощью модели программирования LINQ.</span><span class="sxs-lookup"><span data-stu-id="b8a39-104">LINQ to ADO.NET enables you to query over any enumerable object in ADO.NET by using the Language-Integrated Query (LINQ) programming model.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8a39-105">Документация по LINQ to ADO.NET находится в разделе ADO.NET пакета SDK для .NET Framework: [LINQ и ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="b8a39-105">The LINQ to ADO.NET documentation is located in the ADO.NET section of the .NET Framework SDK: [LINQ and ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).</span></span>
  
 <span data-ttu-id="b8a39-106">Существуют три отдельные технологии ADO.NET LINQ: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] и LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="b8a39-106">There are three separate ADO.NET Language-Integrated Query (LINQ) technologies: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], and LINQ to Entities.</span></span> <span data-ttu-id="b8a39-107">Технология LINQ to DataSet обеспечивает расширенные и оптимизированные запросы к <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] позволяет запрашивать непосредственно схемы базы данных SQL Server, а LINQ to Entities — выполнять запросы к EDM.</span><span class="sxs-lookup"><span data-stu-id="b8a39-107">LINQ to DataSet provides richer, optimized querying over the <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] enables you to directly query SQL Server database schemas, and LINQ to Entities allows you to query an Entity Data Model.</span></span>  
  
## <a name="linq-to-dataset"></a><span data-ttu-id="b8a39-108">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="b8a39-108">LINQ to DataSet</span></span>  

 <span data-ttu-id="b8a39-109"><xref:System.Data.DataSet> является одним из наиболее широко используемых компонентов в ADO.NET и ключевым элементом модели автономного программирования, на основе которой создан ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="b8a39-109">The <xref:System.Data.DataSet> is one of the most widely used components in ADO.NET, and is a key element of the disconnected programming model that ADO.NET is built on.</span></span> <span data-ttu-id="b8a39-110">Несмотря на все это, объект <xref:System.Data.DataSet> имеет ограниченные возможности запросов.</span><span class="sxs-lookup"><span data-stu-id="b8a39-110">Despite this prominence, however, the <xref:System.Data.DataSet> has limited query capabilities.</span></span>  
  
 <span data-ttu-id="b8a39-111">LINQ to DataSet позволяет использовать расширенные возможности запросов в <xref:System.Data.DataSet> — те же функции, что и для многих других источников данных.</span><span class="sxs-lookup"><span data-stu-id="b8a39-111">LINQ to DataSet enables you to build richer query capabilities into <xref:System.Data.DataSet> by using the same query functionality that is available for many other data sources.</span></span>  
  
 <span data-ttu-id="b8a39-112">Дополнительные сведения см. в разделе [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="b8a39-112">For more information, see [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).</span></span>  
  
## <a name="linq-to-sql"></a><span data-ttu-id="b8a39-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b8a39-113">LINQ to SQL</span></span>  

 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] <span data-ttu-id="b8a39-114">предоставляет инфраструктуру времени выполнения для управления реляционными данными в виде объектов.</span><span class="sxs-lookup"><span data-stu-id="b8a39-114">provides a run-time infrastructure for managing relational data as objects.</span></span> <span data-ttu-id="b8a39-115">В [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] модель данных реляционной базы данных сопоставляется объектной модели, выраженной в языке программирования разработчика.</span><span class="sxs-lookup"><span data-stu-id="b8a39-115">In [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="b8a39-116">При выполнении приложения [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] преобразует интегрированные в язык запросы из объектной модели в SQL и отправляет их в базу данных для выполнения.</span><span class="sxs-lookup"><span data-stu-id="b8a39-116">When you execute the application, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] translates language-integrated queries in the object model into SQL and sends them to the database for execution.</span></span> <span data-ttu-id="b8a39-117">Когда база данных возвращает результаты, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] переводит их обратно в объекты, которыми можно управлять.</span><span class="sxs-lookup"><span data-stu-id="b8a39-117">When the database returns the results, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] translates them back into objects that you can manipulate.</span></span>  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] <span data-ttu-id="b8a39-118">включает поддержку хранимых процедур, определяемых пользователем функций в базе данных и наследования в объектной модели.</span><span class="sxs-lookup"><span data-stu-id="b8a39-118">includes support for stored procedures and user-defined functions in the database, and for inheritance in the object model.</span></span>  
  
 <span data-ttu-id="b8a39-119">Дополнительные сведения см. в разделе [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="b8a39-119">For more information, see [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).</span></span>  
  
## <a name="linq-to-entities"></a><span data-ttu-id="b8a39-120">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b8a39-120">LINQ to Entities</span></span>  

 <span data-ttu-id="b8a39-121">В модели EDM реляционные данные представлены в виде объектов в среде .NET.</span><span class="sxs-lookup"><span data-stu-id="b8a39-121">Through the Entity Data Model, relational data is exposed as objects in the .NET environment.</span></span> <span data-ttu-id="b8a39-122">Благодаря этому поддержка LINQ эффективно реализуется на уровне объектов, что позволяет составлять запросы баз данных на языке, используемом для сборки бизнес-логики.</span><span class="sxs-lookup"><span data-stu-id="b8a39-122">This makes the object layer an ideal target for LINQ support, allowing developers to formulate queries against the database from the language used to build the business logic.</span></span> <span data-ttu-id="b8a39-123">Эта функция называется LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="b8a39-123">This capability is known as LINQ to Entities.</span></span> <span data-ttu-id="b8a39-124">Дополнительные сведения см. в разделе [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="b8a39-124">See [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a39-125">См. также</span><span class="sxs-lookup"><span data-stu-id="b8a39-125">See also</span></span>

- [<span data-ttu-id="b8a39-126">LINQ и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b8a39-126">LINQ and ADO.NET</span></span>](../../../../framework/data/adonet/linq-and-ado-net.md)
- [<span data-ttu-id="b8a39-127">LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8a39-127">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
