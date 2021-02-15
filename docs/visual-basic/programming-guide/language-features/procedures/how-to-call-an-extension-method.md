---
description: Дополнительные сведения см. в статье как вызвать метод расширения (Visual Basic).
title: Практическое руководство. Вызов метода расширения
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: ec5217526eb0cb28d172ab917df08a8bfe87fe95
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471387"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="b20e0-103">Практическое руководство. Вызов метода расширения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b20e0-103">How to: Call an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="b20e0-104">Методы расширения позволяют добавлять методы в существующий класс.</span><span class="sxs-lookup"><span data-stu-id="b20e0-104">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="b20e0-105">После объявления и включения в область действия метода расширения можно вызвать его как метод экземпляра типа, который он расширяет.</span><span class="sxs-lookup"><span data-stu-id="b20e0-105">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="b20e0-106">Дополнительные сведения о написании метода расширения см. [в разделе как написать метод расширения](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="b20e0-106">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>

 <span data-ttu-id="b20e0-107">Следующие инструкции относятся к методу расширения `PrintAndPunctuate` , который отображает экземпляр строки, который вызывает его, за которым следует любое значение, отправляемое для второго параметра `punc` .</span><span class="sxs-lookup"><span data-stu-id="b20e0-107">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

<span data-ttu-id="b20e0-108">Метод должен находиться в области видимости при его вызове.</span><span class="sxs-lookup"><span data-stu-id="b20e0-108">The method must be in scope when it is called.</span></span>

### <a name="to-call-an-extension-method"></a><span data-ttu-id="b20e0-109">Вызов метода расширения</span><span class="sxs-lookup"><span data-stu-id="b20e0-109">To call an extension method</span></span>

1. <span data-ttu-id="b20e0-110">Объявите переменную с типом данных первого параметра метода расширения.</span><span class="sxs-lookup"><span data-stu-id="b20e0-110">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="b20e0-111">Для необходимо `PrintAndPunctuate` иметь <xref:System.String> переменную:</span><span class="sxs-lookup"><span data-stu-id="b20e0-111">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>

    ```vb
    Dim example = "Ready"
    ```

2. <span data-ttu-id="b20e0-112">Эта переменная вызывает метод расширения, и его значение привязывается к первому параметру, `aString` .</span><span class="sxs-lookup"><span data-stu-id="b20e0-112">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="b20e0-113">Отобразится следующая инструкция вызова `Ready?` .</span><span class="sxs-lookup"><span data-stu-id="b20e0-113">The following calling statement will display `Ready?`.</span></span>

    ```vb
    example.PrintAndPunctuate("?")
    ```

     <span data-ttu-id="b20e0-114">Обратите внимание, что вызов этого метода расширения выглядит так же, как вызов любого метода <xref:System.String> экземпляра, для которого требуется один параметр:</span><span class="sxs-lookup"><span data-stu-id="b20e0-114">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. <span data-ttu-id="b20e0-115">Объявите другую строковую переменную и снова вызовите метод, чтобы увидеть, что он работает с любой строкой.</span><span class="sxs-lookup"><span data-stu-id="b20e0-115">Declare another string variable and call the method again to see that it works with any string.</span></span>

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     <span data-ttu-id="b20e0-116">Результат в этом случае: `or not!!!` .</span><span class="sxs-lookup"><span data-stu-id="b20e0-116">The result this time is: `or not!!!`.</span></span>

## <a name="example"></a><span data-ttu-id="b20e0-117">Пример</span><span class="sxs-lookup"><span data-stu-id="b20e0-117">Example</span></span>

 <span data-ttu-id="b20e0-118">Следующий код является полным примером создания и использования простого метода расширения.</span><span class="sxs-lookup"><span data-stu-id="b20e0-118">The following code is a complete example of the creation and use of a simple extension method.</span></span>

```vb
Imports System.Runtime.CompilerServices
Imports ConsoleApplication1.StringExtensions

Module Module1

    Sub Main()

        Dim example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")

        Dim example2 = "Goodbye"
        example2.PrintAndPunctuate("?")
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module

' Output:
' Hello.
' Hello!!!!
' Goodbye?
```

## <a name="see-also"></a><span data-ttu-id="b20e0-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b20e0-119">See also</span></span>

- [<span data-ttu-id="b20e0-120">Практическое руководство. Написание метода расширения</span><span class="sxs-lookup"><span data-stu-id="b20e0-120">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="b20e0-121">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="b20e0-121">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="b20e0-122">Область видимости в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b20e0-122">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
