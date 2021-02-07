---
description: Дополнительные сведения о предложении DISTINCT (Visual Basic)
title: Предложение Distinct
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: df1cdc58f7af406533e67a396a958a26b0c79635
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700654"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="9d7cf-103">Предложение Distinct (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d7cf-103">Distinct Clause (Visual Basic)</span></span>

<span data-ttu-id="9d7cf-104">Ограничивают значения текущей переменной диапазона, чтобы исключить дублирующиеся значения в последующих предложениях запроса.</span><span class="sxs-lookup"><span data-stu-id="9d7cf-104">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7cf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9d7cf-105">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="9d7cf-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="9d7cf-106">Remarks</span></span>  

 <span data-ttu-id="9d7cf-107">`Distinct`Для получения списка уникальных элементов можно использовать предложение.</span><span class="sxs-lookup"><span data-stu-id="9d7cf-107">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="9d7cf-108">`Distinct`Предложение приводит к тому, что запрос пропускает дублирующиеся результаты запроса.</span><span class="sxs-lookup"><span data-stu-id="9d7cf-108">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="9d7cf-109">`Distinct`Предложение применяется к повторяющимися значениям для всех полей возврата, указанных в `Select` предложении.</span><span class="sxs-lookup"><span data-stu-id="9d7cf-109">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="9d7cf-110">Если `Select` предложение не указано, `Distinct` предложение применяется к переменной диапазона для запроса, указанного в `From` предложении.</span><span class="sxs-lookup"><span data-stu-id="9d7cf-110">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="9d7cf-111">Если переменная диапазона не является неизменяемым типом, запрос будет игнорировать только результат запроса, если все элементы типа соответствуют существующему результату запроса.</span><span class="sxs-lookup"><span data-stu-id="9d7cf-111">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d7cf-112">Пример</span><span class="sxs-lookup"><span data-stu-id="9d7cf-112">Example</span></span>  

 <span data-ttu-id="9d7cf-113">Следующее выражение запроса соединяет список клиентов и список заказов клиентов.</span><span class="sxs-lookup"><span data-stu-id="9d7cf-113">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="9d7cf-114">`Distinct`Предложение включается для возврата списка уникальных имен клиентов и дат заказов.</span><span class="sxs-lookup"><span data-stu-id="9d7cf-114">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="9d7cf-115">См. также</span><span class="sxs-lookup"><span data-stu-id="9d7cf-115">See also</span></span>

- <span data-ttu-id="9d7cf-116">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d7cf-116">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="9d7cf-117">Запросы</span><span class="sxs-lookup"><span data-stu-id="9d7cf-117">Queries</span></span>](index.md)
- [<span data-ttu-id="9d7cf-118">Предложение From</span><span class="sxs-lookup"><span data-stu-id="9d7cf-118">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="9d7cf-119">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="9d7cf-119">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="9d7cf-120">Предложение WHERE</span><span class="sxs-lookup"><span data-stu-id="9d7cf-120">Where Clause</span></span>](where-clause.md)
