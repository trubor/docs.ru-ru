---
description: 'Дополнительные сведения: Асинхронные типы возвращаемых значения (Visual Basic)'
title: Асинхронные типы возвращаемых значений
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 12a7f577a89ff8f8037de879f9e37d6fdb917aa8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438922"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="e272e-103">Async Return Types (Visual Basic) (Типы возвращаемых значений Async (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="e272e-103">Async Return Types (Visual Basic)</span></span>

<span data-ttu-id="e272e-104">Асинхронные методы имеют три возможных типа возврата: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> и void.</span><span class="sxs-lookup"><span data-stu-id="e272e-104">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="e272e-105">В Visual Basic тип возвращаемого значения void записывается как процедура [Sub](../../language-features/procedures/sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e272e-105">In Visual Basic, the void return type is written as a [Sub](../../language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="e272e-106">Дополнительные сведения о асинхронных методах см. [в разделе Асинхронное программирование с использованием Async и await (Visual Basic)](index.md).</span><span class="sxs-lookup"><span data-stu-id="e272e-106">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="e272e-107">Каждый тип возвращаемого значения рассматривается в одном из следующих разделов, а полный пример, в котором используются все три типа, вы найдете в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="e272e-107">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>

> [!NOTE]
> <span data-ttu-id="e272e-108">Для выполнения этого примера на компьютере должны быть установлены Visual Studio 2012 или более поздней версии и .NET Framework 4.5 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="e272e-108">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="taskt-return-type"></a><a name="BKMK_TaskTReturnType"></a> <span data-ttu-id="e272e-109">Тип возвращаемого значения Task(T)</span><span class="sxs-lookup"><span data-stu-id="e272e-109">Task(T) Return Type</span></span>

<span data-ttu-id="e272e-110"><xref:System.Threading.Tasks.Task%601>Тип возвращаемого значения используется для асинхронного метода, содержащего оператор [return](../../../language-reference/statements/return-statement.md) , в котором операнд имеет тип `TResult` .</span><span class="sxs-lookup"><span data-stu-id="e272e-110">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>

<span data-ttu-id="e272e-111">В следующем примере асинхронный метод `TaskOfT_MethodAsync` содержит оператор return, который возвращает целое число.</span><span class="sxs-lookup"><span data-stu-id="e272e-111">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="e272e-112">Поэтому в объявлении метода должен указываться тип возвращаемого значения `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="e272e-112">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>

```vb
' TASK(OF T) EXAMPLE
Async Function TaskOfT_MethodAsync() As Task(Of Integer)

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.FromResult is a placeholder for actual work that returns a string.
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

    ' The method then can process the result in some way.
    Dim leisureHours As Integer
    If today.First() = "S" Then
        leisureHours = 16
    Else
        leisureHours = 5
    End If

    ' Because the return statement specifies an operand of type Integer, the
    ' method must have a return type of Task(Of Integer).
    Return leisureHours
End Function
```

<span data-ttu-id="e272e-113">При вызове `TaskOfT_MethodAsync` из выражения await это выражение await извлекает целочисленное значение (значение `leisureHours`), хранящееся в задаче, которая возвращается `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="e272e-113">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="e272e-114">Дополнительные сведения о выражениях await см. в разделе [оператор await](../../../language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e272e-114">For more information about await expressions, see [Await Operator](../../../language-reference/operators/await-operator.md).</span></span>

<span data-ttu-id="e272e-115">В следующем коде вызывается и ожидается метод `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="e272e-115">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="e272e-116">Результат назначается переменной `result1`.</span><span class="sxs-lookup"><span data-stu-id="e272e-116">The result is assigned to the `result1` variable.</span></span>

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

<span data-ttu-id="e272e-117">Чтобы лучше понять, как это происходит, отделите вызов метода `TaskOfT_MethodAsync` от применения `Await`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="e272e-117">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="e272e-118">Вызов метода `TaskOfT_MethodAsync`, который не ожидается немедленно, возвращает `Task(Of Integer)`, как и следовало ожидать из объявления метода.</span><span class="sxs-lookup"><span data-stu-id="e272e-118">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="e272e-119">В данном примере эта задача назначается переменной `integerTask`.</span><span class="sxs-lookup"><span data-stu-id="e272e-119">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="e272e-120">Поскольку `integerTask` является <xref:System.Threading.Tasks.Task%601>, она содержит свойство <xref:System.Threading.Tasks.Task%601.Result> типа `TResult`.</span><span class="sxs-lookup"><span data-stu-id="e272e-120">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="e272e-121">В этом примере TResult представляет собой целочисленный тип.</span><span class="sxs-lookup"><span data-stu-id="e272e-121">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="e272e-122">Если выражение `Await` применяется к `integerTask`, выражение await вычисляется как содержимое свойства <xref:System.Threading.Tasks.Task%601.Result%2A> объекта `integerTask`.</span><span class="sxs-lookup"><span data-stu-id="e272e-122">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="e272e-123">Это значение присваивается переменной `result2`.</span><span class="sxs-lookup"><span data-stu-id="e272e-123">The value is assigned to the `result2` variable.</span></span>

> [!WARNING]
> <span data-ttu-id="e272e-124">Свойство <xref:System.Threading.Tasks.Task%601.Result%2A> является блокирующим свойством.</span><span class="sxs-lookup"><span data-stu-id="e272e-124">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="e272e-125">При попытке доступа к нему до завершения его задачи поток, который в текущий момент активен, блокируется до того момента, пока задача не будет завершена, а ее значение не станет доступным.</span><span class="sxs-lookup"><span data-stu-id="e272e-125">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="e272e-126">В большинстве случаев следует получать доступ к этому значению с помощью `Await` вместо прямого обращения к свойству.</span><span class="sxs-lookup"><span data-stu-id="e272e-126">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

<span data-ttu-id="e272e-127">Операторы отображения в следующем коде проверяют, одинаковы ли значения переменной `result1`, переменной `result2` и свойства `Result`.</span><span class="sxs-lookup"><span data-stu-id="e272e-127">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="e272e-128">Помните, что свойство `Result` является блокирующим свойством, и к нему не стоит обращаться до того, как его задача закончит ожидание.</span><span class="sxs-lookup"><span data-stu-id="e272e-128">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="task-return-type"></a><a name="BKMK_TaskReturnType"></a> <span data-ttu-id="e272e-129">Тип возвращаемого значения задачи</span><span class="sxs-lookup"><span data-stu-id="e272e-129">Task Return Type</span></span>

<span data-ttu-id="e272e-130">Асинхронные методы, не содержащие оператор return или содержащие оператор return, который не возвращает операнд, обычно имеют тип возврата <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="e272e-130">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="e272e-131">Такие методы будут [подпрограммными](../../language-features/procedures/sub-procedures.md) процедурами, если они были написаны для синхронного выполнения.</span><span class="sxs-lookup"><span data-stu-id="e272e-131">Such methods would be [Sub](../../language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="e272e-132">Если для асинхронного метода вы используете тип возвращаемого значения `Task`, вызывающий метод может использовать оператор `Await` для приостановки выполнения вызывающего объекта до завершения вызванного асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="e272e-132">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>

<span data-ttu-id="e272e-133">В следующем примере асинхронный метод `Task_MethodAsync` не содержит оператор return.</span><span class="sxs-lookup"><span data-stu-id="e272e-133">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="e272e-134">Следовательно, вы указываете для метода тип возвращаемого значения `Task`, который позволяет ожидать `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="e272e-134">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="e272e-135">Определение типа `Task` не включает свойство `Result` для хранения возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="e272e-135">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>

```vb
' TASK EXAMPLE
Async Function Task_MethodAsync() As Task

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.Delay is a placeholder for actual work.
    Await Task.Delay(2000)
    textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

    ' This method has no return statement, so its return type is Task.
End Function
```

<span data-ttu-id="e272e-136">`Task_MethodAsync` вызывается и ожидается с помощью оператора await (вместо выражения await), похожего на оператор вызова для синхронного метода, возвращающего `Sub` или void.</span><span class="sxs-lookup"><span data-stu-id="e272e-136">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="e272e-137">Применение `Await` оператора в данном случае не приводит к созданию значения.</span><span class="sxs-lookup"><span data-stu-id="e272e-137">The application of an `Await` operator in this case doesn't produce a value.</span></span>

<span data-ttu-id="e272e-138">В следующем коде вызывается и ожидается метод `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="e272e-138">The following code calls and awaits method `Task_MethodAsync`.</span></span>

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

<span data-ttu-id="e272e-139">Как и в предыдущем <xref:System.Threading.Tasks.Task%601> примере, можно разделить вызов `Task_MethodAsync` из приложения `Await` оператора, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="e272e-139">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="e272e-140">Однако следует помнить, что `Task` не содержит свойство `Result`, и при применении оператора await к `Task` никакое значение не создается.</span><span class="sxs-lookup"><span data-stu-id="e272e-140">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>

<span data-ttu-id="e272e-141">В следующем коде вызов `Task_MethodAsync` отделяется от ожидания задачи, которая возвращает `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="e272e-141">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="void-return-type"></a><a name="BKMK_VoidReturnType"></a> <span data-ttu-id="e272e-142">Тип возвращаемого значения void</span><span class="sxs-lookup"><span data-stu-id="e272e-142">Void Return Type</span></span>

<span data-ttu-id="e272e-143">Процедуры в основном используются `Sub` в обработчиках событий, где нет возвращаемого типа (называемого типом возвращаемого значения void в других языках).</span><span class="sxs-lookup"><span data-stu-id="e272e-143">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="e272e-144">Тип возврата void также можно использовать для переопределения методов, возвращающих void, или для методов, выполняющих действия, которые можно классифицировать как "запустить и забыть".</span><span class="sxs-lookup"><span data-stu-id="e272e-144">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="e272e-145">Тем не менее вы должны возвращать `Task` везде, где это возможно, поскольку нельзя ожидать асинхронный метод, возвращающий void.</span><span class="sxs-lookup"><span data-stu-id="e272e-145">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="e272e-146">Любой вызывающий объект такого метода должен иметь возможность завершить свою работу, не дожидаясь завершения вызванного асинхронного метода, и он не должен зависеть ни от каких значений и исключений, создаваемых асинхронным методом.</span><span class="sxs-lookup"><span data-stu-id="e272e-146">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>

<span data-ttu-id="e272e-147">Вызывающий объект асинхронного метода, возвращающего void, не может перехватывать исключения, создаваемые методом, и такие необработанные исключения могут привести к сбою приложения.</span><span class="sxs-lookup"><span data-stu-id="e272e-147">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="e272e-148">Если исключение возникает в асинхронном методе, который возвращает <xref:System.Threading.Tasks.Task> или <xref:System.Threading.Tasks.Task%601>, исключение хранится в возвращенной задаче и повторно вызывается при ожидании задачи.</span><span class="sxs-lookup"><span data-stu-id="e272e-148">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="e272e-149">Поэтому убедитесь, что любой асинхронный метод, который может вызвать исключение, имеет тип возвращаемого значения <xref:System.Threading.Tasks.Task> или <xref:System.Threading.Tasks.Task%601> и что вызовы метода являются ожидаемыми.</span><span class="sxs-lookup"><span data-stu-id="e272e-149">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>

<span data-ttu-id="e272e-150">Дополнительные сведения о перехвате исключений в асинхронных методах см. в статье [об операторе Try...Catch...Finally](../../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e272e-150">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>

<span data-ttu-id="e272e-151">Следующий код определяет асинхронный обработчик событий.</span><span class="sxs-lookup"><span data-stu-id="e272e-151">The following code defines an async event handler.</span></span>

```vb
' SUB EXAMPLE
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

    textBox1.Clear()

    ' Start the process and await its completion. DriverAsync is a
    ' Task-returning async method.
    Await DriverAsync()

    ' Say goodbye.
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
End Sub
```

## <a name="complete-example"></a><a name="BKMK_Example"></a> <span data-ttu-id="e272e-152">Полный пример</span><span class="sxs-lookup"><span data-stu-id="e272e-152">Complete Example</span></span>

<span data-ttu-id="e272e-153">Следующий проект Windows Presentation Foundation (WPF) содержит примеры кода из этого раздела.</span><span class="sxs-lookup"><span data-stu-id="e272e-153">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>

 <span data-ttu-id="e272e-154">Чтобы запустить проект, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e272e-154">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="e272e-155">Запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e272e-155">Start Visual Studio.</span></span>

2. <span data-ttu-id="e272e-156">В строке меню выберите **Файл**, **Создать**, **Проект**.</span><span class="sxs-lookup"><span data-stu-id="e272e-156">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="e272e-157">Откроется диалоговое окно **Новый проект** .</span><span class="sxs-lookup"><span data-stu-id="e272e-157">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="e272e-158">В категории **установленные** **шаблоны** выберите **Visual Basic**, а затем выберите **Windows**.</span><span class="sxs-lookup"><span data-stu-id="e272e-158">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="e272e-159">В списке типов проектов выберите **Приложение WPF**.</span><span class="sxs-lookup"><span data-stu-id="e272e-159">Choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="e272e-160">Введите `AsyncReturnTypes` в качестве имени проекта и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="e272e-160">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="e272e-161">В **обозревателе решений** появится новый проект.</span><span class="sxs-lookup"><span data-stu-id="e272e-161">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="e272e-162">В редакторе кода Visual Studio перейдите на вкладку **MainWindow.xaml** .</span><span class="sxs-lookup"><span data-stu-id="e272e-162">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="e272e-163">Если вкладка не отображается, откройте контекстное меню для MainWindow.xaml в **обозревателе решений** и выберите пункт **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="e272e-163">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>

6. <span data-ttu-id="e272e-164">В окне **XAML** MainWindow.xaml замените код на следующий.</span><span class="sxs-lookup"><span data-stu-id="e272e-164">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>

    ```vb
    <Window x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            Title="MainWindow" Height="350" Width="525">
        <Grid>
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>

        </Grid>
    </Window>
    ```

     <span data-ttu-id="e272e-165">Простое окно, содержащее текстовое поле и кнопку, отобразится в окне **конструктора** для MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="e272e-165">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>

7. <span data-ttu-id="e272e-166">В **Обозреватель решений** откройте контекстное меню файла MainWindow. XAML. vb и выберите пункт **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="e272e-166">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

8. <span data-ttu-id="e272e-167">Замените код в MainWindow.xaml.vb на приведенный далее.</span><span class="sxs-lookup"><span data-stu-id="e272e-167">Replace the code in MainWindow.xaml.vb with the following code.</span></span>

    ```vb
    Class MainWindow

        ' SUB EXAMPLE
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

            textBox1.Clear()

            ' Start the process and await its completion. DriverAsync is a
            ' Task-returning async method.
            Await DriverAsync()

            ' Say goodbye.
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
        End Sub

        Async Function DriverAsync() As Task

            ' Task(Of T)
            ' Call and await the Task(Of T)-returning async method in the same statement.
            Dim result1 As Integer = Await TaskOfT_MethodAsync()

            ' Call and await in separate statements.
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

            ' You can do other work that does not rely on resultTask before awaiting.
            textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

            Dim result2 As Integer = Await integerTask

            ' Display the values of the result1 variable, the result2 variable, and
            ' the resultTask.Result property.
            textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
            textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
            textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf

            ' Task
            ' Call and await the Task-returning async method in the same statement.
            Await Task_MethodAsync()

            ' Call and await in separate statements.
            Dim simpleTask As Task = Task_MethodAsync()

            ' You can do other work that does not rely on simpleTask before awaiting.
            textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

            Await simpleTask
        End Function

        ' TASK(OF T) EXAMPLE
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.FromResult is a placeholder for actual work that returns a string.
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

            ' The method then can process the result in some way.
            Dim leisureHours As Integer
            If today.First() = "S" Then
                leisureHours = 16
            Else
                leisureHours = 5
            End If

            ' Because the return statement specifies an operand of type Integer, the
            ' method must have a return type of Task(Of Integer).
            Return leisureHours
        End Function

        ' TASK EXAMPLE
        Async Function Task_MethodAsync() As Task

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.Delay is a placeholder for actual work.
            Await Task.Delay(2000)
            textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

            ' This method has no return statement, so its return type is Task.
        End Function

    End Class
    ```

9. <span data-ttu-id="e272e-168">Нажмите клавишу F5, чтобы запустить программу, а затем нажмите кнопку **Start** .</span><span class="sxs-lookup"><span data-stu-id="e272e-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="e272e-169">Должны отобразиться следующие выходные данные:</span><span class="sxs-lookup"><span data-stu-id="e272e-169">The following output should appear:</span></span>

    ```console
    Application can continue working while the Task<T> runs. . . .

    Value of result1 variable:   5
    Value of result2 variable:   5
    Value of integerTask.Result: 5

    Sorry for the delay. . . .

    Application can continue working while the Task runs. . . .

    Sorry for the delay. . . .

    All done, exiting button-click event handler.
    ```

## <a name="see-also"></a><span data-ttu-id="e272e-170">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e272e-170">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="e272e-171">Пошаговое руководство. Получение доступа к Интернету с помощью модификатора Async и оператора Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e272e-171">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- <span data-ttu-id="e272e-172">[Control Flow in Async Programs (Visual Basic)](control-flow-in-async-programs.md) (Поток управления в асинхронных программах (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="e272e-172">[Control Flow in Async Programs (Visual Basic)](control-flow-in-async-programs.md)</span></span>
- [<span data-ttu-id="e272e-173">Асинхронный режим</span><span class="sxs-lookup"><span data-stu-id="e272e-173">Async</span></span>](../../../language-reference/modifiers/async.md)
- [<span data-ttu-id="e272e-174">Оператор Await</span><span class="sxs-lookup"><span data-stu-id="e272e-174">Await Operator</span></span>](../../../language-reference/operators/await-operator.md)
