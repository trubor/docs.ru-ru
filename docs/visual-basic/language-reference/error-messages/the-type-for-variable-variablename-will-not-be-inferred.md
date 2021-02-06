---
description: 'Дополнительные сведения о: BC42110: тип для переменной " <variablename> " не будет определен, так как он привязан к полю во внешней области видимости'
title: Тип для переменной <variablename> не будет определен, так как она привязана к полю во включающей области
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: db31f1a6e87a2fd133f095e2fbdde7bc6bded97e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641243"
---
# <a name="bc42110-the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="b770f-103">BC42110: тип для переменной " \<variablename> " не будет определен, так как он привязан к полю во внешней области видимости</span><span class="sxs-lookup"><span data-stu-id="b770f-103">BC42110: The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>

<span data-ttu-id="b770f-104">Тип для переменной " \<variablename> " не будет определен, так как он привязан к полю во внешней области видимости.</span><span class="sxs-lookup"><span data-stu-id="b770f-104">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="b770f-105">Либо измените имя " \<variablename> ", либо используйте полное имя (например, "Me. variablename" или "MyBase. variablename").</span><span class="sxs-lookup"><span data-stu-id="b770f-105">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>

<span data-ttu-id="b770f-106">Переменная цикла в коде имеет то же имя, что и поле класса или другой включающей области.</span><span class="sxs-lookup"><span data-stu-id="b770f-106">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="b770f-107">Так как переменная управления используется без `As` предложения, она привязывается к полю во включающей области, и компилятор не создает для него новую переменную или не выводит ее тип.</span><span class="sxs-lookup"><span data-stu-id="b770f-107">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>

<span data-ttu-id="b770f-108">В следующем примере `Index` Переменная элемента управления в `For` операторе привязана к `Index` полю в `Customer` классе.</span><span class="sxs-lookup"><span data-stu-id="b770f-108">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="b770f-109">Компилятор не создает новую переменную для управляющей переменной `Index` или выводит ее тип.</span><span class="sxs-lookup"><span data-stu-id="b770f-109">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

    ' The following line will raise this warning.
        For Index = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

<span data-ttu-id="b770f-110">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="b770f-110">By default, this message is a warning.</span></span> <span data-ttu-id="b770f-111">Дополнительные сведения о том, как скрыть предупреждения или как рассматривать предупреждения как ошибки, см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b770f-111">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="b770f-112">**Идентификатор ошибки:** BC42110</span><span class="sxs-lookup"><span data-stu-id="b770f-112">**Error ID:** BC42110</span></span>

## <a name="to-address-this-warning"></a><span data-ttu-id="b770f-113">Устранение предупреждения</span><span class="sxs-lookup"><span data-stu-id="b770f-113">To address this warning</span></span>

- <span data-ttu-id="b770f-114">Сделайте переменную управления циклом локальной, изменив ее имя на идентификатор, который не является именем поля класса.</span><span class="sxs-lookup"><span data-stu-id="b770f-114">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>

  ```vb
  For I = 1 To 10
  ```

- <span data-ttu-id="b770f-115">Уточните, что управляющая переменная цикла привязывается к полю класса путем добавления префикса `Me.` к имени переменной.</span><span class="sxs-lookup"><span data-stu-id="b770f-115">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>

  ```vb
  For Me.Index = 1 To 10
  ```

- <span data-ttu-id="b770f-116">Вместо того чтобы полагаться на вывод локального типа, используйте `As` предложение, чтобы указать тип для управляющей переменной цикла.</span><span class="sxs-lookup"><span data-stu-id="b770f-116">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a><span data-ttu-id="b770f-117">Пример</span><span class="sxs-lookup"><span data-stu-id="b770f-117">Example</span></span>

 <span data-ttu-id="b770f-118">В следующем коде показан предыдущий пример с первым исправлением.</span><span class="sxs-lookup"><span data-stu-id="b770f-118">The following code shows the earlier example with the first correction in place.</span></span>

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

        For I = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="b770f-119">См. также</span><span class="sxs-lookup"><span data-stu-id="b770f-119">See also</span></span>

- [<span data-ttu-id="b770f-120">Оператор Option Infer</span><span class="sxs-lookup"><span data-stu-id="b770f-120">Option Infer Statement</span></span>](../statements/option-infer-statement.md)
- [<span data-ttu-id="b770f-121">Оператор For Each…Next</span><span class="sxs-lookup"><span data-stu-id="b770f-121">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="b770f-122">Оператор For…Next</span><span class="sxs-lookup"><span data-stu-id="b770f-122">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="b770f-123">Практическое руководство. Ссылка на текущий экземпляр объекта</span><span class="sxs-lookup"><span data-stu-id="b770f-123">How to: Refer to the Current Instance of an Object</span></span>](../../programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="b770f-124">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="b770f-124">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="b770f-125">Me, My, MyBase и MyClass</span><span class="sxs-lookup"><span data-stu-id="b770f-125">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
