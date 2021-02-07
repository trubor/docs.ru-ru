---
description: 'Дополнительные сведения об инструкции: using (Visual Basic)'
title: Оператор Using
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: fea77a441182b7c3ecac58d4fe7f1297a87f086c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740890"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="1ad33-103">Оператор Using (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ad33-103">Using Statement (Visual Basic)</span></span>

<span data-ttu-id="1ad33-104">Объявляет начало `Using` блока и при необходимости получает системные ресурсы, которые блокируют элементы управления.</span><span class="sxs-lookup"><span data-stu-id="1ad33-104">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ad33-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1ad33-105">Syntax</span></span>

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a><span data-ttu-id="1ad33-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="1ad33-106">Parts</span></span>

|<span data-ttu-id="1ad33-107">Термин</span><span class="sxs-lookup"><span data-stu-id="1ad33-107">Term</span></span>|<span data-ttu-id="1ad33-108">Определение</span><span class="sxs-lookup"><span data-stu-id="1ad33-108">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="1ad33-109">Требуется, если не указан `resourceexpression` .</span><span class="sxs-lookup"><span data-stu-id="1ad33-109">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="1ad33-110">Список из одного или нескольких системных ресурсов, которые `Using` управляются этим блоком, разделенные запятыми.</span><span class="sxs-lookup"><span data-stu-id="1ad33-110">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="1ad33-111">Требуется, если не указан `resourcelist` .</span><span class="sxs-lookup"><span data-stu-id="1ad33-111">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="1ad33-112">Ссылка на переменную или выражение, ссылающееся на системный ресурс, который должен управляться этим `Using` блоком.</span><span class="sxs-lookup"><span data-stu-id="1ad33-112">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="1ad33-113">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1ad33-113">Optional.</span></span> <span data-ttu-id="1ad33-114">Блок операторов, `Using` выполняемых блоком.</span><span class="sxs-lookup"><span data-stu-id="1ad33-114">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="1ad33-115">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1ad33-115">Required.</span></span> <span data-ttu-id="1ad33-116">Завершает определение `Using` блока и уничтожает все ресурсы, которыми он управляет.</span><span class="sxs-lookup"><span data-stu-id="1ad33-116">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  

 <span data-ttu-id="1ad33-117">Каждый ресурс в `resourcelist` части имеет следующий синтаксис и части:</span><span class="sxs-lookup"><span data-stu-id="1ad33-117">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 <span data-ttu-id="1ad33-118">-или-</span><span class="sxs-lookup"><span data-stu-id="1ad33-118">-or-</span></span>

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a><span data-ttu-id="1ad33-119">ресаурцелист части</span><span class="sxs-lookup"><span data-stu-id="1ad33-119">resourcelist Parts</span></span>

