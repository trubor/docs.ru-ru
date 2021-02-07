---
description: 'Дополнительные сведения: ReadOnly (Visual Basic)'
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: f510271531f6e6604f2b542d8331d1a1d7f64d58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700914"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="803cd-103">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="803cd-103">ReadOnly (Visual Basic)</span></span>

<span data-ttu-id="803cd-104">Указывает, что переменная или свойство может быть прочитано, но не записано.</span><span class="sxs-lookup"><span data-stu-id="803cd-104">Specifies that a variable or property can be read but not written.</span></span>

## <a name="remarks"></a><span data-ttu-id="803cd-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="803cd-105">Remarks</span></span>

## <a name="rules"></a><span data-ttu-id="803cd-106">Правила</span><span class="sxs-lookup"><span data-stu-id="803cd-106">Rules</span></span>

- <span data-ttu-id="803cd-107">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="803cd-107">**Declaration Context.**</span></span> <span data-ttu-id="803cd-108">`ReadOnly` можно использовать только на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="803cd-108">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="803cd-109">Это означает, что контекст объявления для `ReadOnly` элемента должен быть классом, структурой или модулем и не может быть исходным файлом, пространством имен или процедурой.</span><span class="sxs-lookup"><span data-stu-id="803cd-109">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="803cd-110">**Комбинированные модификаторы.**</span><span class="sxs-lookup"><span data-stu-id="803cd-110">**Combined Modifiers.**</span></span> <span data-ttu-id="803cd-111">Нельзя указывать `ReadOnly` вместе с `Static` в одном объявлении.</span><span class="sxs-lookup"><span data-stu-id="803cd-111">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>

- <span data-ttu-id="803cd-112">**Присвоение значения.**</span><span class="sxs-lookup"><span data-stu-id="803cd-112">**Assigning a Value.**</span></span> <span data-ttu-id="803cd-113">Код, использующий `ReadOnly` свойство, не может задать его значение.</span><span class="sxs-lookup"><span data-stu-id="803cd-113">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="803cd-114">Но код, имеющий доступ к базовому хранилищу, может назначить или изменить значение в любое время.</span><span class="sxs-lookup"><span data-stu-id="803cd-114">But code that has access to the underlying storage can assign or change the value at any time.</span></span>

     <span data-ttu-id="803cd-115">Значение переменной можно присвоить `ReadOnly` только в ее объявлении или в конструкторе класса или структуры, в которой он определен.</span><span class="sxs-lookup"><span data-stu-id="803cd-115">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>

## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="803cd-116">Когда следует использовать переменную только для чтения</span><span class="sxs-lookup"><span data-stu-id="803cd-116">When to Use a ReadOnly Variable</span></span>

<span data-ttu-id="803cd-117">Существуют ситуации, в которых нельзя использовать [оператор Const](../statements/const-statement.md) для объявления и присваивания постоянного значения.</span><span class="sxs-lookup"><span data-stu-id="803cd-117">There are situations in which you cannot use a [Const Statement](../statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="803cd-118">Например, `Const` инструкция может не принять тип данных, который необходимо назначить, или не удастся вычислить значение во время компиляции с помощью константного выражения.</span><span class="sxs-lookup"><span data-stu-id="803cd-118">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="803cd-119">Возможно, вы даже не узнаете значение во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="803cd-119">You might not even know the value at compile time.</span></span> <span data-ttu-id="803cd-120">В таких случаях можно использовать `ReadOnly` переменную для хранения постоянного значения.</span><span class="sxs-lookup"><span data-stu-id="803cd-120">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="803cd-121">Если тип данных переменной является ссылочным типом, например массивом или экземпляром класса, его члены можно изменить, даже если сама переменная имеет значение `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="803cd-121">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="803cd-122">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="803cd-122">The following example illustrates this.</span></span>

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

<span data-ttu-id="803cd-123">При инициализации массив, на который указывает, `characterArray()` содержит "x", "y" и "z".</span><span class="sxs-lookup"><span data-stu-id="803cd-123">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="803cd-124">Так как переменная `characterArray` является `ReadOnly` , ее значение нельзя изменить после инициализации, то есть нельзя присвоить ему новый массив.</span><span class="sxs-lookup"><span data-stu-id="803cd-124">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="803cd-125">Однако можно изменить значения одного или нескольких элементов массива.</span><span class="sxs-lookup"><span data-stu-id="803cd-125">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="803cd-126">После вызова процедуры `ChangeArrayElement` массив, на который указывает, `characterArray()` содержит "x", "M" и "z".</span><span class="sxs-lookup"><span data-stu-id="803cd-126">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>

<span data-ttu-id="803cd-127">Обратите внимание, что это похоже на объявление параметра процедуры как [ByVal](byval.md), что не позволяет процедуре изменять сам аргумент вызова, но позволяет ему изменять его члены.</span><span class="sxs-lookup"><span data-stu-id="803cd-127">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>

## <a name="example"></a><span data-ttu-id="803cd-128">Пример</span><span class="sxs-lookup"><span data-stu-id="803cd-128">Example</span></span>

<span data-ttu-id="803cd-129">В следующем примере определяется `ReadOnly` свойство для даты найма сотрудника.</span><span class="sxs-lookup"><span data-stu-id="803cd-129">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="803cd-130">Класс сохраняет значение свойства внутри в виде `Private` переменной, и только код внутри класса может изменить это значение.</span><span class="sxs-lookup"><span data-stu-id="803cd-130">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="803cd-131">Однако свойство имеет значение `Public` , а любой код, который может получить доступ к классу, может считать свойство.</span><span class="sxs-lookup"><span data-stu-id="803cd-131">However, the property is `Public`, and any code that can access the class can read the property.</span></span>

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

<span data-ttu-id="803cd-132">Модификатор `ReadOnly` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="803cd-132">The `ReadOnly` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="803cd-133">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="803cd-133">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="803cd-134">Property Statement</span><span class="sxs-lookup"><span data-stu-id="803cd-134">Property Statement</span></span>](../statements/property-statement.md)

## <a name="see-also"></a><span data-ttu-id="803cd-135">См. также</span><span class="sxs-lookup"><span data-stu-id="803cd-135">See also</span></span>

- [<span data-ttu-id="803cd-136">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="803cd-136">WriteOnly</span></span>](writeonly.md)
- [<span data-ttu-id="803cd-137">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="803cd-137">Keywords</span></span>](../keywords/index.md)
