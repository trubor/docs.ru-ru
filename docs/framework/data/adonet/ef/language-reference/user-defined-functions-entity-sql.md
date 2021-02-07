---
description: 'Дополнительные сведения: функции User-Defined (Entity SQL)'
title: Пользовательские функции (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: b5ebff087da08530e13f301e58509ba2d90c3605
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673210"
---
# <a name="user-defined-functions-entity-sql"></a><span data-ttu-id="d0eec-103">Пользовательские функции (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d0eec-103">User-Defined Functions (Entity SQL)</span></span>

<span data-ttu-id="d0eec-104">Entity SQL поддерживает вызов встроенных определяемых пользователем функций в запросе.</span><span class="sxs-lookup"><span data-stu-id="d0eec-104">Entity SQL supports calling user-defined functions in a query.</span></span> <span data-ttu-id="d0eec-105">Эти функции можно определить в строке запроса (см [. раздел как вызвать функцию User-Defined](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) или как часть концептуальной модели (см. раздел [как определить пользовательские функции в концептуальной модели](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="d0eec-105">You can define these functions inline with the query (see [How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) or as part of the conceptual model (see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))).</span></span> <span data-ttu-id="d0eec-106">Функции концептуальной модели определяются как команда Entity SQL в элементе [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) элемента [Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="d0eec-106">Conceptual model functions are defined as an Entity SQL command in the [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) element of a [Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) element in the conceptual model.</span></span>  
  
 <span data-ttu-id="d0eec-107">Entity SQL позволяет определить функции в самой команде запроса.</span><span class="sxs-lookup"><span data-stu-id="d0eec-107">Entity SQL enables you to define functions in the query command itself.</span></span> <span data-ttu-id="d0eec-108">Оператор [функции](function-entity-sql.md) определяет встроенные функции.</span><span class="sxs-lookup"><span data-stu-id="d0eec-108">The [FUNCTION](function-entity-sql.md) operator defines inline functions.</span></span> <span data-ttu-id="d0eec-109">В одной команде можно задать несколько функций с одним и тем же именем при условии, что эти функции имеют уникальные сигнатуры.</span><span class="sxs-lookup"><span data-stu-id="d0eec-109">You can define multiple functions in a single command, and these functions can have the same function name, as long as the function signatures are unique.</span></span> <span data-ttu-id="d0eec-110">Для получения дополнительной информации см. [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d0eec-110">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0eec-111">См. также</span><span class="sxs-lookup"><span data-stu-id="d0eec-111">See also</span></span>

- [<span data-ttu-id="d0eec-112">Функции</span><span class="sxs-lookup"><span data-stu-id="d0eec-112">Functions</span></span>](functions-entity-sql.md)
