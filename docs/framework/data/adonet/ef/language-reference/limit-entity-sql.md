---
description: 'Дополнительные сведения о: LIMIT (Entity SQL)'
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 873f3fd5ed83d04313aff92bf1f97e07001c3f08
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748210"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="9935d-103">LIMIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9935d-103">LIMIT (Entity SQL)</span></span>

<span data-ttu-id="9935d-104">Вложенное предложение LIMIT в предложении ORDER BY позволяет проводить физическое разбиение на страницы.</span><span class="sxs-lookup"><span data-stu-id="9935d-104">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="9935d-105">Ключевое слово LIMIT не может использоваться отдельно от предложения ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="9935d-105">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9935d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9935d-106">Syntax</span></span>  
  
```sql  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9935d-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="9935d-107">Arguments</span></span>  

 `n`  
 <span data-ttu-id="9935d-108">Число элементов, которые будут выбраны.</span><span class="sxs-lookup"><span data-stu-id="9935d-108">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="9935d-109">Если в предложении ORDER BY имеется подчиненное выражение LIMIT, результаты запроса будут отсортированы в соответствии со спецификацией сортировки, а количество строк в наборе будет ограничено выражением LIMIT.</span><span class="sxs-lookup"><span data-stu-id="9935d-109">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="9935d-110">Например, LIMIT 5 ограничит результирующий набор до пяти экземпляров строк.</span><span class="sxs-lookup"><span data-stu-id="9935d-110">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="9935d-111">Ключевое слово LIMIT является функциональным эквивалентом оператора TOP, однако для LIMIT необходимо присутствие предложения ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="9935d-111">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="9935d-112">Предложения SKIP и LIMIT могут использоваться в предложении ORDER BY независимо друг от друга.</span><span class="sxs-lookup"><span data-stu-id="9935d-112">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9935d-113">Если в одном выражении запроса присутствуют модификатор TOP и вложенное предложение SKIP, то запрос Entity SQL является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="9935d-113">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="9935d-114">Его следует переписать, заменив выражение TOP выражением LIMIT.</span><span class="sxs-lookup"><span data-stu-id="9935d-114">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9935d-115">Пример</span><span class="sxs-lookup"><span data-stu-id="9935d-115">Example</span></span>  

 <span data-ttu-id="9935d-116">В следующем запросе Entity SQL оператор ORDER BY с предложением LIMIT задает порядок сортировки, используемый для объектов, возвращаемых инструкцией SELECT.</span><span class="sxs-lookup"><span data-stu-id="9935d-116">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="9935d-117">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="9935d-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9935d-118">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="9935d-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9935d-119">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9935d-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9935d-120">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="9935d-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LIMIT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="9935d-121">См. также</span><span class="sxs-lookup"><span data-stu-id="9935d-121">See also</span></span>

- [<span data-ttu-id="9935d-122">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="9935d-122">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="9935d-123">[Практическое руководство. Разбивка на страницы результатов запроса](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9935d-123">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="9935d-124">Разбивка на страницы</span><span class="sxs-lookup"><span data-stu-id="9935d-124">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="9935d-125">В начало</span><span class="sxs-lookup"><span data-stu-id="9935d-125">TOP</span></span>](top-entity-sql.md)
