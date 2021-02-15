---
description: Дополнительные сведения о том, как ускорить доступ к объекту с длинным квалификационным путем (Visual Basic).
title: Практическое руководство. Увеличение скорости доступа к объекту с длинным классификационным путем
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 8e0b5dc2ab6c23d57a4e9d905cfd711a79843185
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100467047"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="a07b1-103">Практическое руководство. Увеличение скорости доступа к объекту с длинным классификационным путем (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a07b1-103">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>

<span data-ttu-id="a07b1-104">При частом доступе к объекту, для которого требуется квалификация пути нескольких методов и свойств, можно ускорить код, не повторив классификационный путь.</span><span class="sxs-lookup"><span data-stu-id="a07b1-104">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>

<span data-ttu-id="a07b1-105">Существует два способа избежать повторения пути для уточнения.</span><span class="sxs-lookup"><span data-stu-id="a07b1-105">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="a07b1-106">Объект можно назначить переменной или использовать в `With` блоке.... `End With`</span><span class="sxs-lookup"><span data-stu-id="a07b1-106">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="a07b1-107">Ускорение доступа к сильно известному объекту путем присвоения его переменной</span><span class="sxs-lookup"><span data-stu-id="a07b1-107">To speed up access to a heavily qualified object by assigning it to a variable</span></span>

1. <span data-ttu-id="a07b1-108">Объявите переменную типа объекта, к которому часто осуществляется доступ.</span><span class="sxs-lookup"><span data-stu-id="a07b1-108">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="a07b1-109">Укажите классификационный путь в части инициализации объявления.</span><span class="sxs-lookup"><span data-stu-id="a07b1-109">Specify the qualification path in the initialization part of the declaration.</span></span>

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="a07b1-110">Используйте переменную для доступа к членам объекта.</span><span class="sxs-lookup"><span data-stu-id="a07b1-110">Use the variable to access the object's members.</span></span>

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="a07b1-111">Для ускорения доступа к сильно известному объекту с помощью метода with... Конец блока</span><span class="sxs-lookup"><span data-stu-id="a07b1-111">To speed up access to a heavily qualified object by using a With...End With block</span></span>

1. <span data-ttu-id="a07b1-112">Укажите классификационный путь в `With` операторе.</span><span class="sxs-lookup"><span data-stu-id="a07b1-112">Put the qualification path in a `With` statement.</span></span>

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="a07b1-113">Получите доступ к членам объекта внутри `With` блока перед `End With` инструкцией.</span><span class="sxs-lookup"><span data-stu-id="a07b1-113">Access the object's members inside the `With` block, before the `End With` statement.</span></span>

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a><span data-ttu-id="a07b1-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a07b1-114">See also</span></span>

- [<span data-ttu-id="a07b1-115">Объектные переменные</span><span class="sxs-lookup"><span data-stu-id="a07b1-115">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="a07b1-116">Оператор With…End With</span><span class="sxs-lookup"><span data-stu-id="a07b1-116">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
