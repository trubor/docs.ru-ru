---
description: Дополнительные сведения см. в статье как вызвать метод делегата (Visual Basic).
title: Практическое руководство. Вызов метода делегата
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c5c20048969f2fef16b8b7f65e84a094a3f1cf9f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434476"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="7756c-103">Практическое руководство. Вызов метода делегата (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7756c-103">How to: Invoke a Delegate Method (Visual Basic)</span></span>

<span data-ttu-id="7756c-104">В этом примере показано, как связать метод с делегатом, а затем вызвать этот метод через делегат.</span><span class="sxs-lookup"><span data-stu-id="7756c-104">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>

### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="7756c-105">Создание делегата и процедур сопоставления</span><span class="sxs-lookup"><span data-stu-id="7756c-105">Create the delegate and matching procedures</span></span>

1. <span data-ttu-id="7756c-106">Создайте делегат с именем `MySubDelegate` .</span><span class="sxs-lookup"><span data-stu-id="7756c-106">Create a delegate named `MySubDelegate`.</span></span>

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. <span data-ttu-id="7756c-107">Объявите класс, содержащий метод с той же сигнатурой, что и у делегата.</span><span class="sxs-lookup"><span data-stu-id="7756c-107">Declare a class that contains a method with the same signature as the delegate.</span></span>

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. <span data-ttu-id="7756c-108">Определите метод, который создает экземпляр делегата и вызывает метод, связанный с делегатом, вызвав встроенный `Invoke` метод.</span><span class="sxs-lookup"><span data-stu-id="7756c-108">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a><span data-ttu-id="7756c-109">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7756c-109">See also</span></span>

- [<span data-ttu-id="7756c-110">Оператор Delegate</span><span class="sxs-lookup"><span data-stu-id="7756c-110">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="7756c-111">Делегаты</span><span class="sxs-lookup"><span data-stu-id="7756c-111">Delegates</span></span>](index.md)
- [<span data-ttu-id="7756c-112">События</span><span class="sxs-lookup"><span data-stu-id="7756c-112">Events</span></span>](../events/index.md)
- [<span data-ttu-id="7756c-113">Многопоточные приложения</span><span class="sxs-lookup"><span data-stu-id="7756c-113">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
