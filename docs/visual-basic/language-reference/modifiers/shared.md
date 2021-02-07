---
description: 'Дополнительные сведения: Shared (Visual Basic)'
title: Shared
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: 0cc671c67486d01026f2283837448db7b00c1a0a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700758"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="c599e-103">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c599e-103">Shared (Visual Basic)</span></span>

<span data-ttu-id="c599e-104">Указывает, что один или несколько объявленных программных элементов связаны с классом или структурой в большом объеме, а не с конкретным экземпляром класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="c599e-104">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>

## <a name="when-to-use-shared"></a><span data-ttu-id="c599e-105">Когда следует использовать Shared</span><span class="sxs-lookup"><span data-stu-id="c599e-105">When to Use Shared</span></span>

<span data-ttu-id="c599e-106">Совместное использование члена класса или структуры делает его доступным для каждого экземпляра, а не для *общего доступа*, где каждый экземпляр хранит собственную копию.</span><span class="sxs-lookup"><span data-stu-id="c599e-106">Sharing a member of a class or structure makes it available to every instance, rather than *non-shared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="c599e-107">Общий доступ может быть полезен, например, если значение переменной применяется ко всему приложению.</span><span class="sxs-lookup"><span data-stu-id="c599e-107">Sharing is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="c599e-108">Если объявить эту переменную как `Shared` , то все экземпляры получают доступ к тому же месту хранения, и если один экземпляр изменяет значение переменной, все экземпляры получают доступ к обновленному значению.</span><span class="sxs-lookup"><span data-stu-id="c599e-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>

<span data-ttu-id="c599e-109">Совместное использование не изменяет уровень доступа элемента.</span><span class="sxs-lookup"><span data-stu-id="c599e-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="c599e-110">Например, член класса может быть общим и частным (доступным только в пределах класса), а также не является общим и открытым.</span><span class="sxs-lookup"><span data-stu-id="c599e-110">For example, a class member can be shared and private (accessible only from within the class), or non-shared and public.</span></span> <span data-ttu-id="c599e-111">Дополнительные сведения см. [в разделе уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c599e-111">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

## <a name="rules"></a><span data-ttu-id="c599e-112">Правила</span><span class="sxs-lookup"><span data-stu-id="c599e-112">Rules</span></span>

- <span data-ttu-id="c599e-113">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="c599e-113">**Declaration Context.**</span></span> <span data-ttu-id="c599e-114">`Shared` можно использовать только на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="c599e-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="c599e-115">Это означает, что контекст объявления для `Shared` элемента должен быть классом или структурой и не может быть исходным файлом, пространством имен или процедурой.</span><span class="sxs-lookup"><span data-stu-id="c599e-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="c599e-116">**Комбинированные модификаторы.**</span><span class="sxs-lookup"><span data-stu-id="c599e-116">**Combined Modifiers.**</span></span> <span data-ttu-id="c599e-117">Нельзя указывать `Shared` вместе с [переопределениями](overrides.md), [переопределяемыми](overridable.md), [NotOverridable](notoverridable.md), [MustOverride](mustoverride.md)или [static](static.md) в одном объявлении.</span><span class="sxs-lookup"><span data-stu-id="c599e-117">You cannot specify `Shared` together with [Overrides](overrides.md), [Overridable](overridable.md), [NotOverridable](notoverridable.md), [MustOverride](mustoverride.md), or [Static](static.md) in the same declaration.</span></span>

- <span data-ttu-id="c599e-118">**Данному.**</span><span class="sxs-lookup"><span data-stu-id="c599e-118">**Accessing.**</span></span> <span data-ttu-id="c599e-119">Доступ к общему элементу осуществляется путем указания его имени класса или структуры, а не имени переменной определенного экземпляра его класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="c599e-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="c599e-120">Вам даже не нужно создавать экземпляр класса или структуры для доступа к его общим членам.</span><span class="sxs-lookup"><span data-stu-id="c599e-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>

     <span data-ttu-id="c599e-121">В следующем примере вызывается общая процедура, <xref:System.Double.IsNaN%2A> предоставляемая <xref:System.Double> структурой.</span><span class="sxs-lookup"><span data-stu-id="c599e-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- <span data-ttu-id="c599e-122">**Неявный общий доступ.**</span><span class="sxs-lookup"><span data-stu-id="c599e-122">**Implicit Sharing.**</span></span> <span data-ttu-id="c599e-123">Нельзя использовать `Shared` Модификатор в [операторе const](../statements/const-statement.md), но константы неявно являются общими.</span><span class="sxs-lookup"><span data-stu-id="c599e-123">You cannot use the `Shared` modifier in a [Const Statement](../statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="c599e-124">Аналогичным образом нельзя объявить член модуля или интерфейса `Shared` , но они являются неявно общими.</span><span class="sxs-lookup"><span data-stu-id="c599e-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>

