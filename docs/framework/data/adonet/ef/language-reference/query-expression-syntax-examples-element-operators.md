---
description: 'Дополнительные сведения: примеры синтаксиса выражений запросов: операторы element'
title: Примеры синтаксиса выражений запросов. Операторы элементов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: 0dc6d49959abba712cef572eaa549138af646bd5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696247"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="eb401-103">Примеры синтаксиса выражений запросов. Операторы элементов</span><span class="sxs-lookup"><span data-stu-id="eb401-103">Query Expression Syntax Examples: Element Operators</span></span>

<span data-ttu-id="eb401-104">В примерах этого раздела показано, как использовать <xref:System.Linq.Enumerable.First%2A> метод для запроса [модели AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) с помощью синтаксиса выражения запроса.</span><span class="sxs-lookup"><span data-stu-id="eb401-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using the query expression syntax.</span></span> <span data-ttu-id="eb401-105">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="eb401-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="eb401-106">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="eb401-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="eb401-107">First</span><span class="sxs-lookup"><span data-stu-id="eb401-107">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="eb401-108">Пример</span><span class="sxs-lookup"><span data-stu-id="eb401-108">Example</span></span>  

 <span data-ttu-id="eb401-109">В следующем примере используется метод <xref:System.Linq.Enumerable.First%2A> для возврата первого контактного лица с фамилией «Brooke».</span><span class="sxs-lookup"><span data-stu-id="eb401-109">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="eb401-110">См. также</span><span class="sxs-lookup"><span data-stu-id="eb401-110">See also</span></span>

- [<span data-ttu-id="eb401-111">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="eb401-111">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
