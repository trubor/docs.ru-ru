---
description: 'Дополнительные сведения о: BC42326: лямбда-выражение не будет удалено из этого обработчика событий'
title: Лямбда-выражение не будет удалено из этого обработчика событий
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 6feb8733a6413caa564d2c930b4d35dc5697b4fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795954"
---
# <a name="bc42326-lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="e768d-103">BC42326: лямбда-выражение не будет удалено из этого обработчика событий</span><span class="sxs-lookup"><span data-stu-id="e768d-103">BC42326: Lambda expression will not be removed from this event handler</span></span>

<span data-ttu-id="e768d-104">Лямбда-выражение не будет удалено из этого обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="e768d-104">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="e768d-105">Назначьте лямбда-выражение переменной и используйте переменную для добавления и удаления события.</span><span class="sxs-lookup"><span data-stu-id="e768d-105">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>

<span data-ttu-id="e768d-106">При использовании лямбда-выражений с обработчиками событий вы не сможете увидеть ожидаемое поведение.</span><span class="sxs-lookup"><span data-stu-id="e768d-106">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="e768d-107">Компилятор создает новый метод для каждого определения лямбда-выражения, даже если они идентичны.</span><span class="sxs-lookup"><span data-stu-id="e768d-107">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="e768d-108">Поэтому отображается следующий код `False` .</span><span class="sxs-lookup"><span data-stu-id="e768d-108">Therefore, the following code displays `False`.</span></span>

```vb
Module Module1

    Sub Main()
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1
        Console.WriteLine(fun1 = fun2)
    End Sub

    Delegate Function ChangeInteger(ByVal x As Integer) As Integer

End Module
```

<span data-ttu-id="e768d-109">При использовании лямбда-выражений с обработчиками событий это может привести к непредвиденным результатам.</span><span class="sxs-lookup"><span data-stu-id="e768d-109">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="e768d-110">В следующем примере лямбда-выражение, добавленное с помощью, `AddHandler` не удаляется `RemoveHandler` инструкцией.</span><span class="sxs-lookup"><span data-stu-id="e768d-110">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Sub Main()

        ' The following line adds one listener to the event.
        AddHandler ProcessInteger, Function(m As Integer) m

        ' The following statement searches the current listeners
        ' for a match to remove. However, this lambda is not the same
        ' as the previous one, so nothing is removed.
        RemoveHandler ProcessInteger, Function(m As Integer) m

    End Sub
End Module
```

<span data-ttu-id="e768d-111">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="e768d-111">By default, this message is a warning.</span></span> <span data-ttu-id="e768d-112">Дополнительные сведения о скрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e768d-112">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="e768d-113">**Идентификатор ошибки:** BC42326</span><span class="sxs-lookup"><span data-stu-id="e768d-113">**Error ID:** BC42326</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e768d-114">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="e768d-114">To correct this error</span></span>

<span data-ttu-id="e768d-115">Чтобы избежать предупреждения и удалить лямбда-выражение, назначьте лямбда-выражение переменной и используйте переменную в `AddHandler` `RemoveHandler` инструкциях и, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e768d-115">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Dim PrintHandler As ProcessIntegerEventHandler

    Sub Main()

        ' Assign the lambda expression to a variable.
        PrintHandler = Function(m As Integer) m

        ' Use the variable to add the listener.
        AddHandler ProcessInteger, PrintHandler

        ' Use the variable again when you want to remove the listener.
        RemoveHandler ProcessInteger, PrintHandler

    End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="e768d-116">См. также</span><span class="sxs-lookup"><span data-stu-id="e768d-116">See also</span></span>

- [<span data-ttu-id="e768d-117">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="e768d-117">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="e768d-118">Неявное преобразование делегата</span><span class="sxs-lookup"><span data-stu-id="e768d-118">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="e768d-119">События</span><span class="sxs-lookup"><span data-stu-id="e768d-119">Events</span></span>](../../programming-guide/language-features/events/index.md)
