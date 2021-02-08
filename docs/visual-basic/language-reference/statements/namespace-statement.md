---
description: Дополнительные сведения о инструкции Namespace
title: Оператор Namespace
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 2c315947a26f72a90e03bc1f4bf1b5f647866b33
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768861"
---
# <a name="namespace-statement"></a><span data-ttu-id="63fa6-103">Оператор Namespace</span><span class="sxs-lookup"><span data-stu-id="63fa6-103">Namespace Statement</span></span>

<span data-ttu-id="63fa6-104">Объявляет имя пространства имен и вызывает компиляцию исходного кода, следующего за объявлением, в пределах этого пространства имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-104">Declares the name of a namespace and causes the source code that follows the declaration to be compiled within that namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63fa6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="63fa6-105">Syntax</span></span>  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a><span data-ttu-id="63fa6-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="63fa6-106">Parts</span></span>  

 <span data-ttu-id="63fa6-107">Глобальный</span><span class="sxs-lookup"><span data-stu-id="63fa6-107">Global</span></span>  
 <span data-ttu-id="63fa6-108">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="63fa6-108">Optional.</span></span> <span data-ttu-id="63fa6-109">Позволяет определить пространство имен из корневого пространства имен проекта.</span><span class="sxs-lookup"><span data-stu-id="63fa6-109">Allows you to define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="63fa6-110">См. раздел [пространства имен в Visual Basic](../../programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="63fa6-110">See [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 `name`  
 <span data-ttu-id="63fa6-111">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="63fa6-111">Required.</span></span> <span data-ttu-id="63fa6-112">Уникальное имя, идентифицирующее пространство имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-112">A unique name that identifies the namespace.</span></span> <span data-ttu-id="63fa6-113">Должен быть допустимым идентификатором Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="63fa6-113">Must be a valid Visual Basic identifier.</span></span> <span data-ttu-id="63fa6-114">Дополнительные сведения см. в разделе [Имена объявленных элементов](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="63fa6-114">For more information, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `componenttypes`  
 <span data-ttu-id="63fa6-115">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="63fa6-115">Optional.</span></span> <span data-ttu-id="63fa6-116">Элементы, составляющие пространство имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-116">Elements that make up the namespace.</span></span> <span data-ttu-id="63fa6-117">К ним относятся, но не ограничиваются, перечисления, структуры, интерфейсы, классы, модули, делегаты и другие пространства имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-117">These include, but are not limited to, enumerations, structures, interfaces, classes, modules, delegates, and other namespaces.</span></span>  
  
 `End Namespace`  
 <span data-ttu-id="63fa6-118">Завершает `Namespace` блок.</span><span class="sxs-lookup"><span data-stu-id="63fa6-118">Terminates a `Namespace` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63fa6-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="63fa6-119">Remarks</span></span>  

 <span data-ttu-id="63fa6-120">Пространства имен используются в качестве организационной системы.</span><span class="sxs-lookup"><span data-stu-id="63fa6-120">Namespaces are used as an organizational system.</span></span> <span data-ttu-id="63fa6-121">Они предоставляют способ классификации и представления программных элементов, предоставляемых другим программам и приложениям.</span><span class="sxs-lookup"><span data-stu-id="63fa6-121">They provide a way to classify and present programming elements that are exposed to other programs and applications.</span></span> <span data-ttu-id="63fa6-122">Обратите внимание, что пространство имен не является *типом* в том смысле, что класс или структура — нельзя объявить элемент программирования для типа данных пространства имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-122">Note that a namespace is not a *type* in the sense that a class or structure is—you cannot declare a programming element to have the data type of a namespace.</span></span>  
  
 <span data-ttu-id="63fa6-123">Все программные элементы, объявленные после `Namespace` оператора, принадлежат к этому пространству имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-123">All programming elements declared after a `Namespace` statement belong to that namespace.</span></span> <span data-ttu-id="63fa6-124">Visual Basic будет продолжать компилировать элементы в последнее объявленное пространство имен до тех пор, пока не встретится `End Namespace` оператор или другая `Namespace` инструкция.</span><span class="sxs-lookup"><span data-stu-id="63fa6-124">Visual Basic continues to compile elements into the last declared namespace until it encounters either an `End Namespace` statement or another `Namespace` statement.</span></span>  
  
 <span data-ttu-id="63fa6-125">Если пространство имен уже определено, даже за пределами проекта, в него можно добавить программные элементы.</span><span class="sxs-lookup"><span data-stu-id="63fa6-125">If a namespace is already defined, even outside your project, you can add programming elements to it.</span></span> <span data-ttu-id="63fa6-126">Для этого используйте `Namespace` оператор, чтобы направить Visual Basic для компиляции элементов в это пространство имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-126">To do this, you use a `Namespace` statement to direct Visual Basic to compile elements into that namespace.</span></span>  
  
 <span data-ttu-id="63fa6-127">Инструкцию можно использовать `Namespace` только на уровне файла или пространства имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-127">You can use a `Namespace` statement only at the file or namespace level.</span></span> <span data-ttu-id="63fa6-128">Это означает, что *контекст объявления* для пространства имен должен быть исходным файлом или другим пространством имен и не может быть классом, структурой, модулем, интерфейсом или процедурой.</span><span class="sxs-lookup"><span data-stu-id="63fa6-128">This means the *declaration context* for a namespace must be a source file or another namespace, and cannot be a class, structure, module, interface, or procedure.</span></span> <span data-ttu-id="63fa6-129">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="63fa6-129">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="63fa6-130">Одно пространство имен можно объявить в другом.</span><span class="sxs-lookup"><span data-stu-id="63fa6-130">You can declare one namespace within another.</span></span> <span data-ttu-id="63fa6-131">Нет ограниченного ограничения уровней вложенности, которые можно объявить, но помните, что если другой код обращается к элементам, объявленным во внутреннем пространстве имен, он должен использовать уточняющую строку, содержащую все имена пространств имен в иерархии вложений.</span><span class="sxs-lookup"><span data-stu-id="63fa6-131">There is no strict limit to the levels of nesting you can declare, but remember that when other code accesses the elements declared in the innermost namespace, it must use a qualification string that contains all the namespace names in the nesting hierarchy.</span></span>  
  
## <a name="access-level"></a><span data-ttu-id="63fa6-132">Уровень доступа</span><span class="sxs-lookup"><span data-stu-id="63fa6-132">Access Level</span></span>  

 <span data-ttu-id="63fa6-133">Пространства имен обрабатываются так, как если бы они имели `Public` уровень доступа.</span><span class="sxs-lookup"><span data-stu-id="63fa6-133">Namespaces are treated as if they have a `Public` access level.</span></span> <span data-ttu-id="63fa6-134">К пространству имен можно обращаться из кода в любом месте в том же проекте, из других проектов, которые ссылаются на проект, и из любой сборки, построенной из проекта.</span><span class="sxs-lookup"><span data-stu-id="63fa6-134">A namespace can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project.</span></span>  
  
 <span data-ttu-id="63fa6-135">Элементы программирования, объявленные на уровне пространства имен, то есть в пространстве имен, но не внутри какого-либо другого элемента, могут иметь `Public` или иметь `Friend` доступ к.</span><span class="sxs-lookup"><span data-stu-id="63fa6-135">Programming elements declared at namespace level, meaning in a namespace but not inside any other element, can have `Public` or `Friend` access.</span></span> <span data-ttu-id="63fa6-136">Если этот параметр не указан, по умолчанию используется уровень доступа такого элемента `Friend` .</span><span class="sxs-lookup"><span data-stu-id="63fa6-136">If unspecified, the access level of such an element uses `Friend` by default.</span></span> <span data-ttu-id="63fa6-137">Элементы, которые можно объявить на уровне пространства имен, включают классы, структуры, модули, интерфейсы, перечисления и делегаты.</span><span class="sxs-lookup"><span data-stu-id="63fa6-137">Elements you can declare at namespace level include classes, structures, modules, interfaces, enumerations, and delegates.</span></span> <span data-ttu-id="63fa6-138">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="63fa6-138">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="root-namespace"></a><span data-ttu-id="63fa6-139">Корневое пространство имен</span><span class="sxs-lookup"><span data-stu-id="63fa6-139">Root Namespace</span></span>  

 <span data-ttu-id="63fa6-140">Все имена пространств имен в проекте основаны на *корневом пространстве имен*.</span><span class="sxs-lookup"><span data-stu-id="63fa6-140">All namespace names in your project are based on a *root namespace*.</span></span> <span data-ttu-id="63fa6-141">Visual Studio назначает имя проекта в качестве корневого пространства имен по умолчанию для всего кода в проекте.</span><span class="sxs-lookup"><span data-stu-id="63fa6-141">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="63fa6-142">Например, если проект называется `Payroll`, его программные элементы относятся к пространству имен `Payroll`.</span><span class="sxs-lookup"><span data-stu-id="63fa6-142">For example, if your project is named `Payroll`, its programming elements belong to namespace `Payroll`.</span></span> <span data-ttu-id="63fa6-143">При объявлении `Namespace funding` полное имя этого пространства имен имеет значение `Payroll.funding` .</span><span class="sxs-lookup"><span data-stu-id="63fa6-143">If you declare `Namespace funding`, the full name of that namespace is `Payroll.funding`.</span></span>  
  
 <span data-ttu-id="63fa6-144">Если вы хотите указать существующее пространство имен в `Namespace` инструкции, например в примере класса Generic List, можно задать для корневого пространства имен значение null.</span><span class="sxs-lookup"><span data-stu-id="63fa6-144">If you want to specify an existing namespace in a `Namespace` statement, such as in the generic list class example, you can set your root namespace to a null value.</span></span> <span data-ttu-id="63fa6-145">Для этого в меню **проект** выберите пункт **Свойства проекта** , а затем очистите запись **корневого пространства имен** , чтобы поле было пустым.</span><span class="sxs-lookup"><span data-stu-id="63fa6-145">To do this, click **Project Properties** from the **Project** menu and then clear the **Root namespace** entry so that the box is empty.</span></span> <span data-ttu-id="63fa6-146">Если это не было сделано в примере класса Generic List, то компилятор Visual Basic будет использовать в `System.Collections.Generic` проекте новое пространство имен `Payroll` с полным именем `Payroll.System.Collections.Generic` .</span><span class="sxs-lookup"><span data-stu-id="63fa6-146">If you did not do this in the generic list class example, the Visual Basic compiler would take `System.Collections.Generic` as a new namespace within project `Payroll`, with the full name of `Payroll.System.Collections.Generic`.</span></span>  
  
 <span data-ttu-id="63fa6-147">Кроме того, можно использовать `Global` ключевое слово для ссылки на элементы пространств имен, определенные за пределами проекта.</span><span class="sxs-lookup"><span data-stu-id="63fa6-147">Alternatively, you can use the `Global` keyword to refer to elements of namespaces defined outside your project.</span></span> <span data-ttu-id="63fa6-148">Это позволит хранить имя проекта в качестве корневого пространства имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-148">Doing so lets you retain your project name as the root namespace.</span></span> <span data-ttu-id="63fa6-149">Это снижает вероятность непреднамеренного слияния программных элементов вместе с существующими пространствами имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-149">This reduces the chance of unintentionally merging your programming elements together with those of existing namespaces.</span></span> <span data-ttu-id="63fa6-150">Дополнительные сведения см. в разделе "глобальное ключевое слово в полных именах" раздела [пространства имен в Visual Basic](../../programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="63fa6-150">For more information, see the "Global Keyword in Fully Qualified Names" section in [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="63fa6-151">`Global`Ключевое слово также можно использовать в операторе Namespace.</span><span class="sxs-lookup"><span data-stu-id="63fa6-151">The `Global` keyword can also be used in a Namespace statement.</span></span> <span data-ttu-id="63fa6-152">Это позволяет определить пространство имен из корневых пространств имен проекта.</span><span class="sxs-lookup"><span data-stu-id="63fa6-152">This lets you define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="63fa6-153">Дополнительные сведения см. в подразделе «глобальное ключевое слово в операторах пространства имен» раздела [пространства имен в Visual Basic](../../programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="63fa6-153">For more information, see the "Global Keyword in Namespace Statements" section in [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="63fa6-154">**Выявлен.**</span><span class="sxs-lookup"><span data-stu-id="63fa6-154">**Troubleshooting.**</span></span> <span data-ttu-id="63fa6-155">Корневое пространство имен может привести к непредвиденному объединению имен пространств имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-155">The root namespace can lead to unexpected concatenations of namespace names.</span></span> <span data-ttu-id="63fa6-156">Если вы задаете ссылку на пространства имен, определенные за пределами проекта, Visual Basic компилятор может конструе их как вложенные пространства имен в корневом пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-156">If you make reference to namespaces defined outside your project, the Visual Basic compiler can construe them as nested namespaces in the root namespace.</span></span> <span data-ttu-id="63fa6-157">В этом случае компилятор не распознает типы, которые уже были определены во внешних пространствах имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-157">In such a case, the compiler does not recognize any types that have been already defined in the external namespaces.</span></span> <span data-ttu-id="63fa6-158">Чтобы избежать этого, следует либо присвоить корневому пространству имен значение null, как описано в разделе "корневое пространство имен", либо использовать `Global` ключевое слово для доступа к элементам внешних пространств имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-158">To avoid this, either set your root namespace to a null value as described in "Root Namespace," or use the `Global` keyword to access elements of external namespaces.</span></span>  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="63fa6-159">Атрибуты и модификаторы</span><span class="sxs-lookup"><span data-stu-id="63fa6-159">Attributes and Modifiers</span></span>  

 <span data-ttu-id="63fa6-160">К пространству имен нельзя применять атрибуты.</span><span class="sxs-lookup"><span data-stu-id="63fa6-160">You cannot apply attributes to a namespace.</span></span> <span data-ttu-id="63fa6-161">Атрибут вносит сведения в метаданные сборки, которые не имеют смысла для исходных классификаторов, таких как пространства имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-161">An attribute contributes information to the assembly's metadata, which is not meaningful for source classifiers such as namespaces.</span></span>  
  
 <span data-ttu-id="63fa6-162">К пространству имен нельзя применять модификаторы доступа и процедур, а также любые другие модификаторы.</span><span class="sxs-lookup"><span data-stu-id="63fa6-162">You cannot apply any access or procedure modifiers, or any other modifiers, to a namespace.</span></span> <span data-ttu-id="63fa6-163">Поскольку это не тип, эти модификаторы не имеют смысла.</span><span class="sxs-lookup"><span data-stu-id="63fa6-163">Because it is not a type, these modifiers are not meaningful.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63fa6-164">Пример</span><span class="sxs-lookup"><span data-stu-id="63fa6-164">Example</span></span>  

 <span data-ttu-id="63fa6-165">В следующем примере объявляются два пространства имен, одно из которых вложено в другое.</span><span class="sxs-lookup"><span data-stu-id="63fa6-165">The following example declares two namespaces, one nested in the other.</span></span>  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a><span data-ttu-id="63fa6-166">Пример</span><span class="sxs-lookup"><span data-stu-id="63fa6-166">Example</span></span>  

 <span data-ttu-id="63fa6-167">В следующем примере несколько вложенных пространств имен объявляются в одной строке и эквивалентны предыдущему примеру.</span><span class="sxs-lookup"><span data-stu-id="63fa6-167">The following example declares multiple nested namespaces on a single line, and it is equivalent to the previous example.</span></span>  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="63fa6-168">Пример</span><span class="sxs-lookup"><span data-stu-id="63fa6-168">Example</span></span>  

 <span data-ttu-id="63fa6-169">В следующем примере осуществляется доступ к классу, определенному в предыдущих примерах.</span><span class="sxs-lookup"><span data-stu-id="63fa6-169">The following example accesses the class defined in the previous examples.</span></span>  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a><span data-ttu-id="63fa6-170">Пример</span><span class="sxs-lookup"><span data-stu-id="63fa6-170">Example</span></span>  

 <span data-ttu-id="63fa6-171">В следующем примере определяется скелет нового класса универсального списка и добавляется в <xref:System.Collections.Generic?displayProperty=nameWithType> пространство имен.</span><span class="sxs-lookup"><span data-stu-id="63fa6-171">The following example defines the skeleton of a new generic list class and adds it to the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="63fa6-172">См. также</span><span class="sxs-lookup"><span data-stu-id="63fa6-172">See also</span></span>

- [<span data-ttu-id="63fa6-173">Оператор Imports (пространство имен .NET и тип)</span><span class="sxs-lookup"><span data-stu-id="63fa6-173">Imports Statement (.NET Namespace and Type)</span></span>](imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="63fa6-174">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="63fa6-174">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="63fa6-175">Пространства имен в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63fa6-175">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