|<span data-ttu-id="1ad33-120">Термин</span><span class="sxs-lookup"><span data-stu-id="1ad33-120">Term</span></span>|<span data-ttu-id="1ad33-121">Определение</span><span class="sxs-lookup"><span data-stu-id="1ad33-121">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="1ad33-122">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="1ad33-122">Required.</span></span> <span data-ttu-id="1ad33-123">Ссылочная переменная, которая ссылается на системный ресурс, который `Using` контролируется блоком.</span><span class="sxs-lookup"><span data-stu-id="1ad33-123">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="1ad33-124">Требуется, если `Using` инструкция получает ресурс.</span><span class="sxs-lookup"><span data-stu-id="1ad33-124">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="1ad33-125">Если вы уже приобрели ресурс, используйте второй альтернативный синтаксис.</span><span class="sxs-lookup"><span data-stu-id="1ad33-125">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="1ad33-126">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1ad33-126">Required.</span></span> <span data-ttu-id="1ad33-127">Класс ресурса.</span><span class="sxs-lookup"><span data-stu-id="1ad33-127">The class of the resource.</span></span> <span data-ttu-id="1ad33-128">Класс должен реализовывать <xref:System.IDisposable> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="1ad33-128">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="1ad33-129">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1ad33-129">Optional.</span></span> <span data-ttu-id="1ad33-130">Список аргументов, передаваемый конструктору для создания экземпляра `resourcetype` .</span><span class="sxs-lookup"><span data-stu-id="1ad33-130">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="1ad33-131">См. [список параметров](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="1ad33-131">See [Parameter List](parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="1ad33-132">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1ad33-132">Required.</span></span> <span data-ttu-id="1ad33-133">Переменная или выражение, ссылающееся на системный ресурс, удовлетворяющий требованиям `resourcetype` .</span><span class="sxs-lookup"><span data-stu-id="1ad33-133">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="1ad33-134">Если используется второй альтернативный синтаксис, необходимо получить ресурс перед передачей управления `Using` оператору.</span><span class="sxs-lookup"><span data-stu-id="1ad33-134">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ad33-135">Remarks</span><span class="sxs-lookup"><span data-stu-id="1ad33-135">Remarks</span></span>

 <span data-ttu-id="1ad33-136">Иногда коду требуется неуправляемый ресурс, например файловый обработчик, оболочка COM или соединение SQL.</span><span class="sxs-lookup"><span data-stu-id="1ad33-136">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="1ad33-137">`Using`Блок гарантирует удаление одного или нескольких таких ресурсов при завершении кода с ними.</span><span class="sxs-lookup"><span data-stu-id="1ad33-137">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="1ad33-138">Это делает их доступными для использования другим кодом.</span><span class="sxs-lookup"><span data-stu-id="1ad33-138">This makes them available for other code to use.</span></span>

 <span data-ttu-id="1ad33-139">Управляемые ресурсы удаляются сборщиком мусора платформа .NET Framework (GC) без дополнительного написания кода для вашей части.</span><span class="sxs-lookup"><span data-stu-id="1ad33-139">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="1ad33-140">`Using`Для управляемых ресурсов блок не требуется.</span><span class="sxs-lookup"><span data-stu-id="1ad33-140">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="1ad33-141">Однако можно по-прежнему использовать `Using` блок для принудительного удаления управляемого ресурса вместо ожидания сборщика мусора.</span><span class="sxs-lookup"><span data-stu-id="1ad33-141">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

 <span data-ttu-id="1ad33-142">`Using`Блок состоит из трех частей: приобретение, использование и утилизация.</span><span class="sxs-lookup"><span data-stu-id="1ad33-142">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>

- <span data-ttu-id="1ad33-143">*Получение* означает создание переменной и ее инициализацию для ссылки на системный ресурс.</span><span class="sxs-lookup"><span data-stu-id="1ad33-143">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="1ad33-144">`Using`Инструкция может получить один или несколько ресурсов, либо можно получить ровно один ресурс, прежде чем входить в блок и передать его в `Using` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="1ad33-144">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="1ad33-145">При указании необходимо `resourceexpression` получить ресурс перед передачей управления `Using` оператору.</span><span class="sxs-lookup"><span data-stu-id="1ad33-145">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>

- <span data-ttu-id="1ad33-146">*Использование* означает доступ к ресурсам и выполнение действий с ними.</span><span class="sxs-lookup"><span data-stu-id="1ad33-146">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="1ad33-147">Операторы между `Using` и `End Using` представляют использование ресурсов.</span><span class="sxs-lookup"><span data-stu-id="1ad33-147">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>

- <span data-ttu-id="1ad33-148">*Реализация* означает вызов <xref:System.IDisposable.Dispose%2A> метода для объекта в `resourcename` .</span><span class="sxs-lookup"><span data-stu-id="1ad33-148">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="1ad33-149">Это позволяет объекту очищать свои ресурсы.</span><span class="sxs-lookup"><span data-stu-id="1ad33-149">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="1ad33-150">`End Using`Оператор уничтожает ресурсы под `Using` управлением блока.</span><span class="sxs-lookup"><span data-stu-id="1ad33-150">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>

## <a name="behavior"></a><span data-ttu-id="1ad33-151">Поведение</span><span class="sxs-lookup"><span data-stu-id="1ad33-151">Behavior</span></span>

 <span data-ttu-id="1ad33-152">`Using`Блок ведет себя подобно `Try` конструкции..., `Finally` в которой `Try` блок использует ресурсы и `Finally` блок удаляет их.</span><span class="sxs-lookup"><span data-stu-id="1ad33-152">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="1ad33-153">По этой причине `Using` блок гарантирует освобождение ресурсов, независимо от того, как вы выйдете из блока.</span><span class="sxs-lookup"><span data-stu-id="1ad33-153">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="1ad33-154">Это справедливо даже в случае необработанного исключения, за исключением <xref:System.StackOverflowException> .</span><span class="sxs-lookup"><span data-stu-id="1ad33-154">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>

 <span data-ttu-id="1ad33-155">Область каждой переменной ресурса, полученной `Using` инструкцией, ограничена `Using` блоком.</span><span class="sxs-lookup"><span data-stu-id="1ad33-155">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>

 <span data-ttu-id="1ad33-156">Если в инструкции указано более одного системного ресурса `Using` , то такой результат будет таким же, как если бы вложенные `Using` блоки совпадали друг с другом.</span><span class="sxs-lookup"><span data-stu-id="1ad33-156">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>

 <span data-ttu-id="1ad33-157">Если `resourcename` имеет значение `Nothing` , вызов не выполняется <xref:System.IDisposable.Dispose%2A> и исключение не создается.</span><span class="sxs-lookup"><span data-stu-id="1ad33-157">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>

## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="1ad33-158">Структурированная обработка исключений в блоке using</span><span class="sxs-lookup"><span data-stu-id="1ad33-158">Structured Exception Handling Within a Using Block</span></span>

 <span data-ttu-id="1ad33-159">Если необходимо выполнить обработку исключения, которое может возникнуть в `Using` блоке, можно добавить `Try` `Finally` к нему полную конструкцию...</span><span class="sxs-lookup"><span data-stu-id="1ad33-159">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="1ad33-160">Если необходимо решить, когда `Using` инструкция не сможет получить ресурс, можно проверить, `resourcename` имеет ли это значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="1ad33-160">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>

## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="1ad33-161">Структурированная обработка исключений вместо блока using</span><span class="sxs-lookup"><span data-stu-id="1ad33-161">Structured Exception Handling Instead of a Using Block</span></span>

 <span data-ttu-id="1ad33-162">Если требуется более точный контроль за приобретением ресурсов или требуется дополнительный код в `Finally` блоке, можно переписать `Using` блок как `Try` конструкцию... `Finally` .</span><span class="sxs-lookup"><span data-stu-id="1ad33-162">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="1ad33-163">В следующем примере показаны скелеты `Try` и `Using` конструкции, эквивалентные в приобретении и утилизации `resource` .</span><span class="sxs-lookup"><span data-stu-id="1ad33-163">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>

```vb
Using resource As New resourceType
    ' Insert code to work with resource.
End Using

' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.
Dim resource As New resourceType
Try
    ' Insert code to work with resource.
Finally
    If resource IsNot Nothing Then
        resource.Dispose()
    End If
End Try
```

> [!NOTE]
> <span data-ttu-id="1ad33-164">Код внутри `Using` блока не должен назначать объект в `resourcename` другую переменную.</span><span class="sxs-lookup"><span data-stu-id="1ad33-164">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="1ad33-165">При выходе из `Using` блока ресурс удаляется, а другая переменная не может получить доступ к ресурсу, на который он указывает.</span><span class="sxs-lookup"><span data-stu-id="1ad33-165">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>

## <a name="example"></a><span data-ttu-id="1ad33-166">Пример</span><span class="sxs-lookup"><span data-stu-id="1ad33-166">Example</span></span>

 <span data-ttu-id="1ad33-167">В следующем примере создается файл с именем log.txt и в файл записывается две строки текста.</span><span class="sxs-lookup"><span data-stu-id="1ad33-167">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="1ad33-168">В примере также считывается тот же файл и отображаются строки текста:</span><span class="sxs-lookup"><span data-stu-id="1ad33-168">The example also reads that same file and displays the lines of text:</span></span>

 <span data-ttu-id="1ad33-169">Поскольку <xref:System.IO.TextWriter> классы и <xref:System.IO.TextReader> реализуют <xref:System.IDisposable> интерфейс, код может использовать инструкции, `Using` чтобы убедиться, что файл правильно закрыт после операций записи и чтения.</span><span class="sxs-lookup"><span data-stu-id="1ad33-169">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a><span data-ttu-id="1ad33-170">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1ad33-170">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="1ad33-171">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="1ad33-171">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="1ad33-172">Практическое руководство. Удаление системного ресурса</span><span class="sxs-lookup"><span data-stu-id="1ad33-172">How to: Dispose of a System Resource</span></span>](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
