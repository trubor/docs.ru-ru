---
description: Дополнительные сведения см. в статье как использовать хранимые процедуры, сопоставленные с несколькими результирующими формами.
title: Практическое руководство. Как использовать хранимые процедуры, сопоставленные с несколькими результирующими формами
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 9faf80e565656120a2601b30424df80ca10913e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785826"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="27a42-103">Практическое руководство. Как использовать хранимые процедуры, сопоставленные с несколькими результирующими формами</span><span class="sxs-lookup"><span data-stu-id="27a42-103">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>

<span data-ttu-id="27a42-104">Если хранимая процедура возвращает несколько результирующих форм, тип возвращаемых данных не может быть строго типизированным в соответствии с отдельной формой проекции.</span><span class="sxs-lookup"><span data-stu-id="27a42-104">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="27a42-105">Хотя [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] может формировать все возможные типы проекций, он не может понять порядок, в котором они будут возвращены.</span><span class="sxs-lookup"><span data-stu-id="27a42-105">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="27a42-106">Этот сценарий противоположен сценарию использования хранимых процедур, которые последовательно возвращают несколько результирующих форм.</span><span class="sxs-lookup"><span data-stu-id="27a42-106">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="27a42-107">Дополнительные сведения см. [в разделе инструкции. Использование хранимых процедур, сопоставленных с последовательной фигурой результатов](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="27a42-107">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="27a42-108">Чтобы указать набор типов, которые могут возвращать хранимые процедуры, возвращающие несколько типов результатов, к этим процедурам применяется атрибут <xref:System.Data.Linq.Mapping.ResultTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="27a42-108">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27a42-109">Пример</span><span class="sxs-lookup"><span data-stu-id="27a42-109">Example</span></span>  

 <span data-ttu-id="27a42-110">В следующем примере SQL-кода результирующая форма зависит от входных данных (`shape =1` или `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="27a42-110">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="27a42-111">Какая проекция будет возвращена первой, неизвестно.</span><span class="sxs-lookup"><span data-stu-id="27a42-111">You do not know which projection will be returned first.</span></span>  
  
``` sql
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="27a42-112">Пример</span><span class="sxs-lookup"><span data-stu-id="27a42-112">Example</span></span>  

 <span data-ttu-id="27a42-113">Для выполнения этой хранимой процедуры следует использовать код, который выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="27a42-113">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27a42-114">Необходимо использовать шаблон <xref:System.Data.Linq.IMultipleResults.GetResult%2A> для получения перечислителя правильного типа на основе сведений о хранимой процедуре.</span><span class="sxs-lookup"><span data-stu-id="27a42-114">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="27a42-115">См. также</span><span class="sxs-lookup"><span data-stu-id="27a42-115">See also</span></span>

- [<span data-ttu-id="27a42-116">Хранимые процедуры</span><span class="sxs-lookup"><span data-stu-id="27a42-116">Stored Procedures</span></span>](stored-procedures.md)