## <a name="behavior"></a><span data-ttu-id="c599e-125">Поведение</span><span class="sxs-lookup"><span data-stu-id="c599e-125">Behavior</span></span>

- <span data-ttu-id="c599e-126">**Объема.**</span><span class="sxs-lookup"><span data-stu-id="c599e-126">**Storage.**</span></span> <span data-ttu-id="c599e-127">Общая переменная или событие хранится в памяти только один раз, независимо от того, сколько экземпляров вы создаете его класс или структуру.</span><span class="sxs-lookup"><span data-stu-id="c599e-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="c599e-128">Аналогично, Общая процедура или свойство содержит только один набор локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="c599e-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>

- <span data-ttu-id="c599e-129">**Доступ через переменную экземпляра.**</span><span class="sxs-lookup"><span data-stu-id="c599e-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="c599e-130">Доступ к общему элементу можно получить, добавив в него имя переменной, содержащей конкретный экземпляр его класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="c599e-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="c599e-131">Несмотря на то, что обычно работает, как и ожидалось, компилятор создает предупреждающее сообщение и предоставляет доступ через имя класса или структуры вместо переменной.</span><span class="sxs-lookup"><span data-stu-id="c599e-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>

- <span data-ttu-id="c599e-132">**Доступ через выражение экземпляра.**</span><span class="sxs-lookup"><span data-stu-id="c599e-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="c599e-133">При доступе к общему элементу с помощью выражения, возвращающего экземпляр класса или структуры, компилятор делает доступ через имя класса или структуры вместо вычисления выражения.</span><span class="sxs-lookup"><span data-stu-id="c599e-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="c599e-134">Такой доступ дает непредвиденные результаты, если выражение предназначено для выполнения других действий, а также для возврата экземпляра.</span><span class="sxs-lookup"><span data-stu-id="c599e-134">This access produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="c599e-135">В следующем примере показана такая ситуация.</span><span class="sxs-lookup"><span data-stu-id="c599e-135">The following example illustrates this situation.</span></span>
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     <span data-ttu-id="c599e-136">В предыдущем примере компилятор выдает предупреждающее сообщение в обоих случаях, когда код обращается к общему свойству `Total` через экземпляр.</span><span class="sxs-lookup"><span data-stu-id="c599e-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared property `Total` through an instance.</span></span> <span data-ttu-id="c599e-137">В каждом случае он делает доступ напрямую через класс `ShareTotal` и не использует ни одного экземпляра.</span><span class="sxs-lookup"><span data-stu-id="c599e-137">In each case, it makes the access directly through the class `ShareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="c599e-138">В случае предполагаемого вызова процедуры `ReturnClass` это означает, что он даже не создает вызов `ReturnClass` , поэтому не выполняется дополнительное действие отображения "функция ретурнкласс ()".</span><span class="sxs-lookup"><span data-stu-id="c599e-138">In the case of the intended call to the procedure `ReturnClass`, this means it does not even generate a call to `ReturnClass`, so the additional action of displaying "Function ReturnClass() called" is not performed.</span></span>

<span data-ttu-id="c599e-139">Модификатор `Shared` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="c599e-139">The `Shared` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="c599e-140">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="c599e-140">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="c599e-141">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="c599e-141">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="c599e-142">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="c599e-142">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="c599e-143">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="c599e-143">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="c599e-144">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c599e-144">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="c599e-145">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="c599e-145">Sub Statement</span></span>](../statements/sub-statement.md)
  
## <a name="see-also"></a><span data-ttu-id="c599e-146">См. также</span><span class="sxs-lookup"><span data-stu-id="c599e-146">See also</span></span>

- [<span data-ttu-id="c599e-147">Shadows</span><span class="sxs-lookup"><span data-stu-id="c599e-147">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="c599e-148">статически.</span><span class="sxs-lookup"><span data-stu-id="c599e-148">Static</span></span>](static.md)
- [<span data-ttu-id="c599e-149">Время существования в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c599e-149">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="c599e-150">Процедуры</span><span class="sxs-lookup"><span data-stu-id="c599e-150">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="c599e-151">Структуры</span><span class="sxs-lookup"><span data-stu-id="c599e-151">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="c599e-152">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="c599e-152">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
