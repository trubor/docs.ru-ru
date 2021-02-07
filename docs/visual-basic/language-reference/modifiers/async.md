---
description: 'Дополнительные сведения: async (Visual Basic)'
title: Async
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: a20c80ace06e386e7c106acc2b7e6258abca13b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701161"
---
# <a name="async-visual-basic"></a><span data-ttu-id="3c460-103">Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c460-103">Async (Visual Basic)</span></span>

<span data-ttu-id="3c460-104">`Async`Модификатор указывает, что метод или [лямбда-выражение](../../programming-guide/language-features/procedures/lambda-expressions.md) , которое он изменяет, является асинхронным.</span><span class="sxs-lookup"><span data-stu-id="3c460-104">The `Async` modifier indicates that the method or [lambda expression](../../programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span></span> <span data-ttu-id="3c460-105">Такие методы называются *асинхронными методами*.</span><span class="sxs-lookup"><span data-stu-id="3c460-105">Such methods are referred to as *async methods*.</span></span>

<span data-ttu-id="3c460-106">Асинхронный метод представляет собой удобный способ для выполнения работы, которая может занять длительное время, без блокировки потока вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="3c460-106">An async method provides a convenient way to do potentially long-running work without blocking the caller's thread.</span></span> <span data-ttu-id="3c460-107">Вызывающий метод асинхронного метода может возобновить свою работу, не дожидаясь завершения асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="3c460-107">The caller of an async method can resume its work without waiting for the async method to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="3c460-108">Ключевые слова `Async` и `Await` появились в Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="3c460-108">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="3c460-109">Общие сведения о асинхронном программировании см. в статье [Асинхронное программирование с использованием Async и await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="3c460-109">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="3c460-110">В следующем примере показана структура асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="3c460-110">The following example shows the structure of an async method.</span></span> <span data-ttu-id="3c460-111">По соглашению имена асинхронных методов заканчиваются на "Async".</span><span class="sxs-lookup"><span data-stu-id="3c460-111">By convention, async method names end in "Async."</span></span>

```vb
Public Async Function ExampleMethodAsync() As Task(Of Integer)
    ' . . .

    ' At the Await expression, execution in this method is suspended and,
    ' if AwaitedProcessAsync has not already finished, control returns
    ' to the caller of ExampleMethodAsync. When the awaited task is
    ' completed, this method resumes execution.
    Dim exampleInt As Integer = Await AwaitedProcessAsync()

    ' . . .

    ' The return statement completes the task. Any method that is
    ' awaiting ExampleMethodAsync can now get the integer result.
    Return exampleInt
End Function
```

<span data-ttu-id="3c460-112">Как правило, метод, измененный с помощью `Async` ключевого слова, содержит по крайней мере одно выражение или оператор [await](async.md) .</span><span class="sxs-lookup"><span data-stu-id="3c460-112">Typically, a method modified by the `Async` keyword contains at least one [Await](async.md) expression or statement.</span></span> <span data-ttu-id="3c460-113">Метод выполняется синхронно до тех пор, пока не достигнет первого `Await` , после чего он приостанавливается до тех пор, пока не завершится ожидаемая задача.</span><span class="sxs-lookup"><span data-stu-id="3c460-113">The method runs synchronously until it reaches the first `Await`, at which point it suspends until the awaited task completes.</span></span> <span data-ttu-id="3c460-114">Пока Управление возвращается вызывающему методу метода.</span><span class="sxs-lookup"><span data-stu-id="3c460-114">In the meantime, control is returned to the caller of the method.</span></span> <span data-ttu-id="3c460-115">Если метод не содержит `Await` выражение или оператор, метод не приостанавливается и выполняется как синхронный метод.</span><span class="sxs-lookup"><span data-stu-id="3c460-115">If the method doesn't contain an `Await` expression or statement, the method isn't suspended and executes as a synchronous method does.</span></span> <span data-ttu-id="3c460-116">Предупреждение компилятора предупреждает о любых асинхронных методах, которые не содержат, `Await` так как такая ситуация может указывать на ошибку.</span><span class="sxs-lookup"><span data-stu-id="3c460-116">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span></span> <span data-ttu-id="3c460-117">Дополнительные сведения см. в описании [ошибки компилятора](../error-messages/bc42358.md).</span><span class="sxs-lookup"><span data-stu-id="3c460-117">For more information, see the [compiler error](../error-messages/bc42358.md).</span></span>

<span data-ttu-id="3c460-118">`Async`Ключевое слово является незарезервированным ключевым словом.</span><span class="sxs-lookup"><span data-stu-id="3c460-118">The `Async` keyword is an unreserved keyword.</span></span> <span data-ttu-id="3c460-119">Это ключевое слово при изменении метода или лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="3c460-119">It is a keyword when it modifies a method or a lambda expression.</span></span> <span data-ttu-id="3c460-120">Во всех остальных контекстах он интерпретируется как идентификатор.</span><span class="sxs-lookup"><span data-stu-id="3c460-120">In all other contexts, it is interpreted as an identifier.</span></span>

## <a name="return-types"></a><span data-ttu-id="3c460-121">Типы возвращаемых данных</span><span class="sxs-lookup"><span data-stu-id="3c460-121">Return Types</span></span>

<span data-ttu-id="3c460-122">Асинхронный метод является либо [подпроцедурой, либо процедурой](../../programming-guide/language-features/procedures/sub-procedures.md) [функции](../../programming-guide/language-features/procedures/function-procedures.md) , имеющей тип возвращаемого значения <xref:System.Threading.Tasks.Task> или <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="3c460-122">An async method is either a [Sub](../../programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="3c460-123">Метод не может объявлять никакие параметры [ByRef](byref.md) .</span><span class="sxs-lookup"><span data-stu-id="3c460-123">The method cannot declare any [ByRef](byref.md) parameters.</span></span>

<span data-ttu-id="3c460-124">Указывается `Task(Of TResult)` для возвращаемого типа асинхронного метода, если оператор [return](../statements/return-statement.md) метода имеет операнд типа TResult.</span><span class="sxs-lookup"><span data-stu-id="3c460-124">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../statements/return-statement.md) statement of the method has an operand of type TResult.</span></span> <span data-ttu-id="3c460-125">Класс `Task` используется при отсутствии содержательного значения, возвращаемого методом при его завершении.</span><span class="sxs-lookup"><span data-stu-id="3c460-125">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="3c460-126">Это значит, что вызов метода возвращает `Task` , но после `Task` завершения любая `Await` инструкция, ожидающая, `Task` не формирует результирующее значение.</span><span class="sxs-lookup"><span data-stu-id="3c460-126">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `Await` statement that's awaiting the `Task` doesn’t produce a result value.</span></span>

<span data-ttu-id="3c460-127">Асинхронные подпрограммы используются в основном для определения обработчиков событий, где `Sub` требуется процедура.</span><span class="sxs-lookup"><span data-stu-id="3c460-127">Async subroutines are used primarily to define event handlers where a `Sub` procedure is required.</span></span> <span data-ttu-id="3c460-128">Вызывающая сторона асинхронной подпрограммы не может ожидать ее и не может перехватывать исключения, которые вызывает метод.</span><span class="sxs-lookup"><span data-stu-id="3c460-128">The caller of an async subroutine can't await it and can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="3c460-129">Дополнительные сведения и примеры см. в разделе [Асинхронные типы возвращаемых значений](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="3c460-129">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="3c460-130">Пример</span><span class="sxs-lookup"><span data-stu-id="3c460-130">Example</span></span>

<span data-ttu-id="3c460-131">В следующих примерах показан асинхронный обработчик событий, асинхронное лямбда-выражение и асинхронный метод.</span><span class="sxs-lookup"><span data-stu-id="3c460-131">The following examples show an async event handler, an async lambda expression, and an async method.</span></span> <span data-ttu-id="3c460-132">Полный пример использования этих элементов см. в разделе [Пошаговое руководство. доступ к Интернету с помощью Async и await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="3c460-132">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="3c460-133">Код пошагового руководства можно скачать в разделе [Примеры кода от разработчиков](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="3c460-133">You can download the walkthrough code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

```vb
' An event handler must be a Sub procedure.
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click
    textBox1.Clear()
    ' SumPageSizesAsync is a method that returns a Task.
    Await SumPageSizesAsync()
    textBox1.Text = vbCrLf & "Control returned to button1_Click."
End Sub

' The following async lambda expression creates an equivalent anonymous
' event handler.
AddHandler button1.Click, Async Sub(sender, e)
                              textBox1.Clear()
                              ' SumPageSizesAsync is a method that returns a Task.
                              Await SumPageSizesAsync()
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."
                          End Sub

' The following async method returns a Task(Of T).
' A typical call awaits the Byte array result:
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

    ' The downloaded resource ends up in the variable named content.
    Dim content = New MemoryStream()

    ' Initialize an HttpWebRequest for the current URL.
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

    ' Send the request to the Internet resource and wait for
    ' the response.
    Using response As WebResponse = Await webReq.GetResponseAsync()
        ' Get the data stream that is associated with the specified URL.
        Using responseStream As Stream = response.GetResponseStream()
            ' Read the bytes in responseStream and copy them to content.
            ' CopyToAsync returns a Task, not a Task<T>.
            Await responseStream.CopyToAsync(content)
        End Using
    End Using

    ' Return the result as a byte array.
    Return content.ToArray()
End Function
```

## <a name="see-also"></a><span data-ttu-id="3c460-134">См. также</span><span class="sxs-lookup"><span data-stu-id="3c460-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="3c460-135">Оператор Await</span><span class="sxs-lookup"><span data-stu-id="3c460-135">Await Operator</span></span>](../operators/await-operator.md)
- [<span data-ttu-id="3c460-136">Асинхронное программирование с использованием ключевых слов Async и Await</span><span class="sxs-lookup"><span data-stu-id="3c460-136">Asynchronous Programming with Async and Await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="3c460-137">Пошаговое руководство: Получение доступа к Интернету с помощью модификатора Async и оператора Await (C#)</span><span class="sxs-lookup"><span data-stu-id="3c460-137">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
