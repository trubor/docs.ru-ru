---
description: 'Дополнительные сведения: запросы к наборам данных (LINQ to DataSet)'
title: Запросы к наборам данных (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 609de99069d39317d8d372cb2a7f43ea301ada2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663460"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="f345f-103">Запросы к наборам данных (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="f345f-103">Querying DataSets (LINQ to DataSet)</span></span>

<span data-ttu-id="f345f-104">После того как в объекте <xref:System.Data.DataSet> появятся данные, к нему можно выполнять запросы.</span><span class="sxs-lookup"><span data-stu-id="f345f-104">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="f345f-105">Запросы составления с LINQ to DataSet похожи на использование Language-Integrated query (LINQ) с другими источниками данных, поддерживающими LINQ.</span><span class="sxs-lookup"><span data-stu-id="f345f-105">Formulating queries with LINQ to DataSet is similar to using Language-Integrated Query (LINQ) against other LINQ-enabled data sources.</span></span> <span data-ttu-id="f345f-106">Однако помните, что при использовании запросов LINQ через <xref:System.Data.DataSet> объект выполняется запрос перечисления <xref:System.Data.DataRow> объектов вместо перечисления настраиваемого типа.</span><span class="sxs-lookup"><span data-stu-id="f345f-106">Remember, however, that when you use LINQ queries over a <xref:System.Data.DataSet> object, you're querying an enumeration of <xref:System.Data.DataRow> objects instead of an enumeration of a custom type.</span></span> <span data-ttu-id="f345f-107">Это означает, что вы можете использовать любой из членов <xref:System.Data.DataRow> класса в запросах LINQ.</span><span class="sxs-lookup"><span data-stu-id="f345f-107">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your LINQ queries.</span></span> <span data-ttu-id="f345f-108">Это позволяет создавать сложные сложных запросы.</span><span class="sxs-lookup"><span data-stu-id="f345f-108">This lets you create rich, complex queries.</span></span>  
  
 <span data-ttu-id="f345f-109">Как и в других реализациях LINQ, запросы LINQ to DataSet можно создавать в двух разных формах: синтаксис выражений запроса и синтаксис запросов на основе методов.</span><span class="sxs-lookup"><span data-stu-id="f345f-109">As with other implementations of LINQ, you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="f345f-110">Синтаксис выражений запросов или синтаксис запросов на основе методов можно использовать для выполнения запросов к отдельным таблицам в <xref:System.Data.DataSet>, к нескольким таблицам в <xref:System.Data.DataSet> или к таблицам в типизированном <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f345f-110">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f345f-111">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="f345f-111">In This Section</span></span>  

 [<span data-ttu-id="f345f-112">Запросы к одной таблице</span><span class="sxs-lookup"><span data-stu-id="f345f-112">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="f345f-113">Описывается выполнение запросов к отдельным таблицам.</span><span class="sxs-lookup"><span data-stu-id="f345f-113">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="f345f-114">Запросы между таблицами</span><span class="sxs-lookup"><span data-stu-id="f345f-114">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="f345f-115">Описывается выполнение межтабличных запросов.</span><span class="sxs-lookup"><span data-stu-id="f345f-115">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="f345f-116">Запрос к типизированным объектам DataSet</span><span class="sxs-lookup"><span data-stu-id="f345f-116">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="f345f-117">Описываются запросы к типизированным объектам <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f345f-117">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f345f-118">См. также</span><span class="sxs-lookup"><span data-stu-id="f345f-118">See also</span></span>

- [<span data-ttu-id="f345f-119">Примеры LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f345f-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="f345f-120">Загрузка данных в набор данных</span><span class="sxs-lookup"><span data-stu-id="f345f-120">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
