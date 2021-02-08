---
description: 'Дополнительные сведения: оператор Dim (Visual Basic)'
title: Dim - оператор
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: b950ae95af01be4e064ac9177300f144e0cc08b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795200"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="0d750-103">Оператор Dim (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d750-103">Dim statement (Visual Basic)</span></span>

<span data-ttu-id="0d750-104">Объявляет и выделяет дисковое пространство для одной или нескольких переменных.</span><span class="sxs-lookup"><span data-stu-id="0d750-104">Declares and allocates storage space for one or more variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d750-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0d750-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a><span data-ttu-id="0d750-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="0d750-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="0d750-107">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-107">Optional.</span></span> <span data-ttu-id="0d750-108">См. [список атрибутов](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-108">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="0d750-109">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-109">Optional.</span></span> <span data-ttu-id="0d750-110">Может принимать следующие значения:</span><span class="sxs-lookup"><span data-stu-id="0d750-110">Can be one of the following:</span></span>

  - [<span data-ttu-id="0d750-111">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="0d750-111">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="0d750-112">Защищенный</span><span class="sxs-lookup"><span data-stu-id="0d750-112">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="0d750-113">Friend</span><span class="sxs-lookup"><span data-stu-id="0d750-113">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="0d750-114">Частная</span><span class="sxs-lookup"><span data-stu-id="0d750-114">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="0d750-115">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="0d750-115">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="0d750-116">Частный защищенный</span><span class="sxs-lookup"><span data-stu-id="0d750-116">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="0d750-117">См. раздел [уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-117">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `Shared`

  <span data-ttu-id="0d750-118">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-118">Optional.</span></span> <span data-ttu-id="0d750-119">См. раздел [Shared](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-119">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="0d750-120">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-120">Optional.</span></span> <span data-ttu-id="0d750-121">См. раздел [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-121">See [Shadows](../modifiers/shadows.md).</span></span>

- `Static`

  <span data-ttu-id="0d750-122">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-122">Optional.</span></span> <span data-ttu-id="0d750-123">См. раздел [static](../modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-123">See [Static](../modifiers/static.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="0d750-124">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-124">Optional.</span></span> <span data-ttu-id="0d750-125">См. раздел [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-125">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WithEvents`

  <span data-ttu-id="0d750-126">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-126">Optional.</span></span> <span data-ttu-id="0d750-127">Указывает, что это переменные объекта, которые ссылаются на экземпляры класса, которые могут создавать события.</span><span class="sxs-lookup"><span data-stu-id="0d750-127">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="0d750-128">См. раздел [WithEvents](../modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-128">See [WithEvents](../modifiers/withevents.md).</span></span>

- `variablelist`

  <span data-ttu-id="0d750-129">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-129">Required.</span></span> <span data-ttu-id="0d750-130">Список переменных, объявляемых в этой инструкции.</span><span class="sxs-lookup"><span data-stu-id="0d750-130">List of variables being declared in this statement.</span></span>

  `variable [ , variable ... ]`

  <span data-ttu-id="0d750-131">Каждый элемент `variable` имеет перечисленные ниже синтаксис и компоненты.</span><span class="sxs-lookup"><span data-stu-id="0d750-131">Each `variable` has the following syntax and parts:</span></span>

  <span data-ttu-id="0d750-132">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="0d750-132">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>

  |<span data-ttu-id="0d750-133">Отделение</span><span class="sxs-lookup"><span data-stu-id="0d750-133">Part</span></span>|<span data-ttu-id="0d750-134">Описание</span><span class="sxs-lookup"><span data-stu-id="0d750-134">Description</span></span>|
  |---|---|
  |`variablename`|<span data-ttu-id="0d750-135">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-135">Required.</span></span> <span data-ttu-id="0d750-136">Имя переменной.</span><span class="sxs-lookup"><span data-stu-id="0d750-136">Name of the variable.</span></span> <span data-ttu-id="0d750-137">См. раздел [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-137">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
  |`boundslist`|<span data-ttu-id="0d750-138">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-138">Optional.</span></span> <span data-ttu-id="0d750-139">Список границ каждого измерения переменной массива.</span><span class="sxs-lookup"><span data-stu-id="0d750-139">List of bounds of each dimension of an array variable.</span></span>|
  |`New`|<span data-ttu-id="0d750-140">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-140">Optional.</span></span> <span data-ttu-id="0d750-141">Создает новый экземпляр класса при `Dim` выполнении инструкции.</span><span class="sxs-lookup"><span data-stu-id="0d750-141">Creates a new instance of the class when the `Dim` statement runs.</span></span>|
  |`datatype`|<span data-ttu-id="0d750-142">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-142">Optional.</span></span> <span data-ttu-id="0d750-143">Тип данных переменной.</span><span class="sxs-lookup"><span data-stu-id="0d750-143">Data type of the variable.</span></span>|
  |`With`|<span data-ttu-id="0d750-144">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-144">Optional.</span></span> <span data-ttu-id="0d750-145">Представляет список инициализаторов объектов.</span><span class="sxs-lookup"><span data-stu-id="0d750-145">Introduces the object initializer list.</span></span>|
  |`propertyname`|<span data-ttu-id="0d750-146">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d750-146">Optional.</span></span> <span data-ttu-id="0d750-147">Имя свойства в классе, экземпляр которого вы вносите.</span><span class="sxs-lookup"><span data-stu-id="0d750-147">The name of a property in the class you are making an instance of.</span></span>|
  |`propinitializer`|<span data-ttu-id="0d750-148">Требуется после `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="0d750-148">Required after `propertyname` =.</span></span> <span data-ttu-id="0d750-149">Выражение, которое вычисляется и присваивается имени свойства.</span><span class="sxs-lookup"><span data-stu-id="0d750-149">The expression that is evaluated and assigned to the property name.</span></span>|
  |`initializer`|<span data-ttu-id="0d750-150">Необязательный `New` , если не указан.</span><span class="sxs-lookup"><span data-stu-id="0d750-150">Optional if `New` is not specified.</span></span> <span data-ttu-id="0d750-151">Выражение, которое вычисляется и присваивается переменной при ее создании.</span><span class="sxs-lookup"><span data-stu-id="0d750-151">Expression that is evaluated and assigned to the variable when it is created.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0d750-152">Remarks</span><span class="sxs-lookup"><span data-stu-id="0d750-152">Remarks</span></span>

<span data-ttu-id="0d750-153">Компилятор Visual Basic использует `Dim` инструкцию для определения типа данных переменной и других сведений, например кода, который может получить доступ к переменной.</span><span class="sxs-lookup"><span data-stu-id="0d750-153">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="0d750-154">В следующем примере объявляется переменная для хранения `Integer` значения.</span><span class="sxs-lookup"><span data-stu-id="0d750-154">The following example declares a variable to hold an `Integer` value.</span></span>

```vb
Dim numberOfStudents As Integer
```

<span data-ttu-id="0d750-155">Можно указать любой тип данных или имя перечисления, структуры, класса или интерфейса.</span><span class="sxs-lookup"><span data-stu-id="0d750-155">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

<span data-ttu-id="0d750-156">Для ссылочного типа используйте `New` ключевое слово, чтобы создать новый экземпляр класса или структуры, заданный типом данных.</span><span class="sxs-lookup"><span data-stu-id="0d750-156">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="0d750-157">Если используется `New` , выражение инициализатора не используется.</span><span class="sxs-lookup"><span data-stu-id="0d750-157">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="0d750-158">Вместо этого вы предоставляете аргументы, если они требуются, в конструктор класса, из которого создается переменная.</span><span class="sxs-lookup"><span data-stu-id="0d750-158">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

<span data-ttu-id="0d750-159">Переменную можно объявить в процедуре, блоке, классе, структуре или модуле.</span><span class="sxs-lookup"><span data-stu-id="0d750-159">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="0d750-160">Нельзя объявить переменную в исходном файле, пространстве имен или интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="0d750-160">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="0d750-161">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-161">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="0d750-162">Переменная, объявленная на уровне модуля вне любой процедуры, является переменной или *полем* *члена* .</span><span class="sxs-lookup"><span data-stu-id="0d750-162">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="0d750-163">Переменные членов находятся в области действия класса, структуры или модуля.</span><span class="sxs-lookup"><span data-stu-id="0d750-163">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="0d750-164">Переменная, объявленная на уровне процедуры, является *локальной переменной*.</span><span class="sxs-lookup"><span data-stu-id="0d750-164">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="0d750-165">Локальные переменные находятся в области действия только в пределах их процедуры или блока.</span><span class="sxs-lookup"><span data-stu-id="0d750-165">Local variables are in scope only within their procedure or block.</span></span>

<span data-ttu-id="0d750-166">Следующие модификаторы доступа используются для объявления переменных вне процедуры: `Public` ,, `Protected` `Friend` , `Protected Friend` и `Private` .</span><span class="sxs-lookup"><span data-stu-id="0d750-166">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="0d750-167">Дополнительные сведения см. [в разделе уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-167">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="0d750-168">`Dim`Ключевое слово является необязательным и обычно опускается при указании любого из следующих модификаторов: `Public` , `Protected` , `Friend` ,,, `Protected Friend` `Private` `Shared` , `Shadows` , `Static` , `ReadOnly` или `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="0d750-168">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

<span data-ttu-id="0d750-169">Если `Option Explicit` параметр имеет значение On (значение по умолчанию), компилятору требуется объявление для каждой используемой переменной.</span><span class="sxs-lookup"><span data-stu-id="0d750-169">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="0d750-170">Дополнительные сведения см. в разделе [оператор Option Explicit](option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-170">For more information, see [Option Explicit Statement](option-explicit-statement.md).</span></span>

## <a name="specifying-an-initial-value"></a><span data-ttu-id="0d750-171">Указание начального значения</span><span class="sxs-lookup"><span data-stu-id="0d750-171">Specifying an initial value</span></span>

<span data-ttu-id="0d750-172">При создании переменной можно присвоить значение.</span><span class="sxs-lookup"><span data-stu-id="0d750-172">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="0d750-173">Для типа значения используйте *инициализатор* , чтобы указать выражение, присваиваемое переменной.</span><span class="sxs-lookup"><span data-stu-id="0d750-173">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="0d750-174">Результатом вычисления выражения должно быть константа, которую можно вычислить во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="0d750-174">The expression must evaluate to a constant that can be calculated at compile time.</span></span>

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

<span data-ttu-id="0d750-175">Если инициализатор указан и в предложении не указан тип данных `As` , для получения типа данных из инициализатора используется *вывод типа* .</span><span class="sxs-lookup"><span data-stu-id="0d750-175">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="0d750-176">В следующем примере оба типа `num1` и `num2` строго типизированы как целые числа.</span><span class="sxs-lookup"><span data-stu-id="0d750-176">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="0d750-177">Во втором объявлении определение типа выводит тип из значения 3.</span><span class="sxs-lookup"><span data-stu-id="0d750-177">In the second declaration, type inference infers the type from the value 3.</span></span>

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

<span data-ttu-id="0d750-178">Определение типа применяется на уровне процедуры.</span><span class="sxs-lookup"><span data-stu-id="0d750-178">Type inference applies at the procedure level.</span></span> <span data-ttu-id="0d750-179">Он не применяется за пределами процедуры в классе, структуре, модуле или интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="0d750-179">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="0d750-180">Дополнительные сведения о выводе типа см. в разделе [Option Infer](option-infer-statement.md) и [определение локального типа](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-180">For more information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="0d750-181">Сведения о том, что происходит, если не указан тип данных или инициализатор, см. в подразделе [типы данных и значения по умолчанию](dim-statement.md#default) далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="0d750-181">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](dim-statement.md#default) later in this topic.</span></span>

<span data-ttu-id="0d750-182">*Инициализатор объекта* можно использовать для объявления экземпляров именованных и анонимных типов.</span><span class="sxs-lookup"><span data-stu-id="0d750-182">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="0d750-183">Следующий код создает экземпляр `Student` класса и использует инициализатор объекта для инициализации свойств.</span><span class="sxs-lookup"><span data-stu-id="0d750-183">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

<span data-ttu-id="0d750-184">Дополнительные сведения об инициализаторах объектов см. [в разделе как объявить объект с помощью инициализатора](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)объекта, [инициализаторов объектов: именованные и анонимные типы](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)и [анонимные типы](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-184">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="declaring-multiple-variables"></a><span data-ttu-id="0d750-185">Объявление нескольких переменных</span><span class="sxs-lookup"><span data-stu-id="0d750-185">Declaring multiple variables</span></span>

<span data-ttu-id="0d750-186">Можно объявить несколько переменных в одном операторе объявления, указав имя переменной для каждой из них, и после каждого имени массива с круглыми скобками.</span><span class="sxs-lookup"><span data-stu-id="0d750-186">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="0d750-187">Переменные разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="0d750-187">Multiple variables are separated by commas.</span></span>

```vb
Dim lastTime, nextTime, allTimes() As Date
```

<span data-ttu-id="0d750-188">Если объявить более одной переменной с одним `As` предложением, вы не сможете предоставить инициализатор для этой группы переменных.</span><span class="sxs-lookup"><span data-stu-id="0d750-188">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>

<span data-ttu-id="0d750-189">Можно указать различные типы данных для разных переменных, используя отдельное `As` предложение для каждой объявляемой переменной.</span><span class="sxs-lookup"><span data-stu-id="0d750-189">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="0d750-190">Каждая переменная принимает тип данных, указанный в первом `As` предложении, обнаруженном после его `variablename` части.</span><span class="sxs-lookup"><span data-stu-id="0d750-190">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a><span data-ttu-id="0d750-191">Массивы</span><span class="sxs-lookup"><span data-stu-id="0d750-191">Arrays</span></span>

<span data-ttu-id="0d750-192">Можно объявить переменную для хранения *массива*, который может содержать несколько значений.</span><span class="sxs-lookup"><span data-stu-id="0d750-192">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="0d750-193">Чтобы указать, что переменная содержит массив, сразу после нее следует использовать `variablename` круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="0d750-193">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="0d750-194">Дополнительные сведения см. в руководстве по работе с [массивами](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-194">For more information about arrays, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="0d750-195">Можно указать нижнюю и верхнюю границы каждого измерения массива.</span><span class="sxs-lookup"><span data-stu-id="0d750-195">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="0d750-196">Для этого добавьте в `boundslist` круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="0d750-196">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="0d750-197">Для каждого измерения объект `boundslist` задает верхнюю границу и, при необходимости, нижнюю границу.</span><span class="sxs-lookup"><span data-stu-id="0d750-197">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="0d750-198">Нижняя граница всегда равна нулю, независимо от того, указана она или нет.</span><span class="sxs-lookup"><span data-stu-id="0d750-198">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="0d750-199">Каждый индекс может изменяться от нуля до значения его верхней границы.</span><span class="sxs-lookup"><span data-stu-id="0d750-199">Each index can vary from zero through its upper bound value.</span></span>

<span data-ttu-id="0d750-200">Следующие две инструкции эквивалентны.</span><span class="sxs-lookup"><span data-stu-id="0d750-200">The following two statements are equivalent.</span></span> <span data-ttu-id="0d750-201">Каждый оператор объявляет массив из 21 `Integer` элемента.</span><span class="sxs-lookup"><span data-stu-id="0d750-201">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="0d750-202">При доступе к массиву индекс может изменяться от 0 до 20.</span><span class="sxs-lookup"><span data-stu-id="0d750-202">When you access the array, the index can vary from 0 through 20.</span></span>

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

<span data-ttu-id="0d750-203">В следующей инструкции объявляется двухмерный массив типа `Double` .</span><span class="sxs-lookup"><span data-stu-id="0d750-203">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="0d750-204">Массив содержит 4 строки (3 + 1) из 6 столбцов (5 + 1) каждого.</span><span class="sxs-lookup"><span data-stu-id="0d750-204">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="0d750-205">Обратите внимание, что верхняя граница представляет наибольшее возможное значение индекса, а не длину измерения.</span><span class="sxs-lookup"><span data-stu-id="0d750-205">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="0d750-206">Длина измерения является верхней границей плюс единица.</span><span class="sxs-lookup"><span data-stu-id="0d750-206">The length of the dimension is the upper bound plus one.</span></span>

```vb
Dim matrix2(3, 5) As Double
```

<span data-ttu-id="0d750-207">Массив может иметь размер от 1 до 32.</span><span class="sxs-lookup"><span data-stu-id="0d750-207">An array can have from 1 to 32 dimensions.</span></span>

<span data-ttu-id="0d750-208">Все границы в объявлении массива можно оставить пустыми.</span><span class="sxs-lookup"><span data-stu-id="0d750-208">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="0d750-209">В этом случае массив имеет указанное число измерений, но не инициализировано.</span><span class="sxs-lookup"><span data-stu-id="0d750-209">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="0d750-210">Он имеет значение `Nothing` до тех пор, пока не будет инициализировано по крайней мере часть его элементов.</span><span class="sxs-lookup"><span data-stu-id="0d750-210">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="0d750-211">В `Dim` инструкции должны быть указаны границы для всех измерений или для отсутствия измерений.</span><span class="sxs-lookup"><span data-stu-id="0d750-211">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

<span data-ttu-id="0d750-212">Если массив имеет более одного измерения, необходимо включить запятые между круглыми скобками, чтобы указать количество измерений.</span><span class="sxs-lookup"><span data-stu-id="0d750-212">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

<span data-ttu-id="0d750-213">Можно объявить *массив нулевой длины* , объявляя один из измерений массива равным-1.</span><span class="sxs-lookup"><span data-stu-id="0d750-213">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="0d750-214">Переменная, содержащая массив нулевой длины, не имеет значения `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="0d750-214">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="0d750-215">Для некоторых функций среды CLR требуются массивы нулевой длины.</span><span class="sxs-lookup"><span data-stu-id="0d750-215">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="0d750-216">При попытке доступа к такому массиву возникает исключение времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="0d750-216">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="0d750-217">Дополнительные сведения см. в статье [Arrays (C++/CLI and C++/CX)](../../programming-guide/language-features/arrays/index.md) (Массивы (C++/CLI и C++/CX)).</span><span class="sxs-lookup"><span data-stu-id="0d750-217">For more information, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="0d750-218">Значения массива можно инициализировать с помощью литерала массива.</span><span class="sxs-lookup"><span data-stu-id="0d750-218">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="0d750-219">Для этого заключите значения инициализации в фигурные скобки ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="0d750-219">To do this, surround the initialization values with braces (`{}`).</span></span>

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

<span data-ttu-id="0d750-220">Для многомерных массивов инициализация каждого отдельного измерения заключается в фигурные скобки во внешнем измерении.</span><span class="sxs-lookup"><span data-stu-id="0d750-220">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="0d750-221">Элементы задаются в построчном порядке.</span><span class="sxs-lookup"><span data-stu-id="0d750-221">The elements are specified in row-major order.</span></span>

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

<span data-ttu-id="0d750-222">Дополнительные сведения о литералах массивов см. в разделе [массивы](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-222">For more information about array literals, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

## <a name="default-data-types-and-values"></a><a name="default"></a> <span data-ttu-id="0d750-223">Типы данных и значения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="0d750-223">Default data types and values</span></span>

<span data-ttu-id="0d750-224">В следующей таблице перечислены результаты различных сочетаний заданных типов данных и инициализаторов в операторе `Dim`.</span><span class="sxs-lookup"><span data-stu-id="0d750-224">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="0d750-225">Указан тип данных?</span><span class="sxs-lookup"><span data-stu-id="0d750-225">Data type specified?</span></span>|<span data-ttu-id="0d750-226">Указан инициализатор?</span><span class="sxs-lookup"><span data-stu-id="0d750-226">Initializer specified?</span></span>|<span data-ttu-id="0d750-227">Пример</span><span class="sxs-lookup"><span data-stu-id="0d750-227">Example</span></span>|<span data-ttu-id="0d750-228">Результат</span><span class="sxs-lookup"><span data-stu-id="0d750-228">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="0d750-229">нет</span><span class="sxs-lookup"><span data-stu-id="0d750-229">No</span></span>|<span data-ttu-id="0d750-230">Нет</span><span class="sxs-lookup"><span data-stu-id="0d750-230">No</span></span>|`Dim qty`|<span data-ttu-id="0d750-231">Если [параметр optioned](option-strict-statement.md) имеет значение OFF (значение по умолчанию), то переменной присваивается значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="0d750-231">If [Option Strict](option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="0d750-232">Если параметр `Option Strict` включен, возникает ошибка времени при компиляции.</span><span class="sxs-lookup"><span data-stu-id="0d750-232">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="0d750-233">Нет</span><span class="sxs-lookup"><span data-stu-id="0d750-233">No</span></span>|<span data-ttu-id="0d750-234">Да</span><span class="sxs-lookup"><span data-stu-id="0d750-234">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="0d750-235">Если [параметр Infer](option-infer-statement.md) имеет значение On (значение по умолчанию), переменная принимает тип данных инициализатора.</span><span class="sxs-lookup"><span data-stu-id="0d750-235">If [Option Infer](option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="0d750-236">См. раздел [определение локального типа](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-236">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="0d750-237">Если параметры `Option Infer` и `Option Strict` отключены, переменная получает тип данных `Object`.</span><span class="sxs-lookup"><span data-stu-id="0d750-237">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="0d750-238">Если параметр `Option Infer` отключен, а параметр `Option Strict` включен, возникает ошибка времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="0d750-238">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="0d750-239">Да</span><span class="sxs-lookup"><span data-stu-id="0d750-239">Yes</span></span>|<span data-ttu-id="0d750-240">Нет</span><span class="sxs-lookup"><span data-stu-id="0d750-240">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="0d750-241">Переменная инициализируется со значением по умолчанию для типа данных.</span><span class="sxs-lookup"><span data-stu-id="0d750-241">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="0d750-242">См. таблицу далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="0d750-242">See the table later in this section.</span></span>|
|<span data-ttu-id="0d750-243">Да</span><span class="sxs-lookup"><span data-stu-id="0d750-243">Yes</span></span>|<span data-ttu-id="0d750-244">Да</span><span class="sxs-lookup"><span data-stu-id="0d750-244">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="0d750-245">Если тип данных инициализатора нельзя преобразовать в указанный тип данных, возникает ошибка времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="0d750-245">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

<span data-ttu-id="0d750-246">Если указать тип данных, но не указать инициализатор, Visual Basic инициализирует переменную как значение по умолчанию для ее типа данных.</span><span class="sxs-lookup"><span data-stu-id="0d750-246">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="0d750-247">В следующей таблице приведены значения инициализации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0d750-247">The following table shows the default initialization values.</span></span>

|<span data-ttu-id="0d750-248">Тип данных</span><span class="sxs-lookup"><span data-stu-id="0d750-248">Data type</span></span>|<span data-ttu-id="0d750-249">Значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="0d750-249">Default value</span></span>|
|---|---|
|<span data-ttu-id="0d750-250">Все числовые типы (включая `Byte` и `SByte` )</span><span class="sxs-lookup"><span data-stu-id="0d750-250">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="0d750-251">0</span><span class="sxs-lookup"><span data-stu-id="0d750-251">0</span></span>|
|`Char`|<span data-ttu-id="0d750-252">Двоичный 0</span><span class="sxs-lookup"><span data-stu-id="0d750-252">Binary 0</span></span>|
|<span data-ttu-id="0d750-253">Все ссылочные типы (включая `Object` , `String` и все массивы)</span><span class="sxs-lookup"><span data-stu-id="0d750-253">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|
|`Boolean`|`False`|
|`Date`|<span data-ttu-id="0d750-254">12:00 AM 1 января 1 года (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="0d750-254">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|

<span data-ttu-id="0d750-255">Каждый элемент структуры инициализируется так, как если бы он был отдельной переменной.</span><span class="sxs-lookup"><span data-stu-id="0d750-255">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="0d750-256">Если вы объявили длину массива, но не инициализируйте его элементы, каждый элемент инициализируется так, как если бы он был отдельной переменной.</span><span class="sxs-lookup"><span data-stu-id="0d750-256">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>

## <a name="static-local-variable-lifetime"></a><span data-ttu-id="0d750-257">Время существования статической локальной переменной</span><span class="sxs-lookup"><span data-stu-id="0d750-257">Static local variable lifetime</span></span>

<span data-ttu-id="0d750-258">`Static`Срок жизни локальной переменной превышает время существования процедуры, в которой она объявлена.</span><span class="sxs-lookup"><span data-stu-id="0d750-258">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="0d750-259">Границы времени существования переменной зависят от того, где объявляется процедура, и является ли она `Shared` .</span><span class="sxs-lookup"><span data-stu-id="0d750-259">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>

|<span data-ttu-id="0d750-260">Объявление процедуры</span><span class="sxs-lookup"><span data-stu-id="0d750-260">Procedure declaration</span></span>|<span data-ttu-id="0d750-261">Переменная инициализирована</span><span class="sxs-lookup"><span data-stu-id="0d750-261">Variable initialized</span></span>|<span data-ttu-id="0d750-262">Переменная останавливается</span><span class="sxs-lookup"><span data-stu-id="0d750-262">Variable stops existing</span></span>|
|---|---|---|
|<span data-ttu-id="0d750-263">В модуле</span><span class="sxs-lookup"><span data-stu-id="0d750-263">In a module</span></span>|<span data-ttu-id="0d750-264">При первом вызове процедуры</span><span class="sxs-lookup"><span data-stu-id="0d750-264">The first time the procedure is called</span></span>|<span data-ttu-id="0d750-265">При остановке выполнения программы</span><span class="sxs-lookup"><span data-stu-id="0d750-265">When your program stops execution</span></span>|
|<span data-ttu-id="0d750-266">В классе или структуре процедура `Shared`</span><span class="sxs-lookup"><span data-stu-id="0d750-266">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="0d750-267">При первом вызове процедуры либо в определенном экземпляре, либо в самом классе или структуре.</span><span class="sxs-lookup"><span data-stu-id="0d750-267">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="0d750-268">При остановке выполнения программы</span><span class="sxs-lookup"><span data-stu-id="0d750-268">When your program stops execution</span></span>|
|<span data-ttu-id="0d750-269">В классе или структуре процедура не `Shared`</span><span class="sxs-lookup"><span data-stu-id="0d750-269">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="0d750-270">При первом вызове процедуры в определенном экземпляре</span><span class="sxs-lookup"><span data-stu-id="0d750-270">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="0d750-271">Когда экземпляр выпускается для сборки мусора (GC)</span><span class="sxs-lookup"><span data-stu-id="0d750-271">When the instance is released for garbage collection (GC)</span></span>|

## <a name="attributes-and-modifiers"></a><span data-ttu-id="0d750-272">Атрибуты и модификаторы</span><span class="sxs-lookup"><span data-stu-id="0d750-272">Attributes and modifiers</span></span>

<span data-ttu-id="0d750-273">Атрибуты можно применять только к переменным члена, а не к локальным переменным.</span><span class="sxs-lookup"><span data-stu-id="0d750-273">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="0d750-274">Атрибут вносит сведения в метаданные сборки, что не имеет смысла для временного хранения, например локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="0d750-274">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>

<span data-ttu-id="0d750-275">На уровне модуля нельзя использовать `Static` Модификатор для объявления переменных члена.</span><span class="sxs-lookup"><span data-stu-id="0d750-275">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="0d750-276">На уровне процедуры нельзя использовать,, `Shared` , `Shadows` `ReadOnly` `WithEvents` или модификаторы доступа для объявления локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="0d750-276">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>

<span data-ttu-id="0d750-277">Можно указать, какой код может получить доступ к переменной, указав `accessmodifier` .</span><span class="sxs-lookup"><span data-stu-id="0d750-277">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="0d750-278">Переменные-члены класса и модуля (вне любой процедуры) по умолчанию имеют частный доступ, а переменные-члены структуры по умолчанию имеют общий доступ.</span><span class="sxs-lookup"><span data-stu-id="0d750-278">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="0d750-279">Уровни доступа можно изменить с помощью модификаторов доступа.</span><span class="sxs-lookup"><span data-stu-id="0d750-279">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="0d750-280">Нельзя использовать модификаторы доступа для локальных переменных (внутри процедуры).</span><span class="sxs-lookup"><span data-stu-id="0d750-280">You cannot use access modifiers on local variables (inside a procedure).</span></span>

<span data-ttu-id="0d750-281">Можно указать `WithEvents` только для переменных-членов, но не для локальных переменных внутри процедуры.</span><span class="sxs-lookup"><span data-stu-id="0d750-281">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="0d750-282">Если указать `WithEvents` , то тип данных переменной должен быть конкретным типом класса, а не `Object` .</span><span class="sxs-lookup"><span data-stu-id="0d750-282">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="0d750-283">Нельзя объявить массив с помощью `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="0d750-283">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="0d750-284">Дополнительные сведения о событиях см. в разделе [события](../../programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-284">For more information about events, see [Events](../../programming-guide/language-features/events/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0d750-285">Код за пределами класса, структуры или модуля должен уточнять имя переменной-члена именем этого класса, структуры или модуля.</span><span class="sxs-lookup"><span data-stu-id="0d750-285">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="0d750-286">Код за пределами процедуры или блока не может ссылаться на локальные переменные в этой процедуре или блоке.</span><span class="sxs-lookup"><span data-stu-id="0d750-286">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>

## <a name="releasing-managed-resources"></a><span data-ttu-id="0d750-287">Освобождение управляемых ресурсов</span><span class="sxs-lookup"><span data-stu-id="0d750-287">Releasing managed resources</span></span>

<span data-ttu-id="0d750-288">Сборщик мусора платформа .NET Framework уничтожает управляемые ресурсы без дополнительного программирования.</span><span class="sxs-lookup"><span data-stu-id="0d750-288">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="0d750-289">Однако можно вызвать принудительное удаление управляемого ресурса вместо ожидания сборщика мусора.</span><span class="sxs-lookup"><span data-stu-id="0d750-289">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

<span data-ttu-id="0d750-290">Если класс принадлежит особому ценному и ограниченному ресурсу (например, к подключению к базе данных или файлу), может возникнуть необходимость в ожидании следующей сборки мусора для очистки экземпляра класса, который больше не используется.</span><span class="sxs-lookup"><span data-stu-id="0d750-290">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="0d750-291">Класс может реализовать интерфейс, <xref:System.IDisposable> чтобы предоставить способ освобождения ресурсов перед сборкой мусора.</span><span class="sxs-lookup"><span data-stu-id="0d750-291">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="0d750-292">Класс, реализующий этот интерфейс, предоставляет `Dispose` метод, который может быть вызван для немедленного освобождения ценных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="0d750-292">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>

<span data-ttu-id="0d750-293">`Using`Инструкция автоматизирует процесс получения ресурса, выполнения набора инструкций и последующего удаления ресурса.</span><span class="sxs-lookup"><span data-stu-id="0d750-293">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="0d750-294">Однако ресурс должен реализовывать <xref:System.IDisposable> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="0d750-294">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="0d750-295">Дополнительные сведения см. в разделе [оператор using](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0d750-295">For more information, see [Using Statement](using-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="0d750-296">Пример</span><span class="sxs-lookup"><span data-stu-id="0d750-296">Example</span></span>

<span data-ttu-id="0d750-297">В следующем примере переменные объявляются с помощью `Dim` инструкции с различными параметрами.</span><span class="sxs-lookup"><span data-stu-id="0d750-297">The following example declares variables by using the `Dim` statement with various options.</span></span>

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a><span data-ttu-id="0d750-298">Пример</span><span class="sxs-lookup"><span data-stu-id="0d750-298">Example</span></span>

<span data-ttu-id="0d750-299">В следующем примере выводятся простые числа от 1 до 30.</span><span class="sxs-lookup"><span data-stu-id="0d750-299">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="0d750-300">Область локальных переменных описывается в разделе Комментарии к коду.</span><span class="sxs-lookup"><span data-stu-id="0d750-300">The scope of local variables is described in code comments.</span></span>

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a><span data-ttu-id="0d750-301">Пример</span><span class="sxs-lookup"><span data-stu-id="0d750-301">Example</span></span>

<span data-ttu-id="0d750-302">В следующем примере `speedValue` переменная объявляется на уровне класса.</span><span class="sxs-lookup"><span data-stu-id="0d750-302">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="0d750-303">`Private`Ключевое слово используется для объявления переменной.</span><span class="sxs-lookup"><span data-stu-id="0d750-303">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="0d750-304">Доступ к переменной может осуществляться любой процедурой в `Car` классе.</span><span class="sxs-lookup"><span data-stu-id="0d750-304">The variable can be accessed by any procedure in the `Car` class.</span></span>

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a><span data-ttu-id="0d750-305">См. также</span><span class="sxs-lookup"><span data-stu-id="0d750-305">See also</span></span>

- [<span data-ttu-id="0d750-306">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="0d750-306">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="0d750-307">Оператор reDim</span><span class="sxs-lookup"><span data-stu-id="0d750-307">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="0d750-308">Оператор Option Explicit</span><span class="sxs-lookup"><span data-stu-id="0d750-308">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="0d750-309">Оператор Option Infer</span><span class="sxs-lookup"><span data-stu-id="0d750-309">Option Infer Statement</span></span>](option-infer-statement.md)
- [<span data-ttu-id="0d750-310">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="0d750-310">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="0d750-311">Страница "Компиляция" в конструкторе проектов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d750-311">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="0d750-312">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="0d750-312">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="0d750-313">Массивы</span><span class="sxs-lookup"><span data-stu-id="0d750-313">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="0d750-314">Инициализаторы объектов: именованные и анонимные типы</span><span class="sxs-lookup"><span data-stu-id="0d750-314">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="0d750-315">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="0d750-315">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="0d750-316">Инициализаторы объектов: именованные и анонимные типы</span><span class="sxs-lookup"><span data-stu-id="0d750-316">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="0d750-317">Практическое руководство. Объявление объекта с помощью инициализатора объектов</span><span class="sxs-lookup"><span data-stu-id="0d750-317">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="0d750-318">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="0d750-318">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
