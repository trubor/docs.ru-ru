---
description: Дополнительные сведения о затенении в Visual Basic
title: Удаленное управление
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 468ad72808d689016cacb8d2be56fa9f9fcd1eec
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434827"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="7d999-103">Сокрытие в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d999-103">Shadowing in Visual Basic</span></span>

<span data-ttu-id="7d999-104">Если два программных элемента имеют одно и то же имя, один из них может скрыть или *затенить* другой.</span><span class="sxs-lookup"><span data-stu-id="7d999-104">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="7d999-105">В такой ситуации затененный элемент недоступен для справки; Вместо этого, если в коде используется имя элемента, компилятор Visual Basic разрешает его в элемент с тенью.</span><span class="sxs-lookup"><span data-stu-id="7d999-105">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="7d999-106">Назначение</span><span class="sxs-lookup"><span data-stu-id="7d999-106">Purpose</span></span>  

 <span data-ttu-id="7d999-107">Основной задачей теневого копирования является защита определения членов класса.</span><span class="sxs-lookup"><span data-stu-id="7d999-107">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="7d999-108">Базовый класс может быть подвергнут изменениям, создающим элемент с тем же именем, что и у уже определенного.</span><span class="sxs-lookup"><span data-stu-id="7d999-108">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="7d999-109">В этом случае `Shadows` Модификатор принудительно определяет ссылки через класс на определенный член, а не на новый элемент базового класса.</span><span class="sxs-lookup"><span data-stu-id="7d999-109">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="7d999-110">Типы затенения</span><span class="sxs-lookup"><span data-stu-id="7d999-110">Types of Shadowing</span></span>  

 <span data-ttu-id="7d999-111">Элемент может скрывать другой элемент двумя разными способами.</span><span class="sxs-lookup"><span data-stu-id="7d999-111">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="7d999-112">Элемент с тенью можно объявить внутри подобласти, содержащей затененный элемент. в этом случае затенение выполняется *через область*.</span><span class="sxs-lookup"><span data-stu-id="7d999-112">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="7d999-113">Или производный класс может переопределить член базового класса, в этом случае теневая работа осуществляется *с помощью наследования*.</span><span class="sxs-lookup"><span data-stu-id="7d999-113">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="7d999-114">Затенение через область</span><span class="sxs-lookup"><span data-stu-id="7d999-114">Shadowing Through Scope</span></span>  

 <span data-ttu-id="7d999-115">Элементы программирования в одном модуле, классе или структуре могут иметь одно и то же имя, но разные области.</span><span class="sxs-lookup"><span data-stu-id="7d999-115">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="7d999-116">Когда два элемента объявляются таким образом и код ссылается на имя, к которому они относятся, элемент с более узким областью скрывает другой элемент (область видимости блока является самой узким элементом).</span><span class="sxs-lookup"><span data-stu-id="7d999-116">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="7d999-117">Например, модуль может определить `Public` переменную с именем `temp` , а процедура в модуле может объявить локальную переменную с именем `temp` .</span><span class="sxs-lookup"><span data-stu-id="7d999-117">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="7d999-118">Ссылки на `temp` из процедуры в процедуре обращаются к локальной переменной, а ссылки на `temp` из за пределами процедуры обращаются к `Public` переменной.</span><span class="sxs-lookup"><span data-stu-id="7d999-118">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="7d999-119">В этом случае переменная процедуры `temp` затеняет переменную модуля `temp` .</span><span class="sxs-lookup"><span data-stu-id="7d999-119">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="7d999-120">На следующем рисунке показаны две переменные с именами `temp` .</span><span class="sxs-lookup"><span data-stu-id="7d999-120">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="7d999-121">Локальная переменная `temp` затеняет переменную члена `temp` при доступе из своей собственной процедуры `p` .</span><span class="sxs-lookup"><span data-stu-id="7d999-121">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="7d999-122">Однако `MyClass` ключевое слово обходит затенение и обращается к переменной члена.</span><span class="sxs-lookup"><span data-stu-id="7d999-122">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![Рисунок, демонстрирующий затенение через область.](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="7d999-124">Пример затенения с помощью области см. в разделе [как скрыть переменную с тем же именем, что и у переменной](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="7d999-124">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="7d999-125">Затенение через наследование</span><span class="sxs-lookup"><span data-stu-id="7d999-125">Shadowing Through Inheritance</span></span>  

 <span data-ttu-id="7d999-126">Если производный класс переопределяет программный элемент, наследуемый от базового класса, переопределяющий элемент затеняет исходный элемент.</span><span class="sxs-lookup"><span data-stu-id="7d999-126">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="7d999-127">Можно создать тень любого типа объявленного элемента или набора перегруженных элементов с любым другим типом.</span><span class="sxs-lookup"><span data-stu-id="7d999-127">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="7d999-128">Например, `Integer` переменная может затенить `Function` процедуру.</span><span class="sxs-lookup"><span data-stu-id="7d999-128">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="7d999-129">При скрытии процедуры с помощью другой процедуры можно использовать другой список параметров и другой тип возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="7d999-129">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="7d999-130">На следующем рисунке показан базовый класс `b` и производный класс `d` , наследуемый от `b` .</span><span class="sxs-lookup"><span data-stu-id="7d999-130">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="7d999-131">Базовый класс определяет процедуру с именем `proc` , а производный класс скрывает его с помощью другой процедуры с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="7d999-131">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="7d999-132">Первая `Call` Инструкция обращается к теневой копии `proc` в производном классе.</span><span class="sxs-lookup"><span data-stu-id="7d999-132">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="7d999-133">Однако `MyBase` ключевое слово обходит затенение и обращается к затененной процедуре в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="7d999-133">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![График схемы затемнения посредством наследования](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="7d999-135">Пример затенения с помощью наследования см. в разделе [как скрыть переменную с тем же именем, что и у переменной](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) , и [как скрыть унаследованную переменную](how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="7d999-135">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="7d999-136">Затенение и уровень доступа</span><span class="sxs-lookup"><span data-stu-id="7d999-136">Shadowing and Access Level</span></span>  

 <span data-ttu-id="7d999-137">Элемент с тенью не всегда доступен из кода, использующего производный класс.</span><span class="sxs-lookup"><span data-stu-id="7d999-137">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="7d999-138">Например, он может быть объявлен `Private` .</span><span class="sxs-lookup"><span data-stu-id="7d999-138">For example, it might be declared `Private`.</span></span> <span data-ttu-id="7d999-139">В этом случае переобъявление нарушается, и компилятор разрешает любую ссылку на тот же элемент, который был бы в случае отсутствия тени.</span><span class="sxs-lookup"><span data-stu-id="7d999-139">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="7d999-140">Этот элемент является доступным элементом, который является минимальным количеством порожденных шагов назад от класса теневого копирования.</span><span class="sxs-lookup"><span data-stu-id="7d999-140">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="7d999-141">Если затененный элемент является процедурой, то решением является Ближайшая доступная версия с тем же именем, списком параметров и типом возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="7d999-141">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="7d999-142">В следующем примере показана иерархия наследования трех классов.</span><span class="sxs-lookup"><span data-stu-id="7d999-142">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="7d999-143">Каждый класс определяет `Sub` процедуру `display` , и каждый производный класс затеняет `display` процедуру в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="7d999-143">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7d999-144">В предыдущем примере производный класс `secondClass` затеняет `display` с помощью `Private` процедуры.</span><span class="sxs-lookup"><span data-stu-id="7d999-144">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="7d999-145">При `callDisplay` вызове модуля `display` в `secondClass` вызывающий код находится за пределами `secondClass` и поэтому не может получить доступ к закрытой `display` процедуре.</span><span class="sxs-lookup"><span data-stu-id="7d999-145">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="7d999-146">Затенение нарушается, и компилятор разрешает ссылку на процедуру базового класса `display` .</span><span class="sxs-lookup"><span data-stu-id="7d999-146">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="7d999-147">Однако следующий производный класс `thirdClass` объявляется `display` как `Public` , поэтому код в `callDisplay` может получить к нему доступ.</span><span class="sxs-lookup"><span data-stu-id="7d999-147">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="7d999-148">Затенение и переопределение</span><span class="sxs-lookup"><span data-stu-id="7d999-148">Shadowing and Overriding</span></span>  

 <span data-ttu-id="7d999-149">Не путайте перекрытие с переопределением.</span><span class="sxs-lookup"><span data-stu-id="7d999-149">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="7d999-150">Оба используются, когда производный класс наследует от базового класса, и оба переопределяют один объявленный элемент с другим.</span><span class="sxs-lookup"><span data-stu-id="7d999-150">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="7d999-151">Но существуют значительные различия между ними.</span><span class="sxs-lookup"><span data-stu-id="7d999-151">But there are significant differences between the two.</span></span> <span data-ttu-id="7d999-152">Сравнение см. в разделе [различия между затенением и переопределением](differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="7d999-152">For a comparison, see [Differences Between Shadowing and Overriding](differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="7d999-153">Затенение и перегрузка</span><span class="sxs-lookup"><span data-stu-id="7d999-153">Shadowing and Overloading</span></span>  

 <span data-ttu-id="7d999-154">Если вы переобъявляете тот же элемент базового класса с более чем одним элементом в производном классе, элементы с тенью становятся перегруженными версиями этого элемента.</span><span class="sxs-lookup"><span data-stu-id="7d999-154">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="7d999-155">Дополнительные сведения см. в разделе [Procedure Overloading](../procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="7d999-155">For more information, see [Procedure Overloading](../procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="7d999-156">Доступ к затененному элементу</span><span class="sxs-lookup"><span data-stu-id="7d999-156">Accessing a Shadowed Element</span></span>  

 <span data-ttu-id="7d999-157">При доступе к элементу из производного класса это обычно делается через текущий экземпляр этого производного класса путем уточнения имени элемента `Me` ключевым словом.</span><span class="sxs-lookup"><span data-stu-id="7d999-157">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="7d999-158">Если производный класс затеняет элемент базового класса, можно получить доступ к элементу базового класса, указав его с помощью `MyBase` ключевого слова.</span><span class="sxs-lookup"><span data-stu-id="7d999-158">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="7d999-159">Пример доступа к затененному элементу см. в разделе [как получить доступ к переменной, скрытой производным классом](how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="7d999-159">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="7d999-160">Объявление объектной переменной</span><span class="sxs-lookup"><span data-stu-id="7d999-160">Declaration of the Object Variable</span></span>  

 <span data-ttu-id="7d999-161">Способ создания объектной переменной также может влиять на то, имеет ли производный класс доступ к теневому элементу или к затененному элементу.</span><span class="sxs-lookup"><span data-stu-id="7d999-161">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="7d999-162">В следующем примере создаются два объекта из производного класса, но один объект объявляется как базовый класс, а другой — как производный класс.</span><span class="sxs-lookup"><span data-stu-id="7d999-162">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="7d999-163">В предыдущем примере переменная `basObj` объявлена как базовый класс.</span><span class="sxs-lookup"><span data-stu-id="7d999-163">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="7d999-164">Присвоение `dervCls` объекту объекта образует расширяющее преобразование и, следовательно, является допустимым.</span><span class="sxs-lookup"><span data-stu-id="7d999-164">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="7d999-165">Однако базовый класс не может получить доступ к версии теневого копирования переменной `z` в производном классе, поэтому компилятор разрешается `basObj.z` в исходное значение базового класса.</span><span class="sxs-lookup"><span data-stu-id="7d999-165">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d999-166">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7d999-166">See also</span></span>

- [<span data-ttu-id="7d999-167">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="7d999-167">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="7d999-168">Область видимости в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d999-168">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="7d999-169">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="7d999-169">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="7d999-170">Shadows</span><span class="sxs-lookup"><span data-stu-id="7d999-170">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="7d999-171">Переопределения</span><span class="sxs-lookup"><span data-stu-id="7d999-171">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="7d999-172">Me, My, MyBase и MyClass</span><span class="sxs-lookup"><span data-stu-id="7d999-172">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="7d999-173">Основы наследования</span><span class="sxs-lookup"><span data-stu-id="7d999-173">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
