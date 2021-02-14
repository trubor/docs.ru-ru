---
description: Дополнительные сведения о пространствах имен см. в Visual Basic
title: Пространства имен
ms.date: 07/20/2015
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
ms.openlocfilehash: 2f7c0bfd29bf6fe104252aa125b4ddff1259b50a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460752"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="9024e-103">Пространства имен в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9024e-103">Namespaces in Visual Basic</span></span>

<span data-ttu-id="9024e-104">Пространства имен упорядочивают объекты, определенные в сборке.</span><span class="sxs-lookup"><span data-stu-id="9024e-104">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="9024e-105">Сборки могут содержать несколько пространств имен, которые, в свою очередь, могут содержать другие пространства имен.</span><span class="sxs-lookup"><span data-stu-id="9024e-105">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="9024e-106">Пространства имен предотвращают неоднозначность и упрощают ссылки при использовании больших групп объектов, таких как библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="9024e-106">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="9024e-107">Например, платформа .NET Framework определяет <xref:System.Windows.Forms.ListBox> класс в <xref:System.Windows.Forms?displayProperty=nameWithType> пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="9024e-107">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="9024e-108">В следующем фрагменте кода показано, как объявить переменную, используя полное имя для этого класса:</span><span class="sxs-lookup"><span data-stu-id="9024e-108">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="9024e-109">Предотвращение конфликтов имен</span><span class="sxs-lookup"><span data-stu-id="9024e-109">Avoiding Name Collisions</span></span>  

 <span data-ttu-id="9024e-110">Платформа .NET Framework пространства имен устраняют проблему, которая иногда называется *засорением пространства имен*, при которой разработчик библиотеки классов страдает от использования аналогичных имен в другой библиотеке.</span><span class="sxs-lookup"><span data-stu-id="9024e-110">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="9024e-111">Такие конфликты с существующими компонентами иногда называют *конфликтами имен*.</span><span class="sxs-lookup"><span data-stu-id="9024e-111">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="9024e-112">Например, если вы создаете новый класс `ListBox`, то можете использовать его внутри проекта без уточнения.</span><span class="sxs-lookup"><span data-stu-id="9024e-112">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="9024e-113">Однако если вы хотите использовать <xref:System.Windows.Forms.ListBox> класс платформа .NET Framework в том же проекте, необходимо использовать полную ссылку, чтобы сделать ссылку уникальной.</span><span class="sxs-lookup"><span data-stu-id="9024e-113">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="9024e-114">Если ссылка не является уникальной, Visual Basic выдает ошибку, сообщающую, что имя неоднозначно.</span><span class="sxs-lookup"><span data-stu-id="9024e-114">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="9024e-115">В примере кода ниже показано, как объявить эти объекты:</span><span class="sxs-lookup"><span data-stu-id="9024e-115">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 <span data-ttu-id="9024e-116">На следующем рисунке показаны две иерархии пространства имен, содержащие объект с именем `ListBox` :</span><span class="sxs-lookup"><span data-stu-id="9024e-116">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span></span>  
  
 ![Снимок экрана, на котором показаны две иерархии пространств имен.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 <span data-ttu-id="9024e-118">По умолчанию каждый исполняемый файл, созданный с помощью Visual Basic, содержит пространство имен с тем же именем, что и у проекта.</span><span class="sxs-lookup"><span data-stu-id="9024e-118">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="9024e-119">Например, если вы определяете объект в проекте `ListBoxProject`, то исполняемый файл ListBoxProject.exe содержит пространство имен `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="9024e-119">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="9024e-120">Несколько сборок могут использовать одно и то же пространство имен.</span><span class="sxs-lookup"><span data-stu-id="9024e-120">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="9024e-121">Visual Basic обрабатывает их как единый набор имен.</span><span class="sxs-lookup"><span data-stu-id="9024e-121">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="9024e-122">Например, можно определить классы для пространства имен `SomeNameSpace` в сборке `Assemb1`, а также определить дополнительные классы для того же пространства имен из сборки `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="9024e-122">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="9024e-123">полные имена</span><span class="sxs-lookup"><span data-stu-id="9024e-123">Fully Qualified Names</span></span>  

 <span data-ttu-id="9024e-124">Полные имена — это ссылки на объекты, имеющие префикс в виде имени пространства имен, в котором определен объект.</span><span class="sxs-lookup"><span data-stu-id="9024e-124">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="9024e-125">Вы можете использовать объекты, определенные в других проектах, если создадите ссылку на класс (выбрав **Добавить ссылку** в меню **Проект** ) и затем используете полное имя объекта в коде.</span><span class="sxs-lookup"><span data-stu-id="9024e-125">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="9024e-126">В следующем фрагменте кода показано, как использовать полное имя объекта из пространства имен другого проекта:</span><span class="sxs-lookup"><span data-stu-id="9024e-126">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 <span data-ttu-id="9024e-127">Полные имена предотвращают возникновение конфликтов имен, так как позволяют компилятору определить, какой именно объект используется.</span><span class="sxs-lookup"><span data-stu-id="9024e-127">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="9024e-128">Однако сами эти имена могут получиться длинными и громоздкими.</span><span class="sxs-lookup"><span data-stu-id="9024e-128">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="9024e-129">Чтобы обойти эту проблему, можно использовать оператор `Imports` для определения *псевдонима*— сокращенного имени, которое можно применить вместо полного имени.</span><span class="sxs-lookup"><span data-stu-id="9024e-129">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="9024e-130">Например, в следующем примере кода создаются псевдонимы для двух полных имен, которые затем используются для определения двух объектов.</span><span class="sxs-lookup"><span data-stu-id="9024e-130">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 <span data-ttu-id="9024e-131">Если вы применяете оператор `Imports` без псевдонима, можно использовать все имена в данном пространстве имен без уточнения при условии, что они являются уникальными в данном проекте.</span><span class="sxs-lookup"><span data-stu-id="9024e-131">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="9024e-132">Если проект содержит операторы `Imports` для пространств имен, где есть элементы с одинаковым именем, необходимо полностью уточнять это имя.</span><span class="sxs-lookup"><span data-stu-id="9024e-132">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="9024e-133">Предположим, что проект содержал два следующих оператора `Imports` :</span><span class="sxs-lookup"><span data-stu-id="9024e-133">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 <span data-ttu-id="9024e-134">При попытке использовать `Class1` без полного указания этого имени Visual Basic выдает ошибку, сообщающую, что имя `Class1` неоднозначно.</span><span class="sxs-lookup"><span data-stu-id="9024e-134">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="9024e-135">Операторы уровня пространства имен</span><span class="sxs-lookup"><span data-stu-id="9024e-135">Namespace Level Statements</span></span>  

 <span data-ttu-id="9024e-136">В пространстве имен можно определить такие элементы, как модули, интерфейсы, классы, делегаты, перечисления, структуры и другие пространства имен.</span><span class="sxs-lookup"><span data-stu-id="9024e-136">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="9024e-137">Вы не можете определить такие элементы, как свойства, процедуры, переменные и события, на уровне пространства имен.</span><span class="sxs-lookup"><span data-stu-id="9024e-137">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="9024e-138">Их следует объявить внутри контейнеров, таких как модули, структуры или классы.</span><span class="sxs-lookup"><span data-stu-id="9024e-138">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="9024e-139">Ключевое слово Global в полных именах</span><span class="sxs-lookup"><span data-stu-id="9024e-139">Global Keyword in Fully Qualified Names</span></span>  

 <span data-ttu-id="9024e-140">Если вы определили вложенную иерархию пространств имен, доступ кода внутри этой иерархии к пространству имен <xref:System?displayProperty=nameWithType> платформы .NET Framework может быть заблокирован.</span><span class="sxs-lookup"><span data-stu-id="9024e-140">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="9024e-141">В следующем примере показана иерархия, где пространство имен `SpecialSpace.System` блокирует доступ к <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9024e-141">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="9024e-142">В результате компилятору Visual Basic не удается разрешить успешно ссылку в <xref:System.Int32?displayProperty=nameWithType>, так как `SpecialSpace.System` не определяет `Int32`.</span><span class="sxs-lookup"><span data-stu-id="9024e-142">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="9024e-143">Можно использовать ключевое слово `Global` для запуска цепочки квалификации на самом внешнем уровне библиотеки классов .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9024e-143">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="9024e-144">Это позволяет указать пространство имен <xref:System?displayProperty=nameWithType> или любое другое пространство имен в библиотеке классов.</span><span class="sxs-lookup"><span data-stu-id="9024e-144">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="9024e-145">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="9024e-145">The following example illustrates this.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="9024e-146">Можно использовать `Global` для доступа к другим пространствам имен корневого уровня, таким как <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, и любому пространству имен, сопоставленному с проектом.</span><span class="sxs-lookup"><span data-stu-id="9024e-146">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="9024e-147">Ключевое слово Global в операторах пространства имен</span><span class="sxs-lookup"><span data-stu-id="9024e-147">Global Keyword in Namespace Statements</span></span>  

 <span data-ttu-id="9024e-148">Можно также использовать ключевое слово `Global` в [Namespace Statement](../../language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9024e-148">You can also use the `Global` keyword in a [Namespace Statement](../../language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="9024e-149">Это позволяет определить пространство имен из корневых пространств имен проекта.</span><span class="sxs-lookup"><span data-stu-id="9024e-149">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="9024e-150">Все пространства имен в проекте основаны на его корневом пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="9024e-150">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="9024e-151">Visual Studio назначает имя проекта в качестве корневого пространства имен по умолчанию для всего кода в проекте.</span><span class="sxs-lookup"><span data-stu-id="9024e-151">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="9024e-152">Например, если проект называется `ConsoleApplication1`, его программные элементы относятся к пространству имен `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="9024e-152">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="9024e-153">При объявлении `Namespace Magnetosphere`ссылки на `Magnetosphere` в проекте будут обращаться к `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="9024e-153">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="9024e-154">В следующих примерах используется ключевое слово `Global` для объявления пространства имен из корневого пространства имен для проекта.</span><span class="sxs-lookup"><span data-stu-id="9024e-154">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 <span data-ttu-id="9024e-155">В объявлении пространства имен `Global` не может быть вложенным в другое пространство имен.</span><span class="sxs-lookup"><span data-stu-id="9024e-155">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="9024e-156">Вы можете использовать [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) для просмотра и изменения значения **Корневое пространство имен** проекта.</span><span class="sxs-lookup"><span data-stu-id="9024e-156">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="9024e-157">Для новых проектов параметру **Корневое пространство имен** по умолчанию присваивается имя проекта.</span><span class="sxs-lookup"><span data-stu-id="9024e-157">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="9024e-158">Чтобы сделать `Global` пространством имен верхнего уровня, можно очистить запись **Корневое пространство имен** , оставив поле пустым.</span><span class="sxs-lookup"><span data-stu-id="9024e-158">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="9024e-159">Очистка значения **Корневое пространство имен** избавляет от необходимости использовать ключевое слово `Global` в объявлениях пространств имен.</span><span class="sxs-lookup"><span data-stu-id="9024e-159">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="9024e-160">Когда оператор `Namespace` объявляет имя, которое также является пространством имен в платформе .NET Framework, пространство имен .NET Framework станет недоступным, если в полном имени не используется ключевое слово `Global` .</span><span class="sxs-lookup"><span data-stu-id="9024e-160">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="9024e-161">Для обеспечения доступа к пространству имен .NET Framework без использования ключевого слова `Global` можно включить ключевое слово `Global` в оператор `Namespace` .</span><span class="sxs-lookup"><span data-stu-id="9024e-161">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="9024e-162">В следующем примере ключевое слово `Global` присутствует в объявлении пространства имен `System.Text` .</span><span class="sxs-lookup"><span data-stu-id="9024e-162">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="9024e-163">Если ключевое слово `Global` отсутствует в объявлении пространства имен, к <xref:System.Text.StringBuilder> нельзя обратиться без указания `Global.System.Text.StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="9024e-163">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="9024e-164">Если ключевое слово `ConsoleApplication1`не использовалось, для проекта с именем `System.Text` ссылки на `ConsoleApplication1.System.Text` обращаются к `Global` .</span><span class="sxs-lookup"><span data-stu-id="9024e-164">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="9024e-165">См. также</span><span class="sxs-lookup"><span data-stu-id="9024e-165">See also</span></span>

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [<span data-ttu-id="9024e-166">Сборки в .NET</span><span class="sxs-lookup"><span data-stu-id="9024e-166">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="9024e-167">Ссылки и оператор Imports</span><span class="sxs-lookup"><span data-stu-id="9024e-167">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)
- [<span data-ttu-id="9024e-168">Оператор Imports (пространство имен .NET и тип)</span><span class="sxs-lookup"><span data-stu-id="9024e-168">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="9024e-169">Написание кода в решениях Office</span><span class="sxs-lookup"><span data-stu-id="9024e-169">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
