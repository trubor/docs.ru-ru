---
description: 'Дополнительные сведения о переменных: Variables (Entity SQL)'
title: Переменные (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 134fee8f61c8e87a18520e6622f6a6a5cceb0076
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795044"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="99b43-103">Переменные (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="99b43-103">Variables (Entity SQL)</span></span>

## <a name="variable"></a><span data-ttu-id="99b43-104">Переменная</span><span class="sxs-lookup"><span data-stu-id="99b43-104">Variable</span></span>  

 <span data-ttu-id="99b43-105">Выражение переменной – это ссылка на именованное выражение, определенное в текущей области.</span><span class="sxs-lookup"><span data-stu-id="99b43-105">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="99b43-106">Ссылка на переменную должна быть допустимым [!INCLUDE[esql](../../../../../../includes/esql-md.md)] идентификатором, как определено в [идентификаторах](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="99b43-106">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="99b43-107">В следующем примере показано применение переменной в выражении.</span><span class="sxs-lookup"><span data-stu-id="99b43-107">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="99b43-108">Символ `c` в предложении FROM является определением переменной.</span><span class="sxs-lookup"><span data-stu-id="99b43-108">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="99b43-109">Использование символа `c` в предложении SELECT представляет ссылку на переменную.</span><span class="sxs-lookup"><span data-stu-id="99b43-109">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="99b43-110">См. также</span><span class="sxs-lookup"><span data-stu-id="99b43-110">See also</span></span>

- [<span data-ttu-id="99b43-111">Идентификаторы</span><span class="sxs-lookup"><span data-stu-id="99b43-111">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="99b43-112">Параметры</span><span class="sxs-lookup"><span data-stu-id="99b43-112">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="99b43-113">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="99b43-113">Entity SQL Overview</span></span>](entity-sql-overview.md)
