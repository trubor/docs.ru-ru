---
description: 'Дополнительные сведения о: WHERE (Entity SQL)'
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: e094a93927f6ac77aef772654f1d8d4fcf999cbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712874"
---
# <a name="where-entity-sql"></a><span data-ttu-id="5cc4c-103">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5cc4c-103">WHERE (Entity SQL)</span></span>

<span data-ttu-id="5cc4c-104">Предложение WHERE применяется непосредственно после предложения [from](from-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="5cc4c-104">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc4c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5cc4c-105">Syntax</span></span>  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5cc4c-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="5cc4c-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="5cc4c-107">Тип Boolean.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-107">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cc4c-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="5cc4c-108">Remarks</span></span>  

 <span data-ttu-id="5cc4c-109">В предложении WHERE есть та же семантика, которая описана для Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-109">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="5cc4c-110">Она ограничивает набор объектов, полученный выражением запроса, выбирая из исходной коллекции только те элементы, которые соответствуют условию.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-110">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```sql  
select c from cs as c where e  
```  
  
 <span data-ttu-id="5cc4c-111">Выражение `e` должно иметь тип Boolean.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-111">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="5cc4c-112">Предложение WHERE применяется непосредственно после предложения FROM, до выполнения любого группирования, упорядочения или проекции.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-112">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="5cc4c-113">Все имена элементов, определенные в предложении FROM, доступны в выражении предложения WHERE.</span><span class="sxs-lookup"><span data-stu-id="5cc4c-113">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc4c-114">См. также</span><span class="sxs-lookup"><span data-stu-id="5cc4c-114">See also</span></span>

- [<span data-ttu-id="5cc4c-115">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5cc4c-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5cc4c-116">Выражения запросов</span><span class="sxs-lookup"><span data-stu-id="5cc4c-116">Query Expressions</span></span>](query-expressions-entity-sql.md)
