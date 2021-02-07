---
description: 'Дополнительные сведения о: возврат первого элемента последовательности'
title: Возврат первого элемента в последовательности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 004e9a1f03677f6ba49916404b1c44408df40dfa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663018"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="a7859-103">Возврат первого элемента в последовательности</span><span class="sxs-lookup"><span data-stu-id="a7859-103">Return the First Element in a Sequence</span></span>

<span data-ttu-id="a7859-104">Для возвращения первого элемента последовательности используется оператор <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7859-104">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="a7859-105">Запросы, использующие оператор <xref:System.Linq.Enumerable.First%2A>, выполняются немедленно.</span><span class="sxs-lookup"><span data-stu-id="a7859-105">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a7859-106">не поддерживает оператор <xref:System.Linq.Enumerable.Last%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7859-106">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7859-107">Пример</span><span class="sxs-lookup"><span data-stu-id="a7859-107">Example</span></span>  

 <span data-ttu-id="a7859-108">В следующем примере кода выполняется поиск первого поставщика (`Shipper`) в таблице.</span><span class="sxs-lookup"><span data-stu-id="a7859-108">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="a7859-109">При выполнении данного запроса в учебной базе данных "Northwind" возвращается результат:</span><span class="sxs-lookup"><span data-stu-id="a7859-109">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="a7859-110">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="a7859-110">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="a7859-111">Пример</span><span class="sxs-lookup"><span data-stu-id="a7859-111">Example</span></span>  

 <span data-ttu-id="a7859-112">В следующем примере кода выполняется поиск отдельного клиента (`Customer`), которому присвоен код (`CustomerID`) BONAP.</span><span class="sxs-lookup"><span data-stu-id="a7859-112">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="a7859-113">При выполнении данного запроса в учебной базе данных "Northwind" возвращается результат `ID = BONAP, Contact = Laurence Lebihan`.</span><span class="sxs-lookup"><span data-stu-id="a7859-113">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="a7859-114">См. также</span><span class="sxs-lookup"><span data-stu-id="a7859-114">See also</span></span>

- [<span data-ttu-id="a7859-115">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="a7859-115">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="a7859-116">Загрузка примеров баз данных</span><span class="sxs-lookup"><span data-stu-id="a7859-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
