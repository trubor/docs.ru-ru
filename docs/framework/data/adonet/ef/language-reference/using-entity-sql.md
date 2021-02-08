---
description: 'Дополнительные сведения: использование (Entity SQL)'
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 084ab56f25041377dd6a0a35dd743122f482eeba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795057"
---
# <a name="using-entity-sql"></a><span data-ttu-id="82b88-103">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="82b88-103">USING (Entity SQL)</span></span>

<span data-ttu-id="82b88-104">Задает пространства имен, используемые в выражении запроса.</span><span class="sxs-lookup"><span data-stu-id="82b88-104">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82b88-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="82b88-105">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="82b88-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="82b88-106">Arguments</span></span>  

 `alias`  
 <span data-ttu-id="82b88-107">Задает более короткий псевдоним, с помощью которого можно уточнить применяемое пространство имен.</span><span class="sxs-lookup"><span data-stu-id="82b88-107">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="82b88-108">Любое допустимое пространство имен.</span><span class="sxs-lookup"><span data-stu-id="82b88-108">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82b88-109">Пример</span><span class="sxs-lookup"><span data-stu-id="82b88-109">Example</span></span>  

 <span data-ttu-id="82b88-110">В следующем запросе Entity SQL используется оператор USING для задания пространства имен, используемого в выражении запроса.</span><span class="sxs-lookup"><span data-stu-id="82b88-110">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="82b88-111">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="82b88-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="82b88-112">Выполните процедуру, описанную в разделе [инструкции. выполнение запроса, возвращающего тип PrimitiveType результаты](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="82b88-112">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="82b88-113">Передайте следующий запрос в качестве аргумента методу `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="82b88-113">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="82b88-114">См. также</span><span class="sxs-lookup"><span data-stu-id="82b88-114">See also</span></span>

- [<span data-ttu-id="82b88-115">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="82b88-115">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="82b88-116">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="82b88-116">Entity SQL Reference</span></span>](entity-sql-reference.md)
