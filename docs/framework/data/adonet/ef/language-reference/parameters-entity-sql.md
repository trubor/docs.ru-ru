---
description: Дополнительные сведения о параметрах (Entity SQL)
title: Параметры (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 77b1e6ee95b5d367fec8d99345bbb416c2b9787d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724535"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="3eee7-103">Параметры (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3eee7-103">Parameters (Entity SQL)</span></span>

<span data-ttu-id="3eee7-104">Параметры - это переменные, определенные вне [!INCLUDE[esql](../../../../../../includes/esql-md.md)] обычно через привязку API, используемую базовым языком.</span><span class="sxs-lookup"><span data-stu-id="3eee7-104">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="3eee7-105">Каждый параметр имеет имя и тип.</span><span class="sxs-lookup"><span data-stu-id="3eee7-105">Each parameter has a name and a type.</span></span> <span data-ttu-id="3eee7-106">Имена параметров определены в выражениях запросов с символом (@) в качестве префикса.</span><span class="sxs-lookup"><span data-stu-id="3eee7-106">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="3eee7-107">Так они отличаются от имен свойств или других имен, определенных в запросе.</span><span class="sxs-lookup"><span data-stu-id="3eee7-107">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="3eee7-108">API-привязки базового языка предоставляет API для параметров привязки.</span><span class="sxs-lookup"><span data-stu-id="3eee7-108">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3eee7-109">Пример</span><span class="sxs-lookup"><span data-stu-id="3eee7-109">Example</span></span>  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="3eee7-110">См. также</span><span class="sxs-lookup"><span data-stu-id="3eee7-110">See also</span></span>

- [<span data-ttu-id="3eee7-111">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3eee7-111">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="3eee7-112">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3eee7-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
