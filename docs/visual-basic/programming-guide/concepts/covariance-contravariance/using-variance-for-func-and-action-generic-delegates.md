---
description: Дополнительные сведения см. в статье Использование вариативности для универсальных делегатов Func и Action (Visual Basic)
title: Использование вариативности в универсальных методах-делегатах Func и Action
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: 4a445d9ad1cf1bd6ca6e13bdd2e40545c6b28fe8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485241"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="c558d-103">Использование вариативности в универсальных методах-делегатах Func и Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c558d-103">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>

<span data-ttu-id="c558d-104">Эти примеры показывают, как обеспечить возможность многократного использования методов и сделать код более гибким, используя ковариацию и контравариацию в универсальных методах-делегатах `Func` и `Action`.</span><span class="sxs-lookup"><span data-stu-id="c558d-104">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>

<span data-ttu-id="c558d-105">Дополнительные сведения о ковариации и контрвариация см. [в разделе вариативность в делегатах (Visual Basic)](variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c558d-105">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="c558d-106">Использование методов-делегатов с параметрами ковариантного типа</span><span class="sxs-lookup"><span data-stu-id="c558d-106">Using Delegates with Covariant Type Parameters</span></span>

<span data-ttu-id="c558d-107">Следующий пример иллюстрирует преимущества поддержки ковариации в универсальных методах-делегатах `Func`.</span><span class="sxs-lookup"><span data-stu-id="c558d-107">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="c558d-108">Метод `FindByTitle` принимает параметр типа `String` и возвращает объект типа `Employee`.</span><span class="sxs-lookup"><span data-stu-id="c558d-108">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="c558d-109">При этом данный метод можно назначить методу-делегату `Func(Of String, Person)`, поскольку `Employee` наследует `Person`.</span><span class="sxs-lookup"><span data-stu-id="c558d-109">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>

```vb
' Simple hierarchy of classes.
Public Class Person
End Class

Public Class Employee
    Inherits Person
End Class

Class Finder
    Public Shared Function FindByTitle(
        ByVal title As String) As Employee
        ' This is a stub for a method that returns
        ' an employee that has the specified title.
        Return New Employee
    End Function

    Sub Test()
        ' Create an instance of the delegate without using variance.
        Dim findEmployee As Func(Of String, Employee) =
            AddressOf FindByTitle

        ' The delegate expects a method to return Person,
        ' but you can assign it a method that returns Employee.
        Dim findPerson As Func(Of String, Person) =
            AddressOf FindByTitle

        ' You can also assign a delegate
        ' that returns a more derived type to a delegate
        ' that returns a less derived type.
        findPerson = findEmployee
    End Sub
End Class
```

## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="c558d-110">Использование методов-делегатов с параметрами контравариантного типа</span><span class="sxs-lookup"><span data-stu-id="c558d-110">Using Delegates with Contravariant Type Parameters</span></span>

<span data-ttu-id="c558d-111">Следующий пример иллюстрирует преимущества поддержки контравариации в универсальных методах-делегатах `Action`.</span><span class="sxs-lookup"><span data-stu-id="c558d-111">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="c558d-112">Метод `AddToContacts` принимает параметр типа `Person`.</span><span class="sxs-lookup"><span data-stu-id="c558d-112">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="c558d-113">При этом данный метод можно назначить методу-делегату `Action(Of Employee)`, поскольку `Employee` наследует `Person`.</span><span class="sxs-lookup"><span data-stu-id="c558d-113">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>

```vb
Public Class Person
End Class

Public Class Employee
    Inherits Person
End Class

Class AddressBook
    Shared Sub AddToContacts(ByVal person As Person)
        ' This method adds a Person object
        ' to a contact list.
    End Sub

    Sub Test()
        ' Create an instance of the delegate without using variance.
        Dim addPersonToContacts As Action(Of Person) =
            AddressOf AddToContacts

        ' The Action delegate expects
        ' a method that has an Employee parameter,
        ' but you can assign it a method that has a Person parameter
        ' because Employee derives from Person.
        Dim addEmployeeToContacts As Action(Of Employee) =
            AddressOf AddToContacts

        ' You can also assign a delegate
        ' that accepts a less derived parameter
        ' to a delegate that accepts a more derived parameter.
        addEmployeeToContacts = addPersonToContacts
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="c558d-114">См. также</span><span class="sxs-lookup"><span data-stu-id="c558d-114">See also</span></span>

- [<span data-ttu-id="c558d-115">Ковариация и контрвариантность (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c558d-115">Covariance and Contravariance (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="c558d-116">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="c558d-116">Generics</span></span>](../../../../standard/generics/index.md)
