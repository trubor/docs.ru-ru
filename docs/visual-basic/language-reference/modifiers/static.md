---
description: 'Дополнительные сведения о: Static (Visual Basic)'
title: Статические
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 03c2e3f64ac9052a0c604b8bc34782af16edbf34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700745"
---
# <a name="static-visual-basic"></a><span data-ttu-id="938b6-103">Static (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="938b6-103">Static (Visual Basic)</span></span>

<span data-ttu-id="938b6-104">Указывает, что одна или несколько объявленных локальных переменных должны продолжать существовать и сохранить их последние значения после завершения процедуры, в которой они объявляются.</span><span class="sxs-lookup"><span data-stu-id="938b6-104">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="938b6-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="938b6-105">Remarks</span></span>  

 <span data-ttu-id="938b6-106">Как правило, локальная переменная в процедуре прекращает свое существование сразу после остановки процедуры.</span><span class="sxs-lookup"><span data-stu-id="938b6-106">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="938b6-107">Статическая переменная продолжает существовать и сохраняет ее Последнее значение.</span><span class="sxs-lookup"><span data-stu-id="938b6-107">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="938b6-108">В следующий раз, когда код вызывает процедуру, переменная не инициализируется повторно, и она по-прежнему содержит Последнее назначенное ей значение.</span><span class="sxs-lookup"><span data-stu-id="938b6-108">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="938b6-109">Статическая переменная будет существовать в течение времени существования класса или модуля, в котором он определен.</span><span class="sxs-lookup"><span data-stu-id="938b6-109">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="938b6-110">Правила</span><span class="sxs-lookup"><span data-stu-id="938b6-110">Rules</span></span>  
  
- <span data-ttu-id="938b6-111">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="938b6-111">**Declaration Context.**</span></span> <span data-ttu-id="938b6-112">Можно использовать `Static` только для локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="938b6-112">You can use `Static` only on local variables.</span></span> <span data-ttu-id="938b6-113">Это означает, что контекст объявления для `Static` переменной должен быть процедурой или блоком в процедуре и не может быть исходным файлом, пространством имен, классом, структурой или модулем.</span><span class="sxs-lookup"><span data-stu-id="938b6-113">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="938b6-114">Нельзя использовать `Static` внутри процедуры структуры.</span><span class="sxs-lookup"><span data-stu-id="938b6-114">You cannot use `Static` inside a structure procedure.</span></span>  
  
- <span data-ttu-id="938b6-115">Типы данных `Static` локальных переменных не могут быть определены.</span><span class="sxs-lookup"><span data-stu-id="938b6-115">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="938b6-116">Дополнительные сведения см. в разделе [определение локального типа](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="938b6-116">For more information, see [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
- <span data-ttu-id="938b6-117">**Комбинированные модификаторы.**</span><span class="sxs-lookup"><span data-stu-id="938b6-117">**Combined Modifiers.**</span></span> <span data-ttu-id="938b6-118">Нельзя указывать `Static` вместе с `ReadOnly` , `Shadows` или `Shared` в одном объявлении.</span><span class="sxs-lookup"><span data-stu-id="938b6-118">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="938b6-119">Поведение</span><span class="sxs-lookup"><span data-stu-id="938b6-119">Behavior</span></span>  

 <span data-ttu-id="938b6-120">При объявлении статической переменной в `Shared` процедуре для всего приложения доступна только одна копия статической переменной.</span><span class="sxs-lookup"><span data-stu-id="938b6-120">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="938b6-121">Процедура вызывается с `Shared` помощью имени класса, а не переменной, указывающей на экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="938b6-121">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="938b6-122">При объявлении статической переменной в процедуре, которая не `Shared` имеет, для каждого экземпляра класса доступна только одна копия переменной.</span><span class="sxs-lookup"><span data-stu-id="938b6-122">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="938b6-123">Для вызова процедуры, которая не является общей, используется переменная, указывающая на конкретный экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="938b6-123">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="938b6-124">Пример</span><span class="sxs-lookup"><span data-stu-id="938b6-124">Example</span></span>  

 <span data-ttu-id="938b6-125">В следующем примере показано использование функции `Static`.</span><span class="sxs-lookup"><span data-stu-id="938b6-125">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 <span data-ttu-id="938b6-126">`Static`Переменная `totalSales` инициализируется значением 0 только один раз.</span><span class="sxs-lookup"><span data-stu-id="938b6-126">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="938b6-127">При каждом вводе `updateSales` `totalSales` по-прежнему будет присвоено самое последнее значение, вычисленное для него.</span><span class="sxs-lookup"><span data-stu-id="938b6-127">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="938b6-128">`Static`Модификатор можно использовать в этом контексте:</span><span class="sxs-lookup"><span data-stu-id="938b6-128">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="938b6-129">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="938b6-129">Dim Statement</span></span>](../statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="938b6-130">См. также</span><span class="sxs-lookup"><span data-stu-id="938b6-130">See also</span></span>

- [<span data-ttu-id="938b6-131">Shadows</span><span class="sxs-lookup"><span data-stu-id="938b6-131">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="938b6-132">Общий</span><span class="sxs-lookup"><span data-stu-id="938b6-132">Shared</span></span>](shared.md)
- [<span data-ttu-id="938b6-133">Время существования в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="938b6-133">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="938b6-134">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="938b6-134">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="938b6-135">Структуры</span><span class="sxs-lookup"><span data-stu-id="938b6-135">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="938b6-136">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="938b6-136">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="938b6-137">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="938b6-137">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
