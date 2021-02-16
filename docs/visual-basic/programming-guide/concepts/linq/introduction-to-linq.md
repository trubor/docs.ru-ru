---
description: Дополнительные сведения см. в статье Введение в LINQ (Visual Basic).
title: Введение в LINQ
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: b6be93bbf9b458ca19068961617ee08f67601edc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426794"
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="199c9-103">Знакомство с LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="199c9-103">Introduction to LINQ (Visual Basic)</span></span>

<span data-ttu-id="199c9-104">LINQ (Language-Integrated Query) — это новая возможность, появившаяся в .NET Framework версии 3.5, которая соединяет мир объектов с миром данных.</span><span class="sxs-lookup"><span data-stu-id="199c9-104">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="199c9-105">Традиционно запросы к данным выражаются в виде простых строк без проверки типов при компиляции или поддержки IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="199c9-105">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="199c9-106">Кроме того, разработчику приходится изучать различные языки запросов для каждого типа источников данных: баз данных SQL, XML-документов, различных веб-служб и т. д.</span><span class="sxs-lookup"><span data-stu-id="199c9-106">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="199c9-107">LINQ делает *запрос* к конструкции языка первого класса в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="199c9-107">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="199c9-108">Вы создаете запросы к строго типизированным коллекциям объектов с помощью ключевых слов языка и знакомых операторов.</span><span class="sxs-lookup"><span data-stu-id="199c9-108">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="199c9-109">Можно писать запросы LINQ в Visual Basic для SQL Server баз данных, XML-документов, наборов данных ADO.NET и любой коллекции объектов, поддерживающих <xref:System.Collections.IEnumerable> или универсальный <xref:System.Collections.Generic.IEnumerable%601> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="199c9-109">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="199c9-110">Кроме того, сторонние разработчики обеспечивают поддержку LINQ для множества веб-служб и других реализаций баз данных.</span><span class="sxs-lookup"><span data-stu-id="199c9-110">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="199c9-111">Запросы LINQ можно использовать в новых проектах или параллельно с запросами, не относящимися к LINQ, в существующих проектах.</span><span class="sxs-lookup"><span data-stu-id="199c9-111">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="199c9-112">Единственное требование: проект должен разрабатываться для платформы .NET Framework версии 3.5 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="199c9-112">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="199c9-113">На приведенном ниже рисунке показан частично выполненный запрос LINQ к базе данных SQL Server в C# и Visual Basic с полной проверкой типов и поддержкой IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="199c9-113">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 ![Схема, показывающая запрос LINQ с Intellisense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="199c9-115">Next Steps</span><span class="sxs-lookup"><span data-stu-id="199c9-115">Next Steps</span></span>  

 <span data-ttu-id="199c9-116">Чтобы получить дополнительные сведения о LINQ, начните с ознакомления с некоторыми основными понятиями в начало работы разделе [Начало работы с LINQ в Visual Basic](getting-started-with-linq.md), а затем прочитайте документацию по интересующей вас технологии LINQ:</span><span class="sxs-lookup"><span data-stu-id="199c9-116">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
- <span data-ttu-id="199c9-117">Базы данных SQL Server: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="199c9-117">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
- <span data-ttu-id="199c9-118">XML-документы: [LINQ to XML (Visual Basic)](../../../../standard/linq/linq-xml-overview.md)</span><span class="sxs-lookup"><span data-stu-id="199c9-118">XML documents: [LINQ to XML (Visual Basic)](../../../../standard/linq/linq-xml-overview.md)</span></span>  
  
- <span data-ttu-id="199c9-119">Наборы данных ADO.NET: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="199c9-119">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
- <span data-ttu-id="199c9-120">Коллекции .NET, файлы, строки и т. д. [LINQ to Objects (Visual Basic)](linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="199c9-120">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="199c9-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="199c9-121">See also</span></span>

- [<span data-ttu-id="199c9-122">LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="199c9-122">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
