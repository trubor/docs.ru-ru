---
description: 'Дополнительные сведения: объектная переменная или переменная блока не задана'
title: Не задана переменная объекта или переменная блока With
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: a20655c2219aa5b90015e025a38ea9dd02894a6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795577"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="298d7-103">Не задана переменная объекта или переменная блока With</span><span class="sxs-lookup"><span data-stu-id="298d7-103">Object variable or With block variable not set</span></span>

<span data-ttu-id="298d7-104">Указана недопустимая объектная переменная.</span><span class="sxs-lookup"><span data-stu-id="298d7-104">An invalid object variable is being referenced.</span></span> <span data-ttu-id="298d7-105">Эта ошибка может возникать по нескольким причинам:</span><span class="sxs-lookup"><span data-stu-id="298d7-105">This error can occur for several reasons:</span></span>

- <span data-ttu-id="298d7-106">Переменная объявлена без указания типа.</span><span class="sxs-lookup"><span data-stu-id="298d7-106">A variable was declared without specifying a type.</span></span> <span data-ttu-id="298d7-107">Если переменная объявлена без указания типа, по умолчанию используется тип `Object` .</span><span class="sxs-lookup"><span data-stu-id="298d7-107">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="298d7-108">Например, переменная, объявленная с `Dim x` типом, будет иметь тип `Object;` переменной, объявленной с `Dim x As String` типом `String` .</span><span class="sxs-lookup"><span data-stu-id="298d7-108">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="298d7-109">`Option Strict`Оператор запрещает неявную типизацию, которая приводит к `Object` типу.</span><span class="sxs-lookup"><span data-stu-id="298d7-109">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="298d7-110">Если опустить тип, возникнет ошибка времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="298d7-110">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="298d7-111">См. раздел [Оператор Option Strict](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="298d7-111">See [Option Strict Statement](../statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="298d7-112">Предпринимается попытка сослаться на объект, для которого задано значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="298d7-112">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="298d7-113">Предпринята попытка получить доступ к элементу переменной массива, которая была неправильно объявлена.</span><span class="sxs-lookup"><span data-stu-id="298d7-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="298d7-114">Например, массив, объявленный как, `products() As String` вызовет ошибку при попытке сослаться на элемент массива `products(3) = "Widget"` .</span><span class="sxs-lookup"><span data-stu-id="298d7-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="298d7-115">Массив не содержит элементов и обрабатывается как объект.</span><span class="sxs-lookup"><span data-stu-id="298d7-115">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="298d7-116">Попытка получить доступ к коду в `With...End With` блоке до инициализации блока.</span><span class="sxs-lookup"><span data-stu-id="298d7-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="298d7-117">`With...End With`Блок необходимо инициализировать, выполнив `With` точку входа оператора.</span><span class="sxs-lookup"><span data-stu-id="298d7-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="298d7-118">В более ранних версиях Visual Basic или VBA эта ошибка была также вызвана путем присвоения значения переменной без использования `Set` ключевого слова ( `x = "name"` вместо `Set x = "name"` ).</span><span class="sxs-lookup"><span data-stu-id="298d7-118">In earlier versions of Visual Basic or VBA, this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="298d7-119">`Set`Ключевое слово больше не является допустимым в Visual Basic .NET.</span><span class="sxs-lookup"><span data-stu-id="298d7-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="298d7-120">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="298d7-120">To correct this error</span></span>

1. <span data-ttu-id="298d7-121">Задайте `Option Strict` для значение `On` , добавив следующий код в начало файла:</span><span class="sxs-lookup"><span data-stu-id="298d7-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="298d7-122">При запуске проекта в **Список ошибок** для любой переменной, указанной без типа, отобразится ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="298d7-122">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="298d7-123">Если вы не хотите включать `Option Strict` , найдите в коде любые переменные, которые были указаны без типа ( `Dim x` вместо `Dim x As String` ), и добавьте предполагаемый тип к объявлению.</span><span class="sxs-lookup"><span data-stu-id="298d7-123">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="298d7-124">Убедитесь, что вы не ссылаетесь на переменную объекта, для которой было задано значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="298d7-124">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="298d7-125">Найдите ключевое слово в коде `Nothing` и измените код таким образом, чтобы объект не был установлен в значение `Nothing` до тех пор, пока вы не задали ссылку на него.</span><span class="sxs-lookup"><span data-stu-id="298d7-125">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="298d7-126">Прежде чем обращаться к ним, убедитесь, что все переменные массива имеют размеры.</span><span class="sxs-lookup"><span data-stu-id="298d7-126">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="298d7-127">Можно либо назначить измерение при первом создании массива ( `Dim x(5) As String` вместо `Dim x() As String` ), либо использовать `ReDim` ключевое слово, чтобы задать размеры массива до первого доступа к нему.</span><span class="sxs-lookup"><span data-stu-id="298d7-127">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="298d7-128">Убедитесь, что `With` блок инициализирован путем выполнения `With` точки входа оператора.</span><span class="sxs-lookup"><span data-stu-id="298d7-128">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="298d7-129">См. также</span><span class="sxs-lookup"><span data-stu-id="298d7-129">See also</span></span>

- [<span data-ttu-id="298d7-130">Объявление объектной переменной</span><span class="sxs-lookup"><span data-stu-id="298d7-130">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="298d7-131">Оператор reDim</span><span class="sxs-lookup"><span data-stu-id="298d7-131">ReDim Statement</span></span>](../statements/redim-statement.md)
- [<span data-ttu-id="298d7-132">Оператор With…End With</span><span class="sxs-lookup"><span data-stu-id="298d7-132">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
