---
description: 'Дополнительные сведения: Method-Based примеры синтаксиса запросов: преобразование'
title: Примеры синтаксиса запросов на основе методов. Преобразование
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: 054ef9291a66216b14e2f03ecebd28fb24c6574d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696754"
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="2e927-103">Примеры синтаксиса запросов на основе методов. Преобразование</span><span class="sxs-lookup"><span data-stu-id="2e927-103">Method-Based Query Syntax Examples: Conversion</span></span>

<span data-ttu-id="2e927-104">В примерах этого раздела показано, как использовать <xref:System.Linq.Enumerable.ToArray%2A> <xref:System.Linq.Enumerable.ToDictionary%2A> <xref:System.Linq.Enumerable.ToList%2A> методы и для запроса [модели AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) с помощью синтаксиса запросов на основе методов.</span><span class="sxs-lookup"><span data-stu-id="2e927-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="2e927-105">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2e927-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2e927-106">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="2e927-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="2e927-107">ToArray</span><span class="sxs-lookup"><span data-stu-id="2e927-107">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="2e927-108">Пример</span><span class="sxs-lookup"><span data-stu-id="2e927-108">Example</span></span>  

 <span data-ttu-id="2e927-109">В следующем примере метод <xref:System.Linq.Enumerable.ToArray%2A> вызывается для немедленного вычисления последовательности с получением массива.</span><span class="sxs-lookup"><span data-stu-id="2e927-109">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="2e927-110">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="2e927-110">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="2e927-111">Пример</span><span class="sxs-lookup"><span data-stu-id="2e927-111">Example</span></span>  

 <span data-ttu-id="2e927-112">В следующем примере используется метод <xref:System.Linq.Enumerable.ToDictionary%2A> для немедленного вычисления последовательности и связанного с нею ключевого выражения с получением словаря.</span><span class="sxs-lookup"><span data-stu-id="2e927-112">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="2e927-113">ToList</span><span class="sxs-lookup"><span data-stu-id="2e927-113">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="2e927-114">Пример</span><span class="sxs-lookup"><span data-stu-id="2e927-114">Example</span></span>  

 <span data-ttu-id="2e927-115">В следующем примере используется метод <xref:System.Linq.Enumerable.ToList%2A> для немедленного вычисления последовательности с получением коллекции <xref:System.Collections.Generic.List%601>, где параметр `T` относится к типу <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="2e927-115">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="2e927-116">См. также</span><span class="sxs-lookup"><span data-stu-id="2e927-116">See also</span></span>

- [<span data-ttu-id="2e927-117">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="2e927-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
