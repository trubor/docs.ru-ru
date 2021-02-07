---
description: 'Дополнительные сведения о коллекции: COLLECTION (Entity SQL)'
title: COLLECTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 1269680b2a9009277e79337cfe4df154885b7c1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697053"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="07e90-103">COLLECTION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="07e90-103">COLLECTION (Entity SQL)</span></span>

<span data-ttu-id="07e90-104">Ключевое слово COLLECTION используется только в определении встроенной функции.</span><span class="sxs-lookup"><span data-stu-id="07e90-104">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="07e90-105">Функции коллекций — это функции, которые работают с коллекциями значений и возвращают скалярное значение.</span><span class="sxs-lookup"><span data-stu-id="07e90-105">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e90-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="07e90-106">Syntax</span></span>  
  
```csharp  
COLLECTION(type_definition)
```  
  
## <a name="arguments"></a><span data-ttu-id="07e90-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="07e90-107">Arguments</span></span>  

 `type_definition`  
 <span data-ttu-id="07e90-108">Выражение, возвращающее коллекцию поддерживаемых типов, строк или ссылок.</span><span class="sxs-lookup"><span data-stu-id="07e90-108">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07e90-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="07e90-109">Remarks</span></span>  

 <span data-ttu-id="07e90-110">Дополнительные сведения о ключевом слове COLLECTION см. в статье [Type Definitions](type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="07e90-110">For more information about the COLLECTION keyword, see [Type Definitions](type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07e90-111">Пример</span><span class="sxs-lookup"><span data-stu-id="07e90-111">Example</span></span>  

 <span data-ttu-id="07e90-112">Следующий образец иллюстрирует использование ключевого слова COLLECTION для объявления коллекции десятичных чисел в качестве аргумента для встроенной функции запроса.</span><span class="sxs-lookup"><span data-stu-id="07e90-112">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="07e90-113">См. также</span><span class="sxs-lookup"><span data-stu-id="07e90-113">See also</span></span>

- [<span data-ttu-id="07e90-114">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="07e90-114">Entity SQL Reference</span></span>](entity-sql-reference.md)
