---
description: 'Дополнительные сведения: литералы NULL и определение типа (Entity SQL)'
title: Литералы NULL и вывод типов (Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 3b3474ea9841a34970d2269173d263fda2eb1789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802142"
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="697d1-103">Литералы NULL и вывод типов (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="697d1-103">Null Literals and Type Inference (Entity SQL)</span></span>

<span data-ttu-id="697d1-104">Литералы NULL совместимы с любым типом в системе типов языка [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="697d1-104">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="697d1-105">Однако для правильного вывода типа литерала NULL накладывает [!INCLUDE[esql](../../../../../../includes/esql-md.md)] некоторые ограничения на то, где можно использовать литерал null.</span><span class="sxs-lookup"><span data-stu-id="697d1-105">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="697d1-106">Типизированные значения NULL</span><span class="sxs-lookup"><span data-stu-id="697d1-106">Typed Nulls</span></span>  

 <span data-ttu-id="697d1-107">Типизированные значения NULL могут использоваться где угодно.</span><span class="sxs-lookup"><span data-stu-id="697d1-107">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="697d1-108">Для типизированных значений NULL не требуется логический вывод типа, поскольку тип уже известен.</span><span class="sxs-lookup"><span data-stu-id="697d1-108">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="697d1-109">Например, с помощью следующей конструкции языка [!INCLUDE[esql](../../../../../../includes/esql-md.md)] можно создать значение NULL типа Int16:</span><span class="sxs-lookup"><span data-stu-id="697d1-109">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="697d1-110">Свободные литералы NULL </span><span class="sxs-lookup"><span data-stu-id="697d1-110">Free-Floating Null Literals</span></span>  

 <span data-ttu-id="697d1-111">Свободные литералы NULL используются в следующих ситуациях.</span><span class="sxs-lookup"><span data-stu-id="697d1-111">Free-floating null literals can be used in the following contexts:</span></span>  
  
- <span data-ttu-id="697d1-112">Как аргумент выражений CAST и TREAT.</span><span class="sxs-lookup"><span data-stu-id="697d1-112">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="697d1-113">Это предпочтительный способ создания типизированного выражения NULL.</span><span class="sxs-lookup"><span data-stu-id="697d1-113">This is the recommended way to produce a typed null expression.</span></span>  
  
- <span data-ttu-id="697d1-114">Как аргумент метода или функции.</span><span class="sxs-lookup"><span data-stu-id="697d1-114">As an argument to a method or a function.</span></span> <span data-ttu-id="697d1-115">Применяются стандартные правила перегрузки.</span><span class="sxs-lookup"><span data-stu-id="697d1-115">Standard overload rules apply.</span></span>  
  
- <span data-ttu-id="697d1-116">Как один из аргументов арифметического выражения, например +, - или /.</span><span class="sxs-lookup"><span data-stu-id="697d1-116">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="697d1-117">Остальные аргументы не могут быть литералами NULL, иначе вывод типа будет невозможен.</span><span class="sxs-lookup"><span data-stu-id="697d1-117">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
- <span data-ttu-id="697d1-118">Как один из аргументов логического выражения (И, ИЛИ, НЕ).</span><span class="sxs-lookup"><span data-stu-id="697d1-118">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="697d1-119">Все аргументы должны относиться к логическому типу.</span><span class="sxs-lookup"><span data-stu-id="697d1-119">All the arguments are known to be of type Boolean.</span></span>  
  
- <span data-ttu-id="697d1-120">Как аргумент выражений IS NULL и IS NOT NULL.</span><span class="sxs-lookup"><span data-stu-id="697d1-120">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
- <span data-ttu-id="697d1-121">Как один из аргументов выражения LIKE.</span><span class="sxs-lookup"><span data-stu-id="697d1-121">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="697d1-122">Все аргументы должны быть строками.</span><span class="sxs-lookup"><span data-stu-id="697d1-122">All arguments are expected to be strings.</span></span>  
  
- <span data-ttu-id="697d1-123">Как один или несколько аргументов конструктора именованного типа.</span><span class="sxs-lookup"><span data-stu-id="697d1-123">As one or more of the arguments to a named-type constructor.</span></span>  
  
- <span data-ttu-id="697d1-124">Как один или несколько аргументов конструктора мультинабора.</span><span class="sxs-lookup"><span data-stu-id="697d1-124">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="697d1-125">По крайней мере один аргумент конструктора мультинабора должен быть выражением, отличным от литерала NULL.</span><span class="sxs-lookup"><span data-stu-id="697d1-125">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
- <span data-ttu-id="697d1-126">Как один из аргументов выражений THEN и ELSE в выражении CASE.</span><span class="sxs-lookup"><span data-stu-id="697d1-126">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="697d1-127">По крайней мере одно из выражений THEN или ELSE в выражении CASE должно быть отлично от литерала NULL.</span><span class="sxs-lookup"><span data-stu-id="697d1-127">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="697d1-128">Ни в каких других ситуациях свободные литералы NULL использоваться не могут.</span><span class="sxs-lookup"><span data-stu-id="697d1-128">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="697d1-129">Например, их нельзя использовать в качестве аргументов конструктора строки.</span><span class="sxs-lookup"><span data-stu-id="697d1-129">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="697d1-130">См. также</span><span class="sxs-lookup"><span data-stu-id="697d1-130">See also</span></span>

- [<span data-ttu-id="697d1-131">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="697d1-131">Entity SQL Overview</span></span>](entity-sql-overview.md)
