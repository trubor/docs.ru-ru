---
description: 'Дополнительные сведения: Method-Based примеры синтаксиса запросов: операторы element'
title: Примеры синтаксиса запросов на основе методов. Операторы элементов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 8a83602c4d374ae02b4f39ee75821718f8b53f3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673587"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="1d6e7-103">Примеры синтаксиса запросов на основе методов. Операторы элементов</span><span class="sxs-lookup"><span data-stu-id="1d6e7-103">Method-Based Query Syntax Examples: Element Operators</span></span>

<span data-ttu-id="1d6e7-104">В примерах этого раздела показано, как использовать <xref:System.Linq.Enumerable.First%2A> метод для запроса [модели AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) с помощью синтаксиса запросов на основе методов.</span><span class="sxs-lookup"><span data-stu-id="1d6e7-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="1d6e7-105">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1d6e7-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1d6e7-106">В примере в этом разделе используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="1d6e7-106">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="1d6e7-107">First</span><span class="sxs-lookup"><span data-stu-id="1d6e7-107">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="1d6e7-108">Пример</span><span class="sxs-lookup"><span data-stu-id="1d6e7-108">Example</span></span>  

 <span data-ttu-id="1d6e7-109">В следующем примере метод используется <xref:System.Linq.Enumerable.First%2A> для поиска первого адреса электронной почты, который начинается с "Кэролайн".</span><span class="sxs-lookup"><span data-stu-id="1d6e7-109">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="1d6e7-110">См. также</span><span class="sxs-lookup"><span data-stu-id="1d6e7-110">See also</span></span>

- [<span data-ttu-id="1d6e7-111">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1d6e7-111">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
