---
description: Дополнительные сведения:--(комментарий) (Entity SQL)
title: -- (комментарий) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 793649177d9e64bead7b8755f35bdb51f53f4dd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724977"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="786ec-103">-- (комментарий) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="786ec-103">-- (Comment) (Entity SQL)</span></span>

<span data-ttu-id="786ec-104">Запросы[!INCLUDE[esql](../../../../../../includes/esql-md.md)] могут содержать комментарии.</span><span class="sxs-lookup"><span data-stu-id="786ec-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries can contain comments.</span></span> <span data-ttu-id="786ec-105">Строка комментария начинается с двух дефисов (`--`).</span><span class="sxs-lookup"><span data-stu-id="786ec-105">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="786ec-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="786ec-106">Syntax</span></span>  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="786ec-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="786ec-107">Arguments</span></span>  

 `text_of_comment`  
 <span data-ttu-id="786ec-108">Строка, содержащая текст комментария.</span><span class="sxs-lookup"><span data-stu-id="786ec-108">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="786ec-109">Пример</span><span class="sxs-lookup"><span data-stu-id="786ec-109">Example</span></span>  

 <span data-ttu-id="786ec-110">Следующий запрос Entity SQL демонстрирует использование комментариев.</span><span class="sxs-lookup"><span data-stu-id="786ec-110">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="786ec-111">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="786ec-111">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="786ec-112">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="786ec-112">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="786ec-113">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="786ec-113">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="786ec-114">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="786ec-114">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="786ec-115">См. также</span><span class="sxs-lookup"><span data-stu-id="786ec-115">See also</span></span>

- [<span data-ttu-id="786ec-116">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="786ec-116">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="786ec-117">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="786ec-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
