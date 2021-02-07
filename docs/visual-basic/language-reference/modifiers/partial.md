---
description: 'Дополнительные сведения о: partial (Visual Basic)'
title: Частично
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: bf2d8b06b83f4a90ec2f4edd52405b58695c26e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701018"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="8eb35-103">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8eb35-103">Partial (Visual Basic)</span></span>

<span data-ttu-id="8eb35-104">Указывает, что объявление типа — это частичное определение типа.</span><span class="sxs-lookup"><span data-stu-id="8eb35-104">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="8eb35-105">Вы можете разделить определение типа среди нескольких объявлений, используя ключевое слово `Partial`.</span><span class="sxs-lookup"><span data-stu-id="8eb35-105">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="8eb35-106">Можно использовать столько частичных объявлений, сколько необходимо, во множестве исходных файлах.</span><span class="sxs-lookup"><span data-stu-id="8eb35-106">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="8eb35-107">Однако все объявления должны находиться в одной сборке и одном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="8eb35-107">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8eb35-108">Visual Basic поддерживает *разделяемые методы*, которые обычно реализуются в разделяемых классах.</span><span class="sxs-lookup"><span data-stu-id="8eb35-108">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="8eb35-109">Дополнительные сведения см. в разделе [разделяемые методы](../../programming-guide/language-features/procedures/partial-methods.md) и [подоператоры](../statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8eb35-109">For more information, see [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb35-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8eb35-110">Syntax</span></span>  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="8eb35-111">Компоненты</span><span class="sxs-lookup"><span data-stu-id="8eb35-111">Parts</span></span>  
  
|<span data-ttu-id="8eb35-112">Термин</span><span class="sxs-lookup"><span data-stu-id="8eb35-112">Term</span></span>|<span data-ttu-id="8eb35-113">Определение</span><span class="sxs-lookup"><span data-stu-id="8eb35-113">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="8eb35-114">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8eb35-114">Optional.</span></span> <span data-ttu-id="8eb35-115">Список атрибутов, применяемых к этому событию.</span><span class="sxs-lookup"><span data-stu-id="8eb35-115">List of attributes that apply to this type.</span></span> <span data-ttu-id="8eb35-116">[Список атрибутов](../statements/attribute-list.md) необходимо заключить в угловые скобки ( `< >` ).</span><span class="sxs-lookup"><span data-stu-id="8eb35-116">You must enclose the [Attribute List](../statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="8eb35-117">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8eb35-117">Optional.</span></span> <span data-ttu-id="8eb35-118">Указывает, какой код может получить доступ к этому событию.</span><span class="sxs-lookup"><span data-stu-id="8eb35-118">Specifies what code can access this type.</span></span> <span data-ttu-id="8eb35-119">См. раздел [уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8eb35-119">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="8eb35-120">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8eb35-120">Optional.</span></span> <span data-ttu-id="8eb35-121">См. раздел [Shadows](shadows.md).</span><span class="sxs-lookup"><span data-stu-id="8eb35-121">See [Shadows](shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="8eb35-122">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8eb35-122">Optional.</span></span> <span data-ttu-id="8eb35-123">См. раздел [MustInherit](mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="8eb35-123">See [MustInherit](mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="8eb35-124">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8eb35-124">Optional.</span></span> <span data-ttu-id="8eb35-125">См. [NotInheritable](notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="8eb35-125">See [NotInheritable](notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="8eb35-126">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8eb35-126">Required.</span></span> <span data-ttu-id="8eb35-127">Имя данного типа.</span><span class="sxs-lookup"><span data-stu-id="8eb35-127">Name of this type.</span></span> <span data-ttu-id="8eb35-128">Оно должно соответствовать имени, определенному в других частичных объявлениях того же типа.</span><span class="sxs-lookup"><span data-stu-id="8eb35-128">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="8eb35-129">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8eb35-129">Optional.</span></span> <span data-ttu-id="8eb35-130">Указывает, что это универсальный тип.</span><span class="sxs-lookup"><span data-stu-id="8eb35-130">Specifies that this is a generic type.</span></span> <span data-ttu-id="8eb35-131">См. раздел [универсальные типы в Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="8eb35-131">See [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="8eb35-132">Требуется [, если используется.](../statements/of-clause.md)</span><span class="sxs-lookup"><span data-stu-id="8eb35-132">Required if you use [Of](../statements/of-clause.md).</span></span> <span data-ttu-id="8eb35-133">См. [список типов](../statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="8eb35-133">See [Type List](../statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="8eb35-134">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8eb35-134">Optional.</span></span> <span data-ttu-id="8eb35-135">См. раздел [оператор Inherits](../statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8eb35-135">See [Inherits Statement](../statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="8eb35-136">Обязательный параметр, если используется параметр `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="8eb35-136">Required if you use `Inherits`.</span></span> <span data-ttu-id="8eb35-137">Имя класса или интерфейса, от которого наследует этот класс.</span><span class="sxs-lookup"><span data-stu-id="8eb35-137">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="8eb35-138">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8eb35-138">Optional.</span></span> <span data-ttu-id="8eb35-139">См. [инструкцию Implements](../statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8eb35-139">See [Implements Statement](../statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="8eb35-140">Обязательный параметр, если используется параметр `Implements`.</span><span class="sxs-lookup"><span data-stu-id="8eb35-140">Required if you use `Implements`.</span></span> <span data-ttu-id="8eb35-141">Имена интерфейсов, реализуемых этим типом.</span><span class="sxs-lookup"><span data-stu-id="8eb35-141">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="8eb35-142">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8eb35-142">Optional.</span></span> <span data-ttu-id="8eb35-143">Операторы, которые объявляют дополнительные переменные и события для типа.</span><span class="sxs-lookup"><span data-stu-id="8eb35-143">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="8eb35-144">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8eb35-144">Optional.</span></span> <span data-ttu-id="8eb35-145">Операторы, которые объявляют и определяют дополнительные процедуры для типа.</span><span class="sxs-lookup"><span data-stu-id="8eb35-145">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="8eb35-146">`End Class` либо `End Structure`</span><span class="sxs-lookup"><span data-stu-id="8eb35-146">`End Class` or `End Structure`</span></span>|<span data-ttu-id="8eb35-147">Завершает этот частичное определение `Class` или `Structure`.</span><span class="sxs-lookup"><span data-stu-id="8eb35-147">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8eb35-148">Remarks</span><span class="sxs-lookup"><span data-stu-id="8eb35-148">Remarks</span></span>  

 <span data-ttu-id="8eb35-149">Visual Basic использует разделяемые определения класса для разделения автоматически созданного кода и пользовательского кода в по отдельным файлам исходного кода.</span><span class="sxs-lookup"><span data-stu-id="8eb35-149">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="8eb35-150">Например, **конструктор форм Windows Forms** определяет разделяемые классы для элементов управления, таких как <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="8eb35-150">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="8eb35-151">Не следует изменять код, созданный в этих элементах управления.</span><span class="sxs-lookup"><span data-stu-id="8eb35-151">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="8eb35-152">Все правила для создания класса, структуры, интерфейса и модуля, например для использования модификатора и наследования, применяются при создании частичного типа.</span><span class="sxs-lookup"><span data-stu-id="8eb35-152">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="8eb35-153">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8eb35-153">Best Practices</span></span>  
  
- <span data-ttu-id="8eb35-154">В обычных условиях не следует разбивать один тип на два или более объявлений.</span><span class="sxs-lookup"><span data-stu-id="8eb35-154">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="8eb35-155">Поэтому в большинстве случаев ключевое `Partial` слово не требуется.</span><span class="sxs-lookup"><span data-stu-id="8eb35-155">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="8eb35-156">Для удобочитаемости каждое частичное объявление типа должно включать ключевое слово `Partial`.</span><span class="sxs-lookup"><span data-stu-id="8eb35-156">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="8eb35-157">Компилятор позволяет пропускать ключевое слово только в одном частичном объявлении. Если это происходит в двух или более объявлениях, компилятор сообщает об ошибке.</span><span class="sxs-lookup"><span data-stu-id="8eb35-157">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="8eb35-158">Поведение</span><span class="sxs-lookup"><span data-stu-id="8eb35-158">Behavior</span></span>  
  
- <span data-ttu-id="8eb35-159">**Объявления объединений.**</span><span class="sxs-lookup"><span data-stu-id="8eb35-159">**Union of Declarations.**</span></span> <span data-ttu-id="8eb35-160">Компилятор рассматривает тип как объединение всех его частичных объявлений.</span><span class="sxs-lookup"><span data-stu-id="8eb35-160">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="8eb35-161">Каждый модификатор из каждого частичного определения применяется ко всему типу, а каждый элемент из каждого частичного определения доступен для всего типа.</span><span class="sxs-lookup"><span data-stu-id="8eb35-161">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="8eb35-162">**Повышение типа не допускается для частичных типов в модулях.**</span><span class="sxs-lookup"><span data-stu-id="8eb35-162">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="8eb35-163">Если частичное определение находится внутри модуля, повышение типа этого типа автоматически отменяется.</span><span class="sxs-lookup"><span data-stu-id="8eb35-163">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="8eb35-164">В таком случае набор частичных определений может привести к непредсказуемым результатам и даже ошибкам компилятора.</span><span class="sxs-lookup"><span data-stu-id="8eb35-164">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="8eb35-165">Дополнительные сведения см. в разделе [повышение типа](../../programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="8eb35-165">For more information, see [Type Promotion](../../programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="8eb35-166">Компилятор объединяет частичные определения, только если их полные пути идентичны.</span><span class="sxs-lookup"><span data-stu-id="8eb35-166">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="8eb35-167">Ключевое слово `Partial` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="8eb35-167">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="8eb35-168">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="8eb35-168">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="8eb35-169">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="8eb35-169">Structure Statement</span></span>](../statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="8eb35-170">Пример</span><span class="sxs-lookup"><span data-stu-id="8eb35-170">Example</span></span>  

 <span data-ttu-id="8eb35-171">Следующий пример разделяет определение класса `sampleClass` на два объявления, в каждом из которых определяется отдельная процедура `Sub`.</span><span class="sxs-lookup"><span data-stu-id="8eb35-171">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="8eb35-172">Два частичных определения в предыдущем примере могут находиться в одном или двух исходных файлах.</span><span class="sxs-lookup"><span data-stu-id="8eb35-172">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb35-173">См. также</span><span class="sxs-lookup"><span data-stu-id="8eb35-173">See also</span></span>

- [<span data-ttu-id="8eb35-174">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="8eb35-174">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="8eb35-175">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="8eb35-175">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="8eb35-176">Повышение типа</span><span class="sxs-lookup"><span data-stu-id="8eb35-176">Type Promotion</span></span>](../../programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="8eb35-177">Shadows</span><span class="sxs-lookup"><span data-stu-id="8eb35-177">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="8eb35-178">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8eb35-178">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="8eb35-179">Разделяемые методы</span><span class="sxs-lookup"><span data-stu-id="8eb35-179">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
