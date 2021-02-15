---
description: 'Дополнительные сведения о: SCOPE в Visual Basic'
title: Область
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 5b5412f5743162bb91fc3651d08f5c7ff9ba8abd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480210"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="2b35e-103">Область видимости в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b35e-103">Scope in Visual Basic</span></span>

<span data-ttu-id="2b35e-104">*Областью видимости* объявленного элемента является набор всего кода, который может ссылаться на него без уточнения его имени или предоставления доступа с помощью [оператора Imports (пространство имен .NET и тип)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="2b35e-104">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="2b35e-105">Элемент может иметь область действия на одном из следующих уровней:</span><span class="sxs-lookup"><span data-stu-id="2b35e-105">An element can have scope at one of the following levels:</span></span>

|<span data-ttu-id="2b35e-106">Level</span><span class="sxs-lookup"><span data-stu-id="2b35e-106">Level</span></span>|<span data-ttu-id="2b35e-107">Описание</span><span class="sxs-lookup"><span data-stu-id="2b35e-107">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="2b35e-108">Область действия блока</span><span class="sxs-lookup"><span data-stu-id="2b35e-108">Block scope</span></span>|<span data-ttu-id="2b35e-109">Доступно только в блоке кода, в котором он объявлен</span><span class="sxs-lookup"><span data-stu-id="2b35e-109">Available only within the code block in which it is declared</span></span>|
|<span data-ttu-id="2b35e-110">Область действия процедуры</span><span class="sxs-lookup"><span data-stu-id="2b35e-110">Procedure scope</span></span>|<span data-ttu-id="2b35e-111">Доступен для всего кода в процедуре, в которой он объявлен</span><span class="sxs-lookup"><span data-stu-id="2b35e-111">Available to all code within the procedure in which it is declared</span></span>|
|<span data-ttu-id="2b35e-112">Область модуля</span><span class="sxs-lookup"><span data-stu-id="2b35e-112">Module scope</span></span>|<span data-ttu-id="2b35e-113">Доступен для всего кода в модуле, классе или структуре, в которой он объявлен</span><span class="sxs-lookup"><span data-stu-id="2b35e-113">Available to all code within the module, class, or structure in which it is declared</span></span>|
|<span data-ttu-id="2b35e-114">Область пространства имен</span><span class="sxs-lookup"><span data-stu-id="2b35e-114">Namespace scope</span></span>|<span data-ttu-id="2b35e-115">Доступен для всего кода в пространстве имен, в котором оно объявлено</span><span class="sxs-lookup"><span data-stu-id="2b35e-115">Available to all code in the namespace in which it is declared</span></span>|

<span data-ttu-id="2b35e-116">Эти уровни области выполняются от самого узкого (блока) до самого широкого (пространства имен), где *самая узкие области* означает наименьший набор кода, который может ссылаться на элемент без квалификации.</span><span class="sxs-lookup"><span data-stu-id="2b35e-116">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="2b35e-117">Дополнительные сведения см. в разделе уровни области на этой странице.</span><span class="sxs-lookup"><span data-stu-id="2b35e-117">For more information, see "Levels of Scope" on this page.</span></span>

## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="2b35e-118">Указание области и определение переменных</span><span class="sxs-lookup"><span data-stu-id="2b35e-118">Specifying Scope and Defining Variables</span></span>

<span data-ttu-id="2b35e-119">Вы указываете область элемента при его объявлении.</span><span class="sxs-lookup"><span data-stu-id="2b35e-119">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="2b35e-120">Область может зависеть от следующих факторов:</span><span class="sxs-lookup"><span data-stu-id="2b35e-120">The scope can depend on the following factors:</span></span>

- <span data-ttu-id="2b35e-121">Область (блок, процедура, модуль, класс или структура), в которой объявляется элемент</span><span class="sxs-lookup"><span data-stu-id="2b35e-121">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>

- <span data-ttu-id="2b35e-122">Пространство имен, содержащее объявление элемента</span><span class="sxs-lookup"><span data-stu-id="2b35e-122">The namespace containing the element's declaration</span></span>

- <span data-ttu-id="2b35e-123">Уровень доступа, объявленный для элемента</span><span class="sxs-lookup"><span data-stu-id="2b35e-123">The access level you declare for the element</span></span>

<span data-ttu-id="2b35e-124">Используйте осторожность при определении переменных с одинаковым именем, но с разными областями, так как это может привести к непредвиденным результатам.</span><span class="sxs-lookup"><span data-stu-id="2b35e-124">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="2b35e-125">Для получения дополнительной информации см. [References to Declared Elements](references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="2b35e-125">For more information, see [References to Declared Elements](references-to-declared-elements.md).</span></span>

## <a name="levels-of-scope"></a><span data-ttu-id="2b35e-126">Уровни области</span><span class="sxs-lookup"><span data-stu-id="2b35e-126">Levels of Scope</span></span>

<span data-ttu-id="2b35e-127">Программный элемент доступен по всему региону, в котором он объявлен.</span><span class="sxs-lookup"><span data-stu-id="2b35e-127">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="2b35e-128">Весь код в одном регионе может ссылаться на элемент без уточнения его имени.</span><span class="sxs-lookup"><span data-stu-id="2b35e-128">All code in the same region can refer to the element without qualifying its name.</span></span>

### <a name="block-scope"></a><span data-ttu-id="2b35e-129">Область блока</span><span class="sxs-lookup"><span data-stu-id="2b35e-129">Block Scope</span></span>

<span data-ttu-id="2b35e-130">Блок — это набор инструкций, заключенных в операторы инициирования и завершения объявления, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="2b35e-130">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>

- <span data-ttu-id="2b35e-131">`Do` и `Loop`</span><span class="sxs-lookup"><span data-stu-id="2b35e-131">`Do` and `Loop`</span></span>

- <span data-ttu-id="2b35e-132">`For` [ `Each` ] и `Next`</span><span class="sxs-lookup"><span data-stu-id="2b35e-132">`For` [`Each`] and `Next`</span></span>

- <span data-ttu-id="2b35e-133">`If` и `End If`</span><span class="sxs-lookup"><span data-stu-id="2b35e-133">`If` and `End If`</span></span>

- <span data-ttu-id="2b35e-134">`Select` и `End Select`</span><span class="sxs-lookup"><span data-stu-id="2b35e-134">`Select` and `End Select`</span></span>

- <span data-ttu-id="2b35e-135">`SyncLock` и `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="2b35e-135">`SyncLock` and `End SyncLock`</span></span>

- <span data-ttu-id="2b35e-136">`Try` и `End Try`</span><span class="sxs-lookup"><span data-stu-id="2b35e-136">`Try` and `End Try`</span></span>

- <span data-ttu-id="2b35e-137">`While` и `End While`</span><span class="sxs-lookup"><span data-stu-id="2b35e-137">`While` and `End While`</span></span>

- <span data-ttu-id="2b35e-138">`With` и `End With`</span><span class="sxs-lookup"><span data-stu-id="2b35e-138">`With` and `End With`</span></span>

<span data-ttu-id="2b35e-139">Если переменная объявлена в блоке, ее можно использовать только в пределах этого блока.</span><span class="sxs-lookup"><span data-stu-id="2b35e-139">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="2b35e-140">В следующем примере областью целочисленной переменной `cube` является блок между `If` и `End If` , и вы больше не можете ссылаться на то, `cube` когда выполнение передается из блока.</span><span class="sxs-lookup"><span data-stu-id="2b35e-140">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> <span data-ttu-id="2b35e-141">Даже если область действия переменной ограничена блоком, ее время существования все равно будет содержаться во всей процедуре.</span><span class="sxs-lookup"><span data-stu-id="2b35e-141">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="2b35e-142">Если вы вводите блок несколько раз во время процедуры, каждая переменная блока удерживает свое предыдущее значение.</span><span class="sxs-lookup"><span data-stu-id="2b35e-142">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="2b35e-143">Чтобы избежать непредвиденных результатов в таком случае, разумно инициализировать блочные переменные в начале блока.</span><span class="sxs-lookup"><span data-stu-id="2b35e-143">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>

### <a name="procedure-scope"></a><span data-ttu-id="2b35e-144">Область действия процедуры</span><span class="sxs-lookup"><span data-stu-id="2b35e-144">Procedure Scope</span></span>

<span data-ttu-id="2b35e-145">Элемент, объявленный внутри процедуры, недоступен за пределами этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="2b35e-145">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="2b35e-146">Только процедура, содержащая объявление, может использовать его.</span><span class="sxs-lookup"><span data-stu-id="2b35e-146">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="2b35e-147">Переменные на этом уровне также называются *локальными переменными*.</span><span class="sxs-lookup"><span data-stu-id="2b35e-147">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="2b35e-148">Они объявляются с помощью [оператора Dim](../../../language-reference/statements/dim-statement.md)с ключевым словом [static](../../../language-reference/modifiers/static.md) или без него.</span><span class="sxs-lookup"><span data-stu-id="2b35e-148">You declare them with the [Dim Statement](../../../language-reference/statements/dim-statement.md), with or without the [Static](../../../language-reference/modifiers/static.md) keyword.</span></span>

<span data-ttu-id="2b35e-149">Область действия процедуры и блока тесно связана.</span><span class="sxs-lookup"><span data-stu-id="2b35e-149">Procedure and block scope are closely related.</span></span> <span data-ttu-id="2b35e-150">При объявлении переменной внутри процедуры, но вне любого блока внутри этой процедуры можно считать, что переменная имеет область видимости блока, где блоком является вся процедура.</span><span class="sxs-lookup"><span data-stu-id="2b35e-150">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="2b35e-151">Все локальные элементы, даже если они являются `Static` переменными, являются частными для процедуры, в которой они отображаются.</span><span class="sxs-lookup"><span data-stu-id="2b35e-151">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="2b35e-152">Нельзя объявить какой-либо элемент с помощью ключевого слова [Public](../../../language-reference/modifiers/public.md) в процедуре.</span><span class="sxs-lookup"><span data-stu-id="2b35e-152">You cannot declare any element using the [Public](../../../language-reference/modifiers/public.md) keyword within a procedure.</span></span>

### <a name="module-scope"></a><span data-ttu-id="2b35e-153">Область модуля</span><span class="sxs-lookup"><span data-stu-id="2b35e-153">Module Scope</span></span>

<span data-ttu-id="2b35e-154">Для удобства *уровень модуля* единого термина применяется в равной степени к модулям, классам и структурам.</span><span class="sxs-lookup"><span data-stu-id="2b35e-154">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="2b35e-155">Вы можете объявить элементы на этом уровне, поместив оператор объявления за пределы любой процедуры или блока, но внутри модуля, класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="2b35e-155">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>

<span data-ttu-id="2b35e-156">При создании объявления на уровне модуля этот уровень доступа определяет область.</span><span class="sxs-lookup"><span data-stu-id="2b35e-156">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="2b35e-157">Пространство имен, содержащее модуль, класс или структуру, также влияет на область.</span><span class="sxs-lookup"><span data-stu-id="2b35e-157">The namespace that contains the module, class, or structure also affects the scope.</span></span>

<span data-ttu-id="2b35e-158">Элементы, для которых объявлен [частный](../../../language-reference/modifiers/private.md) уровень доступа, доступны для каждой процедуры в этом модуле, но не для кода в другом модуле.</span><span class="sxs-lookup"><span data-stu-id="2b35e-158">Elements for which you declare [Private](../../../language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="2b35e-159">`Dim`Инструкция на уровне модуля по умолчанию принимает значение, `Private` если не используются ключевые слова уровня доступа.</span><span class="sxs-lookup"><span data-stu-id="2b35e-159">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="2b35e-160">Тем не менее можно сделать область и уровень доступа более очевидными с помощью `Private` ключевого слова в `Dim` инструкции.</span><span class="sxs-lookup"><span data-stu-id="2b35e-160">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>

<span data-ttu-id="2b35e-161">В следующем примере все процедуры, определенные в модуле, могут ссылаться на строковую переменную `strMsg` .</span><span class="sxs-lookup"><span data-stu-id="2b35e-161">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="2b35e-162">При вызове второй процедуры она отображает содержимое строковой переменной `strMsg` в диалоговом окне.</span><span class="sxs-lookup"><span data-stu-id="2b35e-162">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>

```vb
' Put the following declaration at module level (not in any procedure).
Private strMsg As String
' Put the following Sub procedure in the same module.
Sub initializePrivateVariable()
    strMsg = "This variable cannot be used outside this module."
End Sub
' Put the following Sub procedure in the same module.
Sub usePrivateVariable()
    MsgBox(strMsg)
End Sub
```

### <a name="namespace-scope"></a><span data-ttu-id="2b35e-163">Область пространства имен</span><span class="sxs-lookup"><span data-stu-id="2b35e-163">Namespace Scope</span></span>

<span data-ttu-id="2b35e-164">Если элемент объявляется на уровне модуля с помощью ключевого слова [Friend](../../../language-reference/modifiers/friend.md) или [Public](../../../language-reference/modifiers/public.md) , он становится доступным для всех процедур в пространстве имен, в котором объявлен элемент.</span><span class="sxs-lookup"><span data-stu-id="2b35e-164">If you declare an element at module level using the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="2b35e-165">После выполнения следующей изменения в предыдущем примере строковая переменная `strMsg` может называться кодом в любом месте пространства имен его объявления.</span><span class="sxs-lookup"><span data-stu-id="2b35e-165">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

<span data-ttu-id="2b35e-166">Область пространства имен включает вложенные пространства имен.</span><span class="sxs-lookup"><span data-stu-id="2b35e-166">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="2b35e-167">Элемент, доступный из пространства имен, также доступен из любого пространства имен, вложенного в это пространство имен.</span><span class="sxs-lookup"><span data-stu-id="2b35e-167">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>

<span data-ttu-id="2b35e-168">Если проект не содержит [операторов пространства имен](../../../language-reference/statements/namespace-statement.md), все в проекте находится в том же пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="2b35e-168">If your project does not contain any [Namespace Statement](../../../language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="2b35e-169">В этом случае область пространства имен может рассматриваться как область проекта.</span><span class="sxs-lookup"><span data-stu-id="2b35e-169">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="2b35e-170">`Public` элементы в модуле, классе или структуре также доступны для любого проекта, который ссылается на свой проект.</span><span class="sxs-lookup"><span data-stu-id="2b35e-170">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>

## <a name="choice-of-scope"></a><span data-ttu-id="2b35e-171">Выбора области</span><span class="sxs-lookup"><span data-stu-id="2b35e-171">Choice of Scope</span></span>

<span data-ttu-id="2b35e-172">При определении переменной следует учитывать следующие моменты при выборе ее области действия.</span><span class="sxs-lookup"><span data-stu-id="2b35e-172">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>

### <a name="advantages-of-local-variables"></a><span data-ttu-id="2b35e-173">Преимущества локальных переменных</span><span class="sxs-lookup"><span data-stu-id="2b35e-173">Advantages of Local Variables</span></span>

<span data-ttu-id="2b35e-174">Локальные переменные являются хорошим выбором для любого временного вычисления по следующим причинам.</span><span class="sxs-lookup"><span data-stu-id="2b35e-174">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>

- <span data-ttu-id="2b35e-175">**Конфликт имен — избежать.**</span><span class="sxs-lookup"><span data-stu-id="2b35e-175">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="2b35e-176">Имена локальных переменных не подвержены конфликтам.</span><span class="sxs-lookup"><span data-stu-id="2b35e-176">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="2b35e-177">Например, можно создать несколько различных процедур, содержащих переменную с именем `intTemp` .</span><span class="sxs-lookup"><span data-stu-id="2b35e-177">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="2b35e-178">Если каждая из них `intTemp` объявлена как локальная переменная, каждая процедура распознает только собственную версию `intTemp` .</span><span class="sxs-lookup"><span data-stu-id="2b35e-178">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="2b35e-179">Любая процедура может изменить значение в локальной переменной, `intTemp` не влияя на `intTemp` переменные в других процедурах.</span><span class="sxs-lookup"><span data-stu-id="2b35e-179">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>

- <span data-ttu-id="2b35e-180">**Потребление памяти.**</span><span class="sxs-lookup"><span data-stu-id="2b35e-180">**Memory Consumption.**</span></span> <span data-ttu-id="2b35e-181">Локальные переменные потребляют память только во время выполнения процедуры.</span><span class="sxs-lookup"><span data-stu-id="2b35e-181">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="2b35e-182">Их память освобождается, когда процедура возвращается в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="2b35e-182">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="2b35e-183">В отличие от этого, [Общие](../../../language-reference/modifiers/shared.md) и [статические](../../../language-reference/modifiers/static.md) переменные потребляют ресурсы памяти до тех пор, пока приложение не прекратит работу, поэтому используйте их только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="2b35e-183">By contrast, [Shared](../../../language-reference/modifiers/shared.md) and [Static](../../../language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="2b35e-184">*Переменные экземпляра* потребляют память, пока их экземпляры продолжают существовать, что делает их менее эффективными, чем локальные переменные, но потенциально более эффективными, чем `Shared` `Static` переменные.</span><span class="sxs-lookup"><span data-stu-id="2b35e-184">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>

### <a name="minimizing-scope"></a><span data-ttu-id="2b35e-185">Минимизация области</span><span class="sxs-lookup"><span data-stu-id="2b35e-185">Minimizing Scope</span></span>

<span data-ttu-id="2b35e-186">Как правило, при объявлении любой переменной или константы рекомендуется сделать область как можно более узким (область блока является самой узким).</span><span class="sxs-lookup"><span data-stu-id="2b35e-186">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="2b35e-187">Это помогает экономить память и минимизирует вероятность того, что код ошибочно ссылался на неверную переменную.</span><span class="sxs-lookup"><span data-stu-id="2b35e-187">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="2b35e-188">Аналогично, следует объявить переменную как [статическую](../../../language-reference/modifiers/static.md) , только если необходимо сохранить ее значение между вызовами процедур.</span><span class="sxs-lookup"><span data-stu-id="2b35e-188">Similarly, you should declare a variable to be [Static](../../../language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b35e-189">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2b35e-189">See also</span></span>

- [<span data-ttu-id="2b35e-190">Характеристики объявленных элементов</span><span class="sxs-lookup"><span data-stu-id="2b35e-190">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="2b35e-191">Практическое руководство. Управление областью действия переменной</span><span class="sxs-lookup"><span data-stu-id="2b35e-191">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="2b35e-192">Время существования в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b35e-192">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="2b35e-193">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b35e-193">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="2b35e-194">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="2b35e-194">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="2b35e-195">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="2b35e-195">Variable Declaration</span></span>](../variables/variable-declaration.md)
