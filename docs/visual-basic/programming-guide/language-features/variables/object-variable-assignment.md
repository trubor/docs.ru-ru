---
description: 'Дополнительные сведения: назначение переменных объектов (Visual Basic)'
title: Присваивание объектных переменных
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: ac5e534a03d651a23e651e1049477b2bd0769b82
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481653"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="06d46-103">Присваивание объектных переменных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06d46-103">Object Variable Assignment (Visual Basic)</span></span>

<span data-ttu-id="06d46-104">Для назначения объекта объектной переменной используется обычная инструкция присваивания.</span><span class="sxs-lookup"><span data-stu-id="06d46-104">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="06d46-105">Можно назначить выражение объекта или ключевое слово [Nothing](../../../language-reference/nothing.md) , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="06d46-105">You can assign an object expression or the [Nothing](../../../language-reference/nothing.md) keyword, as the following example illustrates.</span></span>

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

<span data-ttu-id="06d46-106">`Nothing` означает, что для переменной в настоящий момент не назначен объект.</span><span class="sxs-lookup"><span data-stu-id="06d46-106">`Nothing` means there is no object currently assigned to the variable.</span></span>

## <a name="initialization"></a><span data-ttu-id="06d46-107">Инициализация</span><span class="sxs-lookup"><span data-stu-id="06d46-107">Initialization</span></span>

<span data-ttu-id="06d46-108">Когда код начинает выполняться, переменные объекта инициализируются значением `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="06d46-108">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="06d46-109">Для тех, чьи объявления включают инициализацию, повторно инициализируются значениями, заданными при выполнении инструкций объявления.</span><span class="sxs-lookup"><span data-stu-id="06d46-109">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>

<span data-ttu-id="06d46-110">Вы можете включить инициализацию в объявление с помощью ключевого слова [New](../../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="06d46-110">You can include initialization in your declaration by using the [New](../../../language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="06d46-111">Следующие операторы объявления объявляют переменные объекта `testUri` и `ver` присваивают им определенные объекты.</span><span class="sxs-lookup"><span data-stu-id="06d46-111">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="06d46-112">Каждый из них использует один из перегруженных конструкторов соответствующего класса для инициализации объекта.</span><span class="sxs-lookup"><span data-stu-id="06d46-112">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a><span data-ttu-id="06d46-113">Рассопоставления</span><span class="sxs-lookup"><span data-stu-id="06d46-113">Disassociation</span></span>

<span data-ttu-id="06d46-114">Задание переменной объекта для `Nothing` прекращения сопоставления переменной с каким бы то ни было конкретным объектом.</span><span class="sxs-lookup"><span data-stu-id="06d46-114">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="06d46-115">Это предотвращает случайное изменение объекта путем изменения переменной.</span><span class="sxs-lookup"><span data-stu-id="06d46-115">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="06d46-116">Он также позволяет проверить, указывает ли объектная переменная на допустимый объект, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="06d46-116">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

<span data-ttu-id="06d46-117">Если объект, на который ссылается переменная, находится в другом приложении, этот тест не может определить, было ли приложение завершено, или просто сделает объект недействительным.</span><span class="sxs-lookup"><span data-stu-id="06d46-117">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>

<span data-ttu-id="06d46-118">Объектная переменная со значением `Nothing` также называется *пустой ссылкой*.</span><span class="sxs-lookup"><span data-stu-id="06d46-118">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>

## <a name="current-instance"></a><span data-ttu-id="06d46-119">Текущий экземпляр</span><span class="sxs-lookup"><span data-stu-id="06d46-119">Current Instance</span></span>

<span data-ttu-id="06d46-120">*Текущим экземпляром* объекта является тот, в котором выполняется код в данный момент.</span><span class="sxs-lookup"><span data-stu-id="06d46-120">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="06d46-121">Поскольку весь код выполняется внутри процедуры, текущим экземпляром является тот, в котором была вызвана процедура.</span><span class="sxs-lookup"><span data-stu-id="06d46-121">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>

<span data-ttu-id="06d46-122">`Me`Ключевое слово выступает в качестве объектной переменной, ссылающейся на текущий экземпляр.</span><span class="sxs-lookup"><span data-stu-id="06d46-122">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="06d46-123">Если процедура не является [общей](../../../language-reference/modifiers/shared.md), она может использовать `Me` ключевое слово для получения указателя на текущий экземпляр.</span><span class="sxs-lookup"><span data-stu-id="06d46-123">If a procedure is not [Shared](../../../language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="06d46-124">Общие процедуры не могут быть связаны с конкретным экземпляром класса.</span><span class="sxs-lookup"><span data-stu-id="06d46-124">Shared procedures cannot be associated with a specific instance of a class.</span></span>

<span data-ttu-id="06d46-125">Использование `Me` особенно полезно для передачи текущего экземпляра в процедуру в другом модуле.</span><span class="sxs-lookup"><span data-stu-id="06d46-125">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="06d46-126">Например, предположим, что имеется несколько XML-документов и вы хотите добавить к ним некоторый стандартный текст.</span><span class="sxs-lookup"><span data-stu-id="06d46-126">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="06d46-127">В следующем примере определяется процедура для этого.</span><span class="sxs-lookup"><span data-stu-id="06d46-127">The following example defines a procedure to do this.</span></span>

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

<span data-ttu-id="06d46-128">Каждый объект XML-документа может затем вызвать процедуру и передать его текущий экземпляр в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="06d46-128">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="06d46-129">В следующем примере это показано.</span><span class="sxs-lookup"><span data-stu-id="06d46-129">The following example demonstrates this.</span></span>

```vb
addStandardText(Me)
```

## <a name="see-also"></a><span data-ttu-id="06d46-130">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="06d46-130">See also</span></span>

- [<span data-ttu-id="06d46-131">Объектные переменные</span><span class="sxs-lookup"><span data-stu-id="06d46-131">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="06d46-132">Объявление объектной переменной</span><span class="sxs-lookup"><span data-stu-id="06d46-132">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="06d46-133">Значения объектных переменных</span><span class="sxs-lookup"><span data-stu-id="06d46-133">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="06d46-134">Практическое руководство. Объявление объектной переменной в Visual Basic и присвоение ей объекта</span><span class="sxs-lookup"><span data-stu-id="06d46-134">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="06d46-135">Практическое руководство. Как сделать так, чтобы объектная переменная не указывала ни на какой экземпляр</span><span class="sxs-lookup"><span data-stu-id="06d46-135">How to: Make an Object Variable Not Refer to Any Instance</span></span>](how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="06d46-136">Me, My, MyBase и MyClass</span><span class="sxs-lookup"><span data-stu-id="06d46-136">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
