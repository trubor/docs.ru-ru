---
description: 'Дополнительные сведения: приоритет операторов (Entity SQL)'
title: Приоритет операторов (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 72cfdecf7dfe4ce590d99e866429e771f9ede231
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739330"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="e54a7-103">Приоритет операторов (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e54a7-103">Operator Precedence (Entity SQL)</span></span>

<span data-ttu-id="e54a7-104">Если [!INCLUDE[esql](../../../../../../includes/esql-md.md)] запрос имеет несколько операторов, приоритет оператора определяет последовательность, в которой выполняются операции.</span><span class="sxs-lookup"><span data-stu-id="e54a7-104">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="e54a7-105">Порядок выполнения может существенно повлиять на результат выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="e54a7-105">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="e54a7-106">Уровни приоритета операторов показаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="e54a7-106">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="e54a7-107">Оператор с более высоким уровнем выполняется раньше оператора с более низким уровнем.</span><span class="sxs-lookup"><span data-stu-id="e54a7-107">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="e54a7-108">Уровень</span><span class="sxs-lookup"><span data-stu-id="e54a7-108">Level</span></span>|<span data-ttu-id="e54a7-109">Operation type (Тип операции)</span><span class="sxs-lookup"><span data-stu-id="e54a7-109">Operation type</span></span>|<span data-ttu-id="e54a7-110">Оператор</span><span class="sxs-lookup"><span data-stu-id="e54a7-110">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="e54a7-111">1</span><span class="sxs-lookup"><span data-stu-id="e54a7-111">1</span></span>|<span data-ttu-id="e54a7-112">Основной</span><span class="sxs-lookup"><span data-stu-id="e54a7-112">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="e54a7-113">2</span><span class="sxs-lookup"><span data-stu-id="e54a7-113">2</span></span>|<span data-ttu-id="e54a7-114">Унарный</span><span class="sxs-lookup"><span data-stu-id="e54a7-114">Unary</span></span>|`! not`|  
|<span data-ttu-id="e54a7-115">3</span><span class="sxs-lookup"><span data-stu-id="e54a7-115">3</span></span>|<span data-ttu-id="e54a7-116">Мультипликативный</span><span class="sxs-lookup"><span data-stu-id="e54a7-116">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="e54a7-117">4</span><span class="sxs-lookup"><span data-stu-id="e54a7-117">4</span></span>|<span data-ttu-id="e54a7-118">Аддитивный</span><span class="sxs-lookup"><span data-stu-id="e54a7-118">Additive</span></span>|`+ -`|  
|<span data-ttu-id="e54a7-119">5</span><span class="sxs-lookup"><span data-stu-id="e54a7-119">5</span></span>|<span data-ttu-id="e54a7-120">Упорядочение</span><span class="sxs-lookup"><span data-stu-id="e54a7-120">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="e54a7-121">6</span><span class="sxs-lookup"><span data-stu-id="e54a7-121">6</span></span>|<span data-ttu-id="e54a7-122">Равенство</span><span class="sxs-lookup"><span data-stu-id="e54a7-122">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="e54a7-123">7</span><span class="sxs-lookup"><span data-stu-id="e54a7-123">7</span></span>|<span data-ttu-id="e54a7-124">Условное И</span><span class="sxs-lookup"><span data-stu-id="e54a7-124">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="e54a7-125">8</span><span class="sxs-lookup"><span data-stu-id="e54a7-125">8</span></span>|<span data-ttu-id="e54a7-126">Условное ИЛИ</span><span class="sxs-lookup"><span data-stu-id="e54a7-126">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="e54a7-127">Если два оператора в выражении имеют один и тот же уровень приоритета, они выполняются в порядке слева направо по мере их появления в выражении.</span><span class="sxs-lookup"><span data-stu-id="e54a7-127">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="e54a7-128">Например, выражение `x+y-z` вычисляется как `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="e54a7-128">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="e54a7-129">Чтобы переопределить порядок вычисления операторов в выражении, следует использовать скобки.</span><span class="sxs-lookup"><span data-stu-id="e54a7-129">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="e54a7-130">Вначале все выражение внутри скобок вычисляется до получения одного значения, которое затем может быть использовано любым оператором за пределами скобок.</span><span class="sxs-lookup"><span data-stu-id="e54a7-130">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="e54a7-131">Например, `x+y*z` умножает на, `y` `z` а затем добавляет `x` , но `(x+y)*z` добавляет в, `x` `y` а затем умножает результат на `z` .</span><span class="sxs-lookup"><span data-stu-id="e54a7-131">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e54a7-132">См. также</span><span class="sxs-lookup"><span data-stu-id="e54a7-132">See also</span></span>

- [<span data-ttu-id="e54a7-133">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e54a7-133">Entity SQL Overview</span></span>](entity-sql-overview.md)
