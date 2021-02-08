---
description: 'Дополнительные сведения о: SKIP (Entity SQL)'
title: SKIP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: f4924acae6e351e076b5795cf47d63966ebdcb43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768016"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="62c40-103">SKIP (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="62c40-103">SKIP (Entity SQL)</span></span>

<span data-ttu-id="62c40-104">Вложенное предложение SKIP в предложении ORDER BY позволяет проводить физическое разбиение на страницы.</span><span class="sxs-lookup"><span data-stu-id="62c40-104">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="62c40-105">Ключевое слово SKIP не может использоваться отдельно от предложения ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="62c40-105">SKIP cannot be used separately from the ORDER BY clause.</span></span>

## <a name="syntax"></a><span data-ttu-id="62c40-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="62c40-106">Syntax</span></span>

```sql
[ SKIP n ]
```

## <a name="arguments"></a><span data-ttu-id="62c40-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="62c40-107">Arguments</span></span>

`n` \
<span data-ttu-id="62c40-108">Число элементов, которые нужно пропустить.</span><span class="sxs-lookup"><span data-stu-id="62c40-108">The number of items to skip.</span></span>

## <a name="remarks"></a><span data-ttu-id="62c40-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="62c40-109">Remarks</span></span>

<span data-ttu-id="62c40-110">Если в предложении ORDER BY есть вложенное предложение SKIP, то результаты будут отсортированы в соответствии со спецификацией сортировки, а результирующий набор будет включать строку или строки, начиная со строки, следующей непосредственно за значением выражения SKIP.</span><span class="sxs-lookup"><span data-stu-id="62c40-110">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="62c40-111">Например, SKIP 5 пропустит первые пять строк и возвратит все, начиная с шестой.</span><span class="sxs-lookup"><span data-stu-id="62c40-111">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>

> [!NOTE]
> <span data-ttu-id="62c40-112">Если в одном предложении запроса присутствуют модификатор TOP и вложенное предложение SKIP, то запрос [!INCLUDE[esql](../../../../../../includes/esql-md.md)] является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="62c40-112">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="62c40-113">Его следует переписать, заменив выражение TOP выражением LIMIT.</span><span class="sxs-lookup"><span data-stu-id="62c40-113">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>

> [!NOTE]
> <span data-ttu-id="62c40-114">В SQL Server 2000 использование инструкции SKIP с предложением ORDER BY в неключевых столбцах может привести к возврату неверных результатов.</span><span class="sxs-lookup"><span data-stu-id="62c40-114">In SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="62c40-115">Если неключевой столбец содержит повторяющиеся данные, то может быть пропущено больше указанного числа строк.</span><span class="sxs-lookup"><span data-stu-id="62c40-115">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="62c40-116">Это происходит из-за преобразования SKIP для SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="62c40-116">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="62c40-117">Например, в следующем коде может быть пропущено более пяти строк, если столбец `E.NonKeyColumn` содержит повторяющиеся значения:</span><span class="sxs-lookup"><span data-stu-id="62c40-117">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

<span data-ttu-id="62c40-118">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Запрос в статье [инструкции по результатам запроса](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) использует оператор ORDER BY с параметром SKIP, чтобы указать порядок сортировки, используемый для объектов, возвращаемых инструкцией SELECT.</span><span class="sxs-lookup"><span data-stu-id="62c40-118">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="62c40-119">См. также</span><span class="sxs-lookup"><span data-stu-id="62c40-119">See also</span></span>

- [<span data-ttu-id="62c40-120">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="62c40-120">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="62c40-121">[Практическое руководство. Разбивка на страницы результатов запроса](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="62c40-121">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="62c40-122">Разбивка на страницы</span><span class="sxs-lookup"><span data-stu-id="62c40-122">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="62c40-123">В начало</span><span class="sxs-lookup"><span data-stu-id="62c40-123">TOP</span></span>](top-entity-sql.md)
