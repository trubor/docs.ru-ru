---
description: 'Дополнительные сведения: Неподдерживаемые выражения'
title: Не поддерживаемые выражения (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: ceb57dc78f9685a79de987d15f7fd57a583b75a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673301"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="5fb30-103">Неподдерживаемые выражения</span><span class="sxs-lookup"><span data-stu-id="5fb30-103">Unsupported expressions</span></span>

<span data-ttu-id="5fb30-104">В этом разделе описываются выражения Transact-SQL, которые не поддерживаются в [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5fb30-104">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="5fb30-105">Дополнительные сведения см. в разделе [Entity SQL отличается от языка Transact-SQL](how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5fb30-105">For more information, see [How Entity SQL Differs from Transact-SQL](how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="5fb30-106">Количественные предикаты</span><span class="sxs-lookup"><span data-stu-id="5fb30-106">Quantified predicates</span></span>

<span data-ttu-id="5fb30-107">Transact-SQL позволяет создавать конструкции следующего вида:</span><span class="sxs-lookup"><span data-stu-id="5fb30-107">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

<span data-ttu-id="5fb30-108">Язык [!INCLUDE[esql](../../../../../../includes/esql-md.md)] такие конструкции не поддерживает.</span><span class="sxs-lookup"><span data-stu-id="5fb30-108">[!INCLUDE[esql](../../../../../../includes/esql-md.md)], however, does not support such constructs.</span></span> <span data-ttu-id="5fb30-109">Эквивалентные выражения могут быть написаны на языке [!INCLUDE[esql](../../../../../../includes/esql-md.md)] следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5fb30-109">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="5fb30-110">\* - оператор</span><span class="sxs-lookup"><span data-stu-id="5fb30-110">\* operator</span></span>

<span data-ttu-id="5fb30-111">Transact-SQL поддерживает использование оператора \* в предложении SELECT для указания того, что все столбцы должны быть прогнозируемыми. Это не поддерживается в [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5fb30-111">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="5fb30-112">См. также</span><span class="sxs-lookup"><span data-stu-id="5fb30-112">See also</span></span>

- [<span data-ttu-id="5fb30-113">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5fb30-113">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="5fb30-114">Отличия Entity SQL от Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5fb30-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)
