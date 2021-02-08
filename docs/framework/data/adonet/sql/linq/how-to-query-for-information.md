---
description: Дополнительные сведения см. в статье как запросить информацию
title: Практическое руководство. Как обращаться с запросами о сведениях
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 41774834fe919b28d71691203941cb8e0a8a0397
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802025"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="fa482-103">Практическое руководство. Как обращаться с запросами о сведениях</span><span class="sxs-lookup"><span data-stu-id="fa482-103">How to: Query for Information</span></span>

<span data-ttu-id="fa482-104">Запросы в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] используют тот же синтаксис, что и запросы в LINQ.</span><span class="sxs-lookup"><span data-stu-id="fa482-104">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in LINQ.</span></span> <span data-ttu-id="fa482-105">Единственное отличие заключается в том, что объекты, на которые имеются ссылки в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] запросах, сопоставляются с элементами в базе данных.</span><span class="sxs-lookup"><span data-stu-id="fa482-105">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="fa482-106">Дополнительные сведения см. в разделе [Введение в запросы LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="fa482-106">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="fa482-107">Технология [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] преобразует написанные пользователем запросы в эквивалентные запросы SQL и отправляет их на сервер для обработки.</span><span class="sxs-lookup"><span data-stu-id="fa482-107">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="fa482-108">Некоторые функции запросов LINQ могут потребовать особого внимания в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] приложениях.</span><span class="sxs-lookup"><span data-stu-id="fa482-108">Some features of LINQ queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="fa482-109">Дополнительные сведения см. в разделе [Основные понятия запросов](query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="fa482-109">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa482-110">Пример</span><span class="sxs-lookup"><span data-stu-id="fa482-110">Example</span></span>  

 <span data-ttu-id="fa482-111">Следующий запрос возвращает список клиентов из Лондона.</span><span class="sxs-lookup"><span data-stu-id="fa482-111">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="fa482-112">В этом примере используется таблица `Customers` из учебной базы данных "Northwind".</span><span class="sxs-lookup"><span data-stu-id="fa482-112">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fa482-113">См. также</span><span class="sxs-lookup"><span data-stu-id="fa482-113">See also</span></span>

- [<span data-ttu-id="fa482-114">Создание модели объектов</span><span class="sxs-lookup"><span data-stu-id="fa482-114">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="fa482-115">Загрузка примеров баз данных</span><span class="sxs-lookup"><span data-stu-id="fa482-115">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="fa482-116">Запрос к базе данных</span><span class="sxs-lookup"><span data-stu-id="fa482-116">Querying the Database</span></span>](querying-the-database.md)
