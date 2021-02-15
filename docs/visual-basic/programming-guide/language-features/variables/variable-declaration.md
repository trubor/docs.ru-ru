---
description: Дополнительные сведения о объявлении переменных см. в Visual Basic
title: Объявление переменной
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: ef0e7bc7a99f320bd40788ef019b05c7ebf4ce46
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462702"
---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="88c91-103">Объявление переменной в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88c91-103">Variable Declaration in Visual Basic</span></span>

<span data-ttu-id="88c91-104">Переменная объявляется для указания ее имени и характеристик.</span><span class="sxs-lookup"><span data-stu-id="88c91-104">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="88c91-105">Оператор объявления для переменных является [оператором Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="88c91-105">The declaration statement for variables is the [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="88c91-106">Его расположение и содержимое определяют характеристики переменной.</span><span class="sxs-lookup"><span data-stu-id="88c91-106">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="88c91-107">Правила именования переменных и рекомендации см. в разделе [Имена объявленных элементов](../declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="88c91-107">For variable naming rules and considerations, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="88c91-108">Уровни объявления</span><span class="sxs-lookup"><span data-stu-id="88c91-108">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="88c91-109">Локальные и переменные членов</span><span class="sxs-lookup"><span data-stu-id="88c91-109">Local and Member Variables</span></span>  

 <span data-ttu-id="88c91-110">*Локальная переменная* — это одна из процедур, объявленная в процедуре.</span><span class="sxs-lookup"><span data-stu-id="88c91-110">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="88c91-111">*Переменная-член* является членом типа Visual Basic; Он объявляется на уровне модуля, внутри класса, структуры или модуля, но не внутри какой-либо процедуры, внутренней для этого класса, структуры или модуля.</span><span class="sxs-lookup"><span data-stu-id="88c91-111">A *member variable* is a member of a Visual Basic type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="88c91-112">Переменные Shared и instance</span><span class="sxs-lookup"><span data-stu-id="88c91-112">Shared and Instance Variables</span></span>  

 <span data-ttu-id="88c91-113">В классе или структуре категория переменной-члена зависит от того, является ли она общей.</span><span class="sxs-lookup"><span data-stu-id="88c91-113">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="88c91-114">Если он объявлен с ключевым словом [Shared](../../../language-reference/modifiers/shared.md) , то это *Общая переменная*, которая существует в одной копии, совместно используемой всеми экземплярами класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="88c91-114">If it is declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="88c91-115">В противном случае это *переменная экземпляра*, и ее отдельная копия создается для каждого экземпляра класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="88c91-115">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="88c91-116">Данная копия переменной экземпляра доступна только для экземпляра класса или структуры, в которой он был создан.</span><span class="sxs-lookup"><span data-stu-id="88c91-116">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="88c91-117">Он не зависит от копии переменной экземпляра в любом другом экземпляре класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="88c91-117">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="88c91-118">Объявление типа данных</span><span class="sxs-lookup"><span data-stu-id="88c91-118">Declaring Data Type</span></span>  

 <span data-ttu-id="88c91-119">Предложение [as](../../../language-reference/statements/as-clause.md) в операторе объявления позволяет определить тип данных или тип объекта объявляемой переменной.</span><span class="sxs-lookup"><span data-stu-id="88c91-119">The [As](../../../language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="88c91-120">Для переменной можно указать любой из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="88c91-120">You can specify any of the following types for a variable:</span></span>  
  
- <span data-ttu-id="88c91-121">Простейший тип данных, например `Boolean` , `Long` или `Decimal`</span><span class="sxs-lookup"><span data-stu-id="88c91-121">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
- <span data-ttu-id="88c91-122">Составной тип данных, например массив или структура</span><span class="sxs-lookup"><span data-stu-id="88c91-122">A composite data type, such as an array or structure</span></span>  
  
- <span data-ttu-id="88c91-123">Тип объекта или класс, определенный либо в приложении, либо в другом приложении</span><span class="sxs-lookup"><span data-stu-id="88c91-123">An object type, or class, defined either in your application or in another application</span></span>  
  
- <span data-ttu-id="88c91-124">Класс платформа .NET Framework, например <xref:System.Windows.Forms.Label> или <xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="88c91-124">A .NET Framework class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
- <span data-ttu-id="88c91-125">Тип интерфейса, например <xref:System.IComparable> или <xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="88c91-125">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="88c91-126">В одной инструкции можно объявить несколько переменных без повторения типа данных.</span><span class="sxs-lookup"><span data-stu-id="88c91-126">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="88c91-127">В следующих инструкциях переменные `i` , `j` и `k` объявляются как тип `Integer` , и `l` `m` как, и и, `Long` `x` `y` как `Single` :</span><span class="sxs-lookup"><span data-stu-id="88c91-127">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="88c91-128">Дополнительные сведения о типах данных см. в разделе [типы данных](../data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="88c91-128">For more information on data types, see [Data Types](../data-types/index.md).</span></span> <span data-ttu-id="88c91-129">Дополнительные сведения об объектах см. в разделе [объекты и классы](../objects-and-classes/index.md) и [программирование с помощью компонентов](/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="88c91-129">For more information on objects, see [Objects and Classes](../objects-and-classes/index.md) and [Programming with Components](/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="88c91-130">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="88c91-130">Local Type Inference</span></span>  

 <span data-ttu-id="88c91-131">*Определение типа* используется для определения типов данных локальных переменных, объявленных без `As` предложения.</span><span class="sxs-lookup"><span data-stu-id="88c91-131">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="88c91-132">Компилятор выводит тип переменной из типа выражения инициализации.</span><span class="sxs-lookup"><span data-stu-id="88c91-132">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="88c91-133">Это позволяет объявлять переменные без явного указания типа.</span><span class="sxs-lookup"><span data-stu-id="88c91-133">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="88c91-134">В следующем примере оба типа `num1` и `num2` строго типизированы как целые числа.</span><span class="sxs-lookup"><span data-stu-id="88c91-134">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 <span data-ttu-id="88c91-135">Если требуется использовать вывод локального типа, `Option Infer` необходимо задать значение `On` .</span><span class="sxs-lookup"><span data-stu-id="88c91-135">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="88c91-136">Дополнительные сведения см. в разделах [Вывод локального типа](local-type-inference.md) и [Оператор Option Infer](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="88c91-136">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="88c91-137">Характеристики объявленных переменных</span><span class="sxs-lookup"><span data-stu-id="88c91-137">Characteristics of Declared Variables</span></span>  

 <span data-ttu-id="88c91-138">Время *существования* переменной — это период времени, в течение которого она доступна для использования.</span><span class="sxs-lookup"><span data-stu-id="88c91-138">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="88c91-139">Как правило, переменная существует, пока не будет существовать элемент, объявляющий ее (например, процедуру или класс).</span><span class="sxs-lookup"><span data-stu-id="88c91-139">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="88c91-140">Если переменная не должна продолжаться за пределами времени существования содержащего его элемента, не нужно делать ничего особенного в объявлении.</span><span class="sxs-lookup"><span data-stu-id="88c91-140">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="88c91-141">Если переменная должна продолжать существовать дольше, чем содержащая ее элемент, можно включить `Static` `Shared` ключевое слово или в `Dim` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="88c91-141">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="88c91-142">Дополнительные сведения см. [в разделе время существования в Visual Basic](../declared-elements/lifetime.md).</span><span class="sxs-lookup"><span data-stu-id="88c91-142">For more information, see [Lifetime in Visual Basic](../declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="88c91-143">*Областью действия* переменной является набор всего кода, который может ссылаться на него без уточнения его имени.</span><span class="sxs-lookup"><span data-stu-id="88c91-143">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="88c91-144">Область переменной определяется тем, где она объявлена.</span><span class="sxs-lookup"><span data-stu-id="88c91-144">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="88c91-145">Код, расположенный в данном регионе, может использовать переменные, определенные в этом регионе, без уточнения их имен.</span><span class="sxs-lookup"><span data-stu-id="88c91-145">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="88c91-146">Для получения дополнительной информации см. [Scope in Visual Basic](../declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="88c91-146">For more information, see [Scope in Visual Basic](../declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="88c91-147">*Уровень доступа* переменной — это область кода, имеющая разрешение на доступ к нему.</span><span class="sxs-lookup"><span data-stu-id="88c91-147">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="88c91-148">Это определяется модификатором доступа (например, [открытым](../../../language-reference/modifiers/public.md) или [закрытым](../../../language-reference/modifiers/private.md)), который используется в `Dim` инструкции.</span><span class="sxs-lookup"><span data-stu-id="88c91-148">This is determined by the access modifier (such as [Public](../../../language-reference/modifiers/public.md) or [Private](../../../language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="88c91-149">Дополнительные сведения см. [в разделе уровни доступа в Visual Basic](../declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="88c91-149">For more information, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88c91-150">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="88c91-150">See also</span></span>

- [<span data-ttu-id="88c91-151">Практическое руководство. Создание новой переменной</span><span class="sxs-lookup"><span data-stu-id="88c91-151">How to: Create a New Variable</span></span>](how-to-create-a-new-variable.md)
- [<span data-ttu-id="88c91-152">Практическое руководство. Запись данных в переменную и их извлечение из переменной</span><span class="sxs-lookup"><span data-stu-id="88c91-152">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="88c91-153">Типы данных</span><span class="sxs-lookup"><span data-stu-id="88c91-153">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="88c91-154">Защищенный</span><span class="sxs-lookup"><span data-stu-id="88c91-154">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="88c91-155">Friend</span><span class="sxs-lookup"><span data-stu-id="88c91-155">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="88c91-156">статически.</span><span class="sxs-lookup"><span data-stu-id="88c91-156">Static</span></span>](../../../language-reference/modifiers/static.md)
- [<span data-ttu-id="88c91-157">Характеристики объявленных элементов</span><span class="sxs-lookup"><span data-stu-id="88c91-157">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="88c91-158">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="88c91-158">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="88c91-159">Оператор Option Infer</span><span class="sxs-lookup"><span data-stu-id="88c91-159">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
