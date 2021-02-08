---
description: 'Дополнительные сведения: разбиение на страницы (Entity SQL)'
title: Разбивка на страницы (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: c32474b772be359dbf2ffd46e5489cc0b4b2abb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791859"
---
# <a name="paging-entity-sql"></a><span data-ttu-id="72a44-103">Разбивка на страницы (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="72a44-103">Paging (Entity SQL)</span></span>

<span data-ttu-id="72a44-104">Физическое разбиение на страницы может быть выполнено с помощью вложенных предложений [Skip](skip-entity-sql.md) и [Limit](limit-entity-sql.md) в предложении [ORDER BY](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="72a44-104">Physical paging can be performed by using the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="72a44-105">Для детерминированного физического разбиения на страницы необходимо использовать предложения SKIP и LIMIT.</span><span class="sxs-lookup"><span data-stu-id="72a44-105">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="72a44-106">Если требуется ограничить количество строк в результате недетерминированным способом, следует использовать [Top](top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="72a44-106">If you only want to restrict the number of rows in the result in a non-deterministic way, you should use [TOP](top-entity-sql.md).</span></span> <span data-ttu-id="72a44-107">Предложения TOP и SKIP/LIMIT являются взаимоисключающими.</span><span class="sxs-lookup"><span data-stu-id="72a44-107">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="72a44-108">Общие сведения о предложении TOP</span><span class="sxs-lookup"><span data-stu-id="72a44-108">TOP Overview</span></span>  

 <span data-ttu-id="72a44-109">Предложение SELECT может иметь необязательное вложенное предложение TOP, которое следует за необязательным модификатором ALL/DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="72a44-109">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="72a44-110">Предложение TOP указывает, что в результатах запроса возвращается только набор первых строк.</span><span class="sxs-lookup"><span data-stu-id="72a44-110">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="72a44-111">Дополнительные сведения см. в разделе [Top](top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="72a44-111">For more information, see [TOP](top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="72a44-112">Общие сведения о предложениях SKIP и LIMIT</span><span class="sxs-lookup"><span data-stu-id="72a44-112">SKIP And LIMIT Overview</span></span>  

 <span data-ttu-id="72a44-113">Предложения SKIP и LIMIT являются частью предложения ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="72a44-113">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="72a44-114">Если в предложении ORDER BY имеется вложенное предложение SKIP, результаты будут отсортированы в соответствии со спецификацией сортировки, а результирующий набор будет включать строку или строки, начиная со строки, следующей непосредственно за значением выражения SKIP.</span><span class="sxs-lookup"><span data-stu-id="72a44-114">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="72a44-115">Например, SKIP 5 пропустит первые пять строк и возвратит все, начиная с шестой.</span><span class="sxs-lookup"><span data-stu-id="72a44-115">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="72a44-116">Если в предложении ORDER BY имеется подчиненное выражение LIMIT, результаты запроса будут отсортированы в соответствии со спецификацией сортировки, а количество строк в наборе будет ограничено выражением LIMIT.</span><span class="sxs-lookup"><span data-stu-id="72a44-116">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="72a44-117">Например, LIMIT 5 ограничит результирующий набор пятью экземплярами строк.</span><span class="sxs-lookup"><span data-stu-id="72a44-117">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="72a44-118">Предложения SKIP и LIMIT необязательно использовать вместе: в предложение ORDER BY можно включить только SKIP или только LIMIT.</span><span class="sxs-lookup"><span data-stu-id="72a44-118">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="72a44-119">Дополнительные сведения см. в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="72a44-119">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="72a44-120">СРАЗУ</span><span class="sxs-lookup"><span data-stu-id="72a44-120">SKIP</span></span>](skip-entity-sql.md)  
  
- [<span data-ttu-id="72a44-121">Размер</span><span class="sxs-lookup"><span data-stu-id="72a44-121">LIMIT</span></span>](limit-entity-sql.md)  
  
- [<span data-ttu-id="72a44-122">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="72a44-122">ORDER BY</span></span>](order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="72a44-123">См. также</span><span class="sxs-lookup"><span data-stu-id="72a44-123">See also</span></span>

- [<span data-ttu-id="72a44-124">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="72a44-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="72a44-125">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="72a44-125">Entity SQL Overview</span></span>](entity-sql-overview.md)
- <span data-ttu-id="72a44-126">[Практическое руководство. Разбивка на страницы результатов запроса](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="72a44-126">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
