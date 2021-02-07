---
description: 'Дополнительные сведения: LINQ to DataSet'
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 74b5f97d9fecb05b1fd13e986dd0cbcc10fa1456
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681673"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="d85cd-103">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="d85cd-103">LINQ to DataSet</span></span>

<span data-ttu-id="d85cd-104">LINQ to DataSet упрощает и ускоряет выполнение запросов к данным, кэшированным в <xref:System.Data.DataSet> объекте.</span><span class="sxs-lookup"><span data-stu-id="d85cd-104">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="d85cd-105">В частности, LINQ to DataSet упрощает выполнение запросов, позволяя разработчикам писать запросы с самого языка программирования, а не с помощью отдельного языка запросов.</span><span class="sxs-lookup"><span data-stu-id="d85cd-105">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="d85cd-106">Это особенно удобно для разработчиков Visual Studio, которые теперь могут использовать преимущества проверки синтаксиса во время компиляции, статическую типизацию и поддержку IntelliSense, предоставляемую Visual Studio в своих запросах.</span><span class="sxs-lookup"><span data-stu-id="d85cd-106">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="d85cd-107">LINQ to DataSet также можно использовать для запроса данных, консолидированных из одного или нескольких источников данных.</span><span class="sxs-lookup"><span data-stu-id="d85cd-107">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="d85cd-108">Это удовлетворяет многим сценариям, требующим гибкости при представлении и обработке данных, таких как запросы к данным, прошедшим локальную агрегатную обработку, и кэширование на среднем уровне в веб-приложениях.</span><span class="sxs-lookup"><span data-stu-id="d85cd-108">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="d85cd-109">В частности, этот метод обработки требуется для универсальных приложений отчетности, анализа и бизнес-аналитики.</span><span class="sxs-lookup"><span data-stu-id="d85cd-109">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="d85cd-110">Функции LINQ to DataSet предоставляются главным образом через методы расширения в <xref:System.Data.DataRowExtensions> <xref:System.Data.DataTableExtensions> классах и.</span><span class="sxs-lookup"><span data-stu-id="d85cd-110">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="d85cd-111">LINQ to DataSet строится на основе существующей архитектуры ADO.NET и не предназначена для замены ADO.NET в коде приложения.</span><span class="sxs-lookup"><span data-stu-id="d85cd-111">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="d85cd-112">Существующий код ADO.NET будет продолжать работать в приложении LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="d85cd-112">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="d85cd-113">Отношение LINQ to DataSet к ADO.NET и хранилищу данных показано на следующей схеме.</span><span class="sxs-lookup"><span data-stu-id="d85cd-113">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![Схема, показывающая, что LINQ to DataSet основан на поставщике ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="d85cd-115">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="d85cd-115">In This Section</span></span>  

 [<span data-ttu-id="d85cd-116">Начало работы</span><span class="sxs-lookup"><span data-stu-id="d85cd-116">Getting Started</span></span>](getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="d85cd-117">Руководство по программированию</span><span class="sxs-lookup"><span data-stu-id="d85cd-117">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="d85cd-118">Справочник</span><span class="sxs-lookup"><span data-stu-id="d85cd-118">Reference</span></span>  

 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="d85cd-119">См. также</span><span class="sxs-lookup"><span data-stu-id="d85cd-119">See also</span></span>

- [<span data-ttu-id="d85cd-120">LINQ — C#</span><span class="sxs-lookup"><span data-stu-id="d85cd-120">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d85cd-121">LINQ — Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d85cd-121">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d85cd-122">LINQ и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d85cd-122">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="d85cd-123">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d85cd-123">ADO.NET</span></span>](index.md)
