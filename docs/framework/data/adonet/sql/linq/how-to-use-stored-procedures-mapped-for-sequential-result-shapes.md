---
description: Дополнительные сведения см. в статье как использовать хранимые процедуры, сопоставленные для последовательной формы результатов.
title: Практическое руководство. Как использовать хранимые процедуры, сопоставленные с последовательными результирующими формами
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 3b5791875a7beb5a0c702e787e775cd528ab2517
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738771"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="39ca9-103">Практическое руководство. Как использовать хранимые процедуры, сопоставленные с последовательными результирующими формами</span><span class="sxs-lookup"><span data-stu-id="39ca9-103">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>

<span data-ttu-id="39ca9-104">Этот тип хранимых процедур может создавать несколько результирующих форм, но всегда известно, в каком порядке возвращаются результаты.</span><span class="sxs-lookup"><span data-stu-id="39ca9-104">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="39ca9-105">Этот сценарий противоположен сценарию, в котором порядок возвращения результатов не известен.</span><span class="sxs-lookup"><span data-stu-id="39ca9-105">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="39ca9-106">Дополнительные сведения см. [в разделе инструкции. Использование хранимых процедур, сопоставленных с несколькими результирующими формами](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="39ca9-106">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="39ca9-107">Пример</span><span class="sxs-lookup"><span data-stu-id="39ca9-107">Example</span></span>  

 <span data-ttu-id="39ca9-108">Ниже представлен код T-SQL для хранимой процедуры, которая последовательно возвращает несколько результирующих наборов.</span><span class="sxs-lookup"><span data-stu-id="39ca9-108">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```sql
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="39ca9-109">Пример</span><span class="sxs-lookup"><span data-stu-id="39ca9-109">Example</span></span>  

 <span data-ttu-id="39ca9-110">Для выполнения этой хранимой процедуры следует использовать код, который выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="39ca9-110">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="39ca9-111">См. также</span><span class="sxs-lookup"><span data-stu-id="39ca9-111">See also</span></span>

- [<span data-ttu-id="39ca9-112">Хранимые процедуры</span><span class="sxs-lookup"><span data-stu-id="39ca9-112">Stored Procedures</span></span>](stored-procedures.md)
